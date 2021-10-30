 ### Broken access control resulting from platform misconfiguration

_Some applications enforce access controls at the platform layer by_ _**restricting access to specific URLs and HTTP methods based on the user's role**_**.**  
  
For example an application might configure rules like the following:  

```http 
DENY: POST, /admin/deleteUser, managers
```
  
This rule denies access to the `POST` method on the URL `/admin/deleteUser`, for users in the managers group.  
Various things can go wrong in this situation, leading to access control bypasses.  
  
_Some application frameworks support various non-standard HTTP headers_ _that can be used to override the URL in the original request, such as_ _`X-Original-URL`_ _and_ _`X-Rewrite-URL`__._  
If a web site uses rigorous front-end controls to restrict access based on URL, but the _application allows the URL to be overridden via a request header_, then it might be possible to bypass the access controls using a request like the following:  
 
```http
POST / HTTP/1.1  
X-Original-URL: /admin/deleteUser  
```

>LAB [URL-based access control can be circumvented](https://portswigger.net/web-security/access-control/lab-url-based-access-control-can-be-circumvented)  