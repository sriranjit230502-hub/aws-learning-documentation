# AWS 2-tier architecture

### Step 1

Create a bucket, upload the html file, enable Static Webhosting and make it publicly readable. Create a cloudfront distribution for the S3 bucket created and verify its connection. Create a SNS subscription with existing topic to the mail id as protocol.

- Open **Amazon S3 → General purpose buckets** and click **Create bucket**.
  - Screenshot: Page 1

- Open the created bucket and click **Upload**.
  - Select the HTML file and upload it.
  - Screenshot: Page 2

- Navigate to the bucket's **Properties** tab and open **Static website hosting → Edit**.
  - Enable Static website hosting.
  - Select **Host a static website**.
  - Enter the index document.
  - Save the changes.
  - Screenshot: Page 3 (top)

- Open the uploaded HTML file and navigate to the **Permissions** tab.
  - Under **Access control list (ACL)**, grant **Everyone (public access)** Read permission.
  - Screenshot: Page 3 (bottom)

- Open **Amazon CloudFront → Distributions** and click **Create distribution**.
  - Create a distribution for the S3 static website.
  - Screenshot: Page 4 (top)

- Verify that the CloudFront distribution is created.
  - Copy the CloudFront DNS name and open it in a browser.
  - Verify the website connection.
  - Screenshot: Page 4 (bottom) and Page 5 (top)

- Open **Amazon SNS → Subscriptions**.
  - Create a subscription using the existing SNS topic.
  - Select **Email** as the protocol and provide the email ID as the endpoint.
  - Verify the subscription status.
  - Screenshot: Page 5 (bottom) and Page 6 (top)

### Step 2

Create a VPC, two public & private subnets, public & private route tables, internet gateway for public subnets and NAT gateway for private subnets. Attach VPC to the gateway, edit subnet associations in respective route tables and attach NAT gateway to private route table, and attach Internet gateway to public route tables. Now create two security groups - one for Application load balancer and one for Auto Scaling group. In Security group swh-alb-sg, add HTTP as inbound rule, and in swh-ec2-sg, add HTTP, NFS, SSH as inbound rules.

- Open **Amazon VPC → Your VPCs** and create a VPC.
  - Screenshot: Page 6 (first screenshot)

- Create two public and two private subnets in the VPC.
  - Screenshot: Page 6 (second screenshot)

- Create public and private route tables.
  - Screenshot: Page 6 (third screenshot)

- Create an Internet Gateway and attach it to the VPC.
  - Screenshot: Page 7 (top)

- Create a NAT Gateway.
  - Select the VPC created.
  - Select **Public** as the connectivity type.
  - Select the Elastic IP allocation option.
  - Screenshot: Page 7 (middle)

- Verify that the NAT Gateway is created.
  - Screenshot: Page 7 (bottom)

- Create a VPC endpoint.
  - Verify that the endpoint is available.
  - Screenshot: Page 8

- Edit the subnet associations in the respective route tables.
  - Attach the NAT Gateway to the private route table.
  - Attach the Internet Gateway to the public route table.
  - Screenshot: Page 6 (third screenshot) and Page 7 (bottom)

- Create the security group `swh-alb-sg`.
  - Add HTTP as the inbound rule.
  - Screenshot: Page 9

- Create the security group `swh-ec2-sg`.
  - Add HTTP, NFS and SSH as inbound rules.
  - Screenshot: Page 10 (top)

- Verify that both security groups have been created.
  - Screenshot: Page 10 (bottom)

### Step 3

Create Target group with Port 80, protocol HTTP, target type as INSTANCE, and Application Load Balancer with internet-facing - select availability zones, IP address type, VPC created. Attach the load balancer to target group created.

Create an IAM role ec3-s3-role, with S3FullAccess as IAM policy to EC2 service. Create an EFS file system.

- Open **EC2 → Target groups** and create a target group.
  - Port: **80**
  - Protocol: **HTTP**
  - Target type: **Instances**
  - Screenshot: Page 11 (top)

- Navigate to **EC2 → Load balancers** and create an Application Load Balancer.
  - Scheme: **Internet-facing**
  - Select the IP address type.
  - Select the VPC created.
  - Select the required Availability Zones and public subnets.
  - Attach the target group created.
  - Screenshot: Page 11 (bottom)

- Open **IAM → Roles** and create the IAM role `ec3-s3-role`.
  - Select **EC2** as the trusted entity/service.
  - Attach the **AmazonS3FullAccess** policy.
  - Screenshot: Page 12 (top)

- Open **Amazon EFS → File systems** and create an EFS file system.
  - Verify that the file system is available.
  - Screenshot: Page 12 (bottom)

### Step 4

Create Launch Template with OS, instance type, keypair, security group chose, under Advanced settings select the IAM role created as IAM instance profile, then add then add the user data. Launch the template.

- Open **EC2 → Launch Templates** and click **Create launch template**.
  - Enter the launch template name and description.
  - Select the operating system / AMI.
  - Screenshot: Page 14

- Under **Instance type**, select the required instance type.
- Under **Key pair (login)**, select the key pair.
- Under **Network settings**, select the security group `swh-ec2-sg`.
  - Screenshot: Page 15 (top)

- Under **Advanced details**:
  - Select the IAM role created as the IAM instance profile.
  - Screenshot: Page 15 (bottom)

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
  - Screenshot: Page 16

### Step 5

Create the Auto scaling group, with the launch template created, select private subnets. Instances start to create automatedly from ASG created. Verify the ALB connection by pasting its dns in a browser, and see the website as result.

- Open **EC2 → Auto Scaling Groups** and click **Create Auto Scaling group**.
  - Select the launch template created.
  - Screenshot: Page 17 (top)

- Under **Choose instance launch options**:
  - Select the VPC created.
  - Select the two private subnets.
  - Screenshot: Page 17 (top)

- Under **Integrate with other services**:
  - Attach the Application Load Balancer created.
  - Select the target group created.
  - Configure health checks.
  - Screenshot: Page 17 (bottom)

- Under **Configure group size and scaling policies**:
  - Configure the desired, minimum and maximum capacity.
  - Configure the target tracking scaling policy.
  - Screenshot: Page 18 (top)

- Under **Add notifications**:
  - Select the existing SNS topic.
  - Configure the required event types.
  - Screenshot: Page 18 (middle)

- Review the Auto Scaling group configuration and click **Create Auto Scaling group**.
  - Verify that the EC2 instances are launched.
  - Screenshot: Page 18 (bottom)

- Open the Application Load Balancer and copy its DNS name.
  - Paste the DNS name into a web browser.
  - Verify that the website loads successfully.
  - Screenshot: Page 19

### Step 6

Create Cloudwatch Alarms for the Auto scaling group metrics and create a dashboard.

- Open **CloudWatch → Alarms** and create alarms for the Auto Scaling group metrics.
  - Verify that the alarms are created.
  - Screenshot: Page 20 (top)

- Navigate to **CloudWatch → Dashboards**.
  - Create a dashboard for the Auto Scaling group metrics.
  - Verify that the dashboard is created.
  - Screenshot: Page 20 (bottom)
