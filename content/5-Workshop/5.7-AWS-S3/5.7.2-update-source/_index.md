---
title : "Update the Image URLs in Source Code"
date : 2026-07-06
weight : 2
chapter : false
pre : " <b> 5.7.2. </b> "
---

### Connect the frontend to the S3 bucket

In this project, image URLs are not hard-coded. Instead, the frontend builds them dynamically from environment variables.

#### 1. Update the environment variables

In your local environment or in Amplify, define:

```bash
NEXT_PUBLIC_S3_BUCKET_NAME=project-management-images-aws
NEXT_PUBLIC_AWS_REGION=us-east-2
```

#### 2. Verify the S3 URL helper

The file `client/src/lib/s3.ts` currently works like this:

```ts
const S3_BUCKET_NAME =
  process.env.NEXT_PUBLIC_S3_BUCKET_NAME ?? "project-management-images-aws";
const S3_REGION = process.env.NEXT_PUBLIC_AWS_REGION ?? "us-east-2";

export const S3_BASE_URL = `https://${S3_BUCKET_NAME}.s3.${S3_REGION}.amazonaws.com`;
```

Whenever a component needs to display an image, the project calls `getS3Url(key)` to generate the full URL.

#### 3. Allow Next.js to load images from S3

In `client/next.config.mjs`, the project already includes `remotePatterns` for the S3 domain. That lets Next.js `Image` render files directly from the AWS bucket.

#### 4. Redeploy the frontend

After changing environment variables or uploading additional objects, redeploy the frontend on Amplify so the UI can use the correct bucket and image keys.