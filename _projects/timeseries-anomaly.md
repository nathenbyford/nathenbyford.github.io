---
layout: project
title: "Time Series Anomaly Detection"
subtitle: "Identifying anomalies in univariate time series"
tech: [R, Neural Networks, STL decomposition]
icon: "fas line-chart"
github: "https://github.com/nathenbyford/anomaly-detection-project"
slides: "https://natebyford.com/anomaly-detection-project"
date: 2023-12-15
excerpt: "Applied machine learning anomaly detection techniques (neural networks, STL, regression leverage points, isolation forests) to identify irregularities in complex time series datasets."
---

# Anomaly Detection with Isolation Forests

As part of a graduate course on advanced analytics, I conducted a comparative study on anomaly detection methods using the **Numenta Anomaly Benchmark**—specifically, Twitter hashtag frequency data for 10 major companies (e.g., Apple, Google, Meta). The dataset included over 150,000 time-stamped observations labeled for known anomalies.

## Objective
Detect anomalies in high-frequency time series data using both statistical and machine learning approaches.

## Methods Compared
- **Linear Regression with Outlier Diagnostics** (e.g., Cook’s distance)
- **STL Decomposition** (Seasonal + Trend + Residual anomaly bounds)
- **Artificial Neural Networks** (ANN2 in R)
- **Isolation Forests** (including a variant using density-based anomaly scores)

## Key Findings
- The **Density Isolation Forest** model consistently outperformed other methods in identifying true anomalies, achieving near-perfect AUC scores across 9 of the 10 companies.
- **STL decomposition** had the strongest overall AUC performance and served as an effective benchmark.
- Standard ANN models underperformed, highlighting challenges in applying deep learning to univariate time series without temporal structure.
- The **UPS** and **Google** time series revealed limitations of univariate models when anomalies do not present as simple spikes or drops.

This project emphasized the importance of both model selection and domain context in time series anomaly detection, particularly when true anomalies are rare or structurally subtle.
