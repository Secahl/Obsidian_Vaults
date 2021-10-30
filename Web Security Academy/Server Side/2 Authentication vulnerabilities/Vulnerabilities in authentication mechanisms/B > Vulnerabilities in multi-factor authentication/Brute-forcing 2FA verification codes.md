## Brute-forcing 2FA verification codes
  
As with passwords, websites need to take steps to prevent brute-forcing of the 2FA verification code.  
This is especially important because the code is often a simple 4 or 6-digit number.  
Without adequate brute-force protection, cracking such a code is trivial.  
  
Some websites attempt to prevent this by automatically logging a user out if they enter a certain number of incorrect verification codes.  
  
This is ineffective in practice because an advanced attacker can even automate this multi-step process by [creating macros](https://portswigger.net/burp/documentation/desktop/options/sessions#macros) _**for Burp Intruder**_. The [Turbo Intruder](https://portswigger.net/bappstore/9abaa233088242e8be252cd4ff534988) _**extension**_ can also be used for this purpose.  
  
  
>LAB [2FA bypass using a brute-force attack](https://portswigger.net/web-security/authentication/multi-factor/lab-2fa-bypass-using-a-brute-force-attack)  
  

### Hint

  
You will need to use Burp macros in conjunction with Burp Intruder to solve this lab. For more information about macros, please refer to the [Burp Suite documentation](https://portswigger.net/burp/documentation/desktop/options/sessions). Users proficient in Python might prefer to use the [Turbo Intruder](https://portswigger.net/bappstore/9abaa233088242e8be252cd4ff534988) extension, which is available from the BApp store.  
  