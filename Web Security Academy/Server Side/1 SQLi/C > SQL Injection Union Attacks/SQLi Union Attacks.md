## About SQLi Union Attacks

  For a `UNION` query to work, two key requirements must be met:  
• The individual queries must return the same number of columns.  
• The data types in each column must be compatible between the individual queries.  
  
To carry out an SQL injection UNION attack, you need to ensure that your attack meets these two requirements. This generally involves figuring out:  
◇ How many columns are being returned from the original query?  
◇ Which columns returned from the original query are of a suitable data type to hold the results from the injected query?

Linked Nodes:
[[Determining the number of columns required in an SQL injection UNION attack]]
[[Probing columns to find columns data type in an SQL injection UNION attack]]
[[Examining the database in SQL injection attacks]]
[[Using an SQL injection UNION attack to retrieve interesting data]]
[[Retrieving multiple values within a single column]]



