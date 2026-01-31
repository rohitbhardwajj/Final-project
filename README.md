# 🌍 Wanderlust – MERN Travel Blog with Complete DevSecOps Pipeline

Wanderlust is a production-ready MERN travel blog application deployed on AWS EKS with a full DevSecOps CI/CD pipeline.  
This project demonstrates real-world cloud-native DevOps and security practices, including continuous integration, GitOps-based deployment, containerization, and monitoring.

---

## 📌 Project Summary

This project showcases an end-to-end DevSecOps workflow:

- Continuous Integration using Jenkins (Master–Worker architecture)  
- Security scanning with OWASP Dependency Check, SonarQube Quality Gates, and Trivy  
- Docker containerization for MERN application  
- GitOps-based Continuous Delivery using ArgoCD  
- Production deployment on AWS EKS (Kubernetes)  
- Cluster monitoring using Prometheus & Grafana  
- Automated Jenkins email notifications for pipeline status  

It demonstrates the complete lifecycle from code commit to secure production deployment with observability.

---

## 🚀 Features

- End-to-End DevSecOps Pipeline  
- Jenkins Master–Worker Architecture  
- OWASP Dependency Scan  
- SonarQube Quality Gates  
- Trivy Image Scanning  
- Docker Build & Push  
- GitOps Deployment using ArgoCD  
- AWS EKS Kubernetes Cluster  
- Helm Monitoring Stack (Prometheus & Grafana)  
- Email Notifications

---

## 🧰 Tech Stack

### ☁ Cloud & Infrastructure
- AWS EC2 – Jenkins Master & Worker setup  
- AWS EKS – Kubernetes cluster  
- AWS IAM – Roles & permissions  
- AWS VPC – Networking  
- eksctl – EKS cluster provisioning  

### 🔧 CI/CD & DevSecOps
- Jenkins – CI pipeline with Master–Worker architecture  
- GitHub – Source code management  
- Docker – Containerization of application  
- SonarQube – Static code analysis & Quality Gates  
- OWASP Dependency Check – Vulnerability scanning  
- Trivy – Docker image security scanning  
- ArgoCD – GitOps continuous deployment  
- Helm – Monitoring stack deployment  
- Gmail SMTP – Jenkins email notifications  

### ☸ Container Orchestration
- Kubernetes (AWS EKS) – Deployments, Services, Namespaces  
- GitOps manifests – Auto Sync & Self Healing  

### 📊 Monitoring & Observability
- Prometheus – Metrics collection  
- Grafana – Visualization dashboards  

### 💻 Full Stack
- MongoDB – Database  
- Express.js – Backend  
- React.js – Frontend  
- Node.js – Server runtime  
- Redis – Caching

---

## 🧠 What I Learned

### DevOps & Cloud
- Setup Jenkins Master–Worker architecture on AWS EC2  
- Built CI/CD pipelines integrating security checks  
- Deployed applications on Kubernetes via GitOps  
- Managed AWS EKS clusters, nodes, namespaces, and services  
- Learned Helm for monitoring stack deployment  
- Understood production-grade cloud-native deployment lifecycle  

### DevSecOps
- Implemented OWASP Dependency Check, SonarQube, and Trivy  
- Ensured secure and high-quality builds  
- Applied shift-left security approach  

### Kubernetes & GitOps
- Created and managed manifests for deployments, services, secrets  
- Configured ArgoCD for automated, self-healing deployments  
- Practiced GitOps workflow with auto-sync and rollback  

### CI/CD Workflow
- Automated stages: build → test → security scan → container push → deployment  
- Configured Jenkins email notifications  
- Integrated GitHub with Jenkins webhooks  

### Monitoring & Observability
- Setup Prometheus & Grafana for cluster and application monitoring  
- Learned alerting and dashboard configuration for observability  

---

## 🏗 Architecture

Developer → GitHub → Jenkins CI → Security Scans → Docker → ArgoCD → AWS EKS → Monitoring  

---

## 🔁 CI/CD Flow

1. Developer pushes code to GitHub  
2. Jenkins triggers pipeline  
3. OWASP Dependency Check scan  
4. SonarQube code quality analysis  
5. Docker build  
6. Trivy image scan  
7. Push image to registry  
8. Update Kubernetes manifests  
9. ArgoCD deploys to EKS  
10. Jenkins sends email notification

---
