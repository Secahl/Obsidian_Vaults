## Executing arbitrary commands
  
Consider a shopping application that lets the user view whether an item is in stock in a particular store.  
  
This information is accessed via a URL like:  
>`https://insecure-website.com/stockStatus?productID=381&storeID=29`

To provide the stock information, the application must query various legacy systems.  
  
For historical reasons, the functionality is implemented by calling out to a shell command with the product and store IDs as arguments:  
>`stockreport.pl 381 29`  
  
This command outputs the stock status for the specified item, which is returned to the user.  
  
  
Since the application implements no defenses against OS command injection, an attacker can submit the following input to execute an arbitrary command:  
>`& echo aiwefwlguh &`  
  
If this input is submitted in the `productID` parameter, then the command executed by the application is:  
>`stockreport.pl & echo aiwefwlguh & 29`  
  
  
The `echo` command simply causes the supplied string to be echoed in the output, and is _a useful way to test for some types of OS command injection._  
  
The _**`&`**_ _**character is a shell command separator**_, and so what gets executed is actually three separate commands one after another.  
As a result, the output returned to the user is:  
>Error - productID was not provided 
 aiwefwlguh 
29: command not found

  
  
The three lines of output demonstrate that:  
>• The original `stockreport.pl` command was executed without its expected arguments, and so returned an error message.
• The injected `echo` command was executed, and the supplied string was echoed in the output.
• The original argument `29` was executed as a command, which caused an error.  
  
Placing the additional command separator `&` after the injected command is generally useful because _it separates the injected command from whatever follows the injection point._  
e.g `productId=1&storeId=1|whoami`

This reduces the likelihood that what follows will prevent the injected command from executing.  
  
  
>LAB [OS command injection, simple case](https://portswigger.net/web-security/os-command-injection/lab-simple)  
  
