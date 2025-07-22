Secure Web App with Public Proxy + Private Backend on AWS using Terraform
📖 Project Description
This project provisions a secure web application infrastructure on AWS using Terraform. It separates the public-facing proxy from the private backend using multiple subnets, NAT, and load balancers.

📦 Infrastructure Components
VPC with the following:
2 Public Subnets:
Contain EC2 instances acting as Nginx Reverse Proxies.
2 Private Subnets:
Contain EC2 instances running the Web Application Backend (e.g., Flask/Node.js).
NAT Gateway for private subnet internet access.
2 Load Balancers:
Public ALB → routes incoming traffic to Nginx proxy.
Internal ALB → proxies route traffic to backend servers.

🛠️ Technical Notes
Do not use the default workspace. Create a new workspace called dev.
Use custom Terraform modules to implement the architecture.
Each module should include:
main.tf, variables.tf, outputs.tf
Use remote state if possible (e.g., S3 + DynamoDB).
The local public IP should be placed in a file called alb-ip.txt in CIDR format:
Use private key to copy the backend files from your local machine to the backend EC2 instance.
Use data source to get the latest AMI ID for EC2 instances.

🚀 Project Delivery Method
Provide a documented walkthrough with:
Screenshots showing Terraform in action
Terraform directory structure
Confirmation that:
Requests go to the public proxy (Nginx)
Proxy securely forwards traffic to the backend in private subnets
