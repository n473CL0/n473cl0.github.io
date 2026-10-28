---
title: "Bond Valuation Framework"
excerpt: "Modelling bond cash flows under different inflation and interest-rate models · Python"
collection: portfolio
order: 7
published: false  # AI-written draft: rewrite the excerpt and text in your own words, then delete this line
---

*Personal project · Mar 2025 – Apr 2025 · Python, pandas, Matplotlib*

## What it is

A Python framework for modelling the cash flows of different bond types and evaluating the return from a bond trade under different inflation models.

## How it works

* **Bond types:** a common `Bond` base class (face value, payment frequency, price, maturity, inflation model) with subclasses for fixed-rate bonds, zero-coupon bonds, floating-rate notes and partially amortising bonds. Each subclass supplies its own cash-flow schedule.
* **Discounting:** given an inflation/discount-rate model, the framework converts each period's rate to a per-payment rate and builds cumulative discount factors, giving the present value of every cash flow and the bond's real (inflation-adjusted) versus nominal profit.
* **Rate models:** constant, linear (time-varying) and Vasicek (stochastic) models, each exposing the same `get_discount_rates(times)` interface so they can be swapped freely.
* **Output:** cash-flow bar charts and discount-rate curves for every bond type and model combination, plus CSV exports of the schedules.

<!-- PICTURE: one cash-flow chart and its matching discount-rate curve side by side. These already exist in the repo: _data/graph/fix_inflation_adjusted/Fixed-Vasic-1000-cash_flows.png and Fixed-Vasic-1000-discount_rates.png -->

<!-- PICTURE (optional): nominal vs Vasicek-adjusted cash flows for the same bond, to show the inflation effect (_data/graph/fix_nominal/Fixed-not_adjusted-1000-cash_flows.png vs the Vasicek one) -->
