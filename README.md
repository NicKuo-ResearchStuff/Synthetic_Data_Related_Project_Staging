# Synthetic Data: A Catalyst for Scalable, Modern Education and Innovation

<!-- Logo and Branding -->
<p align="left">
  <img src="ImageStuff/EFig01_Synth4Education.png" alt="HealthGym.ai Logo" width="300"/>
</p>

---

## The Challenge

Across education, research, and industry training, learners need access to data -- but data are often confidential, proprietary, or restricted by regulation.
These constraints limit hands-on learning, reproducibility, and innovation.

---

## The Solution: Synthetic Data

Synthetic data reproduces the statistical structure of real datasets -- numerical, categorical, and temporal -- without containing identifiable information.
When generated responsibly, it enables educators, students, and developers to:
* Instant Access for Learning: start analysing immediately without ethics or approval delays
* Privacy-Preserving by Design: all records are artificial, removing re-identification risk.
* Fairer and More Representative: rebalance data to include minority or rare cases.
* Universally Applicable: the generative methods transfer across any field using structured, tabular data.

---

## Domains Most Suitable for Synthetic CSVs

| Domain                               | Typical Structure    | Example Variables                                          |
| ------------------------------------ | -------------------- | ---------------------------------------------------------- |
| **Healthcare / EMR**                 | Longitudinal records | `patient_id, visit_date, bp, creatinine, diagnosis_code`   |
| **Finance / Banking**                | Transactions         | `customer_id, date, type, amount, balance`                 |
| **Government / Census**              | Surveys              | `person_id, age, income, occupation, region`               |
| **Education / Assessment**           | Learning analytics   | `student_id, module, quiz_score, time_spent`               |
| **Manufacturing / IoT**              | Sensor logs          | `machine_id, timestamp, pressure, temperature, alert_flag` |
| **Psychology / Behavioural Science** | Experiments          | `participant_id, stimulus, response_time, accuracy`        |

These domains share one thing in common: their data can be easily represented as CSV tables, making them ideal for programmatic synthesis and reproducible teaching.

---

<!-- Side-by-side layout: text and illustration -->
<table>
<tr>
<td width="60%">

**Past Use Cases**
* asd
* asd
* asd

Latest update: XXXX-XX-XX.
  
</td>
<td width="40%">
  <img src="Supporting_Images/ZFig025_HandsOn.png" alt="Health + Data Illustration" width="300"/>
</td>
</tr>
</table>

---

## Quickstart Example

Any educator or student can load and explore a dataset in seconds:

```python
# === Load and Preprocess Raw Data ===
import pandas as pd

raw_url = "https://figshare.com/ndownloader/files/40584980"
All_Data = pd.read_csv(raw_url)
All_Data = All_Data.drop(['VL (M)', 'CD4 (M)'], axis=1)

All_Data.replace({
    "Gender":          {1: "Male", 2: "Female"},
    "Ethnic":          {1: "Asian", 2: "African", 3: "Caucasian", 4: "Other"},
    "Base Drug Combo": {0: "FTC + TDF", 1: "3TC + ABC", 2: "FTC + TAF", 
                        3: "DRV + FTC + TDF", 4: "FTC + RTVB + TDF", 5: "Other"},
    "Comp. INI":       {0: "DTG", 1: "RAL", 2: "EVG", 3: "Not Applied"},
    "Comp. NNRTI":     {0: "NVP", 1: "EFV", 2: "RPV", 3: "Not Applied"},
    "Extra PI":        {0: "DRV", 1: "RTVB", 2: "LPV", 3: "RTV", 4: "ATV", 5: "Not Applied"},
    "Extra pk-En":     {0: "False", 1: "True"}
}, inplace=True)

All_Data = All_Data.drop(columns=['Drug (M)'])
All_Data.head()
```

The same workflow can be applied to any structured CSV domain, benefitting:

| Group                         | Benefit                                                     |
| ----------------------------- | ----------------------------------------------------------- |
| Educators & Trainers      | Ready-to-use, ethics-free datasets for practical coursework |
| Students & Learners       | Authentic experience handling real-world data formats       |
| Competition Organisers    | Safe, reproducible data for public challenges               |
| Enterprises & Governments | Privacy-preserving data sharing across teams and partners   |

---

## Contact

For questions or collaboration opportunities, please reach out to Nic at</br>
[n.kuo@unsw.edu.au](mailto:n.kuo@unsw.edu.au)

---

## References

[1] [Kuo et al., *“The Health Gym: Synthetic Health-Related Datasets for the Development of Reinforcement Learning Algorithms.”* Scientific Data (2022)](https://www.nature.com/articles/s41597-022-01784-7)</br>
[2] [Kuo et al., *“Generating Synthetic Clinical Data that Capture Class Imbalanced Distributions with Generative Adversarial Networks.”* Journal of Biomedical Informatics (2023)](https://www.sciencedirect.com/science/article/pii/S1532046423001570)</br>
[3] [Kuo et al., *“Enriching Data Science and Health Care Education: Application and Impact of Synthetic Data Sets Through the Health Gym Project.”* JMIR Medical Education (2024)](https://mededu.jmir.org/2024/1/e51388/)</br>
[4] [Kuo et al., *“The Health Gym v2.0 Synthetic Antiretroviral Therapy (ART) for HIV Dataset.”* Figshare (2023)](https://figshare.com/articles/dataset/The_Health_Gym_v2_0_Synthetic_Antiretroviral_Therapy_ART_for_HIV_Dataset/22827878)

