# AWS Lab 02 — EC2 Instance Configuration

## 1. AWS EC2 Instance Creation – Ubuntu

### Step 1

Log in to AWS Console, navigate to EC2 instances and click ‘Launch Instance’. Inside, name the instance ec2-210726, choose the preferred OS and cpu Architecture of the server (Ubuntu OS here with x86_64).

<img width="1095" height="783" alt="A-01-ec2-nm,os,cpu" src="https://github.com/user-attachments/assets/7accaca8-a3f5-4062-8331-9a06e1a9c3d4" />


### Step 2

Choose the ‘Instance Type’ t3.micro.

<img width="681" height="207" alt="A-02-ec2-inst-ty-t3-micro" src="https://github.com/user-attachments/assets/fa9d40a4-e93a-472f-b868-681d14d61aba" />


### Step 3

Under ‘Key pair (login)’, click Create new key pair.

<img width="662" height="164" alt="A-03a-ec2-new-kepr" src="https://github.com/user-attachments/assets/ec66c38b-2f82-4146-928c-a9b618842386" />


### Step 4

Name the key pair 210726-ec2-key, choose one ‘key pair type’ (ED25519 is preferred for linux servers) and choose a ‘private key file format’ (.pem is always preferred here). Then click Create key pair.

<img width="874" height="476" alt="A-03b-ec2-kepr-nm,ED,pem" src="https://github.com/user-attachments/assets/b467c587-08c7-45cc-911e-b2a8967c910c" />


### Step 5

Select the key pair created 210726-ec2-key.

<img width="726" height="184" alt="A-03c-ec2-kepr-choose" src="https://github.com/user-attachments/assets/8dbc3360-8964-4490-a105-e669e199bcdc" />


### Step 6

Under the ‘Network settings’, select the VPC created in this region vpc-tsk-160726, allocate the subnet created and enable the Auto-assign public IP.

Under ‘Firewall’, select Create security group and name it ec2-210726-1, then add a description for it too.

<img width="712" height="546" alt="A-04-ec2-VPC+firewall" src="https://github.com/user-attachments/assets/79f5ea63-dda1-42e9-8e01-ec14d0145530" />


### Step 7

Under ‘Inbound Security Group Rules', click add security group rule and choose HTTP and HTTPS as types, 0.0.0.0/0 as source.

<img width="725" height="703" alt="A-05-ec2-SecGrpRules-ssh,http,https" src="https://github.com/user-attachments/assets/26f7a26b-0598-4782-b193-6d2a708c1b49" />


### Step 8

Under ‘Configure storage’, select 8 GiB and gp3 respectively and choose File system (None). Click “Launch Instance”.

<img width="1067" height="408" alt="A-06-ec2-storage+filesys" src="https://github.com/user-attachments/assets/91f980f5-6678-4b51-ab8d-38d753e3c86f" />


### Step 9

The EC2 instance ec2-210726 is successfully created and the Instance state is Running.

<img width="1908" height="834" alt="A-07-ec2-210726-instance-run" src="https://github.com/user-attachments/assets/5bc8b32d-a4ce-41bc-95a4-12f3ac4ccda1" />


---

## 2. AWS EC2 Instance Creation – Windows

### Step 1

Log in to AWS Console, navigate to EC2 instances and click ‘Launch Instance’. Inside, name the instance ec2-wnds-26072, choose the preferred OS and cpu Architecture of the server (Windows OS here with x86_64).

<img width="1091" height="812" alt="D-01-ec2-winds-260726-nm,os,type" src="https://github.com/user-attachments/assets/bd8ce15e-a1c8-42f5-bcac-b426322b57da" />


Choose the ‘Instance Type’ t3.micro.

### Step 2

Under ‘Key pair (login)’, click Create new key pair.

<img width="720" height="167" alt="D-02a-ec2-wnds-kepr" src="https://github.com/user-attachments/assets/2df2b045-6e62-4c44-836a-404645607499" />


### Step 3

Name the key pair ec2-wnds-kpr, choose one ‘key pair type’ (RSA is mandatory for all Windows servers) and choose a ‘private key file format’ (.pem is always preferred here). Then click ‘Create key pair’.

<img width="1048" height="469" alt="D-02b-ec2-wnds-kepr" src="https://github.com/user-attachments/assets/3590275f-c688-45a9-9b95-7dde204d4ad3" />


### Step 4

Select the key pair created ec2-wnds-key.

<img width="717" height="160" alt="D-02c-ec2-wnds-kepr" src="https://github.com/user-attachments/assets/39b85352-11ee-405a-a6ae-a82701ff0f16" />


### Step 5

Under the ‘Network settings’, select the VPC created in this region vpc-tsk-160726, allocate the subnet created and enable the Auto-assign public IP.

Under ‘Firewall’, select Create security group and name it ec2-wnds-1, then add a description for it too.

<img width="722" height="433" alt="D-03-ec2-wnds-VPC+firewall" src="https://github.com/user-attachments/assets/493f960c-8e7e-4187-86b3-0eb00a26d127" />


### Step 6

Under ‘Inbound Security Group Rules', click add security group rule and choose HTTP and HTTPS as types, 0.0.0.0/0 as source.

<img width="690" height="593" alt="D-04-ec2-wnds-rdp,http,https" src="https://github.com/user-attachments/assets/f4932600-c6d7-44c4-8830-0f0671d6b22a" />


### Step 7

Under ‘Configure storage’, select 30 GiB and gp3 respectively and choose File system (None). Click “Launch Instance”.

<img width="1074" height="330" alt="D-05-ec2-wnds-launch-instance" src="https://github.com/user-attachments/assets/370b2fe4-5f1c-46c8-9681-8b3392ced260" />


### Step 8

The EC2 instance ec2-wnds-26072 is successfully created and the Instance state is Running.

<img width="1917" height="297" alt="D-06-ec2-wnds-instance-run" src="https://github.com/user-attachments/assets/f67377b5-c14c-475e-a91c-13d907c64433" />


---

## 3. AWS EC2 AMI – Ubuntu

### Step 1

Navigate to EC2 -> Instances. Select the instance created ec2-210726. Click ‘Actions’, select ‘Image and templates’ and click ‘Create Image’.

<img width="1090" height="836" alt="B-02-ec2-210726ubu-ami-create" src="https://github.com/user-attachments/assets/e132baf0-f0b3-4691-8610-37ea5965635e" />



### Step 2

Inside ‘Create Image’, name the image ec2-210726ubu-ami, then uncheck the Reboot Instance and click ‘Create Image’.

<img width="1917" height="320" alt="B-03-ec2-210726ubu-ami-created" src="https://github.com/user-attachments/assets/9d671263-6529-4d43-ae88-2a3f96bcf2cb" />



### Step 3

Thus ‘Amazon Machine Image’ (AMI) of the instance ec2-210726 has been created.

<img width="1093" height="351" alt="B-01-ec2-210726-actions,crt-image" src="https://github.com/user-attachments/assets/d0f0541e-0251-4ea4-ba2c-8e88cf2a6122" />



---

## 4. SSH into the EC2 Instance – Ubuntu

### Step 1

Open the Linux terminal.

<img width="1237" height="799" alt="01-ssh-open-open-terminal" src="https://github.com/user-attachments/assets/0ab15da9-7a96-4166-87e8-83469f1cce0b" />



### Step 2

Note down the IPv4 public IP of the EC2 instance to SSH.

<img width="1256" height="254" alt="02-ssh-aws-console-IP" src="https://github.com/user-attachments/assets/1fd16394-3b7f-4f3f-a6d0-c370e923941f" />



### Step 3

Check the keypair 210726-ec2-key's file location, permission and note down the directory path of that file.

<img width="1237" height="799" alt="03-ssh-pem-location-perm" src="https://github.com/user-attachments/assets/86e3313d-097d-41a9-a7dd-0493b871eb28" />



### Step 4

Now SSH into the ec2 instance created in the format username@publicIP [ubuntu@16.112.191.150 here] along with the .pem key pair file path.

<img width="1028" height="716" alt="04-ssh-command" src="https://github.com/user-attachments/assets/da951ea7-9040-424e-a935-d1423f66ca66" />



### Step 5

Thus successfully connected to the AWS ec2 server created from our local machine's terminal using SSH. Now we can check file system storage, memory, list contents, etc from our local machine's terminal.

<img width="1237" height="799" alt="05-ssh-filesys-mem-ll" src="https://github.com/user-attachments/assets/90aa7980-8372-4085-8f46-1e3127ae355b" />



---

## 5. Create a "Snapshot" of Ubuntu EC2 Instance's Volume

### Step 1

Navigate to the left side bar, under "Elastic Block Storage" lick "Volumes". Select the instance created volumne, click Actions, click "Create Snapshot".

<img width="1101" height="432" alt="C-01-ec2-210726-snapshot-step01" src="https://github.com/user-attachments/assets/6ea39914-2980-45f1-b34c-8d3411889ea5" />


### Step 2

Under "Snapshot Details", give a short-form description, add a tag & value and click "Create Snapshot".

<img width="1098" height="666" alt="C-02-ec2-210726-snapshot-step02" src="https://github.com/user-attachments/assets/f29a246c-0abc-479b-ba36-a0493fad2405" />


### Step 3

Thus the "Snapshot" of the Ubuntu EC2 instance created.

<img width="1913" height="286" alt="C-03-ec2-210726-snapshot-step03" src="https://github.com/user-attachments/assets/5b885978-2ccd-43b2-ae0d-bf51350901e6" />




