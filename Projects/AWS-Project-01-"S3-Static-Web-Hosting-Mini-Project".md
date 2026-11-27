# AWS S3 Static Website Hosting Mini-project

### Step 1

Create an S3 bucket, upload an index.html file and enable static web hosting.

- Open **Amazon S3 → General purpose buckets** and click **Create bucket**.
  - Select **Account Regional namespace** and enter the bucket name.
<img width="1109" height="1001" alt="A-S3-01" src="https://github.com/user-attachments/assets/3c48eaad-98dc-4e70-af91-bdc2dfb81b78" />

<img width="1081" height="614" alt="A-S3-02" src="https://github.com/user-attachments/assets/7b1930dd-c95a-475c-8621-00a750655bb5" />


- Under **Object Ownership**, select **ACLs enabled** and **Bucket owner preferred**.
- Under **Block Public Access settings**, uncheck **Block all public access** and acknowledge the warning.
- Under **Bucket Versioning**, select **Disable**.
<img width="1085" height="785" alt="A-S3-03" src="https://github.com/user-attachments/assets/3f1fec69-fe8e-4d10-9cec-1e48a03241c9" />


- Under **Default encryption**, select **Server-side encryption with Amazon S3 managed keys (SSE-S3)**.
- Keep **Object Lock** disabled.
- Click **Create bucket**.
<img width="1063" height="709" alt="A-S3-04" src="https://github.com/user-attachments/assets/fe6609cd-14d0-4ffd-8924-2a3b013ea341" />
 
- Open the created bucket, click **Upload**, select the `index.html` file and upload it.
<img width="1109" height="1001" alt="A-S3-05" src="https://github.com/user-attachments/assets/98a3110f-ecf5-4ada-9afd-ee73148b0c97" />


- Navigate to the bucket's **Properties** tab and open **Static website hosting → Edit**.
<img width="1109" height="1001" alt="A-S3-06" src="https://github.com/user-attachments/assets/822d7be0-017a-4d42-888e-96a7a05d6d74" />

- Enable **Static website hosting**.
- Select **Host a static website** as the hosting type.
- Enter `index.html` as the Index document and save the changes.
<img width="961" height="690" alt="A-S3-07" src="https://github.com/user-attachments/assets/efa41200-939a-4c11-b6d3-6d9acb6b722c" />

- Open the uploaded `index.html` file and navigate to the **Permissions** tab.
- Under **Access control list (ACL)**, grant **Everyone (public access)** Read permission.
<img width="1096" height="458" alt="A-S3-08" src="https://github.com/user-attachments/assets/90a86d82-fd5d-4968-9763-5b6f1368a567" />

### Step 2

Create a Cloudfront distribution for the S3 bucket created where static webhosting enabled. Copy the cloudfront dns and paste in a web browser, to verify the Cloudfront-S3 connection establishment.

- Open **Amazon CloudFront → Distributions** and click **Create distribution**.
<img width="1109" height="1001" alt="A-CF-01-" src="https://github.com/user-attachments/assets/68fdcb72-43c8-43a1-850c-3f8ddde576a6" />

- Under **Get started**, select **Single website or app** as the distribution type.
- Enter the distribution name: `s3-swh-01`.
<img width="1109" height="1001" alt="A-CF-02" src="https://github.com/user-attachments/assets/d5660a49-46b3-420c-8273-b96617fac3d9" />

- Under **Specify origin**, select **Amazon S3** as the Origin type.
- Select the S3 static website endpoint as the origin.
- Keep the recommended origin and cache settings.
<img width="1109" height="1001" alt="A-CF-03" src="https://github.com/user-attachments/assets/b174a063-0a9c-4cf6-bccc-2dae7c66d5f8" />

- Under **Enable security**, select **Use monitor mode** for AWS WAF.
<img width="1101" height="418" alt="A-CF-04" src="https://github.com/user-attachments/assets/e281502a-c804-49a4-b927-7bd83b21a891" />

- Review the configuration and click **Create distribution**.
<img width="1109" height="1001" alt="A-CF-05" src="https://github.com/user-attachments/assets/256fa5bc-eac9-4e40-ae47-35c070359d1e" />


- Copy the CloudFront distribution domain name and open it in a web browser.
- Verify that the hosted website loads successfully.
<img width="1082" height="579" alt="A-CF-06" src="https://github.com/user-attachments/assets/c7ad8477-d535-427c-b043-ec79aa4c9103" />

<img width="1109" height="1001" alt="A-CF-07" src="https://github.com/user-attachments/assets/e33027b0-c320-465b-a1e9-4d2b04c831cf" />


### Step 3

Create an SNS topic with standard type and create a subscription with Email as endpoint and provide the email ID. Open a mail client, open the email received from AWS currently and click “confirm subscription” - and report as not spam option if available.

- Open **Amazon SNS → Topics** and click **Create topic**.
<img width="1109" height="1001" alt="B-SNS-01" src="https://github.com/user-attachments/assets/4c1ce8dd-35af-401a-8eb1-a1615e743fb4" />

- Under **Create topic → Details**:
  - Select **Standard** as the topic type.
  - Enter the topic name: `s3-swh-cf-alerts-01`.
  - Enter the display name: `s3-cloudfront-alerts-01`.
  - Click **Create topic**.
 <img width="1059" height="847" alt="B-SNS-02" src="https://github.com/user-attachments/assets/c93679db-0150-4a59-a278-320bcf6a6839" />

- Open the created topic and navigate to the **Subscriptions** tab.
- Click **Create subscription**.
<img width="1068" height="481" alt="B-SNS-03" src="https://github.com/user-attachments/assets/af6cc00a-3c2a-43a7-b401-457095994b74" />

- Under **Create subscription**:
  - Select **Email** as the Protocol.
  - Enter the email address as the Endpoint.
  - Click **Create subscription**.
<img width="1064" height="512" alt="B-SNS-04" src="https://github.com/user-attachments/assets/315570e2-4f0a-44b3-a9eb-841bc4370a5c" />

- Open the email received from AWS and click **Confirm subscription**.
- Verify that the subscription status is **Confirmed**.
<img width="1077" height="197" alt="B-SNS-05" src="https://github.com/user-attachments/assets/7e581623-1ef7-4c9f-9a2b-0a484d06babd" />

### Step 4

Create a Cloudwatch Alarm for the cloudfront - the metrics for cloudfront are available in us-east-1 AZ since Cloudfront is a global service, select requests as metrics, and provide statistics, period & threshold needed. Select the existing SNS topic, provide a name and create the Alarm. Now create a Cloudwatch dashboard for the Cloudfront metrics.

- Open **CloudWatch → Alarms** and click **Create alarm**.
<img width="1077" height="346" alt="C-Cwatch-01" src="https://github.com/user-attachments/assets/4230926c-eeb0-4bb1-99c9-9820b4f68082" />

- Under **Specify metric and conditions**:
  - Select **Metrics** as the data source.
  - Select **Classic** as the alarm type.
  - Click **Select metric**.
<img width="1072" height="493" alt="C-Cwatch-02" src="https://github.com/user-attachments/assets/54fa646b-9fc0-4d76-aa23-96930de2b309" />

- Change the AWS console region to **US East (N. Virginia) – us-east-1**.
<img width="1080" height="1001" alt="C-Cwatch-03" src="https://github.com/user-attachments/assets/0f447e6c-b719-448f-a929-7cc42251690c" />

- Under **Select metric**, navigate to **CloudFront → Per-Distribution Metrics**.
- Select **Requests** and click **Select metric**.
<img width="974" height="772" alt="C-Cwatch-04" src="https://github.com/user-attachments/assets/5ac23f09-36dd-4a62-9e6a-d594df880c5c" />

<img width="975" height="771" alt="C-Cwatch-05" src="https://github.com/user-attachments/assets/54bb815a-5b0e-4baa-b065-f7765433e2a3" />


- Under **Metric and Conditions**, configure:
  - Statistic: **Sum**
  - Period: **5 minutes**
  - Threshold type: **Static**
  - Whenever Requests is: **Greater**
  - Threshold value: **0**
<img width="839" height="737" alt="C-Cwatch-06" src="https://github.com/user-attachments/assets/1e7ab463-9e36-49fc-ac5f-5e5417a4c255" />

- Under **Configure actions**:
  - Select **In alarm** as the alarm state trigger.
  - Select the existing SNS topic: `s3-swh-cf-alerts-01`.
<img width="1067" height="744" alt="C-Cwatch-07" src="https://github.com/user-attachments/assets/2825a88e-984e-451b-ba2b-670a0eb82136" />

- Under **Add alarm details**:
  - Enter the alarm name: `s3-cloudfront-swh-Alarm-01`.
  - Enter a description if required.
 <img width="1068" height="538" alt="C-Cwatch-08" src="https://github.com/user-attachments/assets/0c4ddc95-b2f8-4054-bc54-020fed3e1d89" />

- Review the configuration and click **Create alarm**.
- Verify that the alarm appears under CloudWatch Alarms.
<img width="953" height="806" alt="C-Cwatch-09" src="https://github.com/user-attachments/assets/ac10cd2b-a1dc-492d-84aa-4c6516c28772" />

- Navigate to **CloudWatch → Dashboards**.
- Open the dashboard `SWH-Cloudfront-01`.
- Add a widget for the CloudFront **Requests** metric and save the dashboard.
<img width="1080" height="1001" alt="C-Cwatch-11" src="https://github.com/user-attachments/assets/abe86ae9-65c4-4193-b332-9d248ae9c15a" />

- Verify the CloudWatch alarm notification received through email.
<img width="1073" height="354" alt="C-Cwatch-10" src="https://github.com/user-attachments/assets/952ef8a0-2851-4eb4-b4c0-8ce263d82edd" />

<img width="1316" height="969" alt="Cloudwatch-cloudfront-notification" src="https://github.com/user-attachments/assets/0bcc0e8e-221b-468c-a9e0-ded43a9e96b8" />

