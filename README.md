

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

#### **1. Stock Price Trends Over Time**
- **Yearly Trends:**
  - **ENBD and FAB** demonstrated significant growth from 2014 to 2021, with ENBD peaking in 2021 before showing a slight decline.
  - **DIB and ADCB** displayed relatively stable growth, appealing to risk-averse investors.
  - The post-2021 decline for most banks correlates with global market uncertainties, possibly influenced by economic disruptions such as the pandemic.

- **Monthly Trends:**
  - A stable price movement across months suggests limited intra-year volatility, making these stocks a reliable investment for long-term holders.

**Visualization:**  
The **"Bank Stock Trends: Price Movement Over Time"** chart illustrates the gradual growth of stock prices over the years, with notable peaks in 2021 for ENBD and FAB. The monthly trend chart highlights the stability in short-term fluctuations.

---

#### **2. Trading Volume Analysis**
- **Volume Trends:**
  - DIB, despite its lower stock price, consistently records higher trading volumes, indicating its liquidity and appeal to a broad investor base.
  - FAB leads in both price and volume, reflecting strong investor confidence in its market leadership.

**Visualization:**  
The **"Trade Volume Analysis by Bank"** scatter plot shows the relationship between price and trading volume, while the bar chart highlights the 2021 volume spikes, likely due to market recovery post-COVID-19.

---

#### **3. Moving Average Analysis**
- The 5-day and 10-day moving averages show a consistent upward trend from 2016 to 2021, reflecting steady growth.
- Post-2021, moving averages plateau, indicating market stabilization.

**Visualization:**  
The **"Moving Average Trends"** chart showcases how short-term (MA5) and medium-term (MA10) trends closely track each other, reflecting consistent price stability.

---

#### **4. Macroeconomic Dependencies**
- The **DFM Index** aligns closely with **Brent Oil prices**, underscoring the UAE’s reliance on energy markets.
- Both indices experienced a sharp decline in 2020 due to the global economic downturn but rebounded strongly in 2021.

**Visualization:**  
The **"DFM Index vs. Brent Oil Prices"** bar chart vividly displays the synchronized movements of the two indicators, emphasizing the UAE economy’s dependence on oil prices.

---

#### **5. Price Changes Across Banks**
- ENBD and FAB experienced significant year-on-year price changes, particularly in 2014 and 2021, driven by macroeconomic growth and recovery phases.
- ADCB and DIB remained stable, appealing to conservative investors.

**Visualization:**  
The **"Heatmap of Price Changes Across Banks"** highlights the variability in price changes, with ENBD showing more dynamic movement compared to its peers.

---

#### **6. Actual vs. Predicted Prices**
- **Predicted Trends:**
  - Predictions for daily prices align closely with actual trends, showcasing the model's short-term accuracy.
  - Monthly forecasts, however, deviate significantly for ENBD post-2024, suggesting the need for improved long-term modeling techniques.
- **Residual Analysis:**
  - Absolute errors are higher for monthly forecasts, particularly for FAB and ENBD, reflecting their higher volatility.

**Visualization:**  
The **"Actual vs. Predicted Prices Over Time"** chart compares historical and forecasted prices, highlighting the model's strengths and weaknesses. The **"Absolute Error by Forecast Type and Bank Name"** bar chart emphasizes the challenges in long-term forecasting.

---

### **Challenges and Future Directions**
1. **Data Quality:** Managing missing values in external datasets and aligning them with stock data posed challenges.
2. **Model Refinement:** Monthly forecasts require additional tuning to reduce variance.
3. **Market Dynamics:** Incorporating sentiment analysis or news data could enhance prediction accuracy.

---

### **Conclusion**
This project offers a robust framework for analyzing and forecasting stock prices in the UAE banking sector. By integrating market trends, macroeconomic factors, and machine learning, it provides valuable insights for investors and policymakers alike.



