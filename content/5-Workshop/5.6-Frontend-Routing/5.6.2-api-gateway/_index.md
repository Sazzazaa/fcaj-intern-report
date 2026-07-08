---
title : "Configure HTTPS with API Gateway"
date : 2026-07-06
weight : 2
chapter : false
pre : " <b> 5.6.2. </b> "
---

### Expose the EC2 backend through API Gateway

The frontend is deployed with HTTPS through Amplify, while the backend on EC2 is serving HTTP on port `8000`. If the browser calls EC2 directly, you may run into mixed-content issues. To solve this, place **HTTP API Gateway** in front of the backend.

#### 1. Inspect the backend request in the test environment

During testing, browser DevTools can be used to verify that the frontend is calling the EC2 backend.

![Network request EC2](/images/5-Workshop/5.6-Frontend-Routing/z8014760739864_e165daf9d210725e62aca43dc5f544c9.jpg)

The screenshot shows the `/projects` route responding from the backend running on EC2 port `8000`.

#### 2. Create the HTTP API

1. Open **API Gateway**.
2. Create a new **HTTP API**, for example `project-management-api`.
3. Create an **HTTP integration** pointing to:

```text
http://<ec2-public-host>:8000
```

4. Create the `$default` route with method `ANY`.

![API Gateway integration](/images/5-Workshop/5.6-Frontend-Routing/z8015055837944_bd126c4ebb6fb08a2c95b7c33d772a56.jpg)

#### 3. Deploy the default stage

In **Stages**, use `$default` and enable **Automatic deployment**.

![API Gateway stage](/images/5-Workshop/5.6-Frontend-Routing/z8014993693598_79208f8b6748fc2c042d562bc54d4683.jpg)

After that, AWS provides a public **Invoke URL**, such as:

```text
https://30o8modynj.execute-api.us-east-2.amazonaws.com
```

#### 4. Update the frontend

Set:

```bash
NEXT_PUBLIC_API_BASE_URL=https://30o8modynj.execute-api.us-east-2.amazonaws.com
```

Then redeploy the frontend on Amplify. From this point on, frontend API requests go through API Gateway before reaching the backend EC2 server.