# AWS-DevOps-CI-CD

# AWS DevOps for Beginners: Todo List Web App Deployment

## Overview

Welcome to an exciting journey into the world of AWS DevOps! This comprehensive guide will walk you through the steps to set up a robust CI/CD pipeline for deploying a Todo List web app. By leveraging AWS **CodeCommit**, **CodeBuild**, **CodeDeploy**, and **CodePipeline**, you'll not only learn the basics but also witness the deployment of your own Nginx-powered web application.

## Prerequisites

Before diving into the tutorial, make sure you have the following:

- AWS account with the necessary permissions.
- Git installed on your local machine.

## Step 1: Setting Up CodeCommit

# 1.1 Create a CodeCommit Repository

Navigate to the AWS Management Console, select **CodeCommit**, and click "Create Repository." Provide a unique name for your repository.

# 1.2 Create IAM User and Generate Credentials

Create an IAM user with administrative permissions and generate HTTPS Git credentials for the IAM user.

# 1.3 Clone Repository Locally

Clone the repository to your local machine using the HTTPS URL and the credentials generated.

# 1.4 Create Project Files

Inside the local repository, create the following files: `index.html`, `app.js`, `styles.css`. Push the changes to the CodeCommit repository.

## Step 2: Configuring CodeBuild

# 2.1 Create a Build Project

Open the AWS **CodeBuild** console and create a new build project. Use the provided `buildspec.yaml` file as the build specification.

# 2.2 Configure Artifacts

Edit the build project to specify an S3 bucket and a folder for storing artifacts. Create a folder in the S3 bucket named `artifact`.

# 2.3 Run the Build

Trigger a build in the **CodeBuild** console. Verify that the build is successful, and artifacts are stored in the S3 bucket.

## Step 3: Implementing CodeDeploy

# 3.1 Create CodeDeploy Application

Navigate to the AWS **CodeDeploy** console and create a new application named `demo-app-application`. Specify the compute platform as `ec2/on-premises`.

# 3.2 Create Deployment Group

Create a deployment group and associate it with an EC2 instance.

# 3.3 Install CodeDeploy Agent on EC2 Instance

SSH into the EC2 instance. Execute the provided shell script to install the CodeDeploy agent.

# 3.4 Create `appspec.yaml` and Scripts (Continued)

Create an `appspec.yaml` file with the provided content. Create a `scripts` folder with `install_nginx.sh` and `start_nginx.sh` scripts.

# 3.5 Build and Deploy (Continued)

Trigger another **CodeBuild** to ensure the latest code artifact is in the S3 bucket. Create a deployment in **CodeDeploy**, specifying the S3 location of the artifact.

# 3.6 Configure EC2 Role (Continued)

Create a role for the EC2 instance with permissions to access S3 and CodeDeploy. Attach the role to the EC2 instance.

# 3.7 Restart CodeDeploy Agent (Continued)

On the EC2 instance, restart the CodeDeploy agent.

## Step 4: Setting Up CodePipeline

# 4.1 Configure CodePipeline

Open the AWS **CodePipeline** console and create a new pipeline. Add **CodeCommit** as the source, **CodeBuild** as the build stage, and **CodeDeploy** as the deploy stage.

# 4.2 Create Pipeline

Click "Create Pipeline" to initiate the pipeline. The pipeline will automatically fetch code from **CodeCommit**, build using **CodeBuild**, and deploy using **CodeDeploy**.

![Screenshot from 2024-01-04 08-48-03](https://github.com/Kritika257/AWS-DevOps-CI-CD/assets/85506435/f7ee84ba-3dc5-4d74-aec0-77925eec1827)

![Screenshot from 2024-01-04 08-48-21](https://github.com/Kritika257/AWS-DevOps-CI-CD/assets/85506435/1937e703-472a-401a-b06e-773788e97045)

![Screenshot from 2024-01-04 08-48-32](https://github.com/Kritika257/AWS-DevOps-CI-CD/assets/85506435/584f6fd1-1f6c-4693-ba0f-b34869d96ebd)

# 4.3 Test the Web App

Access the public IP of the EC2 instance. Verify that the Todo List web app is successfully deployed.

![Screenshot from 2024-01-04 09-25-25](https://github.com/Kritika257/AWS-DevOps-CI-CD/assets/85506435/e13d12f4-6366-48fa-b56b-6acb1a931c6a)
