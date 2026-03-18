# 01 · Tipping Behavior — Regression Analysis
**[← Back to Portfolio](../README.md)**

> Statistical Analysis · Python · OLS Regression · Hypothesis Testing  
> Emory University — Business Analytics  
> Team: Zixuan Li, Sam Grinberg, Grant Lichtman, Natalie Ronen

---

## Overview

End-to-end Python analysis of 244 restaurant tables across 7 days. Built three multiple OLS regression models to identify what truly drives tip amounts — controlling for total bill, party size, day, and shift. Includes statistical significance testing, effect size analysis, and an executive summary deck for non-technical stakeholders.

## Dataset

- **244** restaurant tables · **7 days** · Lunch and Dinner shifts
- Features: total bill, tip amount, sex, smoker, day, time, party size

## Key Findings

| Finding | Result |
|---|---|
| Every $1 increase in total bill | +$0.093 in tip (p < 0.05) |
| Every additional party member | +$0.187 in tip (p < 0.05) |
| Dinner vs. Lunch tip *amount* | Dinner ~13.7% larger |
| Dinner vs. Lunch tip *rate* | No significant difference (p = 0.51) |
| Day of week effect | Not significant (p > 0.05) after controlling for bill & size |
| Gender / smoking status | No predictive power (p > 0.05) |

**Headline:** Bill size is the primary driver of tip amount. Guests tip at roughly the same *percentage* regardless of time, day, or demographics.

## Methodology

1. **Data Processing** — Removed PII columns; created dummy variables for categorical features
2. **Descriptive Analytics** — Mean/median tips by meal time, party size, and day; box plots and bar charts
3. **Hypothesis Testing** — Independent samples t-tests comparing lunch vs. dinner tip rates
4. **Correlation Analysis** — Pearson r between party size, bill size, and tip amount
5. **Multiple Regression** — Three OLS models, selected best fit by R² and significance
6. **Executive Report** — Non-technical deck with 3 key insights, myth-busting analysis, and action plan

## Files

```
01_tipping-behavior/
├── README.md
├── tipping_analysis.ipynb          ← Full Python analysis
└── executive_report.pptx           ← Stakeholder summary deck
```

## Libraries

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import statsmodels.api as sm
from scipy import stats
```

---

**[← Back to Portfolio](../README.md)** · **[→ Next Project: Real Estate Analysis](../02_real-estate-analysis/)**
