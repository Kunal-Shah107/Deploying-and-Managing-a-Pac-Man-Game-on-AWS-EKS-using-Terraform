# Deploying-and-Managing-a-Pac-Man-Game-on-AWS-EKS-using-Terraform
This repo is used for hands on lab for Deploying-and-Managing-a-Pac-Man-Game-on-AWS-EKS-using-Terraform.

STEP 1 :

Deploy the EKS Cluster with Terraform.
git clone Github Repo
Change into the eks directory: cd eks
ls now & we should see the eks-cluster.tf, main.tf, outputs.tf, terraform.tf, variables.tf, and vpc.tf configuration files.
Initialize the working directory: terraform init
Validate the configuration: terraform validate
Now apply the configuration and deploy the EKS cluster: terraform apply -auto-approve
Note: It can take between 15 and 20 minutes to deploy the eks cluster.
![ezgif-5-c8763281f6 (1)](https://github.com/bikrantsahoo/Deploy-webapp-with-techstack-terraform-aws--eks/assets/90495596/84e5ba03-0233-4783-b9f4-ab6c032ebabc)
