## Finding hidden attack surface for SSRF vulnerabilities

  
Many server-side request forgery vulnerabilities are relatively easy to spot, because the application's normal traffic involves request parameters containing full URLs. Other examples of SSRF are harder to locate.  
  
### Partial URLs in requests

Sometimes, an application places only a hostname or part of a URL path into request parameters. The value submitted is then incorporated server-side into a full URL that is requested. If the value is readily recognized as a hostname or URL path, then the potential attack surface might be obvious.  
>However, exploitability as full SSRF might be limited since you do not control the entire URL that gets requested.  
  
  

### URLs within data formats
  
_Some applications transmit data in formats whose specification allows the inclusion of URLs that might get requested by the data parser for the format._ An obvious example of this is the XML data format, which has been widely used in web applications to transmit structured data from the client to the server. 
>_**When an application accepts data in XML format and parses it, it might be vulnerable to [XXE injection](https://portswigger.net/web-security/xxe), and in turn be vulnerable to SSRF via XXE.**_ 

We'll cover this in more detail when we look at [XXE injection](https://portswigger.net/web-security/xxe) vulnerabilities.  
  
  

### SSRF via the Referer header

Some applications employ server-side analytics software that tracks visitors. This software often logs the Referer header in requests, since this is of particular interest for tracking incoming links. Often the analytics software will actually visit any third-party URL that appears in the Referer header. This is typically done to analyze the contents of referring sites, including the anchor text that is used in the incoming links. As a result, the Referer header often represents fruitful attack surface for SSRF vulnerabilities. See [Blind SSRF vulnerabilities](https://portswigger.net/web-security/ssrf/blind) for examples of vulnerabilities involving the Referer header.  
  
  
  

>##### Read more : [Cracking the lens: Targeting auxiliary systems](https://portswigger.net/blog/cracking-the-lens-targeting-https-hidden-attack-surface#aux)