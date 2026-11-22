
# AWS S3 Bucket Creation & Basic Functions

## Create an AWS S3 Bucket

### Step 1

Log in to the AWS Console and open S3. Navigate to General Purpose Buckets. Click “Create Bucket”.

 

### Step 2

Under Bucket namespaces, choose “Account Regional namespace”, name the bucket 3107-s3-gen-purp-bkt and select “ACLs enabled” & “Bucket owner preferred”.

### Step 3

Uncheck “Block all public access” and click the acknowledgement. Choose Bucket versioning “disable” and add a tag “Key: name” “Value: 3107-s3-gen-purp-bkt-051542582635-ap-south-2-an”

### Step 4

Select “SSE-S3” as default encryption type and choose Bucket Key is “Enable”. In Advanced settings, choose “Disable” under Object Lock. Click “Create Bucket”.

## Create an Object

### Step 5

Thus the bucket was successfully created. Click “Create Folder”.

### Step 6

Name the folder 3107-obj and select “Don’t specify an encryption key” under Server-side-encryption. Click “Create folder” and thus 3107-obj successfully created.

## Upload an Image File and View It Online

### Step 7

Click “upload”. Select an image from the local machine, choose “Private” under Predefined ACLs and click “upload’.

### Step 8

Select the file, click “open” and the image opens in new browser tab.

### Step 9

Click “Actions”, select “Make public using ACL” and click “copy URL” and paste in new browser tab. Image is viewed.

## Upload a Text File and View It Online

### Step 10

Create a .txt file s3_sample.txt contains text “hello aws”. Click “upload”.

### Step 11

Click “Open” and the text file appears as a webpage in the new browser tab.

### Step 12

Same as image file, make it public, copy its url and paste in a browser tab. The text file appears as a web page.

### Step 13

Edit the file’s content, from “hello aws” to “hi aws”. Upload the file again. The older version gets soft deleted and the new version gets uploaded. Click “open” to view the file as a web page.

## Create Another Bucket & an Object and Copy Files from Another Bucket

### Step 14

Click “Create bucket” and create another bucket named 3107-s3-bkt-02. After naming, click “choose bucket” and select the bucket 3107-s3-gen-purp-bkt created. And create an object 3107-obj-02 in 3107-s3-bkt-02.

### Step 15

Navigate to bucket 3107-s3-gen-purp-bkt and select the files uploaded. Click “Actions -> Copy”. Select the destination as s3/3107-s3-bkt-02/3107-obj-02 and click “Copy”.

Thus the files were copied successfully.
