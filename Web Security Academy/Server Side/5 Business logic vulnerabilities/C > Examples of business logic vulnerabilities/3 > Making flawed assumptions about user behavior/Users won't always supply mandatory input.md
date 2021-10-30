### Users won't always supply mandatory input
  
One misconception is that users will always supply values for mandatory input fields.  
_  
Browsers may prevent ordinary users from submitting a form without a required input, but as we know, attackers can tamper with parameters in transit._  
  
This even extends to removing parameters entirely.  
  
This is a particular issue in cases where multiple functions are implemented within the same server-side script.  
In this case, the presence or absence of a particular parameter may determine which code is executed.  
Removing parameter values may allow an attacker to access code paths that are supposed to be out of reach.  
  
  
>**When probing for logic flaws, you should try removing each parameter in turn and observing what effect this has on the response.**  
  
**You should make sure to : ** 
>• Only remove one parameter at a time to ensure all relevant code paths are reached.  
• Try deleting the name of the parameter as well as the value. The server will typically handle both cases differently.  
• Follow multi-stage processes through to completion. Sometimes tampering with a parameter in one step will have an effect on another step further along in the workflow.  
  
  
  
_This applies to both_ _`URL`_ _and_ _`POST`_ _parameters_, _**but don't forget to check the cookies too**_. This simple process can reveal some bizarre application behavior that may be exploitable.  
  
  
>LAB [Weak isolation on dual-use endpoint](https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-weak-isolation-on-dual-use-endpoint)  
  
>LAB [Password reset broken logic](https://portswigger.net/web-security/authentication/other-mechanisms/lab-password-reset-broken-logic)