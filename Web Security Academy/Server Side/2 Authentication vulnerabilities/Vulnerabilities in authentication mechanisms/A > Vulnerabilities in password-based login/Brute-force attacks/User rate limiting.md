### User rate limiting

Another way websites try to prevent brute-force attacks is through user rate limiting. In this case, making _too many login requests within a short period of time_ causes your IP address to be blocked.  
  
Typically, the IP can only be unblocked in one of the following ways:  
  
• Automatically after a certain period of time has elapsed  
• Manually by an administrator  
• Manually by the user after successfully completing a CAPTCHA  
  
User rate limiting is sometimes preferred to account locking due to being less prone to username enumeration and denial of service attacks.  
  
However, it is still not completely secure. As we saw an example of in an earlier lab, there are several ways an attacker can manipulate their apparent IP in order to bypass the block.  
As the limit is based on the rate of HTTP requests sent from the user's IP address, it is sometimes also possible to bypass this defense _if you can work out how to guess multiple passwords with a single request._  
  
  
LAB [Broken brute-force protection, multiple credentials per request](https://portswigger.net/web-security/authentication/password-based/lab-broken-brute-force-protection-multiple-credentials-per-request)