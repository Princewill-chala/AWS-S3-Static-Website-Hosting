# AWS-S3-Static-Website-Hosting
End-to-end implementation of a static website hosted on AWS S3. Includes bucket creation, public access policy setup, static website hosting configuration, and security considerations.

# AWS S3 Static Website Hosting Project

## Project Overview

This project demonstrates how to host a static website using Amazon S3. The implementation includes creating an S3 bucket, configuring bucket permissions, enabling public access, and hosting a website through the S3 Static Website Hosting feature.

## Objective

The goal of this project was to:

- Create an Amazon S3 bucket
- Upload static website files
- Configure bucket permissions
- Enable public access
- Enable Static Website Hosting
- Make the website accessible through a public S3 endpoint

---

## Architecture

User Browser
      |
      v
Amazon S3 Bucket
      |
      v
Static Website Hosting Endpoint

---

## Prerequisites

Before starting, ensure you have:

- An AWS account
- IAM user with S3 permissions
- Static website files (HTML, CSS, JavaScript)

---

## Step 1: Create an S3 Bucket

1. Log in to the AWS Management Console.
2. Navigate to **Amazon S3**.
3. Click **Create bucket**.
4. Enter a globally unique bucket name.
5. Select your preferred AWS Region.
6. Leave default settings unless customization is required.
7. Click **Create bucket**.

### Screenshot

![Create Bucket](images/create-bucket.png)

---

## Step 2: Upload Website Files

1. Open the newly created bucket.
2. Click **Upload**.
3. Add website files:
   - index.html
   - style.css
   - script.js
4. Complete the upload process.

### Screenshot

![Upload Files](images/upload-files.png)

---

## Step 3: Disable Block Public Access

By default, S3 blocks public access to protect resources.

1. Navigate to:
   - Bucket
   - Permissions
   - Block Public Access
2. Click **Edit**.
3. Uncheck:

   - Block all public access

4. Acknowledge the warning.
5. Save changes.

### Screenshot

![Public Access](images/public-access.png)

---

## Step 4: Configure Bucket Policy

Attach a bucket policy to allow public read access.

Replace `YOUR-BUCKET-NAME` with your actual bucket name.

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadAccess",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::YOUR-BUCKET-NAME/*"
    }
  ]
}
```

### Screenshot

![Bucket Policy](images/bucket-policy.png)

---

## Step 5: Enable Static Website Hosting

1. Navigate to:
   - Bucket
   - Properties
2. Scroll to **Static website hosting**.
3. Click **Edit**.
4. Enable Static Website Hosting.
5. Specify:

   - Index document: `index.html`

6. Save changes.

### Screenshot

![Static Hosting](images/static-hosting.png)

---

## Step 6: Access the Website

After enabling Static Website Hosting, AWS generates a website endpoint.

Example:

```text
http://my-static-site.s3-website-us-east-1.amazonaws.com
```

Open the endpoint in a browser to verify the website is publicly accessible.

### Screenshot

![Website Live](images/website-live.png)

---

## Security Considerations

This project intentionally enables public access to host a public website.

For production environments:

- Use CloudFront for content delivery.
- Enable HTTPS.
- Restrict unnecessary permissions.
- Implement AWS WAF where appropriate.
- Follow the Principle of Least Privilege.

---

## Lessons Learned

During this project, I learned:

- How Amazon S3 stores and serves static content.
- How bucket policies control access.
- The relationship between Block Public Access settings and bucket policies.
- How Static Website Hosting works in AWS.
- Security implications of public S3 buckets.

---

## Future Improvements

- Integrate Amazon CloudFront
- Configure HTTPS with AWS Certificate Manager
- Register a custom domain using Route 53
- Implement CI/CD deployment pipeline

---

## Technologies Used

- Amazon S3
- AWS IAM
- HTML
- CSS
- JavaScript

---

## Author

**Princewill Chala**

Cloud Computing | Cybersecurity | Data Analysis

GitHub: https://github.com/YOUR_USERNAME
