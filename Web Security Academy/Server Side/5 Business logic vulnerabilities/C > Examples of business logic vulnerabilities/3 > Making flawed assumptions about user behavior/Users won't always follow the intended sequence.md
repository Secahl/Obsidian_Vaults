 ## Users won't always follow the intended sequence
  
Many transactions rely on predefined workflows consisting of a _sequence of steps_.  
The web interface will typically guide users through this process, taking them to the next step of the workflow each time they complete the current one.  
However, attackers won't necessarily adhere to this intended sequence.  
Failing to account for this possibility can lead to dangerous flaws that may be relatively simple to exploit.  
  
**For example**, _many websites that implement two-factor authentication (2FA) require users to log in on one page before entering a verification code on a separate page_.  

Assuming that users will always follow this process through to completion and, as a result, not verifying that they do, may allow attackers to bypass the 2FA step entirely.  
  
>LAB [2FA simple bypass](https://portswigger.net/web-security/authentication/multi-factor/lab-2fa-simple-bypass)  
 
Making assumptions about the sequence of events can lead to a wide range of issues even within the same workflow or functionality.  
  
Using tools like Burp Proxy and Repeater, once an attacker has seen a request, they can replay it at will and use forced browsing to perform any interactions with the server in any order they want. This allows them to complete different actions while the application is in an unexpected state.  
  
>**To identify these kinds of flaws, you should use forced browsing to submit requests in an unintended sequence.**  
For example, you might skip certain steps, access a single step more than once, return to earlier steps, and so on.  
Take note of how different steps are accessed.  
Although you often just submit a `GET` or `POST` request to a specific URL, sometimes you can access steps by submitting different sets of parameters to the same URL.  
  
  
As with all logic flaws, try to identify what assumptions the developers have made and where the attack surface lies.  
You can then look for ways of violating these assumptions. 
-
Note that this kind of testing will often cause exceptions **because expected variables have `null` or `uninitialized values`.**

>Arriving at a location in a partly defined or inconsistent state is also likely to cause the application to complain.  
In this case, be sure to _pay close attention to any error messages or debug information that you encounter._ These can be a valuable source of [information disclosure](https://portswigger.net/web-security/information-disclosure), which can help you fine-tune your attack and understand key details about the back-end behavior.  
  
  
>>LAB [Insufficient workflow validation](https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-insufficient-workflow-validation)  
>LAB [Authentication bypass via flawed state machine](https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-authentication-bypass-via-flawed-state-machine)