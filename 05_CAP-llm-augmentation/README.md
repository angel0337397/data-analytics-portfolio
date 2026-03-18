# 05 · Causal Alignment Prompting (CAP) — LLM Synthetic Survey Augmentation

**[← Back to Portfolio](../README.md)**

> Causal Inference · Python · RCT Design · LLM Augmentation · Hypothesis Testing · OLS Regression  
> Emory University — QTM 385: Experimental Methods (AI/NLP)  
> Team: Zixuan Li,Mingke Tian, Nicole Chen, Anny Huang

---

## Overview

Can large language models act as synthetic survey respondents to augment small randomized experiments — without distorting causal estimates? We designed and tested **Causal Alignment Prompting (CAP)**, a preregistered augmentation framework for policy-framing RCTs. Using a gain vs. loss framing experiment (N = 253 human respondents), we generated CAP-aligned synthetic respondents and applied a rigorous equivalence testing protocol to determine whether augmentation preserved the human-only treatment effect. The answer: it didn't — and our framework caught it before it could mislead inference.

---

## Research Design

- **Two-arm RCT**: Gain vs. Loss policy framing, stratified randomization on Education × Gender × Ideology
- **Human sample**: N = 253 (main) + N = 88 pilot for CAP calibration
- **Synthetic respondents**: k = 3 generated per human participant per stratum × arm
- **Down-weighting scheme**: ω ∈ {0, 0.2, 0.35, 0.5, 0.7}, where ω = 0 is the confirmatory human-only estimand
- **Preregistered equivalence band**: augmented τ(ω) must stay within ±0.15 SD of human-only τ(0)

---

## Outcomes

| Outcome | Type | Description | Role |
|---|---|---|---|
| Y1: Policy Support | Ordinal (1–7) | 7-point Likert on policy support | Primary |
| Y2: Donation | Binary (0/1) | Willingness to donate $10 to advocacy group | Secondary |
| Y3: Knowledge | Integer (0–5) | Sum of 5 factual policy items | Secondary |

---

## Key Findings

| Finding | Result |
|---|---|
| Gain vs. Loss framing effect on Y1 (τ(0)) | +0.63 points (p ≈ 0.054, approaches significance) |
| Framing effect on Y2 (Donation) | ≈ 0, p >> 0.10 — no detected effect |
| Framing effect on Y3 (Knowledge) | ≈ 0, p ≈ 0.89 — no detected effect |
| CAP augmentation equivalence | ❌ FAILED — τ(ω) declines to ~0.19 as ω increases |
| Standard error under augmentation | Widens (0.33 → 0.37) — no precision gain |
| HTE (ideology, gender, education) | Directional but noisy; unreliable under augmentation |

**Headline:** Gain framing directionally increases policy support, but LLM-generated synthetic respondents failed to preserve the causal estimand under CAP — validating why the framework's pre-registration criteria exist in the first place.

---

## Why CAP Failed: Diagnostic Findings

- **Under-dispersed responses**: Synthetic data showed less variance than human data
- **Over-confidence**: LLMs clustered toward mid-scale values, avoiding extremes
- **Inconsistent subgroup effects**: HTE patterns were amplified or flipped relative to human-only estimates
- **Marginal distributions**: Did not fully match human distributions despite calibration attempts

> The framework worked exactly as intended — it caught a problematic augmentation *before* it could mislead inference.

---

## Methodology

1. **Pre-Analysis Plan (PAP)** — Fully preregistered hypotheses, estimands, equivalence bands, and decision rules before data analysis
2. **Pilot Calibration** — Used N = 88 pilot sample to derive empirical bands for CAP temperature tuning and rejection sampling
3. **CAP Alignment** — Persona prompts encode demographic priors; temperature grid {0.2, 0.7, 1.0} with rejection sampling to match pilot-derived moment bands
4. **Confirmatory Analysis** — Post-stratified difference-in-means (ω = 0) with HC2 robust SEs clustered by stratum
5. **Augmented Estimation** — Mixture estimands at ω ∈ {0.2, 0.35, 0.5, 0.7}; ω selected by validation RMSE subject to TOST equivalence
6. **Validation Suite** — Pattern replication, effect-direction coherence (bootstrap), external benchmarking, multi-model sensitivity
7. **Robustness Checks** — MICE for missing data (20 imputations), IPW for attrition, ITT primary with CACE via 2SLS
8. **HTE Analysis** — Ideology × Gender × Education interactions; Holm–Bonferroni correction for confirmatory, BH-FDR for exploratory

---

## Sample & Data Quality

| Metric | Value |
|---|---|
| Started | 300 respondents |
| Completed | 253 respondents |
| Attrition rate | 15.7% (no differential attrition by arm) |
| Compliance rate | 93% |
| Missing Y1 | 15.7% |
| Missing Y2 | 20.3% (mostly declined donation option) |

---

## Files

```
05_CAP-llm-augmentation/
├── README.md
├── CAP_Analysis_Complete_WITH_OUTPUTS.ipynb   ← Full Python analysis with outputs
├── PAP.pdf                                     ← Pre-Analysis Plan (preregistered)
└── 385_presentation.html                       ← Final presentation deck
```

---

## Libraries

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import statsmodels.api as sm
from scipy import stats
from sklearn.experimental import enable_iterative_imputer
from sklearn.impute import IterativeImputer  # MICE
```

---

**[← Back to Portfolio](../README.md)** · **[→ Next Project](../06_next-project/)**
