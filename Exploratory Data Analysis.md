
## DATA EXPLORATORY ANALYSIS (BUSINESS QUESTIONS)

<br>
<br>

### Section A: Business Performance & Operational Metrics

<br>
<br>

#### 1. What is the total revenue from car sales? 

```SQL
SELECT SUM(Price) AS Total_Revenue
FROM car_worksheet;
```

<BR>
<BR>


#### 2. Which car models generate the highest revenue? 

```SQL
SELECT model, SUM(price) AS Total_Revenue
FROM car_worksheet
GROUP BY model
ORDER BY 2 DESC;
```

<BR>
<BR>

#### 3. Which dealer regions contributed most to revenue? 

```SQL
SELECT dealer_region, SUM(price) AS Total_Revenue
FROM car_worksheet
GROUP BY Dealer_Region
ORDER BY 2 DESC;
```

<BR>
<BR>

#### 4. What is the average revenue per customer? 

```SQL
WITH customer_table AS 
	(SELECT customer_name, SUM(price) AS Total_Revenue
    FROM car_worksheet
    GROUP BY Customer_Name)
SELECT 
    AVG(total_revenue) AS Avg_Revenue_Per_Customer
FROM customer_table;
```

<BR>
<BR>

#### 5. Which dealerships achieved the most sales? 
```SQL
SELECT Dealer_Name, COUNT(*) AS Total_Sales, SUM(Price) AS Total_Revenue
FROM car_worksheet
GROUP BY Dealer_Name
ORDER BY 3 DESC;
```

<BR>
<BR>

#### 6. How do monthly car sales trend across the year? 

```SQL
SELECT 
	YEAR(Date) AS Sales_Year,
	DATENAME(MONTH, Date) AS Sales_Month,
	MONTH(Date) AS Month_No,
	COUNT(*) AS Car_Sales,
	SUM(Price) AS TOtal_Revenue
FROM car_worksheet
GROUP BY YEAR(Date), MONTH(Date), DATENAME(MONTH, Date)
ORDER BY Sales_Year, Month_No;
```

<BR>
<BR>

#### 7. Which months had the highest and lowest sales volumes? 

```SQL
WITH Highest_table AS
(SELECT 
	TOP 1 'Highest' AS Category,
	YEAR(Date) AS Sales_Year,
	DATENAME(MONTH, Date) AS Sales_Month,
	MONTH(Date) AS Month_NO,
	COUNT(*) AS Sales_Volume
FROM car_worksheet
GROUP BY YEAR(Date), MONTH(Date), DATENAME(MONTH, Date)
ORDER BY Sales_Volume DESC),

Lowest_table AS
(SELECT 
	TOP 1 'Lowest' AS Category,
	YEAR(Date) AS Sales_Year,
	DATENAME(MONTH, Date) AS Sales_Month,
	MONTH(Date) AS Month_NO,
	COUNT(*) AS Sales_Volume
FROM car_worksheet
GROUP BY YEAR(Date), MONTH(Date), DATENAME(MONTH, Date)
ORDER BY Sales_Volume ASC)

SELECT * FROM Highest_table
UNION ALL
SELECT * FROM Lowest_table;
```

<BR>
<BR>

#### 8. Are there customers who made multiple purchases?

```SQL
SELECT 
	Customer_name, 
	COUNT(*) AS Multiple_purchase
FROM car_worksheet
GROUP BY Customer_Name
HAVING COUNT(*) > 1
ORDER BY Multiple_purchase DESC;
```

<BR>
<BR>

#### 9. Are there customers who significantly reduced their purchase activity? 

```SQL
WITH Purchase_Table AS
(SELECT 
	Customer_name,
	COUNT(*) AS Purchase,
	YEAR(Date) AS Sales_Year,
	LAG(COUNT(*)) OVER (PARTITION BY customer_name ORDER BY YEAR(Date)) AS Previous_purchase
FROM car_worksheet
GROUP BY Customer_Name, YEAR(Date)),

Dropped_Table AS 
(SELECT 
	customer_Name,
	Sales_Year,
	Purchase,
	Previous_Purchase,
	(ISNULL(Previous_purchase, 0) - Purchase) AS Dropped_No
FROM Purchase_Table)

SELECT
	Customer_Name,
	Sales_Year,
	Purchase,
	Previous_Purchase,
	Dropped_No
FROM Dropped_Table
WHERE Dropped_No >= 1;
```

<BR>
<BR>
<BR>

### SECTION B. Customer Segmentation Questions

<BR>

#### 1. Can customers be segmented by purchase value (e.g., high-, mid-, and low-tier spenders)? 

> Using Above 1,000,000 as High Spender; 500,000 - 999,999 as Mid Spender; Others Low Spender


```SQL
WITH customer_table AS
(SELECT customer_name, SUM(price) AS Price
FROM car_worksheet
GROUP BY customer_name)

SELECT 
	customer_name, Price,
	CASE
		WHEN Price >= 1000000 THEN 'High Spender'
		WHEN Price BETWEEN 500000 AND 999999 THEN 'Mid Spender'
		ELSE 'Low Spender'
	END AS Price_Segment
FROM customer_table
ORDER BY Price DESC;
```

<BR>
<BR>


#### 2. What’s the gender-wise distribution of car buyers? 

```SQL
WITH Gender_table AS
(SELECT 
	Gender, COUNT(*) AS Distribution_count
FROM car_worksheet
GROUP BY Gender)

SELECT -- To cal. in percentage
	Gender, Distribution_count,
	Concat((Distribution_count * 100)/ (SELECT COUNT(*) FROM car_worksheet), '%') AS Percentage_Distribution
FROM Gender_table
GROUP BY Gender, Distribution_count;
```

<BR>
<BR>

#### 3. What is the income range of customers buying specific models or brands? 

```SQL
SELECT 
	DISTINCT Model,
	MIN(annual_income) AS Low_Income,
	AVG(annual_income) AS Average_Income,
	MAX(annual_income) AS High_Income
FROM car_worksheet
GROUP BY Model
ORDER BY High_Income ;
```

<BR>
<BR>

#### 4. What is the average revenue per income bracket? 

```SQL
WITH income_table AS
(SELECT 
	Customer_Name,
	Price,
	Annual_income,
	CASE
		WHEN Annual_income < 60000 THEN 'Low_Annual_Income'
		WHEN Annual_income BETWEEN 60000 AND 1000000 THEN 'AVG_Annual_Income'
		WHEN Annual_income > 1000000 THEN 'High_Annual_Income'
		ELSE 'Unkownn'
END AS Income_Bracket
FROM car_worksheet)

SELECT 
	Income_bracket,
	COUNT(*) AS Customer_No,
	SUM(Price) AS Total_Price,
	AVG(Price) AS AVG_Price
FROM income_table
GROUP BY Income_Bracket
ORDER BY AVG_Price;
```

<BR>
<BR>



#### 5. Can we identify potential premium customers based on purchase patterns or amounts? 

```SQL
WITH Price_table AS
(SELECT 
	Customer_Name,
	COUNT(*) AS No_of_Transactions,
	MIN(Price) AS Low_Purchase,
	AVG(Price) AS AVG_Purchase,
	MAX(Price) AS High_Purchase
FROM car_worksheet
GROUP BY Customer_Name)

SELECT 
	Customer_Name,
	High_Purchase,
	CASE
		WHEN High_Purchase > 80000 THEN 'Elite Premium'
		ELSE 'Premium'
	END AS Premium_Type
FROM Price_table
WHERE High_Purchase > 60000
ORDER BY High_Purchase DESC;
```

<BR>
<BR>

##### THE END

> Verification

```SQL
select * from car_worksheet;
```



