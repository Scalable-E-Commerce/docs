# Scalable E-Commerce Platform (Open Source)
![image](https://github.com/user-attachments/assets/28b17d45-7084-4bc5-9ba0-aac42347e575)

This is an open-source project designed to provide a modern and scalable solution for building e-commerce systems. By leveraging a microservices architecture, this platform ensures modularity, scalability, and reliability, making it an ideal choice for developers and businesses looking to create robust online stores.

## Overview
The platform is built using **Node.js** and **TypeScript**, with each core feature implemented as an independent microservice. This approach allows for:

- **Independent Development**: Each microservice can be developed, tested, and deployed independently.
- **Scalability**: Services can be scaled based on demand without affecting others.
- **Resilience**: Fault isolation ensures that issues in one service don’t bring down the entire system.


## Core Features

The platform includes the following core microservices:

1. [**User Service**](https://github.com/scalify-xyz/user-microservice)  
   Handles user registration, authentication, and profile management.  

2. [**Payment Service**](https://github.com/scalify-xyz/payment-microservice)  
   Handles payment processing, integrating with external payment gateways such as Stripe or PayPal.  

3. [**Notification Service**](https://github.com/scalify-xyz/notification-microservice)  
   Sends email and SMS notifications for events such as order confirmations and shipping updates.  

4. [**Product Service**](https://github.com/scalify-xyz/product-microservice)  
   Manages product listings, categories, and inventory.  

5. [**Cart Service**](https://github.com/scalify-xyz/cart-microservice)  
   Manages users’ shopping carts, including adding/removing items and updating quantities.  

6. [**Order Service**](https://github.com/scalify-xyz/order-microservice)  
   Processes orders, tracks order status, and manages order history.  
   
7. [**Client Web**](https://github.com/scalify-xyz/frontend-monolithic)  
   Provides a user-friendly interface for customers to browse products, manage their carts, and place orders.  

## Infrastructure

The platform is designed with cloud scalability in mind and utilizes:

- **CI/CD Pipeline**: Automated deployments to Amazon EC2 using GitHub Actions, ensuring efficient and consistent releases.
- **PostgreSQL**: A powerful relational database hosted on Amazon RDS for data persistence.
- **MongoDB**: A NoSQL database for handling unstructured or semi-structured data.
- **RabbitMQ**: Implements RabbitMQ (via Amazon MQ) for asynchronous communication between services.
- **Load Balancer**: Ensures even distribution of incoming traffic across multiple instances, improving reliability and performance.
- **API Gateway**: Serves as the single entry point for all client requests, routing them to the appropriate microservices.
- **Centralized Logging**: Aggregates logs from all microservices using the ELK stack (Elasticsearch, Logstash, Kibana).
- **Monitoring**: Uses Datadog for system monitoring.
- **Service Discovery**: Automatically detects and manages service instances using tools like Consul.

## Deployment
All microservices are containerized using Docker, with orchestration managed through Docker Compose for development and Kubernetes for production.

## Key Deployment Features:
- **EC2 Instances**: The platform is deployed on AWS EC2 instances for flexibility and scalability.
- **GitHub Actions**: Automates the build, test, and deployment processes.
- **Load Balancing**: Ensures high availability and efficient request handling.

## Documentation
For those who want a deeper understanding of the platform, comprehensive documentation is available in the [/docs folder.](https://github.com/scalify-xyz/docs/tree/main/docs) The documentation provides insights!

## Technology Stack for Microservices  
This platform includes a **boilerplate project** that explains the recommended technologies and architecture for building microservices. You can find it here: [Boilerplate for Scalable Microservices](https://github.com/scalify-xyz/boilerplate-microservice).  

## Contributing
Contributions are welcome! If you’re interested in improving the platform or adding new features, please follow these steps:

1. Fork the repository of the specific microservice you wish to contribute to.
2. Create a feature branch.
3. Submit a pull request with a detailed explanation of your changes.

## License
This project is licensed under the [MIT License](LICENSE). Feel free to use, modify, and distribute it as per the terms of the license.

## Contact
For questions or suggestions, feel free to open an issue in the respective repository or contact us directly.
