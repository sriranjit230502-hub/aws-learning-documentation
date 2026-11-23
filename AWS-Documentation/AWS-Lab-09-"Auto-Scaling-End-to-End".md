# AWS Auto Scaling End-to-End

## EC2 Instance Creation

### Step 1
Create two EC2 instances (`2807-ec2-A01` & `2807-ec2-B02`) with public subnets in distinct Availability Zones (`ap-south-2a` & `ap-south-2b`) respectively.

<img width="1109" height="1001" alt="01-ec2-A01,B02-created" src="https://github.com/user-attachments/assets/865a9f0f-4c7b-4cb5-bdfd-fbc84b3ee93e" />


### Step 2
Create the Target Group `2807-tar-grp`.

<img width="1109" height="1001" alt="02-2807-tar-grp-created" src="https://github.com/user-attachments/assets/c7f4b631-5795-47bd-9d99-9fc6139de8c3" />


### Step 3
Create the Application Load Balancer (`2807-lb`) and associate it with the existing Target Group (`2807-tar-grp`).

<img width="1109" height="1001" alt="03-2807-lb-created associated-targrp" src="https://github.com/user-attachments/assets/e4ef0020-c4ff-4074-9117-f5ffe9694c05" />


### Step 4
Navigate to Launch Template through the sidebar and click “Create Launch Template”.

<img width="1109" height="1001" alt="01-2807-create-launch-template-01" src="https://github.com/user-attachments/assets/fcfd0424-2651-4929-aa4f-31d7d46d53fc" />


### Step 5
Name the Launch Template, select the OS image, instance type, key pair, security group and EBS volume (don't select the VPC subnet & Availability Zones) and launch the template. Just like an EC2 instance is created.

<img width="1109" height="1001" alt="02-2807-launch-temp-OS" src="https://github.com/user-attachments/assets/3710c49f-d9ae-41e3-9b1a-2a2b5330f35b" />

<img width="1109" height="1001" alt="03-2807-launch-temp-instType-kpr-vpc-az-sg" src="https://github.com/user-attachments/assets/7319adee-b34d-4f97-a4d5-8e578d56f88d" />

<img width="717" height="409" alt="04-2807-launch-template-ebs-tags" src="https://github.com/user-attachments/assets/c3f1a4fa-20a9-4a03-9057-d804a677c6a6" />

<img width="1109" height="1001" alt="05-2807-launch-template-userdata-launch" src="https://github.com/user-attachments/assets/54e8dbf7-0b84-429b-a02e-8ea086839eba" />

<img width="1109" height="1001" alt="06-2807-launch-template-created" src="https://github.com/user-attachments/assets/00bcfad8-8026-4f6e-a818-e496696b4423" />



---

## Auto Scaling Group Creation

### Step 6
After launching the template, navigate to Auto Scaling Groups and click “Create Auto Scaling Group”.

<img width="1380" height="1001" alt="01-create-ASG" src="https://github.com/user-attachments/assets/d1947434-12b8-45d2-a79b-6215d55f8b2a" />


### Step 7
Name it `2807-asg` and select the Launch Template created, and click “Next”.

<img width="1380" height="1001" alt="02-2087-asg select-2807-LT" src="https://github.com/user-attachments/assets/ea01d207-9dab-44ef-86fe-3e5e722f5214" />


### Step 8
Choose the VPC created and the public subnets (AZs), Balanced Best Effort as “Availability Zones distribution”. Click “Next”.

<img width="1380" height="1001" alt="03-2087-asg-network-vpc,az" src="https://github.com/user-attachments/assets/cc7c6119-40ab-4992-924c-e39dc1906fc0" />


### Step 9
Select “Attach to an existing load balancer”, inside it select “Choose from Application or Network Load Balancer target groups" and choose the Target Group `2807-tar-grp` in the Load Balancing section. Choose “No VPC Lattice service”.

<img width="1380" height="1001" alt="04A-LoadBalancing,VPClattices" src="https://github.com/user-attachments/assets/630591d2-4b53-453e-a26e-e5b6525bc3d8" />


### Step 10
Under ARC, select "Enable Zonal shift” & “Skip zonal shift validation”, then “Replace Unhealthy” as Health check behavior. Then, again select options for health checks in ELB & Amazon EBS checkboxes. Click “Next”.

<img width="1380" height="1001" alt="04B-ARC,HealthCheck" src="https://github.com/user-attachments/assets/f6bf4d11-018d-4399-8b18-47727d901128" />


### Step 11
Choose desired (2), min (2) and max (4) server capacity for Auto Scaling, select “No Scaling policy” over “Target tracking policy“, and “No policy” for Instance maintenance. Select “Enable instance scale-in protection”, and “None (default)” in Auto Scaling group protection, then click “Next”.

<img width="1380" height="1001" alt="05A-size,scaling" src="https://github.com/user-attachments/assets/43059a78-0a4b-41ef-8d5e-8fc7692e5691" />

<img width="1380" height="1001" alt="05B-scalingPolicies,settings" src="https://github.com/user-attachments/assets/b1293c72-a418-47cf-93f8-cfdac99de96e" />


### Step 12
Click “Next”, again “Next”, then review and click “Create Auto Scaling Group”.

<img width="1074" height="198" alt="06-2087asg-click-next" src="https://github.com/user-attachments/assets/f8c26f72-767c-477d-b55b-a1824b5fd813" />

<img width="1076" height="267" alt="07-2087-asg-next-again" src="https://github.com/user-attachments/assets/909343e4-9fe3-4fba-994a-67ba54046981" />

<img width="1380" height="1001" alt="08-2087-asg-review create" src="https://github.com/user-attachments/assets/911d652a-1fb9-4667-aafb-f1ce7f76b982" />


### Step 13
Thus the Auto Scaling Group `2807-asg` was created successfully. Also, two instances corresponding to the chosen minimum and desired capacity have been successfully launched and are in running state.

<img width="1380" height="1001" alt="09-2087-asg-autoscaling-created" src="https://github.com/user-attachments/assets/d9b36f79-4359-461a-a957-f59622914df9" />

<img width="1380" height="1001" alt="10-2087-asg-desiredec2-run" src="https://github.com/user-attachments/assets/a00084d5-8dfc-424f-91d6-8333e904c511" />

