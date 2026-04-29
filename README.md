# 🚀 DevSecOps-URI-Shortener-Webservice
____

## 🖼️ System Architecture

<img width="1536" height="1024" alt="new-depi" src="https://github.com/user-attachments/assets/1769fa68-23f3-4639-bd06-82eb39bb72b9" />

## 📋 What This Project Does: 
- Provisions AWS infrastructure (EKS, VPC, EC2) using Terraform.
- Builds and scans Docker images with integrated security tools (Trivy, Gitleaks, SonarQube).
- Deploys a URL Shortener microservice to Kubernetes via ArgoCD (GitOps).
- Implements full monitoring stack (Prometheus, Grafana, Loki).
- Auto-triggers downstream pipelines for complete workflow automation.

## Main Application: 
- A URL Shortener web service that converts long URLs into short, shareable links. Built with Node.js, SQLlite, containerized with Docker, and deployed on Kubernetes via ArgoCD.

## 📂 Project Structure
           
#### 1️⃣ Infrastructure Pipeline 
<b> Purpose: </b>


- Automates AWS infrastructure provisioning with Terraform

<b> Key Features: </b> 

- Provisions EKS cluster, VPC, EC2 instances on AWS.
- Modular Terraform architecture with S3 remote state.
- Integrated security scanning: Gitleaks (secrets), Trivy (IaC), SonarQube (code quality).
- Auto-triggers all downstream pipelines on success.

<b> 🛠️ Tech Stack: </b>

- Terraform
- AWS (EKS/EC2/VPC)
- Jenkins
- Security Tools (Trivy, Gitleaks, SonarQube)
____

#### 2️⃣ CI Pipeline 
<b> Purpose:  
</b>

- Builds and pushes URL Shortener Docker images

<b> Key Features: </b> 

- Builds Docker image for URL Shortener application (Node.js + SQLlite).
- Trivy vulnerability scanning before image push.
- Multi-stage Docker builds for optimization.
- Pushes to Docker Hub/ECR.

<b> Application: Full-stack URL Shortener with REST API </b> 

- Frontend: HTML/CSS/JavaScript
- Backend: Node.js + Express
- Database: SQLlite

<b> 🛠️ Tech Stack: </b> 

- Docker
- Node.js
- PostgreSQL
- Jenkins
- Trivy
____

#### 3️⃣ GitOps Deployment Pipeline 
<b> Purpose: </b>


- Deploys applications using ArgoCD (GitOps approach)

<b> Key Features: </b> 

- Installs ArgoCD on EKS cluster.
- Deploys URL Shortener service with auto-scaling (3-10 pods).
- Deploys monitoring stack: Prometheus, Grafana, Loki, Promtail.
- Deploys security tools: Trivy Operator, Gitleaks, SonarQube.

<b> Components: </b> 

- ArgoCD Application: URL Shortener deployment + LoadBalancer service.
- Monitoring: Full observability with metrics, logs, and dashboards.
- Security: Runtime vulnerability scanning and code quality monitoring.

<b> 🛠️ Tech Stack: </b> 

- ArgoCD
- Kubernetes
- Helm
- Prometheus
- Grafana
- Loki
____

## 🔄 Workflow Automation: 
```
1. Push to Infra GitHub repo → Jenkins triggers:
   └─ Infra Pipeline (provision / update EKS infrastructure)

2. Infra Pipeline:
   ├─ Runs Terraform to provision AWS EKS cluster, VPC, and node groups
   └─ Configures base IAM roles, networking, and access for ArgoCD and workloads

3. After Infra Pipeline succeeds (first run), Jenkins automatically runs:
   ├─ ArgoCD installation job on the EKS cluster
   ├─ ArgoCD Application for the URL Shortener (GitOps repo: ArgoCD-Pipeline)
   ├─ ArgoCD Application for the Monitoring stack (Prometheus + Grafana + Loki)
   └─ ArgoCD Application for Security tools (Gitleaks, Trivy, SonarQube)

4. Push to CI GitHub repo (URL Shortener source code) → GitHub Webhook triggers:
   └─ Jenkins CI Pipeline (build, security scans, and image push)

5. CI Pipeline:
   ├─ Builds the URL Shortener Docker image
   ├─ Runs Gitleaks on the repository, Trivy on the image, and SonarQube on the code
   ├─ Pushes the image to DockerHub with an auto-incremented tag
   └─ Updates the ArgoCD GitOps repo (ArgoCD-Pipeline) with the new image tag

6. ArgoCD watches the CD repo:
   └─ Detects the updated image tag, auto-syncs, and deploys the new version to EKS

7. Monitoring and observability:
   ├─ Prometheus scrapes metrics from the URL Shortener and Kubernetes components
   ├─ Grafana provides dashboards for application, cluster, and CI/CD metrics
   └─ Loki + Promtail collect logs for troubleshooting and performance analysis

8. From zero to full environment (EKS + URL Shortener + monitoring + security tools).

```
Result: Fully automated infrastructure → build → deploy → monitor workflow with security integrated at every stage.
____

## 🛠️ Tech Stack: 

- Infrastructure	-> Terraform, AWS (EKS, EC2, VPC, S3)
- CI/CD	-> Jenkins, Docker, Git
- GitOps	-> ArgoCD, Kubernetes, Helm
- Security	-> Trivy, Gitleaks, SonarQube
- Monitoring	-> Prometheus, Grafana, Loki, Promtail
- Application	-> Node.js, Express, SQLlite
____

## 🚀 Quick Start 

#### Clone All Repositories: 
```
git clone https://github.com/Ahmedlebshten/Jenkins-Pipeline-Build-Infra.git

git clone https://github.com/Ahmedlebshten/Jenkins-CI-Pipeline.git

git clone https://github.com/Ahmedlebshten/ArgoCD-Pipeline.git
```
#### Access Deployed Service: 
``` 
kubectl get svc url-shortener
```
____

## 📊 Monitoring: 

- Prometheus: Collects metrics (requests/sec, response time, resource usage).
- Grafana: Pre-configured dashboards for URL Shortener, Kubernetes, and security.
- Loki: Centralized log aggregation from all pods.
____

## 💡 Skills Demonstrated: 

- ✅ DevSecOps (security shift-left)
- ✅ Infrastructure as Code (Terraform)
- ✅ CI/CD Pipeline Automation (Jenkins)
- ✅ GitOps Deployment (ArgoCD)
- ✅ Container Orchestration (Kubernetes)
- ✅ Cloud Infrastructure (AWS EKS)
- ✅ Monitoring & Observability (Prometheus/Grafana)
- ✅ Security Integration (Trivy/Gitleaks/SonarQube)
- ✅ Microservices Architecture (URL Shortener)
____

## 📂 Project Repositories:

#### 🔗 Infrastructure Pipeline 
- https://github.com/Ahmedlebshten/Jenkins-Pipeline-Build-Infra

#### 🔗 CI Pipeline 
- https://github.com/Ahmedlebshten/Jenkins-CI-Pipeline

#### 🔗 GitOps Deployment 
- https://github.com/Ahmedlebshten/ArgoCD-Pipeline

#### 🔗 DockerHub Repo 
- https://hub.docker.com/repository/docker/ahmedlebshten/url-shortener/general

## 📬 Connect With Me 

- GitHub: [https://github.com/Ahmedlebshten]
- LinkedIn: [https://www.linkedin.com/in/ahmedlebshten]
- Email: [ahmedlebshtenlebshten@gmail.com]

<div align="center">
⭐ Star this project if you find it useful!
DevSecOps Pipeline - Production Ready - Fully Automated

</div>
