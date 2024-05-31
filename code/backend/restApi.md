---

Resource - https://learn.microsoft.com/en-us/azure/architecture/best-practices/api-design

## **What Defines a Well-Designed API?**

A well-designed API is platform-independent and supports evolutionary service updates without breaking existing clients.

## **Key Elements of REST Architecture**

### **Stateless Interactions**

REST holds no state. Each request from the client includes all the necessary information for the server to fulfil that request, promoting scalability and simplicity.

### **Naming Routines - Resource-Oriented Architecture**

- **Naming**: Use nouns to name resources (e.g., **`users`**, **`tickets`**) and HTTP methods (GET, POST, PUT, DELETE) to perform operations.
- **URL Structure**: Keep URLs intuitive and hierarchical where necessary (e.g., **`customers/123/orders`**). Avoid deep nesting to maintain simplicity.
- **Abstraction**: The API should not expose the database schema directly but provide an abstraction that best serves the client.

### **Handling Non-Resource Operations**

For operations that don't map directly to resources, like calculations or procedural commands, provide clear endpoints that reflect their functionality (e.g., **`/calculate?operand1=10&operand2=5`**).

Alternatively, these operations can be grouped under an `operations` area e.g. `/opreations/subscribe`

### **Versioning**

To manage changes and maintain compatibility:

- **URI Versioning**: Include a version number in the URI (e.g., **`/v1/resource`**).
- **Query Parameter Versioning**: Use query parameters to indicate version (e.g., **`?version=1`**).

### **Filtering and Query Parameters**

Limit the scope of data returned by any single request using query parameters to specify data constraints:

- Example: **`GET /users?limit=10&offset=20`** to control data pagination.
- Implement sensible defaults and always consider the impact on caching strategies.

### **Asynchronous Methods**

POST, PUT, PATCH or DELETE requests may take a while, therefore, utilize asynchronous request handling to improve performance:

- **202 Accepted** - Request accepted for processing but not completed.
- **303 See Other** - Direct client to retrieve the result of a completed asynchronous operation at a different URI.

## **Summary**

Adhering to REST principles ensures APIs are flexible, scalable, and maintainable. Using straightforward naming, stateless communications, and hypermedia links helps build robust, client-friendly APIs that are easy to integrate and upgrade over time.