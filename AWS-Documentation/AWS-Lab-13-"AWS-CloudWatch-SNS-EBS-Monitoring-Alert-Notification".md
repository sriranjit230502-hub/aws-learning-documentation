# AWS CloudWatch SNS EBS Monitoring Alert Notification

### Step 1

Create an instance, SSH into it from the local machine terminal. Install `stress` from apt repository.

<img width="1920" height="1080" alt="CW-SNS-A-01a-ec2-cw-sns-ec2-0808-ssh" src="https://github.com/user-attachments/assets/bd2c0f4d-a9cc-4322-be7b-5bd54c616dae" />


### Step 2

Log into the AWS Console. Navigate to CloudWatch -> Dashboards. Create a dashboard `ec2-ebs-utilization`. Next, click “Create Widget”.

<img width="1359" height="413" alt="CW-SNS-A-02a-click-createDashboard" src="https://github.com/user-attachments/assets/0b7c05d2-85a7-49a2-8442-1deba7d8534d" />

<img width="738" height="384" alt="CW-SNS-A-02b-dshboard-name-click-createDashboard" src="https://github.com/user-attachments/assets/f12a9aa9-3e3f-48a5-8e24-de9020380bc4" />

<img width="1121" height="452" alt="CW-SNS-A-03a-addWidget" src="https://github.com/user-attachments/assets/605cf03a-dfc9-421d-bd43-bc04ee4fba66" />


### Step 3

Choose Metrics as Data type, Metrics Console as preferred experience, Line as Widget type and click next.

<img width="750" height="715" alt="CW-SNS-A-03b-metrics-line" src="https://github.com/user-attachments/assets/6ab03a70-c9a9-48eb-87f6-b85bda3cc294" />


### Step 4

Under Add Metric graph in Browse, navigate to EC2 -> Per-instance Metrics -> select EBSWriteBytes under created instance. Click “Create Widget”. The widget is created and click “save”.

<img width="1026" height="789" alt="CW-SNS-A-03c-Browse-EC2-PerInstanceMetrics-EBSWriteBytes-creWidget" src="https://github.com/user-attachments/assets/ce08b562-a121-443e-992b-a649e66f059a" />

<img width="1117" height="362" alt="CW-SNS-A-03d-save-widgetDashboard" src="https://github.com/user-attachments/assets/abc7ce1c-6b4a-4d05-9a19-1e873f6538df" />


### Step 5

Navigate to Alarms through the sidebar, click “Create alarm”. Under Specify metric and conditions select Metrics as Data source, Classic as Type and click next. Then under Select Metric in browse, select the instance created and metric type, click “Select Metric”.

<img width="1121" height="414" alt="CW-SNS-A-04a-createAlarm" src="https://github.com/user-attachments/assets/01e9e537-84f3-4cab-aeb4-4a145fcceb95" />

<img width="1123" height="546" alt="CW-SNS-A-04b-metrics-next" src="https://github.com/user-attachments/assets/07f05687-fc88-49d8-bfb3-f2b0d9fe97c1" />

<img width="1022" height="774" alt="CW-SNS-A-04c-select-metric" src="https://github.com/user-attachments/assets/adbb256e-7fcd-44fb-823d-a7053279f976" />


### Step 6

Under Configure actions select In alarms as Alarm state trigger, then select Create new Topic. Name the topic `CloudWatch-EBS-Alarm-0808` and personal email as endpoint. Click “Create Topic”. Topic is created in SNS and click “Create Subscription”.

<img width="1096" height="507" alt="CW-SNS-A-04d-topic-createTOPIC" src="https://github.com/user-attachments/assets/d7a39a0c-c6d1-43d9-8318-9f913d13e464" />

<img width="1126" height="393" alt="CW-SNS-A-05a-createSubscription" src="https://github.com/user-attachments/assets/92fec298-e600-4642-a5e4-5b0023553be3" />


### Step 7

Under Create Subscription select Email as Protocol and personal email ad endpoint. Click “Create Subscription”. Now open a mail client in the local machine and navigate to spam. An email is received from AWS, click Report as not spam and click confirm subscription. AWS SNS “Subscription confirmation” is confirmed by a confirmation message in a browser tab.

<img width="1106" height="533" alt="CW-SNS-A-05b-email-createSub" src="https://github.com/user-attachments/assets/0b2c2ef8-c0af-406a-8cff-1b544436c252" />

<img width="1117" height="637" alt="CW-SNS-A-04e-gmail-spam-reportNotAsSpam" src="https://github.com/user-attachments/assets/eb2c72ca-822a-4b3f-90af-a35d5d07a560" />

<img width="1128" height="1001" alt="CW-SNS-A-05c-gmail-confirmSub" src="https://github.com/user-attachments/assets/c89cdaab-e91c-4c17-8ab8-91a1e1b4ad9a" />

<img width="1128" height="1001" alt="CW-SNS-A-05d-gmail-confirmed" src="https://github.com/user-attachments/assets/f7083ce3-d61b-49dd-a3e0-c649398b4998" />


### Step 8

Back to Alarms, under Add alarm details add an alarm name `EBSWriteBytes Alert` and an alarm description. Click next. Review and click “Create Alarm”. Thus Alarm created.

<img width="1125" height="597" alt="CW-SNS-A-04f-AlarmDetails" src="https://github.com/user-attachments/assets/4aba22a4-fc38-4ef9-b2bc-c1b06bf5ee47" />

<img width="1127" height="390" alt="CW-SNS-A-04g-created-Alarm" src="https://github.com/user-attachments/assets/7c495143-619d-4f88-968e-4f6508f39315" />


### Step 9

Now, in terminal SSH into instance, run:

```bash
stress –hdd 2 –timeout 60s
```

Due to sudden high stress in the instance volume, an email is received instantly from AWS SNS alerting high EBSWriteBytes.

<img width="1920" height="1080" alt="CW-SNS-A-01b-ec2-ssh-stress-gmai-alrt" src="https://github.com/user-attachments/assets/72344bfe-cc35-458f-b7fb-7e4ff975d79f" />

