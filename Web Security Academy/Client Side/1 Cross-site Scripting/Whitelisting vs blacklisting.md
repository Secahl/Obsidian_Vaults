Parent Links : [[Cross-site scripting]] > [[How to prevent XSS attacks]] > [[Validate input on arrival]]     

### Whitelisting vs blacklisting
  
Input validation should generally employ whitelists rather than blacklists.  
  
For example, instead of trying to make a list of all harmful protocols (`javascript`, `data`, etc.), simply make a list of safe protocols (HTTP, HTTPS) and disallow anything not on the list. This will ensure your defense doesn't break when new harmful protocols appear and make it less susceptible to attacks that seek to obfuscate invalid values to evade a blacklist.