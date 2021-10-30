Parent Links : [[Cross-site scripting]] > [[Content security policy]]     

## Protecting against [clickjacking](https://portswigger.net/web-security/clickjacking) using CSP
  
The following directive will only allow the page to be framed by other pages from the same origin:  
`frame-ancestors 'self'`  
The following directive will prevent framing altogether:  
`frame-ancestors 'none'  
`  
Using content security policy to prevent clickjacking is more flexible than using the X-Frame-Options header because you can specify multiple domains and use wildcards.  
  
For example:  
`frame-ancestors 'self' https://normal-website.com https://*.robust-website.com  
`  
CSP also validates each frame in the parent frame hierarchy, whereas `X-Frame-Options` only validates the top-level frame.  
Using CSP to protect against clickjacking attacks is recommended. You can also combine this with the `X-Frame-Options` header to provide protection on older browsers that don't support CSP, such as Internet Explorer.