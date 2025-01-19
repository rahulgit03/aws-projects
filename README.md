# aws-projects
AWS S3 Static Website Deployment (Free Tier)

Project Overview

This repository documents my step-by-step process for deploying a static website using AWS S3 and IAM. It serves as a backup of my work and a reference for others who want to follow the same process.

Tech Stack Used

AWS S3 (Static Website Hosting)

AWS IAM (Permissions and Access Control)

GitHub (Version Control and Documentation)

Steps to Deploy a Static Website on AWS S3

1. Creating an S3 Bucket

Sign in to AWS Free Tier: AWS Console.

Open the S3 service.

Click Create bucket and enter a unique bucket name (e.g., my-static-website).

Choose a region closest to your audience.

Uncheck Block all public access (since this is a public website).

Acknowledge the warning and click Create bucket.

2. Uploading Website Files

Open your newly created S3 bucket.

Click Upload and add your index.html, styles.css, script.js, and any other static files.

Make files public by adjusting permissions for each file (or configuring bucket policies).

3. Enabling Static Website Hosting

Open your S3 bucket and go to the Properties tab.

Scroll down to Static website hosting and click Edit.

Select Enable.

Set the Index document as index.html.

Click Save changes.

Copy the Bucket Website Endpoint (this is your website URL).

4. Configuring IAM Permissions (Make Website Public)

Open your S3 bucket and navigate to the Permissions tab.

Click Bucket Policy and add the following policy:

{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::my-static-website/*"
    }
  ]
}

Replace my-static-website with your actual bucket name.

Click Save.

5. Testing and Verifying Deployment

Open the Bucket Website Endpoint in a browser.

Verify that the website loads correctly.

Check for missing files, permission issues, or incorrect URLs.

Common Challenges & Solutions

1. Website Not Loading (403 Forbidden Error)

Ensure public access is enabled in S3 settings.

Check if the Bucket Policy allows public access.

Verify that index.html is correctly set as the default document.

2. CSS or JavaScript Not Loading

Ensure each file is set to public access.

Double-check the file paths in index.html.

3. S3 Website URL Returns XML Error

Ensure that Static Website Hosting is enabled under the Properties tab.
