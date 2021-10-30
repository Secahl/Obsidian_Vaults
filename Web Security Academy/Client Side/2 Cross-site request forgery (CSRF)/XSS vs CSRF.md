Parent Links : [[Cross-site request forgery (CSRF)]] > [[How to deliver a CSRF exploit]]     

## What is the difference between XSS and CSRF?
  
[[Cross-site scripting]] (or XSS) allows an attacker to execute arbitrary JavaScript within the browser of a victim user.  
[Cross-site request forgery](https://portswigger.net/web-security/csrf) (or CSRF) allows an attacker to induce a victim user to perform actions that they do not intend to.  
  
The consequences of XSS vulnerabilities are generally more serious than for CSRF vulnerabilities :  
  
>• CSRF often only applies to a subset of actions that a user is able to perform. Many applications implement CSRF defenses in general but overlook one or two actions that are left exposed. Conversely, a successful XSS exploit can normally induce a user to perform any action that the user is able to perform, regardless of the functionality in which the vulnerability arises.  
>  
>• CSRF can be described as a "one-way" vulnerability, in that while an attacker can induce the victim to issue an HTTP request, they cannot retrieve the response from that request. Conversely, XSS is "two-way", in that the attacker's injected script can issue arbitrary requests, read the responses, and exfiltrate data to an external domain of the attacker's choosing.