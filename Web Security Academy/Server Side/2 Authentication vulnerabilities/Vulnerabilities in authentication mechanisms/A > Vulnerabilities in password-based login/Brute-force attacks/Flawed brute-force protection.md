## Flawed brute-force protection

The two most common ways of preventing brute-force attacks are:  
 
• Locking the account that the remote user is trying to access if they make too many failed login attempts  
• Blocking the remote user's IP address if they make too many login attempts in quick succession  
  
Both approaches offer varying degrees of protection, but _**neither is invulnerable, especially if implemented using flawed logic.**_  
  
For example, you might sometimes find that your IP is blocked if you fail to log in too many times.  

In some implementations, the counter for the number of failed attempts resets if the IP owner logs in successfully. This means an attacker would simply have to log in to their own account every few attempts to prevent this limit from ever being reached.  
  
In this case, merely including your own login credentials at regular intervals throughout the wordlist is enough to render this defense virtually useless.  
i.e. _creating a wordlist with username and password and including your correct login credential at a regular interval in order to reset the number of failed attempts thus preventing IP block._  
  
NOTE: _If websites accept_ _**X-Forwarded-Header**_ _then we can spoof the IP itself._