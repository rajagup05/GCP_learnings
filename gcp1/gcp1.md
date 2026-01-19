# 🚀 gcp1 : High Availability with MIGs and Load Balancing

## 🎯 AIM
Learn how to deploy a production-ready, highly available web application in GCP using **Managed Instance Groups (MIGs)**, **HTTP(S) Load Balancer**, and **health checks**.

## 📚 things Covered

| **Managed Instance Group**     |
| **Instance Template**          |
| **HTTP(S) Load Balancer**      | 
| **Health Check**               | 

---

### 🛠️ step 1 : Create an Instance Template

1. Go to **Compute Engine → Instance templates**
2. Click **Create instance template**
3. Set:
   - Name: `web-template`
   - Machine type: `e2-micro`
   - Boot disk: Debian or Ubuntu
4. Under **Advanced options → Automation → Startup script**:
   - Paste the contents of `startup.sh`
5. Add **network tag**: `http-server`
6. Click **Create**

> Use and save this script in `startup.sh` field

    #!/bin/bash
    apt update
    apt install -y nginx
    echo "Welcome to MIG Demo - $(hostname)" > /var/www/html/index.html
---

### step 2 : 
