**Source:** [https://twitter.com/i/web/status/1884518401286037894](https://twitter.com/i/web/status/1884518401286037894)
**Original Post Date:** 2025-05-28 05:56:35

# Integrating AWS ECR, Terraform, and GitHub Actions for CI/CD Pipelines

## Introduction
Modern DevOps pipelines require seamless integration of infrastructure provisioning, container management, and continuous delivery. This article explores the implementation of a robust CI/CD pipeline using Amazon Elastic Container Registry (ECR), Infrastructure as Code with Terraform, and automated deployments via GitHub Actions. We'll cover secure repository configuration, image tagging strategies, security scanning, and cost optimization techniques.

## AWS ECR Setup with Terraform

Initialize your AWS provider in Terraform to manage cloud resources:

Configure ECR repositories for different environments (dev/staging/prod) with appropriate policies and lifecycle rules.

_Defines a secure, version-controlled ECR repository with lifecycle management._

```hcl
provider "aws" {
  region = var.aws_region
}

resource "aws_ecr_repository" "app_repo" {
  name                 = var.repository_name
  image_tag_mutability = "IMMUTABLE"
  lifecycle_policy      {
    rule {
      tag_prefix_list     = ["prod"]
      max_image_count     = 5
      tag_status          = "TAGGED"
      expiration_in_days  = 14
    }
  }
}
```

> **Note/Tip:** Use immutable tags to prevent accidental overwrites of production images.

> **Note/Tip:** Implement lifecycle policies to manage image retention and storage costs.

## GitHub Actions CI/CD Pipeline

Configure automated workflows for building, testing, and deploying containerized applications.

Leverage GitHub Secrets for secure credential management during the build process.

```yaml
name: Container CI/CD
on:
  push:
    branches:
      - main
type: workflow
jobs:
  build-and-deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Login to Amazon ECR
        id: login-ecr
        uses: aws-actions/amazon-ecr-login@v1
      - name: Build and push image
        env:
          AWS_REGION: ${{ secrets.AWS_REGION }}
          ECR_REGISTRY: ${{ steps.login-ecr.outputs.registry }}
        run: |
          docker build -t $ECR_REGISTRY/${{ github.repository }}:${GITHUB_SHA}} .
          aws ecr get-login-password --region $AWS_REGION | \
            docker login --username AWS --password-stdin $ECR_REGISTRY
          docker push $ECR_REGISTRY/${{ github.repository }}:${GITHUB_SHA}}
```

- Automate build processes
- Implement security scanning
- Deploy to multiple environments

## Key Takeaways

- Use Terraform for consistent, version-controlled ECR repository management.
- Implement automated workflows with GitHub Actions for reproducible deployments.
- Prioritize security through immutable tags and comprehensive image scanning.

## Conclusion
This integration creates a robust, scalable pipeline that ensures secure container deployment while maintaining infrastructure consistency. By leveraging Terraform's state management alongside GitHub Actions' automation capabilities, teams can achieve reliable, automated deployments with minimal operational overhead.

## External References

- [AWS ECR Documentation](https://docs.aws.amazon.com/AmazonECR/latest/userguide/welcome.html)
- [Terraform AWS Provider](https://registry.terraform.io/providers/hashicorp/aws/latest/docs)