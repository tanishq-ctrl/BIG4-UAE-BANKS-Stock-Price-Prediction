

### **Title: UAE Banking Sector Analysis: Forecasting Stock Prices with Machine Learning**

---

### **Introduction:**
The UAE banking sector is a dynamic and integral component of the nation's economy. This project focuses on analyzing and forecasting stock prices for four major banks — Emirates NBD (ENBD), Dubai Islamic Bank (DIB), First Abu Dhabi Bank (FAB), and Abu Dhabi Commercial Bank (ADCB). By integrating historical stock data with macroeconomic indicators and leveraging machine learning, we aim to uncover trends, insights, and actionable predictions for the future.

This repository combines rigorous data preprocessing, advanced feature engineering, and Random Forest-based modeling to predict stock prices with precision.

---

### **Data Collection and Integration**
The journey began with collecting historical stock price data from reliable sources for each bank. Additionally, macroeconomic indicators such as the DFM Index, Brent Oil prices, USD to AED exchange rates, and GDP figures were incorporated to provide a holistic view of the market.

**Steps:**
1. Individual stock price datasets were loaded and labeled with their respective bank names.
2. External datasets, including oil prices, exchange rates, and GDP data, were collected to enhance the dataset with meaningful features.

---

### **Data Preprocessing**
Preprocessing involved transforming raw datasets into a format suitable for modeling while handling missing values and standardizing features. Key steps included:

1. **Combining Stock Data:**
   - Stock data from all four banks was consolidated into a single master dataset.
   - A `Bank Name` column was added to distinguish data across banks.

2. **Handling Missing Values:**
   - Missing values in trading volume (`Vol.`) were converted to numeric values and filled with the mean.
   - Missing values in macroeconomic indicators were forward-filled for continuity.

3. **Feature Engineering:**
   - **Lagged Features:** Created `Price Lag 1` and `Change % Lag 1` to capture past trends.
   - **Moving Averages:** Added 5-day (`Price MA 5`) and 10-day (`Price MA 10`) moving averages for smoothing.
   - **Interaction Features:** Calculated `Price per Vol` to assess price efficiency relative to trading volume.

4. **Merging Macroeconomic Data:**
   - DFM Index, Brent Oil prices (converted to AED), and GDP data were merged on a daily basis.
   - Missing GDP values were filled using forward and backward filling techniques, and expanded to daily granularity.

5. **Normalization:**
   - Numerical columns were scaled using MinMaxScaler to ensure consistent feature ranges for machine learning.

**Outcome:** A clean, feature-rich dataset ready for predictive modeling, saved as `enhanced_stock_data.csv`.

---

### **Modeling: Predicting Stock Prices with Random Forest**
Random Forest, a robust ensemble learning algorithm, was employed to predict stock prices. The modeling workflow involved:

1. **Data Encoding:**
   - The `Bank Name` column was encoded as integers to ensure compatibility with the model.

2. **Feature Selection:**
   - Selected a range of numerical features, including price-related metrics, macroeconomic indicators, and lagged values.

3. **Forecasting Approach:**
   - Separate models were trained for each bank using an 80-20 time-based train-test split.
   - Predictions were made for:
     - **Daily Forecasts:** For the next 30 days.
     - **Monthly Forecasts:** For up to 24 months.

4. **Recalibration and Restoration:**
   - Predicted prices were restored to their original scale using MinMaxScaler.
   - Predictions were recalibrated to align with the most recent actual prices.

5. **Combining Predictions:**
   - Daily and monthly forecasts were combined, labeled by `Prediction Type`, and merged with actual prices for comparative analysis.

**Outcome:** A comprehensive dataset of actual and predicted prices, saved as `combined_forecasts.csv`.

---

### **Key Insights**
**1. Stock Price Trends:**
- ENBD and FAB exhibited significant growth, particularly during 2021, aligning with global recovery trends.
- DIB showed lower price levels but higher trading volumes, reflecting investor interest in its stability.

**2. Macroeconomic Impact:**
- A strong correlation was observed between Brent Oil prices and the DFM Index, highlighting the UAE’s dependency on energy markets.

**3. Forecasting Accuracy:**
- **Daily Forecasts:** Showed higher accuracy due to reduced compounding errors.
- **Monthly Forecasts:** Displayed greater variance, particularly for ENBD, indicating the need for refinement.

---

### **Visual Storytelling**
Visualizations played a vital role in communicating insights:
- **Line Charts:** To compare actual vs. predicted prices over time.
- **Scatter Plots:** To analyze residuals and forecast accuracy.
- **Bar Charts:** To highlight errors across banks and prediction types.
- **Heatmaps:** To visualize year-on-year price changes across banks.

Explore the interactive dashboards and code implementations in the repository to dive deeper into the findings.

---

### **Challenges and Future Directions**
1. **Data Quality:** Managing missing values in external datasets and aligning them with stock data posed challenges.
2. **Model Refinement:** Monthly forecasts require additional tuning to reduce variance.
3. **Market Dynamics:** Incorporating sentiment analysis or news data could enhance prediction accuracy.

---

### **Conclusion**
This project offers a robust framework for analyzing and forecasting stock prices in the UAE banking sector. By integrating market trends, macroeconomic factors, and machine learning, it provides valuable insights for investors and policymakers alike.



