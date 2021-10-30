 ## What is authentication?

Authentication is the process of verifying the identity of a given user or client.  
  
There are three authentication factors:  
  
• Something you **know**, sometimes referred to as _"knowledge factors"._  
• Something you **have**, sometimes referred to as _"possession factors"._  
• Something you **are** or **do**, sometimes referred to as _"inherence factors"._  
 
### What is the difference between authentication and authorization?

Authentication is the process of verifying that a user really **is who they claim to be**, whereas authorization involves verifying whether a user **is allowed to do something**.  
  
**In the context of a website or web application**,  
authentication determines whether someone attempting to access the site with the username `Carlos123` really _is the same person who created the account._ 

Once `Carlos123` is authenticated, his permissions determine whether or not he is authorized, for example, to access personal information about other users or _perform actions such as deleting another user's account._  
  
## How do authentication vulnerabilities arise?

Broadly speaking, most vulnerabilities in authentication mechanisms arise in one of two ways:  
  
• The authentication mechanisms are weak because they fail to adequately protect against brute-force attacks.  
• Logic flaws or poor coding in the implementation allow the authentication mechanisms to be bypassed entirely by an attacker. This is sometimes referred to as _"broken authentication"._  
  
In many areas of web development, [logic flaws](https://portswigger.net/web-security/logic-flaws) will simply cause the website to behave unexpectedly, which may or may not be a security issue. However, as authentication is so critical to security, the likelihood that flawed authentication logic exposes the website to security issues is clearly elevated

Linked Nodes:
[[Vulnerabilities in authentication mechanisms]]
[[OAuth 2.0 authentication vulnerabilities]]