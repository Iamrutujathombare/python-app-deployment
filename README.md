# 🚀 Python Application - Fully Automated CI/CD Pipeline using Jenkins & AWS EC2

This project demonstrates a **complete CI/CD pipeline** setup for deploying a Python application automatically onto a deployment server using **Jenkins**, **GitHub**, and **AWS EC2 Instances**.

## 🏗️ Project Architecture

GitHub Repository  →  Jenkins Server (Build & Deploy)  →  EC2 Deployment Server (Run App using PM2)

- **EC2 Instance 1:** Jenkins CI/CD Server
- **EC2 Instance 2:** Application Deployment & Execution Server

## ✅ Prerequisites

### On Both EC2 Instances:
| Software | Purpose |
|---------|---------|
| Python3 / pip | Run application |
| Git | Code cloning & management |
| OpenSSH | SSH communication |

### Extra on Jenkins Server:
| Software | Purpose |
|---------|---------|
| Jenkins | CI/CD automation |
| Required Plugins (SSH Agent Plugin) | Secure deployment |

### Extra on Deployment Server:
| Software | Purpose |
|---------|---------|
| PM2 | Run and monitor Python application |
| python3-venv | Create Python virtual environments |

## 🗂️ Project Repository Structure

python-app-CICD/
│── app.py
│── requirements.txt
│── Dockerfile
│── README.md
│── Jenkinsfile
└── test/

## 🔧 Steps to Configure Deployment Server (EC2)

1. Launch a new EC2 Ubuntu instance.
2. Connect via SSH.
3. Install necessary tools:
   sudo apt update
   sudo apt install -y python3 python3-venv python3-pip npm git
   sudo npm install -g pm2

4. Create directory for app:
   mkdir -p /home/ubuntu/pythonapp



   

## ⚙️ Jenkins Pipeline Setup

1. Login to Jenkins Server.
2. Go to Manage Jenkins → Credentials → Add Credentials
   - Type: SSH Username with Private Key
   - ID: node-key
   - Username: ubuntu
   - Private Key: (Paste PEM key)

3. Create New Pipeline Job → pipeline script from SCM
4. Repository URL: https://github.com/Iamrutujathombare/python-app-deployment.git
5. Branch: main
6. Save and Build

## 🧪 Jenkinsfile

(Include the pipeline script here as provided)

## 🔔 Webhook Setup

GitHub → Settings → Webhooks → Add Webhook

Payload URL:
http://<JENKINS-IP>:8080/github-webhook/

Content type: application/json
Events: Just push events

## 🎯 Final Result

Automatic deployment on each Git push using Jenkins + PM2.

## ✨ Author

**Rutuja Thombare**
