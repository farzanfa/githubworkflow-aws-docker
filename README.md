# AWS Terraform and Docker CI/CD Project

This project automates the provisioning of AWS infrastructure using Terraform, containerizes a simple web application with Docker, and sets up a CI/CD pipeline using GitHub Actions to validate and build the configurations.



## Features
- **Terraform**: Automates the creation of AWS resources (VPC, Subnet, and EC2 instance).
- **Docker**: Containerizes a simple `index.html` file using an NGINX image.
- **GitHub Actions**: Implements CI/CD to validate Terraform configurations and build Docker images.


## Prerequisites
To run this project, ensure you have:
1. **Tools Installed**:
   - [Terraform](https://www.terraform.io/)
   - [Docker](https://www.docker.com/)
   - [Git](https://git-scm.com/)

2. **AWS Setup**:
   - An AWS account.
   - An IAM user with programmatic access and required permissions.

3. **GitHub Secrets**:
   - Add your AWS credentials as secrets in the repository:
     - `AWS_ACCESS_KEY_ID`
     - `AWS_SECRET_ACCESS_KEY`


## Terraform Setup

### Steps:
1. **Write Configuration**:
   The `main.tf` file provisions:
   - A VPC with a subnet.
   - An EC2 instance.

2. **Run Terraform Commands**:
     ```bash
     terraform init
     terraform validate
     terraform plan
     terraform apply -auto-approve
     ```   
3. **Verify Resources**:
   Log in to the AWS Management Console to ensure the resources are created.

## Docker Setup

### Steps:
1. **Create `index.html`**:
   A simple web page displaying "Hello World".

2. **Write a `Dockerfile`**:
   The `Dockerfile` uses an NGINX base image to serve the `index.html`.

3. **Build and Run the Docker Image**:
   - Build the image:
     ```bash
     docker build -t hello-world .
     ```
   - Run the container:
     ```bash
     docker run -d -p 80:80 hello-world
     ```



## CI/CD Pipeline

### Overview
The GitHub Actions workflow is defined in `.github/workflows/main.yml`. It automates:
- **Terraform Validation**: Ensures the Terraform configuration is valid.
- **Docker Build**: Verifies that the Docker image builds successfully.

### How to Use:
1. Commit and push changes to the `main` branch.
2. Navigate to the **Actions** tab in your GitHub repository.
3. Monitor the workflow to ensure all steps pass. 
