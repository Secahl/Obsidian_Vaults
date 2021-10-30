Parent Links : [[Cross-site scripting]] > [[What are the types of XSS attacks?]]

# DOM-based XSS

## What is DOM-based cross-site scripting?

DOM-based XSS (also known as DOM XSS arises when an application contains some client-side JavaScript that processes data from an untrusted source in an unsafe way, usually by writing the data back to the DOM.  
  
DOM-based XSS vulnerabilities usually arise when JavaScript takes data from an attacker-controllable source, such as the URL, and passes it to _a sink that supports dynamic code execution_, such as `eval()` or `innerHTML`. This enables attackers to execute malicious JavaScript, which typically allows them to hijack other users' accounts.  
  
To deliver a DOM-based XSS attack, you need to place data into a source so that it is propagated to a sink and causes execution of arbitrary JavaScript.  
  
The most common source for DOM XSS is the URL, which is typically accessed with the `window.location` object. An attacker can construct a link to send a victim to a vulnerable page with a payload in the query string and fragment portions of the URL. In certain circumstances, such as when targeting a 404 page or a website running PHP, the payload can also be placed in the path.  
  
For a detailed explanation of the taint flow between sources and sinks, please refer to the [DOM-based vulnerabilities](https://portswigger.net/web-security/dom-based) page.  
  
In the following example, an application uses some JavaScript to read the value from an input field and write that value to an element within the HTML:  
```js 
var search = document.getElementById('search').value;  
var results = document.getElementById('results');  
results.innerHTML = 'You searched for: ' + search;
```
  
If the attacker can control the value of the input field, they can easily construct a malicious value that causes their own script to execute:  
`You searched for:` 
```html 
<img src=1 onerror='/* Bad stuff here... */'>
``` 
  
In a typical case, the input field would be populated from part of the HTTP request, such as a URL query string parameter, allowing the attacker to deliver an attack using a malicious URL, in the same manner as reflected XSS.


## DOM-based XSS MOC :
- [[How to test for DOM-based cross-site scripting]]
- [[Exploiting DOM XSS with different sources and sinks]]
- [[DOM XSS combined with reflected and stored data]]
- [[Which sinks can lead to DOM-XSS vulnerabilities?]]
- [[How to prevent DOM-XSS vulnerabilities]]