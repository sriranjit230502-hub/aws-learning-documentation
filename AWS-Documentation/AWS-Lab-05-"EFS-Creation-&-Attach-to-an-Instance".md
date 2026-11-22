
# AWS Elastic File System Storage Attached to an EC2 Instance

### Step 1

Create an Elastic File system (EFS), name it and select the vpc created. Click “Create file system”.

<img width="1600" height="900" alt="IMG-20260813-WA0001" src="https://github.com/user-attachments/assets/0853f9ee-9181-4bf0-8316-164d85668609" />


### Step 2

Create an ec2 instance by configuring OS, instance type, key, vpc, security group as usual. Under Storage, select EFS. Launch instance.

<img width="1600" height="900" alt="IMG-20260813-WA0003" src="https://github.com/user-attachments/assets/489837c8-f43a-4f5a-82a7-305a13faa921" />


### Step 3

In EC2, under security groups edit the Inbound rules. Add NFS port as an inbound rule and select anywhere as a custom type. Save it.

<img width="1600" height="900" alt="IMG-20260813-WA0008" src="https://github.com/user-attachments/assets/02e5e2c2-af70-446c-9161-a39a7cd0fe75" />

<img width="1600" height="900" alt="IMG-20260813-WA0009" src="https://github.com/user-attachments/assets/846d4675-e215-4eb3-8b99-f1fc1323955b" />



### Step 4

Navigate to EFS created, under “Network access” click “manage”. Add the security group that contains NFS and other ports attached to our Instance. Save it.

<img width="1600" height="900" alt="IMG-20260813-WA0007" src="https://github.com/user-attachments/assets/eb353617-7131-43e7-bd52-c4a3bb03f333" />


### Step 5

Open the terminal, SSH into the instance created. Then create a directory /mnt/efs. Install nfs-common from the apt repository. Then use this command to attach the instance created to the EFS created,

```bash
sudo mount -t nfs4 -o nfsvers=4.1 {fs-1234567890abcdef.efs.ap-south-1.amazonaws.com}:/ /mnt/efs
```

“Note : The Curly braced part is the dns, which should be copied from EFS and pasted there.”

Check the disk storage to verify whether EFS (8.0 E) attached.

<img width="1046" height="683" alt="Screenshot from 2026-08-13 08-45-05" src="https://github.com/user-attachments/assets/4f887fb7-45b5-44ee-958c-41bef768746c" />


<img width="1160" height="959" alt="Screenshot from 2026-08-13 08-46-16" src="https://github.com/user-attachments/assets/95996ca5-a16f-4913-8388-d695d3f58aca" />


