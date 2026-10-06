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
│       ├── gold.dim_customers.csv
│       ├── gold.dim_products.csv
│       └── gold.fact_sales.csv
├── scripts/
│   └── 00_init_database.sql
└── README.md
```

## How to Run the Project

1. Download or clone this repository.
2. Open `scripts/00_init_database.sql` in SSMS.
3. In each `BULK INSERT` statement, replace the placeholder with the full path to the matching CSV file on **your** computer.

   Example:

   ```sql
   FROM 'PASTE_FULL_PATH_TO_gold.dim_customers.csv_HERE'
   ```

4. Run the complete script.
5. SQL Server will create the database, create the `gold` schema and tables, and load the CSV data.

## What the Setup Script Does

- Removes the existing `DataWarehouseAnalytics` database, if it already exists
- Creates a new `DataWarehouseAnalytics` database
- Creates the `gold` schema
- Creates the customer, product, and sales tables
- Loads the three CSV files into those tables using `BULK INSERT`

> **Warning:** The setup script drops and recreates the database each time it runs. Any data previously saved in `DataWarehouseAnalytics` will be deleted.

## Next Steps

I plan to use these tables to write SQL queries, explore sales performance, and build portfolio-ready analysis.
