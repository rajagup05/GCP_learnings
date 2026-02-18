## Private App on Custom VPC + Regional External HTTP(S) Load Balancer 

## Step 1 — Create the VPC and subnets (Console)

1. In the console, go to: VPC network → VPC networks → Create VPC network

- Name: prod-vpc
- Subnet creation mode: Custom
- Add subnets (same Region you chose):
  - Name: subnet-public, IP range: 10.10.10.0/24
  - Name: subnet-app, IP range: 10.10.20.0/24
- Click Create.
