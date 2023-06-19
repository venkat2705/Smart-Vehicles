# Smart-Vehicles

Smart Vehicles is a Data engineering project which gives you a good understanding of how Azure Data Factory works and How can we connect AWS S3 with Azure Data Factory. 
In this project we are going to implement the below architecture. The main motto of the architecture is to collect every day data and analyse it in Azure SQL Server. 
First we collect data every day into an AWS S3 and we move that data from AWS S3 to Azure Data Lake Gen 2 using ADF pipeline (by a manual trigger). 
Now we will evaluate if the data that we got is valid or not and push into staging folder if it is valid and to rejected folder if it is not valid. 
From here we must move data from staging to Azure SQL server to perform required analytics there. We creates a storage event trigger that triggers the pipeline whenever data comes into staging folder and the pipeline moves the same data into Azure SQL Server.
