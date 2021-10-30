 Parent Links : [[Cross-site scripting]] > [[What are the types of XSS attacks?]] > [[Stored XSS]]
 
## How to find and test for stored XSS vulnerabilities
  
Many stored XSS vulnerabilities can be found using Burp Suite's [web vulnerability scanner](https://portswigger.net/burp/vulnerability-scanner).  
Testing for stored XSS vulnerabilities manually can be challenging. You need to test all relevant "entry points" via which attacker-controllable data can enter the application's processing, and all "exit points" at which that data might appear in the application's responses.  
  
Entry points into the application's processing include:  
 >
• Parameters or other data within the URL query string and message body.  
• The URL file path.  
• HTTP request headers that might not be exploitable in relation to [[Reflected XSS]]
• Any out-of-band routes via which an attacker can deliver data into the application. The routes that exist depend entirely on the functionality implemented by the application: a webmail application will process data received in emails; an application displaying a Twitter feed might process data contained in third-party tweets; and a news aggregator will include data originating on other web sites.  
  
  
The exit points for stored XSS attacks are all possible HTTP responses that are returned to any kind of application user in any situation.  
The first step in testing for stored XSS vulnerabilities is to locate the links between entry and exit points, whereby data submitted to an entry point is emitted from an exit point.  
  
The reasons why this can be challenging are that:  
 >
◇ Data submitted to any entry point could in principle be emitted from any exit point. For example, user-supplied display names could appear within an obscure audit log that is only visible to some application users.  
◇ Data that is currently stored by the application is often vulnerable to being overwritten due to other actions performed within the application. For example, a search function might display a list of recent searches, which are quickly replaced as users perform other searches.  
  
To comprehensively identify links between entry and exit points would involve testing each permutation separately, submitting a specific value into the entry point, navigating directly to the exit point, and determining whether the value appears there.  
However, this approach is not practical in an application with more than a few pages.  
  
Instead, a more realistic approach is to work systematically through the data entry points, submitting a specific value into each one, and monitoring the application's responses to detect cases where the submitted value appears. Particular attention can be paid to relevant application functions, such as comments on blog posts. When the submitted value is observed in a response, you need to determine whether the data is indeed being stored across different requests, as opposed to being simply reflected in the immediate response.  
  
When you have identified links between entry and exit points in the application's processing, each link needs to be specifically tested to detect if a stored XSS vulnerability is present. This involves determining the context within the response where the stored data appears and testing suitable candidate XSS payloads that are applicable to that context. At this point, the testing methodology is broadly the same as for finding [[How to find and test for reflected XSS vulnerabilities | reflected XSS vulnerabilites]]