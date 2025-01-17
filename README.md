# Microservices Messages (RabbitMQ)

## Overview

This repository demonstrates how to work with RabbitMQ, including its installation, using its web interface, and implementing RabbitMQ with Spring Boot for messaging between microservices. We will go through the process of:

1. **Installing RabbitMQ** using Docker.
2. **Using RabbitMQ's Web Interface** to set up exchanges, queues, and publish messages.
3. **Implementing RabbitMQ in Spring Boot** with two microservices: Producer and Consumer.
4. **Working with MySQL** to insert data from the producer into a MySQL database in the consumer service.

## 1) Installation

### RabbitMQ Docker Setup
- The RabbitMQ Docker image used is the stable version `3.12.9-management`.
- We configure the Docker container with ports:
  - **15672** for the web UI.
  - **5672** for RabbitMQ broker.
- The following command runs the RabbitMQ image:
  ```
  docker run -d --hostname rabbitmq-server --name rabbitmq -p 15672:15672 -p 5672:5672 rabbitmq:3.12.9-management
  ```

### Web Interface
- Default username: `guest`
- Default password: `guest`
- Once logged in, you can manage exchanges, queues, and publish messages via the UI.

## 2) Manipulation (Interface)

### Working with the Web UI
- Add an **Exchange**: Create a new exchange called `2iteExchange`.
- Add a **Queue**: Create a queue named `2iteQueue` and bind it to the exchange.
- **Publish a Message**: Send a message to the queue and verify the messages received in the queue.

## 3) Microservices (Spring Boot with RabbitMQ)

### Spring Boot Services

In this section, we implement RabbitMQ in Spring Boot with two microservices:
- **Producer Service**: Sends messages to RabbitMQ.
- **Consumer Service**: Listens for messages from RabbitMQ and processes them.

These services are configured dynamically in the Spring Boot application using the `spring-boot-starter-amqp` dependency.

- The producer sends a `CustomMessage` with a unique ID and timestamp.
- The consumer listens to the queue and prints out the received message.

### Test Communication:
- Start the **Producer Service**.
- Start the **Consumer Service**.
- Use Postman to test publishing a message to RabbitMQ, which the consumer then processes.

## 4) Microservices with MySQL Integration

In this section, the producer sends data through RabbitMQ, and the consumer stores this data in a MySQL database.

- The producer service sends a `User` object as a message.
- The consumer service receives the message and stores the user data into the MySQL database.

## Demo Video
You can check out the demo video here: 


https://github.com/user-attachments/assets/cdc396c1-29cd-4fae-86e1-adade04e5996



## Contributors  

- **Amal Ourajim** (GitHub: [AmalOur](https://github.com/AmalOur))  
- **Mohamed Lachgar** (ResearchGate: [M. Lachgar](https://www.researchgate.net/profile/Mohamed-Lachgar))  

---

Feel free to contribute and share your feedback to enhance this project!

