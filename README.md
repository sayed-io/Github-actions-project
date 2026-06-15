# 🚀 End-to-End CI/CD Pipeline Using GitHub Actions, Docker, SonarQube, Trivy, and AWS EKS

## 📌 Project Overview

This project demonstrates a complete DevOps CI/CD pipeline that automates the software delivery lifecycle from code commit to deployment on Amazon EKS using GitHub Actions.

The pipeline includes:

* Source Code Compilation
* Security Scanning
* Secret Detection
* Unit Testing
* SonarQube Code Analysis
* Quality Gate Validation
* Docker Image Build & Push
* Kubernetes Deployment on AWS EKS

---

## 🏗️ Architecture

```text
Developer Push
      │
      ▼
GitHub Repository
      │
      ▼
GitHub Actions (Self-Hosted Runner)
      │
      ├── Compile Stage
      │
      ├── Security Scan
      │      ├── Trivy Scan
      │      └── Gitleaks Scan
      │
      ├── Unit Testing
      │
      ├── Build & Package
      │
      ├── SonarQube Analysis
      │
      ├── Quality Gate Validation
      │
      ├── Docker Image Build
      │
      ├── Push to Docker Hub
      │
      └── Deploy to AWS EKS
                    │
                    ▼
              Kubernetes Cluster
```

---

## 🛠️ Tech Stack

| Technology     | Purpose                |
| -------------- | ---------------------- |
| GitHub Actions | CI/CD Automation       |
| Java 17        | Application Runtime    |
| Maven          | Build Tool             |
| Trivy          | Vulnerability Scanning |
| Gitleaks       | Secret Detection       |
| SonarQube      | Code Quality Analysis  |
| Docker         | Containerization       |
| Docker Hub     | Container Registry     |
| AWS EKS        | Kubernetes Platform    |
| kubectl        | Kubernetes Management  |
| AWS CLI        | AWS Authentication     |

---

## 📂 Repository Structure

```text
.
├── .github
│   └── workflows
│       └── cicd.yml
├── src
├── target
├── Dockerfile
├── ds.yml
├── pom.xml
└── README.md
```

---

## 🔄 CI/CD Pipeline Stages

### 1️⃣ Compile Stage

Compiles the Java application using Maven.

```bash
mvn compile
```

---

### 2️⃣ Security Scan Stage

#### Trivy Scan

Scans the repository for:

* Vulnerabilities
* Misconfigurations
* Dependency Risks
* Secrets

```bash
trivy fs .
```

#### Gitleaks Scan

Detects:

* Hardcoded Credentials
* API Keys
* AWS Secrets
* Passwords

```bash
gitleaks detect
```

---

### 3️⃣ Test Stage

Executes unit tests.

```bash
mvn test
```

---

### 4️⃣ Build & SonarQube Analysis

Packages the application.

```bash
mvn package
```

Generated Artifact:

```text
target/*.jar
```

Artifact is uploaded and used in later stages.

#### SonarQube Analysis

Performs:

* Code Quality Checks
* Bug Detection
* Security Analysis
* Code Smell Detection
* Maintainability Review

#### Quality Gate Validation

Pipeline proceeds only when SonarQube Quality Gate passes.

---

### 5️⃣ Docker Build & Push

Build Docker Image:

```bash
docker build -t sayedkhan28/bankapp:latest .
```

Push Image:

```bash
docker push sayedkhan28/bankapp:latest
```

---

### 6️⃣ Deploy to AWS EKS

Apply Kubernetes Manifest:

```bash
kubectl apply -f ds.yml
```

Verify Deployment:

```bash
kubectl get pods
kubectl get svc
kubectl get deployments
```

---

## 🔐 Required GitHub Secrets

### AWS Credentials

| Secret Name           |
| --------------------- |
| AWS_ACCESS_KEY_ID     |
| AWS_SECRET_ACCESS_KEY |
| EKS_KUBECONFIG        |

### SonarQube

| Secret Name |
| ----------- |
| SONAR_TOKEN |

### Docker Hub

| Secret Name     |
| --------------- |
| DOCKERHUB_TOKEN |

---

## ⚙️ Required GitHub Variables

| Variable Name      |
| ------------------ |
| SONAR_HOST_URL     |
| DOCKERHUB_USERNAME |

---

## 🖥️ Self-Hosted Runner Requirements

Install the following tools on the self-hosted runner:

```bash
java --version
mvn --version
docker --version
kubectl version --client
aws --version
git --version
```

Required:

* Java 17
* Maven
* Docker
* kubectl
* AWS CLI
* Git

---

## 🚀 How to Run Locally

### Clone Repository

```bash
git clone https://github.com/sayed-io/Github-Actions-Project.git
cd Github-Actions-Project
```

### Build Project

```bash
mvn clean package
```

### Run Application

```bash
java -jar target/*.jar
```

---

## ☁️ Kubernetes Commands

Check Pods:

```bash
kubectl get pods -A
```

Check Services:

```bash
kubectl get svc -A
```

Check Deployments:

```bash
kubectl get deployments -A
```

View Logs:

```bash
kubectl logs <pod-name>
```

---

## 📊 Pipeline Workflow

```text
Code Push
    │
    ▼
Compile
    │
    ▼
Security Scan
    │
    ▼
Unit Testing
    │
    ▼
Build & Package
    │
    ▼
SonarQube Analysis
    │
    ▼
Quality Gate
    │
    ▼
Docker Build
    │
    ▼
Docker Push
    │
    ▼
Deploy to AWS EKS
```

---

## 🎯 Key DevOps Concepts Demonstrated

* Continuous Integration (CI)
* Continuous Deployment (CD)
* Infrastructure Automation
* Security Scanning
* Secret Detection
* Containerization
* Kubernetes Deployment
* Artifact Management
* Code Quality Governance
* Cloud-Native Deployment

---

## 🔮 Future Enhancements

* Helm Charts
* ArgoCD GitOps
* Prometheus Monitoring
* Grafana Dashboards
* Slack Notifications
* Terraform Infrastructure Provisioning
* OWASP Dependency Check
* Multi-Environment Deployment

---

## 👨‍💻 Author

### Sayed IO

DevOps Engineer | Cloud & Kubernetes Enthusiast

### 🔗 Connect With Me

* GitHub: https://github.com/sayed-io
* Docker Hub: https://hub.docker.com/u/sayedkhan28

### 🚀 Core Skills

* AWS Cloud
* Docker
* Kubernetes (EKS)
* Terraform
* GitHub Actions
* Jenkins
* Linux Administration
* SonarQube
* Trivy Security Scanning
* CI/CD Automation
* Infrastructure as Code (IaC)

---

## ⭐ Support

If you found this project useful, please consider giving it a ⭐ on GitHub.

---

## 📜 License

This project is created for learning, demonstration, and DevOps practice purposes.
