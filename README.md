# 🏠 Smart Home Management System

<div align="center">

![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.1.5-brightgreen?style=for-the-badge&logo=spring-boot)
![Java](https://img.shields.io/badge/Java-17-orange?style=for-the-badge&logo=java)
![MySQL](https://img.shields.io/badge/MySQL-8.0-blue?style=for-the-badge&logo=mysql)
![Angular](https://img.shields.io/badge/Angular-Latest-red?style=for-the-badge&logo=angular)
![Docker](https://img.shields.io/badge/Docker-Enabled-2496ED?style=for-the-badge&logo=docker)

**A professional enterprise-grade home automation platform built with Spring Boot**

[Features](#-features) • [Technologies](#-technologies) • [Getting Started](#-getting-started) • [Documentation](#-documentation) • [Architecture](#-architecture)

</div>

---

## 📋 Description

**Smart Home Management System** is a comprehensive, production-ready platform designed to manage and control home automation devices seamlessly. Built on Spring Boot 3.1.5 with a modern Angular frontend, this system provides a robust REST API for device management, real-time monitoring, and intelligent automation workflows.

The application follows enterprise best practices with a clean architecture, ensuring scalability, maintainability, and ease of integration with various IoT devices and third-party services.

---

## ✨ Features

- 🔌 **Device Management**: Complete CRUD operations for smart home devices
- 📊 **Real-time Monitoring**: Track device status and performance metrics
- 🔐 **Secure API**: RESTful endpoints with Spring Data REST
- 🗄️ **Persistent Storage**: MySQL database with JPA/Hibernate ORM
- 🎨 **Modern UI**: Responsive Angular frontend with intuitive controls
- 🐳 **Containerized Deployment**: Docker and Docker Compose support
- 📡 **Data REST**: Auto-generated REST endpoints for entities
- 🔄 **Microservice Ready**: Clean architecture prepared for service decomposition

---

## 🛠️ Technologies

### Backend
- **Framework**: Spring Boot 3.1.5
- **Language**: Java 17
- **ORM**: Spring Data JPA, Hibernate
- **API**: Spring Data REST, Spring Web
- **Build Tool**: Maven 3.8+
- **Database**: MySQL 8.0

### Frontend
- **Framework**: Angular (latest)
- **Styling**: TailwindCSS
- **HTTP Client**: Angular HttpClient

### DevOps & Infrastructure
- **Containerization**: Docker, Docker Compose
- **Database Management**: PhpMyAdmin
- **Version Control**: Git

---

## 📦 Project Information

| Property | Value |
|----------|-------|
| **Group ID** | `com.radimyassine.smarthome` |
| **Artifact ID** | `smart-home-core` |
| **Version** | `1.0.0` |
| **Java Version** | 17 |
| **Spring Boot** | 3.1.5 |
| **Author** | Radim Yassine |
| **Role** | Lead Architect & Developer |

---

## 🚀 Getting Started

### Prerequisites

Before running the application, ensure you have the following installed:

- ✅ **Docker** & **Docker Compose** (recommended)
- ✅ **Java 17 SDK** (for local development)
- ✅ **Maven 3.8+** (for building from source)
- ✅ **MySQL 8.0** (if running without Docker)

### Installation & Execution

#### Option 1: Docker Compose (Recommended) 🐳

The easiest way to launch the complete ecosystem (Backend, Frontend, Database, PhpMyAdmin):

```bash
# Clone the repository
git clone https://github.com/RadimYassin/tp-24.git
cd tp-24

# Start all services
docker-compose up -d --build
```

#### Option 2: Local Development 💻

1. **Configure Database**
   
   Edit `Smart_Home_back/src/main/resources/application.properties`:
   ```properties
   spring.datasource.url=jdbc:mysql://localhost:3306/smart-house?serverTimezone=UTC
   spring.datasource.username=root
   spring.datasource.password=your_password
   ```

2. **Run Backend**
   ```bash
   cd Smart_Home_back
   mvn clean install
   mvn spring-boot:run
   ```

3. **Run Frontend**
   ```bash
   cd smartHome-front
   npm install
   npm start
   ```

---

## 🌐 Access Points

Once the application is running, access the following services:

| Service | URL | Description |
|---------|-----|-------------|
| 🖥️ **Backend API** | [http://localhost:8085](http://localhost:8085) | Spring Boot REST API |
| 🎨 **Frontend** | [http://localhost:80](http://localhost:80) | Angular Web Application |
| 🗄️ **Database** | `localhost:3306` | MySQL Database Server |
| 🔧 **PhpMyAdmin** | [http://localhost:8081](http://localhost:8081) | Database Management UI |

### API Endpoints

The REST API is automatically exposed via Spring Data REST:

- `GET /appareils` - List all devices
- `GET /appareils/{id}` - Get device by ID
- `POST /appareils` - Create new device
- `PUT /appareils/{id}` - Update device
- `DELETE /appareils/{id}` - Delete device

---

## 🏗️ Architecture

The project follows a **clean, layered architecture** designed for scalability and maintainability:

```
┌─────────────────────────────────────────┐
│         Angular Frontend (Port 80)      │
│         (smartHome-front)               │
└──────────────┬──────────────────────────┘
               │ HTTP/REST
┌──────────────▼──────────────────────────┐
│      Spring Boot Backend (Port 8085)    │
│      ┌──────────────────────────────┐   │
│      │  Controller/REST Layer       │   │
│      │  (Spring Data REST)          │   │
│      └──────────┬───────────────────┘   │
│      ┌──────────▼───────────────────┐   │
│      │  Service Layer               │   │
│      │  (Business Logic)            │   │
│      └──────────┬───────────────────┘   │
│      ┌──────────▼───────────────────┐   │
│      │  Repository Layer            │   │
│      │  (Spring Data JPA)           │   │
│      └──────────┬───────────────────┘   │
└─────────────────┼───────────────────────┘
                  │ JDBC
┌─────────────────▼───────────────────────┐
│      MySQL Database (Port 3306)         │
│      (smart-house)                      │
└─────────────────────────────────────────┘
```

### Layer Responsibilities

- **Controller/REST Layer**: Exposes RESTful endpoints via Spring Data REST
- **Service Layer**: Implements business logic and orchestrates operations
- **Repository Layer**: Handles data persistence with Spring Data JPA
- **Persistence Layer**: MySQL database with Hibernate ORM

### Package Structure

```
com.radimyassine.smarthome
├── controller/     # REST controllers (currently using Spring Data REST)
├── service/        # Business logic services
├── repository/     # JPA repositories
└── entity/         # JPA entities (domain models)
```

> **Note**: The current implementation uses a monolithic architecture but is designed to be **microservice-ready** for future decomposition.

---

## 📁 Project Structure

```
tp-24-main/
├── Smart_Home_back/          # Spring Boot Backend
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/com/example/appareil/
│   │   │   │   ├── controller/
│   │   │   │   ├── service/
│   │   │   │   ├── repository/
│   │   │   │   ├── entity/
│   │   │   │   └── AppareilApplication.java
│   │   │   └── resources/
│   │   │       └── application.properties
│   │   └── test/
│   ├── pom.xml
│   └── Dockerfile
├── smartHome-front/          # Angular Frontend
│   ├── src/
│   ├── package.json
│   └── angular.json
├── docker-compose.yml        # Multi-container orchestration
└── README.md                 # This file
```

---

## 🔧 Configuration

### Database Configuration

Edit `application.properties` to configure your database connection:

```properties
# MySQL Database Configuration
spring.datasource.url=jdbc:mysql://localhost:3306/smart-house?serverTimezone=UTC
spring.datasource.username=root
spring.datasource.password=your_password
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

# JPA/Hibernate Configuration
spring.jpa.hibernate.ddl-auto=update
spring.jpa.open-in-view=true

# Server Configuration
server.port=8085
```

### Docker Configuration

The `docker-compose.yml` orchestrates all services:

- **Backend**: Spring Boot application
- **Frontend**: Angular application
- **Database**: MySQL 8.0
- **PhpMyAdmin**: Database management interface

---

## 🧪 Testing

Run the test suite:

```bash
cd Smart_Home_back
mvn test
```

---

## 📚 Documentation

### API Documentation

The REST API follows Spring Data REST conventions. Access the API documentation at:

- **Base URL**: `http://localhost:8085`
- **HAL Browser**: `http://localhost:8085/browser/index.html` (if enabled)

### Entity Models

- **Appareil** (Device): Represents a smart home device with properties like name, status, type, etc.

---

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

---

## 👤 Author

**Radim Yassine**  
*Lead Architect & Developer*

- GitHub: [@RadimYassin](https://github.com/RadimYassin)
- Project Link: [https://github.com/RadimYassin/tp-24](https://github.com/RadimYassin/tp-24)

---

## 🙏 Acknowledgments

- Spring Boot Team for the excellent framework
- Angular Team for the powerful frontend framework
- MySQL for the reliable database system
- Docker for containerization support

---

<div align="center">

**⭐ Star this repository if you find it helpful!**

Made with ❤️ by Radim Yassine

</div>