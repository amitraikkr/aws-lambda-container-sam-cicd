# AWS Lambda Container Deployment CI/CD Pipeline

This project demonstrates a continuous integration and deployment (CI/CD) pipeline for an AWS Lambda function packaged as a container. The pipeline automates the process from code commit in GitHub through to build with AWS CodeBuild, storing the Docker image in Amazon ECR, and deploying the function to AWS Lambda.

## Prerequisites

- **AWS Account** and **AWS CLI** configured on your machine.
- **GitHub account** and repository for your Lambda function.
- **Dockerfile** in the root of your GitHub repository for building the Lambda container image.
- **Build specifications** (`buildspec.yml`) in your repository root.

## Getting Started

### Step 1: Create a GitHub Personal Access Token

1. Go to GitHub and generate a new personal access token (**Settings -> Developer settings -> Personal access tokens**).
2. Grant the token `repo` scope for access to private repositories (if necessary).
3. Note down the token for the CloudFormation stack creation.

### Step 2: Prepare Your Lambda Function

Ensure your repository contains:

- A `Dockerfile` for your Lambda function.
- A `buildspec.yml` defining the build and push process to ECR.

### Step 3: Deploy the CloudFormation Stack

Deploy the provided CloudFormation template to set up the CI/CD pipeline. You can use the AWS CLI:

### Step 4: Test Your Pipeline

- Make a commit to your GitHub repository to trigger the pipeline.
- Monitor the pipeline execution in the AWS CodePipeline console.
- Upon successful completion, your Docker image will be stored in ECR, and your Lambda function will be updated with the new image.

## Security

- Store sensitive information, such as your GitHub token, securely. Consider using AWS Secrets Manager.
- Review the permissions granted by the IAM roles in the CloudFormation template. Apply the principle of least privilege.

## Cleanup

To avoid incurring future charges, remember to delete resources created by this project:

```
aws cloudformation delete-stack --stack-name your-stack-name
```

Additionally, delete the ECR repository and the images within it if no longer needed.

---

This README.md is now formatted for better readability and usability on GitHub, guiding users through setting up their CI/CD pipeline for AWS Lambda container deployments.