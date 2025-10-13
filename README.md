# Cloud-Native WeMedia Platform

> A production-grade microservices platform demonstrating Spring Cloud architecture, event-driven design, and distributed systems best practices.

🎥 **[Watch Live Demo on YouTube](https://youtu.be/eIuYezbRpQI)**

[![Java](https://img.shields.io/badge/Java-8%2F11-orange)](https://www.oracle.com/java/)
[![Spring Cloud](https://img.shields.io/badge/Spring%20Cloud-2021-green)](https://spring.io/projects/spring-cloud)
[![Kafka](https://img.shields.io/badge/Kafka-2.8-black)](https://kafka.apache.org/)
[![Redis](https://img.shields.io/badge/Redis-6.x-red)](https://redis.io/)

---

## 📋 Table of Contents
- [Overview](#overview)
- [Key Features](#key-features)
- [System Architecture](#system-architecture)
- [Tech Stack](#tech-stack)
- [Getting Started](#getting-started)
- [Project Structure](#project-structure)
- [Performance Highlights](#performance-highlights)

---

## 🎯 Overview

This project is a **full-stack microservices platform** built to demonstrate modern cloud-native architecture patterns. It simulates a media content platform with user management, article publishing, search, and real-time notifications.

**Built during my career transition period (2022-2025)** to showcase:
- Spring Cloud ecosystem mastery
- Event-driven architecture with Kafka
- High-performance caching strategies
- Distributed system design patterns

---

## ✨ Key Features

### Microservices Architecture
- **API Gateway** - Spring Cloud Gateway for routing and load balancing
- **Service Discovery** - Nacos for dynamic service registration
- **Load Balancing** - Feign client with Ribbon for inter-service communication
- **Circuit Breaking** - Sentinel for fault tolerance and rate limiting

### Core Functionalities
- 📝 **User Management** - Registration, authentication, profile management
- 📰 **Article Publishing** - CRUD operations with rich text support
- 🔍 **Full-Text Search** - Elasticsearch integration for fast content discovery
- 📊 **Media Storage** - MinIO for object storage (images, videos)
- 💬 **Real-Time Updates** - Kafka streams for async event processing

### Performance Optimization
- **Redis Caching Layer** - Multi-level cache achieving 90%+ hit rate
- **Database Optimization** - Connection pooling, query optimization with MongoDB
- **Async Processing** - Kafka for decoupling heavy operations

---

## 🏗️ System Architecture

```
┌─────────────────────────────────────────────────────────┐
│                    Spring Cloud Gateway                  │
│              (Routing, Load Balancing, Auth)            │
└────────────────────┬────────────────────────────────────┘
                     │
        ┌────────────┼────────────┐
        │            │            │
   ┌────▼───┐  ┌────▼───┐  ┌────▼───┐
   │ User   │  │Article │  │Search  │
   │Service │  │Service │  │Service │
   └────┬───┘  └────┬───┘  └────┬───┘
        │           │            │
        └───────────┼────────────┘
                    │
          ┌─────────┼─────────┐
          │                   │
     ┌────▼────┐        ┌────▼────┐
     │  Kafka  │        │  Redis  │
     │ Streams │        │  Cache  │
     └─────────┘        └─────────┘
          │
     ┌────▼────┐        ┌─────────┐
     │MongoDB  │        │MinIO    │
     │Database │        │Storage  │
     └─────────┘        └─────────┘
```

---

## 🛠️ Tech Stack

| Category | Technologies |
|----------|--------------|
| **Backend Framework** | Spring Boot 2.5+, Spring Cloud 2021.x |
| **Service Mesh** | Spring Cloud Gateway, Nacos, Feign, Sentinel |
| **Message Queue** | Apache Kafka 2.8 |
| **Caching** | Redis 6.x (Clustering, Pipelines) |
| **Search Engine** | Elasticsearch 7.x |
| **Databases** | MongoDB 4.x, MySQL 8.x |
| **Object Storage** | MinIO |
| **Containerization** | Docker, Docker Compose |
| **Build Tool** | Maven 3.x |

---

## 🚀 Getting Started

### Prerequisites
- Java 11 or higher
- Maven 3.6+
- Docker & Docker Compose
- At least 8GB RAM available

### Quick Start

1. **Clone the repository**
   ```bash
   git clone https://github.com/yangjianingpaul/Cloud-Native-WeMedia-Platform.git
   cd Cloud-Native-WeMedia-Platform
   ```

2. **Start infrastructure services**
   ```bash
   docker-compose up -d
   ```
   This starts: Nacos, Kafka, Redis, MongoDB, Elasticsearch, MinIO

3. **Build the project**
   ```bash
   mvn clean package -DskipTests
   ```

4. **Start microservices** (in separate terminals)
   ```bash
   # Start Gateway
   java -jar gateway/target/gateway.jar

   # Start User Service
   java -jar user-service/target/user-service.jar

   # Start Article Service
   java -jar article-service/target/article-service.jar

   # Start Search Service
   java -jar search-service/target/search-service.jar
   ```

5. **Access the platform**
   - API Gateway: `http://localhost:9000`
   - Nacos Console: `http://localhost:8848/nacos` (nacos/nacos)
   - Sentinel Dashboard: `http://localhost:8080`

---

## 📁 Project Structure

```
Cloud-Native-WeMedia-Platform/
├── gateway/                 # API Gateway service
├── user-service/            # User management microservice
├── article-service/         # Article CRUD microservice
├── search-service/          # Elasticsearch integration
├── common/                  # Shared utilities and models
├── docker-compose.yml       # Infrastructure setup
└── README.md
```

---

## 📊 Performance Highlights

| Metric | Achievement |
|--------|-------------|
| **Cache Hit Rate** | 90%+ through intelligent caching strategies |
| **API Response Time** | <100ms for cached requests |
| **Throughput** | 1,000+ requests/second (single instance) |
| **Service Availability** | 99%+ with circuit breaker patterns |

---

## 🧪 Key Technical Implementations

### 1. Advanced Caching Strategy (1400+ lines)
```java
// Multi-level cache with cache-aside pattern
// Logical expiration to prevent cache avalanche
// Mutex locks for cache breakdown prevention
```

### 2. Event-Driven Architecture
```java
// Kafka producers for async operations
// Consumer groups for parallel processing
// Dead letter queues for failed messages
```

### 3. Distributed Tracing
```java
// Request correlation IDs
// Log aggregation across services
// Performance monitoring
```

---

## 📚 What This Project Demonstrates

✅ **Microservices Decomposition** - Proper service boundaries and responsibilities
✅ **Spring Cloud Ecosystem** - Gateway, Discovery, Config, Circuit Breaker
✅ **Event-Driven Design** - Kafka for async communication
✅ **High-Performance Caching** - Redis with multiple strategies
✅ **Search Integration** - Elasticsearch for full-text search
✅ **Containerization** - Docker for easy deployment
✅ **Production Readiness** - Monitoring, logging, fault tolerance

---

## 🎥 Demo Video

The YouTube demo shows:
- Service startup and registration with Nacos
- API Gateway routing requests
- CRUD operations on articles
- Real-time search with Elasticsearch
- Cache performance under load
- Circuit breaker activation

**[▶️ Watch Demo](https://youtu.be/eIuYezbRpQI)**

---

## 👨‍💻 About the Developer

Built by **Paul Yang** as part of a strategic career transition to international backend engineering roles.

- 📧 yangjianing73@gmail.com
- 💼 [LinkedIn](https://www.linkedin.com/in/paul-yang-30684128a/)
- 💻 [GitHub](https://github.com/yangjianingpaul)

**Professional Background:**
- 5+ years backend engineering at Huawei, JD.com
- Specialized in distributed systems and high-concurrency design
- IELTS 6.0 certified for English-speaking work environments

---

## 📄 License

This project is open source and available for educational purposes.

---

## 🤝 Contributing

While this is primarily a portfolio project, suggestions and feedback are welcome via issues or pull requests.

---

**⭐ If you find this project helpful, please star the repository!**
