
# Mobile Sales Power BI Dashboard

This Power BI dashboard provides an interactive analysis of mobile sales data, enabling insights into sales trends, customer behavior, and brand performance over time.


## 🔹 Goal of the Dashboard
The goal was to build a user-friendly, data-rich dashboard that:
- Tracks total sales, transaction volume, and average price.
- Identifies top cities, brands, and mobile models.
- Analyzes customer feedback through rating status.
- Visualizes month-wise and weekday-wise trends.
- Highlights preferred payment methods to optimize customer experience.

- ## 🔹 Key Visuals Walkthrough
- **KPI Cards**: Show overall Total Sales (₹68M), Quantity Sold (2K units), Transactions (325), and Avg. Price (₹41.73K).
- **Pie Chart**: Displays total sales by top 10 cities (Delhi contributes the highest with 32.22%).
- **Line Chart**: Shows month-wise sales quantity, with July peaking.
- **Bar Chart**: Ratings breakdown by status (Good, Average, Poor).
- **Donut Chart**: Transactions by payment method – Credit Card and UPI lead.
- **Area Chart**: Day-wise total sales, with Tuesday showing the highest.
- **Horizontal Bar**: Top-performing mobile models – Vivo S1, Galaxy A57, and iPhone SE.
- **Table**: Brand-wise total sales and transaction counts.


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

- ## 🔹 Insights & Conclusion
- 📍 **Delhi** is the top-performing city in terms of sales.
- 📆 **July** saw the highest demand – great for launching new products or promotions.
- 💳 **Digital payments** dominate, especially Credit Cards and UPI.
- 🌟 **Customer satisfaction** is high, with the majority rating their experience as “Good”.
- 📈 **Tuesday** is the most profitable day for sales.
- 🏆 **Samsung and Apple** are the best-selling brands, with Vivo S1 leading among models.


## 🛠️ Tools Used

- Power BI Desktop
- DAX for calculated columns and measures
- Excel for raw data
