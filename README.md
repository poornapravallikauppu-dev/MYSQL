Zepto Data Analysis Project
This repository contains a structured dataset and SQL-based analysis focused on Zepto product and sales data. The project demonstrates data cleaning, exploration, and business insights generation using SQL.

Repository Structure
├── zepto_csv file                    # Raw dataset
├── Zepto_SQL queries.sql      # SQL queries for analysis
└── README.md                        # Project documentation

 Dataset Overview
File: zepto_csv
The dataset contains product-level information including pricing, discounts, ratings, and availability. 
It can be used for:
Exploratory Data Analysis (EDA)
Pricing strategy evaluation
Discount pattern analysis
Rating distribution insights
Revenue estimation

SQL practice and portfolio projects
Sample Columns (Typical Structure)
Depending on the dataset version, columns may include:
product_name – Name of the product
category – Product category
mrp – Maximum Retail Price
discounted_price – Selling price after discount
discount_percentage – Discount applied
rating – Customer rating
rating_count – Number of ratings
availability – Stock availability

Technologies Used
SQL (MySQL / PostgreSQL compatible)
CSV dataset
Any SQL client (MySQL Workbench, pgAdmin, DBeaver, etc.)


 How to Use This Project
1️⃣ Import Dataset into SQL
Create a table:sql or pgadmin
CREATE TABLE zepto_products (
    product_name TEXT,
    category TEXT,
    mrp FLOAT,
    discounted_price FLOAT,
    discount_percentage FLOAT,
    rating FLOAT,
    rating_count INT,
    availability TEXT
);
Import the CSV file:
Use LOAD DATA INFILE (MySQL), or
Use the Import Wizard in your SQL tool.

2️⃣ Run SQL Analysis
Open:
Zepto_SQL_data_analysis.sql
Execute queries to generate insights such as:
Top discounted products
Highest rated products
Category-wise average pricing
Revenue estimation
Products with maximum rating counts
Discount impact analysis

 Example Business Questions Answered
Which category offers the highest average discount?
What are the top-rated products?
Is there a correlation between discount and rating?
Which products generate the highest potential revenue?
What is the price distribution across categories?

 Project Objectives
Practice SQL querying techniques
Perform real-world retail data analysis
Generate business insights from e-commerce data
Build a portfolio-ready data analytics project

 Skills Demonstrated
Data Cleaning
Aggregations (SUM, AVG, COUNT)
GROUP BY & ORDER BY
Subqueries
Filtering & Conditional Logic
Business Insight Generation

 Possible Extensions
Create dashboards using Power BI / Tableau
Perform Python-based EDA (Pandas, Matplotlib, Seaborn)
Build price prediction models
Create category-wise profitability analysis
Deploy insights in a web dashboard
