Parent Links : [[ClientSide]]     

## What is CSRF?
  
  
Cross-site request forgery (also known as CSRF) is a web security vulnerability that allows an attacker to induce users to perform actions that they do not intend to perform. It allows an attacker to partly circumvent the same origin policy, which is designed to prevent different websites from interfering with each other.  
[![file:///tmp/.IDPXB1/1.png](file:///tmp/.IDPXB1/1.png)](https://portswigger.net/web-security/images/cross-site%20request%20forgery.svg)  
  
  

### What is the impact of a CSRF attack?

  
In a successful CSRF attack, the attacker causes the victim user to carry out an action unintentionally. For example, this might be to change the email address on their account, to change their password, or to make a funds transfer. Depending on the nature of the action, the attacker might be able to gain full control over the user's account. If the compromised user has a privileged role within the application, then the attacker might be able to take full control of all the application's data and functionality.


#### MOC :
- [[How does CSRF work?]]
- [[How to construct a CSRF attack]]
- [[How to deliver a CSRF exploit]]
- [[Preventing CSRF attacks]]
- [[Common CSRF vulnerabilities]]