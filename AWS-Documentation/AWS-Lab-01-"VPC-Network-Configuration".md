# AWS Lab 01 — VPC Network Configuration (End to End)

**Step 1**

Create VPC tsk-140726 manually with IPv4 CIDR range 32.0.0.0\16.




**Step 2**

Create four Subnets - two public subnets tsk-public-subnet-001 & tsk-public-subnet-002 and two private subnets tsk-private-subnet-001 & tsk-private-subnet-002 , with IPv4 CIDR ranges 32.0.1.0/24 , 32.0.3.0/24 for public subnets and 32.0.2.0/24 , 32.0.4.0/24 for private subnets respectively for the VPC created.



**Step 3**

Create Route Tables tsk-public-rt & tsk-private-rt each for public private subnets respectively for the VPC created.



**Step 4**

Create Internet gateway tsk-int-gtw-public for the VPC created.







**Step 5**

Attach the internet gateway to the VPC created. 

















**Step 6**

Connect the public route table tsk-public-rt to the internet gateway tsk-int-gtw-public for the VPC created and Do NOT Connect private route table to the internet gatway.









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


