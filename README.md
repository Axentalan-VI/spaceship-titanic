# Spaceship Titanic

Kaggle competition: [Spaceship Titanic](https://www.kaggle.com/competitions/spaceship-titanic).

Predict whether each passenger was **transported to an alternate dimension**
(binary classification, metric = accuracy). Mid-difficulty tabular problem
with mixed numeric/categorical features and informative missingness.

## Approach

Standard tabular ensemble pipeline:

1. **Feature engineering** — split `Cabin` into deck/num/side, derive a
   `Group` id from `PassengerId`, age buckets, total spend, zero-spend flags,
   `CryoSleep` consistency check, group-aggregate features.
2. **Models** — LightGBM, XGBoost, CatBoost (gradient boosted trees handle
   the mix of numeric + categorical natively) and a small MLP for the NN
   notebook.
3. **Ensembling** — rank-average and stacking across the boosted models;
   submissions for each variant are kept under `submissions/`.

## Layout

```
notebooks/
  00_eda.ipynb              exploratory data analysis
  01_submission_demo.ipynb  minimal end-to-end baseline
  spaceship_titanic_v2.ipynb LGB / XGB / CatBoost ensemble
  spaceship_titanic_nn.ipynb tabular MLP variant
data/                        raw competition data (gitignored)
models/                      saved boosters / checkpoints (gitignored)
submissions/                 per-model submission CSVs (gitignored)
```

## Reproducing

1. Download `train.csv`, `test.csv`, `sample_submission.csv` from the
   competition page into `data/`.
2. Open the notebooks in order. Each is self-contained — features are
   recomputed inside the notebook, no external pipeline required.
3. The final submission is the ensemble produced by
   `spaceship_titanic_v2.ipynb` (saved as
   `submissions/submission_ensemble_v2.csv`).
