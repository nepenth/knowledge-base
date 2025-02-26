
### Description

This guide provides a step-by-step approach to setting up a DevOps project that covers various aspects of modern software development, including containerization, infrastructure as code, continuous integration and delivery (CI/CD), and monitoring. By following this guide, you will gain hands-on experience with popular tools like Docker, Nginx, Terraform, GitHub Actions, and AWS.

### Technical Content

#### Prerequisites

* Basic understanding of Java programming language
* Familiarity with Linux command-line interface
* AWS account with IAM credentials

#### Step 1: Find a Java-Based Application and Create Dockerfiles for Components

First, identify a simple Java-based application that you can use for this project. Then, create separate Dockerfiles for each component of the application. For example, if your application has a web server and a database, you would create two separate Dockerfiles.

```dockerfile
# Dockerfile for web server
FROM openjdk:8-jdk-alpine
COPY target/web-server.jar /app/
EXPOSE 8080
CMD ["java", "-jar", "/app/web-server.jar"]
```

```dockerfile
# Dockerfile for database
FROM postgres:12-alpine
ENV POSTGRES_USER=myuser
ENV POSTGRES_PASSWORD=mypassword
ENV POSTGRES_DB=mydb
```

#### Step 2: Create AWS Account and IAM Credentials

Create an AWS account and set up IAM credentials. You will need these to authenticate with AWS services.

* Log in to the AWS Management Console.
* Navigate to the IAM dashboard.
* Create a new user or use an existing one.
* Generate access keys for the user.

#### Step 3: Create Terraform Scripts to Create AWS ECR and EC2

Next, create Terraform scripts to set up an AWS Elastic Container Registry (ECR) and an EC2 instance. You will store your Docker images in the ECR and deploy them to the EC2 instance.

```terraform
# Configure AWS provider
provider "aws" {
  region = "us-west-2"
}

# Create ECR repository
resource "aws_ecr_repository" "my-repo" {
  name = "my-java-app"
}
```

```terraform
# Create EC2 instance
resource "aws_instance" "my-ec2" {
  ami           = "ami-abcd1234"
  instance_type = "t2.micro"
}
```

#### Step 4: Add User-Data to Terraform Script

Add user-data to your Terraform script to pre-install Docker and Nginx on the EC2 instance.

```terraform
# Configure user-data for EC2 instance
resource "aws_instance" "my-ec2" {
  # ...
  user_data = <<-EOF
              #!/bin/bash
              sudo apt-get update -y
              sudo apt-get install docker.io -y
              sudo systemctl start docker
              sudo apt-get install nginx -y
              sudo systemctl start nginx
              EOF
}
```

#### Step 5: Create GitHub Actions CI/CD Pipeline

Create a GitHub Actions pipeline to automate the build, test, and deployment process.

```yml
# .github/workflows/ci-cd.yml
name: Java App CI/CD

on:
  push:
    branches:
      - main

jobs:
  build-and-deploy:
    runs-on: ubuntu-latest
    steps:
      # Build Docker image
      - name: Build and push Docker image
        run: |
          docker build -t my-java-app .
          docker tag my-java-app:latest $AWS_ACCOUNT_ID.dkr.ecr.$AWS_REGION.amazonaws.com/my-java-app:latest
          docker push $AWS_ACCOUNT_ID.dkr.ecr.$AWS_REGION.amazonaws.com/my-java-app:latest

      # SSH into EC2 and pull latest image version
      - name: Deploy to EC2
        uses: appleboy/ssh-action@master
        with:
          host: $EC2_INSTANCE_PUBLIC_IP
          username: $EC2_USERNAME
          key: $EC2_PRIVATE_KEY
          script: |
            docker pull $AWS_ACCOUNT_ID.dkr.ecr.$AWS_REGION.amazonaws.com/my-java-app:latest
            docker run -d -p 8080:8080 $AWS_ACCOUNT_ID.dkr.ecr.$AWS_REGION.amazonaws.com/my-java-app:latest
```

#### Step 6: Configure Nginx to Expose the Application

Configure Nginx to expose the Java application running on the EC2 instance.

```nginx
# /etc/nginx/nginx.conf
http {
    server {
        listen 80;
        location / {
            proxy_pass http://localhost:8080;
            proxy_set_header Host $host;
            proxy_set_header X-Real-IP $remote_addr;
        }
    }
}
```

#### Step 7: Set Up AWS CloudWatch Monitoring

Set up AWS CloudWatch monitoring to track CPU utilization and create alerts.

```terraform
# Create CloudWatch metric alarm
resource "aws_cloudwatch_metric_alarm" "cpu-alarm" {
  alarm_name          = "EC2-CPU-Utilization"
  comparison_operator = "GreaterThanThreshold"
  evaluation_periods  = 1
  metric_name         = "CPUUtilization"
  namespace           = "AWS/EC2"
  period              = 300
  statistic           = "Average"
  threshold           = 80
}
```

#### Step 8: Destroy Resources with Terraform

Finally, destroy all resources created using Terraform.

```bash
terraform destroy
```

### Advanced Options

* Use AWS IAM Role in GitHub Actions instead of standard credentials.
* Automate Terraform in another pipeline.
* Swap the EC2 instance with AWS ECS and automate deployment.

### Key Takeaways and Best Practices

* Containerization using Docker provides a consistent and reliable way to deploy applications.
* Infrastructure as code using Terraform enables version control and reproducibility of infrastructure configurations.
* CI/CD pipelines using GitHub Actions automate the build, test, and deployment process.
* Monitoring using AWS CloudWatch provides real-time insights into application performance.

### References

* [Docker](https://www.docker.com/)
* [Nginx](https://www.nginx.com/)
* [Terraform](https://www.terraform.io/)
* [GitHub Actions](https://github.com/features/actions)
* [AWS](https://aws.amazon.com/)
## Source

- Original Tweet: [https://twitter.com/i/web/status/1884518401286037894](https://twitter.com/i/web/status/1884518401286037894)
- Date: 2025-02-26 01:31:32

*Last updated: 2025-02-26 01:31:32*