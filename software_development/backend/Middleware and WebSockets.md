### Middleware

**Middleware** is a function or a set of functions that runs between the server receiving a request and sending a response. Middleware functions can execute any code, make changes to the request and the outgoing response, end the request-response cycle, and call the next middleware function in the stack.

#### Why use middleware?

- **Session Management**: Handling user sessions, such as login states or user-specific data storage.
- **Authentication and Authorization**: Checking if a user is logged in and if they have permission to access certain routes or resources.
- **Logging and Monitoring**: Recording data about requests and responses for debugging or analysis.
- **Data Processing**: Modifying request data before it reaches the application logic, like parsing cookies or formatting incoming data.

#### How it works

Middleware functions are typically defined in a sequence within the application's request-handling pipeline. Each middleware can either pass the request to the next middleware or complete the request-response cycle. This allows you to layer your application with various functionalities that process the HTTP requests and responses systematically.

### WebSockets

**WebSockets** provide a way to open an interactive communication session between a user's browser and a server. With WebSockets, you can send messages to a server and receive event-driven responses without having to poll the server for a reply.

#### Why use WebSockets?

- **Real-Time Data**: Ideal for applications that require real-time data flow, such as live chat applications, real-time notifications, and online gaming.
- **Efficient Communication**: Reduces the overhead of HTTP connections by maintaining a persistent connection where both parties can start sending data at any time.

#### How they work

The WebSocket protocol facilitates continuous data exchange between client and server after a WebSocket connection is established over a single, long-lived connection. It starts with a handshake via HTTP, upgrading the connection to a WebSocket connection which then remains open for real-time, bi-directional communication.