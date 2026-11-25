# 🏦 Banking Data Warehouse & Fraud Analytics (Power BI + SQL Server)

An end-to-end Business Intelligence and Data Engineering solution designed to centralize, transform, and analyze banking transactions, customer demographics, and fraud patterns. Built using **SQL Server** (Medallion Architecture) and **Power BI** (Star Schema Modeling).

---

## 🏗️ Architecture & Data Modeling

### 1. Medallion Architecture (SQL Server)
The data warehouse (`BankingDW`) is structured into three distinct schemas to ensure data quality, lineage, and scalability:
* **🥉 Bronze Layer:** Raw data ingestion from transactional source systems.
* **🥈 Silver Layer:** Cleansed, standardized, and deduplicated data ready for analytical modeling.
* **🥇 Gold Layer:** Business-level aggregated tables structured in a **Star Schema** optimized for Power BI reporting.

### 2. Star Schema (Gold Layer)
The semantic model in Power BI connects a central fact table to three core dimension tables:
* **`Gold.FactTransaction`**: Contains transactional metrics (`amt`, `discount_amt`, `is_fraud`) and attributes (`category`, `channel`, `device_type`, `entry_mode`, `currency`).
* **`Gold.DimCustomer`**: Customer demographics and profile data (`customer_id`, `first_name`, `gender`, `dob`, `city`, `city_pop`, `job`, `cc_num`, `email_domain`).
* **`Gold.DimMerchant`**: Merchant details and geolocation (`merchant_id`, `merchant_name`, `dominant_category`, `merchant_city`, `merchant_state`, `merchant_lat`, `merchant_long`, `merchant_since`, `is_active`).
* **`Gold.DimDate`**: Time intelligence attributes (`datekey`, `full_date`, `day`, `day_name`, `month`, `month_name`, `quarter`, `year`, `is_weekend`).

---

## 📊 Power BI Dashboard Overview

The Power BI report is divided into three main analytical views, tracking **50,000 transactions** totaling **$3.18M** with an average ticket size of **$63.69**:

### 1. Executive & Transaction Overview
* **Key Metrics:** Total Amount (`$3.18M`), Total Transactions (`50.00K`), Average Ticket (`$63.69`), Total Discounts (`$158.09K`), and Overall Fraud Rate (`0.01` / `~0.62%`).
* **Trend Analysis:** Monthly transaction volume tracking (Jan–Jun).
* **Spend Breakdown:**
  * **By Category:** `Travel` leads spending (~$0.8M), followed by `Home` and `Shopping (Net)`.
  * **By Payment Method:** Balanced distribution across `Credit Card`, `Debit Card`, and `Digital Wallet`.
  * **By Channel:** Even split between `In-Store` and `Online` transactions.
* **Interactive Slicers:** Filter by `Transaction Status` (Approved, Declined, Refunded) and `Month`.

### 2. Fraud Detection & Risk Analysis
* **Fraud KPIs:** Tracks **310 flagged transactions** out of 50,000 total transactions.
* **Risk Vectors:**
  * **By Entry Mode:** `Online` entry mode accounts for the highest number of flagged transactions, followed by `Chip`, `Tap`, and `Swipe`.
  * **By Device Type:** `POS Terminal` shows the highest volume of flagged activity compared to `Tablet`, `Mobile`, and `Desktop`.
  * **By Category:** `Shopping (Net)`, `Home`, and `Kids & Pets` show the highest fraud frequency.
* **High-Risk Merchants:** A detailed table identifying merchants with the highest count of flagged transactions (e.g., *fraud_Stroman PLC*, *fraud_Stroman*, *fraud_Bailey Ltd*).

### 3. Customer Insights & Loyalty
* **Customer KPIs:** Analyzes **1,000 unique customers** generating `$3.18M` in total spend.
* **Demographics & Segmentation:**
  * **By Loyalty Tier:** Breakdown across `Platinum` (highest spend), `Bronze`, `Silver`, and `Gold`.
  * **By Geography:** `Texas (TX)` leads state-level transaction volume, followed by `California (CA)` and `North Carolina (NC)`.
  * **By Gender:** Balanced customer distribution between Female (`F`) and Male (`M`).
* **Top Customers Leaderboard:** Ranks high-value customers by total spend and transaction count (led by *Linda Rodriguez* with `$9,331.46` across 59 transactions).

---

## 🛠️ Tech Stack
* **Database & ETL:** Microsoft SQL Server (T-SQL)
* **Data Modeling:** Dimensional Modeling (Star Schema)
* **Data Visualization:** Microsoft Power BI Desktop (DAX, Power Query)

---

## 🚀 How to Use
1. **Database Setup:** Execute the SQL scripts in the `/sql` directory to initialize the `BankingDW` database and create the `Bronze`, `Silver`, and `Gold` schemas.
2. **Data Loading:** Run the ETL scripts to populate the tables and transform data into the Gold Star Schema.
3. **Power BI Report:** Open the `.pbix` file in Power BI Desktop, update the SQL Server connection string to point to your local/cloud instance, and click **Refresh**.

---

## 📸 Screenshots
*(Tip
