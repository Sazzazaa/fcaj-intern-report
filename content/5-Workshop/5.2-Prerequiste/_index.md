---
title : "Prerequisites"
date : 2026-07-04 
weight : 2
chapter : false
pre : " <b> 5.2. </b> "
---

#### 1. AWS Account & Region Requirements

To complete this workshop, you need an active AWS account. It is recommended to use a newly created account to take advantage of the **AWS Free Tier** (12 months free for many core services such as EC2, RDS).

Throughout this Lab, to minimize latency and ensure consistency, we will select a single Region:
* **Region Name:** `ap-southeast-1`
* **Region Location:** Singapore

![AWS Region Selection](/images/5-Workshop/5.2-Prerequisite/aws-region.png)


---

#### 2. IAM Permissions

To provision services (VPC, EC2, RDS, Cognito, Amplify...), the IAM User account you are using to log in must have sufficient permissions. It is recommended to attach `AdministratorAccess` for the lab environment, or you can attach the following JSON inline-policy to your User:

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "ProjectManagementLabPermissions",
            "Effect": "Allow",
            "Action": [
                "ec2:*",
                "rds:*",
                "cognito-idp:*",
                "s3:*",
                "apigateway:*",
                "amplify:*",
                "lambda:*",
                "iam:PassRole",
                "iam:CreateRole",
                "iam:AttachRolePolicy",
                "iam:PutRolePolicy",
                "budgets:*"
            ],
            "Resource": "*"
        }
    ]
}
```

---

#### 3. AWS Budgets Setup (Zero Spend Budget)

This workshop is designed to be completely free ($0) if you stick to the Free Tier configurations. However, to manage cloud cost risks, creating a budget alert is mandatory.


**Step 1:** From the AWS Console interface, search for the **Billing and Cost Management** service.


**Step 2:** In the left navigation pane, select **Budgets** -> **Create budget**.

**Step 3:** Under *Budget setup*, choose **Use a template (simplified)**. In the *Templates* section, select **Zero spend budget**. 

**Step 4:** Enter your email address in the **Email recipients** field and click **Create budget**. The system will automatically alert you via email if the project costs begin to exceed `$0.01`.

![Zero Spend Budget Config](/images/5-Workshop/5.2-Prerequisite/zero-spend-budget.png)

---

#### 4. Project Source Code Preparation

Unlike automatic labs that use CloudFormation code, in this workshop, we will manually deploy the infrastructure from scratch. You need to push the application source code (including both frontend and backend) to your personal GitHub Repository to prepare for the subsequent upload and CI/CD process.


Open Terminal (or Git Bash) on your computer and run the following commands to set it up:

```bash
# Clone the original project repository
git clone [https://github.com/Sazzazaa/project-management-aws](https://github.com/Sazzazaa/project-management-aws)

# Navigate into the project directory
cd project-management

# Install dependencies for client and server
cd client && npm install
cd ../server && npm install

# Clean up old .gitignore and push to your own new Repository
rm -rf client/.git
rm -rf server/.git
git init
git add .
git commit -m "Initial commit for AWS Deployment"
git remote add origin <YOUR_GITHUB_REPO_LINK>
git push -u origin master
```

![GitHub Repository](/images/5-Workshop/5.2-Prerequisite/github-repo.png)