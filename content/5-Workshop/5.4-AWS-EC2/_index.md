---
title : "Deploy Backend (AWS EC2)"
date : 2026-07-04
weight : 4
chapter : false
pre : " <b> 5.4. </b> "
---

### Deploying the Backend on Amazon EC2

In this section, we deploy the Node.js/Express backend to **Amazon EC2** so it can serve API requests for the frontend. The EC2 instance is placed in a public subnet for easier administration, while the database remains in private subnets for better security.

EC2 is a good fit for this project because:

* **Full control over the environment**: easy to install Node.js, Prisma, PM2, and project dependencies
* **Low cost**: `t2.micro` or `t3.micro` can be used within Free Tier limits
* **Easy integration**: the backend can connect privately to RDS and sit behind API Gateway for HTTPS access

![EC2 launched successfully](/images/5-Workshop/5.4-AWS-EC2/z8007993502305_c977416dc91cb6dd7fa401b0e8741e0e.jpg)

#### Contents

1. [Launch EC2 Instance](5.4.1-launch-ec2/)
2. [Install the Environment and Prepare the Backend](5.4.2-install-env/)