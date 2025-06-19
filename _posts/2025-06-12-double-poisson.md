---
layout: post
title: "Remembering the Double Poisson Distribution"
date: 2025-06-12
tags: [Count Data, Poisson, Conway-Maxwell Poisson, Double Poisson, GLM]
author: Nathen Byford
excerpt: "Why you might want to consider using the double Poisson in place of the Conway-Maxwell Poisson (CMP) Distribution."
---

# Non-equidispersed Cound Data

When modeling count data, the Poisson distribution has long been the workhorse. But real data rarely play by Poisson's rules. Specifically, the assumption that the mean equals the variance (equidispersion). Overdispersion is common; underdispersion, though rarer, can be even trickier. This has led to the rise of more flexible models like the Conway-Maxwell Poisson (CMP), which adjusts dispersion through an extra parameter.

The CMP is powerful—but it’s also computationally expensive, hard to interpret in its standard form, and not naturally compatible with GLMs. And yet, it dominates modern flexible count modeling.

# Enter the Double Poisson

Back in 1986, Bradley Efron quietly introduced the Double Poisson (DP)—a simple, elegant generalization of the Poisson. It allows the variance to differ from the mean using a dispersion parameter $\theta$, while keeping the familiar Poisson-like structure. The key idea: scale the likelihood to adjust variance.

Unlike CMP, the Double Poisson:

- Is mean-parameterized by default
- Plays well with GLM frameworks
- Is easy to implement and interpret
- Requires far less computational effort (compared to CMP)

## Why Is It Overlooked?

Mostly because it wasn’t loudly marketed. While CMP saw a wave of papers, software packages, and attention over the last two decades, the DP remained under the radar—despite being a fast, flexible, and interpretable solution for dispersed count data.

## When Should You Use the DP?

- You want Poisson-like behavior with flexible variance
- You’re working in GLMs and don’t want to rewrite your modeling stack
- You're doing Bayesian inference and want stable, fast sampling
- You're analyzing data with moderate under- or overdispersion

For extreme underdispersion or skewed count distributions, CMP might still fit better. But for many use cases, the Double Poisson is the practical sweet spot.