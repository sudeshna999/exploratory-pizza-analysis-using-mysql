
#  Pizza Sales Data Analytics Project

## Project Overview

This project dives deep into a pizza sales dataset to uncover insights about customer preferences, order patterns, revenue trends, and inventory needs. Using advanced SQL queries, the analysis covers peak sales hours, top-performing pizzas, order frequency by size and category, and demand forecasting.
By understanding key drivers behind sales and customer behavior, this project empowers pizzerias to optimize menu offerings, streamline inventory, and enhance marketing strategies.

---
## Business Problem
Pizza restaurants often face challenges such as:

- Over- or under-stocking ingredients.
- Not knowing the most profitable or popular pizzas.
- Failing to predict peak sales hours or days.
- Ineffective targeting of customers based on ordering patterns.
- Limited understanding of seasonal demand and trends.
Solving these issues can lead to higher profits, better customer satisfaction, and more efficient operations.
---
## Solution & Approach
This project uses **SQL-based data analysis to answer crucial business questions**, including:

- What are the best-selling and most profitable pizzas?
- Which size or category of pizza is most ordered?
- What are the busiest sales days and hours?
- How do weekly and monthly trends impact inventory planning?
- How can we segment customers by their preferences?

## 📁 Project Structure

#### 🧠 Sample Query Snippet

```sql

-- How many pizzas were ordered?

select count(*) as pizza_orderd
from runner_orders 
where cancellation is null;

-- How many Vegetarian and Meatlovers were ordered by each customer?

select c.customer_id, concat(count(*), '  ', p.pizza_name) as no_of_pizza_ordered
from customer_orders as c join pizza_names as p using(pizza_id)
group by c.customer_id, p.pizza_name
order by c.customer_id ;

-- What was the total volume of pizzas ordered for each hour of the day?

select hour(order_time) as hour, count(*) as total
from customer_orders
group by 1
order by 1;


-- Is there any relationship between the number of pizzas and how long the order takes to prepare?

from customer_orders as c join runner_orders as r using(order_id)
where r.pickup_time is not null
group by 1,2,3)
select customer_id, count(order_id) as num_of_pizza_order, prepare_time from cte
group by 1,3;           -- no realtion for this dataset


-- What was the difference between the longest and shortest delivery times for all orders?

select concat(min(duration_mins), ' minute') as shortest,
		concat(max(duration_mins), ' minute') as longest
        from runner_orders;

-- What is the successful delivery percentage for each runner?

with cte2 as (
	with cte as (
    select *, 
	if(cancellation is null , 'Successful Delivery',null) as delivery_status
	from runner_orders)
			select runner_id, count(delivery_status) as successful_delivery, 
			count(*) as total_delivery from cte
			group by 1)
            
            select runner_id, round((successful_delivery / total_delivery)*100,2) as percent
            from cte2
;


```
---

## Some snip of Outputs

-- How many pizzas were ordered?

![image](https://github.com/user-attachments/assets/2be133d4-84c6-42bf-8ac7-3843e2aa6f38)

-- How many Vegetarian and Meatlovers were ordered by each customer?

![image](https://github.com/user-attachments/assets/5d57d112-0673-46bb-90de-2ca59ea1cde8)

 -- What was the total volume of pizzas ordered for each hour of the day?

![image](https://github.com/user-attachments/assets/ef1a1b3d-b808-42f4-8387-9524a36bd2c9)

-- Is there any relationship between the number of pizzas and how long the order takes to prepare?

![image](https://github.com/user-attachments/assets/e284d3e4-b495-49de-9ecb-98c112e04156)

 -- What was the difference between the longest and shortest delivery times for all orders?

![image](https://github.com/user-attachments/assets/ac360b69-8439-44ff-b1df-eb620e75b8da)

-- What is the successful delivery percentage for each runner?

![image](https://github.com/user-attachments/assets/a0f38fdf-26dd-4afa-89d0-9faa92703c57)



---
## Key techniques include:

- Window functions to rank top-selling pizzas.
- Date functions to identify time-based sales trends.
- CTEs and subqueries for clean, modular logic.
- Aggregation to evaluate sales performance over time.
Insights are translated into action items to maximize sales, minimize waste, and improve menu design.
---
## Repository Structure
- .sql — Contains SQL scripts for each analysis use case.
- README.md — Project documentation.
- create_insert_table — Sample pizza sales dataset.

---
## Technologies Used
- MySQL for querying
- SQL concepts: CTEs, window functions, groupings, and aggregations
- GitHub for version control and collaboration
---

## Author
### — Sudeshna Dey
###  — Contact & Contributions

#### 📧 Email: sudeshnadey1000@gmail.com
#### 🔗 LinkedIn: https://www.linkedin.com/in/sudeshna-dey-724a811a0/
 Have feedback or suggestions? I'm always open to improving and collaborating!
 
If you find this project helpful:
⭐ Give it a star
Thanks for visiting — and happy data analyzing!

