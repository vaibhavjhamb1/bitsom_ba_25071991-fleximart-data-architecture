# FlexiMart Data Architecture Project

**Student Name:** Vaibhav Jhamb
**Student ID:** bitsom_ba_25071991-fleximart-data-architecture
**Email:** vaibhavjhamb1@gmail.com
**Date:** 7th January 2026

## Project Overview
I built an end-to-end data ecosystem for FlexiMart, an e-commerce platform, featuring a robust MySQL-based relational database and a high-performance Star Schema data warehouse. The project includes an automated Python ETL pipeline for data cleaning and a MongoDB implementation to handle semi-structured product catalogs and nested reviews.

## Repository Structure
├── part1-database-etl/
│   ├── etl_pipeline.py
│   ├── schema_documentation.md
│   ├── business_queries.sql
│   └── data_quality_report.txt
├── part2-nosql/
│   ├── nosql_analysis.md
│   ├── mongodb_operations.js
│   └── products_catalog.json
├── part3-datawarehouse/
│   ├── star_schema_design.md
│   ├── warehouse_schema.sql
│   ├── warehouse_data.sql
│   └── analytics_queries.sql
└── README.md

## Technologies Used

-Python 3.x: pandas, mysql-connector-python.
-MySQL 8.0: Relational database and Star Schema warehouse.
-MongoDB 6.0: Document store for semi-structured product data.

## Setup Instructions

### Database Setup

```bash
# Create databases
mysql -u root -p -e "CREATE DATABASE fleximart;"
mysql -u root -p -e "CREATE DATABASE fleximart_dw;"

# Run Part 1 - ETL Pipeline
python part1-database-etl/etl_pipeline.py

# Run Part 1 - Business Queries
mysql -u root -p fleximart < part1-database-etl/business_queries.sql

# Run Part 3 - Data Warehouse
mysql -u root -p fleximart_dw < part3-datawarehouse/warehouse_schema.sql
mysql -u root -p fleximart_dw < part3-datawarehouse/warehouse_data.sql
mysql -u root -p fleximart_dw < part3-datawarehouse/analytics_queries.sql


### MongoDB Setup

mongosh < part2-nosql/mongodb_operations.js

## Key Learnings

I gained hands-on experience in implementing a Star Schema, realizing how it simplifies complex analytical queries through de-normalization of dimensions. I learned to automate data quality checks within an ETL pipeline to ensure that numeric facts remain accurate during migration. Additionally, working with MongoDB taught me the benefits of flexible schemas and embedded documents for handling diverse product attributes and high-volume reviews.

## Challenges Faced

1. Schema Mismatch: I encountered an "Unknown Column" error during SQL aggregation because the total_amount was not pre-calculated; I solved this by implementing on-the-fly multiplication of quantity and price within the SQL script.
2. MongoDB Connection: The local MongoDB service was initially inactive, resulting in a connection timeout; I resolved this by starting the mongod service and verifying the connection via MongoDB Compass.
