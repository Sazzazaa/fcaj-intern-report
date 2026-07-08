---
title : "Create RDS PostgreSQL"
date : 2026-07-04
weight : 1
chapter : false
pre : " <b> 5.5.1. </b> "
---

### Create a PostgreSQL database on Amazon RDS

#### 1. Open the RDS console

1. Search for `RDS` in the AWS Console.
2. Open **Databases**.
3. Click **Create database**.

#### 2. Configure the database

Use a configuration similar to:

* **Engine type**: PostgreSQL
* **Template**: Free tier
* **DB instance identifier**: `project-management-db`
* **Master username**: for example `postgres`
* **DB instance class**: `db.t3.micro` or a Free Tier equivalent
* **Initial database name**: `project_management_aws`

#### 3. Configure networking

In the **Connectivity** section:

* Select the same **VPC** used by EC2
* Place the DB in **private subnets**
* Set **Public access** to `No`
* Create or select the Security Group `pm-rds-sg`
* Keep the **Database port** as `5432`

#### 4. Wait for the database to be created

After clicking **Create database**, the initial status will be **Creating**.

![RDS creating](/images/5-Workshop/5.5-AWS-RDS/z8007964995120_4ae5126884b8b2c034b6aae6e646f5b3.jpg)

Once completed, the status changes to **Available**.

![RDS available](/images/5-Workshop/5.5-AWS-RDS/z8007996839089_2b855aa77f72204f2e7ff7d3ca5e659b.jpg)

#### 5. Save the endpoint

Open the database details page and copy the **endpoint**. It will be used in the `.env` file on EC2:

```bash
DATABASE_URL="postgresql://<db-username>:<db-password>@<rds-endpoint>:5432/project_management_aws?schema=public"
```