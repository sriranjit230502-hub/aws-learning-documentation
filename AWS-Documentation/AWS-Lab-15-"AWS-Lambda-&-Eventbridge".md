# AWS LAMBDA & EVENTBRIDGE

### Step 1

Create an S3 bucket `lmbd-s3-050926` with empty. Navigate to Lambda > functions > functions and click create function. Name the function and choose the runtime as Python 3.14, then click create function.

<img width="1048" height="353" alt="A-lmdba-01-s3" src="https://github.com/user-attachments/assets/2cd91600-587b-4263-9fc0-3b57c5566464" />

<img width="1042" height="153" alt="A-lmbda-02-create-fnc" src="https://github.com/user-attachments/assets/e584fce6-6898-45dd-afbf-d35f05d27b07" />

<img width="1044" height="590" alt="A-lmbda-03-s3-demo-py314" src="https://github.com/user-attachments/assets/c8ff5ee0-3da2-48f7-a43b-1f1a688f0c19" />


### Step 2

Then in code, paste the given python code and click deploy. Then click “Add trigger”, inside it choose S3 and the bucket we created, acknowledge it and click “add trigger”. Go to S3 bucket and add an object - a text file.

<img width="1031" height="848" alt="A-lmdba-04-replacePY-deploy" src="https://github.com/user-attachments/assets/eefdb282-0033-497e-8295-7b7aac1d2adb" />

<img width="1047" height="608" alt="A-lmdba-05-addS3-trigger" src="https://github.com/user-attachments/assets/7e188b1b-e048-4b53-9cc6-a6476ed41248" />

<img width="1043" height="284" alt="A-lmdba-06-s3txt" src="https://github.com/user-attachments/assets/a6003064-84e7-4972-8e8e-d846e15f3d77" />


### Step 3

Check the monitor in Lambda, CloudWatch logs and click log stream link, which will redirect to CloudWatch and the logs specific to Lambda connected to S3 bucket. Look for logs àbout the text file upload.

<img width="1038" height="486" alt="A-lmdba-07-cwatchLog" src="https://github.com/user-attachments/assets/c43cf5a8-159c-41b7-9595-3ea40effc8ad" />


## Eventbridge

### Step 4

In the S3 bucket, enable Amazon Eventbridge and navigate to EventBridge and click create rule.

<img width="1028" height="371" alt="B-evntbrdg-01A-s3-prop-evntbrdg" src="https://github.com/user-attachments/assets/d8818888-7cf7-490d-a52e-ba65899675ef" />

<img width="1048" height="230" alt="B-evntbrdg-01B-s3-prop-evntbrdg" src="https://github.com/user-attachments/assets/eb860829-239b-4096-b467-6537beecd0b0" />

<img width="1054" height="1038" alt="B-evntbrdg-02-create-rule" src="https://github.com/user-attachments/assets/b1289780-50c7-431d-8fc9-a240a54f2eb6" />


### Step 5

Before completing next step create another lambda function with another given python code and deploy it.

Under Eventbridge Step 1, provide name and description, and click next.  
At the bottom, choose “custom pattern (JSON editor)” and paste the given JSON config for our S3 bucket. Click next.

Choose “Aws service” as target type and select the lambda function created and click next, until “review and create”.

<img width="851" height="330" alt="B-evntbrdg-03-name" src="https://github.com/user-attachments/assets/9c6d659d-d1ce-4d80-bbd5-a886bc19bc87" />

<img width="820" height="811" alt="B-evntbrdg-04-json-evnt-pttrn" src="https://github.com/user-attachments/assets/da9f8f0e-9b43-4b96-9cdf-a3f96e7b65c0" />

<img width="809" height="759" alt="B-evntbrdg-05-select-targets-lmbdfunc2" src="https://github.com/user-attachments/assets/02638598-92a2-4481-a15d-23ec9b26abd5" />

<img width="1054" height="1038" alt="B-evntbrdg-06-rev cre" src="https://github.com/user-attachments/assets/af006ec1-f289-4d34-9603-5301db05a88c" />


### Step 6

Navigate to the lambda function created for Eventbridge and add trigger with Eventbridge as source. Then, again upload a text file first and check whether the logs have been updated. As per rule created, logs must be updated. And then upload a jpg file and check whether the logs have been updated. As per rule created, logs must not update for non TXT format files in that S3 bucket.

<img width="1054" height="1038" alt="B-evntbrdg-07-lmbda-trigger-evntbrdg" src="https://github.com/user-attachments/assets/49e65a17-482a-4646-bd81-808d06ffb877" />

<img width="1026" height="275" alt="B-evntbrdg-08-s3-text-upload" src="https://github.com/user-attachments/assets/8fc3f87a-745c-4bda-9de1-61d54360c13d" />

<img width="1054" height="1038" alt="B-evntbrdg-09-Cwatch" src="https://github.com/user-attachments/assets/e9fbc7b5-ef19-481a-98ed-78fc245e6979" />

<img width="1038" height="471" alt="B-evntbrdg-09-S3-JPG-upload" src="https://github.com/user-attachments/assets/b1315b95-32cc-4978-b339-60418e5fffdf" />

<img width="1186" height="928" alt="Screenshot from 2026-09-10 18-30-26" src="https://github.com/user-attachments/assets/4f3fe2b3-3221-4fea-88a2-57a84849b58e" />
