# End-to-End Data Engineering Project — Medallion Architecture (Bronze → Silver → Gold)

This project implements a full Modern Data Engineering Pipeline using:

- Azure Data Factory (ADF) → Data ingestion

- Azure Data Lake Storage Gen2 (ADLS Gen2) → Raw, cleaned, and curated storage

- Databricks (PySpark) → Transformation & Delta Lake

- Synapse / SQL → Serving layer

- Power BI → Reporting

The solution follows the Medallion Architecture, ensuring scalability, reliability, and data quality.

# Architecture
![](https://github.com/abigailmwanza/Adventure-Works-DataEngineering-Project/blob/main/Images/Screenshot%202025-12-04%20at%2011.49.23.png)


# 1.Medallion Architecture Explained

Layer	Purpose	Storage	Tools Used

- Bronze (Raw)	Stores original ingested data exactly as received	ADLS Gen2	ADF
- Silver (Cleaned/Transformed)	Applies cleaning, type casting, deduplication, and normalization	ADLS Gen2	Databricks
- Gold (Curated/Serving)	Business-ready tables for analytics & reports	Synapse / Delta Lake	Databricks, Synapse, Power BI


# Data Ingestion & Analytics Pipeline
## 1. Data Ingestion (ADF)

Bring raw data from HTTP, GitHub, APIs, or Blob into the Bronze layer.

### Key Features:

- Dynamic ingestion using parameters

- Reusable datasets with dynamic file/folder names

- Logging and error handling

- Automated runs via ADF triggers

### Pipeline Flow:
Lookup → ForEach → Copy

- Lookup reads config.json

- ForEach loops through each dataset

- Copy loads data 

## 2. Transformation Layer (Databricks + Delta)

Silver Layer:

- Remove duplicates, Fix data types, Handle nulls, Standardize columns and Add ingestion_date

Gold Layer:

- Apply business rules, Aggregations, Create dimension/fact tables, Optimize Delta tables

### Example PySpark (Silver):

## 3. Serving Layer (Gold + Synapse)

- Gold data loaded into Synapse SQL

- Delta tables for BI reporting

- Analytics-ready data with fast Power BI queries

## 4. Reporting (Power BI)

- Connects to Synapse SQL or Gold Delta tables

- Reports include customer segmentation, sales & revenue insights, and KPIs

## 5. Pipeline Automation

- ADF Trigger: runs daily at 1 AM, logs runs, sends notifications

- Databricks Jobs: execute Bronze → Silver → Gold notebooks sequentially


# What I Learned While Building This Project

Working on this Medallion Architecture project strengthened my technical, analytical, and cloud engineering skills. Some of the key things I learned include:

## 1. Designing a Scalable Data Architecture

- How to apply the Medallion Architecture (Bronze, Silver, Gold) to improve data quality and performance.

- Why separating raw, cleaned, and curated data reduces pipeline failures and increases governance.

## 2. Building Dynamic Data Ingestion in Azure Data Factory

- How to use Lookup + ForEach + Copy activities to ingest multiple datasets automatically.

- Creating parameterized datasets to avoid duplication and make pipelines reusable.

- Debugging ingestion errors such as 404, 42501, and connection issues.

## 3. Structuring ADLS Gen2 for Lakehouse Workloads

- Designing folder structures for raw, transformed, and curated layers.

- Managing access control and understanding permissions (RBAC + ACLs).

- Organizing data in a way that supports Delta Lake and BI tools.

## 4. Transforming Data Using Databricks & Delta Lake

- Writing scalable PySpark transformations.

- Handling data cleaning: duplicates, schema enforcement, nulls, and data types.

- Converting data into Delta format for performance and reliability.

## 5. Building a Serving Layer Using Synapse

- Publishing Gold tables to Synapse for BI use.

- Understanding how SQL pools and serverless queries interact with Delta tables.

- Preparing curated datasets for analytics teams.

## 6. Connecting Power BI to a Lakehouse

- Building fast and optimized reports using Gold tables.

- Understanding how data models improve dashboard performance.

- Designing KPIs and visualizations based on business logic.

## 7. Debugging & Pipeline Error Handling

- Investigating 404 errors when GitHub raw paths change.

- Understanding ADF error logs and troubleshooting failed activities.

- Fixing permission errors between ADF → ADLS → Databricks.

## 8. End-to-End Cloud Engineering Thinking

- How each component fits together (ADF → ADLS → Databricks → Synapse → Power BI).

- Documenting architecture using diagrams and clear flow explanations.

- Thinking like a data engineer: optimization, scalability, automation, and governance.

Implement Unity Catalog for governance
