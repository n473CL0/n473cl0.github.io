---
title: "ShipPy"
excerpt: "A Python library for the financial impact of biofouling on ships · Python, pytest"
collection: portfolio
order: 8
published: false  # AI-written draft: rewrite the excerpt and text in your own words, then delete this line
---

*Personal project · Mar 2026 – Jun 2026 · Python, pytest · [Code on GitHub](https://github.com/n473CL0/shippy)*

## What it is

A library for calculating the financial impact of biofouling (marine growth on a ship's hull, which increases drag and fuel use) and comparing hull-cleaning schedules.

## The model

* **Vessel inputs:** an operating profile (operating days, daily fuel use by fuel type, share of voyages under the EU Emissions Trading System, EU ETS carbon price), a biofouling model (yearly increase in fuel consumption) and a cleaning profile (cleans per year, post-clean fuel efficiency, service price per metre of hull).
* **Fouling:** fuel penalty grows linearly between cleans, so the average over a cleaning period is the post-clean level plus half the growth over the period.
* **Costs:** fuel cost, carbon emitted, carbon cost under the EU ETS, and cleaning service cost combine into a total cost per vessel.
* **Comparison:** `year_payback` compares two cleaning profiles and breaks the yearly difference down into fuel, carbon and service components.
* **Sensitivity analysis:** an example script sweeps fuel price (300–500 per tonne) and carbon price (50–100 per tonne) to see how the payback of a cleaning schedule changes.

The library offers two interfaces: an object-oriented one (`Vessel`, `OperatingProfile`, `Biofouling`, `CleaningProfile`, `Fleet`) and a functional "declarative" one built on named tuples. Both are covered by pytest tests.

<!-- PICTURE: a sensitivity chart, e.g. yearly cost difference against fuel price and against carbon price. The example script prints these numbers; plotting them would make a good figure -->
