 ## What is access control?

Access control (or authorization) is the application of constraints on who (or what) can perform attempted actions or access resources that they have requested.  
  
In the context of web applications, **access control is dependent on authentication and session management**:  
>• **Authentication** identifies the user and confirms that they are who they say they are.  
• **Session management** identifies which subsequent HTTP requests are being made by that same user.  
• **Access control** determines whether the user is allowed to carry out the action that they are attempting to perform.  
  
Broken access controls are a commonly encountered and often critical security vulnerability.  
>_Design and management of access controls is a complex and dynamic problem that applies business, organizational, and legal constraints to a technical implementation._  

Access control design decisions have to be made by humans, not technology, and the potential for errors is high.  
  
From a user perspective, access controls can be divided into the following categories:  
>◇ [Vertical access controls](https://portswigger.net/web-security/access-control#vertical-access-controls)  
◇ [Horizontal access controls](https://portswigger.net/web-security/access-control#horizontal-access-controls)  
◇ [Context-dependent access controls](https://portswigger.net/web-security/access-control#context-dependent-access-controls)  
  
[![file:///tmp/.MSD3B1/1.png](file:///tmp/.MSD3B1/1.png)](https://portswigger.net/web-security/images/access-control.svg)  
  
  

>##### Read more : [Access control security models](https://portswigger.net/web-security/access-control/security-models)  
  
  
  

### Vertical access controls

  
  
>Vertical access controls are mechanisms that restrict access to sensitive _functionality_ that is not available to other types of users.  
_With vertical access controls, different types of users have access to different application functions._  
  
**For example**, an administrator might be able to modify or delete any user's account, while an ordinary user has no access to these actions.  
Vertical access controls can be more fine-grained implementations of security models designed to enforce business policies such as separation of duties and least privilege.  
  
  

### Horizontal access controls

  
  
>Horizontal access controls are mechanisms that restrict access to _resources_ to the users who are specifically allowed to access those resources.  
_With horizontal access controls, different users have access to a subset of resources of the same type._  
  
**For example**, a banking application will allow a user to view transactions and make payments from their own accounts, but not the accounts of any other user.  
  
  

### Context-dependent access controls

  
  
>Context-dependent access controls restrict access to _functionality_ and _resources_ based upon the state of the application or the user's interaction with it.  
_Context-dependent access controls prevent a user performing actions in the wrong order._  
  
**For example**, a retail website might prevent users from modifying the contents of their shopping cart after they have made payment.


Linked Nodes :

[[A > Access control security models]]
[[Examples of broken access controls]]
[[C > How to prevent access control vulnerabilities]]