 ## How to prevent a directory traversal attack
  
The most effective way to prevent file path traversal vulnerabilities is to _avoid passing user-supplied input to filesystem APIs altogether._  
  
Many application functions that do this can be rewritten to deliver the same behavior in a safer way.  
  
  
**If it is considered unavoidable to pass user-supplied input to filesystem APIs,  
then two layers of defense should be used together to prevent attacks**:  
  
>• The application should validate the user input before processing it. Ideally, the validation should compare against a whitelist of permitted values. If that isn't possible for the required functionality, then the validation should verify that the input contains only permitted content, such as purely alphanumeric characters.  
  
>• After validating the supplied input, the application should append the input to the base directory and use a platform filesystem API to canonicalize the path. It should verify that the canonicalized path starts with the expected base directory.  
  
  
  <br>
  <br>
  
Below is an example of some simple Java code to validate the canonical path of a file based on user input :

```js 
File file = new File(BASE_DIRECTORY, userInput);  
             if (file.getCanonicalPath().startsWith(BASE_DIRECTORY)) {  
                 // process file  
                }
```