# Bitcoin LSTM Forecast — Streamlit Deployment

## Streamlit Community Cloud deployment

Deploy this folder as the repository root. The Streamlit entrypoint is `app.py`, and `requirements.txt` is in the same directory. The `models/` and `data/` directories must remain beside `app.py`.

In Streamlit Community Cloud, choose:

```text
Main file path: app.py
Python version: 3.11
```

Select Python 3.11 in the deployment dialog’s **Advanced settings**. Do not rely only on `runtime.txt` if the deployment interface allows an explicit Python selection.

The project structure must be:

```text
app.py
features.py
requirements.txt
runtime.txt
models/
  config.json
  model_v1.keras
  fscaler_v1.pkl
data/
  btc_dataset_with_sentiment.csv
```

The requirements file must contain `plotly`, not `plotl`:

```text
streamlit
tensorflow-cpu
scikit-learn
joblib
pandas
numpy
yfinance>=0.2.54
ta
plotly
```

## If keeping the nested repository layout

If the GitHub repository contains a `btc_app/` subdirectory, deploy `btc_app/app.py` as the main file. Keep `btc_app/requirements.txt` beside it, and keep the `btc_app/models/` and `btc_app/data/` directories unchanged.

Do not deploy the parent directory as if it contained `app.py` and `requirements.txt`; those files are inside `btc_app/`.

## Important note

The model artifact was saved in Keras 3 format. The project therefore requires a current TensorFlow/Keras runtime. Do not remove `tensorflow-cpu` from `requirements.txt` unless the model-loading code is changed to use another compatible runtime.
