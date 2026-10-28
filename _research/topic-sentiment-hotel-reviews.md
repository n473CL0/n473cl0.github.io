---
title: "Topic–Sentiment Analysis of Hotel Reviews"
excerpt: "Topic modelling and sentiment analysis of 515,738 Booking.com reviews · Python, BERTopic, RoBERTa, Streamlit"
collection: research
order: 1
published: false  # AI-written draft: rewrite the excerpt and text in your own words, then delete this line
---

*University of Bristol, Mathematical and Data Modelling 2 (group of five) · 2026 · Python, BERTopic, multilingual RoBERTa, Streamlit · [Code on GitHub](https://github.com/n473CL0/MDM2-ReviewsProj)*

* Applied BERTopic topic modelling and sentiment scoring to unstructured hotel reviews, measured how sentiment varied by reviewer category, and built a Streamlit dashboard for hotel owners.

<!-- PICTURE: a per-hotel radar chart (topic scores vs city average) -->

## Data

515,738 Booking.com reviews of hotels in six European cities: Amsterdam, Barcelona, London, Milan, Paris and Vienna. The pipeline draws a city-balanced stratified sample of 36,000 reviews (30 hotels × 6 cities × 200 reviews).

## Pipeline

1. **Pre-processing:** split reviews into fragments, remove stop words and clean placeholders.
2. **Topic modelling:** BERTopic with zero-shot assignment to 10 predefined business categories. LDA and NNMF were also evaluated during the project.
3. **Sentiment:** a multilingual RoBERTa model classifies each of ~53,000 fragments as positive, neutral or negative (VADER was compared as an alternative).
4. **City benchmarking:** a delta score with a ±0.5σ threshold classifies each hotel's performance on each topic relative to its local competitors.
5. **Results:** per-hotel radar charts, peer ranking tables, seasonal analysis and a single-hotel deep dive.

## Dashboards

* **City-level dashboard:** cross-city benchmarks, topic correlations and seasonal trends.
* **Owner dashboard:** a single hotel's topic scores, peer ranking and actionable advice.

<!-- PICTURE: screenshot of the Owner dashboard (run: streamlit run Owner_UI.py) -->
<!-- PICTURE (optional): screenshot of the City-level dashboard (streamlit run Macro_UI.py) -->
