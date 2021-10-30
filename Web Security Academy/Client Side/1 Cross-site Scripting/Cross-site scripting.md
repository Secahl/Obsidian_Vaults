Parent Link : [[ClientSide]]

# Cross-site scripting


### What is cross-site scripting (XSS)?

    Cross-site scripting (also known as XSS) is a web security vulnerability that allows an attacker to compromise the interactions that users have with a vulnerable application.  
_It allows an attacker to circumvent the same origin policy, which is designed to segregate different websites from each other._  
Cross-site scripting vulnerabilities normally allow an attacker to masquerade as a victim user, to carry out any actions that the user is able to perform, and to access any of the user's data. If the victim user has privileged access within the application, then the attacker might be able to gain full control over all of the application's functionality and data.

   

### How does XSS work ?
  
Cross-site scripting works by manipulating a vulnerable web site so that it returns malicious JavaScript to users. When the malicious code executes inside a victim's browser, the attacker can fully compromise their interaction with the application.  
  
[![file:///tmp/.7DC6B1/1.png](file:///tmp/.7DC6B1/1.png)](https://portswigger.net/web-security/images/cross-site-scripting.svg)

   

### XSS proof of concept 

You can confirm most kinds of XSS vulnerability by injecting a payload that causes your own browser to execute some arbitrary JavaScript. It's long been common practice to use the `alert()` function for this purpose because it's short, harmless, and pretty hard to miss when it's successfully called.  
In fact, you solve the majority of our XSS labs by invoking `alert()` in a simulated victim's browser.  
  
_Unfortunately, there's a slight hitch if you use Chrome. From version 92 onward (July 20th, 2021), cross-origin iframes are prevented from calling_ _`alert()`__._ As these are used to construct some of the more advanced XSS attacks, you'll sometimes need to use an alternative PoC payload.  
In this scenario, we recommend the `print()` function. If you're interested in learning more about this change and why we like `print()`, [check out our blog post](https://portswigger.net/research/alert-is-dead-long-live-print) on the subject.  
As the simulated victim in our labs uses Chrome, we've amended the affected labs so that they can also be solved using `print()`. We've indicated this in the instructions wherever relevant.


### Cross-site scripting MOC

- [[What are the types of XSS attacks?]]
- [[What can XSS be used for?]]
- [[Impact of XSS vulnerabilities]]
- [[How to find and test for XSS vulnerabilities]]
- [[Content security policy]]
- [[Dangling markup injection]]
- [[How to prevent XSS attacks]]
- [[Common questions about cross-site scripting]]