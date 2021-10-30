  ## SQL injection in different parts of the query

  
Most SQL injection vulnerabilities arise within the `WHERE` clause of a `SELECT` query. This type of SQL injection is generally well-understood by experienced testers.  
But SQL injection vulnerabilities can in principle occur at any location within the query, and within different query types. The most common other locations where SQL injection arises are:  
▪ In `UPDATE` statements, within the updated values or the `WHERE` clause.  
• In `INSERT` statements, within the inserted values.  
• In `SELECT` statements, within the table or column name.  
• In `SELECT` statements, within the `ORDER BY` clause.  
 

## Database-specific factors

 
Some core features of the SQL language are implemented in the same way across popular database platforms, and so many ways of detecting and exploiting SQL injection vulnerabilities work identically on different types of database.  
However, there are also many differences between common databases. These mean that some techniques for detecting and exploiting SQL injection work differently on different platforms. For example:  
• Syntax for string concatenation.  
• Comments.  
• Batched (or stacked) queries.  
• Platform-specific APIs.  
• Error messages.  
  
  
**REMEMBER**:  
A. _The code of execution in sql is that the execution always starts from FROM and then comes SELECT_  
B. _If the query doesn't work then make sure to URL encode the query with Ctrl+U on Burp_  
C. _Try the query again without the comment -- if the query doesn't work_

Linked Branches:

- [[A > Retrieving Hidden Data]]
- [[B > Subverting Application Logic]]
- [[SQLi Union Attacks]]
- [[Blind SQLi Vulnerabilities]]
- [[E > Second-order SQL injection]]
- [[F > How to prevent SQL injection]]- 












