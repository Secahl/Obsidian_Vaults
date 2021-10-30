Parent Links : [[Cross-site scripting]] > [[What are the types of XSS attacks?]] > [[DOM-based XSS]] > [[How to test for DOM-based cross-site scripting]] 

### Testing HTML sinks		

To test for DOM XSS in an HTML sink, place a random alphanumeric string into the source (such as `location.search`), then use developer tools to inspect the HTML and find where your string appears.  
_Note that the browser's "View source" option won't work for DOM XSS testing because it doesn't take account of changes that have been performed in the HTML by JavaScript._  
In Chrome's developer tools, you can use `Control+F` (or `Command+F` on MacOS) to search the DOM for your string.  
  
For each location where your string appears within the DOM, you need to identify the context. Based on this context, you need to refine your input to see how it is processed. For example, if your string appears within a double-quoted attribute then try to inject double quotes in your string to see if you can break out of the attribute.  
  
_Note that browsers behave differently with regards to URL-encoding, Chrome, Firefox, and Safari will URL-encode_ _`location.search`_ _and_ _`location.hash`__, while IE11 and Microsoft Edge (pre-Chromium) will not URL-encode these sources. If your data gets URL-encoded before being processed, then an XSS attack is unlikely to work._


#testingHTMLSinksinDOM