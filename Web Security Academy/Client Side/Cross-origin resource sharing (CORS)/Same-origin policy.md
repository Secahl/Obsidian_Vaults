Parent Links : [[Cross-origin resource sharing (CORS)#Same-origin policy | CORS > SOP]]

# Same-origin policy (SOP)

## What is the same-origin policy?

The same-origin policy is a web browser security mechanism that aims to prevent websites from attacking each other.

The same-origin policy restricts scripts on one origin from accessing data from another origin. An origin consists of a URI scheme, domain and port number. For example, consider the following URL:

>`http://normal-website.com/example/example.html`

This uses the scheme `http`, the domain `normal-website.com`, and the port number `80`. The following table shows how the same-origin policy will be applied if content at the above URL tries to access other origins:

URL accessed  | Access permitted?
--|--
`http://normal-website.com/example/` | Yes: same scheme, domain, and port
`http://normal-website.com/example2/` | Yes: same scheme, domain, and port
`https://normal-website.com/example/` | No: different scheme and port
`http://en.normal-website.com/example/` | No: different domain
`http://www.normal-website.com/example/` | No: different domain
`http://normal-website.com:8080/example/` | No: different port*

*Internet Explorer will allow this access because IE does not take account of the port number when applying the same-origin policy.