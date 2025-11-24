 
 

---

# 🍕 The Great Pizza Analytics Challenge 📊

SQL Explorations in Data Inspection, Filtering & Sales Performance Analysis

This project showcases SQL queries and insights generated for a pizza business dataset. It covers **data inspection, filtering, exploration**, and **sales performance analytics** using SQL fundamentals such as `SELECT`, `WHERE`, `JOIN`, `GROUP BY`, and aggregate functions.

---

## 💾 Dataset Overview

The dataset includes four core tables:

* **orders**
* **order_details**
* **pizzas**
* **pizza_types**

These tables form the foundation for exploring order behavior, pizza pricing, categories, and sales performance.

---

## 🔎 Phase 1: Foundation & Inspection

Focus: Understanding the structure and quality of the data.

| Task                                                 | Description                                                     | Sample Query                                                                                                 | Output Snippet                                      |
| ---------------------------------------------------- | --------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------ | --------------------------------------------------- |
| **1. List all unique pizza categories**              | Uses `DISTINCT` to display unique categories.                   | `SELECT DISTINCT category FROM pizza_types;`                                                                 | Classic, Chicken, Supreme, Veggie                   |
| **2. Display pizza info & replace NULL ingredients** | Uses `COALESCE` to replace `NULL` values with `"Missing Data"`. | `SELECT pizza_type_id, name, COALESCE(ingredients, 'Missing Data') AS ingredients FROM pizza_types LIMIT 5;` | Shows first 5 pizzas with cleaned ingredient fields |
| **3. Check pizzas missing a price**                  | Identifies rows where the price is missing.                     | `SELECT * FROM pizzas WHERE price IS NULL;`                                                                  | No missing prices found                             |

---

## 🗺️ Phase 2: Filtering & Exploration

Focus: Applying SQL filters using `WHERE`, `ORDER BY`, `IN`, `BETWEEN`, and `LIKE`.

| Task                                       | Description                       | Query                                                                   |
| ------------------------------------------ | --------------------------------- | ----------------------------------------------------------------------- |
| **1. Orders on 2015-01-01**                | Filter by specific date.          | `SELECT * FROM orders WHERE date = '2015-01-01';`                       |
| **2. Pizzas sorted by price (high → low)** | Sort using `ORDER BY`.            | `SELECT * FROM pizzas ORDER BY price DESC;`                             |
| **3. Pizzas sold in sizes L or XL**        | Filters using `IN`.               | `SELECT * FROM pizzas WHERE size IN ('L', 'XL');`                       |
| **4. Pizzas priced between $15–$17**       | Uses `BETWEEN`.                   | `SELECT * FROM pizzas WHERE price BETWEEN 15.00 AND 17.00;`             |
| **5. Pizzas with “Chicken” in the name**   | Uses `LIKE` for pattern matching. | `SELECT * FROM pizza_types WHERE name LIKE '%chicken%';`                |
| **6. Orders on 2015-02-15 OR after 8PM**   | Uses the `OR` operator.           | `SELECT * FROM orders WHERE date = '2015-02-15' OR time >= '20:00:00';` |

---

## 📈 Phase 3: Sales Performance Analysis

Focus: Using `JOIN`, `SUM`, `AVG`, `GROUP BY`, `HAVING`, and advanced SQL logic for business insights.

| Task                                               | Description                                    | Sample Query                                                                                                                                                                                       | Key Result                                               |
| -------------------------------------------------- | ---------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------- |
| **1. Total quantity of pizzas sold**               | Uses `SUM` on `order_details.quantity`.        | `SELECT SUM(quantity) AS total_quantity_sold FROM order_details;`                                                                                                                                  | **49,574** total pizzas sold                             |
| **2. Average pizza price**                         | Uses `AVG` with `ROUND`.                       | `SELECT ROUND(AVG(price),2) AS avg_price FROM pizzas;`                                                                                                                                             | **$16.44**                                               |
| **3. Total order value per order**                 | Joins `orders`, `order_details`, and `pizzas`. | `SELECT o.order_id, SUM(od.quantity * p.price) AS order_value FROM orders o JOIN order_details od ON o.order_id = od.order_id JOIN pizzas p ON od.pizza_id = p.pizza_id GROUP BY o.order_id;`      | First order value: **13.25**                             |
| **4. Total quantity sold per category**            | Joins with `pizza_types`.                      | Uses `JOIN` + `GROUP BY`.                                                                                                                                                                          | Classic category sold: **14,888**                        |
| **5. Categories with more than 5,000 pizzas sold** | Adds `HAVING` clause.                          | `... HAVING SUM(od.quantity) > 5000;`                                                                                                                                                              | All four categories qualify                              |
| **6. Pizzas never ordered**                        | Uses `LEFT JOIN` with `NULL` check.            | `SELECT p.* FROM pizzas p LEFT JOIN order_details od ON p.pizza_id = od.pizza_id WHERE od.order_id IS NULL;`                                                                                       | Includes pizzas like “The Big Meat Pizza (M, L)”         |
| **7. Price difference between pizza sizes**        | Uses a `SELF JOIN` on `pizzas`.                | `SELECT p1.pizza_type_id, p1.size AS size1, p2.size AS size2, p2.price - p1.price AS price_difference FROM pizzas p1 JOIN pizzas p2 ON p1.pizza_type_id = p2.pizza_type_id AND p1.size < p2.size;` | Example: S → M difference is **4** for BBQ Chicken Pizza |

---

## 🚀 What You Learn from This Project

✔ SQL Filtering

✔ Data Aggregation

✔ Multi-table Joins

✔ Handling Missing Data

✔ Pattern Matching

✔ Business-Level Reporting

✔ Sales Insights & Analytics

✔ Data Cleaning + Exploration

---

## 📦 Technologies Used

* **SQL / MySQL**
* **DBMS concepts**
* **Joins & Aggregations**
* **Data cleaning techniques**

---

## 🧑‍💻 Author

**Tharannum** — Passionate about Data Analytics, SQL, and AI-driven insights.
Working on real-world datasets to sharpen analytical skills.

---

 

