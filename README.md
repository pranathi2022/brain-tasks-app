# Project brain-tasks-app – CI/CD to AWS EKS using ECR + CodeBuild + CodePipeline

## Overview
This project demonstrates how to containerize an application, store images in AWS ECR, deploy into AWS EKS using Kubernetes manifests, and automate the workflow using AWS CodePipeline and CodeBuild.

It includes monitoring and logs tracking using AWS CloudWatch.

---

## What I Implemented

### 1) Application Setup
- Cloned the given Git repository.
- Built the application and verified it runs correctly on the required port.

---

### 2) Dockerization
- Created a Dockerfile for the application.
- Built and tested the docker image locally.
- Verified output by running the container.

---

### 3) AWS ECR (Elastic Container Registry)
- Created an AWS ECR repository.
- Authenticated Docker to ECR.
- Tagged and pushed the image successfully into ECR.

---

### 4) AWS EKS (Kubernetes Cluster)
- Created an AWS EKS cluster with worker nodes.
- Verified cluster and node status using kubectl commands.

---

### 5) Kubernetes Deployment
- Created Kubernetes YAML files:
  - `deployment.yaml`
  - `service.yaml`
- Deployed application to EKS using:
  - `kubectl apply`
- Verified pods and services are running.
- Confirmed LoadBalancer service created successfully.

---

### 6) AWS CodeBuild
- Created a CodeBuild project.
- Connected it to the source repository.
- Used a managed environment image.
- Wrote `buildspec.yml` to automate:
  - Docker build
  - ECR push
  - Kubernetes deployment commands

---

### 7) AWS CodePipeline
- Created a CodePipeline pipeline with:
  - Source stage (GitHub)
  - Build stage (CodeBuild)
  - Deploy stage (EKS deployment)

---

### 8) Monitoring using CloudWatch Logs
- Verified CodeBuild execution logs inside CloudWatch.
- Verified deployment logs and pod logs.
- Used kubectl logs for application troubleshooting.

---

## Proof / Screenshots Included
The repository includes screenshots for:
- Docker build and run output
- ECR repository creation and image push
- EKS cluster and node status
- Kubernetes deployment and service output
- CodeBuild project configuration and logs
- CodePipeline execution flow
- LoadBalancer deployment proof
- CloudWatch logs

---

## Conclusion
This project demonstrates a complete AWS-native CI/CD pipeline that builds docker images, stores them in ECR, deploys to EKS, and tracks logs using CloudWatch.
