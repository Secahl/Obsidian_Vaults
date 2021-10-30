## Using an SQL injection UNION attack to retrieve interesting data
 
  
When you have determined the number of columns returned by the original query and found which columns can hold string data, you are in a position to retrieve interesting data.  

Suppose that:  
• The original query returns two columns, both of which can hold string data.  
• The injection point is a quoted string within the `WHERE` clause.  
• The database contains a table called `users` with the columns `username` and `password`.  
  
In this situation, you can retrieve the contents of the `users` table by submitting the input:  
<font color=ligreen>' UNION SELECT username, password FROM users--  
  
Of course, the crucial information needed to perform this attack is that there is a table called `users` with two columns called `username` and `password`. Without this information, you would be left trying to guess the names of tables and columns. In fact, all modern databases provide ways of examining the database structure, to determine what tables and columns it contains.