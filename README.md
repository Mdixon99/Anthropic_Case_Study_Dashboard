# Anthropic Compute Capacity Allocation Framework

A framework for allocating Anthropic's compute capacity between research, training, and inference — balancing safety, frontier capabilities, and revenue generation.

**Author:** Matthew Dixon
**Date:** February 17, 2026

---

## Overview

This case study addresses a core operational challenge: how should Anthropic allocate its finite compute resources across competing priorities?

The framework introduces a **tiered priority system** (P0 / P1 / P2) that:

- **P0 (Non-negotiable):** Reserves capacity for safety evaluations, red teaming, reliability, and SLA compliance
- **P1 (Strategic):** Elevates a category (inference, training, or research) when leadership identifies a strategic initiative
- **P2 (Flexible):** Allocates remaining capacity across inference, training, and research based on quantitative tradeoff analysis
- **Buffer:** Maintains 15% reserve for incidents and demand spikes

## Key Findings

| Scenario | Inference | Training | Research | Serviceable Revenue |
|---|---|---|---|---|
| **Recommendation** | 20% | 18% | 37% | $18.0B |
| Revenue Priority | 35% | 24% | 16% | $31.8B |
| Training Priority | 16% | 35% | 24% | $14.5B |

**Core assumptions:**
- ~12.1B H100-equivalent annual instance hours across AWS (Trainium 2), GCP (TPU v5p), and Azure (B200)
- ~1.08B H100 hours required annually to train 2 model families with 3 variants each
- Revenue per inference H100 hour of $7.48 at 20% utilization (post-discount)

**Note on utilization modeling:** The case study assumes a linear relationship between utilization and revenue per H100 hour. In practice, this relationship exhibits diminishing returns at higher utilization rates due to queuing effects, batching efficiency plateaus, and demand mix degradation. The dashboard models both curves — the theoretical linear model and a realistic logarithmic model anchored to the case study at 20% utilization — so that tradeoffs can be evaluated under either assumption.

## Interactive Dashboard

The project includes a self-contained interactive dashboard built with Chart.js that visualizes the full analysis.

**[View the live dashboard](https://mdixon99.github.io/Anthropic_Case_Study_Dashboard/)**

### Dashboard Sections

1. **Executive Summary** — Key metrics at a glance
2. **Accelerator Supply** — Multi-cloud fleet breakdown normalized to H100 equivalents
3. **Tiered Priority Framework** — Visual walkthrough of the P0/P1/P2/Buffer system
4. **Scenario Comparison** — Interactive toggle between 3 allocation scenarios with donut charts and detailed breakdowns
5. **Allocation Simulator** — Drag sliders to build custom allocations and see real-time impact on revenue, training capacity, and research investment with preset scenario buttons
6. **Sensitivity Analysis** — 7 scenarios showing how changes in revenue, training needs, and utilization shift allocations
7. **Revenue Economics** — Utilization vs. revenue curves and Claude model pricing matrix
8. **Training Benchmarks** — Industry model training costs and Anthropic's annual training estimate
9. **Capacity Management** — Operational recommendations for governance, resource pools, and KPI tracking

## Project Structure

```
├── index.html                              # Interactive dashboard (single-file, no build step)
├── Case_Study_Matthew_Dixon_Final.pdf      # Full case study (PDF)
├── Case_Study_Matthew_Dixon_Final.docx     # Full case study (Word)
└── README.md                               # This file
```

## How to View

1. **Clone the repo:**
   ```bash
   git clone https://github.com/<your-username>/Anthropic_Case_Study.git
   ```
2. **Open the dashboard:**
   Open `index.html` in any modern browser. No server, build step, or dependencies required.

3. **Read the full analysis:**
   Open `Case_Study_Matthew_Dixon_Final.pdf` for the complete written framework.

## Technology

- **Dashboard:** Vanilla HTML/CSS/JavaScript with [Chart.js](https://www.chartjs.org/) (loaded via CDN)
- **Design:** Responsive, mobile-friendly, Anthropic-inspired clean aesthetic
- **Deployment:** Static file — compatible with GitHub Pages, any web server, or local file system
