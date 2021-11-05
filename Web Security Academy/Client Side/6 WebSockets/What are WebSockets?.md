Parent Links : [[WebSockets]]

# What are WebSockets?

[WebSockets](https://portswigger.net/web-security/websockets) are a bi-directional, full duplex communications protocol initiated over HTTP. They are commonly used in modern web applications for streaming data and other asynchronous traffic.

In this section, we'll explain the difference between HTTP and WebSockets, describe how WebSocket connections are established, and outline what WebSocket messages look like.

## What is the difference between HTTP and WebSockets?

Most communication between web browsers and web sites uses HTTP. With HTTP, the client sends a request and the server returns a response. Typically, the response occurs immediately, and the transaction is complete. Even if the network connection stays open, this will be used for a separate transaction of a request and a response.

Some modern web sites use WebSockets. WebSocket connections are initiated over HTTP and are typically long-lived. Messages can be sent in either direction at any time and are not transactional in nature. The connection will normally stay open and idle until either the client or the server is ready to send a message.

WebSockets are particularly useful in situations where low-latency or server-initiated messages are required, such as real-time feeds of financial data.

## How are WebSocket connections established?

WebSocket connections are normally created using client-side JavaScript like the following:

>`var ws = new WebSocket("wss://normal-website.com/chat");`

>#### Note
>
The `wss` protocol establishes a WebSocket over an encrypted TLS connection, while the `ws` protocol uses an unencrypted connection.

To establish the connection, the browser and server perform a WebSocket handshake over HTTP. The browser issues a WebSocket handshake request like the following:

```http 
GET /chat HTTP/1.1  
Host: normal-website.com  
Sec-WebSocket-Version: 13  
Sec-WebSocket-Key: wDqumtseNBJdhkihL6PW7w==  
Connection: keep-alive, Upgrade  
Cookie: session=KOsEJNuflw4Rd9BDNrVmvwBF9rEijeE2  
Upgrade: websocket
```

If the server accepts the connection, it returns a WebSocket handshake response like the following:

```http 
HTTP/1.1 101 Switching Protocols  
Connection: Upgrade  
Upgrade: websocket  
Sec-WebSocket-Accept: 0FFP+2nmNIf/h+4BP36k9uzrYGk=
```

At this point, the network connection remains open and can be used to send WebSocket messages in either direction.

>#### Note
>
Several features of the WebSocket handshake messages are worth noting:
>
>-   The `Connection` and `Upgrade` headers in the request and response indicate that this is a WebSocket handshake.
>-   The `Sec-WebSocket-Version` request header specifies the WebSocket protocol version that the client wishes to use. This is typically `13`.
>-   The `Sec-WebSocket-Key` request header contains a Base64-encoded random value, which should be randomly generated in each handshake request.
>-   The `Sec-WebSocket-Accept` response header contains a hash of the value submitted in the `Sec-WebSocket-Key` request header, concatenated with a specific string defined in the protocol specification. This is done to prevent misleading responses resulting from misconfigured servers or caching proxies.

## What do WebSocket messages look like?

Once a WebSocket connection has been established, messages can be sent asynchronously in either direction by the client or server.

A simple message could be sent from the browser using client-side JavaScript like the following:

>`ws.send("Peter Wiener");`

In principle, WebSocket messages can contain any content or data format. In modern applications, it is common for JSON to be used to send structured data within WebSocket messages.

For example, a chat-bot application using WebSockets might send a message like the following:

```json 
{
"user":"Hal Pline",
"content":"I wanted to be a Playstation growing up, not a device to answer your inane questions"
}
```