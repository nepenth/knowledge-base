Effective logging is crucial for efficient debugging and troubleshooting in software development. Good logs can lead developers to a fix, while bad logs are just noise that hinders the debugging process. This article outlines 7 rules of thumb for effective logging, providing guidelines for writing high-quality log entries that facilitate easy parsing, processing, and analysis.

## Technical Content
### 1. Use Structured Logging
Structured logging involves formatting log entries in a structured way to enable easy parsing and processing by tools and automation systems. This can be achieved using standardized formats such as JSON or XML. For example:
```json
{
  "timestamp": "2022-01-01T12:00:00Z",
  "level": "ERROR",
  "message": "Failed to connect to database",
  "correlationId": "1234567890"
}
```
### 2. Include Unique Identifiers
Each log entry should have a unique identifier, such as correlation IDs, request IDs, or transaction IDs, to trace requests across distributed services. This enables developers to track the flow of events and identify related log entries.

### 3. Log Entries Should Be Small, Easy to Read, and Useful
Log entries should be concise and focused on what's important. Avoid overloading logs with unnecessary information, as this can make it difficult to read and analyze the logs.

### 4. Standardize Timestamps
Use consistent time zones (preferably UTC) and formats for timestamps. This ensures that log entries from different sources can be easily correlated and analyzed. For example:
```json
{
  "timestamp": "2022-01-01T12:00:00Z",
  "level": "INFO",
  "message": "User logged in"
}
```
### 5. Categorize Log Levels
Log levels should be categorized to provide context and facilitate filtering. Common log levels include:
* **Debug**: Detailed technical information for troubleshooting during development.
* **Info**: High-level operational information.
* **Error**: Critical issues requiring attention.

### 6. Include Contextual Information
Contextual details, such as user ID, session ID, and environment-specific identifiers, make debugging easier by providing additional context about the events being logged. For example:
```json
{
  "timestamp": "2022-01-01T12:00:00Z",
  "level": "ERROR",
  "message": "Failed to process order",
  "correlationId": "1234567890",
  "userId": "johnDoe",
  "sessionId": "abcdefg"
}
```
### 7. Protect Sensitive Information
Sensitive information, such as passwords, API keys, or personally identifiable information (PII), should not be logged. If unavoidable, sensitive data should be masked, redacted, or hashed to protect users and systems.

## Key Takeaways and Best Practices
* Use structured logging to enable easy parsing and processing of log entries.
* Include unique identifiers to trace requests across distributed services.
* Keep log entries small, easy to read, and useful.
* Standardize timestamps using consistent time zones and formats.
* Categorize log levels to provide context and facilitate filtering.
* Include contextual information to aid debugging.
* Protect sensitive information by masking, redacting, or hashing.

## References
* [Serilog](https://serilog.net/): A popular logging framework for .NET that supports structured logging and provides a simple, consistent API for logging.

By following these 7 rules of thumb, developers can write high-quality log entries that facilitate efficient debugging and troubleshooting, leading to faster resolution of issues and improved overall system reliability.
## Source

- Original Tweet: [https://twitter.com/i/web/status/1881696953190264862](https://twitter.com/i/web/status/1881696953190264862)
- Date: 2025-02-25 17:30:54


## Media

### Media 1
![media_0](./media_0.jpg)
**Description:** The image presents a code snippet with annotations highlighting its benefits, accompanied by a title that reads "Bad logs are just noise. Good logs lead you to a fix." The purpose of the image is to illustrate the importance of well-structured logging in software development.

* A code snippet:
	+ The code snippet is written in a programming language and appears to be related to error handling or debugging.
	+ It includes various keywords such as "timestamp", "level", "message", and "correlationId".
	+ The code is surrounded by green annotations that highlight its benefits, including clear categorization of errors, concise logging, and easy traceability across services.
* A title:
	+ The title emphasizes the importance of good logs in resolving issues efficiently.
	+ It suggests that bad logs can be distracting and unhelpful, while good logs provide valuable information for debugging and troubleshooting.
* Green annotations:
	+ The annotations are placed throughout the code snippet to highlight specific features or benefits.
	+ They include phrases such as "Clearly categorized as an 'error'", "Provides user ID, session ID, order ID, and environment to aid debugging", and "Includes correlation and order ID for easy traceability across services".

Overall, the image effectively conveys the importance of good logging practices in software development. By highlighting the benefits of clear, concise, and easily traceable logs, the image encourages developers to prioritize effective logging in their code.

*Last updated: 2025-02-25 17:30:54*