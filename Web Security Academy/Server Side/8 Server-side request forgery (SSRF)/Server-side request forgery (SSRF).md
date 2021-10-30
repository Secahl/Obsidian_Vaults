# Server-side request forgery (SSRF)

^95fe30

## What is SSRF?
  
Server-side request forgery (also known as SSRF) is a web security vulnerability that allows an attacker to induce the _server-side application to make HTTP requests to an arbitrary domain of the attacker's choosing_.  
  
In a typical SSRF attack, the attacker might cause the server to make a connection to internal-only services within the organization's infrastructure. In other cases, they may be able to force the server to connect to arbitrary external systems, potentially leaking sensitive data such as authorization credentials.  
  
  
[![file:///tmp/.35TLB1/1.png](file:///tmp/.35TLB1/1.png)](https://portswigger.net/web-security/images/server-side%20request%20forgery.svg)  
  

  <br><br>

## What is the impact of SSRF attacks?

A successful SSRF attack can often result in unauthorized actions or access to data within the organization, either in the vulnerable application itself or on other back-end systems that the application can communicate with.  
In some situations, the SSRF vulnerability might allow an attacker to perform arbitrary command execution.  
  
An SSRF exploit that causes connections to external third-party systems might result in malicious onward attacks that appear to originate from the organization hosting the vulnerable application.  


Linked Nodes :

[[Common SSRF attacks]]
[[Circumventing common SSRF defenses]]
[[Blind SSRF vulnerabilities]]
[[D > Finding hidden attack surface for SSRF vulnerabilities]]
  
