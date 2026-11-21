
AWS IAM Users, Groups, Roles & Policies

AWS IAM Users & Groups

Step 1

Open and Login to AWS console, navigate to IAM service and create an IAM user group “devops-fita-wkday”. Name the group, Attach permission policy AdministratorAccess and click “create user group”.

Step 2

Navigate to IAM users. Create an IAM user. Name the user, click the checkbox “Provide user access to AWS Management Console”, choose “Add user to group”, then select the IAM user group created, review and select “Create group”. Under “Retrieve Password”, click Download .csv file. This .csv file contains Username, password and Account ID of the IAM user.

Step 3

Create another user. Under “Set Permissions” choose “Attach policies directly”. Then under “Permission Policies”, choose “EC2FullAccess”, “VPCFullAccess” and “S3FullAccess” policies, then review and click “Create User”. Then download the csv file.

Step 4

Open the .csv file of one IAM user, open the console and sign in as IAM user. Use the username, password and Account ID (from the aws url in .csv file) and sign in to the AWS Console. Before that, change the password. Thus signed into AWS Console as an IAM user successfully.

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
