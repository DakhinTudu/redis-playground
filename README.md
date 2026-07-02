# 🌟 Redis Playground

Welcome to **Redis Playground**! This repository is a comprehensive, hands-on, Maven multi-module workspace showcasing various core and advanced Redis concepts integrated with Java and Spring Boot. 

It is designed to serve as a reference architecture, learning sandbox, and portfolio codebase for real-world Redis design patterns.

---

## 📂 Project Structure

This project is organized as a Maven multi-module system. Each directory demonstrates a distinct Redis architecture pattern:

| Module | Core Concepts Demonstrated | Tech Stack |
| :--- | :--- | :--- |
| **[`redis-demo`](./redis-demo)** | Distributed Caching, Cache Eviction Patterns, Custom JSON Serialization, JPA Auditing, OpenAPI/Swagger docs. | Java 21, Spring Boot 3.x, Spring Data JPA, Redis, MapStruct, Lombok, H2 |
| **[`redis-pub-sub`](./redis-pub-sub)** | Real-time Messaging, Event-driven architecture, Static & Pattern-based Wildcard Subscriptions, Broadcast Messaging. | Java 17+, Spring Boot 3.x, Spring Data Redis, Redis |

---

## 🛠️ Concepts & Features Covered

### 1. Distributed Caching (`redis-demo`)
*   **Write-Through / Cache Eviction**: Dynamic cache invalidation utilizing Spring Cache annotations (`@Cacheable`, `@CacheEvict`, `@Caching`).
*   **Serialization Rules**: Customized configuration setting up standard Jackson JSON serialization on Redis templates instead of binary formats.
*   **CRUD Integration**: Caches individual database entities by UUID and clears pagination caches respectively when mutations occur.

### 2. Event-Driven Messaging (`redis-pub-sub`)
*   **Decoupled Delivery**: Decoupled Publisher/Subscriber flow leveraging `RedisMessageListenerContainer`.
*   **Multi-Channel & Wildcard Routing**: Distribute events to specific static channels (e.g., `chat.general`, `chat.tech`) or dynamically capture stream groups via pattern matchers (`chat.any.*`).
*   **Uniform Broadcasts**: Broadcasts single-source message packets out to multiple active channels instantly.

---

## ⚙️ Prerequisites & Running Locally

### 1. Start a Redis Server
To run the modules, you need a running Redis instance on port `6379`. The easiest way is using Docker:
```bash
docker run --name redis-playground -p 6379:6379 -d redis
```

### 2. Build the Project
From the root directory (`redisplayground/`), compile and install all module dependencies using Maven:
```bash
mvn clean install
```

### 3. Run Individual Modules
Change directories to the module you want to run, and boot it. For example, to run the Redis Caching Demo:
```bash
cd redis-demo
./mvnw spring-boot:run
```
*(Or use `mvnw.cmd` on Windows command prompts).*

---

## 🚀 Future Demonstrations Roadmap
This sandbox is designed for ongoing Redis integration experiments. The following modules are planned:
*   [ ] **`redis-rate-limiter`**: Implementing API Rate Limiting using Redis token bucket or sliding window algorithms.
*   [ ] **`redis-locks`**: Distributed Locking utilizing Redisson to prevent race conditions in microservices.
*   [ ] **`redis-streams`**: Event sourcing and durable message queues using Redis Streams.
*   [ ] **`redis-session`**: Spring Session management offloaded to Redis for horizontal scalability.
