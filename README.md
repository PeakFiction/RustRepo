## Reflection Notes

### Milestone 1: Single-threaded Web Server

In this milestone, I implemented a basic single-threaded web server in Rust. Let's break down the key points:

1. **Setting up a TCP Listener**: We utilize Rust's standard library (`std::net::TcpListener`) to bind the server to a specific address and port (`127.0.0.1:7878` in this case). This allows our server to listen for incoming TCP connections.

2. **Handling Incoming Connections**: Using a `for` loop over `listener.incoming()`, we accept incoming connections from clients. Each accepted connection (`stream`) represents a client connection to our server.

3. **Handling Connection Requests**: To handle incoming requests from clients, we introduced a `handle_connection` function. This function takes a mutable reference to a `TcpStream` and reads the incoming request line by line using a `BufReader`. The request lines are collected into a `Vec<String>` named `http_request`, which represents the HTTP request sent by the client.

4. **Understanding HTTP Requests**: The `handle_connection` function provides insight into the structure of HTTP requests. Each line of the HTTP request is represented as a string in the `http_request` vector. The first line typically contains the HTTP method, requested path, and HTTP version, while subsequent lines contain headers such as `Host`, `User-Agent`, `Accept`, and others.

5. **Reflection and Learning**: This milestone prompts further exploration into Rust documentation to understand the details of handling TCP connections and parsing HTTP requests. It encourages deeper comprehension of network programming concepts and Rust's standard library functionalities.

Overall, this milestone serves as an introductory step towards building a functional web server in Rust. Further enhancements, such as adding concurrency for handling multiple client connections simultaneously, will be explored in subsequent milestones.
