Parent Links : [[Cross-site scripting]] > [[How to prevent XSS attacks]] 

## Encode data on output
  
Encoding should be applied directly before user-controllable data is written to a page, because the context you're writing into determines what kind of encoding you need to use. For example, values inside a JavaScript string require a different type of escaping to those in an HTML context.  
  
In an HTML context, you should convert non-whitelisted values into HTML entities:  
>• `<` converts to: `&lt;`  
▪ `>` converts to: `&gt;`  
  
In a JavaScript string context, non-alphanumeric values should be Unicode-escaped:  
>◇ `<` converts to: `\u003c`  
◇ `>` converts to: `\u003e`  
  
Sometimes you'll need to apply multiple layers of encoding, in the correct order.  
For example, to safely embed user input inside an event handler, you need to deal with both the JavaScript context and the HTML context.  
  
So you need to first Unicode-escape the input, and then HTML-encode it:  
```html
<a href="#" onclick="x='This string needs two layers of escaping'">test</a>
```