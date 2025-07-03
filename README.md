# S3-Bucket-Policies

## Overview

This project demonstrates how to use Terraform to automate the creation and management of an AWS S3 bucket with lifecycle policies and tagging. It also includes a GitHub Actions workflow for CI/CD automation.

## Theory

### What is an S3 Bucket?

Amazon S3 (Simple Storage Service) is an object storage service that allows you to store and retrieve any amount of data at any time. An S3 bucket is a container for storing objects (files, data, etc.).

### S3 Bucket Policies

A bucket policy is a resource-based AWS Identity and Access Management (IAM) policy that you can use to allow or deny actions on your S3 bucket and the objects in it. Policies are written in JSON and can control access at the bucket or object level.

### S3 Lifecycle Rules

Lifecycle rules allow you to automatically manage objects in your bucket. For example, you can transition objects to a cheaper storage class (like STANDARD_IA) after a certain number of days, or delete them after they are no longer needed. This helps optimize storage costs and automate data management.

**Example in this project:**  
Objects older than 30 days are automatically moved to the STANDARD_IA storage class.

### Tagging

Tags are key-value pairs that help you organize and identify your AWS resources. In this project, the S3 bucket is tagged with `env = "dev"`.

### CI/CD with GitHub Actions

Continuous Integration and Continuous Deployment (CI/CD) automates the process of testing and deploying your infrastructure code.  
This project uses a GitHub Actions workflow to:
- Check out the repository
- Set up Terraform
- Configure AWS credentials
- Run `terraform init`, `terraform plan`, and `terraform apply` automatically on every push to the `main` branch

## Usage

1. **Clone the repository:**
   ```sh
   git clone https://github.com/Pratyushaa94/S3-Bucket-Policies.git
   cd S3-Bucket-Policies
   ```

2. **Set your AWS credentials** as GitHub repository secrets:
   - `AWS_ACCESS_KEY_ID`
   - `AWS_SECRET_ACCESS_KEY`

3. **Edit `terraform.tfvars`** to set your desired bucket name and region.

4. **Push changes to the `main` branch** to trigger the workflow and apply your infrastructure changes automatically.

## Files

- `main.tf`: Terraform configuration for the S3 bucket, lifecycle rule, and tags.
- `variables.tf`: Variable definitions for bucket name, region, etc.
- `terraform.tfvars`: Actual values for the variables.
- `outputs.tf`: Outputs for the bucket name and ARN.
- `.github/workflows/deploy.yml`: GitHub Actions workflow for CI/CD automation.

---

Feel free to modify the configuration and workflow to suit