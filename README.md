# 🍽️ Zomato Unit Economics Simulator (FY24 Model)

A Monte Carlo–based **profitability and risk simulator** built using **Zomato FY24 food delivery data**.  
It models uncertainty in AOV, rider cost, CAC, refunds, and operations to estimate **profit per order**,  
**loss-risk**, and **monthly profit** at Zomato’s ~66M monthly order scale.

The project then evaluates **5 strategic levers** and builds **2 sensitivity heatmaps** to show which decisions  
have the strongest impact on profit and risk.

---

## 🚀 Project Overview

Food delivery unit economics are highly sensitive.  
A small change in AOV, rider payout, CAC, or refund rate can flip profitability.

This simulator answers three questions:

1. **What does Zomato actually earn per order after randomness?**  
2. **Which levers (delivery fee, commission, CAC, refunds, rider variance) move profit the most?**  
3. **Where does the business become risky or unstable?**

---

## 🔧 Monte Carlo Engine (10,000 Order Simulation)

Instead of treating AOV or rider cost as fixed, the simulator models each order as a **random event**:

- AOV ~ Normal(428, 50)  
- Rider Cost ~ Normal(32, 10)  
- Packaging Cost ~ Normal(12, 3)  
- CAC/Marketing Cost ~ Normal(20, 10)  
- Refund Flag ~ Bernoulli(p = 0.02)  
- Payment gateway fee = 2.4% of AOV  

### **Net Profit per Order Formula**
```
Revenue = AOV × Commission + Delivery Fee
Costs   = Rider + Packaging + CAC + Gateway Fee + Refund Loss
Profit  = Revenue – Costs
```

### **Baseline Outputs**
- **Avg Profit/order:** ₹48.26  
- **Loss-Risk:** 2.20% (probability profit < 0)  
- **Monthly Orders:** ~66M (from FY24 GOV/AOV)  
- **Monthly Profit:** ₹318.52 Cr  

The histogram shows a strong right-skewed distribution with rare but heavy losses  
(from refund events).

---

## 📊 Scenario Engine (5 Strategic Levers)

Five real-world strategy levers are tested by re-running the Monte Carlo engine  
and adjusting order volume impact:

### **A. Increase Delivery Fee (+₹5)**
- Slight user churn  
- Slightly higher CAC  
- Profit/order: ₹51.31  
- Monthly Profit: ₹328.52 Cr  

### **B. Reduce Refund Probability (2% → 1%)**
- Stricter refund policy / operational improvements  
- Lower new-user confidence  
- Profit/order: ₹52.70  
- Monthly Profit: ₹337.36 Cr  

### **C. Reduce Rider Cost Variance (SD 10 → 6)**
- More predictable routing  
- Slight operational friction  
- Profit/order: ₹47.49  
- Monthly Profit: ₹310.31 Cr  

### **D. Reduce CAC (₹20 → ₹10)**
- Less aggressive marketing  
- Slower user growth  
- Profit/order: ₹59.27  
- Monthly Profit: ₹371.59 Cr  

### **E. Increase Commission (22.5% → 25%)**
- Higher take rate  
- Mild restaurant churn risk  
- Profit/order: ₹58.24  
- Monthly Profit: ₹376.68 Cr  (Highest among scenarios)

---

## 🔥 Key Insights

- **Commission increase is the strongest profit lever**  
- **Refund reduction is the strongest risk-reduction lever**  
- Delivery fee increase has moderate upside  
- Rider cost variance reduction has minimal impact  
- CAC efficiency has a huge impact but hurts growth  
- Profit zones concentrate at:  
  - **25–26% Commission**  
  - **₹44–₹50 Delivery Fee**

---

## 🌡️ Sensitivity Heatmaps (2D Analysis)

Built using multiple Monte Carlo runs across parameter grids.

### **1. Commission × Delivery Fee → Monthly Profit (₹ Cr)**  
Shows the profit frontier.  
Profits rise sharply with commission and moderately with delivery fee.

### **2. Commission × Refund Probability → Loss-Risk (%)**  
Shows the risk frontier.  
Refund probability is the **dominant driver** of tail risk.

These help identify stable, high-profit operating zones.

---

## 📁 Project Structure

```
zomato-unit-economics-simulator/
│
├── notebooks/
│   ├── 01_baseline_monte_carlo.ipynb
│   ├── 02_scenarios_engine.ipynb
│   └── 03_sensitivity_heatmaps.ipynb
│
├── reports/
│   ├── Zomato_Unit_Economics_&_Risk_Simulator_(FY24.pptx
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

## 🛠 Installation & Usage

### 1. Install dependencies
```
pip install -r requirements.txt
```

### 2. Open notebooks in Google Colab or Jupyter:
- Run baseline simulation  
- Run scenarios  
- Run sensitivity heatmaps  

Charts and results are generated automatically.

---

## 📄 Presentation

A full consulting-style PPT explaining assumptions, logic,  
findings, heatmaps, and recommendations is available in:

```
/reports/Zomato_Simulator_Presentation.pdf
```

---

## 👤 Author

Built by **Kushagra Bansal**  
Email: **writekushagra12@gmail.com**

Role: Quantitative Architect & Product Strategy enthusiast  
Open to feedback, contributions, and collaboration.

---

## ⭐ Why This Project Matters

This simulator demonstrates:
- Real-world understanding of quick-commerce economics  
- Ability to model uncertainty using Monte Carlo  
- Scenario analysis & strategic insights  
- Sensitivity analysis  
- Communication through charts and PPT  
- End-to-end product & analytics thinking  

Useful for product roles, consulting, data science, and strategy.

