---
title : "Deploy the Frontend to Amplify"
date : 2026-07-07
weight : 1
chapter : false
pre : " <b> 5.6.1. </b> "
---

### Deploy the Next.js application with AWS Amplify

The frontend is located in the `client/` directory and already includes an `amplify.yml` file for automated builds.

#### 1. Connect the repository

1. Open **AWS Amplify**.
2. Choose **Host web app** or **Create app**.
3. Connect your GitHub account.
4. Select the repository `Sazzazaa/project-management-aws` and the `main` branch.

#### 2. Check the build file

The project uses this `amplify.yml` configuration:

```yml
version: 1
applications:
  - appRoot: client
    frontend:
      phases:
        preBuild:
          commands:
            - npm ci
        build:
          commands:
            - npm run build
```

This ensures Amplify builds the correct frontend directory.

#### 3. Set environment variables

In Amplify, add the same environment variables used locally:

```bash
NEXT_PUBLIC_API_BASE_URL=https://30o8modynj.execute-api.us-east-2.amazonaws.com
NEXT_PUBLIC_S3_BUCKET_NAME=project-management-images-aws
NEXT_PUBLIC_AWS_REGION=us-east-2
NEXT_PUBLIC_COGNITO_USER_POOL_ID=us-east-2_7KWEBP8Ci
NEXT_PUBLIC_COGNITO_USER_POOL_CLIENT_ID=45qj7u3s4el2ggvjec6oqnfq6d
```

#### 4. Deploy and verify the status

After the build finishes, Amplify provides a public URL for the application.

![Amplify overview](/images/5-Workshop/5.6-Frontend-Routing/z8018624951197_552794d116a7747abbb6451cac611889.jpg)

#### 5. Verify the deployed UI

When visiting the deployed URL, the Dashboard page loads correctly with charts and task data.

![Dashboard home](/images/5-Workshop/5.6-Frontend-Routing/z8015064749679_f863e1da662ef87d8fe7e782dccbd205.jpg)

Other routes, such as the Priority page, also work correctly.

![Priority page](/images/5-Workshop/5.6-Frontend-Routing/z8018816674221_4ba98393e460b77ee8591a7c240df558.jpg)