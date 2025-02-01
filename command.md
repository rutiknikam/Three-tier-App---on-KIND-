# 📌 Commands Guide

## 🐳 Docker Commands
### 🔹 Check running containers
```
docker ps
```
### 🔹 Check Docker version
```
docker --version
```

## ☸️ Kubernetes (kubectl) Commands
### 🔹 Check Kubernetes version
```
kubectl version
```
### 🔹 Get cluster information
```
kubectl cluster-info --context kind-prn-cluster
```
### 🔹 Get nodes in the cluster
```
kubectl get nodes
```
### 🔹 Get available namespaces
```
kubectl get namespace
```
### 🔹 Create a new namespace
```
kubectl create namespace monitoring
```
### 🔹 Get pods in monitoring namespace
```
kubectl get pods -n monitoring
```
### 🔹 Get services in monitoring namespace
```
kubectl get svc -n monitoring
```
### 🔹 Port forward Prometheus service
```
kubectl port-forward svc/prometheus-stack-kube-prom-prometheus 9090:9090 -n monitoring --address=0.0.0.0
```
### 🔹 Port forward Grafana service
```
kubectl port-forward svc/prometheus-stack-grafana 3000:80 -n monitoring --address=0.0.0.0
```
### 🔹 Retrieve Grafana admin password
```
kubectl get secret prometheus-stack-grafana -n monitoring -o jsonpath="{.data.admin-password}" | base64 --decode
```

## 📦 Kind (Kubernetes in Docker) Commands
### 🔹 Check Kind version
```
kind version
```
### 🔹 Create a Kind cluster
```
kind create cluster --name=prn-cluster --config=config.yml
```

## 📂 File and Directory Management Commands
### 🔹 Create a directory
```
mkdir kind-cluster
```
### 🔹 List files in the directory
```
ls
```
### 🔹 Change directory
```
cd kind-cluster/
```
### 🔹 Edit a file with Vim
```
vim config.yml
```

## 🔧 Helm Commands
### 🔹 Download Helm install script
```
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
```
### 🔹 Make Helm script executable
```
chmod 700 get_helm.sh
```
### 🔹 Run Helm installation script
```
./get_helm.sh
```
### 🔹 Check Helm version
```
helm version
```
### 🔹 Add Prometheus Helm repository
```
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
```
### 🔹 Update Helm repositories
```
helm repo update
```
### 🔹 Install Prometheus and Grafana stack using Helm
```
helm install prometheus-stack prometheus-community/kube-prometheus-stack --namespace monitoring --set prometheus.service.nodePort=30000 --set grafana.service.nodePort=31000 --set grafana.service.type=NodePort --set prometheus.service.type=NodePort
```

## 🛠️ Miscellaneous Commands
### 🔹 Clear terminal screen
```
clear
```
### 🔹 View command history
```
history
```

