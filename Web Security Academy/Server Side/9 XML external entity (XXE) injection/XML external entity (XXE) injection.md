 # XML external entity (XXE) injection


In this section, we'll explain what XML external entity injection is, describe some common examples, explain how to find and exploit various kinds of XXE injection, and summarize how to prevent XXE injection attacks.  
  
  

## What is XML external entity injection?

XML external entity injection (also known as XXE) is a web security vulnerability that allows an attacker to interfere with an application's processing of XML data. It often allows an attacker to view files on the application server filesystem, and to interact with any back-end or external systems that the application itself can access.  
In some situations, an attacker can escalate an XXE attack to compromise the underlying server or other back-end infrastructure, by leveraging the XXE vulnerability to perform [[Server-side request forgery (SSRF)#Server-side request forgery SSRF | SSRF]]  attacks. 

[![file:///tmp/.35TLB1/1.png](file:///tmp/.35TLB1/1.png)](https://portswigger.net/web-security/images/xxe-injection.svg)  
  
  <br> 

## How do XXE vulnerabilities arise?

Some applications use the XML format to transmit data between the browser and the server. Applications that do this virtually always use a standard library or platform API to process the XML data on the server. XXE vulnerabilities arise because the XML specification contains various potentially dangerous features, and standard parsers support these features even if they are not normally used by the application.  
  
  

>##### Read more : [[A > XML entities#XML entities| Learn about the XML format, DTDs, and external entities]]  
  
>_XML external entities are a type of custom XML entity whose defined values are loaded from outside of the_ _DTD(document type definition)_ _in which they are declared._  
>>External entities are particularly interesting from a security perspective because `they allow an entity to be defined based on the contents of a file path or URL`.  
  
  <br>

**NOTE**  :
>_** ``&``** xxe is an external entity and **`%`** xxe is a parameter entity._


Linked Nodes :

[[A > XML entities]]
[[What are the types of XXE attacks?]]
[[Finding hidden attack surface for XXE injection]]
[[D > How to find and test for XXE vulnerabilities]]
[[E > How to prevent XXE vulnerabilities]]