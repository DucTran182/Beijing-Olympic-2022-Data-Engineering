# Beijing-Olympic-2022-Data-Engineering
This project aims to create a data pipeline with Microsoft Azure

![Flowchart (1)](https://github.com/DucTran182/Beijing-Olympic-2022-Data-Engineering/assets/102782569/aeb69ce4-26c7-4871-88eb-8424228e0565)

### 1. On-premise MS SQL Server Database
Creating username and password to access the all tables. Then adding them into the Vault Secret Key on MS Azure. 
```
CREATE LOGIN benz WITH PASSWORD = '12345qwer';
create user benz for login benz
```
### 2. Azure Data Factory & Data Lake GEN2
Connect the ADF with SQL Server with an Integration Runtime. Using ***lookup*** function to add all tables in the ADF.
```
SELECT 
s. name AS SchemaName,
t. name AS TableName
FROM sys.tables t
INNER JOIN sys.schemas s
ON t.schema_id = s.schema_id	
WHERE s.name = 'dbo'
```
The raw data are stored in the Data Lake GEN2
