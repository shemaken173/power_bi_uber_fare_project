# 🚖 Power BI Uber Fare Analysis Project

The Power BI Uber Fare Analysis Project is a data visualization and business intelligence solution designed to provide actionable insights into Uber ride fares. Using the uber_enhanced dataset, the project analyzes key performance metrics such as Total Fare Amount, Average Fare Amount, and Trip Volume, enabling data-driven decision-making for ride pricing, customer trends, and operational efficiency.

## 📌 Project Overview
The **Power BI Uber Fare Analysis Project** is designed to analyze Uber trip fare data using interactive visualizations and DAX calculations. The goal is to identify fare patterns, revenue trends, and customer behavior insights for better business decision-making.

This project uses **Power BI** for dashboard creation and **DAX** for calculating key performance indicators (KPIs) like **Total Fare Amount**, **Average Fare**, and **Trip Count**.

---

## ✅ Key Features
- **Interactive Dashboard** built in Power BI
- **KPI Cards**:
  - Total Fare Amount
  - Average Fare Amount
  - Total Trips
- **Visualizations**:
  - Revenue Trends Over Time
  - Fare Distribution by Payment Type
  - Geographic Analysis of Pickup & Dropoff Locations
- **Dynamic Filters** for Date, Location, and Payment Method

## 📸Screenshots
<img width="640" height="480" alt="fare_boxplot" src="https://github.com/user-attachments/assets/5e0cbbf1-eb83-4348-b9ac-13c1f4afd1ad" />

<img width="640" height="480" alt="fare_by_hour" src="https://github.com/user-attachments/assets/9d788f5b-3456-4560-8cda-72c845a689d8" />

<img width="640" height="480" alt="correlation_matrix" src="https://github.com/user-attachments/assets/a3808219-d4c8-466c-9b27-39500539dc5f" />


<img width="881" height="491" alt="Main Dashboard" src="https://github.com/user-attachments/assets/7eb5c5f8-1a20-4daf-b08f-7d563710f8a0" />

## 📊 Dashboard KPIs & DAX Measures

### **1. Total Fare Amount**
```DAX
Total Fare Amount = SUM('uber_enhanced'[fare_amount])

Average Fare Amount = AVERAGE('uber_enhanced'[fare_amount])

Total Trips = COUNTROWS('uber_enhanced')

## 📊 Power BI Dashboard Features
Key Visualizations
1. Executive Summary Cards

Total Rides: 49,753
Average Fare: $14.27
Average Distance: 4.2 miles
Average Duration: 16.8 minutes

2. Time-Based Analysis

Hourly Demand Pattern: Line chart showing ride frequency by hour of day
Weekly Trends: Heatmap displaying ride patterns across days and hours
Monthly Revenue: Column chart tracking total revenue by month
Seasonal Analysis: Trend lines showing quarterly variations

3. Geographic Insights

Borough Performance: Map visualization with ride density and average fares
Route Analysis: Top pickup and dropoff locations with connection flows
Distance Distribution: Histogram showing trip length patterns

4. Pricing Analysis

Surge Impact: Scatter plot correlating surge multiplier with ride demand
Fare Components: Waterfall chart breaking down total fare structure
Price Elasticity: Line chart showing demand response to fare changes

Interactive Features

Date Range Slicer: Filter analysis by custom time periods
Location Filter: Focus on specific boroughs or neighborhoods
Ride Type Filter: Compare different Uber service categories
Weather Conditions: Analyze impact of weather on ride patterns

## 📈 Analysis & Insights
Total Fare Amount: Represents overall revenue.

Average Fare: Indicates pricing trends.

Peak Demand: Weekends and holiday seasons show higher revenue.

Payment Preferences: 65% of transactions are via card.

Geographic Impact: Certain zones account for 40% of revenue.

