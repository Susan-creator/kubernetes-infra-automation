Kubernetes Setup with Terraform and Ansible

This project demonstrates how to set up a Kubernetes cluster on AWS using Terraform and Ansible. The cluster includes one master node and two worker nodes, with all configurations automated via infrastructure as code (IaC).

Project Structure
Terraform: Provisions the required AWS infrastructure (EC2 instances, security groups, etc.).
Ansible: Configures the EC2 instances, installs Kubernetes components, and sets up the cluster.
Kubernetes: Manages the orchestration of containerized applications.


File Structure
├── terraform/
│   ├── main.tf
│   ├── variables.tf
│   ├── outputs.tf
│   ├── provider.tf
├── ansible/
│   ├── inventory.ini
│   ├── site.yml
│   ├── roles/
│       ├── kubernetes/
│           ├── tasks/
│               ├── main.yml
│           ├── meta/
│               ├── main.yml
│           ├── defaults/
│               ├── main.yml
├── README.md


Requirements
Tools
Terraform (>= 1.3.0)
Ansible (>= 2.10)
AWS CLI
SSH key pair for EC2 access
Dependencies


Ensure the following Python packages are installed:

boto3
ansible (via pip)


Setup Instructions
1. Infrastructure Provisioning (Terraform)
Navigate to the terraform/ directory.


Initialize Terraform:
terraform init

Plan and review infrastructure changes:
terraform plan

Apply changes to provision AWS resources:
terraform apply

Note the output values for EC2 instance IPs.

2. Configuration and Kubernetes Setup (Ansible)
Navigate to the ansible/ directory.
Update the inventory.ini file with the IP addresses of the master and worker nodes.
Run the playbook:

ansible-playbook -i inventory.ini site.yml

Usage
Access the Kubernetes Cluster
SSH into the master node:
ssh -i <your-key.pem> ubuntu@<master-node-ip>

Verify cluster status:
kubectl get nodes

Cleanup
Terraform Resources
Destroy the infrastructure:

terraform destroy

Ansible Resources
Use a playbook to remove configurations or manually clean up resources:
ansible-playbook -i inventory.ini delete-resources.yml

Troubleshooting
Ensure your AWS credentials are correctly configured using the AWS CLI.
Verify that all required dependencies are installed.
Check EC2 instance logs for connectivity or configuration errors.


Contributions
Feel free to fork this repository and submit a pull request for any improvements or fixes.

