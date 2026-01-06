<!-- Logo and Branding -->

<p align="left">
  <img src="Supporting_Images/PRIME-CVD_Logo.png" alt="PRIME-CVD Logo" width="300"/>
</p>

---

# About PRIME‑CVD

PRIME‑CVD (Parametrically Rendered Informatics Medical Environment for Cardiovascular Disease) is an educational, privacy-preserving synthetic dataset and teaching environment developed by the Centre for Big Data Research in Health (CBDRH), UNSW. PRIME‑CVD provides fully parameterised, DAG-driven synthetic data designed specifically for teaching causal reasoning, EMR cleaning, and cardiovascular risk modelling without exposing real patient records.

* **What it provides:** two complementary data assets (a clean cohort and an EMR-style relational transform), worked notebooks, and reproducible code for cohort assembly, harmonisation, survival analysis, and causal-sensitivity experiments.
* **How it’s built:** variables are generated deterministically from a hand-specified causal DAG parameterised using public Australian statistics (ABS, AIHW) and published epidemiologic estimates.
* **Datasets included:**

  * **Data Asset 1:** Clean, analysis-ready cohort (50,000 simulated adults; baseline vars: IRSD quintile, age, smoking, BMI, diabetes, CKD, HbA1c, eGFR, SBP, AF, cvd_event, cvd_time).
  * **Data Asset 2:** Relational EMR-style tables (PatientMasterSummary, PatientChronicDiseases, PatientMeasAndPath) with injected lexical heterogeneity, missingness, unit inconsistencies, and non-sequential IDs.
* **Why it’s safe:** all records are generated de novo from aggregate priors; no patient-level EMR is used, minimising disclosure risk.
* **Who it’s for:** educators and students learning data cleaning, causal inference, bias analysis, and survival modelling; researchers testing causal discovery and MNAR sensitivity.

---

<!-- Side-by-side layout: text and illustration -->

<table>
<tr>
<td width="60%">

**Highlights of PRIME‑CVD**

* Open-access: dataset CSVs, code, and instructional notebooks.
* Designed for teaching: clear separation between the data-generating DAG and the observation process (EMR artefacts).
* Reproducible: deterministic pipelines to regenerate cohorts at arbitrary scale.
* Two assets: ideal cohort for modelling and messy EMR for data-engineering exercises.

</td>
<td width="40%">
  <img src="Supporting_Images/PRIME-CVD_Overview.png" alt="PRIME‑CVD Overview" width="300"/>
</td>
</tr>
</table>

---

<!-- Modelling Toolbox Illustration -->

<table>
<tr>
<td width="60%">

**Generative approach & provenance**

* **Parametric DAG engine:** Each node is sampled conditionally according to logistic, linear, or mixture formulations; causal edges and parameter choices are justified from ABS/AIHW and literature estimates.
* **Deterministic transforms:** The relational EMR is constructed from the clean cohort using reproducible rules to inject the kinds of messiness students need to learn to fix.
* **Validation:** Distributional checks, IRSD-stratified summaries, multivariable Cox models, and correlation matrices accompany the dataset so instructors can explain "expected" results.

</td>
<td width="40%">
  <img src="Supporting_Images/PRIME-CVD_Toolbox.png" alt="PRIME‑CVD Toolbox" width="300"/>
</td>
</tr>
</table>

---

<!-- Side-by-side layout: text and illustration -->

<table>
<tr>
<td width="60%">

**Worked notebooks & labs**

* **Lab 1 — EMR reconstruction:** Link the three EMR-style tables, harmonise heterogeneous disease labels, and reconstitute an analysis-ready cohort. (Notebook: `notebooks/01_reconstruct_emr.ipynb`)
* **Lab 2 — Socioeconomic stratification:** Produce IRSD-stratified visualisations and discuss calibration implications. (Notebook: `notebooks/02_stratify_irsd.ipynb`)
* **Lab 3 — Survival modelling:** Fit a Cox model, report adjusted hazard ratios, and interpret policy-relevant effects. (Notebook: `notebooks/03_cox_model.ipynb`)
* **Lab 4 — Missingness experiments:** Implement MAR and MNAR injection strategies and evaluate bias in HR estimates. (Notebook: `notebooks/04_missingness.ipynb`)

For instructors: each lab contains objectives, starter code, expected outputs, and reflection questions.

</td>
<td width="40%">
  <img src="Supporting_Images/PRIME-CVD_Labs.png" alt="Worked Examples" width="300"/>
</td>
</tr>
</table>

---

# Data Assets (quick links)

* **DataAsset1_CleanCohort.csv** — clean, analysis-ready flat table (50k rows).
* **DataAsset2_PatientMasterSummary.csv** — patient-level summary (IDs, Age_At_2024, IRSD, Smoking, CVD_Event, CVD_Time).
* **DataAsset2_PatientChronicDiseases.csv** — long-form diagnosis records (heterogeneous labels).
* **DataAsset2_PatientMeasAndPath.csv** — long-form measurements (HbA1c, eGFR, SBP; mixed units/labels).

> See `/data` for the CSVs and `/notebooks` for reproducible examples.

---

# The Ground-truth DAG

A central teaching artifact: the causal DAG used to generate the cohort. The DAG (rendered in `figures/DAG.png`) shows exogenous variables (IRSD, Age), behavioural nodes (Smoking, BMI), chronic diseases (Diabetes, CKD, AF), biomarkers (HbA1c, eGFR, SBP), and the CVD event node. Instructors should present the DAG at the start of any lab to anchor assumptions.

---

# Team

<table>
<tr>
<td align="center">
  <img src="Supporting_Images/Nic_Kuo.png" alt="Nic Kuo" width="120"/><br/>
  <sub><b>Dr. Nic Kuo (UNSW)</b></sub>
</td>
<td align="center">
  <img src="Supporting_Images/Marzia_Hoque.png" alt="Marzia Hoque" width="120"/><br/>
  <sub><b>Marzia Hoque (CBDRH)</b></sub>
</td>
<td align="center">
  <img src="Supporting_Images/Blanca_Gallego.png" alt="Blanca Gallego" width="120"/><br/>
  <sub><b>Blanca Gallego (CBDRH)</b></sub>
</td>
<td align="center">
  <img src="Supporting_Images/Louisa_Jorm.png" alt="Louisa Jorm" width="120"/><br/>
  <sub><b>Prof. Louisa Jorm (UNSW)</b></sub>
</td>
</tr>
</table>

---

<!-- CBDRH Branding -->

<p align="left">
  <img src="Supporting_Images/CBDRH_Logo.png" alt="UNSW CBDRH Logo" width="300"/>
</p>

For questions or collaboration: Nic Kuo — [n.kuo@unsw.edu.au](mailto:n.kuo@unsw.edu.au)

---

# Reuse & License

All PRIME‑CVD code, figures, and datasets are released under the **Creative Commons Attribution 4.0 (CC BY 4.0)** licence. You may reuse and adapt materials with appropriate attribution.

---

# References & Further Reading

1. Kuo NI-H, Gallego B, Jorm L, et al. PRIME‑CVD: A Parametrically Rendered Informatics Medical Environment for Education in Cardiovascular Risk Modelling. (Manuscript & Supplementary materials).
2. Australian Bureau of Statistics (ABS) population statistics.
3. Australian Institute of Health and Welfare (AIHW) condition prevalence summaries.

(Last edit: 2026-01-07)
