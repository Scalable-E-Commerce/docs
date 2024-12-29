# GitHub Actions CI/CD Pipeline Documentation

## Required Secrets

For the CI/CD pipeline to work properly, the following secrets need to be configured in your repository:

- **AWS_ACCESS_KEY_ID**: Your AWS Access Key ID for authentication.
- **AWS_SECRET_ACCESS_KEY**: Your AWS Secret Access Key for authentication.
- **AWS_DEFAULT_REGION**: The AWS region where your EC2 instance is hosted.
- **AWS_SG_NAME**: The name of the AWS Security Group used for IP whitelisting.
- **HOST_IP**: The public IP address of your AWS EC2 instance.
- **SSH_KEY**: The private SSH key for accessing your AWS EC2 instance.

These secrets can be added under **Settings > Secrets and variables > Actions** in your GitHub repository.

## Pipeline Overview

### Workflow Name: **MicroService CI/CD**

The pipeline consists of the following jobs:

1. **Continuous-Integration_Testing**
   - Runs unit tests using Jest to ensure code quality.
   - Steps:
     - Check out the code.
     - Install dependencies.
     - Run tests.

2. **Continuous-Integration_Build**
   - Builds the application and validates the build folder.
   - Steps:
     - Check out the code.
     - Install dependencies.
     - Run the build process.
     - Validate the `build` folder.
     - Archive and upload the build artifact for later deployment.

3. **Continuous-Deployment_Authorize-Ip**
   - Dynamically adds the GitHub Actions runner's public IP to the AWS Security Group to allow SSH access.
   - Steps:
     - Fetch the public IP.
     - Authorize it in the Security Group.

4. **Continuous-Deployment_Delivery-AWS_EC2**
   - Deploys the build artifact to the AWS EC2 instance and runs the application.
   - Steps:
     - Set up SSH access.
     - Install Node.js and PM2 on the EC2 instance.
     - Download and copy the build artifact to the server.
     - Extract the artifact and run the application using PM2.

5. **Continuous-Deployment_Revoke-Ip**
   - Removes the GitHub Actions runner's IP from the AWS Security Group.
   - Steps:
     - Fetch the public IP.
     - Revoke access from the Security Group.

## Notes

- Ensure that the `build` folder contains all necessary files for the application to run in production, including `package.json` and `ecosystem.config.js`.
- This pipeline is designed for seamless deployment to an AWS EC2 instance, leveraging best practices for CI/CD.
- For additional information on configuring GitHub Actions secrets, refer to [GitHub Documentation](https://docs.github.com/en/actions/security-guides/encrypted-secrets).
