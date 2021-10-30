Parent Links : [[Cross-site scripting]] > [[What are the types of XSS attacks?]] > [[Stored XSS]]

## Impact of stored XSS attacks
  
If an attacker can control a script that is executed in the victim's browser, then they can typically fully compromise that user. The attacker can carry out any of the actions that are applicable to the [[Impact of reflected XSS attacks#Impact of reflected XSS attacks | Impact of reflected XSS attacks]]
  
In terms of exploitability, the key difference between reflected and stored XSS is that a stored XSS vulnerability enables attacks that are self-contained within the application itself. The attacker does not need to find an external way of inducing other users to make a particular request containing their exploit. Rather, the attacker places their exploit into the application itself and simply waits for users to encounter it.  
  
The self-contained nature of stored cross-site scripting exploits is particularly relevant in situations where an XSS vulnerability only affects users who are currently logged in to the application. If the XSS is reflected, then the attack must be fortuitously timed: a user who is induced to make the attacker's request at a time when they are not logged in will not be compromised.  
  
In contrast, if the XSS is stored, then the user is guaranteed to be logged in at the time they encounter the exploit.  
  
  

### Read more

  
[Exploiting cross-site scripting vulnerabilities](https://portswigger.net/web-security/cross-site-scripting/exploiting)