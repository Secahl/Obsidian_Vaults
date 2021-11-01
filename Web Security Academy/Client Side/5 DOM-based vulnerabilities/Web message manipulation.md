Parent Links : [[ClientSide]] > [[DOM-based vulnerabilities]]

# Web message manipulation

In this section, we'll explain what web-message manipulation vulnerabilities are and suggest ways to reduce your exposure to them.

## What is DOM-based [web message](https://portswigger.net/web-security/dom-based/controlling-the-web-message-source) manipulation?

Web message vulnerabilities arise when a script sends attacker-controllable data as a web message to another document within the browser. An attacker may be able to use the web message data as a source by constructing a web page that, if visited by a user, will cause the user's browser to send a web message containing data that is under the attacker's control. For more information about the using web messages as a source, please refer to the [[Web messages | Controlling the web-message source]] page.

## Which sinks can lead to DOM-based web-message manipulation vulnerabilities?

The `postMessage()` method for sending web messages can lead to vulnerabilities if the event listener for receiving messages handles the incoming data in an unsafe way.

## How to prevent DOM-based web message manipulation

In addition to the general measures described on the [[DOM-based vulnerabilities]] page, you should avoid sending web messages that contain data that originated from any untrusted source. When sending cross-origin messages, you should always explicitly specify the target window. Most importantly, make sure to implement robust measures to verify the origin of any incoming messages.