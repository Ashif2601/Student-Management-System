# 📚 Student Management System
## A Complete Spring Boot CRUD REST API Project
The **Student Management System** is a fully functional REST API built with **Spring Boot**, designed to handle all basic operations related to student data.
It follows a clean three-layer architecture (Controller → Service → Repository) and is integrated with a **MySQL** database using **Spring Data JPA**.

This project is ideal for learning:
- ✔ Spring Boot
- ✔ REST API Design
- ✔ CRUD Operations
- ✔ JPA & Hibernate
- ✔ Exception Handling
- ✔ Layered Architecture

## 🧱 Architecture Overview
               +---------------------------+
               |   StudentController       |
               |  (Handles API requests)   |
               +-------------+-------------+
                             |
                             ▼
               +---------------------------+
               |     StudentService        |
               | (Business Logic Layer)    |
               +-------------+-------------+
                             |
                             ▼
               +---------------------------+
               |    StudentRepository      |
               | (Database Interaction)    |
               +-------------+-------------+
                             |
                             ▼
               +---------------------------+
               |       MySQL Database      |
               +---------------------------+

## 🔧 Project Structure

    src/main/java/com/example/studentmanagement/
    │
    ├── controller/
    │   └── StudentController.java          // API endpoints 
    │
    ├── entity/
    │   └── Student.java                    // JPA model      
    │
    ├── exception/
    │   └── StudentNotFoundException.java   // Error handling 
    │
    ├── repository/
    │   └── StudentRepository.java          // JPA repository 
    │
    ├── service/
    │   ├── StudentService.java             // Service interface 
    │   └── StudentServiceImpl.java         // Business logic    
    │
    └── StudentManagementApplication.java   // Main class        

## 🌟 Features
### ✔ Full CRUD Functionality
- Add new students
- Retrieve all students or by ID
- Update student details
- Delete students
### ✔ Proper Layered Architecture
- Controller
- Service
- Repository
### ✔ Database Integration
- MySQL using Spring Data JPA
### ✔ Exception Handling
- Custom `StudentNotFoundException` with 404 error
### ✔ Data Validation Ready
(Easy to extend using `@Valid` annotation)
## 🗄️ Database Setup
Your database is configured in application.properties:

    spring.datasource.url=jdbc:mysql://localhost:3306/studentdb
    spring.datasource.username=root
    spring.datasource.password=YOUR_PASSWORD

    spring.jpa.hibernate.ddl-auto=update
    spring.jpa.show-sql=true
    spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQL8Dialect

    server.port=8080

Create the database:

    CREATE DATABASE studentdb;
## 🚀 Running the Project
**1️⃣ Clone the project**

    git clone https://github.com/Ashif2601/Student-Management-System
**2️⃣ Open in IntelliJ / Eclipse**\
**3️⃣ Install dependencies**

    mvn clean install
**4️⃣ Run Spring Boot App**

    mvn spring-boot:run

App starts on:

    👉 http://localhost:8080
## 📘 API Documentation
### 📍 Base URL

    /api/students
### 📌 1. Get All Students
`GET /api/students`
#### ✔ Response (200 OK)

    [
      {
        "id": 1,
        "name": "Alice",
        "email": "alice@example.com",
        "course": "BCA"
      }
    ]
### 📌 2. Get Student by ID    
`GET /api/students/{id}`
#### ✔ Response (200 OK)

    {
      "id": 1,
      "name": "Alice",
      "email": "alice@example.com",
      "course": "BCA"
    }
#### ❌ Error (404 Not Found)   
Triggered by `StudentNotFoundException`

    {
      "timestamp": "2024-01-01T10:00:00",
      "status": 404,
      "error": "Not Found",
      "message": "Student not found with id: 10"
    }
### 📌 3. Add New Student    
`POST /api/students`
#### ✔ Request Body

    {
      "name": "John Doe",
      "email": "john@example.com",
      "course": "Computer Science"
    }
#### ✔ Response (201 Created)  
Same JSON with generated ID.
### 📌 4. Update Student
`PUT /api/students/{id}`
#### ✔ Request Body

    {
      "name": "Updated Name",
      "email": "updated@example.com",
      "course": "B.Tech"
    }
### 📌 5. Delete Student
`DELETE /api/students/{id}`
#### ✔ Response
`204 No Content`
## 🧩 Internals Explained
#### 🔸 Student Entity
(Defines DB table columns)
- `@Entity` → Marks as JPA table
- `@Id`, `@GeneratedValue` → Auto-generated ID
- Fields: name, email, course
#### 🔸 Repository Layer
Extends `JpaRepository<Student, Long>` → gives:
- `findAll()`
- `findById()`
- `save()`
- `deleteById()`
…all without writing SQL!
#### 🔸 Service Layer
Interface + Implementation

Handles:
- Business logic
- Validation
- Update logic
- Error checking
#### 🔸 Controller Layer
Handles all REST endpoints using:
- `@RestController`
- `@GetMapping`, `@PostMapping`
- `@PutMapping`, `@DeleteMapping`
## 🛡️ Error Handling
When a student is not found, the service throws:

    throw new StudentNotFoundException("Student not found with id: " + id);

Mapped to HTTP 404 because of:

    @ResponseStatus(HttpStatus.NOT_FOUND)

## 📦 Future Improvements (Optional)
- Add input validation using @Valid
- Add Swagger UI for API docs
- Add Pagination & Sorting
- Add Authentication (JWT)
- Add Frontend (React / Angular)















