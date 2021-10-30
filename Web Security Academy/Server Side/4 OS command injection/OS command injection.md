## What is OS command injection?

  
OS command injection (_also known as shell injection_) is a web security vulnerability that allows an attacker to execute _**arbitrary operating system (OS) commands on the server that is running an application**_, and typically fully compromise the application and all its data.  
  
Very often, an attacker can leverage an OS command injection vulnerability to compromise other parts of the hosting infrastructure, exploiting trust relationships to pivot the attack to other systems within the organization.  
  
  
## Useful commands

  
  
When you have identified an OS command injection vulnerability, it is generally useful to execute some initial commands to obtain information about the system that you have compromised.  
  
Below is a summary of some commands that are useful on Linux and Windows platforms:  

><font color=darbrown>Purpose of command | <font color=darbrown>Linux | <font color=darbrown>Windows 
---|---|---
Name of current user | whoami | whoami
Operating system | uname -a | ver
Network configuration | ifconfig | ipconfig /all
Network connections | netstat -an | netstat -an
Running processes | ps -ef | tasklist

  
## Ways of injecting OS commands
  
A variety of shell metacharacters can be used to perform OS command injection attacks.  
  
A number of characters function as command separators, allowing commands to be chained together.  
  
The following command separators work on both Windows and Unix-based systems:  
>• `&`
• `&&`
• `|`
• `||`  
  
  
The following command separators work only on Unix-based systems:  

-
 `;`  
-
 Newline (`0x0a` or `\n`)  
  
  
  
On Unix-based systems, you can also use _**backticks**_ _or the_ _**dollar**_ _character to perform inline execution of an injected command_ within the original command:  

-
 `` ` `` injected command `` ` `` 
-
 `$(` injected command `)`  
  
  
  
Note that the different shell metacharacters have subtly different behaviors that might affect whether they work in certain situations, and whether they allow in-band retrieval of command output or are useful only for blind exploitation.  
  
**Sometimes, the input that you control appears within quotation marks in the original command.** In this situation, you _need to terminate the quoted context (using_ _`"`_ _or_ _`'`_) before using suitable shell metacharacters to inject a new command.
	
Linked Nodes :
	
	[[A > Executing arbitrary commands]]
	[[Blind OS command injection vulnerabilities]]
	[[C > How to prevent OS command injection attacks]]