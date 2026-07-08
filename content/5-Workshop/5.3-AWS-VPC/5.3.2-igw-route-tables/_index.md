---
title : "Configure Internet Gateway & Route Tables"
date : 2026-07-04 
weight : 2
chapter : false
pre : " <b> 5.3.2. </b> "
---

#### 1. Create and Attach an Internet Gateway (IGW)

An Internet Gateway allows resources within the Public Subnet (EC2 server) to communicate with the Internet.

**Step 1:** In the left navigation pane of the VPC Console, select **Internet Gateways** -> **Create internet gateway**.
![IGW](/images/5-Workshop/5.3-AWS-VPC/igw.png)

**Step 2:** Enter `pm_internet-gateway` for the **Name tag** and click **Create internet gateway**.
![Create IGW](/images/5-Workshop/5.3-AWS-VPC/create-gateway.png)

**Step 3:** Once created, the IGW will be in a *Detached* state. Click the **Actions** button -> **Attach to VPC**.
![attach button](/images/5-Workshop/5.3-AWS-VPC/attach-to-vpc.png)

**Step 4:** Select `pm_vpc` from the list and click **Attach internet gateway**.

![Attach IGW](/images/5-Workshop/5.3-AWS-VPC/attach-igw.png)
---

#### 2. Create Route Tables

We need separate Route Tables to ensure that the Private Subnets do not have a route to the Internet.

**Step 1:** Select **Route Tables** in the left navigation pane -> **Create route table**.
![route table button](/images/5-Workshop/5.3-AWS-VPC/create-route-table-button.png)

**Step 2:** Create 3 Route Tables one by one and associate them all with `pm_vpc`:
* `pm_public-route-table-1`    
* `pm_private-route-table-1`
* `pm_private-route-table-2`
![create route table 1](/images/5-Workshop/5.3-AWS-VPC/create-route-table-button.png)

---

#### 3. Configure Public Routing & Associate Subnets

**Step 1:** Configure Internet routing for the Public Route Table:
* Select `pm_public-route-table-1` from the list.
* Switch to the **Routes** tab at the bottom half of the screen -> Select **Edit routes**.
   * ![Select edit](/images/5-Workshop/5.3-AWS-VPC/select-edit-route-table.png)

* Click **Add route**. Enter Destination: `0.0.0.0/0`. Under Target, select **Internet Gateway** and point it to `pm_internet-gateway`.
* Click **Save changes**.

* ![Edit public route table](/images/5-Workshop/5.3-AWS-VPC/edit-route-table.png)
*(Note: Screenshot of the operation adding the 0.0.0.0/0 route pointing to the IGW, equivalent to the 07:41:15 mark)*

**Step 2:** Associate Subnets with their corresponding Route Tables:
* **Public RT:** Select `pm_public-route-table-1` -> **Subnet associations** tab -> **Edit subnet associations** -> Check `pm_public-subnet-1` -> Save.
* ![edit subnet button](/images/5-Workshop/5.3-AWS-VPC/button-edit-subnet.png)

* **Private RT 1:** Select `pm_private-route-table-1` -> **Subnet associations** tab -> Check `pm_private-subnet-1` -> Save.
* **Private RT 2:** Select `pm_private-route-table-2` -> **Subnet associations** tab -> Check `pm_private-subnet-2` -> Save.
* ![edit subnet](/images/5-Workshop/5.3-AWS-VPC/edit-subnet.png)

---

#### 4. Test & Validation

* In the **Route Tables** list, check the **Routes** tab for `pm_private-route-table-1` and `pm_private-route-table-2`.
* **Expected Result:** These Private Route Tables **DO NOT** have a route pointing to `0.0.0.0/0` (only the `local` route exists). This confirms that our database has been securely isolated from the public Internet.
* ![check route](/images/5-Workshop/5.3-AWS-VPC/check-route.png)