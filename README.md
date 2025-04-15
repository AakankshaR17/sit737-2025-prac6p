# SIT737 – Practical 6.1P: Deploying a Node.js App to Kubernetes

## 👩‍💻 Author
**Aakanksha Rajput**  
**Student ID:** S224184261  
**Unit:** SIT737 Cloud Automation Technologies  

---

## 📦 Overview
This project demonstrates how to containerize a simple Node.js application, push the Docker image to Docker Hub, and deploy the application to a local Kubernetes cluster. The service is exposed using NodePort, and the app is accessed via a browser using `localhost:30080`.

---

## 🛠️ Tools Used
- [Node.js](https://nodejs.org/)
- [Docker](https://www.docker.com/)
- [Docker Hub](https://hub.docker.com/)
- [Kubernetes](https://kubernetes.io/) (via Docker Desktop)
- [kubectl](https://kubernetes.io/docs/reference/kubectl/)
- Visual Studio Code (VS Code)

---

## 🗂️ Project Structure
sit737-2025-prac6p/
├── app/
│   ├── index.js
│   ├── package.json
│   └── kubernetes/
│       ├── deployment.yaml
│       └── service.yaml
├── Dockerfile
├── README.md
---

## 🧑‍🍳 Application Code (index.js)
```javascript
const express = require('express');
const app = express();
const port = 3000;

app.get('/', (req, res) => {
  res.send('Hello from Kubernetes Cluster!');
});

app.listen(port, () => {
  console.log(`App listening on port ${port}`);
});

🐳 Docker Commands
# Build the image
docker build -t aakanksha17/k8s-node-app:latest .

# Push to Docker Hub
docker push aakanksha17/k8s-node-app:latest
🚀 Deploy Commands
# Apply Kubernetes configs
kubectl apply -f app/kubernetes/deployment.yaml
kubectl apply -f app/kubernetes/service.yaml

# Verify
kubectl get pods
kubectl get svc
