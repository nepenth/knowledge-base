**Source:** [https://twitter.com/i/web/status/1883134699800867289](https://twitter.com/i/web/status/1883134699800867289)
**Original Post Date:** 2025-05-27 21:28:52

# RESTful API Design Best Practices: Following Zalando Guidelines

## Introduction
Zalando's RESTful API design principles provide a robust framework for building reliable and maintainable web services. This guide explores the essential components required to create APIs that are secure, consistent, and aligned with industry best practices. We'll examine critical aspects including HTTP method usage, versioning strategies, error handling, authentication mechanisms, and proper resource naming conventions.

## HTTP Methods and Status Codes

Utilize HTTP methods according to RESTful principles: GET for retrieving resources, POST for creating new entities, PUT/PATCH for updates, DELETE for removal. Each endpoint should adhere strictly to these semantics.

Implement status codes appropriately: 201 Created for resource creation, 400 Bad Request for validation errors, and 5xx series for server-side failures.

```HTTP
POST /api/v1/orders
Content-Type: application/json
{
  "customer_id": "user123",
  "items": [{"product_id": "prod456", "quantity": 2}]
}

Response:
HTTP/1.1 201 Created
Location: /api/v1/orders/789
```

- Use POST for creating resources that require server-side logic
- Return 303 See Other with Location header after creation
- Avoid mixing collection and resource operations in single endpoints

> **Note/Tip:** Always include 'Content-Type' headers to specify response format

## Versioning Strategy

Implement version control through URL-based or Accept header-based approaches. For example, /v1/orders indicates the API version.

Maintain backward compatibility when possible and deprecate versions with clear communication.

```HTTP
Accept: application/vnd.zalando.v2+json
GET /orders/123
```

## Error Handling and Responses

Structure errors consistently with standard fields including status, code, message, and path.

Avoid exposing sensitive details in production environments.

```JSON
{
  "status": 400,
  "code": "invalid_input",
  "message": "Invalid customer ID format",
  "path": "/orders"
}
```

1. Include meaningful error codes for client handling
1. Provide path to the failing resource or parameter
1. Use 'application/problem+json' format when possible

## Key Takeaways

- Implement strict adherence to HTTP methods and status codes
- Structure API versions using consistent URL or header-based approaches
- Define standardized error responses with clear semantic meanings
- Use appropriate authentication/authorization mechanisms per resource

## Conclusion
Following Zalando's guidelines ensures APIs are maintainable, scalable, and secure. By focusing on proper HTTP usage, versioning strategies, and consistent error handling, developers can create robust services that align with industry standards.

## External References

- [Zalando RESTful API Guidelines](https://github.com/zalando/rest-api-guidelines)
- [REST Architectural Constraints](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm)