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
First install postgreSQL adapter for python known as pyscopg2 or psycopg2-binary using the following command
```
pip install psycopg2
``` 
After successful installation, use the following command to connect with your PostgreSQL database already setup and running using pgadmin4 or postgreSQL CLI, with username as postgres, password as admin and database name as postgres running at default port 5432 
```
%sql postgresql://postgres:admin@localhost/postgres
```  
Once its successfully connected use the following code in the jupyter notebook cell to create a table in it. 
```
%%sql
CREATE TABLE categories (
  category_id SERIAL NOT NULL PRIMARY KEY,
  category_name VARCHAR(255),
  description VARCHAR(255)
);
```
Now insert some dummy data in the table categories you have created above 
```
%%sql 
INSERT INTO categories (category_name, description)
VALUES
  ('Beverages', 'Soft drinks, coffees, teas, beers, and ales'),
  ('Condiments', 'Sweet and savory sauces, relishes, spreads, and seasonings'),
  ('Confections', 'Desserts, candies, and sweet breads'),
  ('Dairy Products', 'Cheeses'),
  ('Grains/Cereals', 'Breads, crackers, pasta, and cereal'),
  ('Meat/Poultry', 'Prepared meats'),
  ('Produce', 'Dried fruit and bean curd'),
  ('Seafood', 'Seaweed and fish');
``` 
Now run the select query to get all the rows from your table
```
%%sql
SELECT * FROM categories;
```  
Creating pandas Dataframe from the postgreSQL table
```
result = %sql SELECT * FROM categories; 
df = result.DataFrame()
print(df)
```