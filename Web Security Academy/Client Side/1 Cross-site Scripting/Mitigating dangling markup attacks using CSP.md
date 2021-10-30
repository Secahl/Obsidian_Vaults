Parent Links : [[Cross-site scripting]] > [[Content security policy]]     

## Mitigating dangling markup attacks using CSP

The following directive will only allow images to be loaded from the same origin as the page itself:  
`img-src 'self'`  
The following directive will only allow images to be loaded from a specific domain:  
`img-src https://images.normal-website.com`  
Note that these policies will prevent some dangling markup exploits, because an easy way to capture data with no user interaction is using an `img` tag. However, it will not prevent other exploits, such as those that inject an anchor tag with a dangling `href` attribute.