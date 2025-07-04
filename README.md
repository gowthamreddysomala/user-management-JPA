# User Management using JPA (Java Presistance API)🚀  
RESTful CRUD service built with **Spring Boot 3 + Spring Data JPA + PostgreSQL**.

<img src="https://github.com/user-attachments/assets/08dbaf74-b1a5-4a34-b453-b5947d7793d0" width="250"/>  
<img src="https://github.com/user-attachments/assets/eb4cd345-85c9-4af0-8c1c-d0fc1a3f866f" width="250"/>  
<img src="https://github.com/user-attachments/assets/cc8e8733-d865-4ec9-9105-4694d3ce07e1" width="250"/>

---

## ✨ Features
| Capability | Details |
|------------|---------|
| **Bulk create** | `POST /api/users` accepts a JSON _array_ and persists all rows in one call (internally uses `saveAll`). |
| **CRUD endpoints** | Create, read, update, delete individual users. |
| **Pagination & sorting** | `GET /api/users/page?page=0&size=10&sort=name,asc` leverages Spring Pageable. |
| **Validation** | Jakarta Bean Validation enforces name length, email format, etc. |
| **Timestamps** | `created_at` & `updated_at` columns are auto‑populated with `@CreationTimestamp` / `@UpdateTimestamp`. |
| **Search helpers** | Repository methods like `findByEmail` & `findByNameContainingIgnoreCase`. |

---

## 🏗 Tech Stack

| Layer | Library/Tool |
|-------|--------------|
| Runtime | Java 24+ |
| Framework | Spring Boot, Spring Data JPA |
| Build | Maven |
| Database | PostgreSQL |
| Validation | Jakarta Validation |
| Dev‑time | Spring DevTools |

---

## ⚡️ Quick Start

```bash
# 1 Clone
git clone https://github.com/KhushiRaj23/user-management-JPA.git
cd user-management-JPA

# 2 Configure DB
spring.application.name=userManagementApi

# Database Connection Properties for MariaDB
spring.datasource.url=jdbc:mariadb://localhost:3306/UNIVERSITY
spring.datasource.username=gowthamreddy
spring.datasource.password=rhkg38yw4w
spring.datasource.driver-class-name=org.mariadb.jdbc.Driver
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true

# 3 Boot the app
./mvnw spring-boot:run          # hot‑reload dev mode
# or
./mvnw clean package
java -jar target/usermanagementapi-0.0.1-SNAPSHOT.jar
````

The API starts on **[http://localhost:8080](http://localhost:8080)** by default.

---

## 📖 API Reference

| Method   | Endpoint          | Body / Params                                    | Purpose             |
| -------- | ----------------- | ------------------------------------------------ | ------------------- |
| `POST`   | `/api/users`      | `[{ "name": "Jane", "email": "jane@x.com" }, …]` | Bulk‑create users   |
| `GET`    | `/api/users`      | –                                                | List all users      |
| `GET`    | `/api/users/{id}` | –                                                | Fetch one user      |
| `PUT`    | `/api/users/{id}` | `{ "name": "New", "email": "new@x.com" }`        | Update a user       |
| `DELETE` | `/api/users/{id}` | –                                                | Remove a user       |
| `GET`    | `/api/users/page` | `page, size, sort`                               | Paged & sorted list |

> All responses are JSON; validation errors return HTTP `400` with a human‑readable message.

---

## 🗄 Database Schema

```text
users
├─ id          BIGSERIAL PK
├─ name        VARCHAR(100)  NOT NULL
├─ email       VARCHAR(255)  NOT NULL UNIQUE
├─ created_at  TIMESTAMP     DEFAULT now()
└─ updated_at  TIMESTAMP
```

JPA/Hibernate creates (or updates) the table automatically thanks to
`spring.jpa.hibernate.ddl-auto=update`.

---

## 🗂 Project Layout

```
src
└── main
    ├── java
    │   └── com.user.usermanagementapi
    │       ├── UsermanagementapiApplication.java   # SpringBoot main class
    │       ├── controller
    │       │   └── UserController.java            # REST endpoints
    │       ├── model
    │       │   └── User.java                      # JPA entity
    │       └── repository
    │           └── UserRepository.java            # JpaRepository helpers
    └── resources
        └── application.properties
```


### Author

**Khushi Raj** – *B.Tech CSE*

> Thanks for checking out the project. 


