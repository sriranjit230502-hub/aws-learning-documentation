# AWS LAMBDA & EVENTBRIDGE

### Step 1

Create an S3 bucket `lmbd-s3-050926` with empty. Navigate to Lambda > functions > functions and click create function. Name the function and choose the runtime as Python 3.14, then click create function.

### Step 2

Then in code, paste the given python code and click deploy. Then click “Add trigger”, inside it choose S3 and the bucket we created, acknowledge it and click “add trigger”. Go to S3 bucket and add an object - a text file.

### Step 3

Check the monitor in Lambda, CloudWatch logs and click log stream link, which will redirect to CloudWatch and the logs specific to Lambda connected to S3 bucket. Look for logs àbout the text file upload.

## Eventbridge

### Step 4

In the S3 bucket, enable Amazon Eventbridge and navigate to EventBridge and click create rule.

### Step 5

Before completing next step create another lambda function with another given python code and deploy it.

Under Eventbridge Step 1, provide name and description, and click next.  
At the bottom, choose “custom pattern (JSON editor)” and paste the given JSON config for our S3 bucket. Click next.

Choose “Aws service” as target type and select the lambda function created and click next, until “review and create”.

### Step 6

Navigate to the lambda function created for Eventbridge and add trigger with Eventbridge as source. Then, again upload a text file first and check whether the logs have been updated. As per rule created, logs must be updated. And then upload a jpg file and check whether the logs have been updated. As per rule created, logs must not update for non TXT format files in that S3 bucket.
