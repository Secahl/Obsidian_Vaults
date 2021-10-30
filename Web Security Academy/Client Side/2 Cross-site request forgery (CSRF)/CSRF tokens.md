Parent Links : [[Cross-site request forgery (CSRF)]] > [[Preventing CSRF attacks]]     

# CSRF tokens
  
In this section, we'll explain what CSRF tokens are, how they protect against [CSRF attacks](https://portswigger.net/web-security/csrf), and how CSRF tokens should be generated and validated.  
  

## What are CSRF tokens?
  
A CSRF token is a unique, secret, unpredictable value that is generated by the server-side application and transmitted to the client in such a way that it is included in a subsequent HTTP request made by the client. When the later request is made, the server-side application validates that the request includes the expected token and rejects the request if the token is missing or invalid.  
  
CSRF tokens can prevent CSRF attacks by making it impossible for an attacker to construct a fully valid HTTP request suitable for feeding to a victim user. Since the attacker cannot determine or predict the value of a user's CSRF token, they cannot construct a request with all the parameters that are necessary for the application to honor the request.  
  
  

## How should CSRF tokens be generated?
  
CSRF tokens should contain significant entropy and be strongly unpredictable, with the same properties as session tokens in general.  
You should use a cryptographic strength pseudo-random number generator (PRNG), seeded with the timestamp when it was created plus a static secret.  
If you need further assurance beyond the strength of the PRNG, you can generate individual tokens by concatenating its output with some user-specific entropy and take a strong hash of the whole structure. This presents an additional barrier to an attacker who attempts to analyze the tokens based on a sample that are issued to them.  
  
  

## How should CSRF tokens be transmitted?
  
CSRF tokens should be treated as secrets and handled in a secure manner throughout their lifecycle. An approach that is normally effective is to transmit the token to the client within a hidden field of an HTML form that is submitted using the POST method. The token will then be included as a request parameter when the form is submitted :  
```html
<input type="hidden" name="csrf-token" value="CIwNZNlR4XbisJF39I8yWnWX9wX4WFoz" /> 
```

 
For additional safety, the field containing the CSRF token should be placed as early as possible within the HTML document, ideally before any non-hidden input fields and before any locations where user-controllable data is embedded within the HTML. This mitigates against various techniques in which an attacker can use crafted data to manipulate the HTML document and capture parts of its contents.  
  
An alternative approach, of placing the token into the URL query string, is somewhat less safe because the query string:  
>• Is logged in various locations on the client and server side;  
• Is liable to be transmitted to third parties within the HTTP Referer header; and  
• can be displayed on-screen within the user's browser.  
  
Some applications transmit CSRF tokens within a custom request header. This presents a further defense against an attacker who manages to predict or capture another user's token, because browsers do not normally allow custom headers to be sent cross-domain. However, the approach limits the application to making CSRF-protected requests using XHR (as opposed to HTML forms) and might be deemed over-complicated for many situations.  
>_**CSRF tokens should not be transmitted within** **cookies**_
  
  
  

## How should CSRF tokens be validated?

  
  
When a CSRF token is generated, it should be stored server-side within the user's session data. When a subsequent request is received that requires validation, the server-side application should verify that the request includes a token which matches the value that was stored in the user's session. This validation must be performed regardless of the HTTP method or content type of the request. If the request does not contain any token at all, it should be rejected in the same way as when an invalid token is present.