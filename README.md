# 📈 Eden Insights: Automated Stock Forecasting Pipeline

A fully automated, end-to-end data pipeline that ingests equity data, generates 7-day price forecasts using the Prophet algorithm, and visualizes insights via a dynamic Power BI dashboard.



## 🏗️ Architecture & Workflow
This project automates the transition from raw market data to actionable foresight for **Eden Enterprises**:

1.  **Data Ingestion:** A Python script automates the extraction of daily historical closing prices via the Yahoo Finance API.
2.  **Predictive Modeling:** The pipeline utilizes **Facebook Prophet** to process time-series data and generate a 7-day forecasting horizon (`yhat`).
3.  **Cloud Storage:** Processed datasets are automatically exported as `.csv` files and uploaded to **Azure Blob Storage**.
4.  **Live Visualization:** **Power BI Service** connects to the Azure cloud source with a scheduled refresh, ensuring the dashboard reflects the most recent predictions without manual intervention.

---

## 🛠️ Technical Stack
* **Modeling:** Python (Prophet, Pandas, NumPy).
* **Cloud Infrastructure:** Azure Machine Learning, Azure Blob Storage.
* **Analytics & BI:** Power BI Desktop/Service, DAX (Data Analysis Expressions).

---

## 📊 Data Engineering & DAX
To maintain data integrity and handle market closures, the dashboard implements custom DAX measures:

### Current Price Baseline
Ensures the "Today's Price" card always displays the last recorded actual value (`y`), ignoring empty forecast dates or weekend gaps.
```dax
Current Price = 
CALCULATE(
    LASTNONBLANKVALUE('stock-data'[ds], SUM('stock-data'[y])),
    ALL('stock-data')
)
