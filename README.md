# Explainable Machine Learning for Personalized Lung Cancer Treatment Response Prediction Using Clinical Data and Multi-Level Explainability

## 1. Project Overview

This project investigates the application of explainable machine learning to predict treatment-response categories in lung cancer patients using clinical data from the P4-LUCAT dataset.

The research compares multiple supervised machine learning algorithms, investigates class imbalance-handling strategies, and uses SHAP (SHapley Additive exPlanations) to interpret model predictions at global and class-specific levels.

## 2. Research Objectives

1. Predict six treatment-response categories.
2. Compare multiple supervised machine learning algorithms.
3. Address severe class imbalance.
4. Apply global and class-specific SHAP explanations.
5. Evaluate prediction reliability, particularly for minority response classes.

## 3. Dataset

**Dataset:** P4-LUCAT – Lung Cancer Diagnosis and Treatment Dataset.

- Original records: 1,242 patients
- Original features: 174 columns
- Patients with recorded first-treatment response: 888

The original patient-level dataset is not included in this repository.

**Dataset source:** https://medal.ctb.upm.es/projects/P4-LUCAT/

## 4. Model Configurations

Three feature configurations were evaluated using CatBoost.

| Model | Feature configuration |
|---|---|
| Model A | Clinical and demographic features |
| Model B1 | Clinical features + first treatment type |
| Model B2 | Clinical features + first treatment type + drug regimen |

## 5. Final Test Results

All three configurations were evaluated on the same held-out test set.

| Model | Accuracy | Macro F1 | Balanced Accuracy |
|---|---:|---:|---:|
| Model A | 39.89% | 0.2337 | 0.2415 |
| Model B1 | 44.94% | 0.2456 | 0.2777 |
| Model B2 | 46.63% | 0.2544 | 0.2871 |

Model B2 achieved the highest accuracy and Macro F1 among the three evaluated configurations. However, the improvement was modest, and performance remained uneven across response categories.

Model B2 recorded zero recall for the minority classes NE and NR on the test set.

## 6. Explainable AI

SHAP was used to investigate:

- Global feature importance.
- Class-specific feature contributions.
- Local explanations for individual predictions during the analysis.

SHAP values describe how features contribute to model predictions. They do not establish causal relationships.

## 7. Class Imbalance and Prediction Reliability

The study investigated class imbalance using approaches including random oversampling and class-weighted learning.

Minority-class predictions remained unreliable. Model B2 did not correctly identify any NE or NR cases in the test set.

Probability evaluation showed that Model B2's Brier score and log loss were approximately comparable to a class-prior baseline. Its predicted probabilities therefore showed no meaningful improvement over that baseline.

## 8. Technologies Used

- Python
- Pandas and NumPy
- Scikit-learn
- CatBoost
- XGBoost
- SHAP
- Imbalanced-learn
- Matplotlib and Seaborn
- Jupyter Notebook

## 9. Project Structure

```text
LungCancerResearch/
├── notebooks/
│   └── 01_data_understanding.ipynb
├── outputs/
│   ├── public_figures/
│   └── public_results/
├── requirements.txt
├── .gitignore
└── README.md
```

The repository contains selected aggregate results and figures. Raw patient-level data, trained model files, and unreviewed outputs are excluded.

## 10. Limitations

- The dataset has substantial class imbalance.
- Minority response categories remain difficult to predict.
- The availability of treatment-related features before treatment initiation has not been fully established.
- The results do not establish causal treatment effects.
- The models have not undergone independent external validation.
- The findings should not be used for clinical decision-making.

## 11. Author

**A. Saketh Ram**

Machine Learning | Explainable AI | Healthcare Analytics