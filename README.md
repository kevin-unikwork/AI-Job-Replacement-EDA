# 🤖 AI Job Replacement & Skill Shift Analysis — EDA Report

> **A comprehensive Exploratory Data Analysis investigating how artificial intelligence is reshaping employment risk, salary outcomes, and workforce skill demands across 15,000 records, 8 industries, 9 countries, and 7 years of data (2020–2026).**

[![GitHub Pages](https://img.shields.io/badge/Live%20Report-GitHub%20Pages-blue?style=flat-square&logo=github)](https://kevin-unikwork.github.io/AI-Job-Replacement-EDA/)
[![Notebook](https://img.shields.io/badge/Notebook-Jupyter-orange?style=flat-square&logo=jupyter)](./AI_Job_Replace_Analysis.ipynb)
[![Dataset](https://img.shields.io/badge/Dataset-Kaggle-20BEFF?style=flat-square&logo=kaggle)](https://www.kaggle.com/)
[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=flat-square&logo=python)](https://www.python.org/)

---

## 📋 Table of Contents

- [Project Overview](#-project-overview)
- [Dataset](#-dataset)
- [Key Findings](#-key-findings)
- [Analysis Sections](#-analysis-sections)
  - [Univariate Analysis](#1-univariate-analysis)
  - [Bivariate Analysis](#2-bivariate-analysis)
  - [Correlation Analysis](#3-correlation-analysis)
  - [Categorical Analysis](#4-categorical-analysis)
  - [Multivariate Analysis](#5-multivariate-analysis)
  - [Time Series Analysis](#6-time-series-analysis)
  - [Geographic Analysis](#7-geographic-analysis)
  - [Advanced Analysis](#8-advanced-analysis)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [How to Run](#-how-to-run)
- [Author](#-author)

---

## 📌 Project Overview

This project performs a full end-to-end Exploratory Data Analysis on the **AI Job Replacement Dataset** from Kaggle. The goal is to uncover data-driven insights into how AI adoption is transforming the workforce — which job roles face the greatest displacement risk, how salaries are shifting, which skills are in demand, and whether geography or industry meaningfully predicts exposure.

The analysis spans **8 analytical sections**, **29 interactive Plotly charts**, **10 Seaborn/Matplotlib visualisations**, and a fully deployed dark-theme dashboard hosted on GitHub Pages.

---

## 📊 Dataset

| Attribute | Value |
|-----------|-------|
| **Source** | Kaggle — AI Job Replacement Dataset |
| **Records** | 15,000 rows |
| **Features** | 20 columns (14 numeric, 4 categorical) |
| **Missing Values** | 0 |
| **Duplicates** | 0 |
| **Year Range** | 2020 – 2026 |
| **Industries** | 8 (Finance, Technology, Healthcare, Education, Manufacturing, Retail, Transportation, Energy) |
| **Countries** | 9 (India, USA, UK, Germany, Australia, Canada, Singapore, Brazil, Japan) |
| **Job Roles** | 10 (Software Engineer, Data Analyst, Truck Driver, Accountant, HR Manager, Marketing Specialist, Customer Support, Nurse, Teacher, Retail Worker) |

### Key Variables

| Variable | Type | Description |
|----------|------|-------------|
| `automation_risk_percent` | Numeric | Percentage likelihood of role being automated |
| `ai_replacement_score` | Numeric | Composite AI replacement risk score (0–100) |
| `salary_before_usd` | Numeric | Annual salary before AI adoption (USD) |
| `salary_after_usd` | Numeric | Annual salary after AI adoption (USD) |
| `salary_change_percent` | Numeric | Percentage change in salary post-adoption |
| `reskilling_urgency_score` | Numeric | Urgency score for upskilling (0–100) |
| `skill_demand_growth_percent` | Numeric | YoY growth in skill demand for the role |
| `skill_gap_index` | Numeric | Gap between required and available skills |
| `ai_adoption_level` | Numeric | Country-level AI technology adoption rate |
| `ai_disruption_intensity` | Numeric | Composite disruption measure per country |
| `remote_feasibility_score` | Numeric | Likelihood of role being performed remotely |
| `wage_volatility_index` | Numeric | Volatility in wages due to AI disruption |
| `job_role` | Categorical | Job title / role category |
| `industry` | Categorical | Industry sector |
| `country` | Categorical | Country of employment |
| `automation_risk_category` | Categorical | Low / Medium / High risk label |

---

## 🔍 Key Findings

### 1. 73% of Jobs Face Medium-to-High Automation Risk
Out of 15,000 records: **Medium 43.1% (6,464)**, **High 30.0% (4,496)**, **Low 26.9% (4,040)**. AI displacement is already a structural reality, not a future concern.

### 2. Strongest Signal: Automation Risk vs AI Replacement Score (r = 0.9644)
The Pearson correlation between `automation_risk_percent` and `ai_replacement_score` is **r = 0.9644** — by far the strongest relationship in the dataset. All 13 other feature pairs show |r| < 0.05. A single variable dominates the risk narrative.

### 3. Salary Change After AI Adoption Is Effectively Zero
Across all 15,000 records, the average salary change post-AI adoption falls between **-0.22% and +0.12%** — statistically indistinguishable from zero. AI is disrupting skills and roles *before* it disrupts wages.

### 4. Job Role Predicts Risk Better Than Industry
- **Highest risk role:** Truck Driver — **60.74%** automation risk
- **Safest role:** Software Engineer — **34.85%** automation risk  
- **Industry spread:** only 1.4 percentage points (45.60% – 47.02%)  
- **Role spread:** 26 percentage points (34.85% – 60.74%)

Industry membership is a weak predictor. The *type of work* matters far more than the sector it sits in.

### 5. AI Metrics Are Stable — Not Accelerating — Over 7 Years
All three core metrics (automation risk, AI replacement score, reskilling urgency) are **flat from 2020 to 2026**. This suggests gradual structural integration, not a sudden disruption event.

### 6. Remote Work Provides Zero Protection
The correlation between `remote_feasibility_score` and `automation_risk_percent` is approximately **r ≈ 0**. Being able to work from home does not reduce displacement risk.

### 7. National AI Policy Doesn't Predict Worker Exposure
India leads AI adoption (50.46), yet has an average automation risk of ~46%. The country range for disruption intensity is only 23.07–23.53. Disruption follows **job role composition**, not national investment level.

### 8. Positive Skill Demand Even for High-Risk Roles
Even Truck Drivers (highest risk) show **4.71% skill demand growth**. Software Engineers lead at **5.59%**. Retraining pathways exist across the board.

---

## 📈 Analysis Sections

### 1. Univariate Analysis

Individual feature distributions, frequency counts, and risk category breakdowns.

**Charts included:**
- Distribution of all 14 numeric features (histograms)
- Top Job Roles by record count — Marketing Specialist leads (1,551 / 10.34%)
- Top Industries by record count — Finance leads (1,942 / 12.95%)
- Top Countries by record count — all 9 balanced at 1,580–1,720
- Top high-paying roles after AI adoption — all roles cluster within $88,256–$91,376
- Automation Risk Category Breakdown — Medium 43.1%, High 30.0%, Low 26.9%
- Risk Category Distribution donut chart

**Key insight:** The dataset is stratified and globally balanced. Near-uniform distributions for `automation_risk_percent` and `ai_replacement_score` indicate consistent sampling across the risk spectrum.

---

### 2. Bivariate Analysis

Pairwise relationships between automation risk, salary, reskilling urgency and AI adoption.

**Charts included:**
- Industry Automation Risk Sunburst — Low/Medium/High breakdown per industry
- Salary Change After AI Adoption by Role — near-zero for all 10 roles
- Average AI Impact — 4 Metrics by Industry (skill_gap_index, automation_risk, reskilling_urgency, ai_disruption)

**Key insight:** Every industry shows the same relative metric ordering — `skill_gap_index` (~49–51) dominates, followed by automation_risk (~45–47), reskilling_urgency (~35–36), and ai_disruption (~22–24). No industry escapes this pattern.

---

### 3. Correlation Analysis

Statistical co-movement between all 14 numeric features.

**Charts included:**
- Full Pearson Correlation Matrix heatmap (14×14)
- Feature correlation bar chart ranked by |r| with `ai_replacement_score`

**Key insight:** `automation_risk_percent` has r = 0.9644 with `ai_replacement_score`. This is the only meaningful pair. `wage_volatility_index` has near-zero correlation with every other feature, making it an independent dimension of disruption.

---

### 4. Categorical Analysis

Cross-tabulation of job roles, industries, and countries against all key AI impact metrics.

**Charts included (11 total):**

| Chart | Key Value |
|-------|-----------|
| Automation Risk % by Job Role | Truck Driver 60.74% → Software Engineer 34.85% |
| Reskilling Urgency by Job Role | SW Engineer 30.83 (safest, yet still urgent) |
| Automation Risk % by Industry | Range 45.60% – 47.02% (1.4pt spread) |
| Reskilling Urgency by Industry | Range 35.41 – 36.18 (flat) |
| Salary Change % by Role | Range -0.22% to +0.12% (near-zero) |
| AI Adoption by Country | India 50.46 → all within 49.5–50.5 |
| AI Disruption Intensity by Country | Range 23.07 – 23.53 |
| Skill Demand Growth % by Role | SW Engineer 5.59% leads; Truck Driver 4.71% |
| Skill Demand Growth % by Industry | Finance and Technology lead; Healthcare lags at 4.60% |
| AI Talent Demand by Country | Globally distributed; all 9 within 4.8–5.2% |
| Remote Feasibility by Industry | Technology 57.08 leads; Manufacturing 53.66 lowest |

---

### 5. Multivariate Analysis

Pivot heatmaps and treemaps combining 3+ variables simultaneously.

**Charts included:**
- Salary Change % heatmap — Job Role × Country
- Skill Gap Index heatmap — Country × Industry  
- AI Replacement Score heatmap — Industry × Year
- Country AI Adoption vs Automation Risk scatter plot
- AI Risk Distribution Treemap — all Industry × Role combinations

**Key insight:** The 3-way heatmaps all reveal the same story — every cross-dimensional slice shows values clustering near the global mean. **HR Manager × India** peaks at +1.8% salary change (highest of any combination). **Brazil × Retail** peaks at 54.9 on the skill gap index. No combination is dramatically above or below the trend.

---

### 6. Time Series Analysis

Year-on-year tracking from 2020 to 2026.

**Charts included:**
- Average Key Metrics Trend (2020–2026) — all flat
- Salary Change % by Industry over Time — all 8 industries oscillate around 0
- Risk Category Distribution by Year — stable at ~900 Medium, ~640 High, ~570 Low per year
- Skill Demand Growth Trend 2020–2026 — range 4.52% (2022) to 5.30% (2026)
- Salary Before vs After AI Adoption by Year — two lines completely overlapping at ~$89K–$90K

**Key insight:** None of the 7-year trends show a meaningful directional shift. AI integration into the labour market, as represented in this dataset, is a gradual and already-present condition rather than an emerging acceleration.

---

### 7. Geographic Analysis

Global mapping of AI disruption intensity across 9 countries.

**Charts included:**
- Global AI Workforce Disruption Map (world choropleth)
- Country AI Adoption vs Automation Risk scatter
- AI Disruption Intensity by Country bar chart

**Key insight:** The world map shows near-uniform disruption across all represented nations. Both developed economies (USA, Germany, Japan) and emerging economies (India, Brazil) show identical exposure levels. Geography is not a protective factor.

---

### 8. Advanced Analysis

High-impact synthesis charts for strategic insight.

**Charts included:**
- **Future-Proof Job Roles Scatter** — Automation Risk % vs Skill Demand Growth %
  - Safe quadrant (low risk, high demand): Software Engineers (35%, 5.59%), Data Analysts (35%, 5.21%)
  - Danger quadrant (high risk, low demand): Truck Drivers (61%)
- **Sankey Diagram** — Country → Industry → Risk Category flow
  - Medium Risk bands are consistently widest from all source countries
- **Industry Multi-Metric Radar** (Normalised 0–1 across 5 axes)
  - Energy: largest footprint across all 5 metrics
  - Education: most protected industry
  - Retail: disproportionate reskilling urgency relative to automation risk

---

## 🛠 Tech Stack

| Tool | Purpose |
|------|---------|
| **Python 3.10+** | Core analysis language |
| **Pandas** | Data loading, cleaning, groupby aggregations, feature engineering |
| **Plotly** | 29 interactive charts — bar, pie, sunburst, sankey, radar, choropleth, treemap |
| **Seaborn** | Correlation matrices, pivot heatmaps, distribution histograms |
| **Matplotlib** | Figure layouts and static chart exports |
| **SciPy / NumPy** | Pearson correlation, statistical significance, numerical operations |
| **Jupyter Notebook** | Interactive analysis environment — 68 cells end-to-end |
| **GitHub Pages** | Live dashboard hosting |

---

## 📁 Project Structure

```
AI-Job-Replacement-EDA/
│
├── AI_Job_Replace_Analysis.ipynb   # Main Jupyter notebook (68 cells)
├── AI_Dashboard_Kevin_Savaliya.html # Interactive dark-theme dashboard
├── README.md                        # This file
│
└── data/
    └── AI_Job_Replacement_Dataset.csv  # Source dataset (15,000 × 20)
```

---

## ▶️ How to Run

### 1. Clone the repository
```bash
git clone https://github.com/kevin-unikwork/AI-Job-Replacement-EDA.git
cd AI-Job-Replacement-EDA
```

### 2. Install dependencies
```bash
pip install pandas numpy plotly seaborn matplotlib scipy jupyter
```

### 3. Launch the notebook
```bash
jupyter notebook AI_Job_Replace_Analysis.ipynb
```

### 4. View the live dashboard
Open the deployed report directly in your browser:
👉 **[https://kevin-unikwork.github.io/AI-Job-Replacement-EDA/](https://kevin-unikwork.github.io/AI-Job-Replacement-EDA/)**

---

## 👤 Author

**Kevin Savaliya**  
Data Analyst · EDA Portfolio

- 🔗 GitHub: [@kevin-unikwork](https://github.com/kevin-unikwork)
- 📊 Live Report: [AI Job Replacement EDA Dashboard](https://kevin-unikwork.github.io/AI-Job-Replacement-EDA/)

---

## 📜 License

This project is open source and available under the [MIT License](LICENSE).

---

<div align="center">

**If you found this analysis useful, please consider giving it a ⭐**

</div>
