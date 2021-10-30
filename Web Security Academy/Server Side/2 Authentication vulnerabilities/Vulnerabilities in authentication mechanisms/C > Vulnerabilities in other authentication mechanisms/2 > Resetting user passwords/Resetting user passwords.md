## Resetting user passwords

There are a few different ways that this feature is commonly implemented, with varying degrees of vulnerability :  

### Sending passwords by email

It should go without saying that sending users their current password should never be possible if a website handles passwords securely in the first place. Instead, some websites generate a new password and send this to the user via email.  
Generally speaking, sending persistent passwords over insecure channels is to be avoided. In this case, the security relies on either the generated password expiring after a very short period, or the user changing their password again immediately. Otherwise, this approach is highly susceptible to man-in-the-middle attacks.  
Email is also generally not considered secure given that inboxes are both persistent and not really designed for secure storage of confidential information. Many users also automatically sync their inbox between multiple devices across insecure channels.

### Resetting passwords using a URL


A more robust method of resetting passwords is to send a unique URL to users that takes them to a password reset page.  
  
Less secure implementations of this method use a URL with an easily guessable parameter to identify which account is being reset, for example:  

`http://vulnerable-website.com/reset-password?user=victim-user`

In this example, an attacker could change the user parameter to refer to any username they have identified. They would then be taken straight to a page where they can potentially set a new password for this arbitrary user.  
 
A better implementation of this process is to generate a high-entropy, hard-to-guess token and create the reset URL based on that.  
  
In the best case scenario, this URL should provide no hints about which user's password is being reset.  
`http://vulnerable-website.com/reset-password?token=a0ba0d1cb3b63d13822572fcff1a241895d893f659164d4cc550b421ebdd48a8`

When the user visits this URL, the system should check whether this token exists on the back-end and, if so, which user's password it is supposed to reset. This token should expire after a short period of time and be destroyed immediately after the password has been reset.  
  
However, some websites fail to also validate the token again when the reset form is submitted.  
In this case, an attacker could simply visit the reset form from their own account, delete the token, and leverage this page to reset an arbitrary user's password.  
  
> LAB Password reset broken logic  
  
  
If the URL in the reset email is generated dynamically, this may also be vulnerable to password reset poisoning. In this case, an attacker can potentially steal another user's token and use it change their password.  
  
> LAB Password reset poisoning via middleware


Linked Nodes :

[[How does a password reset work?]]
[[How to construct a password reset poisoning attack]]