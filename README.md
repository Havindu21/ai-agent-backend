# AI Agent Backend - Spring Boot Application

A Spring Boot REST API application with MySQL database for storing and retrieving messages.

## Prerequisites

- Java 17 or higher
- Maven 3.6+
- MySQL 8.0+
- IDE (IntelliJ IDEA, Eclipse, or VS Code)

## Database Setup

1. Install MySQL if not already installed
2. Start MySQL server
3. The application will automatically create the database `ai_agent` on first run
4. Update database credentials in `src/main/resources/application.properties` if needed:
   ```properties
   spring.datasource.username=root
   spring.datasource.password=your_password
   ```

## Build and Run

### Using Maven

```bash
# Clean and build the project
mvn clean install

# Run the application
mvn spring-boot:run
```

### Using IDE

1. Import the project as a Maven project
2. Run `AiAgentBackendApplication.java` as a Java Application

The application will start on `http://localhost:8080`

## API Endpoints

### 1. Save Message (POST)

**Endpoint:** `POST /api/messages`

**Request Body:**
```json
{
  "content": "Your message here"
}
```

**Response:** (201 Created)
```json
{
  "id": 1,
  "content": "Your message here",
  "createdAt": "2026-02-19T10:30:00",
  "updatedAt": "2026-02-19T10:30:00"
}
```

**cURL Example:**
```bash
curl -X POST http://localhost:8080/api/messages \
  -H "Content-Type: application/json" \
  -d '{"content": "Hello World"}'
```

### 2. Get All Messages (GET)

**Endpoint:** `GET /api/messages`

**Response:** (200 OK)
```json
[
  {
    "id": 1,
    "content": "First message",
    "createdAt": "2026-02-19T10:30:00",
    "updatedAt": "2026-02-19T10:30:00"
  },
  {
    "id": 2,
    "content": "Second message",
    "createdAt": "2026-02-19T10:35:00",
    "updatedAt": "2026-02-19T10:35:00"  }
]
```

**cURL Example:**
```bash
curl -X GET http://localhost:8080/api/messages
```

### 3. Get Message by ID (GET)

**Endpoint:** `GET /api/messages/{id}`

**Response:** (200 OK)
```json
{
  "id": 1,
  "content": "Your message here",
  "createdAt": "2026-02-19T10:30:00",
  "updatedAt": "2026-02-19T10:30:00"
}
```

**cURL Example:**
```bash
curl -X GET http://localhost:8080/api/messages/1
```

## Project Structure

```
ai-agent-backend/
├── src/
│   └── main/
│       ├── java/
│       │   └── com/
│       │       └── aiagent/
│       │           └── backend/
│       │               ├── AiAgentBackendApplication.java  # Main application class
│       │               ├── controller/
│       │               │   └── MessageController.java      # REST endpoints
│       │               ├── service/
│       │               │   └── MessageService.java         # Business logic
│       │               ├── repository/
│       │               │   └── MessageRepository.java      # Data access
│       │               ├── entity/
│       │               │   └── Message.java                # JPA entity
│       │               ├── dto/
│       │               │   ├── MessageRequest.java         # Request DTO
│       │               │   └── MessageResponse.java        # Response DTO
│       │               └── exception/
│       │                   ├── GlobalExceptionHandler.java # Global error handler
│       │                   └── ErrorResponse.java          # Error response model
│       └── resources/
│           └── application.properties                      # Configuration
└── pom.xml                                                 # Maven dependencies
```

## Technologies Used

- **Spring Boot 3.2.2** - Framework
- **Spring Data JPA** - Data persistence
- **MySQL** - Database
- **Lombok** - Reduce boilerplate code
- **Bean Validation** - Input validation
- **Maven** - Build tool

## Features

- RESTful API design
- Input validation
- Global exception handling
- Transaction management
- Automatic database schema creation
- Lombok for cleaner code
- Structured layered architecture (Controller → Service → Repository)
- DTO pattern for request/response
- CORS enabled for frontend integration

## Configuration

Edit `application.properties` to customize:
- Server port
- Database connection
- JPA/Hibernate settings
- Logging levels

## Testing

You can test the APIs using:
- **cURL** (examples provided above)
- **Postman** - Import endpoints and test
- **Browser** - For GET requests
- **HTTPie** - CLI HTTP client

## Troubleshooting

1. **Database Connection Error**: Ensure MySQL is running and credentials are correct
2. **Port Already in Use**: Change server.port in application.properties
3. **Build Failures**: Run `mvn clean install` to refresh dependencies
