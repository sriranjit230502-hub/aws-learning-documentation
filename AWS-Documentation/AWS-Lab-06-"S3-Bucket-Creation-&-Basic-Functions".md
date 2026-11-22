
# AWS S3 Bucket Creation & Basic Functions

## Create an AWS S3 Bucket

### Step 1

Log in to the AWS Console and open S3. Navigate to General Purpose Buckets. Click “Create Bucket”.

<img width="1439" height="1001" alt="S3-A-01-navigate-cre-buck" src="https://github.com/user-attachments/assets/b44b9bd7-26d5-4ffe-976c-c377a6a15ec5" />


### Step 2

Under Bucket namespaces, choose “Account Regional namespace”, name the bucket 3107-s3-gen-purp-bkt and select “ACLs enabled” & “Bucket owner preferred”.

<img width="1439" height="1001" alt="S3-A-02-genConf-objOwn" src="https://github.com/user-attachments/assets/866c2ff7-e3ab-4383-8e39-073efb1e50be" />


### Step 3

Uncheck “Block all public access” and click the acknowledgement. Choose Bucket versioning “disable” and add a tag “Key: name” “Value: 3107-s3-gen-purp-bkt-051542582635-ap-south-2-an”

<img width="1439" height="1001" alt="S3-A-03-access-BktVer-Tags" src="https://github.com/user-attachments/assets/d5768f2e-cc83-4b71-bb6b-948c6f57989e" />


### Step 4

Select “SSE-S3” as default encryption type and choose Bucket Key is “Enable”. In Advanced settings, choose “Disable” under Object Lock. Click “Create Bucket”.

<img width="1231" height="576" alt="S3-A-04-encrpt-bktKey-objLock-createBucket" src="https://github.com/user-attachments/assets/f660dd39-a524-46aa-a93e-a9da468a608b" />


## Create an Object

### Step 5

Thus the bucket was successfully created. Click “Create Folder”.

<img width="1345" height="357" alt="S3-B-01-click-createFolder" src="https://github.com/user-attachments/assets/835ed466-765d-41ed-8a42-c172004fe418" />


### Step 6

Name the folder 3107-obj and select “Don’t specify an encryption key” under Server-side-encryption. Click “Create folder” and thus 3107-obj successfully created.

<img width="1353" height="638" alt="S3-B-02-dirName-encKey-createFolder" src="https://github.com/user-attachments/assets/5ef41d7f-df12-4d30-a360-af28e02c83de" />

<img width="1333" height="363" alt="S3-B-03-objCreated" src="https://github.com/user-attachments/assets/41048c9e-800b-4aa8-a682-cb5bc5872ba5" />



## Upload an Image File and View It Online

### Step 7

Click “upload”. Select an image from the local machine, choose “Private” under Predefined ACLs and click “upload’.

<img width="1342" height="365" alt="S3-C-01-clickUpload" src="https://github.com/user-attachments/assets/f3ef517a-f9b4-40ae-8d54-79db20e31b3c" />

<img width="1439" height="1001" alt="S3-C-02-selFile-priv-upload" src="https://github.com/user-attachments/assets/3f21e1f6-5f48-432a-bffe-d97ec0554123" />


### Step 8

Select the file, click “open” and the image opens in new browser tab.

<img width="1355" height="300" alt="S3-C-03A-fileUploaded-ClickOpen" src="https://github.com/user-attachments/assets/f0b05d98-1663-4d46-abcf-29726ad65bc7" />

<img width="1439" height="1001" alt="S3-C-03B-ClickOpen-OpndBrowser" src="https://github.com/user-attachments/assets/00ee085a-b368-4c80-b8af-97c511a28278" />



### Step 9

Click “Actions”, select “Make public using ACL” and click “copy URL” and paste in new browser tab. Image is viewed.

<img width="1343" height="477" alt="S3-C-04A-actions-pubACL" src="https://github.com/user-attachments/assets/5cdd20e8-2e93-430c-8b44-c817e2869458" />

<img width="1280" height="273" alt="S3-C-04B-copyURL" src="https://github.com/user-attachments/assets/d721281f-e024-46ab-bece-f3c6a55cb9e7" />

<img width="1439" height="1001" alt="S3-C-04C-OpenedBrowser" src="https://github.com/user-attachments/assets/65058de3-dd91-4f63-8570-ba5f13149509" />


## Upload a Text File and View It Online

### Step 10

Create a .txt file s3_sample.txt contains text “hello aws”. Click “upload”.

<img width="1268" height="278" alt="S3-D-01-uploadFile02" src="https://github.com/user-attachments/assets/30e9e43c-1e17-461b-b899-884d4a73fcbc" />

<img width="1920" height="1080" alt="S3-D-02-txtFile-upload" src="https://github.com/user-attachments/assets/60116e1b-9b79-4018-ab85-b213186e1126" />



### Step 11

Click “Open” and the text file appears as a webpage in the new browser tab.

<img width="1018" height="320" alt="S3-D-03A-File2uploadd-clickOpen" src="https://github.com/user-attachments/assets/d033812c-7a82-49b3-a158-6c7a111faf21" />

<img width="1049" height="1045" alt="S3-D-03B-BrowserFile02" src="https://github.com/user-attachments/assets/e71684d6-1183-458b-95c9-a29b965db083" />



### Step 12

Same as image file, make it public, copy its url and paste in a browser tab. The text file appears as a web page.

<img width="1026" height="433" alt="S3-D-04A-file2-actions-pubACL" src="https://github.com/user-attachments/assets/9832328b-94c4-4582-9a36-f4149f47963b" />

<img width="1032" height="322" alt="S3-D-04B-File2-copyURL" src="https://github.com/user-attachments/assets/71b849a3-1b85-49eb-b37c-1ef690f257f1" />

<img width="1049" height="1045" alt="S3-D-04C-File2-OpenedBrowser" src="https://github.com/user-attachments/assets/b0b92400-1b12-4ecb-aac6-e064a8cba955" />




### Step 13

Edit the file’s content, from “hello aws” to “hi aws”. Upload the file again. The older version gets soft deleted and the new version gets uploaded. Click “open” to view the file as a web page.

<img width="1920" height="1080" alt="S3-D-05A-file02-ver02-upload" src="https://github.com/user-attachments/assets/762faa0a-a876-49b0-99aa-f8edf295f9f4" />

<img width="1012" height="325" alt="S3-D-05B-file2ver2uploaded-clickOpen" src="https://github.com/user-attachments/assets/58752035-34e0-4654-8be0-dafa0a6960a7" />





## Create Another Bucket & an Object and Copy Files from Another Bucket

### Step 14

Click “Create bucket” and create another bucket named 3107-s3-bkt-02. After naming, click “choose bucket” and select the bucket 3107-s3-gen-purp-bkt created. And create an object 3107-obj-02 in 3107-s3-bkt-02.

<img width="1049" height="1045" alt="S3-E-01-clickCreateBucket-new" src="https://github.com/user-attachments/assets/ea1c99af-1f18-4f11-b3ff-5347d2ca0d98" />

<img width="1049" height="1045" alt="S3-E-02-3107-s3-bkt-02-create-chooseBucket" src="https://github.com/user-attachments/assets/9fc72a97-059c-4047-b2cf-a8f4afdbf06b" />

<img width="1041" height="317" alt="S3-E-03-3107-obj-02-created" src="https://github.com/user-attachments/assets/39588992-4977-4d6b-ba19-a93b571c89d1" />


### Step 15

Navigate to bucket 3107-s3-gen-purp-bkt and select the files uploaded. Click “Actions -> Copy”. Select the destination as s3/3107-s3-bkt-02/3107-obj-02 and click “Copy”.

<img width="1049" height="1045" alt="S3-F-01-copyFiles1 2" src="https://github.com/user-attachments/assets/b57d7aee-330e-447d-9c2e-d6c5af988f9c" />

<img width="1049" height="1045" alt="S3-F-02-sel-destin-clickCopy" src="https://github.com/user-attachments/assets/693ec780-13d3-4236-9d10-fb8f0e492b88" />

Thus the files were copied successfully.

<img width="1049" height="1045" alt="S3-F-03-success-copied-to-3107-obj-02" src="https://github.com/user-attachments/assets/4b309e55-585e-41d2-80fe-ba00552f35af" />

