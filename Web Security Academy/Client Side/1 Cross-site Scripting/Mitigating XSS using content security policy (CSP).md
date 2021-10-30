Parent Links : [[Cross-site scripting]] > [[How to prevent XSS attacks]]     

## Mitigating XSS using [content security policy](https://portswigger.net/web-security/cross-site-scripting/content-security-policy) (CSP)

  
  
  
Content security policy (CSP) is the last line of defense against cross-site scripting. If your XSS prevention fails, you can use CSP to mitigate XSS by restricting what an attacker can do.  
CSP lets you control various things, such as whether external scripts can be loaded and whether inline scripts will be executed. To deploy CSP you need to include an HTTP response header called `Content-Security-Policy` with a value containing your policy.  
  
An example CSP is as follows:  
- `default-src 'self';` 
- `script-src 'self';` 
- `object-src 'none';` 
- `frame-src 'none';` 
- `base-uri 'none';`  

This policy specifies that resources such as images and scripts can only be loaded from the same origin as the main page. So even if an attacker can successfully inject an XSS payload they can only load resources from the current origin. This greatly reduces the chance that an attacker can exploit the XSS vulnerability.  
If you require loading of external resources, ensure you only allow scripts that do not aid an attacker to exploit your site. For example, if you whitelist certain domains then an attacker can load any script from those domains. Where possible, try to host resources on your own domain.  
If that is not possible then you can use hash- or nonce-based policy to allow scripts on different domains. A nonce is a random string that is added as an attribute of a script or resource, which will only be executed if the random string matches the server-generated one. An attacker is unable to guess the randomized string and therefore cannot invoke a script or resource with a valid nonce and so the resource will not be executed.  
  

>##### Read more : [[Mitigating XSS attacks using CSP]]