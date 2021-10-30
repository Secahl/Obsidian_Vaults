Parent Links : [[Cross-site scripting]] > [[How to find and test for XSS vulnerabilities]] > [[Cross-site scripting contexts]] > [[XSS into JavaScript]]     

### XSS in JavaScript template literals
  
JavaScript template literals are string literals that allow embedded JavaScript expressions. The embedded expressions are evaluated and are normally concatenated into the surrounding text. Template literals are encapsulated in backticks instead of normal quotation marks, and embedded expressions are identified using the `${...}` syntax.  
  
For example, the following script will print a welcome message that includes the user's display name:  
```js 
document.getElementById('message').innerText = `Welcome, ${user.displayName}.`;
```  

When the XSS context is into a JavaScript template literal, there is no need to terminate the literal. Instead, you simply need to use the _`${...}`_ _syntax to embed a JavaScript expression that will be executed when the literal is processed._  
  
For example, if the XSS context is as follows:  
```js 
<script>  
...  
var input = `controllable data here`;  
...  
</script>
```  

then you can use the following payload to execute JavaScript without terminating the template literal:  
`${alert(document.domain)}`  

>LAB [Reflected XSS into a template literal with angle brackets, single, double quotes, backslash and backticks Unicode-escaped](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-javascript-template-literal-angle-brackets-single-double-quotes-backslash-backticks-escaped)