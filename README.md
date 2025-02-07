# Host a Static Website on AWS S3

## Overview
This project demonstrates how to host a static website using Amazon Simple Storage Service (S3). Hosting a website on S3 provides high availability, scalability, and protection against data loss. This guide walks through setting up an S3 bucket, enabling static website hosting, configuring permissions, and using a custom domain with Route 53.

## Project Objectives
- Configure static website hosting on Amazon S3
- Set up a custom domain with Route 53
- Secure the website with appropriate bucket policies

## Prerequisites
- An active AWS account
- Basic knowledge of AWS S3 and Route 53
- A registered domain (preferably in Route 53)

## Steps to Host a Static Website on AWS

### Step 1: Logging Into AWS
- Sign in to your AWS account using your credentials.

### Step 2: Creating an Amazon S3 Bucket
1. Navigate to **S3** in the AWS Management Console.
2. Click **Create Bucket**.
3. Enter a unique bucket name (e.g., `my-static-website`).
4. Select a region (e.g., **US West (Oregon) us-west-2**).
5. Uncheck **Block all public access** to allow public access to website files.
6. Confirm settings and click **Create Bucket**.

### Enable Static Website Hosting
7. Click on your created bucket.
8. Go to the **Properties** tab and select **Static Website Hosting**.
9. Enable static website hosting and set:
   - **Index document:** `index.html`
   - **Error document:** `error.html`
10. Click **Save changes**.

### Step 3: Uploading Website Files to S3
11. Go to the **Objects** tab in your bucket.
12. Click **Upload** and add all website files (HTML, CSS, JS, etc.).
13. Click **Upload** to complete the process.

### Step 4: Setting a Bucket Policy
14. Navigate to **Permissions** > **Bucket Policy**.
15. Add the following policy (replace `YOUR_BUCKET_NAME` with your actual bucket name):
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::YOUR_BUCKET_NAME/*"
    }
  ]
}
```
16. Click **Save Changes**.

### Step 5: Setting Up Route 53 for a Custom Domain
17. Navigate to **AWS Route 53**.
18. Select your hosted zone and create an **A Record (Alias)** pointing to your S3 bucket endpoint.
19. Click **Save Record**.

### Step 6: Testing and Deployment
20. Copy the **S3 Static Website Endpoint** from the **Properties** tab.
21. Open a browser and access your website using the S3 endpoint.
22. Verify that the website loads correctly.

## Conclusion
You have successfully hosted a static website on AWS S3 and configured it with a custom domain using Route 53. This setup provides a scalable and cost-effective solution for hosting static websites.

## Next Steps
- Enable logging and monitoring via AWS CloudWatch.
- Secure your website further with IAM policies.
- Implement additional optimizations such as caching with a CDN if required.

