## Changing user passwords

Typically, changing your password involves entering your current password and then the new password twice.  
  
These pages fundamentally rely on the same process for checking that usernames and current passwords match as a normal login page does.  
Therefore, these pages can be vulnerable to the same techniques.  
  
  
Password change functionality can be particularly dangerous if it allows an attacker to access it directly without being logged in as the victim user.  
  
**For example**, if the username is provided in a hidden field, an attacker might be able to edit this value in the request to target arbitrary users.  
_This can potentially be exploited to enumerate usernames and brute-force passwords._  
  
  
>LAB [Password brute-force via password change](https://portswigger.net/web-security/authentication/other-mechanisms/lab-password-brute-force-via-password-change)