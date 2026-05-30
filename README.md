
# Zomato Unit Economics Simulator (FY24 Model)

Monte Carlo–based profitability and risk simulator built on 
Zomato FY24 food delivery data. Models uncertainty across 
pricing, operations, and cost variables to identify the 
highest-ROI strategic levers at Zomato's ~66M monthly order scale.

---

<<<<<<< HEAD
## Project Overview
=======
## Key Findings
>>>>>>> ffd03ed (Revamp README: lead with findings, add heatmaps, scenario table, recommendations)

> **Commission rate is Zomato's highest-ROI profit lever** —
> a 2.5% increase delivers +₹58 Cr monthly profit,
> outperforming a ₹5 delivery fee increase by 5x.

| Finding | Insight |
|---|---|
| Strongest profit lever | Commission rate increase (22.5% → 25%) |
| Strongest risk-reduction lever | Refund probability reduction (2% → 1%) |
| Largest absolute profit upside | CAC efficiency (₹20 → ₹10 = +₹53 Cr/month) |
| Dominant tail-risk driver | Refund probability — not rider cost or AOV |
| Baseline profitability | ₹48.26 avg profit/order, 2.2% loss risk |
| Optimal strategy | Refund reduction + CAC efficiency first; pricing levers selectively |

---

## Full Analysis

Consulting-style presentation with methodology, assumptions,
findings, heatmaps, and strategic recommendations:

📄 [View Full Report (PDF)](reports/Zomato_Unit_Economics_&_Risk_Simulator_(FY24).pdf)

---

## What This Simulator Does

Food delivery unit economics are highly sensitive.
A small change in AOV, rider payout, CAC, or refund rate
can flip per-order profitability at scale.

This simulator answers three questions:

1. **What does Zomato actually earn per order under real-world uncertainty?**
2. **Which levers move profit and risk the most?**
3. **Where does the business become unstable?**

---

## Monte Carlo Engine (10,000 Order Simulation)

Each order is modeled as a random event drawn from
calibrated FY24 distributions — not fixed averages.

| Variable | Distribution | Parameters |
|---|---|---|
| AOV | Normal | μ=428, σ=50 |
| Rider Cost | Normal | μ=32, σ=10 |
| Packaging Cost | Normal | μ=12, σ=3 |
| CAC / Marketing | Normal | μ=20, σ=10 |
| Refund Flag | Bernoulli | p=0.02 |
| Payment Gateway Fee | Fixed % | 2.4% of AOV |

### Net Profit Formula

```text
Revenue = (AOV × Commission Rate) + Delivery Fee
Costs   = Rider + Packaging + CAC + Gateway Fee + Refund Loss
Profit  = Revenue – Costs
````

### Baseline Results (FY24)

* **Avg Profit/Order:** ₹48.26
* **Loss Risk:** 2.20% (probability profit < 0)
* **Monthly Orders:** ~66M
* **Monthly Profit:** ₹318.5 Cr

![Baseline Profit Distribution](assets/histogram_baseline.png)

---

<<<<<<< HEAD
## Scenario Engine (5 Strategic Levers)
=======
## Scenario Comparison (5 Strategic Levers)
>>>>>>> ffd03ed (Revamp README: lead with findings, add heatmaps, scenario table, recommendations)

| Scenario                 | Avg Profit/Order | Loss Risk | Monthly Profit | Key Trade-off         |
| ------------------------ | ---------------- | --------- | -------------- | --------------------- |
| Baseline FY24            | ₹48.26           | 2.20%     | ₹318.5 Cr      | —                     |
| +₹5 Delivery Fee         | ₹51.31           | 1.82%     | ₹328.5 Cr      | Slight customer churn |
| Refund ↓ (2%→1%)         | ₹52.70           | 1.02%     | ₹337.4 Cr      | Lower new-user trust  |
| Rider Variance ↓         | ₹47.49           | 2.24%     | ₹310.3 Cr      | Minimal upside        |
| CAC ↓ (₹20→₹10)          | ₹59.27           | 1.82%     | ₹371.6 Cr      | Slower user growth    |
| Commission ↑ (22.5%→25%) | ₹58.24           | 2.20%     | ₹376.7 Cr      | Restaurant churn risk |

*All scenarios simulated using 10,000 Monte Carlo runs
scaled to FY24 monthly volumes.*

---

<<<<<<< HEAD
## Key Insights
=======
## Sensitivity Analysis
>>>>>>> ffd03ed (Revamp README: lead with findings, add heatmaps, scenario table, recommendations)

### Monthly Profit: Commission Rate × Delivery Fee

![Profit Heatmap](assets/heatmap_profit.png)

Profit rises sharply with commission and moderately with
delivery fee. Commission has a compounding effect at scale —
delivery fee has a linear effect.

**Profit zones concentrate at: 25–26% commission, ₹44–₹50 delivery fee.**

---

<<<<<<< HEAD
## Sensitivity Heatmaps (2D Analysis)
=======
### Loss Risk: Commission Rate × Refund Probability
>>>>>>> ffd03ed (Revamp README: lead with findings, add heatmaps, scenario table, recommendations)

![Risk Heatmap](assets/heatmap_risk.png)

Refund probability is the dominant driver of tail risk.
Higher commission cannot offset high refund rates.
Loss risk rises sharply beyond ~3–4% refund probability.

**Operational quality matters more than monetization for risk control.**

---

<<<<<<< HEAD
## Project Structure
=======
## Strategic Recommendations
>>>>>>> ffd03ed (Revamp README: lead with findings, add heatmaps, scenario table, recommendations)

1. **Prioritise refund reduction** — lowest risk path,
   halves loss probability with minimal volume impact.
   Improve order accuracy, packaging standards,
   and customer communication.

2. **Focus on CAC efficiency, not absolute cuts** —
   shift from blanket discounts to cohort-based incentives.
   Preserves growth while capturing ₹53 Cr monthly upside.

3. **Apply delivery fee increases selectively** —
   dynamic pricing during peak demand and high congestion only.
   Avoids broad-based churn.

4. **Treat commission increases as a secondary lever** —
   pair with restaurant value-adds (ads, analytics).
   Avoid long-term platform disintermediation risk.

5. **Improve rider cost predictability via routing optimisation** —
   not hard cost suppression.
   Stabilises operations without triggering supply shocks.

---

## Limitations

* FY24 averages used — does not model cohort-level variation
* Cost drivers modeled as independent distributions
* Long-term churn dynamics not captured
* City-level and time-of-day variations not modeled
* Results indicate directional strategy impact, not exact forecasts

---

## Project Structure

```text
zomato-unit-economics-simulator/
│
├── notebooks/
│   ├── 01_baseline_monte_carlo.ipynb
│   ├── 02_scenarios_engine.ipynb
│   └── 03_sensitivity_heatmaps.ipynb
│
├── reports/
<<<<<<< HEAD
│   ├── Zomato_Unit_Economics_&_Risk_Simulator_(FY24.pptx
=======
│   ├── Zomato_Unit_Economics_&_Risk_Simulator_(FY24).pptx
>>>>>>> ffd03ed (Revamp README: lead with findings, add heatmaps, scenario table, recommendations)
│   └── Zomato_Unit_Economics_&_Risk_Simulator_(FY24).pdf
│
├── assets/
│   ├── heatmap_profit.png
│   ├── heatmap_risk.png
│   └── histogram_baseline.png
│
├── requirements.txt
└── README.md
```

---

## Installation & Usage

```bash
pip install -r requirements.txt
```

Open notebooks in order in Google Colab or Jupyter:

1. `01_baseline_monte_carlo.ipynb` — baseline simulation
2. `02_scenarios_engine.ipynb` — strategic lever testing
3. `03_sensitivity_heatmaps.ipynb` — 2D sensitivity analysis

Charts and results generate automatically.

---

<<<<<<< HEAD
## Presentation
=======
## Built By
>>>>>>> ffd03ed (Revamp README: lead with findings, add heatmaps, scenario table, recommendations)

**Kushagra Bansal**
B.Tech CSE — Shiv Nadar University (2024–28)

[LinkedIn](www.linkedin.com/in/kushagra-kb1210) · [GitHub](https://github.com/Kushagra-1210)

```
```
<<<<<<< HEAD

---

## Author

Built by **Kushagra Bansal**  
Email: **writekushagra12@gmail.com**

Role: Quantitative Architect & Product Strategy enthusiast  
Open to feedback, contributions, and collaboration.

---

## Why This Project Matters

This simulator demonstrates:
- Real-world understanding of quick-commerce economics  
- Ability to model uncertainty using Monte Carlo  
- Scenario analysis & strategic insights  
- Sensitivity analysis  
- Communication through charts and PPT  
- End-to-end product & analytics thinking  

Useful for product roles, consulting, data science, and strategy.

=======
>>>>>>> ffd03ed (Revamp README: lead with findings, add heatmaps, scenario table, recommendations)
