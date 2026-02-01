# Systematic Factor Machine Learning
**Machine Learning for Equity Index Forecasting**

---

## Overview

This repository implements an end-to-end quantitative research framework for forecasting and trading equity index returns using sector ETFs ... but what does that mean?

Essentially, we are quants who want to trade the SPY ETF (S&P 500). We want to develop a trading strategy for this purpose. In this notebook, we are going to come up with and test such a trading strategy.

At a high level, our trading strategy is going to involve predicting the SPY ETF returns and taking a position based on the predicted return. In order to predict the SPY ETF returns, we will be using several sector ETF returns as features. These are SPDR ETFs that slice the U.S. equity market (the S&P 500 universe) by sector. Together, they’re a standard way to decompose the market into economically meaningful blocks.

Our trading strategy is going to involve the coupling of a regression that aims to predict the SPY returns and a position sizer that takes in the predicted SPY return and outputs the position we should take. We will try many regression models and aim to narrow it down to one before we test it using a testing data set. The framework couples factor diagnostics, machine learning models, and portfolio simulation into a single reproducible research pipeline.

