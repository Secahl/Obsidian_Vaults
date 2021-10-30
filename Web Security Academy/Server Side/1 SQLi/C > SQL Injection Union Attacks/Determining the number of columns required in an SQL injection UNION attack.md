    
## Determining the number of columns required in an SQL injection UNION attack 
   
The first method involves injecting a series of `ORDER BY` clauses and incrementing the specified column index until an error occurs.  
' ORDER BY 1--  
' ORDER BY 2--  
' ORDER BY 3--  
etc.  
When the specified column index exceeds the number of actual columns in the result set, the database returns an error.  
  
The second method involves submitting a series of `UNION SELECT` payloads specifying a different number of null values:  
' UNION SELECT NULL--  
' UNION SELECT NULL,NULL--  
' UNION SELECT NULL,NULL,NULL--  
etc.  
If the number of nulls does not match the number of columns, the database returns an error, such as:  
`All queries combined using a UNION, INTERSECT or EXCEPT operator must have an equal number of expressions in their target lists.`  
  
  
 Note  
  
• The reason for using `NULL` as the values returned from the injected `SELECT` query is that the data types in each column must be compatible between the original and the injected queries. Since `NULL` is convertible to every commonly used data type, using `NULL` maximizes the chance that the payload will succeed when the column count is correct.  
• On Oracle, every `SELECT` query must use the `FROM` keyword and specify a valid table. There is a built-in table on Oracle called `dual` which can be used for this purpose. So the injected queries on Oracle would need to look like: `' UNION SELECT NULL FROM DUAL--`.  
• The payloads described use the double-dash comment sequence `--` to comment out the remainder of the original query following the injection point. On MySQL, the double-dash sequence must be followed by a space. Alternatively, the hash character `#` can be used to identify a comment.