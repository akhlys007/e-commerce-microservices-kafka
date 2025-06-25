# 🛍️ E-Commerce Microservices Platform with Kafka

A distributed, event-driven e-commerce application built using a microservices architecture, Apache Kafka for messaging, and containerized for scalability. Each service is designed for single responsibility and communicates asynchronously using Kafka topics to improve performance, fault tolerance, and scalability.

---

## 📦 Architecture Overview

This system follows a **modular microservices approach**, with each service handling a specific domain:

### 🔧 Core Services

- **API Gateway** – Central access point to route requests to internal services.
- **Auth Service** – Manages user authentication and JWT-based authorization.
- **Product Service** – CRUD operations for products, categories, and inventory.
- **Order Service** – Handles order creation, validation, and processing.
- **Payment Service** – Processes payments and integrates with payment providers.
- **Notification Service** – Sends emails/SMS for order updates and events.
- **Shipping Service** – Coordinates shipping logistics and updates order status.

### ↺ Asynchronous Communication

All services interact via **Apache Kafka**, using the following topics:

- `order-events`
- `payment-events`
- `inventory-updates`
- `shipping-updates`
- `notification-events`

This decouples services and improves resilience.

---

## 🚀 Tech Stack

| Layer                 | Technology                               |
| --------------------- | ---------------------------------------- |
| API Gateway           | Spring Cloud Gateway / Express.js        |
| Microservices         | Java (Spring Boot) / Node.js             |
| Messaging Queue       | Apache Kafka                             |
| Containerization      | Docker                                   |
| Orchestration         | Docker Compose / Kubernetes (optionally) |
| Database              | PostgreSQL / MongoDB (per service)       |
| Security              | JWT, HTTPS                               |
| Monitoring (optional) | Prometheus, Grafana, ELK                 |

---

## 📂 Project Structure

```
e-commerce-microservices-kafka/
├── api-gateway/
├── auth-service/
├── product-service/
├── order-service/
├── payment-service/
├── notification-service/
├── shipping-service/
├── kafka/
├── docker-compose.yml
└── README.md
```

---

## 🛠️ Setup & Running Locally

> Prerequisite: Docker, Docker Compose

```bash
# Start all services
docker-compose up --build
```

### Access Points:

- API Gateway: `http://localhost:8080`
- Kafka UI (optional): `http://localhost:8082`

---

## 🔪 Testing

Each service includes unit and integration tests:

```bash
# Example: auth-service
cd auth-service
./mvnw test
```

---

## 📬 Kafka Topics & Events

| Topic               | Publisher        | Subscribers                           |
| ------------------- | ---------------- | ------------------------------------- |
| order-events        | order-service    | payment-service, notification-service |
| payment-events      | payment-service  | order-service                         |
| inventory-updates   | product-service  | order-service                         |
| shipping-updates    | shipping-service | order-service                         |
| notification-events | all services     | notification-service                  |

---

## 🔐 Security

- JWT-based authentication
- Role-based access control (admin, customer)
- Secure internal service communication (via Kafka)

---

## 📈 Scalability & Fault Tolerance

- Stateless services: easy to scale horizontally
- Kafka: message durability, replay, and backpressure handling
- Graceful service degradation if dependent service is down

---

## 📜 License

This project is licensed under the MIT License.

---

## 👨‍💼 Author

Timothy Chelelgo – [GitHub](https://github.com/akhlys007) | [LinkedIn](https://linkedin.com/in/timothy-chelelgo-49872222b)

