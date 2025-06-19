---
layout: project
title: "Detecting Benford's Law"
subtitle: "Evaluating Goodness-of-Fit Tests and Exploring Textual Analogues"
tech: [R, Simulation Studies, NLP]
icon: "fas fa-bar-chart"
date: 2021-08-01
excerpt: "Developed and tested innovative methods for detecting Benford’s Law in real data, advancing statistical analysis techniques."
---

# Introduction to Benford's Law

Benford’s Law describes a striking regularity in many naturally occurring numerical datasets: lower digits (like 1 or 2) appear as the leading digit more frequently than higher digits. For example, the digit 1 appears as the first digit about 30% of the time, while 9 appears less than 5% of the time. While the law has been applied in fields like fraud detection and forensic accounting, verifying whether a dataset follows Benford’s Law is not always straightforward—especially with small sample sizes, measurement artifacts, or data that doesn’t naturally span multiple orders of magnitude. Assessing conformance requires careful selection of statistical tests that balance power and false positive control under varying conditions.

# Developing Tests of Benford's Law

As an undergraduate research assistant, I worked with a team to study and compare statistical methods for detecting whether datasets conform to Benford’s Law—a mathematical principle describing the expected distribution of leading digits in naturally occurring data. This law has important applications in fields like fraud detection, forensic accounting, and even geophysics.

## Project Goals

- Evaluate and compare the power and Type I error rates of statistical tests for Benford conformity.
- Explore the law’s relevance in real-world datasets and in non-numerical contexts like text analysis.

## Key Methods

We conducted extensive simulation studies in R, using distributions such as Poisson, gamma, uniform, and normal to assess how well each method performs under different scenarios. Tests evaluated included:

- Chi-Squared goodness-of-fit
- Hotelling-type multivariate test
- Sup-norm (Chebyshev distance)
- Min p-value and combined tests
- Euclidean distance test
- Watson's $U^2$ test
- Kolmogorov-Smirnov test

These were compared in terms of false positive control and sensitivity to Benford violations, helping us understand which tests are most reliable in practice.

## Applications

We applied the best-performing tests to real datasets, including:

- Hospital cost data from CMS
- Global energy production statistics
- COVID-19 case reports and tax simulation models

# Exploring Textual Analogues

In a creative extension of the project, we investigated whether a Benford-like pattern exists in English language word usage. Using word frequency data from a dictionary and a Shakespeare corpus, we analyzed the distribution of initial letters and found evidence of a logarithmic-like shape, suggesting potential analogs to Benford’s Law in text.

# Project Outcomes

This project deepened my skills in simulation, statistical hypothesis testing, and real-world data application, while also encouraging cross-domain thinking between numerical analysis and language modeling.