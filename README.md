# 🚀 Deploying Nginx on Minikube (Windows + Docker Driver)

This guide will help you run **Nginx** on Kubernetes using **Minikube** with Docker driver, and then open it in your browser.  
Follow these simple steps 👇

---

## 🛠 Requirements
Before starting, make sure you have:
- **Windows 10/11** with **PowerShell (Admin)** access
- **Docker Desktop** (installed & running)
- **Minikube** (installed)
- **kubectl** (installed)

---

## 📋 Step-by-Step Guide

### 1️⃣ Start Minikube
Open **PowerShell as Administrator** and run:
```powershell
minikube start --driver=docker

This starts a Minikube cluster using Docker.

2️⃣ Check Cluster Status

kubectl get nodes
kubectl get pods -A

kubectl get pods -A

✅ You should see:

    1 node with status Ready

    All system pods in Running state

3️⃣ Create an Nginx Deployment

kubectl create deployment nginx-deploy --image=nginx

This tells Kubernetes to run an Nginx server.

4️⃣ Expose Nginx to the Outside World
kubectl expose deployment nginx-deploy --type=NodePort --port=80


NodePort = allows browser access

80 = default HTTP port for Nginx

5️⃣ Check the Service Details
kubectl get svc


Example output:
nginx-deploy   NodePort   10.96.44.101   <none>   80:30394/TCP   10s

Here:

30394 is the NodePort (randomly assigned by Kubernetes)

6️⃣ Get Minikube IP
minikube ip


Example:
192.168.49.2

7️⃣ Open Nginx in Browser 🌐

Combine the Minikube IP + NodePort:
http://192.168.49.2:30394

If everything is correct, you’ll see the "Welcome to nginx!" page 🎉 

8️⃣ Shortcut Method (Optional)
minikube service nginx-deploy

This will:

Create a tunnel (keep PowerShell open)

Open Nginx directly in your browser

🗑 Clean Up (Optional)

When you’re done, remove everything:

kubectl delete service nginx-deploy
kubectl delete deployment nginx-deploy

💡 Tips

Always run commands in PowerShell (Admin) mode

If external images don’t pull, load them manually:

docker pull <image-name>
minikube image load <image-name>

✅ Done! You’ve successfully deployed Nginx on Kubernetes using Minikube with Docker driver on Windows 🚀


---
