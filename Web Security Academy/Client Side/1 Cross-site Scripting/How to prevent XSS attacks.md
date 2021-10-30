Parent Links : [[Cross-site scripting]]     

## How to prevent XSS attacks

Preventing cross-site scripting is trivial in some cases but can be much harder depending on the complexity of the application and the ways it handles user-controllable data.  
  
In general, effectively preventing XSS vulnerabilities is likely to involve a combination of the following measures :  
>• **Filter input on arrival :** 
>At the point where user input is received, filter as strictly as possible based on what is expected or valid input.  
  
>• **Encode data on output :** 
>At the point where user-controllable data is output in HTTP responses, encode the output to prevent it from being interpreted as active content. Depending on the output context, this might require applying combinations of HTML, URL, JavaScript, and CSS encoding.  
  
>• **Use appropriate response headers :** 
>To prevent XSS in HTTP responses that aren't intended to contain any HTML or JavaScript, you can use the `Content-Type` and `X-Content-Type-Options` headers to ensure that browsers interpret the responses in the way you intend.  
  
>• **Content Security Policy :** 
>As a last line of defense, you can use Content Security Policy (CSP) to reduce the severity of any XSS vulnerabilities that still occur.  
  
  
In this section, we'll describe some general principles for preventing [cross-site scripting](https://portswigger.net/web-security/cross-site-scripting) vulnerabilities and ways of using various common technologies for protecting against [XSS](https://portswigger.net/web-security/cross-site-scripting) attacks.  

Cross-site scripting prevention can generally be achieved via two layers of defense:  
>• [Encode data on output](https://portswigger.net/web-security/cross-site-scripting/preventing#encode-data-on-output)  
• [Validate input on arrival](https://portswigger.net/web-security/cross-site-scripting/preventing#validate-input-on-arrival)  
  
You can use Burp Scanner to scan your web sites for numerous security vulnerabilities including XSS. Burp's cutting-edge scanning logic replicates the actions of a skilled attacker and is able to achieve correspondingly high coverage of XSS vulnerabilities. You can use Burp Scanner to gain assurance that your defenses against XSS attacks are working effectively.  
  
>Read: [Find XSS vulnerabilities using Burp Suite's web vulnerability scanner](https://portswigger.net/burp/vulnerability-scanner) 


#### MOC :
- [[Encode data on output]]
- [[Validate input on arrival]]
- [[How to prevent XSS using a template engine]]
- [[How to prevent XSS in PHP]]
- [[How to prevent XSS client-side in JavaScript]]
- [[How to prevent XSS in jQuery]]
- [[Mitigating XSS using content security policy (CSP)]]