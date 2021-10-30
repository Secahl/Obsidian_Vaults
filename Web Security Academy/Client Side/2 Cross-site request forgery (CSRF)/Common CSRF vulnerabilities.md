Parent Links : [[Cross-site request forgery (CSRF)]]     

## Common CSRF vulnerabilities
  
Most interesting CSRF vulnerabilities arise due to mistakes made in the validation of [CSRF tokens](https://portswigger.net/web-security/csrf/tokens).  
In the previous example, suppose that the application now includes a CSRF token within the request to change the user's password:  
```http 
POST /email/change HTTP/1.1  
Host: vulnerable-website.com  
Content-Type: application/x-www-form-urlencoded  
Content-Length: 68  
Cookie: session=2yQIDcpia41WrATfjPqvm9tOkDvkMvLm  
  
csrf=WfF1szMUHhiokx9AHFply5L2xAOfjRkE&email=wiener@normal-user.com
```

This ought to prevent CSRF attacks because it violates the necessary conditions for a CSRF vulnerability: the application no longer relies solely on cookies for session handling, and the request contains a parameter whose value an attacker cannot determine. However, there are various ways in which the defense can be broken, meaning that the application is still vulnerable to CSRF.


#### MOC :
- [[Validation of CSRF token depends on request method]]
- [[Validation of CSRF token depends on token being present]]
- [[CSRF token is not tied to the user session]]
- [[CSRF token is tied to a non-session cookie]]
- [[CSRF token is simply duplicated in a cookie]]
- [[Referer-based defenses against CSRF]]