Parent Links : [[Cross-site scripting]] > [[How to prevent XSS attacks]]     

## How to prevent XSS client-side in JavaScript

To escape user input in an HTML context in JavaScript, you need your own HTML encoder because JavaScript doesn't provide an API to encode HTML. Here is some example JavaScript code that converts a string to HTML entities:  

```js
function htmlEncode(str){  
               return String(str).replace(/[^\w. ]/gi, function(c){  
                  return '&#'+c.charCodeAt(0)+';';  
               });  
             }

```  

You would then use this function as follows:  
```html
<script>document.body.innerHTML = htmlEncode(untrustedValue)</script>         
```

  
If your input is inside a JavaScript string, you need an encoder that performs Unicode escaping. Here is a sample Unicode-encoder:  
```js
function jsEscape(str){  
               return String(str).replace(/[^\w. ]/gi, function(c){  
                  return '\\u'+('0000'+c.charCodeAt(0).toString(16)).slice(-4);  
               });  
           
                     }
```
  
You would then use this function as follows:  
```js
<script>document.write('<script>x="'+jsEscape(untrustedValue)+'";<\/script>')</script>
```