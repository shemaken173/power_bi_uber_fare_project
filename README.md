# power_bi_uber_fare_project
The Power BI Uber Fare Analysis Project is a data visualization and business intelligence solution designed to provide actionable insights into Uber ride fares. Using the uber_enhanced dataset.
The Power BI Uber Fare Analysis Project is a data visualization and business intelligence solution designed to provide actionable insights into Uber ride fares. Using the uber_enhanced dataset, the project analyzes key performance metrics such as Total Fare Amount, Average Fare Amount, and Trip Volume, enabling data-driven decision-making for ride pricing, customer trends, and operational efficiency.
# 🚖 Power BI Uber Fare Analysis Project

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

---

## 📂 Repository Structure
PowerBI-Uber-Fare-Project/
│
├── data/
│ └── uber_enhanced.csv # Cleaned dataset used in the dashboard
│
├── screenshots/
│ ├── <img width="640" height="480" alt="fare_boxplot" src="https://github.com/user-attachments/assets/fd5768a1-4fc0-46f3-933f-1d75bc24f30e" />

│ ├── <img width="640" height="480" alt="fare_by_hour" src="https://github.com/user-attachments/assets/1bc1da9d-2a2f-4d03-96df-4d9667aa3b05" />

│ ├── <img width="640" height="480" alt="correlation_matrix" src="https://github.com/user-attachments/assets/49808c4a-e2d0-40e3-b508-3071911b28c0" />

│ └── <img width="881" height="491" alt="Main Dashboard" src="https://github.com/user-attachments/assets/e0bfaaf2-e086-4088-8ad3-3a5b762f5549" />


---

## 📊 Dashboard KPIs & DAX Measures

### **1. Total Fare Amount**
```DAX
Total Fare Amount = SUM('uber_enhanced'[fare_amount])
Average Fare Amount = AVERAGE('uber_enhanced'[fare_amount])
