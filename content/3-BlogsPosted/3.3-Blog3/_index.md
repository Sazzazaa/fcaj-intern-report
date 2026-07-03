---
title: "Blog 3"
date: 2026-07-03
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

# PREVENTING DATA EXFILTRATION IN ML ENVIRONMENTS WITH AMAZON SAGEMAKER AI

This article shares a real-world case study from iBusiness on solving the sensitive data security challenge for data scientists. By implementing a 3-layer security architecture combined with Amazon SageMaker AI, this system completely prevents data exfiltration without the need for expensive VDI infrastructures.

Key takeaways:

* **Layer 1 - WorkSpaces Secure Browser:** Locks down the entry point using a managed browser environment, completely disabling upload/download, copy-paste, and direct printing functions from the client.
* **Layer 2 - URL Allowlisting & VPC Endpoints:** Restricts access to specific AWS domains and forces users to log into the correct organizational account via the internal network, blocking the risk of pushing data to personal accounts.
* **Layer 3 - Isolating the SageMaker environment:** Cuts off all Internet connections for the VPC hosting SageMaker. All interactions with other services (like S3) must go through VPC Endpoints with granular policies strictly managing API calls.
* **Operational cost savings:** Reduces development environment costs from over $40/user/month (VDI) to just $7/user/month.
* **Accelerated deployment:** Thanks to automation, the provisioning time for a new secure workspace is reduced from 2 days to just a few minutes.

![Blog 3](/images/3-BlogsPosted/blog-3.png)

[Blog link: Preventing data exfiltration in machine learning environments with Amazon SageMaker AI](https://www.facebook.com/groups/660548818043427)
