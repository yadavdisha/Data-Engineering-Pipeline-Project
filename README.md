# Azure Data Engineering Pipeline Automation Project
## Overview:
This project automates the process of data movement, transformation, and reporting using Azure services. It encompasses the extraction of data from an on-premises SQL Server database, loading it into Azure Data Lake Storage, performing preprocessing and transformation using Databricks, storing the processed data in Azure Synapse Analytics, and generating reports using Power BI. The pipeline is designed to run daily and fetch the latest data for analysis and reporting.

![image](https://github.com/yadavdisha/Data-Engineering-Pipeline-Project/assets/34658273/574a76c2-5a15-4be7-939f-889c97b06ab7)
## Technologies Used:
1.SQL Server Management Studio (SSMS)
2.Azure Data Factory
3.Azure Data Lake Storage
4.Azure Databricks
5.Azure Synapse Analytics
6.Power BI
## Project Structure:
Datbricks Code: Includes notebooks for data preprocessing and transformation
Databricks_Notebooks: Includes notebooks for data preprocessing and transformation.
PowerBI_Reports: Stores Power BI report files.
## Steps:
## 1.On Prem SQL Server:

1.Used E-commerce Sales dataset.
2.Installed a Microsoft SQL Server on my personal computer.
3.Imported the dataset via Microsoft SQL Server Management Studio.
![image](https://github.com/yadavdisha/Data-Engineering-Pipeline-Project/assets/34658273/b7bf2f2d-68d5-4158-8875-1957387283cf)

## 2.Data Ingestion
To move data from our on-premises SQL server to Azure SQL, we use Azure Data Factory.
Hers What i did:
1.Install Self-Hosted Integration Runtime.
2.Connect Azure Data Factory to our local SQL Server.
3.Set up a copy pipeline to move all tables from our local SQL server to a special folder called "Raw" in Azure Data Lake.
![image](https://github.com/yadavdisha/Data-Engineering-Pipeline-Project/assets/34658273/5c5e96d8-e29c-4d2b-bbf3-66c560b47dac)
## Create Pipeline on Azure datafactory to automatically load the data from On prem sql to Azure data lake 
![image](https://github.com/yadavdisha/Data-Engineering-Pipeline-Project/assets/34658273/5aed96eb-7664-4abd-9ad6-599bb2d4e008)

##  Data Transformation:
Data undergoes structured transformation through raw, discovery, and publish stages for refinement.
Azure Databricks, utilizing PySpark, manages these transformations seamlessly.
Initially stored as parquet  data  format in the "raw" folder, data evolves into delta format as it progresses.
Transformation process  in Databricks notebooks includes:
Mounting the storage.
Transforming data from "raw" to "discovery" layer.
Further refining data from "discovery" to "publish" layer.
Azure Data Factory is set up to run the "raw" to "discovery" and "discovery" to "publish" notebooks automatically each time the pipeline is executed.
![image](https://github.com/yadavdisha/Data-Engineering-Pipeline-Project/assets/34658273/33e42ca5-c593-4a74-ad92-cf8e5c7a97da)

## 3: Data Loading
Data from the "publish" zone which is the final zone is sent to Power BI for reporting through Azure Synapse. Here's how it works:

1.Connect Azure data lake storage  (Publish zone) to Azure Synapse.
2.Create stored procedures to extract table info and make SQL views.
3.Store these views in a server-less SQL Database in Synapse.
4.Data in Synapse is Delta formatted, providing reliability, scalability, and performance. It supports versioning and backup for data management.
![image](https://github.com/yadavdisha/Data-Engineering-Pipeline-Project/assets/34658273/f205f49d-a39d-46fe-973f-0a5a1eec0309)
## Create data model in power BI

![image](https://github.com/yadavdisha/Data-Engineering-Pipeline-Project/assets/34658273/a1d05068-626c-4525-bf29-fa433278720d)

## Data Reporting
![image](https://github.com/yadavdisha/Data-Engineering-Pipeline-Project/assets/34658273/7ec624ee-3b42-4a56-8e2b-13ab68284e8a)

## Final Pipeline Test

I added a new row to the on-premises database. Shortly after, the pipeline automatically triggered at the scheduled time, leading to an increase in the customer count.
![image](https://github.com/yadavdisha/Data-Engineering-Pipeline-Project/assets/34658273/a21f1257-573d-4181-a5ac-480245955bfb)
























