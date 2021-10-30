 ### SSRF with whitelist-based input filters

Some applications only allow input that matches, begins with, or contains, a whitelist of permitted values.  
In this situation, _you can sometimes circumvent the filter by_ _**exploiting inconsistencies in URL parsing**_**.**  
  
**The URL specification** _contains a number of features that are liable to be overlooked when implementing_ _ad hoc parsing and validation of URLs_ :  
  
>• You can embed credentials in a URL before the hostname, using the `@` character.  
>>For example: `https://expected-host``@``evil-host`.  

>• You can use the `#` character to indicate a URL fragment.  
>>For example: `https://evil-host``#``expected-host`.  

>• You can leverage the DNS naming hierarchy to place required input into a fully-qualified DNS name that you control.  
>>For example: `https://expected-host.evil-host`.  

>• You can _URL-encode characters to confuse the URL-parsing code_.  
>>This is particularly useful if the code that implements the filter handles URL-encoded characters differently than the code that performs the back-end HTTP request.  
  
>• You can use combinations of these techniques together.  
  
  
  <br><br>
>LAB [SSRF with whitelist-based input filter](https://portswigger.net/web-security/ssrf/lab-ssrf-with-whitelist-filter)  
  
  

>>##### Read more : [A new era of SSRF](https://portswigger.net/blog/top-10-web-hacking-techniques-of-2017#1)