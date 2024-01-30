# SQL_CTE-Common-Table-Expression-
This covers all about CTE and Best Resources to Refer to Learn and Practise CTE .



SELECT
  initcap(t1.country_name) AS country_name,
  to_char(sum(t2.population), '99G999G999') total_population,
  CASE
  	WHEN (sum(t2.population) % 2) = 0
  		THEN 'Even'
  	ELSE 
  		'Odd'
  END AS odd_or_even
FROM
  cleaned_data.countries AS t1
JOIN 
  cleaned_data.cities AS t2
ON 
  t1.country_code_2 = t2.country_code_2
WHERE
  t1.country_name ILIKE '%stan'
AND 
  EXTRACT('year' FROM t2.insert_date) = 2022
GROUP BY
  t1.country_name
ORDER BY 
  odd_or_even, country_name;

