# NYC Taxi Data Engineering Project

## Overview

This project implements a comprehensive data engineering pipeline for processing NYC Taxi dataset using modern cloud technologies. The solution follows a medallion architecture pattern with bronze, silver, and gold layers, providing scalable data processing from raw ingestion to business intelligence reporting.

## Architecture
![Architecture Diagram](https://github.com/Abhishekmohite25/NYC-TAXI-DE-PROJECT/blob/5dfc966e9313be29bee71bb1c8999971d25ff9f8/Architecture.png)

The project implements a three-tier data lakehouse architecture:

- **Bronze Layer**: Raw data ingestion and storage
- **Silver Layer**: Data transformation and cleansing
- **Gold Layer**: Business-ready analytics data

## Technology Stack

- **Cloud Platform**: Microsoft Azure
- **Data Orchestration**: Azure Data Factory
- **Data Storage**: Azure Data Lake Storage Gen2
- **Data Processing**: Databricks (PySpark & SQL)
- **Data Format**: Parquet (Bronze/Silver), Delta Lake (Gold)
- **Security**: Azure Entra ID (formerly Azure AD)
- **Visualization**: Power BI

## Data Pipeline

### Bronze Layer - Data Ingestion

**Data Source:** [NYC TAXI DATASET](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page)

**Azure Data Factory Components:**
- **HTTP Connector**: Connects to NYC Taxi website for data retrieval
- **ForEach Activity**: Iterates through multiple data files
- **IfElse Activity**: Implements conditional logic for data validation
- **CopyData Activity**: Transfers data to Azure Data Lake Storage Gen2

![Azure Data Factory 1](https://github.com/Abhishekmohite25/NYC-TAXI-DE-PROJECT/blob/5df70f6c13ce43e6095f42750c342f80f5c6c60b/Screenshots/adf1.png)

![Azure Data Factory 2](https://github.com/Abhishekmohite25/NYC-TAXI-DE-PROJECT/blob/5df70f6c13ce43e6095f42750c342f80f5c6c60b/Screenshots/adf2.png)

**Process:**
1. Automated data extraction from NYC Taxi website
2. Raw parquet files stored in bronze layer
3. Metadata capture and error handling

![Bronze ADLS](https://github.com/Abhishekmohite25/NYC-TAXI-DE-PROJECT/blob/5df70f6c13ce43e6095f42750c342f80f5c6c60b/Screenshots/bronze_adls.png)

### Silver Layer - Data Transformation

**Databricks Processing:**
- **PySpark & SQL**: Data transformation and cleansing operations
- **User-Defined Schema**: Enforces data structure and types
- **Recursive File Lookup**: Processes nested directory structures
- **Parquet Format**: Optimized columnar storage for analytics

**Transformations:**
- Data quality checks and validation
- Standardization of data formats
- Removal of duplicates and null values
- Generating new columns
- Removing unwanted data
- Schema evolution handling

![Silver ADLS](https://github.com/Abhishekmohite25/NYC-TAXI-DE-PROJECT/blob/5df70f6c13ce43e6095f42750c342f80f5c6c60b/Screenshots/silver_adls.png)

### Gold Layer - Analytics-Ready Data

**Delta Lake Implementation:**
- **saveAsTable**: Persists transformed data as managed tables
- **Versioning**: Tracks data changes over time
- **Time Travel**: Enables historical data queries
- **ACID Transactions**: Ensures data consistency

**Features:**
- Optimized for analytical queries
- Support for concurrent reads and writes
- Automatic schema evolution
- Data lineage tracking

![Gold ADLS](https://github.com/Abhishekmohite25/NYC-TAXI-DE-PROJECT/blob/5df70f6c13ce43e6095f42750c342f80f5c6c60b/Screenshots/gold_adls.png)

## Security Implementation

**Azure Entra ID Integration:**
- App registration for service authentication
- Access token-based authorization
- Role-based access control (RBAC)
- Secure communication between services

**Security Features:**
- Encrypted data at rest and in transit
- Fine-grained access permissions
- Service principal authentication
- Network security rules

## Business Intelligence

**Power BI Integration:**
- Direct connectivity to Delta Lake gold layer
- Real-time data refresh capabilities
- Interactive dashboards and reports
- Self-service analytics for business users

## Key Features

- **Scalability**: Handles large volumes of NYC taxi data
- **Reliability**: Robust error handling and retry mechanisms
- **Performance**: Optimized data formats and processing
- **Governance**: Data lineage and audit trails
- **Flexibility**: Support for schema evolution and changing requirements

## Data Flow

1. **Ingestion**: Raw NYC taxi data extracted from source API
2. **Processing**: Data transformed through bronze → silver → gold layers
3. **Storage**: Optimized storage in Delta Lake format
4. **Analytics**: Business intelligence through Power BI dashboards

## Monitoring and Maintenance

- Azure Data Factory monitoring for pipeline execution
- Databricks job monitoring and alerting
- Delta Lake optimization and maintenance
- Power BI usage analytics

## Performance Optimization

- Partitioning strategies for large datasets
- Delta Lake optimization techniques
- Query performance tuning
- Resource scaling based on workload
