 Parent Links : [[Cross-site scripting]]    

## How to find and test for XSS vulnerabilities

The vast majority of XSS vulnerabilities can be found quickly and reliably using Burp Suite's [web vulnerability scanner](https://portswigger.net/burp/vulnerability-scanner).  
Manually testing for reflected and stored XSS normally involves submitting some simple unique input (such as a short alphanumeric string) into every entry point in the application, identifying every location where the submitted input is returned in HTTP responses, and testing each location individually to determine whether suitably crafted input can be used to execute arbitrary JavaScript. In this way, you can determine the [context](https://portswigger.net/web-security/cross-site-scripting/contexts) in which the XSS occurs and select a suitable payload to exploit it.  
  
Manually testing for DOM-based XSS arising from URL parameters involves a similar process: placing some simple unique input in the parameter, using the browser's developer tools to search the DOM for this input, and testing each location to determine whether it is exploitable.  
  
However, other types of DOM XSS are harder to detect. _To find_ [[DOM-based XSS]]_in_ _non-URL-based input_ _(such as_ _`document.cookie`__) or_ _non-HTML-based sinks_ _(like_ _`setTimeout`__),_ _**there is no substitute for reviewing JavaScript code, which can be extremely time-consuming.**_  

`Burp Suite's web vulnerability scanner combines static and dynamic analysis of JavaScript to reliably automate the detection of DOM-based vulnerabilities.`  
  

#### MOC :
[[Cross-site scripting contexts]]