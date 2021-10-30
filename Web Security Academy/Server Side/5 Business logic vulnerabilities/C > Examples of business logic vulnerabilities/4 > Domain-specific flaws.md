## Domain-specific flaws
  
In many cases, you will encounter logic flaws that are _specific to the business domain or the purpose of the site._  
  
The discounting functionality of online shops is a classic attack surface when hunting for logic flaws. This can be a potential gold mine for an attacker, with all kinds of basic logic flaws occurring in the way discounts are applied.  
  
**For example**, 
>Consider an online shop that offers a 10% discount on orders over $1000. This could be vulnerable to abuse if the business logic fails to check whether the order was changed after the discount is applied.  
In this case, an attacker could _simply add items to their cart until they hit the $1000 threshold, then remove the items they don't want before placing the order._  
They would then receive the discount on their order even though it no longer satisfies the intended criteria.  
  
  
**You should pay particular attention to any situation where prices or other sensitive values are adjusted based on criteria determined by user actions.**  
Try to understand what algorithms the application uses to make these adjustments and at what point these adjustments are made.  
This often involves manipulating the application so that it is in a state where the applied adjustments do not correspond to the original criteria intended by the developers.  
  
To identify these vulnerabilities, you need to think carefully about what objectives an attacker might have and try to find different ways of achieving this using the provided functionality. This may require a certain level of _domain-specific knowledge_ in order to understand what might be advantageous in a given context.  
To use a simple example, you need to understand social media to understand the benefits of forcing a large number of users to follow you.  
Without this _knowledge of the domain_, you may dismiss dangerous behavior because you simply aren't aware of its potential knock-on effects.  
  
Likewise, you may struggle to join the dots and notice how two functions can be combined in a harmful way.  
  
  
For simplicity, the examples used in this topic are specific to a domain that all users will already be familiar with, namely an online shop.  
>However, whether you're bug bounty hunting, [pentesting](https://portswigger.net/solutions/penetration-testing), or even just a developer trying to write more secure code, you may at some point encounter applications from less familiar domains.  
In this case, you should _read as much documentation as possible and, where available, talk to subject-matter experts from the domain to get their insight._  
This may sound like a lot of work, but the more obscure the domain is, the more likely other testers will have missed plenty of bugs.  
  
  
>>LAB [Flawed enforcement of business rules](https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-flawed-enforcement-of-business-rules)  
LAB [Infinite money logic flaw](https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-infinite-money)