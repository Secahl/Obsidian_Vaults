# Directory traversal

In this section, we'll explain what directory traversal is, describe how to carry out path traversal attacks and circumvent common obstacles, and spell out how to prevent path traversal vulnerabilities.  
[![file:///tmp/.N6XWB1/1.png](file:///tmp/.N6XWB1/1.png)](https://portswigger.net/web-security/images/directory-traversal.svg)  
  
  
## What is directory traversal?

Directory traversal (_also known as file path traversal_) is a web security vulnerability that _allows an attacker to read arbitrary files on the server that is running an application._  
  
This might include application code and data, credentials for back-end systems, and sensitive operating system files.  
In some cases, an attacker might be able to write to arbitrary files on the server, allowing them to modify application data or behavior, and ultimately take full control of the server.



Linked Nodes : 

[[Reading arbitrary files via directory traversal]]
[[Common obstacles to exploiting file path traversal vulnerabilities]]
[[How to prevent a directory traversal attack]]