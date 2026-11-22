# AWS S3 Static Webhosting + CloudFront

## Static WebHosting

### Step 1
Open a S3 Bucket. Upload an `index.html` file while granting public access.

<img width="842" height="635" alt="SWH-01-obj-upload-indexHtml" src="https://github.com/user-attachments/assets/f50edf84-ff8e-4745-979a-92367b1edf83" />


### Step 2
After uploading the file, switch to properties.

<img width="1015" height="299" alt="SWH-02-bucket-prop" src="https://github.com/user-attachments/assets/4838993f-22df-4bf7-9b36-98564b8d5759" />


### Step 3
Move to end of the page, to Static website hosting. Click “edit”.

<img width="995" height="134" alt="SWH-03-swh-edit" src="https://github.com/user-attachments/assets/1d0095d5-4d5a-4fc8-907d-28b9be78ca5a" />


### Step 4
Enable the “Static website hosting” and type `index.html` in index document section. Click “save changes”.

<img width="839" height="653" alt="SWH-04-swh-enable-indexHtml-save" src="https://github.com/user-attachments/assets/d0c37c55-ca25-4923-9c4b-0cc49397262a" />


### Step 5
Copy the URL of the “bucket website endpoint". Paste it in the browser.

<img width="1002" height="239" alt="SWH-05-copy-paste" src="https://github.com/user-attachments/assets/6a531894-cfed-4eca-bd95-177ab02bbfb6" />


### Step 6
Thus the website `index.html` file is hosted in s3 bucket using static web hosting.

<img width="1037" height="1001" alt="SWH-06-website-hosted" src="https://github.com/user-attachments/assets/50e555d5-2358-4d19-b5e7-1e11e57c2252" />


---

## CloudFront

### Step 7
Navigate to CloudFront -> Distribution -> Click “Create Distribution”.

<img width="1025" height="257" alt="CF-01-click-createDistribution" src="https://github.com/user-attachments/assets/c52aef32-65b1-4b65-8e37-588b854c7258" />


### Step 8
Name the Distribution, `0308-clf-swh-s3`. Give a description and click “next”.

<img width="1037" height="1001" alt="CF-02-name-next" src="https://github.com/user-attachments/assets/8f6ab83d-5808-4984-92c6-943f57a73e9b" />


### Step 9
Select “Amazon S3” under Origin Type, click “Browse s3” choose the s3 bucket where the website is hosted. Then click “Next”.

<img width="842" height="617" alt="CF-03-originType-bucket-next" src="https://github.com/user-attachments/assets/a3633a51-1b37-423f-9905-c0026b598c5a" />


### Step 10
Click “Next”.

<img width="1021" height="435" alt="CF-04-waf-next" src="https://github.com/user-attachments/assets/f221bfc5-ed16-4966-980a-1ea8803fc1c7" />


### Step 11
Review and click “Create Distribution”. Thus `0308-clf-swh-s3` is created.


<img width="1037" height="1001" alt="CF-05-review click-createDistribution" src="https://github.com/user-attachments/assets/724364e5-0982-4d77-8d33-9dbaef9ba72b" />

<img width="1014" height="155" alt="CF-06-distribution-created" src="https://github.com/user-attachments/assets/a90f51c9-bc86-4375-a492-01b4206f490e" />


