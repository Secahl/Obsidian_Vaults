Parent Links : [[Cross-site scripting]] > [[How to find and test for XSS vulnerabilities]] > [[Cross-site scripting contexts]]     

## XSS between HTML tags
  
When the XSS context is text between HTML tags, you need to introduce some new HTML tags designed to trigger execution of JavaScript.  
  
Some useful ways of executing JavaScript are:  
  
```js 
<script>alert(document.domain)</script>  
<img src=1 onerror=alert(1)>  
```


>- LAB [Reflected XSS into HTML context with nothing encoded](https://portswigger.net/web-security/cross-site-scripting/reflected/lab-html-context-nothing-encoded)  
>- LAB [Stored XSS into HTML context with nothing encoded](https://portswigger.net/web-security/cross-site-scripting/stored/lab-html-context-nothing-encoded)  
>- LAB [Reflected XSS into HTML context with most tags and attributes blocked](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-html-context-with-most-tags-and-attributes-blocked)  
>- LAB [Reflected XSS into HTML context with all tags blocked except custom ones](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-html-context-with-all-standard-tags-blocked)  
>- LAB [Reflected XSS with event handlers and](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-event-handlers-and-href-attributes-blocked) [href](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-event-handlers-and-href-attributes-blocked) [attributes blocked](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-event-handlers-and-href-attributes-blocked)  
>- LAB [Reflected XSS with some SVG markup allowed](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-some-svg-markup-allowed)