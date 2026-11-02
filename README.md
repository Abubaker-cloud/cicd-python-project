# Python CI/CD Pipeline with GitHub Actions & Docker

## 1. Project Overview

This project demonstrates an automated CI/CD pipeline for a Python Flask application using GitHub Actions, Docker, and Docker Hub.

The pipeline automatically tests the application, builds a Docker image, pushes it to Docker Hub, and deploys the updated application to a local Windows machine using a Self-hosted GitHub Actions Runner.

The main goal is to automate the software delivery process and demonstrate practical DevOps concepts.

## 2. Architecture

```text
Developer
    |
    v
GitHub Repository
    |
    v
GitHub Actions
    |
    v
Automated Testing (Pytest)
    |
    v
Docker Image Build
    |
    v
Docker Hub
    |
    v
Self-hosted Runner (Windows)
    |
    v
Pull Latest Docker Image
    |
    v
Deploy Docker Container
    |
    v
Health Check
    |
    v
Application Running
```

## 3. Technologies Used

| Technology     | Purpose                        |
| -------------- | ------------------------------ |
| Python         | Application Development        |
| Flask          | Web Framework                  |
| Pytest         | Automated Testing              |
| Git            | Version Control                |
| GitHub         | Source Code Management         |
| GitHub Actions | CI/CD Automation               |
| Docker         | Containerization               |
| Docker Hub     | Container Image Registry       |
| Windows        | Self-hosted Runner Environment |
| PowerShell     | Deployment Automation          |

## 4. Project Structure

```text
cicd-python-project/
│
├── .github/
│   └── workflows/
│       └── ci-cd.yml
│
├── app.py
├── test_app.py
├── requirements.txt
├── Dockerfile
├── .dockerignore
├── .gitignore
└── README.md
```

## 5. Application Features

The Flask application provides two endpoints:

**Home Endpoint**

```text
GET /
```

Returns a welcome message.

**Health Check Endpoint**

```text
GET /health
```

Returns the application health status.

Example response:

```json
{
  "status": "healthy"
}
```

## 6. CI/CD Pipeline

The pipeline consists of the following stages:

### Continuous Integration (CI)

1. Checkout Repository
2. Setup Python Environment
3. Install Dependencies
4. Run Automated Tests
5. Build Docker Image

### Continuous Delivery / Deployment (CD)

1. Login to Docker Hub.
2. Push Docker Image to Docker Hub.
3. Execute deployment using a Self-hosted Runner.
4. Pull the latest Docker Image.
5. Stop the previous container.
6. Deploy the updated container.
7. Verify deployment using a health check.

## 7. GitHub Actions Triggers

The workflow supports:

* Push events to the main branch.
* Pull requests targeting the main branch.

Automated deployment runs only after a successful push to the main branch.

## 8. Docker Image

The Docker image is published to Docker Hub.

**Docker Hub Repository:**

https://hub.docker.com/r/abubakeralmhlawi/cicd-python-app

Pull the image:

```powershell
docker pull abubakeralmhlawi/cicd-python-app:latest
```

Run the container:

```powershell
docker run -d --name cicd-app -p 5000:5000 abubakeralmhlawi/cicd-python-app:latest
```

## 9. Running the Project Locally

### Clone Repository

```powershell
git clone https://github.com/Abubaker-cloud/cicd-python-project.git

cd cicd-python-project
```

### Create Virtual Environment

```powershell
python -m venv venv

.\venv\Scripts\Activate.ps1
```

### Install Dependencies

```powershell
pip install -r requirements.txt
```

### Run Tests

```powershell
pytest -v
```

### Run Application

```powershell
python app.py
```

Access the application:

* http://localhost:5000
* http://localhost:5000/health

## 10. GitHub Secrets Configuration

The following repository secrets are required:

| Secret             | Description             |
| ------------------ | ----------------------- |
| DOCKERHUB_USERNAME | Docker Hub username     |
| DOCKERHUB_TOKEN    | Docker Hub access token |

These secrets allow GitHub Actions to authenticate securely with Docker Hub.

## 11. Self-hosted Runner

A Windows Self-hosted Runner is configured to execute deployment jobs on the local machine.

Requirements:

* Windows operating system.
* Docker Desktop installed and running.
* GitHub Actions Runner configured.
* Network connectivity to GitHub and Docker Hub.

The runner receives deployment jobs after the CI pipeline succeeds.

## 12. Project Results

The project successfully demonstrates:

* Automated CI/CD workflow.
* Automated application testing.
* Docker image building.
* Docker Hub integration.
* Automated container deployment.
* Self-hosted runner configuration.
* Application health verification.
* Failure handling.

## 13. Future Improvements

Planned enhancements:

* Docker Image Versioning.
* Automated Rollback.
* Improved deployment security.
* Deployment monitoring.
* Production deployment on AWS EC2.

## 14. Author

**Abubaker Abdallh**

B.Tech Information Technology Student

Aspiring Cloud & DevOps Engineer

GitHub: https://github.com/Abubaker-cloud

---

**Project:** Python CI/CD Pipeline

**Status:** Successfully Implemented
