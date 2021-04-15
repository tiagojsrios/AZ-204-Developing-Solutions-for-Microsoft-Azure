# SignalR

In contrast to polling, a more favorable design features persistent connections between the client and server. Establishing a persistent connection allows the server to push data to the client at will. The on-demand nature of the connection reduces network traffic and load on the server.

SignalR is an abstraction for a series of technologies that allows your app to enjoy two-way communication between the client and server. SignalR handles connection management automatically, and lets you broadcast messages to all connected clients simultaneously. You can also send messages to specific clients. The connection between the client and server is persistent, unlike a classic HTTP connection, which is re-established for each communication.

A key benefit of the abstraction provided by SignalR is the way it supports "transport" fallbacks. A transport is method of communicating between the client and server. SignalR connections begin with a standard HTTP request. As the server evaluates the connection, the most appropriate communication method (transport) is selected. Transports are chosen depending on the APIs available on the client.

For clients that support HTML 5, the WebSockets API transport is used by default. If the client doesn't support WebSockets, then SignalR falls back to Server Sent Events (also known as EventSource). For older clients, Ajax long polling or Forever Frame (IE only) is used to mimic a two-way connection.

The abstraction layer offered by SignalR provides two benefits to your application. The first advantage is future-proofing your app. As the web evolves and APIs superior to WebSockets become available, your application doesn't need to change.