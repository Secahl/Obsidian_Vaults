Parent Links : [[Cross-site scripting]] > [[What are the types of XSS attacks?]] > [[Reflected XSS]]

## Impact of reflected XSS attacks

If an attacker can control a script that is executed in the victim's browser, then they can typically fully compromise that user.  
  
Amongst other things, the attacker can:  
• Perform any action within the application that the user can perform.  
• View any information that the user is able to view.  
• Modify any information that the user is able to modify.  
• Initiate interactions with other application users, including malicious attacks, that will appear to originate from the initial victim user.  
  
There are various means by which an attacker might induce a victim user to make a request that they control, to deliver a reflected XSS attack. These include placing links on a website controlled by the attacker, or on another website that allows content to be generated, or by sending a link in an email, tweet or other message.  
The attack could be targeted directly against a known user, or could an indiscriminate attack against any users of the application:  
The need for an external delivery mechanism for the attack means that the impact of reflected XSS is generally less severe than [stored XSS](https://portswigger.net/web-security/cross-site-scripting/stored), where a self-contained attack can be delivered within the vulnerable application itself.  
  
  

### Read more
  
[Exploiting cross-site scripting vulnerabilities](https://portswigger.net/web-security/cross-site-scripting/exploiting)