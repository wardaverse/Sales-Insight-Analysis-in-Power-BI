# Sales-Insight-Analysis-in-Power-BI

## Project Description

This project showcases the **Sales Insights** of an online store that sells a variety of products each year. The goal is to track live **Sales**, **Top Selling Products**, and **Customers**.

I generated a **Power BI** based report along with an interactive dashboard to analyze sales patterns throughout **2017–2020**.

## The Report Helps to See:

1. Revenue per year
2. Revenue per month
3. Revenue per customer
4. Revenue per region
5. Top 5 customers
6. Top 5 sales quantities
7. Sales by customer
8. Sales by city
9. Sales by year
10. Sales by month
11. Overall sales / Revenue

## Tools Used

1. **Microsoft Power BI Desktop**
2. **MySQL Workbench**

## Skills Needed to Complete the Job

1. Data Cleansing
2. DAX Language
3. Analytical Skills
4. SQL Query Language
5. Business Intelligence Knowledge

## SQL Verification Queries

Here are some of the queries that helped me verify my Report and Dashboard results.

### 1. Total Sales Amount (All Years)

The query will tell you the sum of total sales amount throughout all years.

```sql
SELECT SUM(transactions.sales_amount)
FROM date
INNER JOIN transactions
    ON date.date = transactions.order_date
WHERE date.year = '2020'
    AND (transactions.currency = 'INR\r' OR transactions.currency = 'USD\r');
```

### 2. Total Sales in a Specific Region (e.g., Chennai)

This can be used to check the total sales in a specific region, like I checked in **Chennai**.

```sql
SELECT SUM(sales.transactions.sales_amount)
FROM sales.markets
INNER JOIN sales.transactions
    ON sales.markets.markets_code = sales.transactions.market_code
WHERE sales.markets.markets_name = 'Chennai';
```

## Data Model

The project uses a **star-like schema** consisting of the following tables:

- **`transactions`** – Fact table containing `sales_amount`, `order_date`, `market_code`, `customer_code`, `product_code`, and `currency`.
- **`date`** – Dimension table containing `date`, `year`, `month`.
- **`markets`** – Dimension table containing `markets_code`, `markets_name`, `zone`.
- **`customers`** – Dimension table containing `customer_code`, `customer_name`.
- **`products`** – Dimension table containing `product_code`, `product_type`.

Relationships are established between the fact table (`transactions`) and the dimension tables using their respective codes, enabling seamless filtering and aggregation in Power BI.

## How to Use

1. **Clone the repository:**
   ```bash
   git clone https://github.com/wardaverse/Sales-Insight-Analysis-in-Power-BI.git
   ```
2. **Set up MySQL:** Import the provided SQL dump into MySQL Workbench.
3. **Open Power BI:** Load the `.pbix` file and refresh the data source to connect to your local MySQL instance.
4. **Explore the Dashboard:** Use the interactive slicers and visuals to analyze sales trends.

## Acknowledgements

- **Microsoft Power BI** for the visualization platform.
- **MySQL** for the data storage and querying.
- Inspired by real-world business intelligence reporting practices.
