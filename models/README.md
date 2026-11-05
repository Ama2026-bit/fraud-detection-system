# Saved model artifact

`fraud_detection_model.pkl` is the serialized `RandomForestClassifier` produced by `main.ipynb`. To recreate it, run the notebook through the model training and save cells using the separately obtained dataset at `data/creditcard.csv`.

Only load pickle-based model files from sources you trust. The notebook can regenerate this artifact when rerun.
