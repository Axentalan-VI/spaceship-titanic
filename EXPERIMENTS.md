# Experiments

Scored submissions to
[Spaceship Titanic](https://www.kaggle.com/competitions/spaceship-titanic).
Metric: accuracy, higher is better. Ten submissions scored; the table shows the
spread rather than every near-duplicate.

| ID | Date | Variant | Public LB | Notes |
|----|------|---------|-----------|-------|
| E010 | 2026-04-08 | best of the run | **0.80827** | best |
| E007 | 2026-04-07 | XGBoost | 0.80593 | |
| E006 | 2026-04-08 | CatBoost | 0.80383 | |
| E005 | 2026-04-08 | average v3 | 0.80360 | |
| E004 | 2026-04-08 | stacking | 0.80266 | |
| E003 | 2026-04-08 | LightGBM tuned v2 | 0.80243 | |
| E002 | 2026-04-08 | XGBoost tuned v2 | 0.80219 | |
| E001 | 2026-04-07 | ensemble v2 | 0.80102 | |

## What this table says

**The entire spread is 0.0073** - eight submissions inside three quarters of a
percentage point. On ~4,300 test rows that is a handful of flipped predictions,
which is to say: these models are the same model.

Ranking them by public score, as happened at the time, is reading noise. A
recorded CV mean and standard deviation per variant would have said so
immediately, and would have redirected the effort to features instead of to a
seventh ensemble.
