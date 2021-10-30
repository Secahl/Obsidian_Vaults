  ## About Vulnerabilities in multi-factor authentication
  
Verifying biometric factors is impractical for most websites. However, it is increasingly common to see both mandatory and optional two-factor authentication (2FA) based on **something you know** and **something you have**. This usually requires users to enter both a traditional password and a temporary verification code from an out-of-band physical device in their possession.  
  
While it is sometimes possible for an attacker to obtain a single knowledge-based factor, such as a password, so being able to simultaneously obtain another factor from an out-of-band source is considerably less likely. For this reason, two-factor authentication is demonstrably more secure than single-factor authentication.  
However, as with any security measure, it is only ever as secure as its implementation.  
  
Poorly implemented two-factor authentication can be beaten, or even bypassed entirely, just as single-factor authentication can.  
  
It is also worth noting that the full benefits of multi-factor authentication are only achieved by verifying multiple **different** factors.  
  
Verifying the same factor in two different ways is not true two-factor authentication.  

Email-based 2FA is one such example.  
Although the user has to provide a password and a verification code, accessing the code only relies on them knowing the login credentials for their email account. Therefore, the knowledge authentication factor is simply being verified twice.

Linked Nodes:
[[Two-factor authentication tokens]]
[[Bypassing two-factor authentication]]
[[Flawed two-factor verification logic]]
[[Brute-forcing 2FA verification codes]]