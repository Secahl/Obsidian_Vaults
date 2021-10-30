Parent Links : [[Cross-site scripting]] > [[How to find and test for XSS vulnerabilities]] > [[Cross-site scripting contexts]] > [[XSS into JavaScript]] > [[XSS in the context of the AngularJS sandbox]] > [[How does an AngularJS CSP bypass work?]]    

### Bypassing a CSP with an AngularJS sandbox escape

This next lab employs a length restriction, so the above vector will not work. In order to exploit the lab, you need to think of various ways of hiding the `window` object from the AngularJS sandbox. One way of doing this is to use the `array.map()` function as follows:  
`[1].map(alert)`  
`map()` accepts a function as an argument and will call it for each item in the array. This will bypass the sandbox because the reference to the `alert()` function is being used without explicitly referencing the `window`. To solve the lab, try various ways of executing `alert()` without triggering AngularJS's `window` detection.  
  
  
>LAB [Reflected XSS with AngularJS sandbox escape and CSP](https://portswigger.net/web-security/cross-site-scripting/contexts/angularjs-sandbox/lab-angular-sandbox-escape-and-csp)