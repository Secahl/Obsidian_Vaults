## Keeping users logged in

**A common feature is the option to stay logged in even after closing a browser session.** This is usually a simple checkbox labeled something like "Remember me" or "Keep me logged in".  
  
  
This functionality is often implemented by generating a "remember me" token of some kind, which is then stored in a **persistent cookie.** As possessing this cookie effectively allows you to bypass the entire login process, it is best practice for this cookie to be impractical to guess.  
  
However, some websites generate this cookie based on a predictable concatenation of static values, such as the username and a timestamp. Some even use the password as part of the cookie.  
  
This approach is particularly dangerous if an attacker is able to create their own account because they can _study their own cookie and potentially deduce how it is generated._  
Once they work out the formula, they can try to brute-force other users' cookies to gain access to their accounts.  
  
  
Some websites assume that if the cookie is encrypted in some way it will not be guessable even if it does use static values.  
While this may be true if done correctly, naively "encrypting" the cookie _using a simple two-way encoding like Base64 offers no protection whatsoever._  
  
_Even using proper encryption with a one-way hash function is not completely bulletproof._  
  
If the attacker is able to easily identify the hashing algorithm, and no salt is used, they can potentially brute-force the cookie by simply hashing their wordlists.  
  
_**This method can be used to bypass login attempt limits if a similar limit isn't applied to cookie guesses.**_

>LAB [Brute-forcing a stay-logged-in cookie](https://portswigger.net/web-security/authentication/other-mechanisms/lab-brute-forcing-a-stay-logged-in-cookie)  
  
Even if the attacker is not able to create their own account, they may still be able to exploit this vulnerability.  
  
Using the usual techniques, such as [XSS](https://portswigger.net/web-security/cross-site-scripting), an attacker could steal another user's "remember me" cookie and deduce how the cookie is constructed from that.  
  
_If the website was built using an open-source framework, the key details of the cookie construction may even be publicly documented.  
_  
In some rare cases, it may be possible to obtain a user's actual password in cleartext from a cookie, even if it is hashed.  
  
_**Hashed versions of well-known password lists are available online, so if the user's password appears in one of these lists, decrypting the hash can occasionally be as trivial as just pasting the hash into a search engine. This demonstrates the importance of salt in effective encryption.**_  
  
  
>LAB [Offline password cracking](https://portswigger.net/web-security/authentication/other-mechanisms/lab-offline-password-cracking)