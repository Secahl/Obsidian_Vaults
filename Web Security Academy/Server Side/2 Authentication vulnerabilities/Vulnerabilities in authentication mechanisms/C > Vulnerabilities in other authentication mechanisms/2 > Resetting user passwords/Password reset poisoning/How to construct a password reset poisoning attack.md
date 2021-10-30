 ## How to construct a password reset poisoning attack
  
If the URL that is sent to the user is dynamically generated based on controllable input, _such as the Host header_, it may be possible to construct a password reset poisoning attack as follows:  
  
1. The attacker obtains the victim's email address or username, as required, and submits a password reset request on their behalf. When submitting the form, they intercept the resulting HTTP request and modify the Host header so that it points to a domain that they control.  
For this example, we'll use `evil-user.net`.  
  
2. The victim receives a genuine password reset email directly from the website. This seems to contain an ordinary link to reset their password and, crucially, contains a valid password reset token that is associated with their account.  
  
However, the domain name in the URL points to the attacker's server:  
>`https://evil-user.net/reset?token=0a1b2c3d4e5f6g7h8i9j` 
  
3. If the victim clicks this link (or it is fetched in some other way, for example, by an antivirus scanner) the password reset token will be delivered to the attacker's server.  
  
4. The attacker can now visit the real URL for the vulnerable website and supply the victim's stolen token via the corresponding parameter. They will then be able to reset the user's password to whatever they like and subsequently log in to their account.  
  
  
  
In a real attack, the attacker may seek to increase the probability of the victim clicking the link by first warming them up with a fake breach notification.  
  
Even if you can't control the password reset link, you can sometimes use the Host header to inject HTML into sensitive emails. _**Note that email clients typically don't execute JavaScript,**_ but other HTML injection techniques like [dangling markup attacks](https://portswigger.net/web-security/cross-site-scripting/dangling-markup) may still apply.  
  
  
>LAB [Basic password reset poisoning](https://portswigger.net/web-security/host-header/exploiting/password-reset-poisoning/lab-host-header-basic-password-reset-poisoning)  
LAB [Password reset poisoning via middleware](https://portswigger.net/web-security/authentication/other-mechanisms/lab-password-reset-poisoning-via-middleware)  
LAB [Password reset poisoning via dangling markup](https://portswigger.net/web-security/host-header/exploiting/password-reset-poisoning/lab-host-header-password-reset-poisoning-via-dangling-markup)