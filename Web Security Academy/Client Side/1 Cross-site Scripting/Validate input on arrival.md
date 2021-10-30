Parent Links : [[Cross-site scripting]] > [[How to prevent XSS attacks]]     

## Validate input on arrival

Encoding is probably the most important line of XSS defense, but it is not sufficient to prevent XSS vulnerabilities in every context. You should also validate input as strictly as possible at the point when it is first received from a user.  
  
Examples of input validation include:  
  
	• If a user submits a URL that will be returned in responses, validating that it starts with a safe protocol such as HTTP and HTTPS. Otherwise someone might exploit your site with a harmful protocol like `javascript` or `data`.  

	• If a user supplies a value that it expected to be numeric, validating that the value actually contains an integer.  

	• Validating that input contains only an expected set of characters.  
  
  
  
Input validation should ideally work by blocking invalid input. An alternative approach, of attempting to clean invalid input to make it valid, is more error prone and should be avoided wherever possible.


#### MOC :
- [[Whitelisting vs blacklisting]]
- [[Allowing "safe" HTML]]