# Web Tier


# AWS 3-Tier Web Application – Web Tier

This repository contains the **Web Tier (Frontend)** of an **AWS 3-Tier Architecture** project.  
The frontend is built using **React** and served via **Nginx**, acting as a reverse proxy to the **Application Tier**.

---

## 🏗️ Architecture Overview

The application follows a classic **3-Tier Architecture**:

1. **Web Tier**
   - React frontend
   - Nginx web server
   - Handles client requests

2. **Application Tier**
   - Node.js backend (API)
   - Runs on EC2 with PM2
   - Communicates with Database Tier

3. **Database Tier**
   - Amazon RDS (MySQL)
   - Private subnet
   - Accessible only from App Tier

