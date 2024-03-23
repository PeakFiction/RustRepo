## Reflection Notes

### Milestone 1: Single Threaded Web Server

In this milestone, I took my first steps in creating a web server using Rust using the provided module as well as the website documentation. Here's what I did:

1. **Setting Up the Server**: I used Rust's standard library to set up a server that listens for incoming connections on a specific address and port. Which is like opening the doors of our server to welcome visitors.

2. **Welcoming Visitors**: With a loop, I basically greeted each visitor (client) who knocked on our server's door. Each visitor was represented by a connection to our server, called a `stream`.

3. **Understanding Visitor Requests**: We created a function called `handle_connection` to understand what each visitor wanted. We read his requests line by line to figure out things like which webpage he wanted to visit and what kind of browser he was using.

### Milestone 2: Serving HTML Pages

In this milestone, I made the server more interesting by sharing a simple web page with our visitors:

1. **Creating a Web Page**: I crafted a basic HTML page called `hello.html` with a friendly greeting. This page will be the first thing our visitors see when they come knocking.

2. **Serving Our Web Page**: I updated our server to send this HTML page to our visitors when they arrive. I learned about HTTP responses, including status lines and headers, to ensure our visitors' browsers understand our message.

3. **Learning about HTTP**: I delved into the world of HTTP, understanding how messages are structured and why headers like `Content-Length` are important. It was like learning the etiquette of the web.


### Milestone 3: Validating Request and Selectively Responding

In this milestone, I enhanced our web server to validate requests and selectively respond with different pages based on the request. Let's dive into the changes made and the reasons behind them:

1. **The Problem**: Previously, our server always responded with the `hello.html` page regardless of the request. Now, I want to differentiate between valid requests (e.g., requesting the homepage) and invalid requests (e.g., requesting a non-existent page).

2. **Splitting Responses**: I modified the `handle_connection` function to split the response based on the request received. If the request is for the homepage (`GET / HTTP/1.1`), I respond with the `hello.html` page and a status line indicating success (`HTTP/1.1 200 OK`). Otherwise, for any other request, I respond with a `404.html` page and a status line indicating that the requested page was not found (`HTTP/1.1 404 NOT FOUND`).

3. **Refactoring for Clarity**: The refactoring introduced in this milestone improves the clarity and maintainability of my code. By separating the response logic based on the request, I make it easier to understand and modify the behavior of our server in the future.

### Milestone 4: Simulation of Slow Request

In this milestone, I simulated slow responses in our web server to observe the impact of single-threaded execution on user experience. Let's delve into the changes made and their implications:

1. **Understanding the Problem**: My server operates on a single thread, meaning it can only handle one request at a time. To simulate the impact of this limitation, I introduced a delay of 10 seconds for requests to `/sleep`, mimicking slow response times.

2. **Implementation**: I modified the `handle_connection` function to introduce a sleep duration for requests to `/sleep`. This delay allows me to simulate scenarios where the server is occupied with processing a request, leading to slower responses for subsequent requests.

3. **Observing the Behavior**: By opening two browser windows and accessing `/sleep` in one and `/` in the other, I observed how the server responds differently based on the type of request. Requests to `/sleep` experienced a noticeable delay, while requests to `/` responded promptly

## Milestone 5: Multithreaded Server using ThreadPool

1. **Motivation for Improvement**: Recognizing the limitations of our single-threaded server, we were motivated to enhance its scalability and responsiveness by introducing multithreading. This allows our server to handle multiple requests concurrently, improving overall performance.

2. **Understanding ThreadPool**: We followed detailed instructions from the documentation website to implement a ThreadPool for our server. The ThreadPool manages a fixed number of worker threads, each responsible for handling incoming requests. This design optimizes resource utilization and prevents thread creation overhead.

3. **Exploring ThreadPool Implementation**: We delved into the inner workings of the ThreadPool to understand how it manages worker threads and distributes incoming tasks. By studying the code and documentation, we gained insights into concurrent programming paradigms and synchronization techniques in Rust.

4. **Observing Improved Performance**: With the multithreaded server in place, we observed significant improvements in response times and concurrency handling. Requests are distributed among worker threads, allowing our server to efficiently utilize available resources and serve multiple clients simultaneously.

5. **Scalability and Robustness**: The introduction of multithreading enhances the scalability and robustness of our server, enabling it to handle increased loads and concurrent requests more effectively. This lays a solid foundation for building high-performance web applications in Rust.

![image](https://github.com/PeakFiction/RustRepo/assets/112671939/4ea76dee-fb74-4f9a-928f-25c8f66b5942)

![image](https://github.com/PeakFiction/RustRepo/assets/112671939/bf2acaaa-5b02-4445-a012-2b315dd7f856)

![image](https://github.com/PeakFiction/RustRepo/assets/112671939/ef17b6b5-1e1c-497d-9d47-26d32b8d17e9)

![image](https://github.com/PeakFiction/RustRepo/assets/112671939/4b78c453-d285-426b-b56a-7f7c50a123f6)


###
