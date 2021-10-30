### Parameter-based access control methods
  
Some applications determine the user's access rights or role at login, and then store this information in a user-controllable location, such as a hidden field, cookie, or preset query string parameter.  
  
The application makes subsequent access control decisions based on the submitted value.  
  
For example:  

-
`https://insecure-website.com/login/home.jsp?admin=true` 
-
`https://insecure-website.com/login/home.jsp?role=1` 

This approach is fundamentally insecure because a user can simply modify the value and gain access to functionality to which they are not authorized, such as administrative functions.  
  
  
>LAB [User role controlled by request parameter](https://portswigger.net/web-security/access-control/lab-user-role-controlled-by-request-parameter)  
  
>LAB [User role can be modified in user profile](https://portswigger.net/web-security/access-control/lab-user-role-can-be-modified-in-user-profile)