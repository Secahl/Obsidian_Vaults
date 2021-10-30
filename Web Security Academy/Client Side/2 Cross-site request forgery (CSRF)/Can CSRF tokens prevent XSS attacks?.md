Parent Links : [[Cross-site request forgery (CSRF)]] > [[How to deliver a CSRF exploit]]     

## Can [CSRF tokens](https://portswigger.net/web-security/csrf/tokens) prevent XSS attacks?
  
Some XSS attacks can indeed be prevented through effective use of CSRF tokens. 

Consider a simple [reflected XSS](https://portswigger.net/web-security/cross-site-scripting/reflected) vulnerability that can be trivially exploited like this:  
>`https://insecure-website.com/status?message=<script>/*+Bad+stuff+here...+*/</script>`  
>
Now, suppose that the vulnerable function includes a CSRF token:  
>`https://insecure-website.com/status?csrf-token=CIwNZNlR4XbisJF39I8yWnWX9wX4WFoz&message=<script>/*+Bad+stuff+here...+*/</script>`  
  
Assuming that the server properly validates the CSRF token, and rejects requests without a valid token, then the token does prevent exploitation of the XSS vulnerability. The clue here is in the name: "cross-site scripting", at least in its [[Reflected XSS | reflected]] form, involves a cross-site request. By preventing an attacker from forging a cross-site request, the application prevents trivial exploitation of the XSS vulnerability.  
  
  
Some important caveats arise here:  
  
>• If a [reflected XSS](https://portswigger.net/web-security/cross-site-scripting/reflected) vulnerability exists anywhere else on the site within a function that is not protected by a CSRF token, then that XSS can be exploited in the normal way.  
>  
>• If an exploitable XSS vulnerability exists anywhere on a site, then the vulnerability can be leveraged to make a victim user perform actions even if those actions are themselves protected by CSRF tokens. In this situation, the attacker's script can request the relevant page to obtain a valid CSRF token, and then use the token to perform the protected action.  
>  
>• CSRF tokens do not protect against [[Stored XSS]] vulnerabilities. If a page that is protected by a CSRF token is also the output point for a [stored XSS](https://portswigger.net/web-security/cross-site-scripting/stored) vulnerability, then that XSS vulnerability can be exploited in the usual way, and the XSS payload will execute when a user visits the page.