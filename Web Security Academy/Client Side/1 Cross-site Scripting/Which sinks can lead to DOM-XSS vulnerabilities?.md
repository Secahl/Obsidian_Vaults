Parent Links : [[Cross-site scripting]] > [[What are the types of XSS attacks?]] > [[DOM-based XSS]]     

## Which sinks can lead to DOM-XSS vulnerabilities?

The following are some of the main sinks that can lead to DOM-XSS vulnerabilities :  
  
	- document.write() 
	- document.writeln()  
	- document.domain  
	- element.innerHTML  
	- element.outerHTML  
	- element.insertAdjacentHTML  
	- element.onevent 

---

The following jQuery functions are also sinks that can lead to DOM-XSS vulnerabilities :  
  
	- add()  
	- after()  
	- append()  
	- animate()  
	- insertAfter()  
	- insertBefore()  
	- before()  
	- html()  
	- prepend()  
	- replaceAll()  
	- replaceWith()  
	- wrap()  
	- wrapInner()  
	- wrapAll()  
	- has()  
	- constructor()  
	- init()  
	- index()  
	- jQuery.parseHTML()  
	- $.parseHTML()