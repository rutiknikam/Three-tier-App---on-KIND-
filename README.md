# Three-tier-App---on-KIND-

📌 Commands Guide
🐳 Docker Commands
🔹 Check running containers
Use the following command to see all running containers:

docker ps
🔹 Check Docker version
To verify your Docker version:

docker --version
☸️ Kubernetes (kubectl) Commands
🔹 Check Kubernetes version
To check the version of Kubernetes:

kubectl version
🔹 Get cluster information
To view the cluster information in use:

kubectl cluster-info --context kind-prn-cluster
🔹 Get nodes in the cluster
To get the list of nodes in the Kubernetes cluster:

kubectl get nodes
🔹 Get available namespaces
To list the available namespaces in the cluster:

kubectl get namespace
🔹 Create a new namespace
To create a new namespace called monitoring:

kubectl create namespace monitoring
🔹 Get pods in monitoring namespace
To list all the pods in the monitoring namespace:

kubectl get pods -n monitoring
🔹 Get services in monitoring namespace
To check the services in the monitoring namespace:

kubectl get svc -n monitoring
🔹 Port forward Prometheus service
To forward the Prometheus service port:

kubectl port-forward svc/prometheus-stack-kube-prom-prometheus 9090:9090 -n monitoring --address=0.0.0.0
🔹 Port forward Grafana service
To forward the Grafana service port:

kubectl port-forward svc/prometheus-stack-grafana 3000:80 -n monitoring --address=0.0.0.0
🔹 Retrieve Grafana admin password
To get the admin password for Grafana:

kubectl get secret prometheus-stack-grafana -n monitoring -o jsonpath="{.data.admin-password}" | base64 --decode
📦 Kind (Kubernetes in Docker) Commands
🔹 Check Kind version
To check the version of Kind:

kind version
🔹 Create a Kind cluster
To create a new Kind cluster:

kind create cluster --name=prn-cluster --config=config.yml
📂 File and Directory Management Commands
🔹 Create a directory
To create a new directory:

mkdir kind-cluster
🔹 List files in the directory
To list the files in a directory:

ls
🔹 Change directory
To move into a specific directory:

cd kind-cluster/
🔹 Edit a file with Vim
To edit a file using Vim:

vim config.yml
🔧 Helm Commands
🔹 Download Helm install script
To download the Helm installation script:

curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
🔹 Make Helm script executable
To make the script executable:

chmod 700 get_helm.sh
🔹 Run Helm installation script
To run the Helm installation script:

./get_helm.sh
🔹 Check Helm version
To check the Helm version:

helm version
🔹 Add Prometheus Helm repository
To add the Prometheus Helm repository:

helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
🔹 Update Helm repositories
To update the Helm repositories:

helm repo update
🔹 Install Prometheus and Grafana stack using Helm
To install the Prometheus and Grafana stack:

helm install prometheus-stack prometheus-community/kube-prometheus-stack --namespace monitoring --set prometheus.service.nodePort=30000 --set grafana.service.nodePort=31000 --set grafana.service.type=NodePort --set prometheus.service.type=NodePort
🛠️ Miscellaneous Commands
🔹 Clear terminal screen
To clear the terminal screen:

clear
🔹 View command history
To view your command history:

history
