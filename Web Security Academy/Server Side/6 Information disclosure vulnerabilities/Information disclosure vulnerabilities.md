## What is information disclosure?

Information disclosure, also known as information leakage, is when a website unintentionally reveals sensitive information to its users.  
  
Depending on the context, websites may leak all kinds of information to a potential attacker, including:  
>• Data about other users, such as usernames or financial information  
• Sensitive commercial or business data  
• Technical details about the website and its infrastructure  

### What are some examples of information disclosure?

Some basic examples of information disclosure are as follows:  
>• Revealing the names of hidden directories, their structure, and their contents via a `robots.txt` file or directory listing  
• Providing access to source code files via temporary backups  
• Explicitly mentioning database table or column names in error messages  
• Unnecessarily exposing highly sensitive information, such as credit card details  
• Hard-coding API keys, IP addresses, database credentials, and so on in the source code  
• Hinting at the existence or absence of resources, usernames, and so on via subtle differences in application behavior  
  

## How do information disclosure vulnerabilities arise?

Information disclosure vulnerabilities can arise in countless different ways, but these can broadly be categorized as follows:  
  
• **Failure to remove internal content from public content**.  
>For example, developer comments in markup are sometimes visible to users in the production environment.  
  
• **Insecure configuration of the website and related technologies**.  
 >For example, failing to disable debugging and diagnostic features can sometimes provide attackers with useful tools to help them obtain sensitive information. Default configurations can also leave websites vulnerable, for example, by displaying overly verbose error messages.  
  
• **Flawed design and behavior of the application**.  
>For example, if a website returns distinct responses when different error states occur, this can also allow attackers to [enumerate sensitive data](https://portswigger.net/web-security/authentication/password-based#username-enumeration), such as valid user credentials.  
  
  
## What is the impact of information disclosure vulnerabilities?

Information disclosure vulnerabilities can have _both a_ _direct and indirect impact_ depending on the purpose of the website and, therefore, what information an attacker is able to obtain.  
  
In some cases, the act of disclosing sensitive information alone can have a high impact on the affected parties.  
  
**For example**, an online shop leaking its customers' credit card details is likely to have severe consequences. 
  
  
**On the other hand**, leaking technical information, such as the _directory structure_ or which _third-party frameworks_ are being used, may have little to no direct impact.  
However, in the wrong hands, this could be the key information required to construct any number of other exploits.  
_The severity in this case depends on what the attacker is able to do with this information._

Linked Nodes :

[[A > How to assess the severity of information disclosure vulnerabilities]]
[[Finding & Exploiting information disclosure]]

