---
title : "Launch EC2 Instance"
date : 2026-07-04
weight : 1
chapter : false
pre : " <b> 5.4.1. </b> "
---

### Create an EC2 instance for the backend

In this step, we create an EC2 instance to run the Node.js backend. Use the **same Region as the VPC and RDS resources** created earlier. In this workshop, the screenshots use **us-east-2 (Ohio)**.

#### 1. Open the EC2 Console

1. Sign in to the AWS Management Console.
2. Search for `EC2`.
3. Open **Instances** and click **Launch instance**.

![Access EC2](/images/5-Workshop/5.4-AWS-EC2/access-ec2.png)

#### 2. Configure the instance

Use a configuration similar to:

* **Name**: `project-management-api`
* **Amazon Machine Image**: Amazon Linux 2023
* **Instance type**: `t2.micro` or `t3.micro`

![Config EC2 OS](/images/5-Workshop/5.4-AWS-EC2/config-os.png)

#### 3. Create a key pair

1. In **Key pair (login)**, choose **Create new key pair**.
2. Enter a name such as `pm-key`.
3. Choose the `.pem` format.
4. Download the file and keep it in a safe place for SSH access.

![Create Key Pair](/images/5-Workshop/5.4-AWS-EC2/create-key-pair.png)

#### 4. Configure networking and the Security Group

1. In **Network settings**, click **Edit**.
2. Select the VPC created in section 5.3.
3. Select a **public subnet**.
4. Enable **Auto-assign public IP**.
5. Create a Security Group named `pm-ec2-sg`.

Recommended rules:

* **SSH (22)**: allow only your IP
* **Custom TCP (8000)**: for the backend API
* **HTTP (80)**: optional for quick testing or reverse proxy setup

![Config Security Group](/images/5-Workshop/5.4-AWS-EC2/config-sg.png)

#### 5. Launch the instance

1. Review the **Summary** section.
2. Click **Launch instance**.
3. Wait for the instance to reach **Running** status.

![Launch Summary](/images/5-Workshop/5.4-AWS-EC2/launch-summary.png)

#### 6. Actual result

After the instance is created successfully, AWS displays the new instance ID and a success message.

![EC2 launch success](/images/5-Workshop/5.4-AWS-EC2/z8007993502305_c977416dc91cb6dd7fa401b0e8741e0e.jpg)