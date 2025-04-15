# Mobile-sales-dashboard
An interactive Power BI dashboard analyzing mobile sales data with DAX measures, time intelligence, and customer insights.


# Mobile Sales Power BI Dashboard

This Power BI dashboard provides an interactive analysis of mobile sales data, enabling insights into sales trends, customer behavior, and brand performance over time.

## 📁 Dataset Overview

The dashboard uses two main datasets:

### Custom Calendar
- **Columns**: `Date`, `Day Name`
- A **Date Hierarchy** was created including: **Year**, **Quarter**, **Month**, **Day**

### Mobile Sales Data
- **Columns** include:
  - `Transaction ID`
  - `Date`
  - `Brand`
  - `Units Sold`
  - `Price per Unit`
  - `Customer Name`
  - `Age`
  - `City`
  - `Payment Method`
  - `Customer Ratings`
  - `Mobile Model`
  - `Rating Status` *(calculated)*

## 🧮 Key Calculated Measures

- **Transactions**:  
  `= COUNTROWS(Sales_Data)`

- **Total Sales**:  
  `= SUMX(Sales_Data, Sales_Data[Units Sold] * Sales_Data[Price Per Unit])`

- **Total Quantity Sold**:  
  `= SUM(Sales_Data[Units Sold])`

- **Rating Status**:  
  `= IF(Customer Ratings >= 4, "Good", IF(Customer Ratings > 2, "Average", "Poor"))`

- **Same Period Last Year (SPLY)**:  
  `= CALCULATE([Total Sales], SAMEPERIODLASTYEAR(Custom_Calendar[Date].[Date]))`

- **Month-To-Date (MTD) Sales**:  
  `= TOTALMTD([Total Sales], Custom_Calendar[Date].[Date])`

## 📌 Dashboard Insights

The dashboard presents the following insights:

- Monthly, Quarterly, and Yearly sales trends
- City-wise and brand-wise sales breakdown
- Sales comparison with the same period last year
- Customer ratings distribution with “Good”, “Average”, and “Poor” classification
- Payment method preferences
- Top-performing mobile models by sales

## 🛠️ Tools Used

- Power BI Desktop
- DAX for calculated columns and measures
- Excel for raw data
