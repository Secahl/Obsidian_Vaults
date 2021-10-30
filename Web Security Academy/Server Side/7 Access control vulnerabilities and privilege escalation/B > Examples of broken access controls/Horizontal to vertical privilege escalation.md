### Horizontal to vertical privilege escalation
  
Often, a horizontal privilege escalation attack can be turned into a vertical privilege escalation, by compromising a more privileged user.  
  
For example, a horizontal escalation might allow an attacker to reset or capture the password belonging to another user.  
_If the attacker targets an administrative user and compromises their account, then they can gain administrative access and so perform vertical privilege escalation._  
  
  
For example, an attacker might be able to gain access to another user's account page using the parameter tampering technique already described for horizontal privilege escalation:  
>`https://insecure-website.com/myaccount?id=456`  

If the target user is an application administrator, then the attacker will gain access to an administrative account page.  
This page might disclose the administrator's password or provide a means of changing it, or might provide direct access to privileged functionality.  
  
  
>LAB [User ID controlled by request parameter with password disclosure](https://portswigger.net/web-security/access-control/lab-user-id-controlled-by-request-parameter-with-password-disclosure)