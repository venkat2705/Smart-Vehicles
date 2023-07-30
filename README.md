# Smart-Vehicles Data Engineering Project.

## Project Goals

1. Data Ingestion: We need to build a proper mechanism to ingest data from various sources into AWS S3
2. ETL System: We always get the data in raw format, so we must transform this data into usable format by using required transformations in Azure Data Factory.
3. Data lake: We get data from different sources so we need to have a centralized repo to store them. Here we are using ADLS Gen 2.
4. Scalability: You never know when we are going to get huge volumes of data, so we need to make sure that our system is able to cope up with that sudden change.
5. Cloud: When we have vast data it is always better to go with cloud because it is easy to use and scalable. Here we are using AWS and Azure cloud environments combinedly.

## Services that we are going to use in this project.

1. Amazon S3 : Amazon S3 is an object storage service that provides manufacturing scalability, data availability, security, and performance.
2. Azure Data Lake Stoage Gen 2 : It is a scalable and secure cloud-based storage service provided by Microsoft Azure. It is designed to store and manage big data in its native format.
3. Azure Data Factory : It is a cloud-based data integration service and it enables users to efficiently orchestrate and automate the movement and transformation of data between different data stores and systems.
4. Azure SQL server : it is a fully managed relational database service and it is built on the same SQL Server engine, offering all the features and capabilities of SQL Server with the added benefits of cloud scalability, high availability, and automated management.
5. Azure Triggers : These are specifically Azure Functions Triggers, are event-driven mechanisms in the Azure cloud platform. They allow users to execute serverless functions in response to specific events or triggers like data changes.

## Architecture Used

<img width="1036" alt="Smart_Vehicles_architecture (1)" src="https://github.com/venkat2705/Smart-Vehicles/assets/60357150/b2fd50e1-4887-4972-826d-6ff286cb6fbb">

## High Level Project Flow

Amazon S3 --> Azure Data Factory --> Landing --> Trigger --> Staging/rejected --> Azure Data Factory --> Azure SQL server

## Deatiled Project Flow

1. First we collect data every day into an AWS S3 and we move that data from AWS S3 to Azure Data Lake Gen2 using ADF pipeline (by a manual trigger).
2. Here we can also automate the trigger by arranging whenever the data gets into Azure Data Lake Gen2 and the ADF pipeline starts automatically.
3. Now we run a Function code to evaluate if the data that we got is valid or not and then pushes into staging folder if it is valid and to rejected folder if it is not valid.
4. Ignore the data in the rejected folder.
5. From here we must move data from staging to Azure SQL server to perform required analytics there.
6. We creates a storage event trigger that triggers the pipeline whenever data comes into staging folder and the pipeline moves the same data into Azure SQL Server.

You need to have good knowledge on Azure cloud services especially Azure Data factory and Azure SQL server to be able to perform the required ETL operations and analytics in SQL.

