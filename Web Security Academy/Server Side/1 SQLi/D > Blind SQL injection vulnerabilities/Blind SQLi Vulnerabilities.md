
## Blind SQL injection vulnerabilities

 Many instances of SQL injection are blind vulnerabilities. This means that the application does not return the results of the SQL query or the details of any database errors within its responses. Blind vulnerabilities can still be exploited to access unauthorized data, but the techniques involved are generally more complicated and difficult to perform.  
With blind SQL injection vulnerabilities, many techniques such as [UNION attacks](https://portswigger.net/web-security/sql-injection/union-attacks), are not effective because they rely on being able to see the results of the injected query within the application's responses. It is still possible to exploit blind SQL injection to access unauthorized data, but different techniques must be used.  
  
Depending on the nature of the vulnerability and the database involved, the following techniques can be used to exploit blind SQL injection vulnerabilities: 

• You can change the logic of the query to trigger a detectable difference in the application's response depending on the truth of a single condition. This might involve injecting a new condition into some Boolean logic, or conditionally triggering an error such as a divide-by-zero.  
• You can conditionally trigger a time delay in the processing of the query, allowing you to infer the truth of the condition based on the time that the application takes to respond.  
• You can trigger an out-of-band network interaction, using [OAST](https://portswigger.net/burp/application-security-testing/oast) techniques. This technique is extremely powerful and works in situations where the other techniques do not. Often, you can directly exfiltrate data via the out-of-band channel, for example by placing the data into a DNS lookup for a domain that you  
  
  
**REMEMBER**: _The code of execution in sql is that the execution always starts from FROM and then comes SELECT_


Linked Nodes:

[[Exploiting blind SQL injection by triggering conditional responses]]
[[Inducing conditional responses by triggering SQL errors]]
[[Exploiting blind SQL injection by triggering time delays]]
[[Exploiting blind SQL injection using out-of-band (OAST) techniques]]

