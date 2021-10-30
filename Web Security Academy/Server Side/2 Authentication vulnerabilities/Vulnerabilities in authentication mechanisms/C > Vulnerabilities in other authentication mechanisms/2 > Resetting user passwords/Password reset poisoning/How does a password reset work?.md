## How does a password reset work?

Virtually all websites that require a login also implement functionality that allows users to reset their password if they forget it. There are several ways of doing this, with varying degrees of security and practicality.  
  
One of the most common approaches goes something like this:  
  
1. The user enters their username or email address and submits a password reset request.  
  
2. The website checks that this user exists and then generates a temporary, unique, high-entropy token, which it associates with the user's account on the back-end.  
  
3. The website sends an email to the user that contains a link for resetting their password. The user's unique reset token is included as a query parameter in the corresponding URL:  
>`https://normal-website.com/reset?token=0a1b2c3d4e5f6g7h8i9j`
  
4. When the user visits this URL, the website checks whether the provided token is valid and uses it to determine which account is being reset. If everything is as expected, the user is given the option to enter a new password. Finally, the token is destroyed.  
  
  
This process is simple enough and relatively secure in comparison to some other approaches. _However, its security relies on the principle that only the intended user has access to their email inbox_ and, therefore, to their unique token.  
  
_Password reset poisoning is a method of stealing this token in order to change another user's password._