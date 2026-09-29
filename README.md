# Rain prediction in Australia

> **Original version:** this README and some fixes were added in 2026. To see the project exactly as it was first built, browse commit [`a1bb746`](https://github.com/dianapaula19/rain-prediction-australia/tree/a1bb746c291d0ca17c4e38c90850251409af7dc1) (2021-10-03).

Will it rain tomorrow? Term project for *CEN 416 Data Mining* at Maltepe University (2021), by
Sabahattin Emirhan Sönmez and Paula-Diana Băcîrcea. We compare seven classifiers on the
[Rain in Australia](https://www.kaggle.com/datasets/jsphyg/weather-dataset-rattle-package) dataset:
about 145,000 days of weather observations from 49 Australian stations.

The full write-up is in the PDF report; the notebook has the code and all outputs.

## Method

1. **Cleaning:** drop rows without a label, remove duplicates, fill missing numbers with the
   column mean and missing categories with the most frequent value, label-encode categories,
   drop highly correlated columns (18 features remain).
2. **Balanced sample:** 15,000 rainy and 15,000 dry days, split 70/30 into train and test;
   features standardised with training-set statistics.
3. **Models:** each tuned with grid search over 10-fold cross-validation repeated 3 times.

## Results (test set, 9,000 days, balanced)

| Model | Accuracy |
|---|---|
| **Random forest** (max depth 30) | **79.7%** |
| Linear SVM | 78.6% |
| Logistic regression | 78.5% |
| k-nearest neighbours (k = 15, Manhattan) | 78.3% |
| Bagged decision trees | 75.7% |
| Gaussian naive Bayes | 75.0% |
| Decision tree | 72.5% |

## Running

```bash
pip install pandas scikit-learn seaborn matplotlib ydata-profiling ipywidgets jupyter
jupyter notebook
```

The dataset is included in `data/weatherAUS.csv`.
