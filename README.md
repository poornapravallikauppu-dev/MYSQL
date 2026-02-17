#  Zepto SQL Data Analysis Project

This project performs **data cleaning, exploration, and business analysis** on a grocery product dataset similar to Zepto inventory using **PostgreSQL**.

The goal of this project is to practice real-world data analyst workflow:

> Raw Data → Database → Cleaning → Analysis → Business Insights

---

##  Project Files

| File                    | Description                                  |
| ----------------------- | -------------------------------------------- |
| `Zepto.csv`             | Raw product dataset                          |
| `zepto_sql_queries.sql` | Table creation + cleaning + analysis queries |

---

## 🗄️ Database Schema

Table name: `zepto`

```sql
create table zepto (
    sku_id SERIAL PRIMARY KEY,
    category VARCHAR(120),
    name VARCHAR(150) NOT NULL,
    mrp NUMERIC(8,2),
    discountPercent NUMERIC(5,2),
    availableQuantity INTEGER,
    discountedSellingPrice NUMERIC(8,2),
    weightInGms INTEGER,
    outOfStock BOOLEAN,
    quantity INTEGER
);
```

---

## ⚙️ Steps to Run Project

### 1️⃣ Create Database

```sql
CREATE DATABASE zepto_db;
```

Connect to database in pgAdmin / psql.

---

### 2️⃣ Create Table

Run table creation query from SQL file.

---

### 3️⃣ Import CSV Data

Use pgAdmin Import/Export:

Right Click Table → Import → Select CSV → Map columns

---

### 4️⃣ Data Cleaning Performed

* Removed products where price = 0
* Converted paise → rupees
* Checked NULL values
* Removed invalid records

Example:

```sql
DELETE FROM zepto
WHERE mrp = 0;

UPDATE zepto
SET mrp = mrp / 100.0,
    discountedSellingPrice = discountedSellingPrice / 100.0;
```

---

##  Data Exploration

* Total number of products
* Unique categories
* Duplicate products
* Stock availability

Example:

```sql
SELECT outOfStock, COUNT(sku_id)
FROM zepto
GROUP BY outOfStock;
```

---

## Business Analysis Queries

### 1. Top 10 Highest Discount Products

```sql
SELECT DISTINCT name, mrp, discountPercent
FROM zepto
ORDER BY discountPercent DESC
LIMIT 10;
```

---

### 2. Expensive Products Out of Stock

```sql
SELECT DISTINCT name, mrp
FROM zepto
WHERE outOfStock = TRUE AND mrp > 300
ORDER BY mrp DESC;
```

---

### 3. Estimated Revenue Per Category

```sql
SELECT category,
SUM(discountedSellingPrice * availableQuantity) AS total_revenue
FROM zepto
GROUP BY category
ORDER BY total_revenue;
```

---

### 4. High Price but Low Discount Products

```sql
SELECT DISTINCT name, mrp, discountPercent
FROM zepto
WHERE mrp > 500 AND discountPercent < 10
ORDER BY mrp DESC, discountPercent DESC;
```

---

### 5. Top Categories by Average Discount

```sql
SELECT category,
ROUND(AVG(discountPercent),2) AS avg_discount
FROM zepto
GROUP BY category
ORDER BY avg_discount DESC
LIMIT 5;
```

---

### 6. Best Value Products (Price per Gram)

```sql
SELECT DISTINCT name, weightInGms, discountedSellingPrice,
ROUND(discountedSellingPrice/weightInGms,2) AS price_per_gram
FROM zepto
WHERE weightInGms >= 100
ORDER BY price_per_gram;
```

---

### 7. Product Weight Segmentation

```sql
SELECT DISTINCT name, weightInGms,
CASE
 WHEN weightInGms < 1000 THEN 'Low'
 WHEN weightInGms < 5000 THEN 'Medium'
 ELSE 'Bulk'
END AS weight_category
FROM zepto;
```

---

### 8. Inventory Weight per Category

```sql
SELECT category,
SUM(weightInGms * availableQuantity) AS total_weight
FROM zepto
GROUP BY category
ORDER BY total_weight;
```

---

## 🎯 Key Skills Practiced

* SQL Joins & Aggregations
* Data Cleaning
* Business KPI Analysis
* Revenue Estimation
* Inventory Analysis
* Case Statements
* Real-world dataset handling

---

##  Insights You Can Derive

* Which categories generate most revenue
* Stock shortage detection
* Best value products for customers
* Discount strategy effectiveness
* Inventory distribution


