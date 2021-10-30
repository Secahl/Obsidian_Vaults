Parent Links : [[Cross-site scripting]] > [[How to find and test for XSS vulnerabilities]] > [[Cross-site scripting contexts]] > [[XSS into JavaScript]]     

## XSS in the context of the AngularJS sandbox
  
Sometimes, XSS vulnerabilities arise in the context of the AngularJS sandbox. This presents additional barriers to exploitation, which can often be circumvented with sufficient ingenuity.  
  
  

### AngularJS sandbox

  
  
In this section, we'll describe the AngularJS sandbox, explain how exploits can escape from the sandbox, and spell out how [content security policy CSP](https://portswigger.net/web-security/cross-site-scripting/content-security-policy)  can be bypassed in the context of the AngularJS sandbox.  
  
  

#### What is the AngularJS sandbox?

  
  
The AngularJS sandbox is a mechanism that prevents access to potentially dangerous objects, such as `window` or `document`, in AngularJS template expressions. It also prevents access to potentially dangerous properties, such as `__proto__`. Despite not being considered a security boundary by the AngularJS team, the wider developer community generally thinks otherwise. Although bypassing the sandbox was initially challenging, security researchers have discovered numerous ways of doing so.  
As a result, it was eventually removed from AngularJS in version 1.6. However, many legacy applications still use older versions of AngularJS and may be vulnerable as a result.  
  
  

#### How does the AngularJS sandbox work?

  
  
The sandbox works by parsing an expression, rewriting the JavaScript, and then using various functions to test whether the rewritten code contains any dangerous objects. For example, the `ensureSafeObject()` function checks whether a given object references itself. This is one way to detect the `window` object, for example. The `Function` constructor is detected in roughly the same way, by checking whether the constructor property references itself.  
  
The `ensureSafeMemberName()` function checks each property access of the object and, if it contains dangerous properties such as `__proto__` or `__lookupGetter__`, the object will be blocked. The `ensureSafeFunction()`function prevents `call()`, `apply()`, `bind()`, or `constructor()` from being called.  
You can see the sandbox in action for yourself by visiting [this fiddle](http://jsfiddle.net/2zs2yv7o/1/) and setting a breakpoint at line 13275 of the `angular.js` file. The variable `fnString` contains your rewritten code, so you can look at how AngularJS transforms it.


#### MOC :
- [[How does an AngularJS sandbox escape work?]]
- [[Constructing an advanced AngularJS sandbox escape]]
- [[How does an AngularJS CSP bypass work?]]
- [[How to prevent AngularJS injection]]