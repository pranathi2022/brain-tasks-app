# Brain Tasks App – Deployment on AWS EKS

This repository contains the complete setup to deploy a React application to a production-ready environment using Docker, Amazon ECR, Amazon EKS, and an automated CI/CD pipeline built with AWS CodePipeline and CodeBuild.

---

## 🚀 Application Overview

- **Application Type**: React
- **Application Port**: 3000
- **Deployment Platform**: Kubernetes (Amazon EKS)
- **Container Runtime**: Docker

---

## 🏗️ Architecture Overview

GitHub Repository  
→ AWS CodePipeline  
→ AWS CodeBuild  
→ Docker Image Build  
→ Amazon ECR  
→ kubectl Deployment  
→ Amazon EKS  
→ Kubernetes LoadBalancer  

---

## 🧰 Tools & Services Used

- :contentReference[oaicite:0]{index=0} – Version control
- :contentReference[oaicite:1]{index=1} – Containerization
- :contentReference[oaicite:2]{index=2} – Docker image storage
- :contentReference[oaicite:3]{index=3} – Kubernetes cluster
- :contentReference[oaicite:4]{index=4} – CI/CD orchestration
- :contentReference[oaicite:5]{index=5} – Build & deployment execution
- :contentReference[oaicite:6]{index=6} – Logging & monitoring

---

## 📦 Dockerization

The React application is containerized using Docker and served via **Nginx**.

### Docker Highlights
- Production-ready `nginx:alpine` base image
- Application served on **port 3000**
- Optimized static file serving

---

## ☸️ Kubernetes Deployment

### Deployment
- Runs multiple replicas for high availability
- Pulls Docker image from Amazon ECR

### Service
- Type: `LoadBalancer`
- Exposes application to the internet via AWS Load Balancer

---

## 🔁 CI/CD Pipeline Explanation

### Source Stage
- GitHub repository is connected to AWS CodePipeline
- Pipeline triggers automatically on code push

### Build & Deploy Stage (CodeBuild)
AWS CodeBuild performs the following actions:
1. Builds the Docker image
2. Pushes the image to Amazon ECR
3. Configures access to the EKS cluster using `kubectl`
4. Deploys the application using Kubernetes manifests

> ⚠️ **Note on CodeDeploy**  
> AWS CodeDeploy does not provide native EKS support in this account/region.  
> Deployment to EKS is therefore implemented using **kubectl as a custom deployment script via CodeBuild**, which is an AWS-recommended and industry-standard approach.

---

## 🧾 buildspec.yml Responsibilities

- Install `kubectl`
- Authenticate with Amazon ECR
- Build and push Docker image
- Deploy Kubernetes manifests using:
  ```bash
  kubectl apply -f deployment.yaml
  kubectl apply -f service.yaml
