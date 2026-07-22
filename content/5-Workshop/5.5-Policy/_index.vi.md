---
title : "Tích hợp Frontend Next.js với Backend APIs"
date : 2026-07-20
weight : 5
chapter : false
pre : " <b> 5.5. </b> "
---

#### 1. Khai báo Biến Môi trường Frontend (`.env.local`)

Kết nối ứng dụng Next.js với URL API Gateway Endpoint vừa được deploy từ Spring Boot backend:

```env
NEXT_PUBLIC_API_URL=https://xxxxxx.execute-api.us-east-1.amazonaws.com
```

#### 2. Kết nối Danh sách Sản phẩm (`GET /products`)

Mã nguồn frontend gọi API để hiển thị catalogue sản phẩm:

```typescript
// Fetch toàn bộ sản phẩm
export async function fetchProducts() {
  const res = await fetch(`${process.env.NEXT_PUBLIC_API_URL}/products`);
  if (!res.ok) throw new Error("Lỗi tải danh sách sản phẩm!");
  return res.json();
}
```

#### 3. Kết nối Đăng nhập & Đăng ký (`POST /auth/login` & `POST /auth/register`)

```typescript
// Gọi API Đăng nhập
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

#### 4. Kích hoạt Seed Database từ Giao diện Admin (`POST /products/reset-database`)

Admin có thể nhấp nút **"Seed Database (110 Products)"** trên giao diện để kích hoạt API khởi tạo ngầm mà không làm treo UI.
