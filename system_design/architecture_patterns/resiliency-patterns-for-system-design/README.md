Resiliency patterns are design principles used to build robust and fault-tolerant systems that can withstand failures, errors, and unexpected conditions. These patterns help ensure system availability, reliability, and performance, even in the face of adversity.

## Technical Content
Resiliency patterns can be categorized into several types, each addressing specific challenges and scenarios. The following are nine common resiliency patterns:

### 1. Circuit Breaker
The circuit breaker pattern acts like an electrical circuit breaker, tripping and stopping requests to a service when it experiences repeated failures. This allows the failing service to recover without being overwhelmed.
* **States:** Closed (requests allowed), Open (requests rejected)
* **Benefits:** Protects against cascading failures, isolates problematic services

### 2. Retry
The retry pattern automatically retries failed requests a certain number of times before giving up. This helps overcome transient errors like network glitches or temporary unavailability.
* **Best Practice:** Implement exponential backoff to avoid retry storms

### 3. Timeout
The timeout pattern sets a maximum time limit for a request. If a response is not received within the timeout period, the request is considered a failure.
* **Benefits:** Prevents indefinite waiting, improves system responsiveness

### 4. Bulkhead
The bulkhead pattern isolates different parts of an application into pools or compartments. This limits the impact of failures or overload in one compartment, preventing it from affecting the entire system.
* **Benefits:** Improves system stability, prevents cascading failures

### 5. Rate Limiting
The rate limiting pattern controls the rate of incoming requests to protect a system from being overwhelmed. This helps prevent denial of service attacks and ensures fair usage.
* **Benefits:** Maintains system stability, prevents overload

### 6. Fallback
The fallback pattern provides an alternative response or action when the primary one fails. This improves system availability and user experience by providing some level of service even when the primary function is unavailable.
* **Benefits:** Improves system availability, enhances user experience

### 7. Hedging (Redundancy)
The hedging pattern sends duplicate requests to multiple identical services and uses the fastest response. This mitigates the impact of slow responses and failures, improving system responsiveness.
* **Benefits:** Improves system responsiveness, reduces latency

### 8. Load Shedding
The load shedding pattern drops non-critical requests when a system is overloaded to protect its core functionality. This helps maintain system stability and availability during peak loads.
* **Benefits:** Maintains system stability, ensures core functionality

### 9. Backpressure
The backpressure pattern uses a feedback loop between the producer (sending data) and the consumer (receiving data). The consumer signals its capacity to the producer, allowing the producer to adjust its output rate dynamically.
* **Strategies:** Reactive Pull, Rate Limiting, Buffering
* **Benefits:** Improves system responsiveness, reduces buffer overflows

## Key Takeaways and Best Practices
When implementing resiliency patterns, keep the following best practices in mind:

* Use circuit breakers to prevent cascading failures
* Implement retry mechanisms with exponential backoff
* Set timeouts to prevent indefinite waiting
* Isolate components using bulkheads to improve system stability
* Limit incoming requests using rate limiting to prevent overload
* Provide fallback options to improve system availability and user experience
* Use hedging (redundancy) to mitigate slow responses and failures
* Shed non-critical loads during peak periods to maintain system stability
* Implement backpressure mechanisms to adjust output rates dynamically

## References
For more information on resiliency patterns, refer to the following resources:

* [Infographic: 9 Resiliency Patterns](https://example.com/resiliency-patterns-infographic)
* [System Design and Architecture Patterns](https://example.com/system-design-patterns)

---
**Source**: [Original Tweet](https://twitter.com/i/web/status/1883731027442778402)