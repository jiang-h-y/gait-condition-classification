# Gait Condition Classification

Gait refers to the specific pattern of walking, including the movement of the legs and joints over time.

## Problem Description
This project focuses on predicting/classifying three different walking conditions using lower-limb joint angle data. Our goal is to distinguish between unbraced walking, knee brace use, and ankle brace use based on movement patterns. Our analysis can understand human locomotion, track abnormal gait, improve rehabilitation, and guide the design of assistive devices.

## Directory

[`analysis.ipynb`](./analysis.ipynb)

[`eda.ipynb`](./eda.ipynb)

This file contains exploratory data analysis, in which we computed summary statistics, created visualizations, or performed miscellaneous transformations to the data.

[`/tabular`](./tabular)

This folder contains analyses in which we feature-engineered the time-series data to create tabular features. These tabular features can be used on general classifier models that are not specifically designed for time-series data, which allows us to use a greater variety of models.

[`/tabular/manual_tabular_features.ipynb`](./tabular/manual_tabular_features.ipynb)

We attempted to manually engineer tabular features.

The engineered features correspond to three categories:
1. **Raw Statistics:** summary statistics for the raw time-series data
2. **Differential Statistics:** summary statistics for changes in the raw data
3. **Quarter Statistics:** summary statistics for each quarter of time in the data

After our first attempt at using an SVM model on thr raw and differential statistics, we found that the accuracy seemed artifically high. We often produced an accuracy of `1.0`, although the accuracy was sometimes slightly lower depending on the training/testing split.

We decided to use the `tsfresh` library to produce tabular features instead. This library is more optimized at producing and selecting a variety of tabular time-series features.

This file is archived for reference, but we are no longer using it as an active part of our analysis pipeline.

[`/tabular/analysis_interdependent.ipynb`](./tabular/analysis_interdependent.ipynb)

In this analysis, we modeled the angles of different leg and joint combinations as interdependent. Each observation contained angle measurements for all leg and joint combinations. 

Our models all performed almost perfectly, which we believe is due to the small size of the feature-engineered dataset. As a result, the metrics may be artifically inflated.

[`/tabular/analysis_independent.ipynb`](./tabular/analysis_independent.ipynb)

To combat the inflated scores of the previous analysis, we tried to make the simplifying assumption that each leg and joint combination had independent angles. This means that each observation only contained one angle measurement, which allowed for a larger dataset. However, with this assumption, none of the models were able to perform well on the data.
