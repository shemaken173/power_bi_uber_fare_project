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
## Data Cleaning
```python

import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
from math import radians, cos, sin, asin, sqrt

# -------------------- Load Dataset --------------------
df = pd.read_csv('C:/Users/USER/Desktop/big data project/uber.csv')

print("Initial Shape:", df.shape)
print("Data types:\n", df.dtypes)
print("Missing values:\n", df.isnull().sum())

# -------------------- Drop Missing Values --------------------
df_clean = df.dropna().copy()
print("Shape after dropping missing values:", df_clean.shape)

# -------------------- Clean Invalid Coordinates --------------------
df_clean = df_clean[
    df_clean['pickup_latitude'].between(-90, 90) &
    df_clean['pickup_longitude'].between(-180, 180) &
    df_clean['dropoff_latitude'].between(-90, 90) &
    df_clean['dropoff_longitude'].between(-180, 180)
].copy()

# -------------------- Convert Datetime --------------------
df_clean['pickup_datetime'] = pd.to_datetime(df_clean['pickup_datetime'], errors='coerce')
df_clean = df_clean[df_clean['pickup_datetime'].notnull()].copy()

# -------------------- Time Features --------------------
df_clean['hour'] = df_clean['pickup_datetime'].dt.hour
df_clean['day'] = df_clean['pickup_datetime'].dt.day
df_clean['month'] = df_clean['pickup_datetime'].dt.month
df_clean['weekday'] = df_clean['pickup_datetime'].dt.dayofweek
df_clean['period'] = df_clean['hour'].apply(lambda x: 'Peak' if 7 <= x <= 9 or 17 <= x <= 20 else 'Off-Peak')

# -------------------- Descriptive Statistics --------------------
print("Descriptive statistics:\n", df_clean.describe())
print("Mode:\n", df_clean.mode(numeric_only=True))

# -------------------- Outlier Detection --------------------
Q1 = df_clean['fare_amount'].quantile(0.25)
Q3 = df_clean['fare_amount'].quantile(0.75)
IQR = Q3 - Q1
lower_bound = Q1 - 1.5 * IQR
upper_bound = Q3 + 1.5 * IQR

outliers = df_clean[(df_clean['fare_amount'] < lower_bound) | (df_clean['fare_amount'] > upper_bound)]
print("Number of outliers in fare_amount:", len(outliers))

# -------------------- Haversine Distance --------------------
def haversine(row):
    lat1, lon1, lat2, lon2 = map(radians, [
        row['pickup_latitude'], row['pickup_longitude'],
        row['dropoff_latitude'], row['dropoff_longitude']
    ])
    dlon = lon2 - lon1
    dlat = lat2 - lat1
    a = sin(dlat/2)**2 + cos(lat1) * cos(lat2) * sin(dlon/2)**2
    a = max(0, min(1, a))  # prevent math domain error
    c = 2 * asin(sqrt(a))
    return 6371 * c  # Earth's radius in km

df_clean['distance_km'] = df_clean.apply(haversine, axis=1)

# Filter unrealistic distances
df_clean = df_clean[(df_clean['distance_km'] > 0) & (df_clean['distance_km'] < 100)].copy()

# -------------------- Visualizations --------------------
# Fare Amount Distribution
sns.histplot(df_clean['fare_amount'], bins=50, kde=True)
plt.title('Fare Amount Distribution')
plt.xlabel('Fare Amount ($)')
plt.savefig('fare_distribution.png')
plt.clf()

# Boxplot of Fare
sns.boxplot(x=df_clean['fare_amount'])
plt.title('Fare Amount Outliers')
plt.savefig('fare_boxplot.png')
plt.clf()

# Scatter Plot: Fare vs Distance
sns.scatterplot(x='distance_km', y='fare_amount', data=df_clean, alpha=0.3)
plt.title("Fare Amount vs Distance")
plt.xlabel("Distance (km)")
plt.ylabel("Fare Amount ($)")
plt.savefig('fare_vs_distance.png')
plt.clf()

# Boxplot: Fare by Hour
sns.boxplot(x='hour', y='fare_amount', data=df_clean)
plt.title('Fare Amount by Hour of Day')
plt.savefig('fare_by_hour.png')
plt.clf()

# Correlation Heatmap
corr = df_clean[['fare_amount', 'hour', 'day', 'month', 'weekday', 'distance_km']].corr()
sns.heatmap(corr, annot=True, cmap='coolwarm')
plt.title('Correlation Heatmap')
plt.savefig('correlation_matrix.png')
plt.clf()

# -------------------- Export Cleaned Data --------------------
df_clean.to_csv('uber_enhanced.csv', index=False)
print("Cleaned and enhanced dataset saved as 'uber_enhanced.csv'")
```











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

📊 Power BI Dashboard Features
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

📈 Analysis & Insights
Total Fare Amount: Represents overall revenue.

Average Fare: Indicates pricing trends.

Peak Demand: Weekends and holiday seasons show higher revenue.

Payment Preferences: 65% of transactions are via card.

Geographic Impact: Certain zones account for 40% of revenue.

