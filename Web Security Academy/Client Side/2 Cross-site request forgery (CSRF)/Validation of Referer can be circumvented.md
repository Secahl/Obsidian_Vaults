Parent Links : [[Cross-site request forgery (CSRF)]] > [[Common CSRF vulnerabilities]] > [[Referer-based defenses against CSRF]]     

### Validation of Referer can be circumvented
  
Some applications validate the [[Referer-based defenses against CSRF#Referer header | Referer header]] in a naive way that can be bypassed. 
For example, if the application validates that the domain in the `Referer` starts with the expected value, then the attacker can place this as a subdomain of their own domain:`http://vulnerable-website.com.attacker-website.com/csrf-attack` 

Likewise, if the application simply validates that the `Referer` contains its own domain name, then the attacker can place the required value elsewhere in the URL:`http://attacker-website.com/csrf-attack?vulnerable-website.com`  
  

>##### Note
>
Although you may be able to identify this behavior using Burp, you will often find that this approach no longer works when you go to test your proof-of-concept in a browser. In an attempt to reduce the risk of sensitive data being leaked in this way, many browsers now strip the query string from the `Referer` header by default.  
You can override this behavior by making sure that the response containing your exploit has the `Referrer-Policy: unsafe-url` header set (note that `Referrer` is spelled correctly in this case, just to make sure you're paying attention!). This ensures that the full URL will be sent, including the query string.  
  
>LAB [CSRF with broken Referer validation](https://portswigger.net/web-security/csrf/lab-referer-validation-broken)