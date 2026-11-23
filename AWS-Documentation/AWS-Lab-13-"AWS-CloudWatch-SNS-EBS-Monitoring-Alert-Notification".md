# AWS CloudWatch SNS EBS Monitoring Alert Notification

### Step 1

Create an instance, SSH into it from the local machine terminal. Install `stress` from apt repository.

### Step 2

Log into the AWS Console. Navigate to CloudWatch -> Dashboards. Create a dashboard `ec2-ebs-utilization`. Next, click “Create Widget”.

### Step 3

Choose Metrics as Data type, Metrics Console as preferred experience, Line as Widget type and click next.

### Step 4

Under Add Metric graph in Browse, navigate to EC2 -> Per-instance Metrics -> select EBSWriteBytes under created instance. Click “Create Widget”. The widget is created and click “save”.

### Step 5

Navigate to Alarms through the sidebar, click “Create alarm”. Under Specify metric and conditions select Metrics as Data source, Classic as Type and click next. Then under Select Metric in browse, select the instance created and metric type, click “Select Metric”.

### Step 6

Under Configure actions select In alarms as Alarm state trigger, then select Create new Topic. Name the topic `CloudWatch-EBS-Alarm-0808` and personal email as endpoint. Click “Create Topic”. Topic is created in SNS and click “Create Subscription”.

### Step 7

Under Create Subscription select Email as Protocol and personal email ad endpoint. Click “Create Subscription”. Now open a mail client in the local machine and navigate to spam. An email is received from AWS, click Report as not spam and click confirm subscription. AWS SNS “Subscription confirmation” is confirmed by a confirmation message in a browser tab.

### Step 8

Back to Alarms, under Add alarm details add an alarm name `EBSWriteBytes Alert` and an alarm description. Click next. Review and click “Create Alarm”. Thus Alarm created.

### Step 9

Now, in terminal SSH into instance, run:

```bash
stress –hdd 2 –timeout 60s
```

Due to sudden high stress in the instance volume, an email is received instantly from AWS SNS alerting high EBSWriteBytes.
