**Source:** [https://twitter.com/i/web/status/1921943565602902111](https://twitter.com/i/web/status/1921943565602902111)
**Original Post Date:** 2025-05-27 22:43:09

# Terraform Project Structure for Environment-Specific Infrastructure as Code

## Introduction
Infrastructure as code (IaC) demands structured organization to maintain clarity, reusability, and scalability. This knowledge base item outlines a proven project structure that separates environment-specific configurations from reusable components. By following this pattern, teams can efficiently manage multi-environment deployments while reducing redundancy and improving maintenance.

## Core Directory Structure Overview

The Terraform project is organized into two main directories: `environments/` for environment-specific configurations and `modules/` for reusable infrastructure components. This separation ensures that common resources are defined once but can be adapted across different environments.

```plaintext
/terraform-project
├── environments/
│   ├── dev/
│   ├── staging/
│   └── prod/
└── modules/
    ├── network/
    ├── compute/
    └── data/
```

## Environment Directory Structure

Each environment directory (dev, staging, prod) contains essential configuration files: main.tf for core resources, variables.tf for inputs, provider.tf for cloud provider settings, outputs.tf for resource references, and a .tfvars file for environment-specific values.

The use of separate .tfvars files enables environment-specific configurations without modifying the base Terraform code.

- main.tf: Contains core resource definitions
- variables.tf: Declares input variables for customization
- provider.tf: Configures cloud provider settings
- outputs.tf: Defines resource references for other parts of the infrastructure

> **Note/Tip:** Always use separate .tfvars files to avoid hardcoding sensitive information in version control.

> **Note/Tip:** Consider using workspaces for environments, but keep configurations environment-specific for clarity.

## Module Organization

The modules directory contains reusable components like network (VPC/subnets), compute (EC2 instances), and data storage (S3 buckets). Each module follows a consistent structure with main.tf, variables.tf, and outputs.tf files.

Modular design improves maintainability by encapsulating common infrastructure patterns and making them reusable across environments.

- Network modules: Handle VPC configuration and subnet management
- Compute modules: Define instance types, AMIs, and security configurations
- Data modules: Configure storage solutions like S3 buckets with appropriate policies

## Implementation Best Practices

When implementing this structure, ensure proper variable scoping and module versioning. Use local variables for environment-specific values that shouldn't be exposed as outputs.

Consider adding a terraform.tfvars file in the root directory to override environment-specific variables when needed.

## Key Takeaways

- Separate environment configurations from reusable modules to improve maintainability
- Use .tfvars files for environment-specific values and avoid hardcoding sensitive information
- Organize modules by function (network, compute, data) with consistent file structures
- Define clear outputs in both environments and modules for cross-infrastructure communication

## Conclusion
This structured approach to Terraform project organization promotes maintainability, scalability, and clarity. By separating environment-specific configurations from reusable components and following a consistent module structure, teams can efficiently manage complex infrastructure deployments while minimizing duplication and potential errors.

## External References

- [Terraform Module Structure Documentation](https://www.terraform.io/language/modules/develop)
- [Infrastructure as Code Best Practices](https://www.hashicorp.com/resources/infrastructure-as-code-best-practices)


## Media

**Image Description:** The image depicts a structured directory layout for managing infrastructure as code using Terraform, a popular tool for automating cloud infrastructure provisioning. The layout is designed to organize configurations and modules in a modular, reusable, and environment-specific manner. Below is a detailed breakdown of the structure:

### **Main Directory Structure**
The overall structure is divided into two primary sections:
1. **Environments**
2. **Modules**

### **1. Environments Directory**
The `environments/` directory is used to separate configurations based on different environments (e.g., development, staging, production). This ensures that each environment has its own set of configurations, variables, and outputs, which can be tailored to the specific needs of that environment.

#### **Subdirectories under `environments/`:**
- **`dev/` (Development Environment)**
  - **`main.tf`**: Defines the core resources for the development environment. This file typically includes the main Terraform configurations for deploying resources.
  - **`variables.tf`**: Declares variables specific to the development environment. These variables can be used to customize resource configurations.
  - **`provider.tf`**: Configures the provider (e.g., AWS, Azure, etc.) for the development environment. This file ensures that the correct provider settings are used.
  - **`outputs.tf`**: Defines output values for the development resources, allowing users to retrieve important information about the deployed infrastructure.
  - **`dev.tfvars`**: Sets specific variable values for the development environment. This file is used to override default variables with environment-specific values.

- **`staging/` (Staging Environment)**
  - The structure is similar to the `dev/` directory, with the same files (`main.tf`, `variables.tf`, `provider.tf`, `outputs.tf`, `staging.tfvars`). The staging environment is used for testing and validating changes before deploying to production.

- **`prod/` (Production Environment)**
  - Similar to `dev/` and `staging/`, the production environment has its own set of configuration files. The `prod.tfvars` file is used to set production-specific variable values.

### **2. Modules Directory**
The `modules/` directory is designed to centralize reusable Terraform modules. These modules encapsulate common infrastructure components, making the codebase modular, maintainable, and reusable across different environments.

#### **Subdirectories under `modules/`:**
- **`network/`**
  - **`main.tf`**: Defines the network module, such as a VPC (Virtual Private Cloud), subnets, etc. This file contains the core configurations for network resources.
  - **`variables.tf`**: Declares input variables for the network module, such as VPC CIDR blocks, subnet configurations, etc.
  - **`outputs.tf`**: Defines outputs for the network module, such as VPC IDs, subnet IDs, etc. These outputs can be used by other modules or environments.

- **`compute/`**
  - **`main.tf`**: Defines the compute module, such as EC2 instances. This file contains configurations for deploying compute resources.
  - **`variables.tf`**: Declares input variables for the compute module, such as instance types, AMIs, etc.
  - **`outputs.tf`**: Defines outputs for the compute module, such as instance IPs and IDs.

- **`data/`**
  - **`main.tf`**: Defines the data module, such as an S3 bucket. This file contains configurations for data storage resources.
  - **`variables.tf`**: Declares input variables for the data module, such as bucket names, access policies, etc.
  - **`outputs.tf`**: Defines outputs for the data module, such as bucket names and ARNs (Amazon Resource Names).

### **Key Features and Technical Details**
1. **Modularity**: The use of modules ensures that common infrastructure components are reusable across different environments. This reduces redundancy and improves maintainability.
2. **Environment-Specific Configurations**: Each environment (`dev`, `staging`, `prod`) has its own directory with tailored configurations and variable values, ensuring that each environment can be managed independently.
3. **Variable Management**: The use of `.tfvars` files allows for environment-specific variable overrides, making it easy to manage different configurations without modifying the core Terraform files.
4. **Outputs**: Outputs are defined in each module and environment to expose important resource information, such as IDs, IPs, and ARNs, which can be used in other parts of the infrastructure or by external systems.
5. **Provider Configuration**: The `provider.tf` file ensures that the correct provider settings (e.g., AWS region, credentials) are used for each environment.

### **Summary**
The directory structure is designed to promote best practices in Terraform project organization, including modularity, environment separation, and reusable components. This structure ensures that infrastructure as code is maintainable, scalable, and easy to manage across different environments. The use of modules and environment-specific configurations enhances reusability and reduces complexity, making it easier to manage and deploy infrastructure consistently.
![The image depicts a structured directory layout for managing infrastructure as code using Terraform,...](./media/image_1.jpg)