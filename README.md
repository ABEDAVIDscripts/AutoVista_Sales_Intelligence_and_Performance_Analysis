#### Project Title: AutoVista Sales Intelligence & Performance Analysis
#### Tool Used: SQL Server Management Studio, Microsoft Power BI & Excel
#### Project Lead: David Abe
#### Start Date: June 2025
#### End Date: August 2025

<br>
<br>
<br>

### Introduction:

The AutoVista Sales project was designed to convert raw automotive sales data from 2022 and 2023 into actionable business insights. The process began in SQL Server Management Studio (SSMS), where the dataset was meticulously cleaned to eliminate inconsistencies, duplicates, and missing values. Comprehensive Exploratory Data Analysis (EDA) was then conducted to identify key sales trends, product performance, and revenue patterns across both years. These findings were translated into a dynamic Power BI dashboard that visualizes sales heatmap, revenue contribution, and monthly trends. The final dashboard serves as a strategic tool for monitoring revenue performance, identifying year-over-year changes, and understanding market behavior — enabling data-driven decisions to optimize sales outcomes.

<br>
<br>
<br>



### Business Objectives

The analysis and visualization were guided by key business questions aimed at uncovering insights from the 2022 and 2023 sales data:

- Section A: Business Performance & Operational Metrics
  - What is the total revenue from car sales? 
  - Which car models generate the highest revenue? 
  - Which dealer regions contributed most to revenue?
  - What is the average revenue per customer? 
  - Which dealerships achieved the most sales? 
  - How do monthly car sales trend across the year? 
  - Which months had the highest and lowest sales volumes? 
  - Are there customers who made multiple purchases? 
  - Are there customers who significantly reduced their purchase activity? 

<br>

- Section B: Customer Segmentation Questions
  - Can customers be segmented by purchase value (e.g., high-, mid-, and low-tier spenders)? 
  - What’s the gender-wise distribution of car buyers? 
  - What is the income range of customers buying specific models or brands? 
  - What is the average revenue per income bracket? 
  - Can we identify potential premium customers based on purchase patterns or amounts? 

<br>

- Section C: Visualization-Focused Questions
  - Sales performance by car brand or model (bar chart)? 
  - Revenue contribution by car body style (pie/donut chart)? 
  - Monthly revenue trends (line chart)? 
  - Heatmap of car model sales across months?

<br>
<br>
<br>

### Data Preparation & Exploratory Data Analysis (EDA)

The Data Preparation and EDA phase formed the foundation of this project, ensuring the dataset was accurate, consistent, and ready for meaningful analysis.


This stage was conducted entirely in SQL Server Management Studio (SSMS), with two core objectives:

1. Prepare and refine the dataset — Eliminating duplicates, correcting inconsistencies, standardizing formats, and addressing missing values to ensure data integrity.

2. Uncover initial insights — Exploring the data to reveal sales trends, product performance patterns, and revenue distribution across both 2022 and 2023.

The EDA process was guided by the Business Performance & Operational Metrics and Customer Segmentation Questions outlined in the objectives section, ensuring each transformation and query directly supported the project’s analytical goals.

- [View complete Data Preparation & Cleaning process here](Data%20Preparation%20%26%20Cleaning.md)
- [View complete EDA process here](Exploratory%20Data%20Analysis.md)

<br>
<br>
<br>


### Onboarding Page (showcasing Top Premium Model)

The Onboarding Page serves as a visually compelling entry point into the ***AutoVista Sales Trend and Performance Dashboard***. It introduces the most premium and high-value vehicle model based on sales data from 2022 and 2023.

<br>

<img width="900" height="500" alt="Onboarding" src="https://github.com/user-attachments/assets/95d5282b-075f-4dd1-bd3e-89aa3b7b73d5" />

<br>
<br>

- Top Premium
  - Model Name: Cadillac Eldorado
  - Selling Price: $85,800
  - Units Sold: 232 cars
  - Model Revenue: $9.7M
  - Overall Sales Revenue: $671.5M.

<br>

- Feature Highlights (vehicle’s premium features)
  - Double Overhead Shaft Engine
  - Convertible Body Style
  - Manual Transmission
  - Passenger Body Style
 
<br>

- Model Specifications Panel
  - Mileage: 12 MPG
  - Horsepower: 335 HP
  - Top Speed: 130 MPH
  - Fuel Type: Petrol


<br>
<br>
<br>


### Slicers & Interactivity

The dashboard is designed to be fully interactive using slicers such as:

- Year
- Car Body
- Car Model
- Company
- Dealer Name
- Dealer Region


<img width="800" height="180" alt="Sales Trend with Year Slicer" src="https://github.com/user-attachments/assets/ef6a9871-3fb4-4947-8337-c9bc46d4974f" />


> These filters enable dynamic data exploration based on business needs and stakeholder interests.

<br>
<br>
<br>

###  KPI & Metrics

This section highlights the core KPIs and performance metrics used to evaluate key aspects of AutoVista’s sales operations across the 2022 and 2023 fiscal years.

#### 1. KPIs

- Total Revenue:

$300.3M (2022) vs $371.2M (2023) = $671.5M (Total Revenue)

<p align="center">
  <img width="191" height="69" alt="Total Revenue 2022" src="https://github.com/user-attachments/assets/101f6e48-6740-480d-b885-579c36543acf" />
  <strong style="font-size: 16px; margin: 0 10px;"> vs </strong>
  <img width="190" height="68" alt="Total Revenue 2023" src="https://github.com/user-attachments/assets/697b0464-b4e8-4f8b-ad8f-37107dc6df29" />
  <strong style="font-size: 20px; margin: 0 10px;"> = </strong>
  <img width="191" height="68" alt="Total Revenue" src="https://github.com/user-attachments/assets/ab511235-3a91-4334-8a98-0c47d42cd8f3" />
</p>

> ##### This highlights a significant YoY growth, with 2023 outperforming 2022 by 23.6% ($70.9M).

<br>
<br>
<br>

- Average Revenue:

$28.2k (2022) vs $28.0k (2023) = $28.1k (Overall Average Revenue)

<p align="center">
  <img width="191" height="68" alt="Avg Revenue 2022" src="https://github.com/user-attachments/assets/391dd921-527b-4546-b1a4-ace3b2b95df0" />
  <span style="font-size: 16px; margin: 0 10px;"> vs </span>
  <img width="189" height="68" alt="Avg Revenue 2023" src="https://github.com/user-attachments/assets/76cc75e7-2244-4f3a-83e3-a6b7bcedb0fd" />
  <strong style="font-size: 20px; margin: 0 10px;"> = </strong>
  <img width="191" height="68" alt="Avg Revenue" src="https://github.com/user-attachments/assets/5cac369b-2886-4b31-94a6-b6958536c643" />
</p>

> ##### This indicates a slight YoY decline, with average revenue in 2023 dropping by 0.8%.

<br>
<br>
<br>

- Annual Income:

$9.1bn (2022) vs $10.7bn (2023) = $19.9bn (Total Annual Income)

<p align="center">
  <img width="189" height="68" alt="Annual Income 2022" src="https://github.com/user-attachments/assets/0ee2c987-fced-40f2-9014-ac59ad791256" />
  <span style="font-size: 16px; margin: 0 10px;"> vs </span>
  <img width="190" height="68" alt="Annual Income 2023" src="https://github.com/user-attachments/assets/7cdf97ec-0be7-4c65-ae75-2ff7cbeb52db" />
  <strong style="font-size: 20px; margin: 0 10px;"> = </strong>
  <img width="191" height="69" alt="Annual Income" src="https://github.com/user-attachments/assets/5724be23-6da4-4d4c-ba44-1ff0b3cae661" />
</p>

> ##### This reflect a strong year-over-year increase, with 2023 annual income rising by 18.0%.


<br>
<br>
<br>

- Average Annual Income:

$856.1k (2022) vs $810.6k (2023) = $830.8k (Overall Average Annual Income)

<p align="center">
  <img width="191" height="68" alt="Avg Annual Income 2022" src="https://github.com/user-attachments/assets/86bc749b-e096-4881-8155-02328bb801bd" />
  <span style="font-size: 16px; margin: 0 10px;"> vs </span>
  <img width="191" height="68" alt="Avg Annual Income 2023" src="https://github.com/user-attachments/assets/b69b1469-3970-4bb4-adb0-723a432b99fd" />
  <strong style="font-size: 20px; margin: 0 10px;"> = </strong>
  <img width="190" height="68" alt="AVG Annual Income" src="https://github.com/user-attachments/assets/2c024cce-4843-4ab2-a54a-ec6951934d47" />
</p>

> ##### This reflect a slight year-over-year decline, with 2023 average income down by 5.3%.

<br>
<br>
<br>

- Number of Sales

10.6k (2022) vs 13.3k (2023) = 23.9k (Total Number of Sales)

<p align="center">
  <img width="191" height="68" alt="Number of Sales 2022" src="https://github.com/user-attachments/assets/1252e64a-d401-4c59-923d-a409c0150421" />
  <span style="font-size: 16px; margin: 0 10px;"> vs </span>
  <img width="191" height="68" alt="Number of Sales 2023" src="https://github.com/user-attachments/assets/110af01e-1786-41b3-b0c0-7263887f818a" />
  <strong style="font-size: 20px; margin: 0 10px;"> = </strong>
  <img width="190" height="67" alt="Number of Sales" src="https://github.com/user-attachments/assets/ec7acf86-9888-4c18-808e-06ab934171ba" />
</p>

> ##### This reflect a strong year-over-year growth, with 2023 sales increasing by 24.6%.

<br>
<br>
<br>

#### 2. Consolidated Metrics

- Sales Performance by Company:

This metric compares total sales across manufacturers, highlighting the top-performing company for the overall year.

<img width="406" height="182" alt="sales performance by company" src="https://github.com/user-attachments/assets/0296e165-63d5-4d54-b15d-59f2ca25623f" />

> ##### Chevrolet outperformed Ford to lead overall sales.

<br>
<br>
<br>

- Monthly Sales Heatmap by Car Model:

This metric tracks revenue over time for specific models, also reveals which car models peak in certain months.

<img width="621" height="183" alt="Monthly sales heatmap" src="https://github.com/user-attachments/assets/b0a28325-a843-4075-80cd-d1d87f856f22" />

> ##### The LS400 recorded the highest monthly sales revenue ($2.68M), peaking in September.

<br>
<br>
<br>

- Monthly Revenue Trend:

Reveals seasonal sales patterns and peak revenue months, performance is benchmarked using an Average Revenue Target line and a Peak Month Marker. Visual indicators confirm whether performance is *On Track* or *Below Target* relative to revenue goals.

<img width="621" height="200" alt="monthly revenue trend" src="https://github.com/user-attachments/assets/b2c61eb7-2edd-4b97-817a-2ee0aad6adfb" />

> ##### December delivered peak revenue due to year-end sales drives.

<br>
<br>
<br>

- Revenue Contribution by Car Body:

This metric shows the percentage share of total revenue generated by each car body type, helping identify the most profitable vehicle categories.

<img width="407" height="198" alt="Revenue contribution" src="https://github.com/user-attachments/assets/497a80be-2609-4d87-83d4-0450d55f39a3" />

> ##### SUVs dominated the top spot


<br>
<br>
<br>

- The Dashboad

<p align="center"> <img width="1069" height="548" alt="AutoVista  Sales Dashboard" src="https://github.com/user-attachments/assets/1186671e-c445-44ff-9c7f-b744111a4bc1" /> </p>



<br>
<br>
<br>

### Insight Snapshot:

Provides a concise, high-level overview of the most important findings from the analysis, spotlighting key performance trends, standout metrics, and notable shifts in sales or market behavior across 2022 and 2023. It serves as a quick reference for decision-makers to grasp critical outcomes without reviewing the full dataset.

<p align="center"> <img width="850" height="400" alt="Insight snapshot" src="https://github.com/user-attachments/assets/ff7fa7f5-25bb-4b79-a9e0-63f673b2e89f" /> </p>

<br>
<br>
<br>
<br>
<br>



<p align="center"> 
<img width="500" height="50" alt="project end image" src="https://github.com/user-attachments/assets/98271561-5f31-46fe-ad47-3ef60b498099" />
</p>

<p align="center"> Thank you for exploring the AutoVista Sales analysis. </p>

<p align="center"> David Abe </p>


<br>
<br>
