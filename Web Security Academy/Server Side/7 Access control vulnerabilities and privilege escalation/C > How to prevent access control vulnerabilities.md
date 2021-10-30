## How to prevent access control vulnerabilities

Access control vulnerabilities can generally be prevented by taking a defense-in-depth approach and applying the following principles:  
  
>• _Never rely on obfuscation alone for access control._  
  • Unless a resource is intended to be publicly accessible, _deny access by default._  
  • Wherever possible, use a _single application-wide mechanism for enforcing access controls._  
  • At the code level, make it _mandatory for developers to declare the access that is allowed for each resource, and deny access by default._  
  • Thoroughly _audit and test access controls_ to ensure they are working as designed.