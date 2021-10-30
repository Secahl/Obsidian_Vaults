## How to prevent SQL injection
  
Most instances of SQL injection can be prevented by using _**parameterized queries**_ (also known as _prepared statements_) _instead of string concatenation within the query._  
  
The following code is vulnerable to SQL injection because the user input is concatenated directly into the query:  
```SQL 
String query = "SELECT * FROM products WHERE category = '"+ input + "'";`  
`Statement statement = connection.createStatement();`  
`ResultSet resultSet = statement.executeQuery(query);` 
```
<br>

This code can be easily rewritten in a way that prevents the user input from interfering with the query structure:  
```SQL
PreparedStatement statement = connection.prepareStatement("SELECT * FROM products WHERE category = ?");`  
`statement.setString(1, input);`  
`ResultSet resultSet = statement.executeQuery();`  
```
<br>

Parameterized queries can be used for any situation where untrusted input appears as data within the query,  
_including the_ _`WHERE`_ _clause and values in an_ _`INSERT`_ _or_ _`UPDATE`_ _statement_.  
  
They can't be used to handle untrusted input in other parts of the query, such as table or column names, or the `ORDER BY` clause. Application functionality that places untrusted data into those parts of the query will need to take a different approach, such as white-listing permitted input values, or using different logic to deliver the required behavior.  
  
For a parameterized query to be effective in preventing SQL injection, the string that is used in the query must always be a _hard-coded constant, and must never contain any variable data from any origin_.  

**Do not be tempted to decide case-by-case whether an item of data is trusted, and continue using string concatenation within the query for cases that are considered safe.** It is all too easy to make mistakes about the possible origin of data, or for changes in other code to violate assumptions about what data is tainted.