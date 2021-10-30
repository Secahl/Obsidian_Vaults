Parent Links : [[Cross-site scripting]] > [[What are the types of XSS attacks?]] > [[Reflected XSS]]

## Common questions about reflected cross-site scripting

**What is the difference between reflected XSS and** [stored XSS](https://portswigger.net/web-security/cross-site-scripting/stored)**?**  
  
Reflected XSS arises when an application takes some input from an HTTP request and embeds that input into the immediate response in an unsafe way. With stored XSS, the application instead stores the input and embeds it into a later response in an unsafe way.  
  
  
**What is the difference between reflected XSS and self-XSS?**  
  
Self-XSS involves similar application behavior to regular reflected XSS, however it cannot be triggered in normal ways via a crafted URL or a cross-domain request. Instead, the vulnerability is only triggered if the victim themselves submits the XSS payload from their browser. Delivering a self-XSS attack normally involves socially engineering the victim to paste some attacker-supplied input into their browser. As such, it is normally considered to be a lame, low-impact issue.