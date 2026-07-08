---
title : "Initialize the Cognito User Pool"
date : 2026-07-07
weight : 1
chapter : false
pre : " <b> 5.8.1. </b> "
---

### Create the User Pool for the application

#### 1. Create a new User Pool

Open **Amazon Cognito** and create a new **User Pool** for the application. After it is created, the Overview page shows:

* **User Pool ID**
* **OpenID Connect configuration URL**
* the active Region

![User pool overview](/images/5-Workshop/5.8-AWS-Cognito-Lambda/z8015062966503_5df85de2a59a22275ab7faf01bb041b2.jpg)

#### 2. Create the App Client for the frontend

Because the frontend is a single-page application, create a dedicated **App client** and record:

* **User Pool ID**: for example `us-east-2_7KWEBP8Ci`
* **Client ID**: for example `45qj7u3s4el2ggvjec6oqnfq6d`

![App client](/images/5-Workshop/5.8-AWS-Cognito-Lambda/z8015063019491_486c54ff7f6487dfb12f9bd1e4d9a1fc.jpg)

#### 3. Update frontend environment variables

In `client/.env.local` or Amplify environment variables:

```bash
NEXT_PUBLIC_COGNITO_USER_POOL_ID=us-east-2_7KWEBP8Ci
NEXT_PUBLIC_COGNITO_USER_POOL_CLIENT_ID=45qj7u3s4el2ggvjec6oqnfq6d
```

The file `client/src/app/authProvider.tsx` uses these values to configure Amplify Authenticator.

#### 4. Verify the sign-up flow

When a new user signs up, Cognito sends a verification email.

![Email verification](/images/5-Workshop/5.8-AWS-Cognito-Lambda/z8015064830628_12dc6c0e7aaef99d2bfc59ad2fe1ad3a.jpg)

After the verification code is entered, the user appears in the **Users** list of the User Pool.

![Cognito users list](/images/5-Workshop/5.8-AWS-Cognito-Lambda/z8015068340177_570aaa9ef9b914783f16a38cb7562492.jpg)