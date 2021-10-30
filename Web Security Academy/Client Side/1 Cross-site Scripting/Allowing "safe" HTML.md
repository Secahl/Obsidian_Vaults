Parent Links : [[Cross-site scripting]] > [[How to prevent XSS attacks]] > [[Validate input on arrival]]     

## Allowing "safe" HTML
  
Allowing users to post HTML markup should be avoided wherever possible, but sometimes it's a business requirement. For example, a blog site might allow comments to be posted containing some limited HTML markup.  
The classic approach is to try to filter out potentially harmful tags and JavaScript. You can try to implement this using a whitelist of safe tags and attributes, but thanks to discrepancies in browser parsing engines and quirks like mutation XSS, this approach is extremely difficult to implement securely.  
  
The least bad option is to use a JavaScript library that performs filtering and encoding in the user's browser, such as DOMPurify. Other libraries allow users to provide content in markdown format and convert the markdown into HTML. Unfortunately, all these libraries have XSS vulnerabilities from time to time, so this is not a perfect solution. If you do use one you should monitor closely for security updates.  
  
  

##### Note

In addition to JavaScript, other content such as CSS and even regular HTML can be harmful in some situations.  
[Attacks using malicious CSS](https://portswigger.net/research/detecting-and-exploiting-path-relative-stylesheet-import-prssi-vulnerabilities#badcss) 