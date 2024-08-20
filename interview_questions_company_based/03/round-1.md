### 1. API optimization at LLD,HLD,FE, DB levels (explain in detail at every stage)


<details>

#### 1. High Level Design (HLD)

At the HLD stage, the focus is <u>**_on the overall system architecture and how different components interact with each other including the APIs_**</u>

- **Defining API Specifications**: Establish clear API specifications using standards like **_OpenAPI_**. This ensures consistency and ease of understanding across the system.

- **Service Architecture**: Choose between monolithic, microservices or serverless architectures based on scalability, maintainability and the nature of the application.

- **Load balancing**: Implement load balancers to distribute API requests efficiently across servers.

- **Caching Strategy**: Design a caching strategy to reduce the load on the backend systems. This could include **_edge caching or application-level caching_**

#### 2. Low Level Design (LLD)

LLD involves the <u>**detailed design of the API, focusing on how components will be implemented.**</u>

- **Endpoint Optimization**: Design endpoints to be specific and granular **_to avoid over-fetching of data_**

- **Data Serialization**: Use efficient data serialization **_formats like JSON or Protocol Buffers_**

- **Rate limiting**: Implement rate limiting **_to prevent abuse and to manage the load on the servers._**
- **Error Handling**: Develop robust error handling **_to ensure API stability and meaningful error responses_** to the clients.

#### 3. Frontend (FE)

At Frontend level, optimization is about <u>**how the application consumes the API**.</u>

- **Minimizing Requests**: Bundle request or use **_techniques like GraphQL_** to minimize the number of API calls.
- **Lazy Loading**: Implement Lazy loading of data **_to improve user experience and reduce initial load times_**.
- **Handling Responses:** Efficiently handle API responses to update the UI smoothly without jarring user experience
- **Caching Responses**: Cache API responses on the client side when appropriate **_to reduce redundant network calls_**.

### Database (DB)

The database layer is crucial for <u>**_optimizing how data is fetched and stored, which directly affects API performance._**</u>

- **Indexing**: Proper indexing of database tables **_to ensure quick data retrieval_**.
- **Query Optimization:** Optimize queries **_to reduce execution time and resource consumption_**.
- **Normalization and De-normalization**: Balance between **_normalization for data integrity_** and **_de-normalization for query efficiency_**.
- **Connection Pooling:** Use connection pooling **_to manage database connections efficiently_** and reduce overhead.

### Cross-Layer Considerations

- **Monitoring and Logging**: Implement comprehensive monitoring and logging to identify bottlenecks and issues
- **Security**: Ensure API security at all levels, including authentication, authorization and data encryption.
- **Documentation**: Maintain up-to-date documentation for all API endpoints to facilitate easy consumption

<summary>
View Answer
</summary>
</details>




---

2. Rest vs spread operator
3. Virtual dom working and benefits
4. Closure with example and benefits
5. Call, apply and bind with working example
6. Redux saga usage
7. JWT & refresh token (indepth discussion on Refresh Token VS Access Token)
8. HOC and higher order functions
9. Class vs function based components
10. IIFE and function currying
11. output of 15+3+"string"

    <details>

    ![image](https://user-images.githubusercontent.com/42731246/164546208-6c84d87e-c3c6-44e4-9966-6ee66e88addb.png)

    <summary>
    View Answer
    </summary>
    </details>

12. output of "string"+15+3
    <details>

    ![image](https://user-images.githubusercontent.com/42731246/164546169-bea51e7b-d8cc-4eed-bc61-3d293a5c222b.png)
    
    <summary>
    View Answer
    </summary>
    </details>

