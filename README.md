
# SQL Data Cleaning Project

This is my first SQL data cleaning project.
The purpose of this project is to clean and validate raw data before analysis.

## Dataset
- Car information dataset
- Tool used: Google BigQuery
- Language: SQL

## What I did

### Step 1: Check missing values
I checked which columns contain missing (NULL) values.

```sql
SELECT
  COUNTIF(make IS NULL) AS make_nulls,
  COUNTIF(fuel_type IS NULL) AS fuel_type_nulls,
  COUNTIF(engine_size IS NULL) AS engine_size_nulls,
  COUNTIF(price IS NULL) AS price_nulls
FROM `sql-2025-468913.cars.car_info`;
```
### Step 2: Standardize text format

I converted text columns to uppercase to ensure consistency.
```sql
SELECT
  UPPER(make) AS make,
  UPPER(fuel_type) AS fuel_type,
  UPPER(body_style) AS body_style,
  engine_size,
  price
FROM `sql-2025-468913.cars.car_info`;
```
### Step 3: Validate text length

I used the LENGTH function to identify invalid text values.
```sql
SELECT
  drive_wheels,
  LENGTH(drive_wheels) AS drive_wheels_length
FROM `sql-2025-468913.cars.car_info`
WHERE LENGTH(drive_wheels) > 3;
```
### Step 4: Identify duplicate records

I checked for potential duplicate rows in the dataset.
```sql
SELECT
  make,
  fuel_type,
  engine_size,
  price,
  COUNT(*) AS record_count
FROM `sql-2025-468913.cars.car_info`
GROUP BY make, fuel_type, engine_size, price
HAVING COUNT(*) > 1;
```
## Result
The dataset was cleaned and validated and is ready for analysis.

## Skills Demonstrated
- SQL data cleaning
- Handling NULL values
- Text standardization
- Data validation
- Data preparation

### SQL queries used in this project: [`data_cleaning.sql`](data_cleaning.sql)

























