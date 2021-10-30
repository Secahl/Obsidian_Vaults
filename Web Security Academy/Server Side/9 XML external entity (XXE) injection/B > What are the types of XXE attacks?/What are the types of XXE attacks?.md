 ## What are the types of XXE attacks?
  
There are various types of XXE attacks:  
  
>• [[1 > Exploiting XXE to retrieve files]], where an external entity is defined containing the contents of a file, and returned in the application's response.  
  
>• [[2 > Exploiting XXE to perform SSRF attacks]], where an external entity is defined based on a URL to a back-end system.  
  
 >- [[Blind XXE vulnerabilities]]
>> [[B > Exploiting blind XXE to exfiltrate data out-of-band#Exploiting blind XXE to exfiltrate data out-of-band | Exploiting blind XXE to exfiltrate data out-of-band]], where sensitive data is transmitted from the application server to a system that the attacker controls.  <br>
>> [[C > Exploiting blind XXE to retrieve data via error messages#Exploiting blind XXE to retrieve data via error messages | Exploiting blind XXE to retrieve data via error messages]], where the attacker can trigger a parsing error message containing sensitive data.