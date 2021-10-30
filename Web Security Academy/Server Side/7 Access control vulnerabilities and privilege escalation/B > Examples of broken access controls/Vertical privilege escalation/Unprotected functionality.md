### Unprotected functionality
  
At its most basic, vertical privilege escalation arises where an application does not enforce any protection over sensitive functionality.  
  
For example, administrative functions might be linked from an administrator's welcome page but not from a user's welcome page. However, a user might simply be able to access the administrative functions by browsing directly to the relevant admin URL.  
  
For example, a website might host sensitive functionality at the following URL:  
>`https://insecure-website.com/admin`
  
This might in fact be accessible by any user, not only administrative users who have a link to the functionality in their user interface.  
In some cases, the administrative URL might be disclosed in other locations, such as the `robots.txt` file:  
>`https://insecure-website.com/robots.txt`
  
_Even if the URL isn't disclosed anywhere, an attacker may be able to use a wordlist to brute-force the location of the sensitive functionality._  
  
  
>LAB [Unprotected admin functionality](https://portswigger.net/web-security/access-control/lab-unprotected-admin-functionality)  
  
  <br>
  <hr>
<hr>
<br>


In some cases, sensitive functionality is not robustly protected but is concealed by giving it a less predictable URL: so called security by obscurity.  
_Merely hiding sensitive functionality does not provide effective access control since users might still discover the obfuscated URL in various ways._  
  
For example, consider an application that hosts administrative functions at the following URL:  
`https://insecure-website.com/administrator-panel-yb556`  
  
This might not be directly guessable by an attacker. However, the application might still leak the URL to users.  
  
For example, the URL might be disclosed in JavaScript that constructs the user interface based on the user's role:  
```js
<script>  
var isAdmin = false;  
if (isAdmin) {  
  ...  
  var adminPanelTag = document.createElement('a');  
  adminPanelTag.setAttribute('https://insecure-website.com/administrator-panel-yb556');  
  adminPanelTag.innerText = 'Admin panel';  
  ...  
}  
</script>  
```

This script adds a link to the user's UI if they are an admin user. However, the script containing the URL is visible to all users regardless of their role.  
  
  
>LAB [Unprotected admin functionality with unpredictable URL](https://portswigger.net/web-security/access-control/lab-unprotected-admin-functionality-with-unpredictable-url)