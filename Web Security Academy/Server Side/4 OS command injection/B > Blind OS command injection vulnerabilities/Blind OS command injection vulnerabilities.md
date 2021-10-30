 ## Blind OS command injection vulnerabilities
  
Many instances of OS command injection are blind vulnerabilities.  
This means that the application _does not return the output from the command_ within its HTTP response.  
  
Blind vulnerabilities can still be exploited, but different techniques are required.  
Consider a web site that lets users submit feedback about the site.  
The user enters their email address and feedback message.  
The server-side application then generates an email to a site administrator containing the feedback.  
  
To do this, it calls out to the `mail` program with the submitted details.  
For example:  
>`mail -s "This site is great" -a From:peter@normal-user.net feedback@vulnerable-website.com`  
  
  
The output from the `mail` command (if any) is not returned in the application's responses, and _**so using the**_ _**`echo`**_ _**payload would not be effective.**_  
  
In this situation, you can use a variety of other techniques to detect and exploit a vulnerability.  
  
 Such are as follows :  
  
[[Detecting blind OS command injection using time delays]]
[[Exploiting blind OS command injection by redirecting output]]
[[Exploiting blind OS command injection using out-of-band (OAST) techniques]]