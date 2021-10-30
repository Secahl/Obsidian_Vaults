### Horizontal privilege escalation

Horizontal privilege escalation arises when a user is able to gain _access to_ **resources** belonging to another user, instead of their own resources of that type.  
  
_For example_, if an employee should only be able to access their own employment and payroll records, but can in fact also access the records of other employees, then this is horizontal privilege escalation.  
  
_Horizontal privilege escalation attacks may use similar types of exploit methods to vertical privilege escalation._  
  
_For example_, a user might ordinarily access their own account page using a URL like the following:  
>`https://insecure-website.com/myaccount?id=123`  

Now, if an attacker modifies the `id` parameter value to that of another user, then the attacker might gain access to another user's account page, with associated data and functions.  
  
  
>LAB [User ID controlled by request parameter](https://portswigger.net/web-security/access-control/lab-user-id-controlled-by-request-parameter)  
  
  
In some applications, the exploitable parameter does not have a predictable value.  
For example, instead of an incrementing number, an application might use **globally unique identifiers (GUIDs)** to identify users.  
Here, an attacker might be unable to guess or predict the identifier for another user.  
However, the GUIDs belonging to other users might be disclosed elsewhere in the application where users are referenced, such as user messages or reviews.  
  
>LAB [User ID controlled by request parameter, with unpredictable user IDs](https://portswigger.net/web-security/access-control/lab-user-id-controlled-by-request-parameter-with-unpredictable-user-ids)  
  
  
  
In some cases, an application does detect when the user is not permitted to access the resource, and returns a redirect to the login page.  
However, the response containing the redirect might still include some sensitive data belonging to the targeted user, so the attack is still successful.  
  
>LAB [User ID controlled by request parameter with data leakage in redirect](https://portswigger.net/web-security/access-control/lab-user-id-controlled-by-request-parameter-with-data-leakage-in-redirect)