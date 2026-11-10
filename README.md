# Treatment Effect Estimator — Apify sample data

Public sample data for the **Treatment Effect Estimator** Actor on Apify Store. This is a
companion repo, not the Actor's source code.

## Contents

- `samples/sample_small.csv` — 500 fully synthetic patients (no real people). Used as the Actor's
  default (prefill) input.

| Column | Description |
|---|---|
| `patient_id` | Unit identifier |
| `age` | Age in years (25–79) |
| `sex` | `F` or `M` |
| `baseline_score` | Symptom score before treatment (higher = worse) |
| `treated` | 1 = treated, 0 = control |
| `outcome` | Symptom score after treatment (higher = worse) |

The data is built with a known effect: the treatment lowers the score by about 2 points
(sample average effect: −1.97), more in older patients. Older patients and patients with a
worse baseline are more likely to be treated, so the naive treated-minus-control difference
is **+2.14** and wrongly suggests the treatment is harmful. Adjusting for `age`, `sex` and
`baseline_score` recovers the true negative effect.

## Use it with the Actor

| Input | Value |
|---|---|
| CSV URL | `https://raw.githubusercontent.com/KunakAI/treatment-effect-estimation-apify-resources/main/samples/sample_small.csv` |
| Treatment column | `treated` |
| Outcome column | `outcome` |
| Covariate columns | `age`, `sex`, `baseline_score` |

## License

The sample data is released under CC0 1.0 (public domain).
