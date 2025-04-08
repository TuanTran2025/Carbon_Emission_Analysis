# Carbon_Emission_Analysis

## 1. Introduction 


### 1.1 Data model


### 1.2 Data structure
Table'product_emissions'
```sql
SELECT * FROM product_emissions pe LIMIT 10
```


## 2. Data Exploration
Data duplication
```sql
SELECT *,
	count(*) as duplicated_count
FROM product_emissions pe
GROUP BY
	id,
	company_id,
	country_id,
	industry_group_id,
	year,
	product_name,
	weight_kg,
	carbon_footprint_pcf,
	upstream_percent_total_pcf,
	operations_percent_total_pcf,
	downstream_percent_total_pcf 
having count(*) > 1
limit 10;
```

Duplicate result
```sql
SELECT COUNT(product_name) as 'Total number of products',
	COUNT(DISTINCT product_name) as 'Number of unique products'
FROM product_emissions;
```
|Total number of products|Number of unique products|
|------------------------|-------------------------|
|1037|661|


## 3. Data Analysis
### 3.1. Which products contribute the most to carbon emissions?
