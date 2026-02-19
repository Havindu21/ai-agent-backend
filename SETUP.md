# Setup Instructions for AI Agent Backend

## Current Status

✅ Spring Boot project structure created
✅ Java 25 is installed  
⚠️  Maven needs to be installed

## What Has Been Created

### 1. Project Files
- [pom.xml](pom.xml) - Maven configuration with all Spring Boot dependencies
- [application.properties](src/main/resources/application.properties) - Database and server configuration
- [README.md](README.md) - Complete documentation

### 2. Source Code (Industry Standard Structure)

**Main Application:**
- [AiAgentBackendApplication.java](src/main/java/com/aiagent/backend/AiAgentBackendApplication.java) - Spring Boot entry point

**Entity Layer:**
- [Message.java](src/main/java/com/aiagent/backend/entity/Message.java) - JPA entity for database table

**Repository Layer:**
- [MessageRepository.java](src/main/java/com/aiagent/backend/repository/MessageRepository.java) - Data access interface

**Service Layer:**
- [MessageService.java](src/main/java/com/aiagent/backend/service/MessageService.java) - Business logic

**Controller Layer:**
- [MessageController.java](src/main/java/com/aiagent/backend/controller/MessageController.java) - REST API endpoints

**DTOs:**
- [MessageRequest.java](src/main/java/com/aiagent/backend/dto/MessageRequest.java) - API request model
- [MessageResponse.java](src/main/java/com/aiagent/backend/dto/MessageResponse.java) - API response model

**Exception Handling:**
- [GlobalExceptionHandler.java](src/main/java/com/aiagent/backend/exception/GlobalExceptionHandler.java) - Centralized error handling
- [ErrorResponse.java](src/main/java/com/aiagent/backend/exception/ErrorResponse.java) - Error response model

## Next Steps

### Step 1: Install Maven

**Option A - Using Homebrew (Recommended):**
```bash
brew install maven
```

**Option B - Manual Download:**
1. Download from https://maven.apache.org/download.cgi
2. Extract and add to PATH

**Verify installation:**
```bash
mvn -version
```

### Step 2: Install MySQL

**Using Homebrew:**
```bash
brew install mysql
brew services start mysql
```

**Or download from:** https://dev.mysql.com/downloads/mysql/

### Step 3: Configure Database

Update credentials in [application.properties](src/main/resources/application.properties) if needed:
```properties
spring.datasource.username=root
spring.datasource.password=your_password
```

### Step 4: Build and Run

```bash
# Navigate to project directory
cd "/Users/havindufonseka/Developer/University/group project/AI-AGENT/ai-agent-backend"

# Build project
mvn clean install

# Run application
mvn spring-boot:run
```

### Step 5: Test the APIs

**Save a message:**
```bash
curl -X POST http://localhost:8080/api/messages \
  -H "Content-Type: application/json" \
  -d '{"content": "Hello from AI Agent!"}'
```

**Get all messages:**
```bash
curl -X GET http://localhost:8080/api/messages
```

## Project Features

✅ RESTful API design following industry standards
✅ Layered architecture (Controller → Service → Repository → Entity)
✅ MySQL database integration with JPA/Hibernate
✅ Automatic database schema creation
✅ Input validation with Bean Validation
✅ Global exception handling
✅ DTO pattern for request/response
✅ Transaction management
✅ Lombok for cleaner code
✅ CORS enabled for frontend integration
✅ Comprehensive logging

## API Endpoints

1. **POST** `/api/messages` - Save a new message
2. **GET** `/api/messages` - Fetch all messages
3. **GET** `/api/messages/{id}` - Fetch specific message by ID

## Database

- **Database Name:** `ai_agent` (auto-created on first run)
- **Table:** `messages`
  - id (BIGINT, Primary Key, Auto-increment)
  - content (TEXT)
  - created_at (TIMESTAMP)
  - updated_at (TIMESTAMP)

## Technology Stack

- Spring Boot 3.2.2
- Spring Data JPA
- MySQL 8.0+
- Java 17+ (Java 25 currently installed)
- Maven
- Lombok
- Bean Validation

## Troubleshooting

**If Maven build fails:**
- Ensure Java 17+ is in PATH
- Check internet connection for dependency download

**If database connection fails:**
- Verify MySQL is running: `brew services list`
- Check credentials in application.properties
- Ensure port 3306 is not blocked

**If port 8080 is already in use:**
- Change `server.port` in application.properties

---

See [README.md](README.md) for complete documentation including API examples and project structure details.
