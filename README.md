# Gait Condition Classification

## Problem Description

## Directory

[`eda.ipynb`](./eda.ipynb)

This file contains exploratory data analysis, in which we computed summary statistics, created visualizations, or performed miscellaneous transformations to the data.

[`manual_tabular_features.ipynb`](./manual_tabular_features.ipynb)

We attempted to manually engineer tabular features based on the time-series data, which could be used for various ML models that are not specifically designed for time-series data.

The engineered features correspond to three categories:
1. **Raw statistics:** summary statistics for the raw time-series data
2. **Differential statistics:** summary statistics for changes in the raw data
3. **Quarter statistics:** summary statistics for each quarter of time in the data

After our first attempt at using an SVM model on thr raw and differential statistics, we found that the accuracy seemed artifically high. We often produced an accuracy of `1.0`, although the accuracy was sometimes slightly lower depending on the training/testing split.

We decided to use the `tsfresh` library to produce tabular features instead. This library is more optimized at producing and selecting a variety of tabular time-series features.

This file is archived for reference, but we are no longer using it as an active part of our analysis pipeline.
