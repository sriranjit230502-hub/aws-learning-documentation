
# AWS IAM Users, Groups, Roles & Policies

## AWS IAM Users & Groups

**Step 1**

Open and Login to AWS console, navigate to IAM service and create an IAM user group “devops-fita-wkday”. Name the group, Attach permission policy AdministratorAccess and click “create user group”.

<img width="1321" height="357" alt="IAM-A-grp-01createGrp" src="https://github.com/user-attachments/assets/a6d819c1-b9ea-483f-993f-ef62fdd3c88b" />

<img width="1312" height="395" alt="IAM-A-grp-02-GrpName" src="https://github.com/user-attachments/assets/ea5997c7-33bb-4679-abc3-4dc2a1fb49de" />

<img width="1314" height="838" alt="IAM-A-grp-03-permPolicies" src="https://github.com/user-attachments/assets/a330c065-55dd-48d1-8026-7418dce3f405" />

<img width="1325" height="272" alt="IAM-A-grp-04-grpCreatedSuccflly" src="https://github.com/user-attachments/assets/73e60ef5-2233-4f48-acaa-51b284573dbf" />




**Step 2**

Navigate to IAM users. Create an IAM user. Name the user, click the checkbox “Provide user access to AWS Management Console”, choose “Add user to group”, then select the IAM user group created, review and select “Create group”. Under “Retrieve Password”, click Download .csv file. This .csv file contains Username, password and Account ID of the IAM user.

<img width="1324" height="288" alt="IAM-B-usr-01createUsr" src="https://github.com/user-attachments/assets/92b81105-3ac9-44fc-9683-723a88e592aa" />

<img width="1286" height="590" alt="IAM-B-usr-02-usrnm-ProvideUsrAccs" src="https://github.com/user-attachments/assets/5fbd96a7-d31f-4186-8fe8-8878424d1fea" />

<img width="1292" height="507" alt="IAM-B-usr-03-setPerm" src="https://github.com/user-attachments/assets/2e3d7601-2298-478b-9e74-92d75e52b444" />

<img width="1327" height="668" alt="IAM-B-usr-04-Review-createUsr" src="https://github.com/user-attachments/assets/725eb2f8-c2f9-4c4c-b1a5-541186c0b321" />

<img width="1037" height="336" alt="IAM-B-usr-05-csvDownload-clickReturn" src="https://github.com/user-attachments/assets/e072baa9-c9ba-4b5e-8c6e-5e8758b42777" />




**Step 3**

Create another user. Under “Set Permissions” choose “Attach policies directly”. Then under “Permission Policies”, choose “EC2FullAccess”, “VPCFullAccess” and “S3FullAccess” policies, then review and click “Create User”. Then download the csv file.

<img width="1036" height="613" alt="IAM-C-usr2-01-attachPolicy-setPerm-EC2fullaccs" src="https://github.com/user-attachments/assets/48a498cf-51b8-4248-a92b-c79ba0ebd1a3" />

<img width="1040" height="437" alt="IAM-C-usr2-02-attachPolicy-setPerm-S3fullaccs" src="https://github.com/user-attachments/assets/aa76fd38-ab6c-407e-9678-b60c474e14d3" />

<img width="1024" height="827" alt="IAM-C-usr2-03-attachPolicy-setPerm-VPCfullaccs png" src="https://github.com/user-attachments/assets/5fd01b60-4c81-4663-bc2b-70043b9f41ad" />

<img width="1035" height="595" alt="IAM-C-usr2-04-review-create" src="https://github.com/user-attachments/assets/e7747121-f6d3-4d25-9e3f-9f3c05a4333b" />

<img width="1032" height="293" alt="IAM-C-usr2-06-csvDownload-clickReturn" src="https://github.com/user-attachments/assets/b3ee9f1b-0cc0-455b-aede-e2fc281e0098" />

<img width="1326" height="359" alt="IAM-C-usr2-07-createdUsers" src="https://github.com/user-attachments/assets/6febc2f2-33a2-4024-a407-8da86bda73a4" />


**Step 4**

Open the .csv file of one IAM user, open the console and sign in as IAM user. Use the username, password and Account ID (from the aws url in .csv file) and sign in to the AWS Console. Before that, change the password. Thus signed into AWS Console as an IAM user successfully.

<img width="1920" height="1080" alt="IAM-D-login-01-accID-usrnm-psswd" src="https://github.com/user-attachments/assets/f5282d61-39e4-4a5d-97e9-040d50196376" />

<img width="972" height="1045" alt="IAM-D-login-02-psswdChange" src="https://github.com/user-attachments/assets/67fc6eae-020a-4cd2-9de2-1cbe28e2cd18" />

<img width="335" height="331" alt="IAM-D-login-03-psswdChangeSuccfly" src="https://github.com/user-attachments/assets/34488b16-197b-4a36-8ea2-855638c6548c" />

<img width="972" height="1045" alt="IAM-D-login-04-signedIN" src="https://github.com/user-attachments/assets/a5426bf0-e224-409c-a9df-7171745eea9d" />



---

AWS IAM Roles Policies use cases And AWS CLI Access using IAM user

Step 1

Navigate to IAM Policy and create a policy. Paste the .json code snippet into the policy json editor and review & create the policy S3ReadOnlyPolicy.

Step 2

Create a role ec2S3ReadOnlyRole, select AWS service as “Trusted Entity”, EC2 as “Use case” and select the policy created as “Permission policy”. Review & click “Create role”.

Step 3

Create an EC2 instance “S3-internal-ec2”, select the IAM Role “ec2S3ReadOnlyRole” as “IAM Instance profile” and launch the instance. Then Connect to the ec2 server remotely. The terminal shell of the EC2 instance created will open in the new tab. Update the apt repo, install awscli, list the S3 service’s & Bucket’s contents in the terminal in .json format.

Note : use this command before awscli commands.

aws sts get-caller-identity
Step 4

Create another IAM user “ranjit-ec2” without AWS Management Console Access and provide AmazonEC2FullAccess “Permission policy”.

Step 5

Navigate to “Security Credentials” of the IAM User created. Click, “Create Access key”. Inside Access key creation, select CLI & confirm it, provide an optimal description and download the .csv file for Access key & Secret key. Open the terminal, “aws configure” - provide the keys from .csv file, region and type of output (json or text). Run “aws ec2 describe-instances”, it outputs the data about the instances currently in this region in EC2 service.
