 ## How do business logic vulnerabilities arise?

Business logic vulnerabilities often arise because the design and development teams make flawed assumptions about how users will interact with the application.  
  
These bad assumptions can lead to inadequate validation of user input.  
  
**For example**, if the developers assume that users will pass data exclusively via a web browser, the application may rely entirely on weak client-side controls to validate input.  
  
_These are easily bypassed by an attacker using an _**intercepting proxy**_._
  
Ultimately, this means that when an attacker deviates from the expected user behavior, the application fails to take appropriate steps to prevent this and, subsequently, fails to handle the situation safely.  
  
  
>_Logic flaws are particularly common in overly complicated systems that even the development team themselves do not fully understand._  
_To avoid logic flaws, developers need to understand the application as a whole._  
_This includes being aware of how different functions can be combined in unexpected ways. _  
_Developers working on large code bases may not have an intimate understanding of how all areas of the application work.  
Someone working on one component could make flawed assumptions about how another component works and, as a result, inadvertently introduce serious logic flaws._  
_If the developers do not explicitly document any assumptions that are being made, it is easy for these kinds of vulnerabilities to creep into an application._