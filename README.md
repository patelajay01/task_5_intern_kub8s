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
// all screenshorts<img width="1905" height="1020" alt="Screenshot 2025-08-13 091114" src="https://github.com/user-attachments/assets/a3aa9313-26e3-49a8-bd47-43cb3fbd81dc" />

<img width="726" height="300" alt="Screenshot 2025-08-13 135537" src="https://github.com/user-attachments/assets/e55322f7-597d-4b1b-ac23-e9d90f6be312" />
<img width="1090" height="331" alt="Screenshot 2025-08-13 135627" src="https://github.com/user-attachments/assets/6bf9b6d4-c285-4da4-8f42-1160610d4f9b" />
<img width="914" height="430" alt="Screenshot 2025-08-13 135706" src="https://github.com/user-attachments/assets/09308e12-234f-49f1-890c-c20b4fed4e40" />
<img width="883" height="346" alt="Screenshot 2025-08-13 135802" src="https://github.com/user-attachments/assets/43f6a11e-9910-4e6a-b2f2-5df214225d99" />
