Parent Links : [[Cross-site scripting]] > [[How to prevent XSS attacks]]     

## How to prevent XSS using a template engine
  
Many modern websites use server-side template engines such as Twig and Freemarker to embed dynamic content in HTML. These typically define their own escaping system.  
  
For example, in Twig, you can use the `e()` filter, with an argument defining the context:  
`{{ user.firstname | e('html') }}`  
Some other template engines, such as Jinja and React, escape dynamic content by default which effectively prevents most occurrences of XSS.  
We recommend reviewing escaping features closely when you evaluate whether to use a given template engine or framework.  
  
  

##### Note

If you directly concatenate user input into template strings, you will be vulnerable to [server-side template injection](https://portswigger.net/kb/issues/00101080_server-side-template-injection) which is often more serious than XSS.