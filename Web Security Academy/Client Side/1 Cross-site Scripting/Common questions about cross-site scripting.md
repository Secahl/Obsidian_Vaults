Parent Links : [[Cross-site scripting]]     

## Common questions about cross-site scripting
  
>- **How common are XSS vulnerabilities?** 
>XSS vulnerabilities are very common, and XSS is probably the most frequently occurring web security vulnerability.  
  
>- **How common are XSS attacks?** 
>It is difficult to get reliable data about real-world XSS attacks, but it is probably less frequently exploited than other vulnerabilities.  
  
>- **What is the difference between XSS and CSRF?** 
>XSS involves causing a web site to return malicious JavaScript, while CSRF involves inducing a victim user to perform actions they do not intend to do.  
  
>- **What is the difference between XSS and SQL injection?** 
>XSS is a client-side vulnerability that targets other application users, while SQL injection is a server-side vulnerability that targets the application's database.  

>- **How do I prevent XSS in PHP?** 
>Filter your inputs with a whitelist of allowed characters and use type hints or type casting. Escape your outputs with `htmlentities` and `ENT_QUOTES` for HTML contexts, or JavaScript Unicode escapes for JavaScript contexts.  
  
>- **How do I prevent XSS in Java?** 
>Filter your inputs with a whitelist of allowed characters and use a library such as Google Guava to HTML-encode your output for HTML contexts, or use JavaScript Unicode escapes for JavaScript contexts.