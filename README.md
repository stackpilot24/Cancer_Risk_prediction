# Cancer Risk Level Predictor

A Streamlit web app that predicts an individual's **cancer risk level** — `Low`, `Medium`, or `High` — from 17 demographic, lifestyle, and health features.

## Model

- **Final model:** Optuna-tuned, class-weighted **XGBoost**
- **Test accuracy:** ~0.86 &nbsp;|&nbsp; **Macro-F1:** ~0.72
- Trained on 17 features (the leaky `Overall_Risk_Score` and identifier/`Cancer_Type` columns were dropped to prevent data leakage).
- Class weighting is used to improve recall on the minority **High-risk** class.

| Metric | High | Low | Medium |
|---|---|---|---|
| Recall | 0.50 | 0.78 | 0.90 |

## Features used (in order)

`Age, Gender, Smoking, Alcohol_Use, Obesity, Family_History, Diet_Red_Meat,
Diet_Salted_Processed, Fruit_Veg_Intake, Physical_Activity, Air_Pollution,
Occupational_Hazards, BRCA_Mutation, H_Pylori_Infection, Calcium_Intake, BMI,
Physical_Activity_Level`

## Run locally

```bash
pip install -r requirements.txt
streamlit run app.py
```

Then open http://localhost:8501.

## Usage

- **Manual input** — enter a single patient's features in the sidebar and click *Predict*.
- **Upload CSV (batch)** — upload a CSV with the feature columns above; the app returns predictions plus per-class probabilities and a downloadable results file.

## Files

| File | Purpose |
|---|---|
| `app.py` | Streamlit application |
| `model_xgb_new.pkl` | Trained XGBoost model |
| `label_encoder.pkl` | Encodes/decodes the `Risk_Level` target |
| `feature_names.pkl` | Ordered list of the 17 model features |
| `cancer-risk-factors.csv` | Dataset |
| `Cancer_Risk_Prediction.ipynb` | Training & EDA notebook |

## Disclaimer

This is an educational/portfolio project trained on a synthetic dataset. It is **not** a medical device and must not be used for real clinical decisions.
