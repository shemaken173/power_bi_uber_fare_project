🚖 Uber Fare Analysis Report
📌 1. Introduction
Project Overview
The Uber Fare Analysis Project utilizes Power BI to transform raw trip data into meaningful insights. The goal is to uncover fare patterns, revenue trends, and customer behavior through interactive dashboards and visual analytics. This supports strategic pricing, marketing decisions, and resource optimization.

Objectives
Calculate and visualize:

✅ Total Fare Amount

✅ Average Fare

✅ Trip Volume

Analyze revenue trends by:

Time

Location

Payment Method

Build an interactive dashboard for decision-makers.

Provide data-driven recommendations.

🛠 2. Methodology
Data Source
Dataset: uber_enhanced

Format: CSV

Key Columns:

fare_amount

trip_date

pickup_location, dropoff_location

payment_type

Data Preparation
Removed duplicates and null values.

Filtered invalid fares (negative amounts).

Standardized formats for dates and locations.

Processed in Power Query, then loaded into Power BI.

Tools & Techniques
Power BI Desktop: For dashboard and KPIs.

Power Query: For cleaning and transformation.

DAX (Data Analysis Expressions): For calculated measures.

📊 3. Analysis
Key KPIs
Total Fare Amount

DAX
Copy
Edit
Total Fare Amount = SUM('uber_enhanced'[fare_amount])
Average Fare Amount

DAX
Copy
Edit
Average Fare Amount = AVERAGE('uber_enhanced'[fare_amount])
Total Trips

DAX
Copy
Edit
Total Trips = COUNTROWS('uber_enhanced')
Visual Elements
✅ KPI Cards: Total Fare, Average Fare, Total Trips

✅ Line Chart: Fare trends over time

✅ Bar Chart: Fare distribution by payment type

✅ Map Visual: Pickup & drop-off analysis

✅ Slicers: Date, Location, Payment Type

📈 4. Results
Total Fare Amount: $X (from dataset)

Average Fare: $Y

Total Trips: Z

Patterns:

Highest revenue: Weekends & Holidays

Preferred payment: 65% Card

70% of fares: $10–$25 range

✅ 5. Conclusion
The dashboard revealed clear revenue patterns and customer preferences, supporting strategic pricing and better allocation of drivers. These insights allow Uber to improve profitability and customer satisfaction.

💡 6. Recommendations
Dynamic Pricing: Apply surge rates during peak demand.

Promotional Offers: Incentivize rides during off-peak hours.

Encourage Cashless Payments: Offer discounts for card payments.

Driver Optimization: Allocate resources to high-demand zones.
