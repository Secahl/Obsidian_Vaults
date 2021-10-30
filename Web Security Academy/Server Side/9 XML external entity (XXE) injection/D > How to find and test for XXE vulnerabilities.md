## How to find and test for XXE vulnerabilities
  
The vast majority of XXE vulnerabilities can be found quickly and reliably using Burp Suite's [web vulnerability scanner](https://portswigger.net/burp/vulnerability-scanner).  
  
**Manually testing for XXE vulnerabilities generally involves :**
  
>• Testing for [[1 > Exploiting XXE to retrieve files#Exploiting XXE to retrieve files | file retrieval]] by defining an external entity based on a well-known operating system file and using that entity in data that is returned in the application's response.  
  
>• Testing for [[Blind XXE vulnerabilities#Blind XXE vulnerabilities | Blind XXE vulnerabilities]] by defining an external entity based on a URL to a system that you control, and monitoring for interactions with that system. [Burp Collaborator client](https://portswigger.net/burp/documentation/desktop/tools/collaborator-client) is perfect for this purpose.  
  
>• Testing for vulnerable inclusion of user-supplied non-XML data within a server-side XML document by using an [[XInclude attacks#XInclude attacks | XInclude attack]] to try to retrieve a well-known operating system file.