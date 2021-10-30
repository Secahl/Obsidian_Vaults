Parent Links : [[Cross-site scripting]] > [[How to find and test for XSS vulnerabilities]] > [[Cross-site scripting contexts]] > [[XSS into JavaScript]]     

### Making use of HTML-encoding
  
When the XSS context is some existing JavaScript within a quoted tag attribute, such as an event handler, it is possible to make use of HTML-encoding to work around some input filters.  
When the browser has parsed out the HTML tags and attributes within a response, it will perform HTML-decoding of tag attribute values before they are processed any further. If the server-side application blocks or sanitizes certain characters that are needed for a successful XSS exploit, you can often bypass the input validation by HTML-encoding those characters.  
  
For example, if the XSS context is as follows:  
```js 
<a href="#" onclick="... var input='controllable data here'; ...">  
```  

and the application blocks or escapes single quote characters, you can use the following payload to break out of the JavaScript string and execute your own script:  
```js 
&apos;-alert(document.domain)-&apos;
```

The `&apos;` sequence is an HTML entity representing an apostrophe or single quote. Because _the browser HTML-decodes the value of the_ _`onclick`_ _attribute before the JavaScript is interpreted_, the entities are decoded as quotes, which become string delimiters, and so the attack succeeds.  
  
  
>LAB [Stored XSS into onclick event with angle brackets and double quotes HTML-encoded and single quotes and backslash escaped](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-onclick-event-angle-brackets-double-quotes-html-encoded-single-quotes-backslash-escaped)