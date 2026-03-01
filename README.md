# Airline Delay Data Pipeline & Analysis

## Project Overview

This project implements a **data pipeline** for analyzing airline delay data.  
The goal is to extract, clean, transform, and load the dataset for further analysis, and then generate meaningful visualizations and insights.

The dataset is sourced from [Kaggle – Airline Delay Data](https://www.kaggle.com/datasets/sriharshaeedala/airline-delay/data), containing **monthly airline arrival statistics** including flight counts, delays, and cancellations.

---

## Pipeline Steps

### 1. Extract

- The dataset was loaded from a CSV file using Pandas.
- Initial shape: `(171,665 rows, 21 columns)`.
- Columns include numeric counts, categorical identifiers, and arrival delays.

### 2. Transform

- **Cleaned missing values:**  
  - Null values were only ~0.26% of total rows; these were dropped.
- **Fixed data types:**  
  - Converted numeric columns to `Int64` for consistent calculations.
  - Converted categorical columns (`carrier`, `airport`, etc.) to `category` type.
- **Feature engineering:**  
  - Created `delay_rate = arr_del15 / arr_flights` to normalize delays relative to flight volume.
  - Binned `arr_delay` into `delay_category` with 4 categories:
    - `short_delay` (0–15 min)
    - `medium_delay` (16–60 min)
    - `long_delay` (61–180 min)
    - `extreme_delay` (>180 min)
  - This allows for meaningful comparisons across carriers, airports, and months.

### 3. Load

- The cleaned and feature-engineered dataset was saved as:

### 4. Visualizations

Correlation heatmap of numerical attributes
Distribution plots of key columns
Boxplot of delay rate by month
Scatter plot of arrivals vs total delay
Countplot of delay categories