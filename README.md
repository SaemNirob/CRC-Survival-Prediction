# Explainable and Uncertainty-Aware Machine Learning for 3-Year Colorectal Cancer-Specific Mortality Risk Classification

**Repository author:** Saem Mohammad Nirob  
**Study design:** SEER-based temporal validation study  
**Data years:** 2018–2020  
**Development cohort:** diagnosis years 2018–2019  
**Temporal test cohort:** diagnosis year 2020  
**Prediction horizon:** 36 months  
**License:** MIT (see [`LICENSE`](LICENSE))

This repository contains the analysis notebook and computational documentation accompanying the study *Explainable and Uncertainty-Aware Machine Learning for 3-Year Colorectal Cancer-Specific Mortality Risk Classification: A SEER-Based Temporal Validation Study*.

## Repository contents

```text
CRC-Survival-Prediction/
├── README.md
├── LICENSE
├── CITATION.cff
├── AUTHORS.md
├── .zenodo.json
├── requirements.txt
├── environment.yml
├── .gitignore
├── data/
│   └── README.md
├── docs/
│   ├── CODE_AVAILABILITY_STATEMENT.md
│   ├── REPRODUCIBILITY.md
│   └── CRC_CSS_analysis.html
├── notebooks/
│   └── CRC_CSS_analysis.ipynb
└── results/
    ├── tables/
    └── figures/
```

## Study workflow

The notebook contains 17 analysis sections: environment setup; data loading; cohort and outcome definition; predictors and preprocessing; development/test split and checks; descriptive statistics; evaluation functions; model development and selection; calibration and temporal test performance; staging baselines and decision curve analysis; stage-wise, subgroup and predictor-set analyses; sensitivity analyses; prediction sets; SHAP explainability; secondary analyses; figures; and reproducibility checks.

Five classifiers are compared: logistic regression, random forest, XGBoost, LightGBM and CatBoost. The notebook reports a headline AUC-ROC of **0.9104** (95% bootstrap CI **0.906–0.914**) and AUC-PR of **0.8454** in its saved outputs. These are existing notebook outputs, not a guarantee of fresh-run reproduction without the same authorized data, software versions and execution conditions. AUC-ROC is a discrimination metric and must not be described as 91.04% accuracy.

## Data availability and access

The SEER patient-level dataset is **not included**. The notebook requires an authorized SEER*Stat case-listing text export covering 2018–2020, named `NEW_CRC_2018-2020.txt` by default. Place it in `data/`, or set the `SEER_DATA_FILE` environment variable. The notebook checks the expected path whether launched from the repository root or from `notebooks/`.

Obtain the data through the relevant SEER access process and comply with all applicable data-use terms. Do not commit patient-level records, identifiers, restricted data, or any data you are not authorized to redistribute. See [`data/README.md`](data/README.md).

## Environment and execution

The supplied notebook records Python **3.10.21** and the package versions pinned in `requirements.txt`. Platform-specific compatibility, especially for `scikit-survival`, should be checked before installation.

Using Conda:

```bash
conda env create -f environment.yml
conda activate crc-survival
jupyter lab
```

Or using pip in a Python 3.10 environment:

```bash
python -m pip install -r requirements.txt
jupyter lab
```

Open `notebooks/CRC_CSS_analysis.ipynb` and run all cells from top to bottom. The notebook writes generated figures to the repository-level `results/` directory. The authorized SEER export must be available before execution.

## Methodological and interpretation notes

- The 2020 cohort is a temporal test cohort, not an independent external validation cohort.
- The analysis describes its 21-feature set as *pretreatment-approximate*, not strictly pretreatment, because some SEER-derived fields may contain pathology or post-operative information.
- Hyperparameter tuning and model selection use the same cross-validation folds; consequently, the cross-validated selection estimate may be optimistic. The temporally held-out 2020 cohort is the main test set.
- The notebook's final reproducibility assertions check consistency of refitting and calibration. They do not establish external validity, clinical utility or readiness for clinical deployment.
- Clinical use would require appropriate independent validation and prospective evaluation.

## Outputs

The notebook generates publication-oriented figures at 600 dpi, including ROC/calibration, decision curve, SHAP, cumulative incidence, precision-recall and Kaplan–Meier figures. Tables are displayed in notebook outputs. The `results/tables/` and `results/figures/` directories are tracked as placeholders; run the notebook and export the final tables/figures before attaching them as journal supplements.

## Citation

Citation metadata are provided in [`CITATION.cff`](CITATION.cff). Once the public repository is created, archive the release with Zenodo to obtain a version-specific DOI, then update the manuscript code-availability statement with the actual GitHub URL and DOI. The `.zenodo.json` file provides draft metadata for the archive; verify it in Zenodo before publishing.

## Before journal submission

1. Run the complete notebook against the exact authorized SEER export used for the manuscript.
2. Reconcile all cohort counts, tables, figures and metrics with the final manuscript and supplement.
3. Confirm the data-use permissions, ethics/IRB statement, consent/waiver, funding, conflicts of interest and author-contribution statements with the study team.
4. Review the full Git history and repository contents for restricted data, identifiers, credentials and accidental temporary files.
5. Confirm the MIT license is appropriate for all code contributors and included materials.
6. Create a versioned GitHub release and archive that exact release with Zenodo. Use the DOI for the archived version, not a placeholder or a generic Zenodo landing page.
7. Replace the placeholders in [`docs/CODE_AVAILABILITY_STATEMENT.md`](docs/CODE_AVAILABILITY_STATEMENT.md) only after the public URL and DOI exist.

This repository is a code and documentation package. It is not, by itself, evidence that the analysis has been independently reproduced or that all journal submission requirements have been met.
