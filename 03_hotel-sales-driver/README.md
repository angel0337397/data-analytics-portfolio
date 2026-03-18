# 03 · Hotel Revenue Sales Driver Analysis
**[← Back to Portfolio](../README.md)**

> Data Analysis · Python · Revenue Analytics  
> Author: Zixuan Li

---

## Overview

Python analysis identifying and quantifying the key drivers of hotel sales revenue. Explores relationships between occupancy rates, pricing strategy, seasonality, and booking channels to surface actionable revenue optimization insights.

## Key Questions

- Which booking channels generate the highest revenue per booking?
- How does seasonality affect occupancy and average daily rate (ADR)?
- What is the relationship between lead time, cancellation rate, and revenue?
- Which hotel and room type combinations deliver highest value?

## Methodology

1. **Data Cleaning** — Handled missing values, engineered revenue and occupancy features
2. **Exploratory Analysis** — Distribution analysis of key revenue metrics
3. **Segment Analysis** — Revenue by booking channel, room type, and season
4. **Driver Identification** — Correlation analysis and feature importance
5. **Visualization** — Seasonality heatmaps, scatter plots, segment bar charts

## Files

```
03_hotel-sales-driver/
├── README.md
└── hotel_sales_analysis.ipynb      ← Full Python analysis
```

## Libraries

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

---

**[← Back to Portfolio](../README.md)** · **[→ Next Project: AI Bidding Optimization](../04_ai-bidding-optimization/)**
