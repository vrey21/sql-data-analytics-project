# SQL Data Warehouse Project

This project builds a small **SQL Server data warehouse** using customer, product, and sales data. It demonstrates how to create a database, organize tables into a schema, and load CSV files with `BULK INSERT`.

## Project Goal

Create a clean, structured Gold layer that can be queried for business analysis, such as sales trends, customer behavior, and product performance.

## Tools Used

- SQL Server
- SQL Server Management Studio (SSMS)
- GitHub

## Database Structure

The project creates a database called `DataWarehouseAnalytics` and a schema called `gold`.

| Table | Purpose | Rows Loaded |
|---|---|---:|
| `gold.dim_customers` | Customer demographic and account information | 18,484 |
| `gold.dim_products` | Product, category, and cost information | 295 |
| `gold.fact_sales` | Sales transactions, dates, quantities, and amounts | 60,398 |

## Project Files

```text
sql-data-analytics-project/
├── datasets/
│   └── csv-files/
│       ├── dim_customers.csv
│       ├── dim_products.csv
│       └── fact_sales.csv
├── scripts/
│   ├── 00_init_database.sql
│   ├── 01_database_exploration.sql
│   ├── 02_dimensions_exploration.sql
│   ├── 03_date_range_exploration.sql
│   ├── 04_measures_exploration.sql
│   ├── 05_magnitude_analysis.sql
│   ├── 06_ranking_analysis.sql
│   ├── 07_change_over_time_analysis.sql
│   ├── 08_cumulative_analysis.sql
│   ├── 09_performance_analysis.sql
│   ├── 10_data_segmentation.sql
│   ├── 11_part_to_whole_analysis.sql
│   ├── 12_report_customers.sql
│   └── 13_report_products.sql
└── README.md
```

## How to Run the Project

1. Download or clone this repository.
2. Open `scripts/00_init_database.sql` in SSMS.
3. In each `BULK INSERT` statement, replace the placeholder with the full path to the matching CSV file in `datasets/csv-files/` on **your** computer.

   | Placeholder | File |
   |---|---|
   | `PASTE_FULL_PATH_TO_gold.dim_customers.csv_HERE` | `dim_customers.csv` |
   | `PASTE_FULL_PATH_TO_gold.dim_products.csv_HERE` | `dim_products.csv` |
   | `PASTE_FULL_PATH_TO_gold.fact_sales.csv_HERE` | `fact_sales.csv` |

   Example:

   ```sql
   FROM 'PASTE_FULL_PATH_TO_gold.dim_customers.csv_HERE'
   ```

4. Run the complete script.
5. SQL Server will create the database, create the `gold` schema and tables, and load the CSV data.
6. Run the analysis scripts (`01`–`13`) in order to explore the data and build the report views.

## What the Setup Script Does

- Removes the existing `DataWarehouseAnalytics` database, if it already exists
- Creates a new `DataWarehouseAnalytics` database
- Creates the `gold` schema
- Creates the customer, product, and sales tables
- Loads the three CSV files into those tables using `BULK INSERT`

> **Warning:** The setup script drops and recreates the database each time it runs. Any data previously saved in `DataWarehouseAnalytics` will be deleted.

## Analysis Scripts

| Script | What it does |
|---|---|
| `01_database_exploration.sql` | Lists tables and columns in the database |
| `02_dimensions_exploration.sql` | Explores unique countries, categories, and products |
| `03_date_range_exploration.sql` | Finds order date range and customer age range |
| `04_measures_exploration.sql` | Calculates key business metrics (sales, quantity, orders, customers) |
| `05_magnitude_analysis.sql` | Groups customers, products, and revenue by dimension |
| `06_ranking_analysis.sql` | Ranks top and bottom products and customers |
| `07_change_over_time_analysis.sql` | Tracks sales trends by year and month |
| `08_cumulative_analysis.sql` | Calculates running totals and moving averages |
| `09_performance_analysis.sql` | Compares yearly product sales to average and prior year |
| `10_data_segmentation.sql` | Segments products by cost and customers into VIP / Regular / New |
| `11_part_to_whole_analysis.sql` | Shows each category's share of total sales |
| `12_report_customers.sql` | Creates the `gold.report_customers` view with customer KPIs |
| `13_report_products.sql` | Creates the `gold.report_products` view with product KPIs |
