## Account locking

One way in which websites try to prevent brute-forcing is to lock the account if certain suspicious criteria are met, usually a set number of failed login attempts. Just as with normal login errors, responses from the server indicating that an account is locked can also help an attacker to enumerate usernames.  
  
Locking an account offers a certain amount of protection against targeted brute-forcing of a specific account. However, this approach fails to adequately prevent brute-force attacks in which the attacker is just trying to gain access to any random account they can.  
  
### Username enumeration via account lock

Example: -  
  
For wrong usernames, the response is `Invalid Username and Password` ,and  
For correct username, the response is `You have made too many incorrect login attempts`.