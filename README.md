# Employee Management REST API

A RESTful API built with **Java Spring Boot** for managing employee records with full CRUD operations, backed by a **MySQL** database using **Spring Data JPA**.

---

## Tech Stack

| Technology | Version | Purpose |
|---|---|---|
| Java | 8 | Programming Language |
| Spring Boot | 2.2.5 | Application Framework |
| Spring Data JPA | - | Database Abstraction Layer |
| Hibernate | 5.4.12 | ORM / Entity Mapping |
| MySQL | 8.0+ | Relational Database |
| Maven | 3.x | Build & Dependency Management |
| JUnit / TestNG | 4.10 / 6.8 | Unit Testing |

---

## Project Structure

```
src/
├── main/
│   ├── java/SpringBoot/SpringDataJPA/
│   │   ├── Application.java              # Entry point
│   │   ├── entity/
│   │   │   └── Employee.java             # Employee data model
│   │   ├── dao/
│   │   │   └── EmployeeRepository.java   # Database operations
│   │   ├── service/
│   │   │   ├── EmployeeService.java      # Service interface
│   │   │   └── EmployeeServiceImpl.java  # Business logic
│   │   └── rest/
│   │       └── EmployeeRestController.java  # API endpoints
│   └── resources/
│       └── application.properties        # App configuration
└── test/
    └── java/SpringBoot/CRUDdemo/         # Unit tests
```

---

## API Endpoints

Base URL: `http://localhost:8080/api`

| Method | Endpoint | Description | Request Body |
|--------|----------|-------------|--------------|
| GET | `/employees` | Get all employees | None |
| GET | `/employees/{id}` | Get employee by ID | None |
| POST | `/employees` | Add new employee | JSON body |
| PUT | `/employees` | Update existing employee | JSON body |
| DELETE | `/employees/{id}` | Delete employee by ID | None |

### Sample Request Body (POST / PUT)

```json
{
    "firstName": "John",
    "lastName": "Doe",
    "email": "john.doe@example.com"
}
```

### Sample Response

```json
{
    "id": 1,
    "firstName": "John",
    "lastName": "Doe",
    "email": "john.doe@example.com"
}
```

---

## Getting Started

### Prerequisites

Make sure you have the following installed:
- Java JDK 8 or higher
- Maven 3.x
- MySQL 8.0+

### 1. Clone the Repository

```bash
git clone https://github.com/YOURUSERNAME/employee-management-api.git
cd employee-management-api
```

### 2. Create the Database

Open MySQL and run:

```sql
CREATE DATABASE employeedb;
```

### 3. Configure Database Credentials

Open `src/main/resources/application.properties` and update:

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/employeedb?serverTimezone=UTC
spring.datasource.username=root
spring.datasource.password=YOUR_MYSQL_PASSWORD
spring.jpa.hibernate.ddl-auto=update
```

### 4. Run the Application

```bash
mvn spring-boot:run
```

You should see:
```
Tomcat started on port(s): 8080
Started Application in x.xxx seconds
```

### 5. Test the API

Use **Postman** or any REST client to hit:
```
GET http://localhost:8080/api/employees
```

---

## Testing with Postman

### Add a New Employee
- **Method:** POST
- **URL:** `http://localhost:8080/api/employees`
- **Body:** raw → JSON
```json
{
    "firstName": "John",
    "lastName": "Doe",
    "email": "john.doe@example.com"
}
```

### Get All Employees
- **Method:** GET
- **URL:** `http://localhost:8080/api/employees`

### Update an Employee
- **Method:** PUT
- **URL:** `http://localhost:8080/api/employees`
- **Body:** raw → JSON (include the `id`)
```json
{
    "id": 1,
    "firstName": "Jane",
    "lastName": "Doe",
    "email": "jane.doe@example.com"
}
```

### Delete an Employee
- **Method:** DELETE
- **URL:** `http://localhost:8080/api/employees/1`

---

## Upcoming Features

- [ ] JWT Authentication (login / register)
- [ ] Input validation with proper error responses
- [ ] Department & Role management
- [ ] Pagination and search filtering
- [ ] Swagger API documentation

---

## License

This project is licensed under the MIT License.
