🚀 Full DevOps Workflow: Code Push → Jenkins Build → Ansible Deploy → Docker Container → Kubernetes Service
📌 Project Overview

This project demonstrates a complete CI/CD pipeline where a code push triggers Jenkins to build the application, deploys it via Ansible into Docker containers, and manages them through Kubernetes services.

The unique part of this setup is that all tools (Jenkins, Ansible, Docker, Kubernetes) are installed and configured manually – no prebuilt Docker images are used. This simulates a real-world production-like environment.



🔄 Workflow

Code Push (GitHub/Git)

Developer pushes code to the repository.

GitHub webhook notifies Jenkins.

Jenkins Build

Jenkins pulls the latest code.

Builds Docker image from custom Dockerfile.

Runs automated tests.

Triggers Ansible for deployment.

Ansible Deploy

Ansible provisions Docker containers on Kubernetes nodes.

Applies Kubernetes manifests (Deployment & Service).

Docker Containers

Application container is built from scratch using Python + Flask.

Kubernetes Service

Pods are managed by Kubernetes Deployment.

Application exposed via NodePort service.



📂 Project Structure
full-devops-workflow/
│── ansible/
│   ├── inventory.ini         # Target nodes for Ansible
│   ├── site.yml              # Master playbook
│   ├── roles/
│   │   ├── docker/
│   │   │   └── tasks/main.yml
│   │   ├── k8s/
│   │   │   └── tasks/main.yml
│── jenkins/
│   └── Jenkinsfile           # CI/CD pipeline definition
│── k8s/
│   ├── deployment.yaml       # Kubernetes Deployment
│   ├── service.yaml          # Kubernetes Service
│── app/
│   ├── Dockerfile            # Custom Dockerfile
│   ├── requirements.txt      # Python dependencies
│   ├── app.py                # Flask application
│   └── tests/
│       └── test_app.py       # Unit tests for app
│── README.md                 # Documentation



⚙️ Setup Guide
1️⃣ Prerequisites

Ensure the following are installed manually on respective servers/nodes:

Git (for version control)

Jenkins (CI tool)

Ansible (automation tool)

Docker (container runtime)

Kubernetes (cluster orchestration)

2️⃣ Jenkins Setup

Install Jenkins on a VM/server.

Configure Jenkins with:

GitHub webhook (trigger on git push).

Credentials for Ansible SSH access.

Add Jenkins pipeline using the provided Jenkinsfile.

✅ End-to-End Flow

Developer pushes code → GitHub webhook triggers Jenkins.

Jenkins checks out repo → builds Docker image → runs pytest tests.

Jenkins triggers Ansible playbook → deploys app to Kubernetes nodes.

Kubernetes runs app in pods (via Deployment).

App exposed through NodePort Service at:

http://<node-ip>:30001


🔑 Key Highlights

All tools (Jenkins, Ansible, Docker, Kubernetes) installed manually – no prebuilt images.

Demonstrates CI/CD automation skills from code commit → build → deploy → orchestrate.

Combines infrastructure automation (Ansible) with container orchestration (K8s).

Full production-grade DevOps pipeline.
