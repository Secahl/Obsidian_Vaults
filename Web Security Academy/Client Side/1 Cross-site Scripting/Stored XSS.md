Parent Links : [[Cross-site scripting]] > [[What are the types of XSS attacks?]]

# Stored cross-site scripting
  
Stored XSS (also known as persistent or second-order XSS) arises when an application receives data from an untrusted source and includes that data within its later HTTP responses in an unsafe way.  
  
The data in question might be submitted to the application via HTTP requests; for example, comments on a blog post, user nicknames in a chat room, or contact details on a customer order.  
In other cases, the data might arrive from other untrusted sources; for example, a webmail application displaying messages received over SMTP, a marketing application displaying social media posts, or a network monitoring application displaying packet data from network traffic.  
  
  
Suppose a website allows users to submit comments on blog posts, which are displayed to other users. Users submit comments using an HTTP request like the following:  
```http 
POST /post/comment HTTP/1.1  
Host: vulnerable-website.com  
Content-Length: 100``postId=3&comment=This+post+was+extremely+helpful
&name=Carlos+Montoya&email=carlos%40normal-user.net`  
```
 
After this comment has been submitted, any user who visits the blog post will receive the following within the application's response:  
>`This post was extremely helpful.`  
  
Assuming the application doesn't perform any other processing of the data, an attacker can submit a malicious comment like this:  
```js 
<script>/* Bad stuff here... */</script>
```  
  
Within the attacker's request, this comment would be URL-encoded as:  
```js 
comment=%3Cscript%3E%2F*%2BBad%2Bstuff%2Bhere...%2B*%2F%3C%2Fscript%3E
```
  
Any user who visits the blog post will now receive the following within the application's response:  
> `<p><script>/* Bad stuff here... */</script></p>`

  
The script supplied by the attacker will then execute in the victim user's browser, in the context of their session with the application.  
  
  
LAB [Stored XSS into HTML context with nothing encoded](https://portswigger.net/web-security/cross-site-scripting/stored/lab-html-context-nothing-encoded)  
    
  

##### Read more
  
[Cross-site scripting cheat sheet](https://portswigger.net/web-security/cross-site-scripting/cheat-sheet)


#### MOC :
- [[Impact of stored XSS attacks]]
- [[Stored XSS in different contexts]]
- [[How to find and test for stored XSS vulnerabilities]]