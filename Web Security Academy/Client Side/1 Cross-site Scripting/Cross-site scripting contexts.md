Parent Links : [[Cross-site scripting]] > [[How to find and test for XSS vulnerabilities]]  

# Cross-site scripting contexts
  
When testing for [[Reflected XSS in different contexts| reflected]] and [[Stored XSS in different contexts | stored]], a key task is to identify the XSS context:  
  
	• The location within the response where attacker-controllable data appears.  
	• Any input validation or other processing that is being performed on that data by the application.  
  
Based on these details, you can then select one or more candidate XSS payloads, and test whether they are effective.  
  
  

#### Note
  
We have built a comprehensive [XSS cheat sheet](https://portswigger.net/web-security/cross-site-scripting/cheat-sheet) to help testing web applications and filters. You can filter by events and tags and see which vectors require user interaction. The cheat sheet also contains AngularJS sandbox escapes and many other sections to help with XSS research.  
  
  
 #### MOC :

- [[XSS between HTML tags]]

- [[XSS in HTML tag attributes]]

- [[XSS into JavaScript]]