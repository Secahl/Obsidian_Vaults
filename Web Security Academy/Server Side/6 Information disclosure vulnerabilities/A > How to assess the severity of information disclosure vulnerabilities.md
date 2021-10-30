## How to assess the severity of information disclosure vulnerabilities

Although the ultimate impact can potentially be very severe, it is only in specific circumstances that information disclosure is a high-severity issue on its own.  
  
_During testing, the disclosure of technical information in particular is often only of interest if you are able to demonstrate how an attacker could do something harmful with it._  
  
**For example**, the knowledge that a website is using a particular framework version is of limited use if that version is fully patched.  
However, this information becomes significant when the website is using an old version that contains a known vulnerability.  
In this case, performing a devastating attack could be as simple as applying a publicly documented exploit.  
  
  
**It is important to exercise common sense when you find that potentially sensitive information is being leaked.  
It is likely that minor technical details can be discovered in numerous ways on many of the websites you test.**  
>_Therefore, your main focus should be on the impact and exploitability of the leaked information, not just the presence of information disclosure as a standalone issue._  
>>**The obvious exception to this is when the leaked information is so sensitive that it warrants attention in its own right.**