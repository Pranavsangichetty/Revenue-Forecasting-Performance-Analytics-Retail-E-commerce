# 📈 Revenue Forecasting & Performance Analytics (Retail / E-commerce)

### *End-to-End Machine Learning + Business Intelligence Project*

## 📝 Project Overview

This project delivers an end-to-end **sales forecasting and performance analytics solution** for a retail/e-commerce business. It highlights expertise across the full data workflow — from data engineering and feature creation using SQL & Python, to machine learning–based revenue forecasting, and enterprise-grade visualization using Power BI.

The goal is to equip business stakeholders with **data-driven insights** into revenue trends, category-level performance, forecasting accuracy, and key drivers affecting sales, enabling strategic planning and proactive decision-making.

---

## 📂 Repository Contents

| File Name                         | Type            | Description                                                                                                                                                   |
| --------------------------------- | --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `retail_sql_data_model.sql`       | SQL Script      | Creates tables, cleans dimension & fact data, and prepares aggregated monthly sales datasets used for modeling.                                               |
| `revenue_forecasting_model.ipynb` | Python Notebook | Full ML pipeline: feature engineering, lag/rolling features, model training (Random Forest / XGBoost), forecast generation, and export of prediction outputs. |
| `Fact_Forecast.csv`               | Data Output     | Machine learning forecast output imported into Power BI as a forecast fact table.                                                                             |
| `Retail_Revenue_Forecasting.pbix` | Power BI Report | Interactive dashboards including actual vs forecast revenue, margin trends, category performance, and forecast accuracy (MAPE).                               |
| `raw_data/`                       | Data Source     | Contains raw order, customer, product, region, marketing spend, and calendar datasets.                                                                        |

---

## ⚙️ Tech Stack

| Component                 | Tool / Language                      | Purpose                                                                                          |
| ------------------------- | ------------------------------------ | ------------------------------------------------------------------------------------------------ |
| **Data Backend**          | MySQL / SQL                          | Data storage, cleaning, aggregation, feature creation for modeling.                              |
| **Machine Learning**      | Python (Pandas, Scikit-Learn, NumPy) | Time-series feature engineering, model training, multi-step forecasting.                         |
| **Business Intelligence** | Microsoft Power BI                   | Interactive dashboards for revenue analysis, forecast vs actual, and category/regional insights. |
| **Modeling Logic**        | DAX                                  | KPI calculations (Revenue, AOV, Margin %), forecast error metrics, YoY comparisons.              |
| **Data Transformation**   | Power Query (M Language)             | Data ingestion and normalization before loading into Power BI.                                   |

---

## 🏗️ Data Engineering & Preparation (MySQL + SQL)

The `retail_sql_data_model.sql` script performs all required backend transformations:

### **1️⃣ Data Cleaning**

* Standardizes date formats (OrderDate, ShipDate).

* Removes duplicates using ranking functions.

* Normalizes categorical fields (Region, Category, Channel).

### **2️⃣ Data Aggregation**

* Generates monthly revenue summaries by **Region**, **Product Category**, and **Channel**.

* Creates a **cleaned star-schema**:

  * `FactSales`, `DimDate`, `DimCustomer`, `DimProduct`, `DimRegion`, `DimChannel`.

### **3️⃣ Modeling Dataset**

Provides a machine-learning-ready dataset containing:

* Lag features (Revenue_Lag_1, Lag_2, Lag_3)

* Rolling averages (3-month, 6-month)

* Discount & marketing spend features

* Seasonality indicators (Holiday, Festive)

### **4️⃣ SQL Views for Power BI**

Optimized views for fast dashboard performance:

* `vw_monthly_revenue`

* `vw_region_category_metrics`

* `vw_customer_segment_performance`

* `vw_marketing_spend_impact`

These views serve as the primary source for Power BI visuals.

---

## 🤖 Machine Learning Forecasting (Python)

The `revenue_forecasting_model.ipynb` notebook contains the complete forecasting workflow:

### **1️⃣ Feature Engineering**

* Time-based features → Month, Year, Quarter

* Holiday & festive season flags

* Lagged revenue values

* Rolling-window moving averages

* Marketing spend & discount rate impact

### **2️⃣ Model Training**

Models tested include:

* Random Forest Regressor

* XGBoost Regressor

* Linear Regression baseline

Models were evaluated using:

* **MAE (Mean Absolute Error)**

* **RMSE (Root Mean Squared Error)**

* **MAPE (Mean Absolute Percentage Error)**

### **3️⃣ Forecast Generation**

Produces **3–6 month forecasts** for

✔ Regions

✔ Product Categories

✔ Channels

Results are exported as `Fact_Forecast.csv` to be used in Power BI.

---

## 📊 Power BI Dashboard Insights & Features

The **Retail_Revenue_Forecasting.pbix** dashboard showcases 4 analytical pages:

---

### 🏠 **1. Executive Summary**

High-level overview of business performance.

**Visuals:**

* Revenue, Forecasted Revenue, Margin %, AOV (KPI Cards)

* Revenue trend with forecast overlay

* Top performing categories & regions

---

### 📈 **2. Forecast vs Actual**

Compare machine learning predictions with real sales performance.

**Visuals:**

* Actual vs Forecast line chart

* Forecast accuracy metrics (MAE, RMSE, MAPE)

* Drill-down by category, region, and channel

---

### 📦 **3. Category & Product Performance**

Deep dive into what drives revenue.

**Visuals:**

* Category-wise revenue and margin

* Product-level drill-through

* Discount impact analysis

---

### 🌍 **4. Regional & Channel Insights**

Analyze geographic and channel-level performance.

**Visuals:**

* Map of revenue by region

* Channel performance comparison

* Marketing spend effectiveness

---

## 🚀 Setup & How to Run

### **1️⃣ SQL Setup**

1. Open MySQL Workbench.

2. Run `retail_sql_data_model.sql` to create tables and views.

3. Load raw CSV files into respective dimension & fact tables.

4. Execute final SQL to generate modeling dataset & aggregates.

---

### **2️⃣ Python ML Setup**

1. Install required libraries:

   ```bash
   pip install pandas scikit-learn numpy xgboost
   ```

2. Open `revenue_forecasting_model.ipynb`.

3. Run all cells to train the model and generate forecast outputs.

4. Export `Fact_Forecast.csv` for Power BI use.

---

### **3️⃣ Power BI Setup**

1. Open the `Retail_Revenue_Forecasting.pbix` file.

2. Update data source connections (SQL Views + Forecast CSV).

3. Refresh the model to load the latest forecast outputs.

---

## 🎯 Future Enhancements

* **Automated Forecast Pipeline**
  Deploy ML model using Airflow / Azure Data Factory for scheduled forecasts.

* **Real-Time Dashboard Refresh**
  Connect to a cloud SQL server with scheduled Power BI refresh.

* **Advanced ML Models**
  Implement Prophet, LSTM models, or hierarchical forecasting.

* **Cloud Deployment**
  Publish dashboard to Power BI Service with RLS for secure stakeholder access.

