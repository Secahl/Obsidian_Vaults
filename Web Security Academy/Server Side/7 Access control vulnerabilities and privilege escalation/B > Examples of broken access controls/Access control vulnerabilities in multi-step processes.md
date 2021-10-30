### Access control vulnerabilities in multi-step processes
  
Many web sites implement important functions over a series of steps.  
This is often done when a variety of _inputs or options need to be captured_, or when the _user needs to review and confirm details_ before the action is performed.  
  
_For example_, administrative function to update user details might involve the following steps:  
>1. Load form containing details for a specific user.  
2. Submit changes.  
3. Review the changes and confirm.  
  
  
Sometimes, a web site will implement rigorous access controls over some of these steps, but ignore others.  
For example, suppose access controls are correctly applied to the first and second steps, but not to the third step.  
Effectively, the web site assumes that a user will only reach step 3 if they have already completed the first steps, which are properly controlled.  
_Here, an attacker can gain unauthorized access to the function by skipping the first two steps and directly submitting the request for the third step_ _with the required parameters._  
  
  
>LAB [Multi-step process with no access control on one step](https://portswigger.net/web-security/access-control/lab-multi-step-process-with-no-access-control-on-one-step)