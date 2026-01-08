# PRIME-CVD Data Asset 1: A Clean, Causal Cohort for Teaching Cardiovascular Risk Modelling

<img src="Supporting_Images/PRIME-CVD_Overview.png" width="600"/>

Hey, hello, and Kia Ora!

In this post, we introduce **PRIME-CVD Data Asset 1**, a clean, analysis-ready synthetic cohort designed specifically for teaching cardiovascular risk modelling, exploratory data analysis, and causal reasoning in medical informatics.</br>
Unlike toy datasets, PRIME-CVD preserves realistic population structure, socioeconomic gradients, and clinically meaningful imbalance — while remaining fully synthetic and safe for classroom use.

This post mirrors how we introduce the dataset **live in class**: by inspecting its shape, columns, and distributions before doing *any* modelling.

---

## Data Provenance

PRIME-CVD is a **fully synthetic cohort**, generated *de novo* from a hand-specified causal directed acyclic graph (DAG) parameterised using publicly available Australian population statistics (ABS, AIHW) and published epidemiologic effect estimates.</br>

No real patient-level electronic medical record (EMR) data are used at any stage. Every individual, covariate, and outcome is simulated deterministically from aggregate priors, ensuring negligible disclosure risk while preserving realistic joint structure.

Data Asset 1 represents a **primary-prevention cardiovascular population** of 50,000 simulated adults, designed to resemble contemporary EMR-based cohorts used in 5-year CVD risk modelling studies.

---

## Dataset Shape and Scope

We begin our live classroom demo exactly as analysts would encounter a new dataset — by asking three simple questions:

1. *How big is it?*
2. *What variables does it contain?*
3. *Which columns matter most for downstream analysis?*

```
Rows × Columns: 50,000 × 13
```

Each row corresponds to one simulated individual, with one-row-per-patient structure suitable for immediate exploratory analysis and survival modelling.

---

## Baseline Variable Structure

The cohort is intentionally compact, with variables grouped into clear conceptual blocks:

| **Category**                    | **Attribute**          | **Type**      | **Notes**               |
| ------------------------------- | ---------------------- | ------------- | ----------------------- |
| **Demographic & Socioeconomic** | Age                    | Numeric       | Continuous (years)      |
|                                 | IRSD quintile          | Ordinal (1–5) | Area-level disadvantage |
| **Behavioural**                 | Smoking status         | Categorical   | non / ex / current      |
| **Anthropometric**              | Body mass index (BMI)  | Numeric       | kg/m²                   |
| **Chronic Conditions**          | Diabetes               | Binary        | 0 / 1                   |
|                                 | Chronic kidney disease | Binary        | 0 / 1                   |
|                                 | Atrial fibrillation    | Binary        | 0 / 1                   |
| **Physiological Measures**      | HbA1c                  | Numeric       | %                       |
|                                 | Systolic BP            | Numeric       | mmHg                    |
|                                 | eGFR                   | Numeric       | mL/min/1.73m²           |
| **Outcome**                     | CVD event              | Binary        | 5-year event            |
|                                 | Follow-up time         | Numeric       | years                   |

This design allows students to immediately distinguish:

* exposures vs outcomes,
* baseline risk factors vs biomarkers,
* and covariates suitable for adjustment vs stratification.

---

## First Look: Distributions and Plausibility

Before fitting any models, we examine univariate distributions — a habit we explicitly teach.</br>
Histograms and boxplots reveal:

* **Age**: approximately normal, centred around mid-life, bounded at 18–90
* **BMI**: right-skewed, with realistic upper tails
* **SBP**: bell-shaped with hypertensive extremes
* **eGFR**: left-skewed decline consistent with ageing and CKD
* **HbA1c**: bimodal structure reflecting diabetic vs non-diabetic subpopulations
* **Follow-up time**: concentrated near 5 years with administrative censoring

Outliers are present — deliberately — to support discussions about robustness, transformation, and data quality checks.

---

## Categorical Structure and Imbalance

PRIME-CVD is **not class-balanced**, by design.

```
──────────────────────────────────────────────────────────────
    Diabetes (Yes) ................. ~7 %
    CKD (Yes) ...................... <1 %
    AF (Yes) ....................... <1 %
    Current smokers ................ ~10 %
    CVD events (5-year) ............ ~4 %
──────────────────────────────────────────────────────────────
```

This imbalance reflects real primary-prevention populations and provides a natural setting to discuss:

* rare-event modelling,
* calibration,
* and subgroup-specific risk.

Students quickly see why naive accuracy metrics fail in this context.

---

## Missingness and Data Quality

Although Data Asset 1 is “clean”, it is **not perfect**.</br>
We explicitly demonstrate how to inspect missingness:

* identify columns with any missing values,
* prioritise clinically important variables,
* and decide which fields require cleaning before modelling.

This sets the stage for Data Asset 2, where the same cohort is deliberately decomposed into messy EMR-style tables.

---

## Teaching Philosophy

PRIME-CVD Data Asset 1 represents **what analysts wish they had**:

* one row per patient,
* coherent variable naming,
* known causal structure,
* and transparent assumptions.

It exists to let students focus on:

* exploratory data analysis,
* stratification,
* survival modelling,
* and interpretation — *before* confronting EMR chaos.

In later labs, students work backwards from the relational EMR representation to recover this structure, reinforcing the full analytic lifecycle.

---

## Closing Thoughts

We introduce PRIME-CVD Data Asset 1 live, with Python, not slides.</br>
By the end of the first 30 minutes, students know:

* what variables exist,
* which distributions look reasonable,
* where imbalance lives,
* and why causal assumptions matter.

Everything else — cleaning, reconstruction, modelling, fairness — builds naturally from this foundation.

Cheers,</br>
- Nic

(Last edit: 2026-01-08)

