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
