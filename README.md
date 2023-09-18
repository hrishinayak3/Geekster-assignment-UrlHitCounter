# <h1 align="center"> URL Hit Counter </h1>


## Overview

The URL Hit Counter is a simple Spring Boot application that allows you to track the number of times a specific URL endpoint has been accessed. It also provides an additional feature to track hit counts for different usernames.

## Technologies Used

- **Framework:** Spring Boot
- **Language:** Java
- **Build Tool:** Maven

- ### Controller

The Controller layer is responsible for handling incoming HTTP requests and delegating them to the appropriate services. It defines API endpoints for various operations, including adding visitors, retrieving hit counts, and updating counts for specific users. Each endpoint maps to a specific service method to ensure proper request handling and response generation.

```java
@RestController
@RequestMapping("/api/v1/visitor-count-app")
public class UrlHitController {
    @Autowired
    private UrlHitService urlHitService;

    // Endpoint mappings for various operations
    // ...
}
```

### Service

The Service layer encapsulates the core business logic and data processing. It interacts with the Repository layer to retrieve and store data. In this application, it handles operations like adding visitors, retrieving hit counts, and updating counts for users. 

```java
@Service
public class UrlHitService {
    @Autowired
    private UrlHitRepo urlHitRepo;

    // Service methods for various operations
    // ...
}
```

### Repository

The Repository layer manages data access to in-memory storage. It maintains a list of `UrlHitCounter` objects to store hit counts for visitors.


```java
@Repository
public class UrlHitRepo {
    @Autowired
    private List<UrlHitCounter> urlHitCounterList;

    // Repository methods for managing visitor data
    // ...
}
```


### Entity Class

The `UrlHitCounter` class defines the structure for storing visitor information. It includes two fields: `userName` (to identify the visitor) and `counter` (to track the hit count for that visitor). Instances of this class are used to represent visitors and manage their hit counts.

```java
@Data
@NoArgsConstructor
@AllArgsConstructor
public class UrlHitCounter {
    private String userName;
    private Integer counter;
}
```

## Endpoints

### Get Total Hit Count
- **Endpoint**: `/api/v1/count`
- **HTTP Method**: GET
- **Description**: Retrieves the total hit count for the default URL.

### Get Hit Count for a Specific User
- **Endpoint**: `/api/v1/username/{username}/count`
- **HTTP Method**: GET
- **Description**: Retrieves the hit count for a specific user identified by `{username}`.

### Add a New Visitor
- **Endpoint**: `/visitor`
- **HTTP Method**: POST
- **Description**: Adds a new visitor to the system.

### Get All Visitors
- **Endpoint**: `/visitors`
- **HTTP Method**: GET
- **Description**: Retrieves a list of all visitors and their hit counts.

### Get the Number of Visitors
- **Endpoint**: `/visitor/count`
- **HTTP Method**: GET
- **Description**: Retrieves the total number of visitors.

### Increment Hit Count for a Specific User
- **Endpoint**: `/api/v1/count_update/username/{username}`
- **HTTP Method**: PUT
- **Description**: Increments the hit count for a specific user identified by `{username}`.


## Contact

For questions or feedback, please contact [Hrishikesh Nayak](hrishinayak3@gmail.com).
