This project is designed to provide a comprehensive understanding of DevOps practices, covering containerization using Docker, infrastructure as code with Terraform, CI/CD pipelines with GitHub Actions, cloud platforms with AWS, and monitoring with AWS CloudWatch. By completing this project, individuals can enhance their CVs and prepare for technical interviews in the field of DevOps.

#### Technical Content
The project involves the following steps:

1. **Find a Java-based Application and Create Dockerfiles**: Begin by selecting a simple Java application. Create Dockerfiles for each component of the application to containerize them. This step introduces you to Docker and containerization.
   
   Example of a basic `Dockerfile`:
   ```dockerfile
   FROM openjdk:8-jdk-alpine
   ARG JAR_FILE=target/myapp.jar
   COPY ${JAR_FILE} app.jar
   ENTRYPOINT ["java","-jar","/app.jar"]
   ```
2. **Create AWS Account and IAM Credentials**: Sign up for an AWS account and create IAM credentials. These will be used to interact with AWS services programmatically.
3. **Terraform Scripts for AWS Resources**: Write Terraform scripts to create:
   - An AWS Elastic Container Registry (ECR) to store Docker images.
   - An EC2 instance to host the application.
   
   Example of a Terraform script snippet:
   ```terraform
   provider "aws" {
     region = "us-west-2"
   }
   
   resource "aws_ecr_repository" "example" {
     name = "example/ec2-repo"
   }
   
   resource "aws_instance" "example" {
     ami           = "ami-0c55b159cbfafe1f4"
     instance_type = "t2.micro"
     vpc_security_group_ids = [aws_security_group.example.id]
     user_data = <<-EOF
               #!/bin/bash
               sudo apt update
               sudo apt install -y docker.io
               sudo systemctl start docker
               sudo systemctl enable docker
               EOF
   }
   ```
4. **Enhance Automation with User-Data**: Include a `user-data` script in your Terraform configuration for the EC2 instance. This script automates the installation of Docker and Nginx on the EC2 instance upon launch.
5. **GitHub Actions CI/CD Pipeline**:
   - **Build a Docker Image**: Use GitHub Actions to automate building a Docker image from your application's codebase.
   - **Push Docker Image to AWS ECR**: Configure the pipeline to push the built Docker image to the AWS ECR repository created earlier.
   - **SSH into EC2 and Pull Latest Image Version**: Automate SSHing into the EC2 instance and pulling the latest version of the Docker image from ECR.
   
   Example `yaml` file for GitHub Actions:
   ```yaml
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
         - name: Login to AWS ECR
           uses: aws-actions/login@v1
         - name: Build and push image
           run: |
             docker build -t myapp .
             docker tag myapp:latest $AWS_ACCOUNT_ID.dkr.ecr.$AWS_REGION.amazonaws.com/myapp:latest
             docker push $AWS_ACCOUNT_ID.dkr.ecr.$AWS_REGION.amazonaws.com/myapp:latest
         - name: SSH into EC2 and pull image
           uses: appleboy/ssh-action@master
           with:
             host: $EC2_HOST
             username: $EC2_USERNAME
             password: $EC2_PASSWORD
             script: |
               docker pull $AWS_ACCOUNT_ID.dkr.ecr.$AWS_REGION.amazonaws.com/myapp:latest
               docker run -d -p 80:80 $AWS_ACCOUNT_ID.dkr.ecr.$AWS_REGION.amazonaws.com/myapp:latest
   ```
6. **Configure Nginx**: Configure Nginx on the EC2 instance to expose your application.
7. **Set Up AWS CloudWatch Monitoring**:
   - Create alerts based on CPU utilization thresholds for the EC2 instance.
   - Monitor the instance's performance and adjust as necessary.

8. **Destroy Resources with Terraform**: Finally, use Terraform to destroy all resources created during this project to avoid unnecessary costs.

#### Advanced Steps
For those looking to further enhance their project:
1. **Use AWS IAM Role in GitHub Actions**: Instead of using standard credentials, configure an AWS IAM role for the GitHub Actions workflow.
2. **Automate Terraform in Another Pipeline**: Create a separate pipeline that automates Terraform deployments.
3. **Swap EC2 Instance with AWS ECS and Automate Deployment**: Replace the EC2 instance with an AWS Elastic Container Service (ECS) cluster and automate container deployment.

#### Key Takeaways and Best Practices
- **Containerization**: Docker simplifies application packaging and deployment.
- **Infrastructure as Code (IaC)**: Terraform allows for version-controlled, repeatable infrastructure deployments.
- **CI/CD Pipelines**: GitHub Actions automates testing, building, and deployment processes.
- **Monitoring and Alerting**: AWS CloudWatch provides insights into resource utilization and performance.

#### References
- [Docker](https://www.docker.com/)
- [Terraform](https://www.terraform.io/)
- [GitHub Actions](https://github.com/features/actions)
- [AWS](https://aws.amazon.com/)
- [AWS CloudWatch](https://aws.amazon.com/cloudwatch/)
## Source

- Original Tweet: [https://twitter.com/i/web/status/1884518401286037894](https://twitter.com/i/web/status/1884518401286037894)
- Date: 2025-02-24 13:04:13

*Last updated: 2025-02-24 13:04:13*