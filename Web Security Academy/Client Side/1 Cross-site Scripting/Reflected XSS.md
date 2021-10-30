Parent Links : [[Cross-site scripting]] > [[What are the types of XSS attacks?]]

## What is reflected cross-site scripting?
  
Reflected cross-site scripting (or XSS) arises when an application receives data in an HTTP request and includes that data within the immediate response in an unsafe way.  
  
Suppose a website has a search function which receives the user-supplied search term in a URL parameter:  
`https://insecure-website.com/search?term=gift`  
The application echoes the supplied search term in the response to this URL:  
`<p>You searched for: gift</p>`  
Assuming the application doesn't perform any other processing of the data, an attacker can construct an attack like this:  
`https://insecure-website.com/search?term=<script>/*+Bad+stuff+here...+*/</script>`  
This URL results in the following response:  
`<p>You searched for: <script>/* Bad stuff here... */</script></p>`  
  
If another user of the application requests the attacker's URL, then the script supplied by the attacker will execute in the victim user's browser, in the context of their session with the application.  
  
  
LAB [Reflected XSS into HTML context with nothing encoded](https://portswigger.net/web-security/cross-site-scripting/reflected/lab-html-context-nothing-encoded)

#### MOC :
-   [[Impact of reflected XSS attacks]]
-   [[Reflected XSS in different contexts]]
-   [[How to find and test for reflected XSS vulnerabilities]]
-   [[Common questions about reflected cross-site scripting]]