---
title: "Bidisperse Disk Packing Simulation"
excerpt: "Minimising wasted material when pressing disks of two sizes from a sheet · Python"
collection: research
order: 2
published: false  # AI-written draft: rewrite the excerpt and text in your own words, then delete this line
---

*University of Bristol, Mathematical and Data Modelling (Year 1) · Jan 2025 – Mar 2025 · Python, pandas, Matplotlib*

* Simulated the densest packing of circular disks of two diameters using fixed-grid and gravity-based methods, scaling runs until packing efficiency converged to a set precision.

<!-- PICTURE: one packing layout preview, e.g. a hexagonal arrangement of two disk sizes (the repo's figures/ folder has 210 per method) -->

## The problem

Disks of two diameters are pressed from a long rectangular sheet (3 m in the previews). The aim is to find the arrangement that wastes the least material for each pair of diameters.

## Methods

* **Fixed-grid arrangements:** square (simple and vertical) and hexagonal (standard and rotated) packings of the two disk sizes, with a square-spiral variant started.
* **Gravity-based packing:** a separate method compared against the grid arrangements.
* **Sweep:** each method is run across every pair of diameters at increasing resolution. Waste percentages are saved per pair, and the results are mirrored so the table covers both orderings of the pair.

## Results

For each method, a heatmap of waste percentage over all diameter pairs, and an overall map of which method wastes least for each pair, with and without the gravity method.

<!-- PICTURE: the overall minimum-waste heatmap (repo: data/heatmaps/min_waste_with_gravity.png), next to one single-method heatmap for comparison (e.g. data/heatmaps/hexagonal.png) -->
