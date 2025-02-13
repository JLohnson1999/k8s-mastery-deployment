# Kubernetes Deployment for k8s-mastery

This repository contains Kubernetes deployment files to deploy the application on **Google Kubernetes Engine (GKE)**.

## 🚀 Deployment Steps

### 1️⃣ Setup Google Cloud Project
Make sure you have a Google Cloud project ready. Set it in Cloud Shell:  
```bash
gcloud config set project YOUR_PROJECT_ID
```

### 2️⃣ Enable Required Services
```bash
gcloud services enable container.googleapis.com
gcloud services enable compute.googleapis.com
```

### 3️⃣ Create a GKE Cluster
```bash
gcloud container clusters create k8s-mastery-cluster \
  --zone us-central1-a \
  --num-nodes 2
```

### 4️⃣ Deploy to Kubernetes
Apply the Kubernetes manifests:
```bash
kubectl apply -f resource-manifests/
```

Check if services are running:
```bash
kubectl get pods
kubectl get services
```

### 5️⃣ Expose the Service
```bash
kubectl expose deployment sa-web-app-deployment --type=LoadBalancer --port=80 --target-port=5000
```

### 6️⃣ Get the External IP
```bash
kubectl get services
```
Look for the `EXTERNAL-IP` of the LoadBalancer and use it to access the application.

---

## 🐳 Docker Hub Images
The following Docker images were used in this deployment (Make sure they are publicly available):

- **sa-webapp**: [https://hub.docker.com/repository/docker/johnson397/sa-webapp/tags/latest/sha256-ab3d8540c94610d589e23c317575da69b6df7d6737951b6aac791ce381f987a9](https://hub.docker.com/repository/docker/johnson397/sa-webapp/tags/latest/sha256-ab3d8540c94610d589e23c317575da69b6df7d6737951b6aac791ce381f987a9)
- **sa-frontend**: [https://hub.docker.com/repository/docker/johnson397/sa-frontend/tags/latest/sha256-9a2a1a6226fdecc7dd49464ad86238330cde922d02e17da60fd09d069627508a](https://hub.docker.com/repository/docker/johnson397/sa-frontend/tags/latest/sha256-9a2a1a6226fdecc7dd49464ad86238330cde922d02e17da60fd09d069627508a)
- **sa-logic**: [https://hub.docker.com/repository/docker/johnson397/sa-logic/tags/latest/sha256-b38e3ff6a97faad96507411a24b9adeadaea339c9898e24dc1ba208072b10152](https://hub.docker.com/repository/docker/johnson397/sa-logic/tags/latest/sha256-b38e3ff6a97faad96507411a24b9adeadaea339c9898e24dc1ba208072b10152)

---

## 🔧 Repository Structure
```
k8s-mastery/
│── resource-manifests/    # Kubernetes YAML manifests
│── sa-frontend/           # Frontend React app
│── Dockerfile             # Docker config
│── README.md              # Documentation
```

## ✅ Done! 🚀
Now you have successfully deployed your application to GKE!
