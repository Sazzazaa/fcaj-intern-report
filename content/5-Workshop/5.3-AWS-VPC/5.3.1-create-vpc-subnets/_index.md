---
title : "Create the VPC and Subnets"
date : 2026-07-04
weight : 1
chapter : false
pre : " <b> 5.3.1. </b> "
---

#### 1. Create the Virtual Private Cloud (VPC)

**Step 1:** Sign in to the AWS Management Console. Search for `VPC` and open the VPC service. Make sure you are working in the correct Region for the workshop.

![Select VPC](/images/5-Workshop/5.3-AWS-VPC/select-vpc.png)

**Step 2:** In the left navigation pane, choose **Your VPCs**, then click **Create VPC**.

![Create VPC](/images/5-Workshop/5.3-AWS-VPC/create-vpc.png)

**Step 3:** In the configuration screen, enter values similar to the following:

* **Resources to create:** `VPC and more` or the workflow used in your AWS console
* **Name tag:** `pm-vpc`
* **IPv4 CIDR block:** `10.0.0.0/16`

![Select create VPC](/images/5-Workshop/5.3-AWS-VPC/select-create-vpc.png)

---

#### 2. Create the subnets

The project needs 3 subnets:

* 1 **public subnet** for EC2
* 2 **private subnets** in different Availability Zones for RDS

**Step 1:** Return to the left navigation pane, choose **Subnets**, then click **Create subnet**.

![Create subnet button](/images/5-Workshop/5.3-AWS-VPC/create-subnet-button.png)

**Step 2:** In **VPC ID**, select the `pm-vpc` you just created.

**Step 3:** Create the following subnets:

* **Subnet 1 (Public)**
  * **Subnet name:** `pm_public-subnet-1`
  * **Availability Zone:** `us-east-2a`
  * **IPv4 CIDR block:** `10.0.0.0/24`

* **Subnet 2 (Private 1)**
  * **Subnet name:** `pm_private-subnet-1`
  * **Availability Zone:** `us-east-2a`
  * **IPv4 CIDR block:** `10.0.1.0/24`

* **Subnet 3 (Private 2)**
  * **Subnet name:** `pm_private-subnet-2`
  * **Availability Zone:** `us-east-2b` a different AZ
  * **IPv4 CIDR block:** `10.0.2.0/24`

![Create subnet](/images/5-Workshop/5.3-AWS-VPC/create-subnet.png)

**Step 4:** Scroll to the bottom and click **Create subnet**.

After the workflow completes, AWS shows a confirmation screen indicating that the VPC, subnets, route tables, and internet gateway were created successfully.

![Create VPC workflow success](/images/5-Workshop/5.3-AWS-VPC/z8007889978504_abaf388742a623b682b46742d309f93a.jpg)

---

#### 3. Test and validation

* Open the **Subnets** page again.
* Filter by `VPC = pm-vpc`.
* **Expected result:** 3 subnets are displayed in **Available** status with the expected CIDR ranges and Availability Zones.

![3 Subnets](/images/5-Workshop/5.3-AWS-VPC/3-subnets.png)