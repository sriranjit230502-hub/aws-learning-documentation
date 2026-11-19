# AWS Lab 02 — EC2 Instance Configuration

## 1. AWS EC2 Instance Creation – Ubuntu

### Step 1

Log in to AWS Console, navigate to EC2 instances and click ‘Launch Instance’. Inside, name the instance ec2-210726, choose the preferred OS and cpu Architecture of the server (Ubuntu OS here with x86_64).

### Step 2

Choose the ‘Instance Type’ t3.micro.

### Step 3

Under ‘Key pair (login)’, click Create new key pair.

### Step 4

Name the key pair 210726-ec2-key, choose one ‘key pair type’ (ED25519 is preferred for linux servers) and choose a ‘private key file format’ (.pem is always preferred here). Then click Create key pair.

### Step 5

Select the key pair created 210726-ec2-key.

### Step 6

Under the ‘Network settings’, select the VPC created in this region vpc-tsk-160726, allocate the subnet created and enable the Auto-assign public IP.

Under ‘Firewall’, select Create security group and name it ec2-210726-1, then add a description for it too.

### Step 7

Under ‘Inbound Security Group Rules', click add security group rule and choose HTTP and HTTPS as types, 0.0.0.0/0 as source.

### Step 8

Under ‘Configure storage’, select 8 GiB and gp3 respectively and choose File system (None). Click “Launch Instance”.

### Step 9

The EC2 instance ec2-210726 is successfully created and the Instance state is Running.

---

## 2. AWS EC2 Instance Creation – Windows

### Step 1

Log in to AWS Console, navigate to EC2 instances and click ‘Launch Instance’. Inside, name the instance ec2-wnds-26072, choose the preferred OS and cpu Architecture of the server (Windows OS here with x86_64).

Choose the ‘Instance Type’ t3.micro.

### Step 2

Under ‘Key pair (login)’, click Create new key pair.

### Step 3

Name the key pair ec2-wnds-kpr, choose one ‘key pair type’ (RSA is mandatory for all Windows servers) and choose a ‘private key file format’ (.pem is always preferred here). Then click ‘Create key pair’.

### Step 4

Select the key pair created ec2-wnds-key.

### Step 5

Under the ‘Network settings’, select the VPC created in this region vpc-tsk-160726, allocate the subnet created and enable the Auto-assign public IP.

Under ‘Firewall’, select Create security group and name it ec2-wnds-1, then add a description for it too.

### Step 6

Under ‘Inbound Security Group Rules', click add security group rule and choose HTTP and HTTPS as types, 0.0.0.0/0 as source.

### Step 7

Under ‘Configure storage’, select 30 GiB and gp3 respectively and choose File system (None). Click “Launch Instance”.

### Step 8

The EC2 instance ec2-wnds-26072 is successfully created and the Instance state is Running.

---

## 3. AWS EC2 AMI – Ubuntu

### Step 1

Navigate to EC2 -> Instances. Select the instance created ec2-210726. Click ‘Actions’, select ‘Image and templates’ and click ‘Create Image’.

### Step 2

Inside ‘Create Image’, name the image ec2-210726ubu-ami, then uncheck the Reboot Instance and click ‘Create Image’.

### Step 3

Thus ‘Amazon Machine Image’ (AMI) of the instance ec2-210726 has been created.

---

## 4. SSH into the EC2 Instance – Ubuntu

### Step 1

Open the Linux terminal.

### Step 2

Note down the IPv4 public IP of the EC2 instance to SSH.

### Step 3

Check the keypair 210726-ec2-key's file location, permission and note down the directory path of that file.

### Step 4

Now SSH into the ec2 instance created in the format username@publicIP [ubuntu@16.112.191.150 here] along with the .pem key pair file path.

### Step 5

Thus successfully connected to the AWS ec2 server created from our local machine's terminal using SSH. Now we can check file system storage, memory, list contents, etc from our local machine's terminal.
