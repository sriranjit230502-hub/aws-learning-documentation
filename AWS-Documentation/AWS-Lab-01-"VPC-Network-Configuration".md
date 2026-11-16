# AWS Lab 01 — VPC Network Configuration (End to End)

**Step 1**

Create VPC tsk-140726 manually with IPv4 CIDR range 32.0.0.0\16.

<img width="1920" height="1001" alt="001-tsk-140726-vpc-created" src="https://github.com/user-attachments/assets/eb7e086d-1df1-4e70-b183-d5c3f7c00c5f" />




**Step 2**

Create four Subnets - two public subnets tsk-public-subnet-001 & tsk-public-subnet-002 and two private subnets tsk-private-subnet-001 & tsk-private-subnet-002 , with IPv4 CIDR ranges 32.0.1.0/24 , 32.0.3.0/24 for public subnets and 32.0.2.0/24 , 32.0.4.0/24 for private subnets respectively for the VPC created.

<img width="1920" height="1001" alt="002-tsk-140726-subnets-pub priv-created" src="https://github.com/user-attachments/assets/1caf7ece-388f-494e-917b-8c927e410a0b" />



**Step 3**

Create Route Tables tsk-public-rt & tsk-private-rt each for public private subnets respectively for the VPC created.


<img width="1920" height="1001" alt="005-tsk-160726-rt-pub priv-created" src="https://github.com/user-attachments/assets/850a5987-3221-48d8-ae02-0c6ee3e2f79e" />






**Step 4**

Create Internet gateway tsk-int-gtw-public for the VPC created.


<img width="1920" height="1001" alt="003-tsk-160726-intgw-created" src="https://github.com/user-attachments/assets/be3d4179-5146-4e59-b761-d0a0e1a3be77" />





**Step 5**

Attach the internet gateway to the VPC created. 


<img width="1920" height="1001" alt="004-tsk-160726-igw-attached-to-vpc" src="https://github.com/user-attachments/assets/ff635007-f8d5-4749-857b-3ddb5c5b1d34" />

<img width="1920" height="1001" alt="006-tsk-160726-pub-rt-igw-connect" src="https://github.com/user-attachments/assets/481ceaa7-9ad9-40e3-bd73-795962359785" />
<img width="1920" height="1001" alt="006-tsk-160726-pub-rt-igw-connect" src="https://github.com/user-attachments/assets/7b53c2f6-bd79-48ff-aaa7-f97240837125" />
















**Step 6**

Connect the public route table tsk-public-rt to the internet gateway tsk-int-gtw-public for the VPC created and Do NOT Connect private route table to the internet gatway.



<img width="1920" height="1001" alt="006-tsk-160726-pub-rt-igw-connect" src="https://github.com/user-attachments/assets/cb533e5a-6214-4159-a3d7-2306e9baeb9b" />


<img width="1920" height="1001" alt="008-tsk-160726-priv-rt-NO-IGW" src="https://github.com/user-attachments/assets/66d9b7e9-958d-4bef-b7c7-b0b90f1dc74f" />










**Step 7**

Associate public subnets tsk-public-subnet-001 & tsk-public-subnet-002 with the public route table tsk-public-rt. 

And associate private subnets tsk-private-subnet-001 & tsk-private-subnet-002 with the private route table tsk-private-rt.










**Step 8**

VPC tsk-140726 manually created with public and private subnets tsk-public-subnet-001 & tsk-public-subnet-002 and tsk-private-subnet-001 & tsk-private-subnet-002 attached  the route tables tsk-public-rt & tsk-private-rt and connect public route table tsk-public-rt with internet gateway tsk-int-gtw-public.




### AWS VPC endpoint creation for the VPC “tsk-140726”

**Step 9**

Navigate into the “create endpoint” window, name the endpoint tsk-endpt-160726 and click AWS services in Type. Leave the service region unticked.

 


**Step 10**

Search S3 in the search bar under services. Choose com.amazonaws.ap-south-2.s3 from search results. Then select gateway type .











**Step 11**

Select the VPC created tsk-160726 in the search bar under the “Networking settings” .





**Step 12**

Click the checkbox of private route table tsk-private-rt in “Route tables” section.





**Step 13**

Then click “create endpoint”. Thus  VPC Endpoint tsk-endpt-160726 is created.


