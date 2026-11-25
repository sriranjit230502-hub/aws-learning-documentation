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
  - Screenshot: Page 7

- Under **Get started**, select **Single website or app** as the distribution type.
- Enter the distribution name: `s3-swh-01`.
  - Screenshot: Page 8

- Under **Specify origin**, select **Amazon S3** as the Origin type.
- Select the S3 static website endpoint as the origin.
- Keep the recommended origin and cache settings.
  - Screenshot: Page 9 (top)

- Under **Enable security**, select **Use monitor mode** for AWS WAF.
  - Screenshot: Page 9 (bottom)

- Review the configuration and click **Create distribution**.
  - Screenshot: Page 10 (top)

- Copy the CloudFront distribution domain name and open it in a web browser.
- Verify that the hosted website loads successfully.
  - Screenshot: Page 10 (bottom) and Page 11

### Step 3

Create an SNS topic with standard type and create a subscription with Email as endpoint and provide the email ID. Open a mail client, open the email received from AWS currently and click “confirm subscription” - and report as not spam option if available.

- Open **Amazon SNS → Topics** and click **Create topic**.
  - Screenshot: Page 12

- Under **Create topic → Details**:
  - Select **Standard** as the topic type.
  - Enter the topic name: `s3-swh-cf-alerts-01`.
  - Enter the display name: `s3-cloudfront-alerts-01`.
  - Click **Create topic**.
  - Screenshot: Page 13 (top)

- Open the created topic and navigate to the **Subscriptions** tab.
- Click **Create subscription**.
  - Screenshot: Page 13 (bottom)

- Under **Create subscription**:
  - Select **Email** as the Protocol.
  - Enter the email address as the Endpoint.
  - Click **Create subscription**.
  - Screenshot: Page 14 (top)

- Open the email received from AWS and click **Confirm subscription**.
- Verify that the subscription status is **Confirmed**.
  - Screenshot: Page 14 (bottom)

### Step 4

Create a Cloudwatch Alarm for the cloudfront - the metrics for cloudfront are available in us-east-1 AZ since Cloudfront is a global service, select requests as metrics, and provide statistics, period & threshold needed. Select the existing SNS topic, provide a name and create the Alarm. Now create a Cloudwatch dashboard for the Cloudfront metrics.

- Open **CloudWatch → Alarms** and click **Create alarm**.
  - Screenshot: Page 14 (CloudWatch section)

- Under **Specify metric and conditions**:
  - Select **Metrics** as the data source.
  - Select **Classic** as the alarm type.
  - Click **Select metric**.
  - Screenshot: Page 15 (top)

- Change the AWS console region to **US East (N. Virginia) – us-east-1**.
  - Screenshot: Page 15 (bottom)

- Under **Select metric**, navigate to **CloudFront → Per-Distribution Metrics**.
- Select **Requests** and click **Select metric**.
  - Screenshots: Pages 16–17

- Under **Metric and Conditions**, configure:
  - Statistic: **Sum**
  - Period: **5 minutes**
  - Threshold type: **Static**
  - Whenever Requests is: **Greater**
  - Threshold value: **0**
  - Screenshot: Page 18

- Under **Configure actions**:
  - Select **In alarm** as the alarm state trigger.
  - Select the existing SNS topic: `s3-swh-cf-alerts-01`.
  - Screenshot: Page 19 (top)

- Under **Add alarm details**:
  - Enter the alarm name: `s3-cloudfront-swh-Alarm-01`.
  - Enter a description if required.
  - Screenshot: Page 19 (bottom)

- Review the configuration and click **Create alarm**.
- Verify that the alarm appears under CloudWatch Alarms.
  - Screenshot: Page 20

- Navigate to **CloudWatch → Dashboards**.
- Open the dashboard `SWH-Cloudfront-01`.
- Add a widget for the CloudFront **Requests** metric and save the dashboard.
  - Screenshot: Page 21

- Verify the CloudWatch alarm notification received through email.
  - Screenshot: Page 22
