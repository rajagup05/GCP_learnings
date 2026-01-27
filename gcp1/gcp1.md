# gcp1 : High Availability with MIGs and Load Balancing

## AIM
Learn how to deploy a production-ready, highly available web application in GCP using **Managed Instance Groups (MIGs)**, **HTTP(S) Load Balancer**, and **health checks**.

## things Covered

| **Managed Instance Group**     |
| **Instance Template**          |
| **HTTP(S) Load Balancer**      | 
| **Health Check**               | 
| **LB Backend Service**                 |

---

### step 1 : Create an Instance Template

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

### Step 2: Create a Managed Instance Group (MIG)

1. Go to **Compute Engine → Instance groups**
2. Click **Create instance group**
3. Set:
   - Name: `web-mig`
   - Location: **Multiple zones in `us-central1`**
   - Select zones: `us-central1-a`, `us-central1-b`, `us-central1-c`
   - Instance template: `web-template`
   - Autoscaling: Enable (optional)
   - Number of instances: 3 (1 per zone)
4. Click **Create**

---
> [!NOTE]
> Head to **Step 5** to start creating Load Balancers.

### Step 3: Allow HTTP Traffic via Firewall

1. Go to **VPC network → Firewall**
2. Click **Create firewall rule**
3. Set:
   - Name: `allow-http`
   - Direction: Ingress
   - Targets: Tags
   - Target tag: `http-server`
   - Source IP ranges: `0.0.0.0/0`
   - Protocols: Allow TCP port 80
4. Click **Create**

---

### Step 4: Create a Health Check

1. Go to **Network services → Health checks**
2. Click **Create a health check**
3. Set:
   - Name: `web-health-check`
   - Protocol: HTTP
   - Port: 80
4. Click **Create**

---

### Step 5: Create (Configure) a Classic Application Load Balancer 

1. Go to **Network services → Load balancing**
2. Click **Create load balancer → Start configuration**
3. Under **Type of load balancer** → select **Application Load Balancer (HTTP/HTTPS)**
4. Click **Next**
5. Under **Public facing or internal** → Select **Public facing (external)**
6. Click **Next**
7. Under **Global or single region deployment** → Select **Global workloads**
6. Click **Next**
7. Under **Load balancer generation** → Select **Classic Application Load Balancer**
6. Click **Configure**

>[!NOTE]
> continue with **step 6** to create LB
---
### Step 6: Create a Classic Application Load Balancer

1. Set:
   - Load Balancer Name: `web-lb`
   - Frontend configuration:
      - Protocol: HTTP
      - Port: 80
   - Backend configuration:
     - Create backend service 
     - Add the MIG (`web-mig`)
     - Attach the **health check** (`web-health-check`) => **refer to Step 4**
3. Click **Create**
---

Congrats!! 
Load Balancer is created successfully 🙂 


> Now, to see if `nginx` application is running, use `http://LB_IP_Address` to see which VM/server the request is going to whenever we hit/open the website. Here LB will send request to any one of the VM running in the backend (VMs created by MIG). It works from any device(mobile, etc).

> Alternatively, from any device/server/VM/instance we can access the output or verify if application is succesfully running by using command `curl http://LB_IP_Address`
