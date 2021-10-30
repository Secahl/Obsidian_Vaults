   Parent Links : [[Cross-site scripting]] > [[What are the types of XSS attacks?]] > [[DOM-based XSS]]

## How to test for DOM-based cross-site scripting
  
The majority of DOM XSS vulnerabilities can be found quickly and reliably using Burp Suite's [web vulnerability scanner](https://portswigger.net/burp/vulnerability-scanner).  
To test for DOM-based cross-site scripting manually, you generally need to use a browser with developer tools, such as Chrome. You need to work through each available source in turn, and test each one individually.

### MOC :
- [[Testing HTML sinks]]
- [[Testing JavaScript execution sinks]]