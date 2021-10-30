### XInclude attacks
  
Some applications receive client-submitted data, embed it on the server-side into an XML document, and then parse the document. An example of this occurs when client-submitted data is placed into a back-end SOAP request, which is then processed by the backend SOAP service.  
In this situation, you cannot carry out a classic XXE attack, because you don't control the entire XML document and so cannot define or modify a `DOCTYPE` element.  
_However, you might be able to use_ _`XInclude`_ _instead._  

>_`XInclude`_ _is a part of the XML specification that allows an XML document to be built from sub-documents._ 

You can place an `XInclude` attack within any data value in an XML document, so the attack can be performed in situations where you only control a single item of data that is placed into a server-side XML document.  
To perform an `XInclude` attack, you need to reference the `XInclude` namespace and provide the path to the file that you wish to include.  
  
For example:  
  
```xml 
<foo xmlns:xi="http://www.w3.org/2001/XInclude">  
<xi:include parse="text" href="file:///etc/passwd"/></foo>
```
  
  
>LAB [Exploiting XInclude to retrieve files](https://portswigger.net/web-security/xxe/lab-xinclude-attack)