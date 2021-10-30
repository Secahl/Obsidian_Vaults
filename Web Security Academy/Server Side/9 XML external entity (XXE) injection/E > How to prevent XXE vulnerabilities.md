## How to prevent XXE vulnerabilities
  
Virtually all XXE vulnerabilities arise because the _application's XML parsing library supports potentially dangerous XML features that the application does not need or intend to use_.  
  
The easiest and most effective way to prevent XXE attacks is to disable those features.  
  
Generally, it is sufficient to disable resolution of external entities and disable support for `XInclude`. This can usually be done via configuration options or by programmatically overriding default behavior.  
Consult the documentation for your XML parsing library or API for details about how to disable unnecessary capabilities.  
  
  

>###### Read more : [Find XXE vulnerabilities using Burp Suite's web vulnerability scanner](https://portswigger.net/burp/vulnerability-scanner)