<!-- Logo and Branding -->
<p align="left">
  <img src="Nic4Jt_NotYetComplete.png" alt="Cellular Scale Model Logo" width="260"/>
</p>

---

# About This Project

Cellular Scale Model (CSM) is a prototype protein large language–model (PLLM) pipeline
for enhancing variant interpretation in cancer.

It builds on the pretrained ESM-2 model and fine-tunes it on human, cancer-relevant
variants so that researchers can:</br>
- compare evolutionary vs cellular views of a mutation (ESM-2 vs CSM),
- visualise full mutational landscapes with heatmaps, and
- explore how CSM behaves on ClinVar-labelled variants (benign, pathogenic, VUS).

This repository accompanies the Honours thesis:</br>
“Enhancing Variant Interpretation in Cancer Using Protein Large Language Models” – Jaime Taitz (UNSW, 2025)

---

<!-- Side-by-side layout: text and illustration -->
<table>
<tr>
<td width="60%">

### Key Features

- ESM-2 + LoRA</br>  
  Parameter-efficient fine-tuning of the 650M-parameter ESM-2 model.

- Cancer-aware scoring</br>  
  Compute log-likelihood ratios (LLRs) and Δ-scores (CSM − ESM-2) for
  mutations of interest.

- ClinVar integration</br>  
  Simple utilities for aligning model scores with ClinVar clinical
  significance labels.

- Visual diagnostics  
  - global variant-effect heatmaps  
  - delta-score kernel density plots  
  - CSM vs ESM-2 scatterplots

</td>

</tr>
</table>

---

## Quick Start

1. **Clone the repo**

```bash
git clone https://github.com/<your-org>/<your-repo>.git
cd <your-repo>
