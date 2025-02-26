
### Description

This knowledge base entry provides a comprehensive guide on setting up a DevOps project that covers various aspects of DevOps, including containerization, infrastructure as code, continuous integration and deployment (CI/CD), and monitoring. The project involves deploying a Java-based application on Amazon Web Services (AWS) using Docker, Nginx, Terraform, and GitHub Actions.

### Technical Content

#### Step 1: Find a Java-Based Application and Create Dockerfiles

* Identify a simple Java-based application that can be used for this project. For example, a Spring Boot application or a Java web application.
* Create a `Dockerfile` for the application to containerize it. The `Dockerfile` should include instructions for building the application, copying the necessary files, and exposing the required ports.

Example `Dockerfile`:
```dockerfile
FROM openjdk:8-jdk-alpine
ARG JAR_FILE=target/myapp.jar
COPY ${JAR_FILE} app.jar
ENTRYPOINT ["java","-jar","/app.jar"]
```
#### Step 2: Create AWS Account and IAM Credentials

* Create an AWS account if you don't already have one.
* Set up IAM credentials for your account. This will be used to authenticate with AWS services.

#### Step 3: Create Terraform Scripts

* Install Terraform on your machine if you haven't already.
* Create a Terraform script (`main.tf`) that creates an AWS ECR (Elastic Container Registry) for storing Docker images and an EC2 instance for hosting the application.

Example `main.tf`:
```terraform
provider "aws" {
  region = "us-west-2"
}

resource "aws_ecr_repository" "myapp" {
  name = "myapp"
}

resource "aws_instance" "myec2" {
  ami           = "ami-0c94855ba95c71c99"
  instance_type = "t2.micro"
}
```
#### Step 4: Add User-Data to Terraform Script

* Modify the `main.tf` file to include user-data that pre-installs Docker and Nginx on the EC2 instance.

Example `user-data`:
```terraform
resource "aws_instance" "myec2" {
  // ...
  user_data = <<-EOF
              #!/bin/bash
              sudo apt-get update -y
              sudo apt-get install docker.io -y
              sudo systemctl start docker
              sudo apt-get install nginx -y
              EOF
}
```
#### Step 5: Create GitHub Actions CI/CD Pipeline

* Create a new repository on GitHub for your project.
* Create a `github-actions.yml` file in the `.github/workflows` directory that defines the CI/CD pipeline.

Example `github-actions.yml`:
```yml
name: Build and Deploy

on:
  push:
    branches:
      - main

jobs:
  build-and-deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v2
      - name: Login to AWS
        uses: aws-actions/configure-aws-credentials@v1
        with:
          aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
          aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
          aws-region: 'us-west-2'
      - name: Build and push Docker image
        run: |
          docker build -t myapp .
          docker tag myapp:latest <account_id>.dkr.ecr.us-west-2.amazonaws.com/myapp:latest
          docker push <account_id>.dkr.ecr.us-west-2.amazonaws.com/myapp:latest
      - name: SSH into EC2 and pull latest image version
        uses: appleboy/ssh-action@master
        with:
          host: ${{ secrets.EC2_HOST }}
          username: ${{ secrets.EC2_USERNAME }}
          password: ${{ secrets.EC2_PASSWORD }}
          script: |
            docker pull <account_id>.dkr.ecr.us-west-2.amazonaws.com/myapp:latest
            docker run -d -p 8080:8080 <account_id>.dkr.ecr.us-west-2.amazonaws.com/myapp:latest
```
#### Step 6: Configure Nginx

* Create an `nginx.conf` file that exposes the application on port 80.

Example `nginx.conf`:
```nginx
http {
    server {
        listen 80;
        location / {
            proxy_pass http://localhost:8080;
            proxy_http_version 1.1;
            proxy_set_header Upgrade $http_upgrade;
            proxy_set_header Connection 'upgrade';
            proxy_set_header Host $host;
            proxy_cache_bypass $http_upgrade;
        }
    }
}
```
#### Step 7: Set Up AWS CloudWatch Monitoring

* Create a CloudWatch alarm that monitors the CPU utilization of the EC2 instance.

Example `cloudwatch.tf`:
```terraform
resource "aws_cloudwatch_metric_alarm" "myalarm" {
  alarm_name                = "myalarm"
  comparison_operator       = "GreaterThanThreshold"
  evaluation_periods        = "1"
  metric_name               = "CPUUtilization"
  namespace                 = "AWS/EC2"
  period                    = "300"
  statistic                 = "Average"
  threshold                 = "80"
  alarm_description         = "This metric alarm monitors ec2 instance cpu utilization"
  actions_enabled           = true
  alarm_actions             = [aws_sns_topic.mytopic.arn]
}
```
#### Step 8: Destroy Resources with Terraform

* Run `terraform destroy` to delete all resources created by Terraform.

### Advanced Options

* Use AWS IAM Role in GitHub Actions instead of standard credentials.
* Automate Terraform in another pipeline.
* Swap the EC2 instance with AWS ECS and automate deployment.

### Key Takeaways and Best Practices

* Containerize applications using Docker for easy deployment and management.
* Use infrastructure as code tools like Terraform to manage cloud resources.
* Implement CI/CD pipelines using GitHub Actions to automate build, test, and deployment processes.
* Monitor resources using CloudWatch to ensure optimal performance and scalability.

### References

* [Docker](https://www.docker.com/)
* [Terraform](https://www.terraform.io/)
* [GitHub Actions](https://github.com/features/actions)
* [AWS](https://aws.amazon.com/)
* [Nginx](https://www.nginx.com/)
## Source

- Original Tweet: [https://twitter.com/i/web/status/1884518401286037894](https://twitter.com/i/web/status/1884518401286037894)
- Date: 2025-02-25 20:20:20

*Last updated: 2025-02-25 20:20:20*