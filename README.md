# NutriSync CI/CD Pipeline

A fully automated CI/CD pipeline for NutriSync, a web application that helps users sync health data and manage supplements. This project demonstrates end-to-end DevOps practices using Jenkins, Docker, and AWS.

## 🚀 Project Overview

NutriSync is built with Python (Flask) and features a complete CI/CD pipeline that automates building, testing, code quality analysis, and deployment across staging and production environments.

## 🛠️ Technologies Used

- **CI/CD:** Jenkins
- **Containerization:** Docker, Docker Compose, Docker Hub
- **Cloud Platform:** AWS EC2
- **Code Quality:** SonarQube
- **Version Control:** GitHub
- **Backend:** Python (Flask)
- **Testing:** Pytest

## 📋 Pipeline Stages

### 1. Build Stage
- Creates Python virtual environment
- Installs dependencies from `requirements.txt`
- Builds Docker image tagged as `nutrisync:latest`
- Pushes image to Docker Hub

### 2. Test Stage
- Runs unit tests using pytest
- Verifies core application functionality
- Generates test coverage report

### 3. Code Quality Analysis
- Integrates with SonarQube for static code analysis
- Analyzes code smells, bugs, and security vulnerabilities
- Generates metrics for maintainability, reliability, and security

### 4. Deploy Stage (Staging)
- Uses Docker Compose to deploy to staging environment
- Spins up application container on AWS EC2
- Enables testing in production-like environment

### 5. Release Stage (Production)
- Promotes application to production after successful staging tests
- Deploys using `docker-compose.prod.yml`
- Runs on separate AWS EC2 instance for isolation

## 🏗️ Architecture
GitHub → Jenkins → Docker Build → Docker Hub
↓
SonarQube Analysis
↓
Staging (EC2) → Production (EC2)

## 📊 Key Metrics

- **Deployment Time:** Reduced from 2+ hours (manual) to ~15 minutes (automated)
- **Test Coverage:** Comprehensive unit and integration tests
- **Environment Isolation:** Separate EC2 instances for staging and production
- **Code Quality:** Automated analysis on every commit

## 🚦 Getting Started

### Prerequisites
- Jenkins server
- Docker and Docker Compose
- AWS EC2 instances
- SonarQube server
- Docker Hub account

### Setup

1. **Clone the repository**
```bash
   git clone <repository-url>
   cd nutrisync

Configure Jenkins

Install required plugins (Docker, SonarQube, GitHub)
Set up credentials for Docker Hub and AWS
Create Jenkins pipeline using Jenkinsfile


Configure SonarQube

Set up SonarQube server on EC2
Configure quality gates and analysis rules
Add SonarQube token to Jenkins


Set up AWS EC2

Launch separate instances for staging and production
Install Docker and Docker Compose
Configure security groups

Run Pipeline

Push code to GitHub
Jenkins automatically triggers pipeline
Monitor build progress in Jenkins dashboard

🧪 Testing
Run tests locally:
bashpytest tests/
pytest --cov=app tests/  # With coverage report
🔒 Security

Code security analysis via SonarQube
Vulnerability scanning in pipeline
Isolated production environment
Secure credential management in Jenkins

📈 Future Improvements

 Add monitoring and alerting (Prometheus/Grafana)
 Implement blue-green deployment
 Add automated rollback mechanism
 Integrate container security scanning
 Add performance testing stage
