## Business logic vulnerabilities

In this section, we'll introduce the concept of business logic vulnerabilities and explain how they can arise due to flawed assumptions about user behavior.  

## What are business logic vulnerabilities?

Business logic vulnerabilities are _**flaws in the design and implementation of an application**_ that allow an attacker to elicit unintended behavior.  
This potentially enables attackers to _manipulate legitimate functionality_ to achieve a malicious goal.  
These flaws are generally the result of failing to anticipate unusual application states that may occur and, consequently, failing to handle them safely.  

### Note

>In this context, the term "business logic" simply refers to the set of rules that define how the application operates. As these rules aren't always directly related to a business, the associated vulnerabilities are also known as "application logic vulnerabilities" or simply "logic flaws".  
  
_One of the main purposes of business logic is to enforce the rules and constraints that were defined when designing the application or functionality._  
Broadly speaking, the business rules dictate how the application should react when a given scenario occurs.  
This includes preventing users from doing things that will have a negative impact on the business or that simply don't make sense.  
  
Flaws in the logic can allow attackers to circumvent these rules.  
  
**For example**, they might be able to complete a transaction without going through the intended purchase workflow.  
In other cases, broken or non-existent validation of user-supplied data might allow users to make arbitrary changes to transaction-critical values or submit nonsensical input.  
  
By passing unexpected values into server-side logic, an attacker can potentially induce the application to do something that it isn't supposed to.  
  
Logic-based vulnerabilities can be extremely diverse and are often unique to the application and its specific functionality.  
Identifying them often requires a certain amount of human knowledge, such as an understanding of the business domain or what goals an attacker might have in a given context.  

_
This makes them difficult to detect using automated vulnerability scanners._  
  
As a result, _logic flaws are a great target for bug bounty hunters and manual testers in general.  
_


Linked Nodes :
[[A > How do business logic vulnerabilities arise?]]
[[B > What is the impact of business logic vulnerabilities?]]
[[Examples of business logic vulnerabilities]]
[[D > How to prevent business logic vulnerabilities]]