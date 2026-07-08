---
title : "Install the Environment and Prepare the Backend"
date : 2026-07-06
weight : 2
chapter : false
pre : " <b> 5.4.2. </b> "
---

### Connect to EC2, install Node.js, and clone the repository

After the EC2 instance is running, connect to it and install the required runtime environment for the backend.

#### 1. SSH into the EC2 instance

From your local machine:

```bash
ssh -i "C:\Users\admin\Downloads\pm-key.pem" ec2-user@<public-dns-or-public-ip>
```

Then load the shell profile and use the correct Node version:

```bash
source ~/.bashrc
nvm use node
```

![SSH and install environment](/images/5-Workshop/5.4-AWS-EC2/z8014660664709_d852d8aca4a9c0b88cf677c434a0945a.jpg)

#### 2. Install dependencies and clone the repo

```bash
sudo yum update -y
sudo yum install git -y

git clone https://github.com/Sazzazaa/project-management-aws.git
cd ~/project-management-aws/server
npm install
```

If Node.js is not installed yet, use the NVM and Node setup steps shown in the screenshots below:

![Install Nodejs](/images/5-Workshop/5.4-AWS-EC2/install-nodejs.png)
![Install Nodejs 2](/images/5-Workshop/5.4-AWS-EC2/install-nodejs1.png)

#### 3. Prepare the `.env` file

At the beginning, you can create the file with `PORT`. After finishing the RDS section, come back and add `DATABASE_URL`.

```bash
cat > .env <<EOF
PORT=8000
DATABASE_URL="postgresql://<db-username>:<db-password>@<rds-endpoint>:5432/project_management_aws?schema=public"
EOF
```

![Config Env](/images/5-Workshop/5.4-AWS-EC2/config-env0.png)
![Config Env 2](/images/5-Workshop/5.4-AWS-EC2/config-env.png)

#### 4. Next step

At this point, EC2 is ready to connect to the database. In section **5.5 AWS RDS**, we will:

* create the PostgreSQL database on RDS
* configure the Security Group rule between `pm-ec2-sg` and `pm-rds-sg`
* run Prisma generate, migrations, and seed data from EC2