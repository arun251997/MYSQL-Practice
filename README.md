# MYSQL-Practice

#1. Find the names of the customer that are not referred by the customer with id = 2.

select name from customer
where referee_id!=2 or referee_id is null

#2. Write a solution to find the ids of products that are both low fat and recyclable.

select product_id From Products
where low_fats='Y' and recyclable='Y'

#3. A country is big if:

it has an area of at least three million (i.e., 3000000 km2), or
it has a population of at least twenty-five million (i.e., 25000000).
Write a solution to find the name, population, and area of the big countries.

SELECT name, population, area
FROM world
WHERE area >= 3000000 OR population >= 25000000;

#4.Write a solution to find all the authors that viewed at least one of their own articles.
Return the result table sorted by id in ascending order.

select distinct author_id as id
from Views
where author_id = viewer_id
order by id;

#5. Write a solution to find the IDs of the invalid tweets. The tweet is invalid if the number of characters used in the content of the tweet is strictly greater than 15.

select tweet_id
from Tweets
where length(content)>15;

#6. Write a solution to report the product_name, year, and price for each sale_id in the Sales table.

select p.product_name, s.year, s.price
from product p
join sales s
on p.product_id = s.product_id

#7.# Write a solution to find the IDs of the users who visited without making any transactions and the number of times they made these types of visits.

SELECT customer_id, COUNT(*) AS count_no_trans
FROM Visits
WHERE visit_id NOT IN (SELECT visit_id FROM Transactions)
GROUP BY customer_id;
