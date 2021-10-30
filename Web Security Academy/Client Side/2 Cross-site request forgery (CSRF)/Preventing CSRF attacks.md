Parent Links : [[Cross-site request forgery (CSRF)]] 

## Preventing CSRF attacks
  
The most robust way to defend against CSRF attacks is to include a [CSRF token](https://portswigger.net/web-security/csrf/tokens) within relevant requests.  

>The token should be:  
>  
>• Unpredictable with high entropy, as for session tokens in general.  
• Tied to the user's session.  
• Strictly validated in every case before the relevant action is executed.  
  
  

>##### Read more :
>  
>- [CSRF tokens](https://portswigger.net/web-security/csrf/tokens)  
>- [Find CSRF vulnerabilities using Burp Suite's web vulnerability scanner](https://portswigger.net/burp/vulnerability-scanner)  
  
  
An additional defense that is partially effective against CSRF, and can be used in conjunction with [CSRF tokens](https://portswigger.net/web-security/csrf/tokens), is [SameSite cookies](https://portswigger.net/web-security/csrf/samesite-cookies).

#### MOC :
- [[CSRF tokens]]