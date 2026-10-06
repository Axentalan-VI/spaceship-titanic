# Progress

## Current status

Complete. **0.80827 public accuracy**, the best of 10 scored submissions. The
competition has no deadline.

Tabular ensemble: cabin split into deck/num/side, a group id derived from
`PassengerId`, spend aggregates and zero-spend flags, a CryoSleep consistency
check, and group-aggregate features, fed to LightGBM, XGBoost, CatBoost and a
small MLP, then rank-averaged and stacked.

## Last session (2026-10-06)

- Recorded the measured result in the README; it had none.
- Added this file and `EXPERIMENTS.md`.

## Open issues

- **All ten submissions land within 0.006 of each other** (0.801-0.808), so the
  differences between the variants are noise, not a ranking. No CV score was
  recorded, which is exactly what would have shown that at the time.

## Next steps (prioritized)

1. If revisited: record CV mean and standard deviation per variant and compare
   differences against the standard deviation. On this spread, most of the
   submissions were indistinguishable.

## Decisions & rationale

- Gradient-boosted trees as the core, because the features are a mix of numeric
  and categorical with informative missingness, which they handle natively.
- The group id from `PassengerId` is the strongest engineered feature: people
  travelling together share an outcome.
