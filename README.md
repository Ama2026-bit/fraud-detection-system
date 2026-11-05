# Financial Fraud Detection System

A Jupyter Notebook project that trains and evaluates a Random Forest classifier on the Credit Card Fraud Detection dataset. The notebook demonstrates dataset inspection, a stratified train/test split, classification metrics, visualizations, feature importance, and a sample prediction function.

## Repository contents

```text
.
├── main.ipynb                         # End-to-end training and evaluation notebook
├── models/
│   └── fraud_detection_model.pkl      # Serialized model produced by the notebook
├── requirements.txt                   # Python packages used by the notebook
└── .gitignore                         # Excludes local data, environments, and caches
```

The dataset and local virtual environment are intentionally not included. Download the dataset separately and place it at `data/creditcard.csv` before running the notebook.

## Dataset

This project uses the [Credit Card Fraud Detection dataset](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud) from Kaggle. The notebook expects a `Class` target column and reads the file from `data/creditcard.csv`. The dataset is highly imbalanced: the recorded notebook run contains 284,807 transactions, with 492 labeled as fraud. The dataset is not bundled with this repository; follow the dataset provider's terms when obtaining and using it.

## Setup

Use Python 3.9 or later, then install the notebook dependencies:

```bash
python -m venv .venv
```

Activate the environment and install packages:

```bash
# Windows PowerShell
.venv\Scripts\Activate.ps1

# macOS / Linux
source .venv/bin/activate

python -m pip install --upgrade pip
pip install -r requirements.txt
```

Download `creditcard.csv` from Kaggle, then place it at:

```text
data/creditcard.csv
```

## Run the notebook

```bash
jupyter notebook
```

Open `main.ipynb` and run the cells from top to bottom. The notebook trains a `RandomForestClassifier` with 100 trees, balanced class weights, and a fixed random seed. It saves the trained estimator to `models/fraud_detection_model.pkl`.

## Recorded evaluation

The notebook's saved output records a stratified 80/20 split with `random_state=42`. On the 56,962-row test set, it reports:

| Metric | Recorded result |
| --- | ---: |
| Fraud precision | 0.91 |
| Fraud recall | 0.79 |
| Fraud F1 score | 0.84 |
| Average precision (PR AUC as labeled in notebook) | 0.8629 |
| Confusion matrix (normal/fraud rows and columns) | `[[56856, 8], [21, 77]]` |

These are the results saved in the notebook, not a guarantee of future performance. They depend on the dataset, split, and software versions. In fraud detection, accuracy alone can obscure missed fraud because the classes are highly imbalanced; review precision and recall together for the intended use.

## Model artifact

`models/fraud_detection_model.pkl` is the serialized estimator included with the project. The notebook also recreates it when run. Pickle-based model files can execute code when loaded; only load this artifact from a source you trust. For model deployment, validate inputs, monitor performance, and assess operational and regulatory requirements before use.

## Scope

This repository contains a notebook-based demonstration. It does not include a web dashboard, API, or production monitoring system.
