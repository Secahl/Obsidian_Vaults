## HTTP basic authentication

Although fairly old, its relative simplicity and ease of implementation means you might sometimes see HTTP basic authentication being used.  
  
>In HTTP basic authentication, _the client receives an authentication token from the server, which is constructed by concatenating the username and password, and encoding it in Base64_.  

This token is stored and managed by the browser, which automatically adds it to the `Authorization` header of every subsequent request as follows:  
`Authorization: Basic base64(username:password)`  
For a number of reasons, this is generally not considered a secure authentication method.  
  
Firstly, it involves repeatedly sending the user's login credentials with every request. Unless the website also implements HSTS, user credentials are open to being captured in a man-in-the-middle attack.  

In addition, implementations of **HTTP basic authentication often don't support brute-force protection**. As the token consists exclusively of static values, this can leave it vulnerable to being brute-forced.  

HTTP basic authentication is also particularly vulnerable to session-related exploits, notably [CSRF](https://portswigger.net/web-security/csrf), against which it offers no protection on its own.  
  
In some cases, exploiting vulnerable HTTP basic authentication might only grant an attacker access to a seemingly uninteresting page. However, in addition to providing a further attack surface, the credentials exposed in this way might be reused in other, more confidential contexts.