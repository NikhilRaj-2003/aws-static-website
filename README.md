# Host Your Static Website on AWS S3 in Minutes (No Server Needed)

This guide explains how to quickly host a static website using Amazon S3 without needing a web server.

**Original article:** [Medium Post by Nikhil Siri](https://medium.com/@nikhilsiri2003/host-your-static-website-on-aws-s3-in-minutes-no-server-needed-8f13b1a83daf)

---

## Step 1: Create an S3 Bucket

<div align="center">
  <img src="images/create-s3-bucket.png" alt="Create S3 Bucket" width="600" />
  <p><em>Screenshot: Creating a new S3 bucket in AWS Console</em></p>
</div>

- Log in to AWS Management Console.
- Go to **S3 service**.
- Click **Create bucket**.
- Enter bucket name and region.
- Keep other defaults or configure as needed.
- Click **Create bucket**.

---

## Step 2: Upload Your Website Files

<div align="center">
  <img src="images/upload-files-s3.png" alt="Upload files to S3" width="600" />
  <p><em>Screenshot: Uploading static website files to the S3 bucket</em></p>
</div>

- Open your S3 bucket.
- Click **Upload**.
- Select your website files (e.g., `index.html`, CSS, images).
- Click **Upload**.

---

## Step 3: Configure Bucket for Static Website Hosting

<div align="center">
  <img src="images/s3-static-website-hosting.png" alt="Static website hosting config" width="600" />
  <p><em>Screenshot: Enabling static website hosting on S3 bucket</em></p>
</div>

- In bucket properties, scroll to **Static website hosting**.
- Select **Enable**.
- Specify **index document** (e.g., `index.html`).
- Save changes.

---

## Step 4: Make Your Bucket Content Public

- Go to **Permissions** tab.
- Edit **Bucket Policy** and add a policy to allow public read access:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::your-bucket-name/*"
    }
  ]
}

## Step 4: Enable Static Website Hosting on the S3 Bucket

Under the **Properties** tab of your S3 bucket, scroll to the bottom and locate **Static Website Hosting**.  
Click on **Edit** to enable static web hosting.

<div align="center">
  <img src="images/s3-static-website-hosting-edit.png" alt="Edit Static Website Hosting" width="600" />
  <p><em>Screenshot: Edit Static Website Hosting option</em></p>
</div>

---

## Step 5: Configure Static Web Hosting

- Enable **Static Website Hosting**.
- Provide the **Index Document** as `index.html` so that the S3 bucket knows which file to load by default.
- After enabling, AWS will generate a **Bucket Website Endpoint URL**.

<div align="center">
  <img src="images/s3-enable-static-hosting.png" alt="Enable Static Website Hosting" width="600" />
  <p><em>Screenshot: Enable static website hosting and set index document</em></p>
</div>

---

## What is the S3 Bucket Website Endpoint URL?

When you enable Static Website Hosting on an Amazon S3 bucket, AWS generates a special URL called the **S3 website endpoint**.  
This is the **public URL** where your static website becomes accessible.

It looks like this:


