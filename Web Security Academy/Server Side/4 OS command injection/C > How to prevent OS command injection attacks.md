## How to prevent OS command injection attacks

By far the most effective way to prevent OS command injection vulnerabilities is to never call out to OS commands from **application-layer code**.  
  
In virtually every case, there are alternate ways of implementing the required functionality _using safer platform APIs._  
  
If it is considered unavoidable to call out to OS commands with user-supplied input, then strong input validation must be performed.  
  
  
Some examples of effective validation include:  
  
>• Validating against a whitelist of permitted values.  
• Validating that the input is a number.  
• Validating that the input contains only alphanumeric characters, no other syntax or whitespace.  
•  
  
**Never** attempt to sanitize input by _**escaping shell metacharacters**_.  
  
In practice, _this is just too error-prone and vulnerable_ to being bypassed by a skilled attacker.