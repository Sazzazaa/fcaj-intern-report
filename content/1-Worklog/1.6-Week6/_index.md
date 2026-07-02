---
title: "Week 6 Worklog"
date: 2026-06-14
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Week 6 Objectives:
* Deploy core APIs on the Node.js/Express Backend.
* Initialize the Amazon VPC network infrastructure with a full set of subnets.
* Deploy Amazon RDS PostgreSQL in a secure network area (Private Subnet).

### Tasks to be implemented this week:
| Day | Task | Start Date | Completion Date | Reference |
| :--- | :--- | :--- | :--- | :--- |
| Mon | - **Backend Task:** Install Express, configure CORS, Helmet, and Morgan logging.<br>- Write Controllers to handle GET/POST logic for `projects` and `tasks`. | 08/06/2026 | 08/06/2026 | |
| Tue | - **Infra Task:** Create a custom **Amazon VPC** with a CIDR Block network range.<br>- Create 1 Public Subnet (for EC2) and 2 Private Subnets (for RDS) in different AZs. | 09/06/2026 | 09/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| Wed | - **Infra Task:** Set up an **Internet Gateway (IGW)** and attach it to the VPC.<br>- Configure **Route Tables**: Grant internet access permissions for the Public Subnet. | 10/06/2026 | 10/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| Thu | - **Infra Task:** Initialize an **Amazon RDS (PostgreSQL)** Free Tier instance placed in the Private Subnet.<br>- Configure the Security Group to allow connections on port 5432. | 11/06/2026 | 11/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| Fri | - Hold a team meeting to update progress and test GET/POST Project APIs via Postman on Local. | 12/06/2026 | 12/06/2026 | |

### Week 6 Achievements:
* Finished programming the core API endpoints for the Backend.
* Successfully deployed a secure VPC network architecture with distinct Subnet layers.
* Successfully initialized a PostgreSQL database on Amazon RDS, ensuring the Database is isolated from the Internet.