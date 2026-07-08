---
title : "Configure the RDS Security Group"
date : 2026-07-04
weight : 2
chapter : false
pre : " <b> 5.5.2. </b> "
---

### Allow EC2 to connect to RDS

To let the backend access PostgreSQL, we only need to allow the **EC2 Security Group** to reach the **RDS Security Group** on port `5432`.

#### 1. Check the Security Groups in use

In the Security Groups list, verify that you have:

* `pm-ec2-sg`: used by the backend EC2 instance
* `pm-rds-sg`: used by the RDS database

![Security groups](/images/5-Workshop/5.5-AWS-RDS/z8007929031359_78ceac77af5643bd71396e152859972c.jpg)

#### 2. Add an inbound rule to `pm-rds-sg`

Open the `pm-rds-sg` Security Group and add:

* **Type**: PostgreSQL
* **Protocol**: TCP
* **Port range**: `5432`
* **Source**: Security Group `pm-ec2-sg`

This ensures:

* the database is **not publicly exposed**
* only the backend inside the VPC can reach it

#### 3. Verify the outbound rule of EC2

The default outbound rule of `pm-ec2-sg` usually allows all traffic. If you restricted outbound access, make sure EC2 is still allowed to connect to the private RDS endpoint on port `5432`.

#### 4. Real verification

In the next step, we will validate the setup by running:

* `npx prisma generate`
* `npx prisma migrate deploy`
* `npm run seed`

If those commands succeed, the network path between EC2 and RDS is configured correctly.