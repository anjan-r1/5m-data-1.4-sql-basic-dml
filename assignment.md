# Assignment

## Brief

Write the SQL DML statements for the following questions.

## Instructions

Paste the answer as SQL in the answer code section below each question.

### Question 1

Select the minimum and maximum price per sqm of all the flats.

```sql
select round(min(resale_price/floor_area_sqm)) as min_price_per_sqm, 
	   round(max(resale_price/floor_area_sqm)) as max_price_per_sqm
from main.resale_flat_prices_2017 r ;
```

### Question 2

Select the average price per sqm for flats in each town.

```sql
select town, round(avg(resale_price/floor_area_sqm)) as avg_price_per_sqm,
from main.resale_flat_prices_2017 r 
group by town
order by avg_price_per_sqm;
```

### Question 3

Categorize flats into price ranges and count how many flats fall into each category:

- Under $400,000: 'Budget'
- $400,000 to $700,000: 'Mid-Range'
- Above $700,000: 'Premium'
  Show the counts in descending order.

```sql
select case when resale_price < 400000 then 'Budget'
	        when resale_price < 700000 then 'Mid-Range'
	        else 'Premium' end as price_range, 
	   count(*) as count_of_units
from main.resale_flat_prices_2017 r 
group by price_range
ORDER BY count_of_units desc;
```

### Question 4

Count the number of flats sold in each town during the first quarter of 2017 (January to March).

```sql
SELECT  town, count(*) no_flats_sold, 
from main.resale_flat_prices_2017 r 
where month in ('2017-01','2017-02','2017-03')
group by town
order by no_flats_sold desc;

```

## Submission

- Submit the URL of the GitHub Repository that contains your work to NTU black board.
- Should you reference the work of your classmate(s) or online resources, give them credit by adding either the name of your classmate or URL.
