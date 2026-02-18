Automated Stock Forecasting Pipeline
A fully automated, end-to-end data pipeline that ingests equity data, generates 7-day price forecasts using Facebook Prophet, and visualizes insights via a dynamic Power BI dashboard.

🏗️ The Architecture
This project automates the transition from raw market data to actionable foresight:

Data Ingestion: A Python-based automation pulls daily historical closing prices for specific tickers via the Yahoo Finance API.

Predictive Modeling: The pipeline utilizes the Facebook Prophet algorithm to process time-series data and generate a 7-day forecast (yhat).

Cloud Storage: The processed dataset, containing both actual and predicted values, is automatically uploaded to Azure Blob Storage.

Live Visualization: Power BI Service is configured with a scheduled refresh to pull the latest data from Azure, ensuring the dashboard reflects the most recent 7-day outlook.

🛠️ Technical Implementation
The Python Forecasting Engine
The core script handles the model training and forecasting horizon.

Algorithm: Facebook Prophet for additive time-series forecasting.

Automation: Configured to run daily, ensuring the forecast window moves forward with the market.

Power BI & DAX Engineering
To handle the challenges of stock market data (such as weekends and holidays), the dashboard uses specialized DAX measures:

Current Price Baseline: Uses LASTNONBLANKVALUE to ensure the dashboard always shows the most recent "Actual" price, even when the timeline moves into future forecast dates.

Dynamic Timeframes: Implements relative date filtering to allow users to toggle between 1D, 7D, 1M, and 1Y views.

Accuracy Tracking: Includes a MAPE (Mean Absolute Percentage Error) calculation to quantify the model's reliability over time.

🚀 Impact & Results
Zero-Touch Automation: Eliminated manual data entry and model retraining by creating a scheduled cloud-native pipeline.

Executive Decision Support: Provides a 7-day price target and current market baseline in a single, mobile-accessible interface.

Scalability: The architecture is built to support multiple tickers by simply updating the ingestion parameters.

👤 Author
Chibuike ‘Chib’ Odibeli
Founder, Eden Enterprises | Master’s in Data Science Candidate, UMass Dartmouth.
