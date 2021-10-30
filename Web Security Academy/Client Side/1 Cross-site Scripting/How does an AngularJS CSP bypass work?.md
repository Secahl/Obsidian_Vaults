Parent Links : [[Cross-site scripting]] > [[How to find and test for XSS vulnerabilities]] > [[Cross-site scripting contexts]] > [[XSS into JavaScript]] > [[XSS in the context of the AngularJS sandbox]]     

## How does an AngularJS CSP bypass work?

Content security policy (CSP) bypasses work in a similar way to standard sandbox escapes, but usually involve some HTML injection. When the CSP mode is active in AngularJS, it parses template expressions differently and avoids using the `Function` constructor. This means the standard sandbox escape described above will no longer work.  
  
Depending on the specific policy, the CSP will block JavaScript events. However, AngularJS defines its own events that can be used instead. When inside an event, AngularJS defines a special `$event` object, which simply references the browser event object. You can use this object to perform a CSP bypass.  
On Chrome, there is a special property on the `$event/event` object called `path`. This property contains an array of objects that causes the event to be executed. The last property is always the `window` object, which we can use to perform a sandbox escape. By passing this array to the `orderBy` filter, we can enumerate the array and use the last element (the `window` object) to execute a global function, such as `alert()`.  
  
The following code demonstrates this:  
```js 
<input autofocus ng-focus="$event.path|orderBy:'[].constructor.from([1],alert)'">
```

Notice that the `from()` function is used, which allows you to convert an object to an array and call a given function (specified in the second argument) on every element of that array. In this case, we are calling the `alert()` function. We cannot call the function directly because the AngularJS sandbox would parse the code and detect that the `window` object is being used to call a function. Using the `from()` function instead effectively hides the `window` object from the sandbox, allowing us to inject malicious code.


#### MOC :
- [[Bypassing a CSP with an AngularJS sandbox escape]]