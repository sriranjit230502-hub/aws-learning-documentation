# AWS 2-tier architecture

### Step 1

Create a bucket, upload the html file, enable Static Webhosting and make it publicly readable. Create a cloudfront distribution for the S3 bucket created and verify its connection. Create a SNS subscription with existing topic to the mail id as protocol.

- Open **Amazon S3 → General purpose buckets** and click **Create bucket**.
<img width="1109" height="1001" alt="A-S3-01" src="https://github.com/user-attachments/assets/dd1da4de-bf67-480b-87b0-14eae77ef615" />

- Open the created bucket and click **Upload**.
  - Select the HTML file and upload it.
 <img width="1109" height="1001" alt="A-S3-05" src="https://github.com/user-attachments/assets/d5d17e33-46e9-4928-be6e-7afb1ef5aaf1" />

- Navigate to the bucket's **Properties** tab and open **Static website hosting → Edit**.
  - Enable Static website hosting.
  - Select **Host a static website**.
  - Enter the index document.
  - Save the changes.
<img width="961" height="690" alt="A-S3-07" src="https://github.com/user-attachments/assets/46b58a10-c5e8-4f4e-8f87-f80aa52d47bb" />

- Open the uploaded HTML file and navigate to the **Permissions** tab.
  - Under **Access control list (ACL)**, grant **Everyone (public access)** Read permission.
<img width="1096" height="458" alt="A-S3-08" src="https://github.com/user-attachments/assets/3ff07d10-a77d-4cf8-ba66-bee3f6cd501e" />

- Open **Amazon CloudFront → Distributions** and click **Create distribution**.
  - Create a distribution for the S3 static website.
 <img width="1109" height="1001" alt="A-CF-01-" src="https://github.com/user-attachments/assets/94d057a7-7ef9-4f3c-8cd3-0f775cf74b6b" />

- Verify that the CloudFront distribution is created.
  - Copy the CloudFront DNS name and open it in a browser.
  - Verify the website connection.
 <img width="1082" height="579" alt="A-CF-06" src="https://github.com/user-attachments/assets/fffdd297-b42d-4e75-9002-a0db51461448" />

 <img width="1109" height="1001" alt="A-CF-07" src="https://github.com/user-attachments/assets/50befb1c-f499-4eaf-a44b-d1ca0b8fc812" />


- Open **Amazon SNS → Subscriptions**.
  - Create a subscription using the existing SNS topic.
  - Select **Email** as the protocol and provide the email ID as the endpoint.
  - Verify the subscription status.
<img width="1068" height="481" alt="B-SNS-03" src="https://github.com/user-attachments/assets/d1783fa8-b549-47fd-a2f5-325766bf19ac" />

<img width="1077" height="197" alt="B-SNS-05" src="https://github.com/user-attachments/assets/2442d853-7dad-41dc-86bb-7562c14387dd" />



### Step 2

Create a VPC, two public & private subnets, public & private route tables, internet gateway for public subnets and NAT gateway for private subnets. Attach VPC to the gateway, edit subnet associations in respective route tables and attach NAT gateway to private route table, and attach Internet gateway to public route tables. Now create two security groups - one for Application load balancer and one for Auto Scaling group. In Security group swh-alb-sg, add HTTP as inbound rule, and in swh-ec2-sg, add HTTP, NFS, SSH as inbound rules.

- Open **Amazon VPC → Your VPCs** and create a VPC.
<img width="1076" height="234" alt="D-VPC-01" src="https://github.com/user-attachments/assets/6278e81d-7d01-4feb-94d1-ff976c0cb7bf" />

- Create two public and two private subnets in the VPC.
<img width="1077" height="288" alt="D-VPC-02" src="https://github.com/user-attachments/assets/a48b8d2a-4c20-4ae9-a7d6-9213c5df2de3" />

- Create public and private route tables.
<img width="1074" height="204" alt="D-VPC-03" src="https://github.com/user-attachments/assets/7a2342e4-95a5-4d30-a394-d53ae8ad0149" />

- Create an Internet Gateway and attach it to the VPC.
<img width="1070" height="223" alt="D-VPC-04" src="https://github.com/user-attachments/assets/108933c8-aacc-4429-93b5-9113880f3a9c" />

- Create a NAT Gateway.
  - Select the VPC created.
  - Select **Public** as the connectivity type.
  - Select the Elastic IP allocation option.
<img width="1067" height="759" alt="D-VPC-05" src="https://github.com/user-attachments/assets/48c14ebc-ea7b-46ef-ae9d-3f8ff09a5fa5" />

- Verify that the NAT Gateway is created.
<img width="1074" height="334" alt="D-VPC-06" src="https://github.com/user-attachments/assets/d16463d4-d85f-461c-bfcb-a52dfb1800a9" />

- Create a VPC endpoint.
  - Verify that the endpoint is available.
<img width="1069" height="646" alt="D-VPC-07" src="https://github.com/user-attachments/assets/e28fe665-03ef-42d3-a6ac-8bf4c9d3ac78" />

- Edit the subnet associations in the respective route tables.
  - Attach the NAT Gateway to the private route table.
  - Attach the Internet Gateway to the public route table.

- Create the security group `swh-alb-sg`.
  - Add HTTP as the inbound rule.
<img width="1080" height="992" alt="E-SG-01" src="https://github.com/user-attachments/assets/a82035a3-8a54-40c8-9ab0-8df49bda12d1" />

- Create the security group `swh-ec2-sg`.
  - Add HTTP, NFS and SSH as inbound rules.
<img width="1080" height="992" alt="E-SG-02" src="https://github.com/user-attachments/assets/1c5d6976-f107-4fdd-b226-c279991707d5" />

- Verify that both security groups have been created.
<img width="1072" height="431" alt="E-SG-03" src="https://github.com/user-attachments/assets/2e5ec15e-d439-4b13-87b1-cea63d707bbd" />

### Step 3

Create Target group with Port 80, protocol HTTP, target type as INSTANCE, and Application Load Balancer with internet-facing - select availability zones, IP address type, VPC created. Attach the load balancer to target group created.

Create an IAM role ec3-s3-role, with S3FullAccess as IAM policy to EC2 service. Create an EFS file system.

- Open **EC2 → Target groups** and create a target group.
  - Port: **80**
  - Protocol: **HTTP**
  - Target type: **Instances**
<img width="1074" height="207" alt="F-targrp-01" src="https://github.com/user-attachments/assets/0fa3c403-0095-4643-8e46-31fc988070d6" />

- Navigate to **EC2 → Load balancers** and create an Application Load Balancer.
  - Scheme: **Internet-facing**
  - Select the IP address type.
  - Select the VPC created.
  - Select the required Availability Zones and public subnets.
  - Attach the target group created.
<img width="1076" height="211" alt="F-ALB-02" src="https://github.com/user-attachments/assets/42ade689-9f7e-4b46-83c0-3476c3fa5838" />

- Open **IAM → Roles** and create the IAM role `ec3-s3-role`.
  - Select **EC2** as the trusted entity/service.
  - Attach the **AmazonS3FullAccess** policy.
<img width="1080" height="992" alt="G-IAM-role-01" src="https://github.com/user-attachments/assets/fc8e011e-f070-4bfa-93d1-73480ccd9a20" />

- Open **Amazon EFS → File systems** and create an EFS file system.
  - Verify that the file system is available.
<img width="1062" height="279" alt="G-EFS-01" src="https://github.com/user-attachments/assets/82e5c140-2181-4a89-af38-a7c354eb0041" />

### Step 4

Create Launch Template with OS, instance type, keypair, security group chose, under Advanced settings select the IAM role created as IAM instance profile, then add then add the user data. Launch the template.

- Open **EC2 → Launch Templates** and click **Create launch template**.
  - Enter the launch template name and description.
  - Select the operating system / AMI.
<img width="1073" height="808" alt="H-launchTemp-01" src="https://github.com/user-attachments/assets/425add09-0ae4-43d8-a2ee-97412542f519" />

- Under **Instance type**, select the required instance type.
- Under **Key pair (login)**, select the key pair.
- Under **Network settings**, select the security group `swh-ec2-sg`.
<img width="1063" height="798" alt="H-launchTemp-02" src="https://github.com/user-attachments/assets/689a15cb-7665-4ece-abbf-bb847ca2f30d" />

- Under **Advanced details**:
  - Select the IAM role created as the IAM instance profile.
<img width="1070" height="317" alt="H-launchTemp-03" src="https://github.com/user-attachments/assets/72627231-e7c4-4275-8e55-e468157099fc" />

- Under **User data**, add the following script.

```bash
#!/bin/bash

# Update packages
apt-get update -y

# Install Nginx
apt-get install -y nginx nfs-common awscli

# Enable and start Nginx
systemctl enable nginx
systemctl start nginx

# Create EFS mount directory
mkdir -p /mnt/efs

# Mount EFS
mount -t nfs4 -o nfsvers=4.1 <efs dns name>:/ /mnt/efs

# Make EFS mount persistent
echo "<efs dns name>:/ /mnt/efs nfs4 defaults,_netdev 0 0" >> /etc/fstab

# Remove default Nginx page
rm -f /var/www/html/index.nginx-debian.html

# Copy website from S3 to Nginx web root
aws s3 sync s3://s3-swh-cloudfront-051542582635-ap-south-2-an/ /var/www/html/

# Set ownership
chown -R www-data:www-data /var/www/html

# Restart Nginx
systemctl restart nginx
```

- Click **Create launch template**.
  - Verify that the launch template has been created.
<img width="1069" height="780" alt="H-launchTemp-04" src="https://github.com/user-attachments/assets/d0c29265-78e5-4678-99c0-d12e0a2affbf" />

<img width="1075" height="342" alt="H-launchTemp-05" src="https://github.com/user-attachments/assets/54ea2048-7338-4ab4-9437-db2b58556d9c" />


### Step 5

Create the Auto scaling group, with the launch template created, select private subnets. Instances start to create automatedly from ASG created. Verify the ALB connection by pasting its dns in a browser, and see the website as result.

- Open **EC2 → Auto Scaling Groups** and click **Create Auto Scaling group**.
  - Select the launch template created.

- Under **Choose instance launch options**:
  - Select the VPC created.
  - Select the two private subnets.
<img width="1073" height="724" alt="H-ASG-01" src="https://github.com/user-attachments/assets/8fac3be6-ecc9-4976-9710-2bbd2d86748b" />

- Under **Integrate with other services**:
  - Attach the Application Load Balancer created.
  - Select the target group created.
  - Configure health checks.
<img width="1068" height="501" alt="H-ASG-02" src="https://github.com/user-attachments/assets/1e68b6fe-8cb7-4e31-9274-cee803412a08" />

- Under **Configure group size and scaling policies**:
  - Configure the desired, minimum and maximum capacity.
  - Configure the target tracking scaling policy.
<img width="1067" height="649" alt="H-ASG-03" src="https://github.com/user-attachments/assets/d4e59208-8e2c-40ef-a9fa-e2972da610bb" />

- Under **Add notifications**:
  - Select the existing SNS topic.
  - Configure the required event types.
<img width="832" height="391" alt="H-ASG-04" src="https://github.com/user-attachments/assets/cd9463fd-6033-4f34-bb7a-86c1a0f1dbc8" />

- Review the Auto Scaling group configuration and click **Create Auto Scaling group**.
  - Verify that the EC2 instances are launched.
<img width="1073" height="724" alt="H-ASG-01" src="https://github.com/user-attachments/assets/8f94951a-4267-47ec-a0aa-c39f210c0af9" />

<img width="1074" height="259" alt="I-ASG-EC2-01" src="https://github.com/user-attachments/assets/166acad6-398f-4db7-a0d4-767b942684f8" />

- Open the Application Load Balancer and copy its DNS name.
  - Paste the DNS name into a web browser.
  - Verify that the website loads successfully.
<img width="1092" height="323" alt="J-ALB-web-01" src="https://github.com/user-attachments/assets/8e962efb-4a72-4881-940a-10126346ce77" />

<img width="1096" height="998" alt="J-ALB-web-02" src="https://github.com/user-attachments/assets/14a90b40-867b-41e4-b699-af9c253762c5" />


### Step 6

Create Cloudwatch Alarms for the Auto scaling group metrics and create a dashboard.

- Open **CloudWatch → Alarms** and create alarms for the Auto Scaling group metrics.
  - Verify that the alarms are created.
<img width="1090" height="410" alt="K-Cwatch-alarm-01" src="https://github.com/user-attachments/assets/3bca4968-b886-4695-a772-9ff0badf5a9f" />

- Navigate to **CloudWatch → Dashboards**.
  - Create a dashboard for the Auto Scaling group metrics.
  - Verify that the dashboard is created.
<img width="1073" height="390" alt="K-Cwatch-dashb-01" src="https://github.com/user-attachments/assets/19f1ebed-d771-439e-b20e-1c10656d8135" />
