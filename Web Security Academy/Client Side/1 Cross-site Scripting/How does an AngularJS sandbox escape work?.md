Parent Links : [[Cross-site scripting]] > [[How to find and test for XSS vulnerabilities]] > [[Cross-site scripting contexts]] > [[XSS into JavaScript]] > [[XSS in the context of the AngularJS sandbox]] 

## How does an AngularJS sandbox escape work?

A sandbox escape involves tricking the sandbox into thinking the malicious expression is benign. The most well-known escape uses the modified `charAt()` function globally within an expression:  
  
`'a'.constructor.prototype.charAt=[].join`  
When it was initially discovered, AngularJS did not prevent this modification. The attack works by overwriting the function using the `[].join` method, which causes the `charAt()` function to return all the characters sent to it, rather than a specific single character. Due to the logic of the `isIdent()` function in AngularJS, it compares what it thinks is a single character against multiple characters. As single characters are always less than multiple characters, `the` `isIdent()` function always returns true, as demonstrated by the following example:  
```js 
isIdent= function(ch) {  
return ('a' <= ch && ch <= 'z' ||  
'A' <= ch && ch <= 'Z' ||  
'_' === ch || ch === '$');  
}  
isIdent('x9=9a9l9e9r9t9(919)')
```


Once the `isIdent()` function is fooled, you can inject malicious JavaScript. For example, an expression such as `$eval('x=alert(1)')` would be allowed because AngularJS treats every character as an identifier. Note that we need to use AngularJS's `$eval()` function because overwriting the `charAt()` function will only take effect once the sandboxed code is executed. This technique would then bypass the sandbox and allow arbitrary JavaScript execution.