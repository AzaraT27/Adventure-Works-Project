# Adventure-Works-Project
## Project Overview

This project implements an end-to-end Data Engineering pipeline using Azure services. The goal is to ingest, transform, and analyze Adventure Works dataset by following the medallion architecture.

The project demonstrates best practices in data ingestion, transformation, and reporting using:
- Azure Data Lake Storage Gen2 
- Azure Data Factory 
- Azure Databricks
- Azure Synapse Analytics
- Power BI 

## Architecture (Bronze–Silver–Gold)

Bronze Layer (Raw Data):
Raw CSV/JSON files ingested from GitHub into Data Lake.

Silver Layer (Cleaned Data):
Data transformed & cleaned in Databricks.

Gold Layer (Business-ready Data):
Aggregated and curated datasets stored for analytics & reporting in Synapse, exposed to Power BI.

## Components Used
1. Azure Data Lake Storage
   
  Acts as the central data repository.
  Organized into bronze, silver, and gold containers for different data refinement levels.

3. Azure Data Factory

  Used to ingest data from GitHub into the Bronze layer.
  Built parameterized pipelines with:
  Lookup Activity → reads JSON metadata containing file details.
  ForEach Activity → iterates through each file’s metadata.
  Copy Activity → copies data from GitHub → Data Lake.

3. Azure Databricks

   Performs data transformations from Bronze → Silver → Gold.

5. Azure Synapse Analytics
   
  Serverless SQL pool used for querying transformed data.
  Features used:
  OPENROWSET → query files directly from Data Lake.
  External Tables & Views → structured access to Silver/Gold data.
  Connected Synapse to Power BI for dashboards.
