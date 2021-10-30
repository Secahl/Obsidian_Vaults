   In this section we explain what [access control](https://portswigger.net/web-security/access-control) security models are and we discuss the most commonly encountered models.  
  
## What are access control security models?

_An access control security model is a_ _**formally defined definition of a set of access control rules**_ _that is independent of technology or implementation platform._  
  
Access control security models are implemented within operating systems, networks, database management systems and back office, application and web server software.  
  
Various access control security models have been devised over the years to match access control policies to business or organizational rules and changes in technology.  
  
  
## Programmatic access control

With programmatic access control, _a matrix of user privileges is stored in a database or similar and_ [access controls](https://portswigger.net/web-security/access-control) _are applied programmatically with reference to this matrix._  
This approach to access control can include roles or groups or individual users, collections or workflows of processes and can be highly granular.  
  

## Discretionary access control (DAC)

With discretionary access control, access to resources or functions is constrained based upon users or named groups of users.  
Owners of _resources or functions_ have the ability to assign or delegate access permissions to users.  
This model is highly granular with access rights defined to an _individual resource or function and user_. Consequently the model can become very complex to design and manage.  
  
  
## Mandatory access control (MAC)

Mandatory access control is a centrally controlled system of access control in which access to some object (a file or other resource) by a subject is constrained(forced, obliged).  
Significantly, unlike DAC the users and owners of resources have no capability to delegate or modify access rights for their resources.  
_This model is often associated with military clearance-based systems._  
  
  
## Role-based access control (RBAC)

With role-based access control, named roles are defined to which access privileges are assigned.  
Users are then assigned to single or multiple roles.  
  
_RBAC provides enhanced management over other access control models_ _and provides manageable access control in complex applications if sufficient granularity is properly designed._  
  
**For example**, the purchase clerk might be defined as a role with access permissions for a subset of purchase ledger functionality and resources. As employees leave or join an organization then access control management is simplified to defining or revoking membership of the purchases clerk role.  
  
_RBAC is most effective when there are sufficient roles to properly invoke access controls but not so many as to make the model excessively complex and unwieldy to manage._