# Data Engineering Craft
Collection of my different types of Data Engineering optimized techniques.  
### Tools
1. SQL - PostgreSQL, MySQL or any other SQL
2. Databricks
3. Snowflake
4. Deltalake
5. Ingress
6. Airglow
7. Kafka

### Setup 
Please install the following using command 
```
pip install jupyter jupysql duckdb-engine
```  
- SQL magic commands (%sql)
- A built-in database (DuckDB) so you don’t need external setup

Use the following command to connect to local duck DB in your created Jupyter notebook in VScode. And run the cell.
```
%load_ext sql
%sql duckdb://
``` 
Run your first SQL query in the jupyter notebook cell 
```
%%sql
SELECT 1 AS example;
```  
Create your new table using the SQL query below in your jupyter notebook cell
```
%%sql
CREATE TABLE users AS
SELECT * FROM (VALUES (1, 'Alice'), (2, 'Bob')) AS t(id, name);
```
Now run the select query to check the user table
```
%%sql
SELECT * FROM users;
```
### Setup for PostgreSQL 
