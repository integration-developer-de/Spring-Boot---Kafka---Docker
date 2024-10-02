# Spring Boot - Kafka - Docker

# Spring Boot Application Technical Design Document
## Introduction
- **Purpose**: Outline the design for a Spring Boot application that sends a string via API to another Spring Boot application, which then sends the string to a Kafka server hosted by Docker, consumes the message directly, and logs the message.
## Structure
```plaintext
.
├── HELP.md
├── kafka.yml
├── mvnw
├── mvnw.cmd
├── pom.xml
├── postgree.yml
├── Readme.md
├── src
│   ├── main
│   │   ├── java
│   │   │   └── com
│   │   │       └── example
│   │   │           └── spring_boot_kafka
│   │   │               ├── config
│   │   │               │   └── KafkaTopicConfig.java
│   │   │               ├── consumer
│   │   │               │   └── KafkaConsumer.java
│   │   │               ├── controller
│   │   │               │   └── MessageController.java
│   │   │               ├── models
│   │   │               │   └── Order.java
│   │   │               ├── producer
│   │   │               │   └── KafkaProducer.java
│   │   │               └── SpringBootKafkaApplication.java
```
## System Architecture
- **Overview**: High-level architecture of the system including Spring Boot applications, Kafka server, and Docker containers.
- **Components**:
    - Spring Boot Application (Sender)
    - Spring Boot Application (Receiver)
    - Kafka Server
    - Docker Containers
## Component Design
- **Spring Boot Application (Sender)**:
    - **Responsibilities**: Expose an API to send a string message.
    - **Endpoints**: API endpoint for sending messages.
- **Spring Boot Application (Receiver)**:
    - **Responsibilities**: Receive the string message, send it to Kafka, consume it, and log it.
    - **Endpoints**: API endpoint for receiving messages.
- **Kafka Server**:
    - **Responsibilities**: Message brokering.
    - **Configuration**: Hosted in Docker.
## Data Design
- **Message Format**: Simple string data.
- **Data Flow**: 
    - Sender API -> Receiver API -> Kafka Server -> Receiver Application -> Log
## Performance Metrics
- **Throughput**: High throughput for message processing.
- **Latency**: Low latency for real-time message logging.
- **Scalability**: Ability to scale Kafka and Spring Boot applications horizontally.
## User Interface Design
- **Not Applicable**: This is a backend service has Kafdrop as a User Interface (localhost:9000)
## API Documentation
- **Sender API**:
    - **Endpoint**: `/send` 
    - **Method**: POST
    - **Payload**: With a String message
## Error Handling and Logging
- **Error Handling**: Standard HTTP error codes and messages.
- **Logging**: Log all received messages and errors.
## Deployment Plan
- **Docker**: Use Docker Compose for deploying Kafka 
- **Sping Boot**: Use Spring Boot for deploying the applications.



