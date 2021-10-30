Parent Links : [[Cross-site scripting]]   

## Content security policy
  
Content security policy ([CSP](https://portswigger.net/web-security/cross-site-scripting/content-security-policy)) is a browser mechanism that aims to mitigate the impact of cross-site scripting and some other vulnerabilities. If an application that employs CSP contains XSS-like behavior, then the CSP might hinder or prevent exploitation of the vulnerability. Often, the CSP can be circumvented to enable exploitation of the underlying vulnerability.  
  
It works by restricting the resources (such as scripts and images) that a page can load and restricting whether a page can be framed by other pages.  
To enable CSP, a response needs to include an HTTP response header called `Content-Security-Policy` with a value containing the policy. The policy itself consists of one or more directives, separated by semicolons.  
  
  
In this section, we'll explain what content security policy is, and describe how CSP can be used to mitigate against some common attacks.

#### MOC :
- [[Mitigating XSS attacks using CSP]]
- [[Mitigating dangling markup attacks using CSP]]
- [[Bypassing CSP with policy injection]]
- [[Protecting against clickjacking using CSP]]