# AWS DynamoDB Creation & functioning using AWSCLI

## AWSCLI DynamoDB Commands

```bash
aws dynamodb create-table \
  --table-name Students \
  --attribute-definitions \
    AttributeName=StudentId,AttributeType=S \
  --key-schema \
    AttributeName=StudentId,KeyType=HASH \
  --billing-mode PAY_PER_REQUEST \
  --region ap-south-1

aws dynamodb list-tables --region ap-south-1

aws dynamodb describe-table \
  --table-name Students \
  --region ap-south-1

aws dynamodb put-item \
  --table-name Students \
  --item '{
    "StudentId": {"S": "STU001"},
    "Name": {"S": "Raghul"},
    "Course": {"S": "AWS DevOps"},
    "Age": {"N": "25"}
  }' \
  --region ap-south-1

aws dynamodb put-item \
  --table-name Students \
  --item '{
    "StudentId": {"S": "STU002"},
    "Name": {"S": "Arun"},
    "Course": {"S": "Cloud Computing"},
    "Age": {"N": "22"}
  }' \
  --region ap-south-1

aws dynamodb scan \
  --table-name Students \
  --region ap-south-1
```

---

## AWSCLI DynamoDB Using IAM User

### Step 1
Create an IAM User with 'DynamoDBFullAccess' as existing IAM Policy and create access key. Navigate to terminal and login to the newly created IAM User through `aws configure` AWS CLI command using created access key & secret access key for that IAM User.

<img width="1920" height="1080" alt="AWSCLI-DynamoDB-01-create-table" src="https://github.com/user-attachments/assets/80f42e9b-36e0-4814-ba81-cae59c12b5b3" />


### Step 2
Create a table with name, attributes, key schema and specify the region using AWS CLI commands in the terminal.

```bash
aws dynamodb create-table \
  --table-name Students \
  --attribute-definitions \
    AttributeName=StudentId,AttributeType=S \
  --key-schema \
    AttributeName=StudentId,KeyType=HASH \
  --billing-mode PAY_PER_REQUEST \
  --region ap-south-2
```

<img width="1920" height="1080" alt="AWSCLI-DynamoDB-02-list-describe-put" src="https://github.com/user-attachments/assets/06f0b9cf-4cd7-402f-b2c0-3806421c5942" />


### Step 3
Now list the table created and put items into the table.

```bash
aws dynamodb list-tables --region ap-south-2

aws dynamodb put-item \
  --table-name Students \
  --item '{
    "StudentId": {"S": "STU001"},
    "Name": {"S": "Raghul"},
    "Course": {"S": "AWS DevOps"},
    "Age": {"N": "25"}
  }' \
  --region ap-south-2

aws dynamodb put-item \
  --table-name Students \
  --item '{
    "StudentId": {"S": "STU002"},
    "Name": {"S": "Arun"},
    "Course": {"S": "Cloud Computing"},
    "Age": {"N": "22"}
  }' \
  --region ap-south-2
```


<img width="1920" height="1080" alt="AWSCLI-DynamoDB-03-list-desctribe-scan" src="https://github.com/user-attachments/assets/4909029b-3d9b-40dc-bca4-53b824c5e4c5" />


### Step 4
Now again verify by listing tables created, contents along with the table and scan the table created.

```bash
aws dynamodb list-tables --region ap-south-2

aws dynamodb describe-table \
  --table-name Students \
  --region ap-south-2

aws dynamodb scan \
  --table-name Students \
  --region ap-south-2
```

<img width="1920" height="1080" alt="AWSCLI-DynamoDB-00-aws-configure" src="https://github.com/user-attachments/assets/f41ad73e-b5ed-4dd5-bbc3-527346ef9285" />
