---
title : "Connecting Next.js Frontend with Backend APIs"
date : 2026-07-20
weight : 5
chapter : false
pre : " <b> 5.5. </b> "
---

#### 1. Configuring Frontend Environment (`.env.local`)

Connect your Next.js web app to the deployed API Gateway endpoint:

```env
NEXT_PUBLIC_API_URL=https://xxxxxx.execute-api.us-east-1.amazonaws.com
```

#### 2. Fetching Product Catalogue (`GET /products`)

Frontend integration code for displaying gaming equipment:

```typescript
export async function fetchProducts() {
  const res = await fetch(`${process.env.NEXT_PUBLIC_API_URL}/products`);
  if (!res.ok) throw new Error("Failed to load products!");
  return res.json();
}
```

#### 3. Authentication Integration (`POST /auth/login` & `POST /auth/register`)

```typescript
export async function loginUser(username: string, password: string) {
  const res = await fetch(`${process.env.NEXT_PUBLIC_API_URL}/auth/login`, {
    method: "POST",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify({ username, password }),
  });
  if (!res.ok) {
    const errorText = await res.text();
    throw new Error(errorText);
  }
  return res.json();
}
```

#### 4. Triggering Async Database Seed (`POST /products/reset-database`)

Admin users can trigger **"Seed Database (110 Products)"** directly from the admin panel to populate S3 and DynamoDB asynchronously.
