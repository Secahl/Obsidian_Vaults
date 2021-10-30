## How does OAuth 2.0 work?
  
OAuth 2.0 was originally developed as a way of sharing access to specific data between applications.  
It works by defining a series of _interactions between three distinct parties, namely a_ _client application, a resource owner, and the OAuth service provider._  
  
>• **Client application** - The website or web application that wants to access the user's data.  
• **Resource owner** - The user whose data the client application wants to access.
• **OAuth service provider** - The website or application that controls the user's data and access to it. They support OAuth by providing an _API for interacting with both an authorization server and a resource server._  
  
There are numerous different ways that the actual OAuth process can be implemented.  
_**These are known as OAuth "flows" or "grant types".**_  
  
In this topic, we'll focus on the _**"authorization code" and "implicit" grant types**_ as these are by far the most common.  
  
  
  
** Broadly speaking, both of these grant types involve the following stages:  **
  
>1. The client application requests access to a subset of the user's data, specifying which grant type they want to use and what kind of access they want.  
  
>2. The user is prompted to log in to the OAuth service and explicitly give their consent for the requested access.  
  
>3. The client application receives a unique access token that proves they have permission from the user to access the requested data. Exactly how this happens varies significantly depending on the grant type.  
  
>4. The client application uses this access token to make API calls fetching the relevant data from the resource server.  
  
  
  
Before learning how OAuth is used for authentication, it's important to understand the fundamentals of this basic OAuth process.  
If you're completely new to OAuth, we recommend familiarizing yourself with the details of both of the grant types we're going to cover before reading further.  
  
  

>### Read more: [OAuth grant types](https://portswigger.net/web-security/oauth/grant-types)