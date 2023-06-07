# Deploying-and-Managing-a-Pac-Man-Game-on-AWS-EKS-using-Terraform
This repo is used for hands on lab for Deploying-and-Managing-a-Pac-Man-Game-on-AWS-EKS-using-Terraform.

<img align="right" alt="Coding" width="400" src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSlNSb2n8EOjSuCpO3VtejG0RB3Ql8DI2glSR3EvEDmqw&usqp=CAU&ec=48600112">


STEP 1 :

1.Deploy the EKS Cluster with Terraform.

2.git clone Github Repo

3.Change into the eks directory: cd eks

4.ls now & we should see the eks-cluster.tf, main.tf, outputs.tf, terraform.tf, variables.tf, and vpc.tf configuration files.

5.Initialize the working directory: terraform init

6.Validate the configuration: terraform validate

7.Now apply the configuration and deploy the EKS cluster: terraform apply -auto-approve

Note: It can take between 15 and 20 minutes to deploy the eks cluster.
![ezgif-5-c8763281f6 (1)](https://github.com/bikrantsahoo/Deploy-webapp-with-techstack-terraform-aws--eks/assets/90495596/84e5ba03-0233-4783-b9f4-ab6c032ebabc)

![ezgif-5-0415763f68](https://github.com/bikrantsahoo/Deploy-webapp-with-techstack-terraform-aws--eks/assets/90495596/ea861a39-0a5a-40bd-ae60-93aebc00fdc9)

STEP 2 :

Once aws eks cluster is deployed, configure the Kubernetes CLI to use the cluster’s context.
aws eks --region $(terraform output -raw region) update-kubeconfig --name $(terraform output -raw cluster_name)
kubectl cluster-info (To confirm that the cluster is active)
We should see that the Kubernetes control plane and CoreDNS are running as expected.

![ezgif-5-a33a393b29](https://github.com/bikrantsahoo/Deploy-webapp-with-techstack-terraform-aws--eks/assets/90495596/16709c88-433d-4b6f-84d6-18d311b79d1e)


STEP 3 :

1. Complete the Terraform Configuration by change into main directory
2. cd ../pac-man/
3. Docker Image used for this lab is “docker.io/jessehoch/pacman-nodejs-app:latest”
4. terraform init
5. terraform validate
6. terraform apply -auto-approve

STEP 4 :

1. Once deployed, confirm that the web application resources were deployed in the pac-man namespace and are available.
2. kubectl -n pac-man get all
3. We should see that the mongo and pac-man pods, services, deployments, and replicas are all available and running as expected.
4. For the pac-man service, copy the DNS record provided in the EXTERNAL-IP column.
5. In a new browser tab or window, paste the external IP address and hit Enter.
6. When the Pac-Man web application launches.
7. Click to play as instructed, and play the game to confirm that it is working as expected.

![ezgif-5-36dfc56605](https://github.com/bikrantsahoo/Deploy-webapp-with-techstack-terraform-aws--eks/assets/90495596/4f1cc54a-cf60-4e65-be05-1816a85056e4)

![ezgif-5-f8ad4b3687-0000](https://github.com/bikrantsahoo/Deploy-webapp-with-techstack-terraform-aws--eks/assets/90495596/a9d3626d-fdd3-4564-911b-2f6dec3d5bd1)



STEP 5 :

1. Scale the AWS EKS Pac-Man Application.
2. Edit the MongoDB deployment configuration file:
3. vi modules/mongo/mongo-deployment.tf
4. For the replicas spec, update the replicas value to 2. save & exit.
5. Edit the Pac-Man deployment configuration file:
6. vi modules/pac-man/pac-man-deployment.tf
7. For the replicas spec, update the replicas value to 3. save & exit.
8. Apply the updates to the configuration : terraform apply
9. When prompted, enter yes to confirm.
10. Confirm that the resources were updated: kubectl -n pac-man get all
11. We should see that the mongo and pac-man pods, deployments, and replicas have all been scaled up to 2 and 3, respectively.
12. In the browser, refresh the Pac-Man web application and confirm that it is still working as expected.

STEP 6 :

1. Edit the MongoDB and Pac-Man deployment configuration files again, this time changing the replicas back to 1.
2. Apply the updates to the configuration : terraform apply
3. Confirm that the resources were updated: kubectl -n pac-man get all
4. We should see that the mongo and pac-man pods, deployments, and replicas have all been scaled back down to 1 each.
5. In the browser, refresh the Pac-Man web application and confirm that it is still working as expected.


STEP 7 :

destory all the above proofs by terraform destroy.

Congrtulation for completing the prject involving aws eks/terraform and deploying this game pacman


