 
# 🍕 The Great Pizza Analytics Challenge 📊

This repository contains the SQL queries and results from the "The Great Pizza Analytics Challenge," a project focused on foundational data inspection, filtering, exploration, and sales performance analysis for a pizza business.

## 💾 Dataset Foundation

[cite_start]The initial phase involved creating the database schema and populating the tables (`orders`, `order_details`, `pizzas`, `pizza_types`)[cite: 3].

## Phase 1: Foundation & Inspection 🔎

[cite_start]This phase ensures data quality and understanding the basic structure of the pizza data[cite: 2].

| Task | Description | SQL Query | Result Snippet |
| :--- | :--- | :--- | :--- |
| **1.** List all unique pizza categories | [cite_start]Uses `DISTINCT` to find unique categories[cite: 4]. | [cite_start]`select distinct category FROM idc_pizza.pizza_types;` [cite: 5] | [cite_start]`Chicken`, `Classic`, `Supreme`, `Veggie` [cite: 5] |
| **2.** Display key pizza info, replacing `NULL` ingredients | [cite_start]Uses `COALESCE` to replace null values with `"Missing Data"`[cite: 6]. | [cite_start]`SELECT pizza_type_id, name, coalesce(ingredients, 'Missing Data') as ingredients FROM idc_pizza.pizza_types limit 5;` [cite: 7] | [cite_start]Shows the first 5 rows with non-null ingredients [cite: 7] |
| **3.** Check for pizzas missing a price | [cite_start]Uses `IS NULL` to identify records with missing price data[cite: 9]. | [cite_start]`SELECT * FROM idc_pizza.pizzas where price is null;` [cite: 10] | [cite_start]An empty result grid suggests no prices are missing [cite: 10] |

## Phase 2: Filtering & Exploration 🗺️

[cite_start]This phase focuses on filtering data using `WHERE`, `ORDER BY`, `IN`, `BETWEEN`, and `LIKE`[cite: 11].

| Task | Description | SQL Query |
| :--- | :--- | :--- |
| **1.** Orders placed on '2015-01-01' | [cite_start]Filters records by a specific date[cite: 12]. | [cite_start]`select * FROM idc_pizza.orders where date = '2015-01-01';` [cite: 13, 14] |
| **2.** List pizzas with `price` descending | [cite_start]Sorts all pizzas from most to least expensive[cite: 15]. | [cite_start]`select * FROM idc_pizza.pizzas order by price desc;` [cite: 16, 17] |
| **3.** Pizzas sold in sizes 'L' or 'XL' | [cite_start]Uses the `IN` operator to filter by multiple size values[cite: 18]. | [cite_start]`SELECT * FROM idc_pizza.pizzas where size in ('L','XL');` [cite: 19, 20] |
| **4.** Pizzas priced between \$15.00 and \$17.00 | [cite_start]Uses the `BETWEEN` operator for a range of prices[cite: 21]. | [cite_start]`SELECT * FROM idc_pizza.pizzas where price between 15.00 and 17.00;` [cite: 22, 23] |
| **5.** Pizzas with "Chicken" in the name | [cite_start]Uses the `LIKE` operator with wildcards (`%`) for partial text matching[cite: 24]. | [cite_start]`SELECT * FROM idc_pizza.pizza_types where name like '%chicken%';` [cite: 25, 26] |
| **6.** Orders on '2015-02-15' **or** after 8 PM | [cite_start]Combines two filtering conditions using `OR`[cite: 27]. | [cite_start]`SELECT * FROM idc_pizza.orders where date ='2015-02-15' or time >='20:00:00';` [cite: 28, 29, 30] |

## Phase 3: Sales Performance 📈

[cite_start]This phase uses aggregate functions (`SUM`, `AVG`), joins (`JOIN`), grouping (`GROUP BY`), and filtering on aggregates (`HAVING`, `LEFT JOIN`, `SELF JOIN`) to analyze sales[cite: 31].

| Task | Description | SQL Query | Result Snippet |
| :--- | :--- | :--- | :--- |
| **1.** Total quantity of pizzas sold | [cite_start]Uses `SUM` to calculate the total quantity from `order_details`[cite: 32]. | [cite_start]`SELECT sum(quantity) as total_quantity_sold FROM order_details;` [cite: 33, 34, 35] | [cite_start]`49574` [cite: 35] |
| **2.** Average pizza price | [cite_start]Uses `AVG` and `ROUND` to find the average price across all pizzas[cite: 36]. | [cite_start]`SELECT round(avg(price),2) as Avg_price FROM idc_pizza.pizzas;` [cite: 37, 38] | [cite_start]`16.44` [cite: 38] |
| **3.** Total order value per order | [cite_start]Uses `JOIN`, `SUM`, and `GROUP BY` to calculate the total price for each unique order[cite: 39]. | [cite_start]SQL query involving joins between `orders`, `order_details`, and `pizzas` [cite: 40, 50] | [cite_start]First order value is `13.25` [cite: 50] |
| **4.** Total quantity sold per pizza category | [cite_start]Uses `JOIN` to link quantity to category and `GROUP BY` to aggregate[cite: 51]. | [cite_start]SQL query involving joins between `order_details`, `pizzas`, and `pizza_types` [cite: 52, 60] | [cite_start]`Classic` category sold `14888` [cite: 60] |
| **5.** Categories with more than 5,000 pizzas sold | [cite_start]Extends the previous query using `HAVING` to filter grouped results[cite: 61]. | [cite_start]SQL query with joins, `GROUP BY`, and `having sum(...) > 5000;` [cite: 62, 71] | [cite_start]Includes all four categories: `Classic`, `Veggie`, `Supreme`, `Chicken` [cite: 71] |
| **6.** Pizzas never ordered | [cite_start]Uses a `LEFT JOIN` and filters where `order_details` records are `NULL`[cite: 72]. | [cite_start]SQL query with `LEFT JOIN` on `order_details` and `WHERE od.order_id IS NULL;` [cite: 73, 82] | [cite_start]Shows pizzas like "The Big Meat Pizza" (M and L sizes) [cite: 82] |
| **7.** Price differences between different sizes of the same pizza | [cite_start]Uses a `SELF JOIN` on the `pizzas` table and `CASE` or `FIELD` for size comparison[cite: 83]. | [cite_start]SQL query with a `SELF JOIN` on `pizza_type_id` and size ordering logic [cite: 119, 134] | [cite_start]Shows a price difference of `4` for a size `S` to `M` upgrade for "The Barbecue Chicken Pizza" [cite: 134] |
