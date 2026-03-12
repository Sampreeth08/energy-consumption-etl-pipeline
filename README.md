# Energy Consumption Forecasting Pipeline

## Project Overview

The Energy Consumption Forecasting Pipeline is a data engineering
project designed to process and transform household energy consumption
data for forecasting and analytics.\
The pipeline uses Databricks and PySpark to ingest raw CSV files from
AWS S3, clean and standardize the data, and store it in Delta Lake
tables. The final datasets are optimized for analytical queries and
forecasting use cases.

## Data Source

The data used in this project comes from the **Household Power
Consumption Dataset (Kaggle)**.\
Raw CSV files are stored in AWS S3 using the following path structure:

s3://bucket/raw/energy_data/YYYY/MM/DD/

The dataset contains timestamped records of electricity usage along with
measurements such as voltage, active power, and sub‑metering values.

## Data Architecture

This pipeline follows the **Medallion Architecture** pattern.

Bronze Layer\
Table: energy_catalog.raw.usage_records\
Stores raw ingested data exactly as received from source systems.

Silver Layer\
Table: energy_catalog.processed.usage_cleaned\
Contains cleaned, deduplicated, and standardized data ready for
analysis.

Gold Layer\
Table: energy_catalog.analytics.forecast_features\
Contains aggregated energy consumption metrics used for forecasting and
business analysis.

## Key Transformations

The pipeline performs several transformations to improve data quality
and usability:

-   Ingest CSV files from AWS S3
-   Handle malformed records and schema inference
-   Remove duplicate records
-   Standardize timestamps and data formats
-   Join data with dimension tables
-   Generate aggregated consumption metrics for forecasting

## Pipeline Orchestration

The pipeline is orchestrated using **Databricks Workflows** and runs as
a daily batch process.

Schedule: **4:00 AM UTC**

## Error Handling and Monitoring

Pipeline failures and data anomalies are logged into:

energy_catalog.logs.etl_errors

Alert notifications can be triggered to notify the team if data quality
issues or job failures occur.

## Technologies Used

-   Databricks
-   PySpark
-   Delta Lake
-   AWS S3
-   boto3
-   pytest
-   Git

## Project Objective

The objective of this pipeline is to create a scalable and reliable data
processing workflow that supports accurate energy consumption
forecasting and helps improve energy resource planning.
