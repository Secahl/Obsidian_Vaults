Parent Links : [[Cross-site scripting]] > [[How to find and test for XSS vulnerabilities]] > [[Cross-site scripting contexts]] > [[XSS into JavaScript]] > [[XSS in the context of the AngularJS sandbox]]     

### Constructing an advanced AngularJS sandbox escape
  
So you've learned how a basic sandbox escape works, but you may encounter sites that are more restrictive with which characters they allow. For example, a site may prevent you from using double or single quotes. In this situation, you need to use functions such as `String.fromCharCode()` to generate your characters. Although AngularJS prevents access to the `String` constructor within an expression, you can get round this by using the constructor property of a string instead. This obviously requires a string, so to construct an attack like this, you would need to find a way of creating a string without using single or double quotes.  
In a standard sandbox escape, you would use `$eval()` to execute your JavaScript payload, but in the lab below, the `$eval()` function is undefined. Fortunately, we can use the `orderBy` filter instead. The typical syntax of an `orderBy` filter is as follows:  
`[123]|orderBy:'Some string'`  
Note that the `|` operator has a different meaning than in JavaScript. Normally, this is a bitwise `OR` operation, but in AngularJS it indicates a filter operation. In the code above, we are sending the array `[123]` on the left to the `orderBy` filter on the right. The colon signifies an argument to send to the filter, which in this case is a string. The `orderBy` filter is normally used to sort an object, but it also accepts an expression, which means we can use it to pass a payload.  
You should now have all the tools you need to tackle the next lab.  
  
  
>LAB [Reflected XSS with AngularJS sandbox escape without strings](https://portswigger.net/web-security/cross-site-scripting/contexts/angularjs-sandbox/lab-angular-sandbox-escape-without-strings)  
  
>Note : Javascript Charcode Translator will help to translate characters(i.e. string) to integers if string is not allowed.