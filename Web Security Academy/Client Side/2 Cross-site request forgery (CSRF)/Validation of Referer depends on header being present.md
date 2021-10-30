Parent Links : [[Cross-site request forgery (CSRF)]] > [[Common CSRF vulnerabilities]] > [[Referer-based defenses against CSRF]]     

### Validation of Referer depends on header being present
  
Some applications validate the [[Referer-based defenses against CSRF#Referer header | Referer header]] when it is present in requests but skip the validation if the header is omitted.  
In this situation, an attacker can craft their CSRF exploit in a way that causes the victim user's browser to drop the `Referer` header in the resulting request. There are various ways to achieve this, but the easiest is using a META tag within the HTML page that hosts the CSRF attack:  
	`<meta name="referrer" content="never">`  
	
>LAB [CSRF where Referer validation depends on header being present](https://portswigger.net/web-security/csrf/lab-referer-validation-depends-on-header-being-present)