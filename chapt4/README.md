# Implementation 02: From Table to DataLoader

Hey, hello, and Kia Ora!  

Welcome back to our implementation series for the Health Gym.  
In [Implementation 01](https://github.com/NicKuo-ResearchStuff/Synthetic_Data_Related_Project_Staging/tree/main/chapt3), we pre-processed the ART for HIV dataset -- mapping categoricals, normalising skewed labs, and scaling everything into `[0,1]`.  

This time, we’ll take the next step: reshaping the dataset into a patient–timestep structure and creating a PyTorch DataLoader.  
The main goal here is to clarify what the line

```python
data = data.reshape((-1, Cur_Len, Feats_Len))
````

actually does; let’s unpack it carefully.

---

## Step 0: Why Reshape?

Our dataset starts out **row-based**:

* Each row = a single patient at a single timestep.
* Columns = lab values, regimen info, demographics, etc.
* Ordered by `(PatientID, Timestep)`.

But neural networks like RNNs or Transformers expect **(batch, sequence, features)** input.
That means we need to group the rows for each patient into a 60-month time series.

---

## Step 1: Demo with PatientID + Timestep

Before dropping IDs, let’s keep them in (`All_Data_demo`) and reshape with **12 columns**:

```python
Cur_Len = 60
arr12 = All_Data_demo.values.reshape((-1, Cur_Len, 12))

arr12[0, :10, :]   # patient 0, timesteps 0..9
arr12[1, :10, :]   # patient 1, timesteps 0..9
```

✅ You’ll see at the far right the pairs `(0,0) … (0,9)` for patient 0, and `(1,0) … (1,9)` for patient 1.
This proves that reshape is cleanly grouping rows into patients and timesteps.

---

## Step 2: For Modelling — Drop IDs

For training, we **don’t want the model to see PatientID or raw timestep**, so we drop them.
That leaves **10 features** → `Feats_Len = 10`.

```python
FEAT_COLS = ["VL", "CD4", "Rel CD4",
             "Gender", "Ethnic", "Base Drug Combo",
             "Comp. INI", "Comp. NNRTI",
             "Extra PI", "Extra pk-En"]

X = All_Data[FEAT_COLS].to_numpy()
X = X.reshape(-1, Cur_Len, len(FEAT_COLS))
```

Now each slice `X[i, :, :]` = full 60 months for patient *i*.

---

## Step 3: Building a DataLoader

We wrap this into a PyTorch `TensorDataset` and `DataLoader`:

```python
import torch
from torch.utils.data import TensorDataset, DataLoader

X_tensor = torch.from_numpy(X).float()
T_tensor = torch.full((X_tensor.shape[0], 1), Cur_Len)  # optional metadata

dataset = TensorDataset(X_tensor, T_tensor)
loader  = DataLoader(dataset, batch_size=32, shuffle=True, drop_last=True)

for batch_x, batch_len in loader:
    print(batch_x.shape)  # (32, 60, 10)
    break
```

And that’s it — we’ve turned a flat clinical table into a batched, sequential dataset ready for deep learning.

---

## Step 4: Sanity Checks

Always check two things:

1. **Ordering**

   ```python
   All_Data = All_Data.sort_values(["PatientID", "Timestep"])
   ```

   Otherwise, `reshape` will scramble patients.

2. **Divisibility**

   ```python
   assert len(All_Data) % Cur_Len == 0
   ```

   Every patient must have exactly 60 rows.

---

## Wrapping Up

So, to recap:

* `reshape((-1, Cur_Len, Feats_Len))` reorganises row-based data into `(patients, timesteps, features)`.
* Using `All_Data_demo` (with IDs) shows the alignment clearly.
* For modelling, we strip IDs and keep only real features (10 columns).
* A simple DataLoader then gives us patient sequences in minibatches.

This sets the stage for the next implementation blog, where we’ll start embedding features and building our first neural models! 🚀

Cheers,
\- Nic

[NOT YET DONE]
