# README: Using AWS S3 and CloudFront for Storing and Distributing Site Build Files

This README provides a step-by-step guide on how to utilize AWS S3 (Simple Storage Service) and CloudFront to store and distribute build files of a website. By following these instructions, you will be able to leverage the scalability, reliability, and low-latency content delivery capabilities of AWS for hosting your site's assets.

## Source Code & Demo Link:

- Live web-app link: https://d4uz6yawv2i8a.cloudfront.net/
- Source code of above deployed web-app: https://github.com/abhishek-simform-v1/REACT-PRACTICAL-5

## Prerequisites

Before proceeding with the steps below, ensure that you have the following prerequisites:

- An AWS account (https://aws.amazon.com/)
- The AWS Command Line Interface (CLI) installed and configured on your local machine (https://aws.amazon.com/cli/)

## Step 1: Set up an S3 Bucket

1. Log in to the AWS Management Console.
2. Navigate to the S3 service.
3. Click on "Create bucket" and provide a unique name for your bucket. Make sure to choose a region close to your target audience for optimal performance.
4. Leave the default settings as-is or customize them as per your requirements.
5. Create the bucket.
   ![bucket](/assets/s3bucketList.png)

## Step 2: Upload Build Files to S3 Bucket

1. Access the newly created S3 bucket in the AWS Management Console.
2. Click on "Upload" or "Add files" to select the build files from your local machine.
3. Follow the on-screen instructions to upload the files to the bucket.
   ![bucket](/assets/s3bucket.png)

## Step 3: Configure Bucket Permissions

1. Select the bucket in the AWS Management Console.
2. Navigate to the "Permissions" tab.
3. Click on "Bucket Policy" and add the following policy, replacing `my-first-bucket-for-aws
` with the name of your bucket:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": ["s3:GetObject"],
      "Resource": ["arn:aws:s3:::my-first-bucket-for-aws
/*"]
    }
  ]
}
```

This policy grants public read access to all objects within the bucket.

## Step 5: Create a CloudFront Distribution

1. Navigate to the CloudFront service in the AWS Management Console.
2. Click on "Create Distribution."
3. Under the "Web" section, select "Get Started."
4. In the "Origin Settings," choose the S3 bucket you created as the "Origin Domain Name."
5. Leave other settings as default or modify them as desired.
6. Click on "Create Distribution" to create the CloudFront distribution. This process may take a few minutes.
   ![bucket](/assets/cloudFrontList.png)

## Step 7: Update DNS or CNAME Record (optional)

If you wish to associate a custom domain name with your CloudFront distribution, follow these steps:

1. Obtain a domain name from a domain registrar (e.g., example.com).
2. In your DNS management console, create a CNAME record pointing to the Cloud
