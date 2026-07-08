---
title : "Create the S3 Bucket and Configure Permissions"
date : 2026-07-06
weight : 1
chapter : false
pre : " <b> 5.7.1. </b> "
---

### Create an S3 bucket for application images

#### 1. Create a new bucket

1. Open **Amazon S3**.
2. Click **Create bucket**.
3. Enter a bucket name such as `project-management-images-aws`.
4. Select the same region used by the project, in this case `us-east-2`.

After the bucket is created successfully, it appears in the bucket list.

![S3 bucket created](/images/5-Workshop/5.7-AWS-S3/z8014903805881_ad0eece18580fb6b88234fd493898503.jpg)

#### 2. Upload objects to the bucket

Upload the files used by the UI, such as:

* `logo.png`
* user avatar images
* sample attachments

When you open the object details page, AWS shows the corresponding object URL.

![S3 object properties](/images/5-Workshop/5.7-AWS-S3/z8014913860501_46e832754f7daa970e9eb8d14be759d3.jpg)

#### 3. Configure read access

Because the frontend renders images directly from the object URL, allow public read access in a way that matches your bucket policy setup, for example:

* a bucket policy that allows `s3:GetObject`, or
* public read permissions for specific objects only

The end goal is that a URL in the form:

```text
https://project-management-images-aws.s3.us-east-2.amazonaws.com/<object-key>
```

can be accessed successfully by the frontend.