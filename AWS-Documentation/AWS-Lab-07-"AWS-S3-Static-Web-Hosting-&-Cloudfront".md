# AWS S3 Static Webhosting + CloudFront

## Static WebHosting

### Step 1
Open a S3 Bucket. Upload an `index.html` file while granting public access.

### Step 2
After uploading the file, switch to properties.

### Step 3
Move to end of the page, to Static website hosting. Click “edit”.

### Step 4
Enable the “Static website hosting” and type `index.html` in index document section. Click “save changes”.

### Step 5
Copy the URL of the “bucket website endpoint". Paste it in the browser.

### Step 6
Thus the website `index.html` file is hosted in s3 bucket using static web hosting.

---

## CloudFront

### Step 7
Navigate to CloudFront -> Distribution -> Click “Create Distribution”.

### Step 8
Name the Distribution, `0308-clf-swh-s3`. Give a description and click “next”.

### Step 9
Select “Amazon S3” under Origin Type, click “Browse s3” choose the s3 bucket where the website is hosted. Then click “Next”.

### Step 10
Click “Next”.

### Step 11
Review and click “Create Distribution”. Thus `0308-clf-swh-s3` is created.
