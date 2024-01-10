# Sales-analytics-Project-Reports

Overview
This repository contains the code and documentation for a Sales Analytics project. The goal of this project is to perform Extract, Transform, and Load (ETL) operations on four CSV files: dim_product.csv, dim_market.csv, dim_customer.csv, and fact_sales_monthly.csv. The project involves importing data into an Excel workbook, transforming it using Power Query, and establishing connections in Power Pivot for further analysis.

# ETL Process

1. **Importing Data:**
   - Open a blank Excel workbook.
   - Go to Data -> Get Data -> From File -> From Folder and select the Sales folder.
  
2. **Power Query Transformation:**
   - In the Power Query window, click on "Transform Data."
   - Reference each file separately to create dynamic references.

3. **Data Cleaning:**
   - **dim_customer.csv:**
     - Convert the data type of the customer_code to text.
     - Standardize spelling for consistent entries.

   - **dim_market.csv:**
     - Promote the first row as a header.
     - Replace "NA" with "North America."

   - **dim_product.csv:**
     - Promote the first row as a header.

   - **fact_sales_monthly.csv:**
     - Transform negative quantity values to positive using the Absolute Value option under the Scientific category.

4. **Connection Only and Data Model:**
   - Close & Load To -> Create Connection Only.
   - Add all tables to the Data Model.

## Data Modeling

1. **Power Pivot:**
   - Establish connections between tables.
   - Connect fact_sales_monthly to dim_product and dim_customer using product_code and customer_code, respectively.
   - Connect dim_customer to dim_market using the market column.
   - Create a Date Table and connect it to fact_sales_monthly using the date column.

## Creating Key Measures

1. **Net Sales:** `=SUM(fact_sales_monthly[net_sales_amount])`
2. **Net Sales 2019:** `CALCULATE([net_sales],dim_date[fiscal year]="2019")`
3. **Net Sales 2020:** `CALCULATE([net_sales],dim_date[fiscal year]="2020")`
4. **Net Sales 2021:** `CALCULATE([net_sales],dim_date[fiscal year]="2021")`

## Reports

1. **Top 10 Products on Net Sales 2020 and 2021:**
   - Filter: Region, Customer, and Division
   - Include Percentage Increase in 2021 compared to 2020.

2. **Division Level Report on Net Sales 2020, 2021:**
   - Filter: Region and Customer
   - Include Percentage Increase in 2021 compared to 2020.

3. **Top and Bottom 5 Products on Total Quantity Sold:**
   - Filter: Region, Division, and Customer

4. **Top 5 Countries on Net Sales of 2021:**
   - Filter: Region and Customer

5. **New Products in 2021 on Net Sales:**
   - Filter: Region, Market, and Customer
