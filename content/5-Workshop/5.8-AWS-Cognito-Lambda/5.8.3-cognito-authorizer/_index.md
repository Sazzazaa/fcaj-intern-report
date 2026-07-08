---
title : "Secure API Gateway with a Cognito Authorizer"
date : 2026-07-07
weight : 3
chapter : false
pre : " <b> 5.8.3. </b> "
---

### Require users to sign in before calling the API

The frontend already attaches a `Bearer token` to requests through `fetchAuthSession()` in `client/src/state/api.ts`. That means we can use a **Cognito JWT Authorizer** in API Gateway to protect backend routes.

#### 1. Create the JWT Authorizer

In the API Gateway HTTP API:

1. Open **Authorization**.
2. Create a new **JWT authorizer**.
3. Enter:

* **Issuer**: the Cognito User Pool issuer URL, for example:

```text
https://cognito-idp.us-east-2.amazonaws.com/us-east-2_7KWEBP8Ci
```

* **Audience**: the App Client ID, for example:

```text
45qj7u3s4el2ggvjec6oqnfq6d
```

#### 2. Attach the authorizer to routes

You can attach the authorizer to:

* the `$default` route, or
* specific routes such as `/projects`, `/tasks`, `/users`, `/teams`, and `/search`

After the change, redeploy the `$default` stage.

#### 3. Why the frontend works immediately

In `client/src/state/api.ts`, before each request, the frontend already:

1. reads the current Cognito session
2. extracts the `accessToken`
3. sends:

```text
Authorization: Bearer <token>
```

So after a successful sign-in, requests to API Gateway automatically include a valid token.

#### 4. Expected result

* Authenticated users can use the application normally
* Requests with no token or an invalid token are rejected by API Gateway
* Pages such as Home, Priority, Users, and Teams work fully only when the Cognito session is valid