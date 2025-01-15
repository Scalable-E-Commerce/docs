# Running All Microservices with a Single Docker Compose

If you want to run all the microservices of the platform at once, using a single `docker-compose` file, you can use the [Docker Compose Full Stack repository](https://github.com/Scalable-E-Commerce/docker-compose-full-stack). This repository contains a `docker-compose.yml` file that orchestrates all the platform services, making it easy to configure and start all the necessary containers for the full system.

### How to Use

1. **Clone the Repository**:
   Clone the repository to your local machine using the following command:
   ```bash
   git clone https://github.com/Scalable-E-Commerce/docker-compose-full-stack.git
   cd docker-compose-full-stack
   ```

2. **Bring Up the Containers**:
   Run the following command to start all services with Docker Compose:
   ```bash
    docker-compose up --build
   ```

   This will start all the microservices defined in the `docker-compose.yml` file, including databases, message queues, API Gateway, and other components required for the platform to function.

3. **Access the Platform**:
   After running `docker-compose up`, all services will be available for local development. You can access the client web interface (frontend), API endpoints, and other services defined in the `docker-compose.yml` file.

### Docker Compose Structure

The `docker-compose.yml` file contains configurations for:

- **Microservice containers**: All services such as User, Payment, Product, Notification, Cart, Order, and Client Web.
- **Databases**: PostgreSQL and MongoDB.
- **Message queue**: RabbitMQ.
- **Other components**: Logging, monitoring, etc.

This repository is ideal for anyone who wants to run the entire solution in a single environment without worrying about configuring each service individually.
