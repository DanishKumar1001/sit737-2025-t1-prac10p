# 📦 Node.js App on GCP Kubernetes with Monitoring

This project demonstrates how to containerize a simple Express-based Node.js application, deploy it to a **Google Kubernetes Engine (GKE)** cluster, and set up **monitoring and logging** using Google Cloud Operations (formerly Stackdriver).

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/gcp-node-k8s-app.git
cd gcp-node-k8s-app

### 2. Install Dependencies

npm install

### 3. Docker Setup

Build and Push to Google Container Registry (GCR)

## 4. Authenticate with GCP

gcloud auth login
gcloud config set project YOUR_PROJECT_ID

## 5. Build and push Docker image

docker build -t gcr.io/YOUR_PROJECT_ID/node-app:latest .
docker push gcr.io/YOUR_PROJECT_ID/node-app:latest

### 6. Kubernetes Deployment (GKE)
Create GKE Cluster
gcloud container clusters create node-app-cluster --zone us-central1-a
gcloud container clusters get-credentials node-app-cluster --zone us-central1-a
Deploy to Cluster

kubectl apply -f k8s/deployment.yaml
kubectl apply -f k8s/service.yaml

### 7. Testing

## Get External IP

kubectl get svc node-app-service

Access the app via the external IP in your browser.

### 8. 📊 Monitoring and Logging

GKE automatically integrates with Google Cloud Monitoring and Logging.

##View Metrics

Go to Monitoring > Metrics Explorer in GCP.

Search for metrics like:

kubernetes.io/container/cpu/usage_time
kubernetes.io/container/memory/used_bytes

##View Logs

Go to Logging > Logs Explorer
Filter by resource type: Kubernetes Container

View logs for node-app

##Alerting (Optional)

Navigate to Monitoring > Alerting

Create policies based on:

High CPU or memory usage
App availability

### 9. ✅ Features
1. Serves static HTML files
2. Basic form submission (non-persistent)
3. Containerized with Docker
4. Deployed to GKE
5. Fully observable with GCP Monitoring/Logging

### Troubleshooting

CrashLoopBackOff Pods → Check port mismatch in app.js vs deployment.yaml
No external IP → Make sure service type is LoadBalancer and cluster is in a supported zone
No logs/metrics → Ensure Cloud Operations APIs are enabled in GCP

###References

Gooogle Cloud Platform (GCP) -https://cloud.google.com/kubernetes-engine/docs
Kubernetes - https://kubernetes.io/docs/
Node Package Manager (npm) - https://docs.npmjs.com/
Docker - https://docs.docker.com/
 