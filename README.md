# 🚀 Blue-Green Deployment with Kubernetes, Helm & Jenkins

This repository demonstrates a blue-green deployment pipeline using Kubernetes, Helm, and Jenkins. It shows how to deploy two versions of an application (blue and green), automate the process with Jenkins, and switch live traffic using Kubernetes Ingress.

## 📌 Features

- Blue-green deployment strategy
- Zero-downtime rollouts
- Jenkins CI/CD pipeline
- Helm-based Kubernetes deployments
- NGINX Ingress traffic control

## 🧰 Tech Stack

- Kubernetes
- Helm
- Jenkins
- NGINX Ingress Controller
- Docker

## 🧪 How It Works

1. Deploy the blue version of the app using Helm.
2. Expose it via an Ingress.
3. Deploy the green version in parallel.
4. Jenkins pipeline updates the Ingress to switch traffic.
5. Roll back easily if needed.

## 🚀 Getting Started

### 1. Prerequisites

- Kubernetes cluster (Minikube, EKS, GKE, etc.)
- Jenkins with kubectl and helm installed
- Docker registry (Docker Hub, GitHub Container Registry, etc.)
- NGINX Ingress Controller installed

### 2. Build and Push the App Image

docker build -t yourrepo/myapp:blue .
docker push yourrepo/myapp:blue

### 3. Deploy via Helm

helm upgrade --install myapp-blue ./charts/myapp \
  --set app.color=blue \
  --set app.image=yourrepo/myapp:blue

### 4. Run Jenkins Pipeline

- Jenkins pulls this repo
- Select "blue" or "green" in the DEPLOY_COLOR parameter
- Set the image tag
- Jenkins deploys and optionally switches Ingress traffic

## 🔄 Rollback Strategy

If something goes wrong:
- Rerun the pipeline
- Switch Ingress back to the stable color (e.g., from green to blue)

## 🧼 Cleanup

helm uninstall myapp-blue
helm uninstall myapp-green
helm uninstall myapp-ingress

## 📖 References

- Helm Docs: https://helm.sh/docs/
- Jenkins Pipeline Syntax: https://www.jenkins.io/doc/book/pipeline/syntax/
- NGINX Ingress Controller: https://kubernetes.github.io/ingress-nginx/
- Blue-Green Deployment Pattern: https://martinfowler.com/bliki/BlueGreenDeployment.html

## 👨‍💻 Author

Made for DevOps learners, bootcampers, and professionals exploring real-world CI/CD strategies.
