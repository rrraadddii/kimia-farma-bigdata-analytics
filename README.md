# 🏬 Kimia Farma – Big Data Analytics Project (2020–2023)

This project is the final task of a **Project-Based Internship** as a **Big Data Analyst Intern** at Kimia Farma.  
The goal is to analyze Kimia Farma's business performance from 2020 to 2023 using **Google BigQuery** and **Looker Studio**.

## 📋 Table of Contents
1. [Project Summary](#project-summary)
2. [Prerequisites](#prerequisites)
3. [Workflow](#workflow)
4. [SQL Query](#sql-query)
5. [Looker Studio Dashboard](#looker-studio-dashboard)
6. [Business Questions & Answers](#business-questions--answers)
7. [How to Use](#how-to-use)
8. [Technologies Used](#technologies-used)

---

## 📌 Project Summary

As a Big Data Analyst Intern, I was tasked to:
1. Import 4 CSV datasets into BigQuery.
2. Create an analysis table with calculated profit columns.
3. Build an interactive dashboard in Looker Studio.
4. Prepare a presentation (PPT) and a walkthrough video.

**Datasets:**
- `kf_final_transaction.csv` – transaction data
- `kf_kantor_cabang.csv` – branch data
- `kf_product.csv` – product data
- `kf_inventory.csv` – inventory data

---

## 🛠️ Prerequisites

- Google account (Gmail)
- Access to **Google Cloud Platform** (project: `bigdatanalayst-kimiafarma`)
- Dataset `kimia_farma` in BigQuery
- **Looker Studio** account (login with the same Gmail)

---

## 📋 Workflow

### 1. BigQuery Setup
- Create project `bigdatanalayst-kimiafarma` (or use an existing one).
- Create dataset `kimia_farma`.
- Upload the 4 CSV files as tables (table names without `.csv`).

### 2. Creating the Analysis Table (SQL)
- The query joins the 4 tables using `LEFT JOIN`.
- Calculated columns added:
  - `persentase_gross_laba` – based on price range (CASE WHEN).
  - `nett_sales` – price after discount.
  - `nett_profit` – net profit.
- The query is saved in [`sql/kf_analysis_query.sql`](sql/kf_analysis_query.sql).

### 3. Building the Looker Studio Dashboard
- Connect BigQuery to Looker Studio.
- Dashboard elements:
  - **Scorecard:** total transactions, nett sales, nett profit, average rating.
  - **Filters:** date, province.
  - **Time series:** nett sales per year.
  - **Bar chart:** Top 10 provinces (transactions and nett sales).
  - **Table:** Top 5 branches (high branch rating, low transaction rating).
  - **Geo chart:** profit map by province.
  - **Additional analysis:** best-selling products, average discount.

### 4. Documentation
- This GitHub repository contains SQL, dashboard link, and README.
- Presentation video uploaded to YouTube/Drive (link in the final PPT).

---

## 🔗 Looker Studio Dashboard

Access the interactive dashboard here:  
👉 [**Kimia Farma Performance Analytics 2020-2023**](https://datastudio.google.com/reporting/ecd5ccc8-a88a-4d53-ad5b-05707fad6cab)

---

## ❓ Business Questions & Answers

### 1. How did Kimia Farma's revenue trend from 2020 to 2023?
**Answer:**  
Annual revenue **tended to decline**, but with a clear seasonal pattern: **peak always occurred in Q4** (year-end), followed by a **sharp drop in Q1** of the next year.

### Pattern
- Every year: Q4 peak → Q1 drop (post‑holiday slump).
- A deeper drop occurred every **two years**:
  - **End of 2020 → Q1 2021**: down **2.73%** (IDR 88B → 85.6B)
  - **End of 2022 → Q1 2023**: down **1.82%** (87.9B → 86.3B)
  - (End of 2021 → Q1 2022: only -1.26%)

### Additional Insights
- **Year‑end optimization** (promotions, seasonal demand) successfully boosted sales, but the effect did **not carry over** into early next year.
- The **sharpest drop was in Q1 2021**, indicating the pandemic impact was still strong after the holidays.
- After 2022, Q1 recovery improved slightly, but overall **no positive yearly growth** – revenue stagnated around IDR 347–349B per year.

### Conclusion
Revenue did not grow; it slowly declined with a **peak‑in‑Q4, drop‑in‑Q1** pattern. A strategy is needed to maintain momentum after year‑end.

---

### 2. Which provinces have the highest total transactions and nett sales?
**Answer:**  

- **Top 3 transactions**: West Java, North Sumatra, Central Java.
- **Top 3 nett sales**: West Java, North Sumatra, Central Java.

**West Java dominates both in volume and sales value.**

---

### 3. Which branches have high branch ratings but low transaction ratings (need evaluation)?
**Answer:**  
Based on the top 5 cities (city level, aggregating multiple branches) with the highest average branch ratings (4.42–4.49) but relatively lower average transaction ratings (3.97–4.05):

## Conclusion
The gap between branch rating and transaction rating is small (0.4–0.5 points). However, **Ciamis, Subang, and Purwakarta** have transaction ratings below 4.0 — these require attention.

## Top 5 Cities Data
(Cities with highest average branch rating, filtered for lowest transaction ratings among them)

| City       | Avg Branch Rating | Avg Transaction Rating | Transaction Count (distinct) |
|------------|------------------|------------------------|------------------------------|
| Ciamis     | 4.49             | 3.97                   | 1,120                        |
| Subang     | 4.46             | 3.98                   | 1,494                        |
| Purwakarta | 4.42             | 3.99                   | 1,322                        |
| Garut      | 4.43             | 4.01                   | 1,366                        |
| Sukabumi   | 4.46             | 4.05                   | 1,103                        |

## Business Insights

- Branches in these cities are rated highly for **facilities and location** (high branch rating), but the **transaction experience** (cashier service, queue management, speed) is slightly less satisfactory than expected.
- Although transaction ratings are still fairly good (>3.9), the gap indicates a **satisfaction imbalance** — customers like the place but are less happy with the transaction process.
- High transaction volumes (1,100–1,500 distinct transactions) mean that even small issues can have a significant impact on customer experience.

## Recommendations

- Focus on evaluating **cashier SOPs and queue management** in **Ciamis and Subang** (largest gap + transaction rating below 4.0).
- Conduct **mystery shopping** or **waiting time surveys** to identify bottlenecks.
- Consider staff training and process improvements to align transaction experience with the already high branch perception.

---

### 4. How is the profit distributed by province?
**Answer:**  
Geo chart shows:
- **Highest profit**: West Java, North Sumatra, Central Java.
- **Low profit**: West Papua, Central Sulawesi, East Nusa Tenggara.

### Suggestion
Evaluate operational costs in low‑profit regions, or increase promotions there.

---

*Prepared based on Kimia Farma internal data (2020–2023).*
## 🚀 How to Use

1. Clone this repository:
   ```bash
   git clone https://github.com/rrraadddii/kimia-farma-bigdata-analytics.git
