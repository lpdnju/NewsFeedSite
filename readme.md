# RabbitMQ News Feed Site 

A news feed web site built with java and rabbitmq. 

## Features

- **Real-time news broadcasting** — publish messages from a CLI client and instantly see them on the web portal
- **RabbitMQ message queue** — decouples the publisher (client) from the consumer (service) via a `news` queue
- **WebSocket push** — the service broadcasts received messages to all connected browser clients over WebSocket
- **Multi-client support** — multiple browser sessions can connect simultaneously and receive live updates

## Tech Stack

| Layer | Technology |
|---|---|
| Language | Java 8+ |
| Build Tool | Apache Maven |
| Message Broker | RabbitMQ 3 (AMQP) |
| Web Framework | Java Servlet (Jakarta EE / `javax.servlet`) |
| WebSocket | JSR-356 (`javax.websocket`) |
| Web Server | Eclipse Jetty (via `jetty-maven-plugin`) |
| Frontend | JSP + JavaScript (WebSocket client) |
| Containerization | Docker (RabbitMQ with management UI) |

## Quick Start

1. start rabitmq
```
docker run -d --name rabbitmq -p 5672:5672 -p 15672:15672 rabbitmq:3-management
```

2. start web site service
```
cd service
mvn clean jetty:run
```
Open portal: http://localhost:8080/demo/

3. start client
```
cd client
mvn clean package
mvn exec:java "-Dexec.mainClass=com.example.App"
```
Enter message: hello

Portal shows the received message: hello

## License

This project is provided as-is for educational and demonstration purposes.