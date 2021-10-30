### Detecting blind OS command injection using time delays

You can use an injected command that will trigger a time delay, allowing you to confirm that the command was executed based on the time that the application takes to respond.  
  
  
The `ping` command is an effective way to do this, as it lets you _specify the number of_ _ICMP packets_ _to send_, and therefore the time taken for the command to run:  
>`& ping -c 10 127.0.0.1 &`  
  
  
This command will cause the application to _ping its loopback network adapter_ for 10 seconds.  
  
  
>LAB [Blind OS command injection with time delays](https://portswigger.net/web-security/os-command-injection/lab-blind-time-delays)  
  
>>e.g:  name=x&email=x||ping+-c+10+127.0.0.1||&subject=x&message=x 
  
>Note: Also works without using +