# PRIME-CVD Data Asset 2:</br> Designing EMR Reconstruction Assignments</br> with Presence-Only Diagnosis Data

<img src="https://github.com/NicKuo-ResearchStuff/Synthetic_Data_Related_Project_Staging/blob/main/chaptY/ImageStuff/ZFig_PRIME_CVD_Blog04.png" width="600"/>

Hey, hello, and Kia Ora!

In this post, we show how PRIME-CVD Data Asset 2 can be used to design assessment-ready assignments that test students’ ability to reason about EMR structure, diagnosis harmonisation, and disease prevalence construction -- long before any modelling takes place.

This entry is written for educators: lecturers, course convenors, and tutors teaching undergraduate or early postgraduate courses in health data science, medical informatics, or applied epidemiology.

Rather than focusing on exploratory analysis or prediction, the emphasis here is on reconstruction and interpretation -- specifically, how EMR-style data force analysts to make explicit, defensible choices when estimating something as seemingly simple as disease prevalence.

A fully worked reference solution (code and canonical outputs) is included alongside this post.

---

## Why EMR-Style Prevalence Matters in Assessment

In real-world health data analysis, prevalence is almost never observed directly.

Instead, analysts must ask:

* What counts as evidence of disease?
* Which diagnosis labels should be treated as equivalent?
* Are conditions mutually exclusive -- or overlapping?
* What does “absence” mean in a presence-only record?

These questions are fundamental to epidemiology and health services research, yet they are often invisible in teaching datasets, where disease indicators arrive pre-cleaned as binary columns.

PRIME-CVD Data Asset 2 is deliberately constructed to surface these issues.

It fragments a clean, causal cohort into EMR-style tables with:

* heterogeneous diagnosis strings,
* sparse and presence-only condition records,
* and no canonical disease columns.

This makes it particularly well-suited to assignments that assess judgement and reasoning, not just code execution.

---

## From EMR Tables to an Assignment-Ready Task

A simple but powerful assessment design begins with a constrained, reproducible cohort.

In this demonstration, we select:

* the 500 patients with the smallest synthetic identifiers from the EMR master table, and
* all linked diagnosis records from the chronic disease table.

Within this subset, only 47 diagnosis rows are present — immediately highlighting the sparsity and incompleteness of EMR problem lists.

Before any harmonisation, the most frequent diagnosis labels include:

* “Diabetes”
* “ICD9:250”
* “T2DM”
* “ICD10: E11”
* “High blood sugar”

alongside single-instance labels for chronic kidney disease and atrial fibrillation.

At this stage, there is no such thing as diabetes prevalence -- only diagnosis strings.

---

## Diagnosis Harmonisation as a Pedagogical Decision

To proceed, students must define explicit harmonisation rules.

In the reference solution, heterogeneous labels are collapsed into three canonical disease groups:

* Diabetes
* Chronic kidney disease (CKD)
* Atrial fibrillation (AF)

This step is intentionally normative rather than mechanical.
There is no single correct vocabulary -- only defensible ones.

Different choices (for example, whether to include “high blood sugar” as diabetes) would yield different prevalence estimates, making this an ideal assessment point for testing clinical and analytic judgement.

---

## What the Constructed Prevalence Looks Like

After collapsing diagnosis records to patient-level presence indicators, the following prevalence estimates emerge in the 500-patient demonstration cohort:

| Disease  | Prevalence (%) |
| -------- | -------------- |
| Diabetes | 91.3           |
| CKD      | 4.3            |
| AF       | 6.5            |

These values are not intended to reflect population burden.
Instead, they illustrate how prevalence in EMR data is constructed rather than observed.

Importantly, the summed prevalence exceeds 100%.

This is not an error.

---

## Why Prevalence Sums Exceed 100%

In EMR data, diagnoses are recorded as overlapping conditions, not mutually exclusive states.

Each prevalence estimate is calculated independently as the proportion of patients with any recorded evidence of that condition. A single patient may therefore contribute simultaneously to multiple disease categories -- for example, diabetes and atrial fibrillation.

As a result:

* prevalence estimates do not partition the cohort, and
* their sum has no meaningful upper bound.

This mirrors real EMR problem lists and reinforces a key methodological lesson for students: disease prevalence depends on definitions, linkage rules, and assumptions about comorbidity.

---

Cheers,</br>
\- Nic

(Last edit: 2026-01-20)
