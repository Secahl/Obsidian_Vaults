Parent Links : [[Cross-site request forgery (CSRF)]] > [[Common CSRF vulnerabilities]]     

### CSRF token is not tied to the user session
  
Some applications do not validate that the token belongs to the same session as the user who is making the request. Instead, the application maintains a global pool of tokens that it has issued and accepts any token that appears in this pool.  
In this situation, the attacker can log in to the application using their own account, obtain a valid token, and then feed that token to the victim user in their CSRF attack.  
  
  
>LAB [CSRF where token is not tied to user session](https://portswigger.net/web-security/csrf/lab-token-not-tied-to-user-session)