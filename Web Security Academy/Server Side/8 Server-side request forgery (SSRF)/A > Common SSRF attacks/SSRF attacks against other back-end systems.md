### SSRF attacks against other back-end systems
  
Another type of trust relationship that often arises with server-side request forgery is where the _application server is able to interact with other back-end systems_ that are not directly reachable by users.  
  
*These systems often have non-routable private IP addresses.  *
  
Since the back-end systems are normally protected by the network topology, they often have a weaker security posture.  
  
In many cases, internal back-end systems contain sensitive functionality that can be accessed without authentication by anyone who is able to interact with the systems.  
  
In the preceding example, suppose there is an administrative interface at the back-end URL 
>`https://192.168.0.68/admin`  

Here, an attacker can exploit the SSRF vulnerability to access the administrative interface by submitting the following request:  
  
```http POST /product/stock HTTP/1.0  
Content-Type: application/x-www-form-urlencoded  
Content-Length: 118  
  
stockApi=http://192.168.0.68/admin
```  
  
  
>LAB [Basic SSRF against another back-end system](https://portswigger.net/web-security/ssrf/lab-basic-ssrf-against-backend-system)