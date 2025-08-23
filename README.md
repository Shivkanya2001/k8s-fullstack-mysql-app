#  Kubernetes Fullstack MySQL Application  

This project demonstrates deploying a **Fullstack Application (Frontend + API + MySQL + Adminer)** on **Kubernetes** using persistent storage and secrets.  

## Features  
- **MySQL Database** with PersistentVolume (PV) and PersistentVolumeClaim (PVC).  
- **API Service** connected to MySQL (credentials stored in Kubernetes Secrets).  
- **Frontend (Web)** served via Deployment & Service.  
- **Adminer** for database management.  
- Modular Kubernetes YAML files for easy deployment.  

---

##  Project Structure  

```
k8s-fullstack-mysql-app/
│── k8s-manifests/
│   ├── db-deployment.yaml      # MySQL Deployment + Service
│   ├── mysql-pv-pvc.yaml       # Persistent Volume & Claim for MySQL
│   ├── mysql-secret.yaml       # Kubernetes Secret (DB credentials)
│   ├── api-deployment.yaml     # Backend API Deployment + Service
│   ├── web-deployment.yaml     # Frontend Web Deployment + Service
│   ├── adminer.yaml            # Adminer Deployment + Service
│
└── README.md
```



---

## ⚡ Prerequisites  

- A running **Kubernetes cluster** (Minikube, Kind, or Cloud Kubernetes).  
- `kubectl` installed & configured.  
- Docker images for **API** and **Frontend** pushed to **DockerHub** (or your private registry).  

---

## 🚀 Setup & Deployment  

### 1. Clone the Repository  
```bash
git clone https://github.com/Shivkanya2001/k8s-fullstack-mysql-app.git
cd k8s-fullstack-mysql-app/k8s-manifests
```

### 2. Apply Kubernetes Manifests  
```bash
kubectl apply -f mysql-secret.yaml
kubectl apply -f mysql-pv-pvc.yaml
kubectl apply -f db-deployment.yaml
kubectl apply -f app-config.yaml
kubectl apply -f api-deployment.yaml
kubectl apply -f web-deployment.yaml
kubectl apply -f adminer.yaml




kubectl delete -f mysql-secret.yaml
kubectl delete -f mysql-pv-pvc.yaml
kubectl delete -f db-deployment.yaml
kubectl delete -f app-config.yaml
kubectl delete -f api-deployment.yaml
kubectl delete -f web-deployment.yaml
kubectl delete -f adminer.yaml

```

### 3. Verify Deployments & Services  
```bash
kubectl get pods
kubectl get svc
```

---

## Accessing the Application  

- **Frontend Web App** → via NodePort of `web-service`  
- **Backend API** → via NodePort of `api-service`  
- **Adminer (DB Management UI)** → via NodePort of `adminer-service`  
