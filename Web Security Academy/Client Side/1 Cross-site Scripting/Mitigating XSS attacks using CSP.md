Parent Links : [[Cross-site scripting]] > [[Content security policy]]    

## Mitigating XSS attacks using CSP

The following directive will only allow scripts to be loaded from the [same origin](https://portswigger.net/web-security/cors/same-origin-policy) as the page itself:  
`script-src 'self'`  
The following directive will only allow scripts to be loaded from a specific domain:  
`script-src https://scripts.normal-website.com  
`  
Care should be taken when allowing scripts from external domains. If there is any way for an attacker to control content that is served from the external domain, then they might be able to deliver an attack.  
For example, content delivery networks (CDNs) that do not use per-customer URLs, such as `ajax.googleapis.com`, should not be trusted, because third parties can get content onto their domains.  
  
In addition to whitelisting specific domains, content security policy also provides two other ways of specifying trusted resources: nonces and hashes:  
>• The CSP directive can specify a nonce (a random value) and the same value must be used in the tag that loads a script. If the values do not match, then the script will not execute. To be effective as a control, the nonce must be securely generated on each page load and not be guessable by an attacker.  
>• The CSP directive can specify a hash of the contents of the trusted script. If the hash of the actual script does not match the value specified in the directive, then the script will not execute. If the content of the script ever changes, then you will of course need to update the hash value that is specified in the directive.  
  
It's quite common for a CSP to block resources like `script`. However, many CSPs do allow image requests. This means you can often use `img` elements to make requests to external servers in order to disclose [CSRF tokens](https://portswigger.net/web-security/csrf/tokens), for example.  
  
Some browsers, such as Chrome, have built-in [dangling markup](https://portswigger.net/web-security/cross-site-scripting/dangling-markup) mitigation that will block requests containing certain characters, such as raw, unencoded new lines or angle brackets. In this next lab, you'll need to get round these Chrome restrictions and make an external request using a different element and attribute.  
  
>LAB [Reflected XSS protected by CSP, with dangling markup attack](https://portswigger.net/web-security/cross-site-scripting/content-security-policy/lab-csp-with-dangling-markup-attack)