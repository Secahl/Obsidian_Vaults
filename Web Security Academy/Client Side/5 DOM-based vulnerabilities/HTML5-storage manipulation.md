Parent Links : [[DOM-based vulnerabilities]]

# DOM-based HTML5-storage manipulation

In this section, we'll look at HTML5-storage manipulation using the DOM, point out potentially dangerous sinks that can be used as part of this kind of attack, and suggest ways to reduce your exposure to HTML5-storage manipulation.

## What is DOM-based HTML5-storage manipulation?

HTML5-storage manipulation vulnerabilities arise when a script stores attacker-controllable data in the _**HTML5 storage of the web browser (either `localStorage` or `sessionStorage`)**_. An attacker may be able to use this behavior to construct a URL that, if visited by another user, will cause the user's browser to store attacker-controllable data.

This behavior does not in itself constitute a security vulnerability. However, if the application later reads data back from storage and processes it in an unsafe way, an attacker may be able to leverage the storage mechanism to deliver other DOM-based attacks, such as [cross-site scripting](https://portswigger.net/web-security/cross-site-scripting) and JavaScript injection.

## Which sinks can lead to DOM-based HTML5-storage manipulation vulnerabilities?

The following are some of the main sinks that can lead to DOM-based HTML5-storage manipulation vulnerabilities:

`sessionStorage.setItem()  
localStorage.setItem()`

## How to prevent DOM-based HTML5-storage manipulation vulnerabilities

In addition to the general measures described on the [DOM-based vulnerabilities](https://portswigger.net/web-security/dom-based) page, you should avoid allowing data from any untrusted source to be placed in HTML5 storage.