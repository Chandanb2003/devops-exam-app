# DevOps Exam Application  
A simple Flask-based web application designed to practice and demonstrate end-to-end DevOps skills including CI/CD, Docker, SonarQube, Trivy, and Kubernetes (GKE).

---

## 📌 Features
- Flask backend with form submission  
- MySQL 5.7 database  
- Docker containerization  
- CI/CD using Jenkins  
- Code quality with SonarQube  
- Security scanning with Trivy  
- Deployment on GKE  
- Simple and production-like DevOps flow

---

## 🚀 Tech Stack
| Component | Technology |
|----------|------------|
| Backend  | Python Flask |
| Database | MySQL |
| CI/CD    | Jenkins |
| Scanning | Trivy, SonarQube |
| Containers | Docker, Docker Hub |
| Orchestrator | Kubernetes (GKE) |

---

## 📁 Project Structure
devops-exam-app/
├── backend/
│ ├── app.py
│ ├── Dockerfile
│ ├── requirements.txt
├── k8s/
│ ├── deployment.yaml
│ ├── service.yaml
│ ├── mysql-deployment.yaml
│ ├── mysql-service.yaml
│ ├── mysql-pvc.yaml
├── docker-compose.yml
└── Jenkinsfile

App: http://localhost:5000

MySQL: localhost:3306
Credentials: root / rootpass

⚙️ Jenkins CI/CD Pipeline (Steps)

Checkout code
SonarQube analysis
Build Docker image
Trivy scan
Push to Docker Hub
Deploy to GKE
Verify deployment
All implemented in Jenkinsfile.

Skills I Learnt

Jenkins CI/CD
Docker & Docker Hub
SonarQube Quality Gates
Trivy vulnerability scanning
Kubernetes deployments
GKE cloud deployment
MySQL integration
Production-like DevOps cycle


<img width="1440" height="900" alt="image" src="https://github.com/user-attachments/assets/82574545-1c8a-4c4e-8357-c4a29f929bca" />


<img width="800" height="500" alt="image" src="https://github.com/user-attachments/assets/6838bbfa-a039-44a0-8b1b-3377aab7324c" />

<img width="1440" height="900" alt="image" src="https://github.com/user-attachments/assets/e1ed8d81-0372-4109-ad4c-be42b70ae1a5" />

