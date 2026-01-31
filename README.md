# 🌍 Wanderlust – MERN Travel Blog with Complete DevSecOps Pipeline

Wanderlust is a production-ready MERN travel blog application deployed on AWS EKS with a full DevSecOps CI/CD pipeline.

This project demonstrates:

- Jenkins based CI
- DevSecOps (OWASP, SonarQube, Trivy)
- Docker containerization
- GitOps CD using ArgoCD
- Kubernetes on AWS EKS
- Monitoring via Prometheus & Grafana

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
- Helm Monitoring Stack
- Email Notifications

---

## 🧰 Tech Stack

- AWS EC2
- AWS EKS
- Jenkins
- Docker
- SonarQube
- OWASP Dependency Check
- Trivy
- ArgoCD
- Helm
- Prometheus
- Grafana
- Redis
- MongoDB
- Express
- React
- Node.js

---

## 🏗 Architecture

Developer → GitHub → Jenkins CI → Security Scans → Docker → ArgoCD → AWS EKS → Monitoring

---

# ⚙ Phase 1 – DevSecOps Setup (Jenkins + Security Tools)

---

## 1️⃣ Jenkins Master Setup

Create EC2:

- t2.large
- 8GB RAM
- 29GB Storage
- Ubuntu

Install Docker:

```bash
sudo apt update
sudo apt install docker.io -y
sudo usermod -aG docker ubuntu && newgrp docker
Install Jenkins:

sudo apt install fontconfig openjdk-17-jre -y

wget -O /usr/share/keyrings/jenkins-keyring.asc https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key

echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian-stable binary/" | sudo tee /etc/apt/sources.list.d/jenkins.list

sudo apt update
sudo apt install jenkins -y


Access:

http://<jenkins-master-ip>:8080

2️⃣ Jenkins Worker Setup

Create second EC2 (same config).

Install Java + Docker:

sudo apt install openjdk-17-jre docker.io -y


Generate SSH keys from master:

ssh-keygen


Add public key to worker:

~/.ssh/authorized_keys


Add node:

Manage Jenkins → Nodes → Add Node

3️⃣ Install Jenkins Plugins
Manage Jenkins → Plugins


Install:

OWASP Dependency Check

SonarQube Scanner

Docker

Pipeline Stage View

4️⃣ SonarQube Setup

On Jenkins Master:

docker run -d --name sonarqube -p 9000:9000 sonarqube:lts-community


Create Token:

Administration → Security → Users → Token


Add token to Jenkins Credentials.

Configure Sonar:

Manage Jenkins → System → SonarQube

5️⃣ Trivy Setup (Worker)
sudo apt install trivy -y

6️⃣ OWASP Setup
Manage Jenkins → Tools → Dependency Check

7️⃣ Docker Permission Fix
chmod 777 /var/run/docker.sock

8️⃣ Email Notification

Open port 465 on Jenkins Master.

Create Gmail App Password.

Configure:

Manage Jenkins → System → Email Notification

☸ Phase 2 – AWS EKS Setup

Install AWS CLI:

curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o awscliv2.zip
unzip awscliv2.zip
sudo ./aws/install
aws configure


Install kubectl & eksctl.

Create Cluster:

eksctl create cluster --name=wanderlust --region=us-east-2 --version=1.30 --without-nodegroup


OIDC:

eksctl utils associate-iam-oidc-provider --cluster wanderlust --region us-east-2 --approve


Nodegroup:

eksctl create nodegroup --cluster=wanderlust \
--name=wanderlust \
--node-type=t2.large \
--nodes=2

🚀 Phase 3 – GitOps Deployment (ArgoCD)
kubectl create namespace argocd

kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml


Expose:

kubectl patch svc argocd-server -n argocd -p '{"spec":{"type":"NodePort"}}'


Password:

kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d


Add cluster:

argocd cluster add <cluster-context>


Create Application from UI.

Enable Auto Sync.

📊 Phase 4 – Monitoring (Helm)
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
kubectl create namespace prometheus
helm install monitoring prometheus-community/kube-prometheus-stack -n prometheus


Expose Grafana & Prometheus.

Password:

kubectl get secret -n prometheus monitoring-grafana -o jsonpath="{.data.admin-password}" | base64 --decode

🔁 CI/CD Flow

Git Push

Jenkins Trigger

OWASP Scan

SonarQube

Docker Build

Trivy Scan

Push Image

Update Manifest

ArgoCD Deploy

Email Notification

🧹 Cleanup
eksctl delete cluster --name wanderlust --region us-east-2