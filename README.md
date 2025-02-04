### ****Project Title: Credit Fraud Detection and Transaction Analysis****

#### ****Objective:****

To analyze transaction data, identify patterns and trends, and determine key indicators of fraudulent transactions using the fraudornot column as the target variable.

### ****Dataset Overview:****

The datasets were collected from Kaggle and include the following:

* **transactions\_data.csv**: Transaction-level data.
* **mcc\_codes.json**: Merchant category codes for mapping.
* **train\_fraud\_labels.json**: Labels indicating fraudulent transactions.

### ****Business Questions:****

1. What percentage of transactions are fraudulent?
2. Are there specific merchant categories or locations with higher fraud rates?
3. Does the type of transaction affect the likelihood of fraud?
4. How do fraud rates compare across Swipe and Chip transactions?
5. What is the average transaction amount for fraudulent vs. non-fraudulent transactions?
6. Are there specific days, times, or months when fraud is more likely to occur?
7. Which customers are most frequently involved in fraudulent transactions?
8. Are there patterns in transaction amounts or merchant categories that correlate with fraud?

### ****Excel Tools Used:****

* **Pivot Tables**: For summarizing and analyzing data.
* **Charts**: For visualizing trends and patterns.
* **VLOOKUP**: For mapping merchant category codes (MCC) to transaction data.
* **Conditional Formatting**: To highlight key insights and outliers.
* **Formulas**: Including COUNTIF, COUNTIFS, AVERAGEIF, TEXT TO COLUMNS, SORT, and FILTER for data manipulation and analysis.

### ****Methodology:****

#### ****1. Data Cleaning and Preparation:****

* **Sampling:** Sampled 8,000 data points from 8,914,963 transactions due to Excel's limitations. Since only 0.15% of transactions were flagged as fraudulent, oversampling was performed to include 400 fraud transactions. After cleaning, 41 fraudulent transactions remained.
* **Remove Duplicates:** Used Excel’s **Remove Duplicates** feature to eliminate 7 duplicate rows.
* **Handle Missing Values:** Removed rows with missing values, resulting in a cleaned dataset of 6,693 rows.
* **Format Data:** Ensured consistent data formats across all columns.
* **Replace Binary Values:** Used =IF to replace "Yes" with 1 and "No" with 0 in binary columns.
* **Convert Transaction Amounts:** Used =SUBSTITUTE and =VALUE to remove the "$" sign and convert the amount column to numeric format.
* **Trim MCC Column:** Used =TRIM to clean the mcc column for accurate VLOOKUP mapping.
* **Extract Date Features:** Used the following functions to extract additional features from the date column:
  + **Day of the Week:** =TEXT(date, "dddd").
  + **Hour of the Day:** =HOUR(date).
  + **Month of the Year:** =MONTH(date).

#### ****2. Exploratory Data Analysis (EDA):****

* **Overall Fraud Rate:** Calculated using =COUNTIF(fraudornot, 1) / COUNTA(fraudornot).
* **Fraud by Merchant Category:** Analyzed fraud rates by mcc using pivot tables and VLOOKUP to map MCC codes to categories.
* **Fraud by Location:** Identified high-risk cities and states using pivot tables for merchant\_city and merchant\_state.
* **Fraud by Transaction Type:** Compared fraud rates across Swipe and Chip transactions using =COUNTIFS and pivot tables.
* **Transaction Amount Analysis:** Calculated the average transaction amount for fraudulent and non-fraudulent transactions using =AVERAGEIF.
* **Time-Based Analysis:** Analyzed fraud trends by:
  + **Day of the Week:** =WEEKDAY(date).
  + **Hour of the Day:** =HOUR(date).
  + **Month of the Year:** =MONTH(date).
  + **Year:** =YEAR(date).

#### ****3. Fraud Detection Analysis:****

* **High-Risk Merchant Categories:** Identified using pivot tables and =SORT to rank categories by fraud rates.
* **High-Risk Locations:** Identified using pivot tables and =SORT to rank cities and states by fraud rates.
* **Customer Analysis:** Used =COUNTIFS to identify customers (client\_id) with the most fraudulent transactions.
* **Transaction Type Analysis:** Used =COUNTIFS and pivot tables to determine if certain transaction types (use\_chip) are more prone to fraud.

#### ****4. Visualization:****

* Created a **dashboard** to visualize insights and patterns using:
  + **Bar Charts**: To compare fraud rates by merchant category, location, and transaction type.
  + **Line Graphs**: To show time-based trends in fraudulent activity.
  + **Pie Charts**: To highlight the distribution of fraud by transaction type.
  + **Conditional Formatting**: To emphasize high-risk categories and trends.

### ****Key Findings:****

1. **Fraud Rate:** Out of 6,692 transactions, 41 were fraudulent, with an average fraud amount of **104.72∗∗*comparedto*∗∗64.33** for non-fraudulent transactions.

104.72∗∗comparedto∗∗

1. **High-Risk Merchant Categories:** The top categories with the highest fraud rates include:
   * Wholesale Clubs (26.83%).
   * Discount Stores (9.76%).
   * Grocery Stores and Supermarkets (7.32%).
   * Drug Stores and Pharmacies (7.32%).
2. **High-Risk Locations:** States with the highest fraud rates are **Ohio (OH)**, **California (CA)**, **Pennsylvania (PA)**, and **Florida (FL)**.
3. **Transaction Type:** Swipe transactions accounted for **78.05%** of fraudulent transactions.
4. **Time-Based Trends:**
   * Fraudulent activity peaked in **August** and **June**.
   * The highest fraud rates occurred on **Tuesdays** and **Thursdays**.
   * The average fraud amount increased significantly from **2012 to 2018**, while no fraud was detected in other years (likely due to limited data).
5. **Customer Analysis:** Identified top customers involved in fraudulent transactions, providing actionable insights for further investigation.

### ****Actionable Recommendations:****

1. **Enhanced Monitoring:** Focus on high-risk merchant categories and locations to detect and prevent fraud.
2. **Promote Chip-Enabled Transactions:** Encourage the use of chip-enabled cards for in-person transactions to reduce fraud.
3. **Real-Time Fraud Detection:** Implement real-time monitoring systems during high-risk times (e.g., peak hours, specific days, or months).
4. **Customer Analysis:** Investigate high-risk customers to identify potential fraud rings or patterns.
