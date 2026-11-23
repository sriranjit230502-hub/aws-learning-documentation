# AWS Load Balancer Creation

## Target Group Creation

### Step 1
Create two EC2 instances with custom user data and launch instances.

<img width="1378" height="816" alt="LB-01A-user-data" src="https://github.com/user-attachments/assets/dc6f2493-e777-496d-b955-4c86e5e0d942" />


### Step 2
Two EC2 instances “2507-ec2-A01” & “2507-ec2-B02” were created with public subnets each in different Availability Zones.

<img width="1912" height="659" alt="LB-01B-ec2-creation" src="https://github.com/user-attachments/assets/efeb8aaf-69d7-4260-ab60-21206c72c856" />


### Step 3
Navigate to Target Groups through the left sidebar and click “Create Target Group”.

<img width="1916" height="660" alt="LB-02-targrp-create" src="https://github.com/user-attachments/assets/212faf34-2396-45e6-b474-bcae0363b4f6" />


### Step 4
Inside, select Instances as Target Type, name the Target Group `2507-targrp`, select protocol & port (HTTP - 80), IP type and choose the VPC created.

<img width="1674" height="846" alt="LB-03-tartype-inst IPv4 VPC" src="https://github.com/user-attachments/assets/cd39db97-2645-47eb-af9b-11e94a4270df" />


### Step 5
Choose protocol version as HTTP1 and leave the further settings to default, and click “Next”.

<img width="1635" height="859" alt="LB-04-click-next" src="https://github.com/user-attachments/assets/9e08b683-9e57-4363-b29d-7f0cc4b26db0" />


### Step 6
Select the instances to be registered in Target Group and click “Include on pending below”.

<img width="1918" height="487" alt="LB-05-sel-inst pendblw" src="https://github.com/user-attachments/assets/c37954be-22eb-4fc6-9f0a-e27c7de0c36e" />


### Step 7
Review and click “Next” for registering targets.

<img width="1673" height="317" alt="LB-06-targets-next" src="https://github.com/user-attachments/assets/26975e77-ef71-4528-9692-64153dd72f1d" />


### Step 8
Review and click “Create target group”.

<img width="1332" height="769" alt="LB-07-targrp-review created" src="https://github.com/user-attachments/assets/76afb5e5-2564-4ba1-84df-fac165ad3e30" />


### Step 9
Review the targets.

<img width="1279" height="626" alt="LB-09-register-targets" src="https://github.com/user-attachments/assets/c4ab839b-f357-4b81-8ebb-2f5b6e65ded0" />



### Step 10
Thus Target group created.

<img width="1912" height="840" alt="LB-10-2507-targrp-created" src="https://github.com/user-attachments/assets/81485583-43bc-49e8-a2c7-1d617b159dfe" />


---

## Load Balancer Creation

### Step 11
Now, navigate to Load Balancers in the sidebar. Click “Create Load Balancer”.

<img width="1920" height="1080" alt="LB-11-click-createLoadBalancer" src="https://github.com/user-attachments/assets/b8a3cf43-6720-4063-99dd-3459b1c2d629" />


### Step 12
Click “Create” in Load Balancer types Application Load Balancer.

<img width="1143" height="746" alt="LB-12-create-ALB" src="https://github.com/user-attachments/assets/191d4af5-7fa2-45e8-8191-4d12e2c0065f" />


### Step 13
* Name the load balancer `2507-lb`, select Internet-facing and IPv4 as addressing type in Basic Configuration.

  <img width="1635" height="564" alt="LB-13A-basic-config" src="https://github.com/user-attachments/assets/164d9314-009e-4b4b-ab42-c75df02afd52" />


* In Network Mapping, select the VPC, Availability Zones and Security Groups associated with the instances and leave IP pools unchecked.

  <img width="1248" height="714" alt="LB-13B-netwrk SG" src="https://github.com/user-attachments/assets/075c8eb1-b28b-41e6-97e3-141a21a69f1e" />


* In Listener and Routing, choose port & protocol, select “Forward to target groups”, and choose the target group created `2507-targrp`.

  <img width="1253" height="696" alt="LB-13C-listener routing" src="https://github.com/user-attachments/assets/b3c3129e-c709-4b61-929a-a7dac6933dfb" />


* Review and click “Create Load Balancer”.

  <img width="1724" height="855" alt="LB-13D-create-LB" src="https://github.com/user-attachments/assets/ca367fcf-f4ba-4d13-a627-522189afffe2" />


### Step 14
Load balancer is created. Copy the DNS name.

<img width="1296" height="685" alt="LB-14-success-ALB-created" src="https://github.com/user-attachments/assets/40b9da33-ec8a-4d74-8e2b-47594e80451f" />


### Step 15
Navigate to Target Groups, select the target group created `2507-targrp` and associate it with “existing Load Balancer”.

<img width="1920" height="1001" alt="LB-15-ALB-created" src="https://github.com/user-attachments/assets/ba093680-d442-4e8e-9d3d-9ce01d7669c9" />


### Step 16
Paste the DNS in the browser's search bar. The `.html` program given in user data along with server setup while launching EC2 instances, appears as a website to the DNS searched.

<img width="1026" height="1001" alt="LB-finally-connected" src="https://github.com/user-attachments/assets/77b69b26-34b4-4e5d-8e74-33e9ed9a3c9a" />
