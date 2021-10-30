   ## Probing columns to find columns data type in an SQL injection UNION attack
   
   The reason for performing an SQL injection UNION attack is to be able to retrieve the results from an injected query. Generally, the interesting data that you want to retrieve will be in string form, so you need to find one or more columns in the original query results whose data type is, or is compatible with, string data.  
	   
Having already determined the number of required columns, you can probe each column to test whether it can hold string data by submitting a series of `UNION SELECT` payloads that place a string value into each column in turn. For example, if the query returns four columns, you would submit:  

	' UNION SELECT 'a',NULL,NULL,NULL--  
	' UNION SELECT NULL,'a',NULL,NULL--  
	' UNION SELECT NULL,NULL,'a',NULL--  
	' UNION SELECT NULL,NULL,NULL,'a'--  
	
If the data type of a column is not compatible with string data, the injected query will cause a database error, such as:  
`Conversion failed when converting the varchar value 'a' to data type int.`  
If an error does not occur, and the application's response contains some additional content including the injected string value, then the relevant column is suitable for retrieving string data.