Parent Links : [[DOM-based vulnerabilities]]

# Controlling the web message source

In this section, we'll look at how web messages can be used as a source to exploit [[DOM-based vulnerabilities]] on the recipient page. We'll also describe how such an attack is constructed, including how common origin-verification techniques can often be bypassed.

If a page handles incoming web messages in an unsafe way, for example, by not verifying the origin of incoming messages correctly in the event listener, properties and functions that are called by the event listener can potentially become sinks. For example, an attacker could host a malicious `iframe` and use the `postMessage()` method to pass web message data to the vulnerable event listener, which then sends the payload to a sink on the parent page. This behavior means that you can use web messages as the source for propagating malicious data to any of those sinks.

## What is the impact of DOM-based web message vulnerabilities?

The potential impact of the vulnerability depends on the destination document's handling of the incoming message. If the destination document trusts the sender not to transmit malicious data in the message, and handles the data in an unsafe way by passing it into a sink, then the joint behavior of the two documents may allow an attacker to compromise the user, for example.

## How to construct an attack using web messages as the source

Consider the following code:

```js 
<script>  
window.addEventListener('message', function(e) {  
  eval(e.data);  
});  
</script>
```

This is vulnerable because an attacker could inject a JavaScript payload by constructing the following `iframe`:

```js 
<iframe src="//vulnerable-website" onload="this.contentWindow.postMessage('print()','*')">
```

As the event listener does not verify the origin of the message, and the `postMessage()` method specifies the `targetOrigin` `"*"`, the event listener accepts the payload and passes it into a sink, in this case, the `eval()` function.

>LAB [DOM XSS using web messages](https://portswigger.net/web-security/dom-based/controlling-the-web-message-source/lab-dom-xss-using-web-messages) Not solved

>LAB [DOM XSS using web messages and a JavaScript URL](https://portswigger.net/web-security/dom-based/controlling-the-web-message-source/lab-dom-xss-using-web-messages-and-a-javascript-url)


## Origin verification

Even if an event listener does include some form of origin verification, this verification step can sometimes be fundamentally flawed. For example, consider the following code:

```js 
window.addEventListener('message', function(e) {  
  if (e.origin.indexOf('normal-website.com') > -1) {  
    eval(e.data);  
  }  
});
```

The `indexOf` method is used to try and verify that the origin of the incoming message is the `normal-website.com` domain. However, in practice, it only checks whether the string `"normal-website.com"` is contained anywhere in the origin URL. As a result, an attacker could easily bypass this verification step if the origin of their malicious message was `http://www.normal-website.com.evil.net`, for example.

The same flaw also applies to verification checks that rely on the `startsWith()` or `endsWith()` methods. For example, the following event listener would regard the origin `http://www.malicious-websitenormal-website.com` as safe:

```js 
window.addEventListener('message', function(e) {  
  if (e.origin.endsWith('normal-website.com')) {  
    eval(e.data);  
  }  
});
```

>LAB [DOM XSS using web messages and `JSON.parse`](https://portswigger.net/web-security/dom-based/controlling-the-web-message-source/lab-dom-xss-using-web-messages-and-json-parse)


## Which sinks can lead to DOM-based web message vulnerabilities?

As long as a website accepts web message data from an untrusted source due to a lack of adequate origin verification, any sinks that are used by the incoming message event listener could potentially lead to vulnerabilities.