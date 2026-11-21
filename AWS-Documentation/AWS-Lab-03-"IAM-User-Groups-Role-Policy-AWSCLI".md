
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

## AWS IAM Roles Policies use cases And AWS CLI Access using IAM user

**Step 1**

Navigate to IAM Policy and create a policy. Paste the .json code snippet into the policy json editor and review & create the policy S3ReadOnlyPolicy.

<img width="1260" height="1001" alt="IAM-E-policy-01-createPolicy" src="https://github.com/user-attachments/assets/d2b68c42-0afa-4f06-8099-1276598bc996" />

<img width="1260" height="1001" alt="IAM-E-policy-02-perm-json" src="https://github.com/user-attachments/assets/af3cfac0-ce0b-41f1-9fb4-3d13339c5a69" />

<img width="1254" height="359" alt="IAM-E-policy-03-S3ReadOnlyPolicy-created" src="https://github.com/user-attachments/assets/37088816-a43a-485d-b5b1-372e29259ee0" />


**Step 2**

Create a role ec2S3ReadOnlyRole, select AWS service as “Trusted Entity”, EC2 as “Use case” and select the policy created as “Permission policy”. Review & click “Create role”.

<img width="1260" height="1001" alt="IAM-F-role-01-createRole" src="https://github.com/user-attachments/assets/8c4ee85d-d68d-498e-ba90-09b76e972af0" />

<img width="1260" height="1001" alt="IAM-F-role-02-awsService-ec2" src="https://github.com/user-attachments/assets/1e23019a-246c-4a57-8994-f9706bbf70b5" />

<img width="1250" height="479" alt="IAM-F-role-03-add-perm" src="https://github.com/user-attachments/assets/8d3e5ce4-1496-499c-a88c-152ed41296e6" />

<img width="1260" height="1001" alt="IAM-F-role-04-rolename-createRole" src="https://github.com/user-attachments/assets/733d740f-868b-434d-bff9-b962e4a0092c" />

<img width="1257" height="618" alt="IAM-F-role-05-ec2s3ReadOnlyRole-createdRole" src="https://github.com/user-attachments/assets/e69f5b22-df24-4192-ab79-999cbba43949" />


**Step 3**

Create an EC2 instance “S3-internal-ec2”, select the IAM Role “ec2S3ReadOnlyRole” as “IAM Instance profile” and launch the instance. Then Connect to the ec2 server remotely. The terminal shell of the EC2 instance created will open in the new tab. Update the apt repo, install awscli, list the S3 service’s & Bucket’s contents in the terminal in .json format.
Note : use this command before awscli commands.

```bash
aws sts get-caller-identity
```

<img width="1260" height="1001" alt="IAM-G-ec2-01-IAMrole" src="https://github.com/user-attachments/assets/47cd0bde-7081-42a4-8992-9a939324f900" />

<img width="1260" height="1001" alt="IAM-G-ec2-02a-connectEC2" src="https://github.com/user-attachments/assets/048160c1-fc20-4576-9b84-4a4abc9563c8" />

<img width="1260" height="1001" alt="IAM-G-ec2-02b-connectEC2" src="https://github.com/user-attachments/assets/5f21882e-1b66-4e33-8f9d-0ff32e135059" />

<img width="1260" height="1001" alt="IAM-G-ec2-03-console-awscli-sts-s3" src="https://github.com/user-attachments/assets/e7dc652e-d8cd-43e3-9f06-67f33633ed24" />


**Step 4**

Create another IAM user “ranjit-ec2” without AWS Management Console Access and provide AmazonEC2FullAccess “Permission policy”.

<img width="1253" height="410" alt="IAM-H-awscli-01-user-noConsoleAccess" src="https://github.com/user-attachments/assets/c1f6bcc2-995e-4bd4-b25c-fb193b059fb2" />

<img width="827" height="736" alt="IAM-H-awscli-02-ec2fullAccess-next" src="https://github.com/user-attachments/assets/74709875-2efa-4fc7-8607-06213618cc02" />

<img width="1245" height="555" alt="IAM-H-awscli-03-createUser" src="https://github.com/user-attachments/assets/94081133-ead7-41b0-984a-88dda8a3f63d" />


**Step 5**

Navigate to “Security Credentials” of the IAM User created. Click, “Create Access key”. Inside Access key creation, select CLI & confirm it, provide an optimal description and download the .csv file for Access key & Secret key. Open the terminal, “aws configure” - provide the keys from .csv file, region and type of output (json or text). Run “aws ec2 describe-instances”, it outputs the data about the instances currently in this region in EC2 service.

<img width="1243" height="383" alt="IAM-I-awscli-01-click-createAccessKey" src="https://github.com/user-attachments/assets/0a4f69c9-bc2f-4104-8b7d-4678294f71c8" />

<img width="1036" height="727" alt="IAM-I-awscli-02-AccKey-CLI" src="https://github.com/user-attachments/assets/e1172602-518e-431b-82c0-7a37760b2369" />

<img width="1051" height="312" alt="IAM-I-awscli-03-AccKey-description" src="https://github.com/user-attachments/assets/2122bd3e-87a2-4ee4-934e-9695cfcfd60c" />

<img width="1244" height="606" alt="IAM-I-awscli-04-AccKey-csvFile-created" src="https://github.com/user-attachments/assets/03de7387-4cf2-4ea4-bdcb-adf68a4e79b8" />

<img width="936" height="1034" alt="IAM-I-awscli-05-aws-terminal-cli" src="https://github.com/user-attachments/assets/410624ce-9824-46d8-906a-5116769cbb6c" />



