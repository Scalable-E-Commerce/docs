# EC2 Deployment Documentation

## Overview

This project uses AWS EC2 instances for hosting and deploying services. Each service runs on a separate EC2 instance to ensure isolation, scalability, and ease of management. 

**PM2** is used to manage Node.js applications running on the EC2 instances. It provides process management, automatic restarts in case of failures, and logging.

---

## Deployment Strategy

### 1. **Dedicated EC2 Instances for Each Service**  
Each microservice in the application is deployed on its own EC2 instance. This setup provides:
   - **Service Isolation**: Each service runs independently, ensuring that one service's failure does not impact others.
   - **Scalability**: EC2 instances can be easily scaled up or down depending on the load for each service.
   - **Easy Management**: Managing each service separately simplifies updates, monitoring, and debugging.

### 2. **PM2 for Process Management**  
PM2 is used to run Node.js applications on EC2 instances as background processes. The benefits of using PM2 include:
   - **Process Monitoring**: PM2 keeps track of running services, ensuring they remain active and healthy.
   - **Automatic Restarts**: If a service crashes, PM2 automatically restarts it to maintain availability.
   - **Zero-Downtime Reloads**: PM2 allows for seamless restarts and deployments without service downtime.
   - **Log Management**: PM2 collects logs for each service, simplifying troubleshooting and performance monitoring.

---

## Deployment Flow

1. **CI/CD Pipeline Deployment**:
   - The CI/CD pipeline handles the deployment process automatically. It ensures that the application is built, tested, and packaged into a deployable artifact.
   - The artifact is transferred to the EC2 instance, where the application is extracted and started with PM2.
   
2. **Configuration via Environment Variables**:
   - Sensitive data like database credentials, API keys, and other configurations are stored as environment variables on the EC2 instance. This ensures security and makes it easy to modify configurations without needing to change the code.

3. **Service Start with PM2**:
   - Once the application is on the EC2 instance, it is started using PM2. PM2 reads the configuration from an `ecosystem.config.js` file (automatically transferred with the application) to determine how the application should be run. It manages:
     - Application startup commands.
     - Environment variables for each service.
     - Log files for easy troubleshooting.

4. **Monitoring and Restarting Services**:
   - PM2 ensures that all services remain running by monitoring their health. If a service crashes, PM2 will automatically attempt to restart it.
   - To scale services horizontally, additional EC2 instances can be added, and PM2 can manage multiple instances of the application for load balancing.

5. **Security and Access**:
   - EC2 instances are configured with security groups to control inbound and outbound traffic. Only necessary ports (such as 22 for SSH or the service-specific ports) are open.
   - Access to the EC2 instances is managed via SSH keys, and the security group ensures that only authorized IPs can access the services.

---

## Benefits of Using EC2 with PM2

- **Scalability**: As traffic grows, new EC2 instances can be added to scale the services. PM2 can handle multiple instances of each service seamlessly.
- **High Availability**: PM2 helps ensure that the services stay available by restarting them automatically in case of a crash.
- **Separation of Concerns**: Deploying each service on a dedicated EC2 instance ensures that they don't interfere with each other, making it easier to troubleshoot and manage.
- **Simplified Deployment**: With PM2 and the CI/CD pipeline in place, deployments become automatic and don't require manual intervention.

For more information on how PM2 and EC2 work together, check out the [PM2 Documentation](https://pm2.keymetrics.io/), [YouTube Reference Video](https://www.youtube.com/watch?v=EUIU2Gn0fXQ) and the [AWS EC2 Documentation](https://aws.amazon.com/ec2/).
