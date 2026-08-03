[README (5).md](https://github.com/user-attachments/files/30656410/README.5.md)
# The State of Personal Finance Among Young Nigerian Professionals (2026)

A data analytics deep-dive into savings behaviour, emergency-fund coverage, investing habits, budgeting, and financial literacy among young Nigerian professionals — from survey design through to an executive Power BI dashboard.

**[View the Linkedin write up (https://www.linkedin.com/in/oluwabusola-oyenuga/)]** &nbsp;|&nbsp; **[View the dashboard (PDF/screenshots) →](#)**

---

## 📊 Overview

Financial fragility is common among young professionals, but it's rarely quantified in a way banks, fintechs, and consulting firms can act on. This project builds a **Financial Wellness Score (0–100)** from real survey data, then uses it to answer:

- How financially healthy are young Nigerian professionals, really?
- Where does that health break down first — budgeting, saving, emergency funds, investing, or literacy?
- Does income, employment type, region, or age explain the differences?

**Sample:** 308 respondents (real survey responses collected via Google Forms, supplemented with synthetic data validated to sit within 3–5 percentage points of real-data distributions on key variables).

## 🔑 Key Findings

- **74.4%** of respondents fall into the *Vulnerable* or *At Risk* wellness bands — financial fragility is the norm, not the exception, in this sample.
- **Emergency fund coverage is the weakest link**: the lowest-scoring component for 48% of respondents, and only 58.1% have any fund at all.
- **57.8% don't invest**, and "I don't earn enough" is the most common reason given — not distrust or lack of awareness.
- **Income and employment type both independently predict wellness score** (ANOVA p < 0.0001 and p = 0.0001 respectively) — income alone doesn't tell the whole story.
- **Emergency fund coverage peaks at the ₦500k–1m income bracket, then dips for the highest earners** — a non-linear pattern likely tied to irregular/business income at the top end.
- **Business ownership is the dominant financial goal (39.6%)**, well ahead of home ownership or debt freedom — this is an entrepreneurially-oriented segment.

Full breakdown in the [dashboard](#) and [methodology report](#).

## 🖥️ Dashboard

A 3-page Power BI executive dashboard:

| Page | Focus |
|---|---|
| **The State of Financial Fragility** | Headline KPIs, wellness category split, weakest financial area, regional spread |
| **Who's Struggling, and Why** | Wellness score cut by income, employment type, region, and age |
| **What They Want, and What's in the Way** | Financial goals, investing barriers, budgeting behaviour, literacy vs. confidence gap |
<img width="967" height="585" alt="Executive Overview" src="https://github.com/user-attachments/assets/9f0c5685-57a7-4988-803d-4518a3a75828" />
<img width="968" height="587" alt="Segment Deep Dive" src="https://github.com/user-attachments/assets/3190d1f7-961b-410e-aaa1-7d50669b9f8a" />
<img width="959" height="587" alt="Behaviour and Goals" src="https://github.com/user-attachments/assets/827fd84f-ef38-486e-a124-52b2960fa2a9" />

## 🛠️ Tech Stack

| Stage | Tools |
|---|---|
| Data collection | Google Forms |
| Automated scoring & respondent emails | Google Apps Script |
| Data cleaning & analysis | Python (pandas) |
| SQL querying | SQLite |
| Exploratory Data Analysis | Python (MatPlotlib) |
| Visualization | Power BI |
| Publishing | GitHub, LinkedIn |

## 📁 Project Structure

```
├── data/
│   ├── raw_survey_responses.csv
│   ├── cleaned_data.csv
├── notebooks/
│   ├── 01_data_cleaning.ipynb
│   └── 02_eda_and_analysis.ipynb
├── sql/
│   └── sql_business_questions_and_query.txt
    SQL_Query_Insights_and_Recommendations
├── dashboard/
│   └── financial_wellness_dashboard.pbix
├── docs/
│   └── Methodology_and_Findings_Report.docx
└── README.md
```


## 🧹 Data Cleaning Highlights

- Fixed an Excel auto-date-corruption bug where range answers like `"1-3"` were silently reinterpreted as dates (e.g. `"3-Jan"`) and mapped back using an explicit replacement dictionary.
- Corrected mojibake encoding artefacts (e.g. `â€“` in place of an en dash) introduced by the form export.
- Distinguished **structural missing values** (e.g. investment-related questions that are only asked conditionally) from genuine data-quality gaps, rather than imputing everything uniformly.
- Exploded the multi-select `investment_types` field for accurate per-instrument analysis.
- Consolidated long-tail free-text reasons into a clean `Other` category without collapsing valid, distinct responses.

Full details in [`docs/Methodology_and_Findings_Report.docx`](#).

## 📐 Financial Wellness Score Methodology

A 0–100 composite score across five weighted components:

| Component | Weight | Based on |
|---|---|---|
| Budgeting | 20 pts | Behavioural tracking question |
| Saving | 25 pts | % of income saved, adjusted by frequency |
| Emergency Fund | 20 pts | Has a fund, scaled by months of coverage |
| Investing | 20 pts | Currently invests (Yes/No) |
| Financial Literacy | 15 pts | Budgeting confidence + inflation/compounding knowledge check |

Bands: **Thriving** (80–100) · **Stable** (60–79) · **At Risk** (40–59) · **Vulnerable** (<40)

## 📬 Contact

**Oluwabusola Oyenuga**
[LinkedIn](https://linkedin.com/in/oluwabusola-oyenuga)

---
*This project combines real survey data with synthetic data for sample-size purposes. Findings are directional and most representative of urban young professionals in South West Nigeria, where the sample is concentrated.*
