📋 Overview

This project demonstrates E-commerce data analysis using Python (Pandas, Matplotlib, Seaborn) and MySQL.
It connects Python to a MySQL database, imports multiple CSV datasets, creates tables dynamically, and performs SQL-based analytics with data visualization.

🚀 Features

✅ Automatic creation of MySQL tables from CSV files
✅ Dynamic data type detection and table schema generation
✅ SQL queries for analytical insights
✅ Integration of Python visualization (Matplotlib + Seaborn)
✅ Real-world business metrics extraction

🗂️ Dataset Description

The project uses multiple CSV files representing different entities in an E-commerce platform:

File Name	Description
customers.csv	Customer details including city and state
orders.csv	Order timestamps and IDs
sellers.csv	Seller information
products.csv	Product categories and IDs
geolocation.csv	Location mapping details
payments.csv	Payment details for each order
order_items.csv	Order item and price mapping
🧠 Project Workflow
1️⃣ Data Import and Database Setup

Connects to MySQL using mysql.connector

Creates tables automatically for each CSV file

Detects and maps Python data types to SQL (INT, FLOAT, TEXT, etc.)

Inserts all CSV data into MySQL database

2️⃣ Data Cleaning

Handles missing values (NaN → NULL)

Cleans and formats column names

3️⃣ Data Analysis using SQL + Python

Executed SQL queries to explore and visualize trends:

Query	Description
Q1	List all unique customer cities
Q2	Count total orders placed in 2017
Q3	Calculate total sales per product category
Q4	Percentage of orders paid in installments
Q5	Number of customers per state
Q6	Monthly order counts for 2018
📊 Example Insights & Visuals

🧾 Q3 – Total Sales per Category

SELECT UPPER(products.product_category) AS category,
       ROUND(SUM(payments.payment_value), 2) AS sales
FROM products
JOIN order_items ON products.product_id = order_items.product_id
JOIN payments ON payments.order_id = order_items.order_id
GROUP BY category;


📈 Q5 – Customer Count by State

plt.figure(figsize=(9,4))
plt.bar(df["state"], df["customer_count"])
plt.xticks(rotation=90)
plt.xlabel("States")
plt.ylabel("Customer Count")
plt.title("Count of Customers by States")
plt.show()

🧩 Technologies Used
Tool	Purpose
Python (Pandas, Matplotlib, Seaborn)	Data manipulation & visualization
MySQL	Database management & querying
MySQL Connector	Database connection from Python
Jupyter / VS Code	Development environment
⚙️ Setup Instructions

1️⃣ Clone this repository

git clone https://github.com/yourusername/ecommerce-data-analysis.git
cd ecommerce-data-analysis


2️⃣ Install required Python packages

pip install pandas mysql-connector-python matplotlib seaborn


3️⃣ Set up your MySQL Database

CREATE DATABASE ecommerce;


4️⃣ Update database credentials in the Python script:

conn = mysql.connector.connect(
    host='localhost',
    user='root',
    password='12345',
    database='ecommerce'
)


5️⃣ Run the Python file

python ecommerce_analysis.py

📌 Future Enhancements

Add dashboard using Streamlit or Power BI

Implement predictive sales modeling using ML

Automate daily ETL updates

🧑‍💻 Author

Junaid War
💼 Data Science & ML Enthusiast
📧 your.email@example.com

🌐 LinkedIn Profile
