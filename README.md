🚀 Two-Tier Application Deployment using Jenkins & Docker on AWS EC2

        This project demonstrates a Two-Tier Application deployed on AWS EC2 using Docker, Docker Compose, and Jenkins CI/CD with GitHub Webhook automation.



🏗️ Architecture Overview
    
    Two-Tier Architecture
    Application Layer → Flask application (Docker container)
    Database Layer → MySQL database (Docker container)
    CI/CD → Jenkins pipeline triggered automatically on GitHub push




🧩 Architecture Diagram
       
        Developer -- git push --> GitHub Repository --  Webhook Trigger --> Jenkins (CI/CD) -- Build & Deploy -- >Docker Compose --  Flask App(port 5000) --  MySQL DB(port 3036) --> Access application.
            


🛠️ Technologies Used

    AWS EC2 (Ubuntu)
    Jenkins
    Docker & Docker Compose
    GitHub & GitHub Webhooks
    Flask (Python)
    MySQL


☁️ AWS Infrastructure Setup

    EC2 Instance Type: t3.medium
    Operating System: Ubuntu
    Security Group Rules:

    Port	Purpose
    22	     SSH
    8080	Jenkins
    5000	Application




📂 Project Structure

        two-tier-application/
        │
        ├── frontend/
        │   ├── app.py
        │   ├── requirements.txt
        │   └── Dockerfile
        │
        ├── database/
        │   └── init.sql
        │
        ├── docker-compose.yml
        ├── Jenkinsfile
        └── README.md



🔧 Installation & Setup Steps

1️⃣ Connect to EC2 Instance

    ssh -i key.pem ubuntu@<EC2_PUBLIC_IP>

2️⃣ Install Docker

    sudo apt update
    sudo apt install docker.io -y
    sudo usermod -aG docker ubuntu
    newgrp docker

3️⃣ Install Jenkins

    sudo apt install openjdk-17-jdk -y
    curl -fsSL https://pkg.jenkins.io/debian/jenkins.io-2023.key | sudo tee \
    /usr/share/keyrings/jenkins-keyring.asc > /dev/null
    
    echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
    https://pkg.jenkins.io/debian binary/ | sudo tee \
    /etc/apt/sources.list.d/jenkins.list > /dev/null
    
    sudo apt update
    sudo apt install jenkins -y
    sudo systemctl start jenkins


Access Jenkins:

    http://<EC2_PUBLIC_IP>:8080

🔁 Jenkins CI/CD Pipeline

    Jenkins Job Configuration
    Pipeline project
    SCM: Git
    Repository URL: GitHub repo
    Jenkinsfile from repository
    Jenkinsfile Flow
    Clone GitHub repository
    Build Docker images
    Deploy application using Docker Compose



🔗 GitHub Webhook Configuration

Webhook Payload URL:

    http://<EC2_PUBLIC_IP>:8080/github-webhook/


Content type: application/json

Trigger: Push events

Result: Automatic build & deployment on every code push



🌐 Application Access

After successful deployment:

    http://<EC2_PUBLIC_IP>:5000

The Project has successfully completed🚀
