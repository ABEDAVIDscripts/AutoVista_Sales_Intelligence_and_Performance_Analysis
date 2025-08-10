## Data Preparation & Cleaning

<br>

#### Use Sales database

```SQL
USE [sales db];
```


> verify csv importation

```SQL
  SELECT * FROM car_sales_report;
``` 

<br>
<br>
<br>


### Data Cleaning Procedure:


#### 1. Create *car_worksheet* table and copy the data into it, to preserve the raw file

```SQL
SELECT * 
INTO car_worksheet
FROM car_sales_report;
```


> Verify

```SQL
SELECT * FROM car_worksheet;
```
 
<BR>
<br>
<BR>

#### 2. Check and Remove Duplicates

```SQL
SELECT date, customer_name, gender, annual_income, dealer_name, company, model, count(*) AS duplicate_count
FROM car_worksheet
GROUP BY date, Customer_Name, Gender, annual_income, dealer_name, company, model
Having Count(*) > 1;
```

> No duplicates found

<br>

#### 2b. Check and set car_id as Primary Key

> check for NULL before adding

```SQL
SELECT count(*) 
FROM car_worksheet
WHERE car_id is NULL;
```


> Add Primary key

```SQL
ALTER TABLE car_worksheet
ADD PRIMARY KEY (car_id); 
```

<BR>
<BR>
<br>

#### 3. Check for Missing Values

```SQL
SELECT * FROM car_worksheet
WHERE
    date is NULL OR
    Customer_Name is NULL OR
    Gender is NULL OR
    Annual_Income is NULL OR
    Dealer_Name is NULL OR
    Company is NULL OR
    model is NULL OR
    Engine is NULL OR
    Transmission is NULL OR
    color is NULL OR
    price is NULL OR
    Dealer_No is NULL OR
    body_style is NULL OR
    phone is NULL OR
    Dealer_Region is NULL;
```

<br>
<BR>
<br>

#### 4. Standardize Categorical Text

```SQL
select * from car_worksheet;
```

<br>

#### 4A. check with Customer_Name column

```SQL
SELECT DISTINCT Customer_Name
FROM car_worksheet
ORDER BY 1 ASC;
```



> Update incorrect entries from "Amar'E" to "Amar'e"

```SQL
UPDATE car_worksheet 
SET Customer_Name = 'Amar''e' 
WHERE Customer_Name = 'Amar''E';
```



> verify

```SQL
SELECT customer_name
FROM car_worksheet
WHERE Customer_Name = 'Amar''e' 
OR Customer_Name = 'Amar''E';
```

<br>

#### 4B. check with Company column

```SQL
SELECT DISTINCT Company
FROM car_worksheet
ORDER BY 1 ASC;
```



> Update incorrect entries from 'Mercedes-B' to 'Merecedes-Benz'

```SQL
UPDATE car_worksheet
SET Company = 'Mercedes-Benz'
WHERE Company = 'Mercedes-B';
```



> verfiy

```SQL
SELECT DISTINCT company
FROM car_worksheet
WHERE company = 'Mercedes-Benz' 
OR company = 'Mercedes-B';
```

<br>

#### 4C. check with Model column

```SQL
SELECT DISTINCT Model
FROM car_worksheet
ORDER BY 1 ASC;
```



> Issue Identified: The Model column contains invalid entries i.e. '3-Sep' and '5-Sep', which resemble dates rather than actual car model names.

> Fixed Applied: Update incorrect entries to 'Unknown' values

```SQL
UPDATE car_worksheet
SET Model = 'Unknown'
WHERE Model IN ('3-Sep', '5-Sep');
```



> verify
```SQL
SELECT Model FROM car_worksheet
WHERE model = '3-Sep' OR model = '5-Sep';
```

<br>

#### 4D. check with Engine column
```SQL
SELECT DISTINCT engine
FROM car_worksheet;
```



> Issue identified: Text encoding error in 'Engine' column (e.g., 'DoubleÃ‚Â Overhead Camshaft')

> Fix applied: Updated incorrect entries to 'Double Overhead Camshaft'

```SQL
UPDATE car_worksheet
SET Engine = 'Double Overhead Camshaft'
WHERE Engine = 'DoubleÂ Overhead Camshaft';
```



> verify


```SQL
SELECT DISTINCT engine
FROM car_worksheet;
```

<br>
<BR>
<br>

#### 5. Fix Data Types

> Describe Table car_worksheet

```SQL
EXEC sp_help 'car_worksheet';
```



> Change the Date column Datatype from 'Datetime2' to 'Date' to remove unnecessary timestamp details


```SQL
ALTER TABLE car_worksheet
ALTER COLUMN date DATE;
```



> Verify


```SQL
SELECT date FROM car_worksheet;
```

<br>
<BR>
<br>

#### 6. Validating and Correcting Outliers

> check with the numerical columns(Annual_Income, Price & Phone)

<br>

#### 6A. check with Price column

```SQL
SELECT DISTINCT price
FROM car_worksheet
ORDER BY price DESC;
```



> possible outliers found (4300, 4200, 2200, 1700, 1450, 1200), extremely low compared to the rest in the Price column

> verify the outliers data


```SQL
SELECT *
FROM car_worksheet
WHERE Price < 9000
ORDER BY price DESC;
```



> since there is no indication that the data can be of mixed new and used cars, hence will treat outliers with care

> create a new column to Flag the possible outliers, Flag price that are below 9000


```SQL
ALTER TABLE car_worksheet
ADD Price_Flag VARCHAR(20);
```



> Suspicious if below 9000, Ok if above


```SQL
UPDATE car_worksheet
SET Price_Flag = CASE
	WHEN Price < 9000 THEN 'Suspicious'
	ELSE 'Ok'
	END;
```



> verify


```SQL
SELECT * FROM car_worksheet
WHERE price_flag = 'Suspicious'
ORDER BY Price DESC;
```

<br>

#### 6B. check with Annual_Income


```SQL
SELECT DISTINCT annual_income
FROM car_worksheet
ORDER BY 1 DESC;
```



> possible outliers (24000, 13500, 10080), extremely low compared to the rest 

> verify the outlier data


```SQL
SELECT * FROM car_worksheet
WHERE Annual_Income < 25000
ORDER BY annual_income DESC;
```



> This may seem like an outlier, 
> but certain age groups such as Teenagers (16–19) and Elderly (65+) can fall within this Annual Income range, so the data may still be valid.

<br>
<br>
<br>

#### DATA CLEANING COMPLETE


> verify

```SQL
SELECT * FROM car_worksheet;
```

