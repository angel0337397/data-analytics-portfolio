# 02 · Eastville Real Estate Analysis
**[← Back to Portfolio](../README.md)**

> Exploratory Data Analysis · Python · Correlation · Effect Size  
> Emory University — ISOM 352: Business Analytics  
> Author: Zixuan Li

---

## Overview

Comprehensive EDA of 108 Eastville homes examining the statistical relationships between home prices, square footage, house style, and other property features. Combines single-variable analysis, two-variable comparisons, t-tests, and Cohen's d effect size to identify the true drivers of residential property value.

## Dataset

- **108** homes · **12** attributes
- 10 numeric variables, 2 categorical (`style`, `school`)
- No missing values
- Average home price: ~$341,395

## Key Findings

| Variable | Relationship with Price | Details |
|---|---|---|
| Square footage | Strong positive (r = 0.772) | Primary price driver |
| Ranch style | Significantly higher price | Large practical effect (Cohen's d) |
| Cape Cod vs. Two-story | No significant difference | p = 0.65, d = −0.115 |
| Price clustering | $300K–$400K most common | Right-skewed distribution |

**Headline:** Square footage is the strongest driver of home price in Eastville. House style matters — Ranch commands a premium — but size is the primary value determinant.

## Methodology

### 1. Data Importation & Exploration
- 108 rows, 12 columns; no missing values
- Identified numeric and categorical variable types

### 2. Single Variable Analysis
**Price:** Histogram + box plot; mean ($341,395) vs. median ($331,715) comparison  
**Style:** Frequency + relative frequency tables; bar chart of style distribution

### 3. Two Variable Analysis

**Price vs. Style**
- Mean/median price by style
- Bar chart + Seaborn box plots
- Independent t-tests between all three style pairs (Cape Cod, Ranch, Two-story)
- Cohen's d effect size for practical significance

**Price vs. Square Footage**
- Engineered `price_per_sqft` feature
- Pearson correlation: r = 0.772 (strong positive)
- Scatter plot with r annotation
- Distribution analysis of $/sqft

## Files

```
02_real-estate-analysis/
├── README.md
└── eastville_analysis.ipynb        ← Full Python analysis
```

## Libraries

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from scipy import stats
import statsmodels.api as sm
```

## Statistical Methods Used

| Method | Purpose |
|---|---|
| Descriptive statistics | Price and style distribution |
| Independent t-test | Price differences between house styles |
| Cohen's d | Practical significance of style price gaps |
| Pearson correlation | sqft–price relationship strength |
| Feature engineering | Price per square foot metric |

---

**[← Back to Portfolio](../README.md)** · **[→ Next Project: Hotel Sales Driver](../03_hotel-sales-driver/)**
