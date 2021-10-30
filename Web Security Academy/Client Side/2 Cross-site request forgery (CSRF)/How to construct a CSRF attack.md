Parent Links : [[Cross-site request forgery (CSRF)]]     

## How to construct a CSRF attack
  
Manually creating the HTML needed for a CSRF exploit can be cumbersome, particularly where the desired request contains a large number of parameters, or there are other quirks in the request.  
  
The easiest way to construct a CSRF exploit is using the [CSRF PoC generator](https://portswigger.net/burp/documentation/desktop/functions/generate-csrf-poc) that is built in to [Burp Suite Professional](https://portswigger.net/burp/pro) :  
  
>• Select a request anywhere in Burp Suite Professional that you want to test or exploit.  
• From the right-click context menu, select Engagement tools / Generate CSRF PoC.  
• Burp Suite will generate some HTML that will trigger the selected request (minus cookies, which will be added automatically by the victim's browser).  
• You can tweak various options in the CSRF PoC generator to fine-tune aspects of the attack. You might need to do this in some unusual situations to deal with quirky features of requests.  
• Copy the generated HTML into a web page, view it in a browser that is logged in to the vulnerable web site, and test whether the intended request is issued successfully and the desired action occurs.  
  
  
>LAB [CSRF vulnerability with no defenses](https://portswigger.net/web-security/csrf/lab-no-defenses)