Resiliency patterns are design concepts used to build robust and fault-tolerant systems that can withstand failures, errors, and unexpected events. These patterns help ensure system availability, reliability, and performance, even in the face of adversity.

## Technical Content
Resiliency patterns can be categorized into several types, each addressing specific challenges and scenarios. The following are nine key resiliency patterns:

### 1. Circuit Breaker
The circuit breaker pattern acts like an electrical circuit breaker, tripping when a service experiences repeated failures and stopping requests to that service for a period of time. This allows the failing service to recover without being overwhelmed. A circuit breaker has three main states:
* **Closed**: Requests are allowed to pass through.
* **Open**: Requests are immediately rejected with an error.
* **Half-Open**: A limited number of requests are allowed to test if the service is recovered.

Example: In a microservices architecture, a circuit breaker can be used to detect and prevent cascading failures when one service depends on another.

### 2. Retry
The retry pattern involves automatically retrying a failed request a certain number of times before giving up. This can help overcome transient errors like network glitches or temporary unavailability. However, it's essential to implement exponential backoff to avoid retry storms that could overload the system.

Example: When a user submits a form, the application can retry the submission a few times if it fails due to a temporary network issue.

### 3. Timeout
The timeout pattern sets a maximum time limit for a request. If a response is not received within the timeout period, the request is considered a failure. Timeouts help prevent indefinite waits and allow the system to recover from slow or unresponsive services.

Example: In a web application, setting a timeout for API calls ensures that the user interface remains responsive even if the backend service is slow or down.

### 4. Bulkhead
The bulkhead pattern isolates different parts of an application into pools or compartments. This isolation limits the impact of failures or overload in one compartment, preventing it from affecting the entire system. Bulkheads are particularly useful in distributed systems where multiple services interact.

Example: In a cloud-based e-commerce platform, each service (e.g., order processing, inventory management) can be isolated in its own bulkhead to prevent a failure in one service from bringing down the entire system.

### 5. Rate Limiting
Rate limiting controls the rate of incoming requests to protect a system from being overwhelmed. This pattern helps prevent denial-of-service attacks, ensures fair usage, and maintains system stability. Rate limits can be applied at various levels, including IP addresses, user accounts, or APIs.

Example: A web application can implement rate limiting on login attempts to prevent brute-force attacks and ensure that legitimate users are not locked out due to excessive failed login attempts from a single IP address.

### 6. Fallback
The fallback pattern provides an alternative (often less ideal) response or action when the primary one fails. This improves system availability and user experience by providing some level of service even when the primary function is unavailable.

Example: In a video streaming service, if the primary high-definition stream fails, the application can fall back to a lower definition stream or even an audio-only stream to ensure that the user experiences some level of service continuity.

### 7. Hedging (Redundancy)
The hedging pattern sends duplicate requests to multiple identical services and uses the fastest response. This mitigates the impact of slow responses and failures, improving system responsiveness. Hedging is particularly useful in real-time systems or those requiring low latency.

Example: In a financial trading platform, critical transactions can be hedged across multiple servers to ensure that at least one transaction completes quickly and reliably.

### 8. Load Shedding
Load shedding drops non-critical requests when a system is overloaded to protect its core functionality. This helps maintain system stability and availability during peak loads or when the system is under attack.

Example: During a flash sale, an e-commerce platform can shed load by temporarily disabling non-essential features (e.g., product recommendations) to ensure that critical functions like checkout remain operational.

### 9. Backpressure
Backpressure involves a feedback loop between the producer (sending data) and the consumer (receiving data), allowing the producer to adjust its output rate dynamically based on the consumer's capacity. This pattern helps prevent overloading and ensures smooth data flow.

Example: In a real-time analytics system, backpressure can be used to regulate the flow of data from sensors or logs to the processing engine, preventing it from becoming overwhelmed during peak data ingestion periods.

## Key Takeaways and Best Practices
- **Implement circuit breakers** to prevent cascading failures in distributed systems.
- **Use retry mechanisms** with exponential backoff to handle transient errors.
- **Set appropriate timeouts** to avoid indefinite waits and ensure system responsiveness.
- **Isolate components** using bulkheads to limit the impact of failures.
- **Apply rate limiting** to protect against overload and denial-of-service attacks.
- **Provide fallback options** for improved user experience during service outages.
- **Hedge critical requests** for enhanced reliability and responsiveness.
- **Shed non-critical load** during peak periods or under attack to maintain core functionality.
- **Implement backpressure** to regulate data flow and prevent overloading.

## References
For further reading on system design and architecture patterns, including resiliency patterns, refer to resources like "Designing Data-Intensive Applications" by Martin Kleppmann and "System Design Primer" by Donne Martin. Tools and technologies such as Netflix's Hystrix for circuit breakers, Apache Kafka for backpressure, and AWS API Gateway for rate limiting can be explored for practical implementation of these patterns.
## Source

- Original Tweet: [https://twitter.com/i/web/status/1883731027442778402](https://twitter.com/i/web/status/1883731027442778402)
- Date: 2025-02-25 22:43:14


## Media

### Media 1
![media_0](./media_0.jpg)
**Description:** The infographic, titled "9 Resiliency Patterns," presents a comprehensive overview of various resiliency patterns. The title is prominently displayed at the top, accompanied by a circular profile picture of Mayank Ahuja.

**Key Features:**

* **Title:** "9 Resiliency Patterns"
* **Subtitle:** "@mayankahuja"
* **Profile Picture:** Circular image of Mayank Ahuja

**Patterns:**

The infographic showcases nine distinct resiliency patterns, each represented by a unique icon and color scheme:

1. **Circuit Breaker**
2. **Retry**
3. **Timeout**
4. **Bulkhead**
5. **Rate Limiting**
6. **Fallback**
7. **Hedging**
8. **Load Shedding**
9. **Backpressure**

Each pattern is accompanied by a brief description, providing context and clarity for the viewer.

**Design Elements:**

The infographic features a clean and modern design aesthetic, with:

* A white background
* Black text
* Colorful icons and graphics

Overall, the infographic effectively communicates the concept of resiliency patterns in a visually appealing and easy-to-understand format.

*Last updated: 2025-02-25 22:43:14*