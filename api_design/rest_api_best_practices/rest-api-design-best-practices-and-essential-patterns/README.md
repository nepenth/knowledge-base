**Source:** [https://twitter.com/i/web/status/1875827389562757262](https://twitter.com/i/web/status/1875827389562757262)
**Original Post Date:** 2025-05-27 16:44:57

# REST API Design: Best Practices and Essential Patterns

## Introduction
Modern web applications rely heavily on well-designed REST APIs for reliable communication between services. This knowledge base compiles essential best practices from authoritative sources, focusing on HTTP protocols, security measures, and API structure principles that ensure maintainable and scalable implementations.

We'll explore key concepts including HTTP status codes, idempotent operations, query parameters, authentication methods, versioning strategies, and semantic endpoint design.

## HTTP Status Codes

Status codes organize API responses into five categories (2xx: Success, 3xx: Redirection, 4xx: Client Errors, 5xx: Server Errors).

Clients use these codes to determine success/failure and appropriate response handling.

- 200 OK - Successful request processing
- 401 Unauthorized - Authentication required
- 503 Service Unavailable - Temporary server issues

## Idempotence in REST Operations

Idempotent operations guarantee the same result regardless of execution frequency.

GET, PUT, DELETE are naturally idempotent; POST is not.

> **Note/Tip:** Use idempotency keys for operations like payment processing

## Query Parameters and Pagination

Implement filtering, sorting, and pagination through standardized query parameters.

Example: GET /api/users?page=1&limit=20&sort=name

1. Filtering with specific criteria
1. Sorting by field names
1. Pagination for large result sets

## Authentication Methods

Multiple authentication approaches support different security requirements.

JWT and OAuth2 are widely adopted standards.

```HTTP
# JWT Authentication
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
```

## API Versioning Strategies

Version endpoints to manage API changes without breaking existing clients.

Use path-based or header-based version identifiers.

- /v1/resources (Path-based)
- X-API-Version: v2 (Header-based)

## Semantic URL Design

Create intuitive, resource-oriented endpoints reflecting business domains.

Example: /products/{id}/reviews represents product review relationships.

> **Note/Tip:** Maintain consistent naming conventions across resources

## Key Takeaways

- Implement idempotent operations for predictable API behavior
- Use standardized HTTP methods and status codes
- Apply proper authentication mechanisms based on security requirements
- Design semantic URLs reflecting business domain models

## Conclusion
Following these REST API best practices ensures scalable, maintainable services that promote reliability and developer experience. Regular review of design patterns against evolving standards helps maintain optimal API implementations.

## External References

- [RESTful Web Services](https://www.rfc-editor.org/rfc/rfc7231)
- [OAuth 2.0 Authorization Framework](https://tools.ietf.org/html/rfc6749)


## Media

**Image Description:** The image is a detailed infographic titled **"REST API Best Tips Tips"**, created by **Nina** and published on **SketechWorld.com**. It provides a comprehensive overview of best practices and key concepts related to RESTful API design. The infographic is visually organized into several sections, each highlighting a specific aspect of REST API development. Below is a detailed breakdown of the content:

---

### **1. HTTP Status Codes**
- **Section Title**: HTTP Status
- **Description**: This section lists common HTTP status codes and their meanings, categorized into different groups (2xx, 3xx, 4xx, 5xx). Each code is accompanied by a brief explanation of its purpose.
  - **2xx - Success**:
    - 200 - OK
    - 201 - Created
    - 204 - No Content
  - **3xx - Redirection**:
    - 301 - Moved Permanently
    - 302 - Found
    - 307 - Temporary Redirect
  - **4xx - Client Errors**:
    - 400 - Bad Request
    - 401 - Unauthorized
    - 403 - Forbidden
    - 404 - Not Found
    - 405 - Method Not Allowed
    - 408 - Request Timeout
    - 409 - Conflict
    - 410 - Gone
    - 412 - Precondition Failed
    - 415 - Unsupported Media Type
    - 422 - Unprocessable Entity
    - 425 - Too Early
    - 429 - Too Many Requests
  - **5xx - Server Errors**:
    - 500 - Internal Server Error
    - 502 - Bad Gateway
    - 503 - Service Unavailable
    - 504 - Gateway Timeout

---

### **2. Idempotence**
- **Section Title**: Idempotence
- **Description**: This section explains the concept of idempotence in REST APIs. It emphasizes that idempotent requests should have the same effect, regardless of how many times they are executed. This is particularly important for operations like `GET`, `PUT`, and `DELETE`.

---

### **3. Query Languages**
- **Section Title**: Query Languages
- **Description**: This section outlines how to use query parameters to enhance API functionality. It covers:
  - **Pagination**: Example: `GET /v1/users?page=1&size=10`
  - **Filtering**: Example: `GET /v1/users?name=sketech`
  - **Sorting**: Example: `GET /v1/users?sort=name`

---

### **4. Authentication**
- **Section Title**: Authentication
- **Description**: This section details various authentication mechanisms used in REST APIs:
  - **OAuth2**: Example: `POST /v1/auth/oauth2/token`
  - **API Key**: Example: `X-API-Key: YOUR_KEY`
  - **JWT (JSON Web Token)**: Example: `Authorization: Bearer <token>`

---

### **5. HTTP Methods**
- **Section Title**: HTTP Methods
- **Description**: This section lists the common HTTP methods used in REST APIs and their purposes:
  - **GET**: Retrieve a resource
  - **POST**: Create a resource
  - **PUT**: Replace a resource
  - **PATCH**: Modify a resource
  - **DELETE**: Remove a resource

---

### **6. Versioning**
- **Section Title**: Versioning
- **Description**: This section explains how to version APIs to manage changes over time. It suggests using a version identifier in the URL path or as a header:
  - **Path**: Example: `/v1/users`
  - **Header**: Example: `X-API-Version: v1`

---

### **7. Semantic Path**
- **Section Title**: Semantic Path
- **Description**: This section emphasizes the importance of designing meaningful and intuitive API endpoints. It provides examples of well-structured paths:
  - **Login**: `POST /v1/auth/login`
  - **Token**: `POST /v1/auth/token`
  - **Product**: `GET /products/{id}`
  - **Reviews**: `GET /products/{id}/reviews`

---

### **8. Domain Model Driven Design**
- **Section Title**: Domain Model Driven
- **Description**: This section highlights the importance of designing APIs based on real-world entities. It suggests creating endpoints that reflect the domain model:
  - Example: `/products/{id}/reviews` for retrieving reviews of a specific product.

---

### **Visual Design**
- The infographic uses a clean and organized layout with:
  - **Color-Coded Boxes**: Each section is highlighted with a distinct color for easy differentiation.
  - **Icons and Text**: Simple icons and clear text make the content visually appealing and easy to understand.
  - **Examples**: Real-world examples are provided for each concept to illustrate practical usage.

---

### **Footer**
- The infographic includes:
  - **Copyright**: ©Sketech
  - **Author**: @NinaDurann
  - **Handle**: @HeyNina101
  - **Logo**: A blue logo with the text "Ske" is present in the bottom-left corner.

---

### **Overall Purpose**
The infographic serves as a quick reference guide for developers working with REST APIs. It covers essential concepts such as HTTP status codes, idempotence, query parameters, authentication, HTTP methods, versioning, semantic paths, and domain-driven design. The visual organization and practical examples make it a valuable resource for both beginners and experienced developers.
![The image is a detailed infographic titled **"REST API Best Tips Tips"**, created by **Nina** and pu...](./media/image_1.jpg)