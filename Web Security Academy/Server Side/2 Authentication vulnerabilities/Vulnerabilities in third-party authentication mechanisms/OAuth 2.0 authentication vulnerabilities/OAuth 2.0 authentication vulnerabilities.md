# OAuth 2.0 authentication vulnerabilities

While browsing the web, you've almost certainly come across sites that let you log in using your social media account  
. The chances are that this feature is built using the popular **OAuth 2.0 framework**.  
  
_OAuth 2.0 is highly interesting for attackers because it is both extremely common and inherently prone to implementation mistakes._  
This can result in a number of vulnerabilities, allowing attackers to obtain sensitive user data and potentially bypass authentication completely.  
  
In this section, we'll teach you how to identify and exploit some of the key [vulnerabilities found in OAuth 2.0 authentication](https://portswigger.net/web-security/oauth#exploiting-oauth-authentication-vulnerabilities) mechanisms. Don't worry if you're not too familiar with OAuth authentication - we've provided plenty of background information to help you understand the key concepts you'll need.  
  
_We'll also explore some_ [vulnerabilities in OAuth's OpenID Connect extension](https://portswigger.net/web-security/oauth/openid#openid-connect-vulnerabilities)_._  
  
  
Finally, we've included some guidance on how to [protect your own applications](https://portswigger.net/web-security/oauth/preventing) against these kinds of attacks.  
[![file:///tmp/.N6XWB1/1.png](file:///tmp/.N6XWB1/1.png)](https://portswigger.net/web-security/images/oauth.jpg)  
  
As usual, we've provided a series of deliberately vulnerable websites, known as "labs", so that you can see these vulnerabilities in practice and put what you've learned about exploiting them to the test. If you'd prefer to dive straight into the labs, you can access the full list from our labs index page.  
  
  

### Labs

>[OAuth authentication labs](https://portswigger.net/web-security/all-labs#oauth-authentication)

<br>

Linked Nodes :

[[What is OAuth?]]
[[How does OAuth 2.0 work?]]