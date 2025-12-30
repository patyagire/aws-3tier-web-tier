Awesome 👍
Below is a **full, detailed, production-ready README for the WEB TIER**, written in the **same level and style** as your App Tier README.
You can **copy–paste this directly** into your `aws-3tier-web-tier` repo `README.md`.

---

# 📘 **AWS 3-Tier Web Application – Web Tier (Frontend)**

## 📌 Overview

This repository contains the **Web Tier (Frontend layer)** of a **production-grade AWS 3-Tier Web Application**.

The Web Tier is responsible for:

* Serving the **frontend UI**
* Handling **client/browser requests**
* Acting as a **reverse proxy** to the App Tier
* Providing **secure and scalable access** to backend APIs

---

## 🧠 What is the Web Tier?

The **Web Tier** is the **entry point** of the application.
It receives traffic from users and forwards API requests to the **App Tier**, while serving static frontend assets.

### Responsibilities:

* Serve React build files
* Reverse proxy API requests
* Handle HTTP traffic (Port 80)
* Integrate with Load Balancer / Auto Scaling
* Isolate backend from public access

---

## 🏗 High-Level Architecture

```
+-------------+
|   User      |
|  Browser    |
+------+------+
       |
       v
+------+------+
|   Web Tier  |
|  Nginx     |
|  React UI  |
+------+------+
       |
       v
+------+------+
|   App Tier  |
| Node.js API|
+------+------+
       |
       v
+------+------+
| Database    |
| RDS MySQL   |
+-------------+
```

---

## 🧱 AWS Components Used

| Component                 | Purpose                    |
| ------------------------- | -------------------------- |
| EC2                       | Hosts Nginx + React        |
| Nginx                     | Web server & reverse proxy |
| Auto Scaling Group        | High availability          |
| Application Load Balancer | Traffic distribution       |
| Security Groups           | Network access control     |
| VPC                       | Network isolation          |
| Public Subnet             | Internet access            |
| IAM Role                  | Secure AWS access          |

---

## ⚙️ Technology Stack

### Frontend

* **React.js**
* **HTML / CSS / JavaScript**
* **Create-React-App**

### Web Server

* **Nginx**

---

## 📂 Project Structure

```
web-tier/
│
├── build/
│   └── Production-ready React build
│
├── public/
│   └── Static assets
│
├── src/
│   └── React source code
│
├── nginx.conf
│   └── Nginx reverse proxy config
│
├── package.json
│   └── Dependencies & scripts
│
├── package-lock.json
│
└── README.md
```

---

## 🚀 Application Flow

1️⃣ User opens the application URL
2️⃣ Request reaches **Web Tier (Nginx)**
3️⃣ Static files served from `/build`
4️⃣ API requests forwarded to **App Tier**
5️⃣ App Tier queries **Database Tier**
6️⃣ Response returned to user

---

## 🔄 Nginx Reverse Proxy Configuration

```nginx
server {
    listen 80;
    server_name _;

    root /home/ec2-user/web-tier/build;
    index index.html;

    location / {
        try_files $uri /index.html;
    }

    location /api/ {
        proxy_pass http://127.0.0.1:4000;
        proxy_http_version 1.1;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    }
}
```

📌 **Why Nginx?**

* Lightweight & fast
* Acts as reverse proxy
* Handles static content efficiently
* Improves security

---

## 📦 Build & Deployment Steps

### 1️⃣ Install Dependencies

```bash
npm install
```

### 2️⃣ Build React App

```bash
npm run build
```

### 3️⃣ Configure Nginx

```bash
sudo cp nginx.conf /etc/nginx/nginx.conf
sudo nginx -t
sudo systemctl restart nginx
```

---

## 🌐 Access Application

```
http://<EC2-PUBLIC-IP>
```

or via

```
http://<LOAD-BALANCER-DNS>
```

---

## 🔒 Security Best Practices

✔ Web Tier in **public subnet**
✔ Only HTTP/HTTPS exposed
✔ App Tier in **private subnet**
✔ No direct DB access
✔ Reverse proxy prevents backend exposure
✔ Security Groups restrict traffic

---

## 📈 Scalability & High Availability

* Web Tier supports **Auto Scaling**
* Stateless frontend
* Load Balancer distributes traffic
* Nginx handles concurrent connections efficiently

---

## 🛠 Troubleshooting

### ❌ Site Not Loading

* Check Nginx status

```bash
sudo systemctl status nginx
```

### ❌ 502 Bad Gateway

* App Tier not running
* Wrong proxy_pass IP/Port
* Security Group blocking traffic

### ❌ Nginx Not Listening

```bash
sudo ss -tulnp | grep nginx
```

---

## 📊 Logs & Monitoring

### Nginx Logs

```bash
/var/log/nginx/access.log
/var/log/nginx/error.log
```

### Health Check

```bash
curl http://localhost
```

---

## 🔁 CI/CD Friendly

This repo can be integrated with:

* GitHub Actions
* Jenkins
* AWS CodePipeline

Example flow:

```
Git Push → Build → Deploy → Restart Nginx
```

---

## 🔗 Related Repositories

* **App Tier:**
  [https://github.com/patyagire/aws-3tier-app-tier](https://github.com/patyagire/aws-3tier-app-tier)

---

## 👨‍💻 Author

**Prathmesh Gire**
Cloud | DevOps | AWS Engineer
GitHub: [https://github.com/patyagire](https://github.com/patyagire)

---

## ⭐ Support

If this project helped you:

* ⭐ Star the repo
* 🍴 Fork it
* 🧠 Use it in interviews

---

## 💼 Interview Value

This Web Tier demonstrates:

* Real-world Nginx reverse proxy
* AWS networking concepts
* Load balancing & scalability
* Secure frontend-backend separation

---

### 🚀 Want Next?

I can help you with:

* **Database Tier README**
* **Complete Architecture Diagram**
* **Terraform for all 3 tiers**
* **Interview Q&A from this project**
* **Production Hardening Checklist**

Just say the word 😎
