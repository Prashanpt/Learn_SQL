# SQL_CT-Common-Table-Expression-
This covers all about CTE and Best Resources to Refer to Learn and Practise CTE .


  ```sql
SELECT 
	-- initcap() capitalizes the first letter of every word in a string.
	initcap(region) AS region,
	count(*) AS country_count
FROM
	cleaned_data.countries
GROUP BY
	-- Aggregate functions 'count()' require you to group all column fields.
	region
ORDER BY 
	country_count DESC;
  ```
