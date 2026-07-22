---
title : "Quản lý Người dùng & Xác thực qua AuthController"
date : 2026-07-20
weight : 3
chapter : false
pre : " <b> 5.4.3. </b> "
---

#### Phân tích Các APIs trong `AuthController.java`

Mã nguồn tại `gearstore-backend/src/main/java/com/gearstore/backend/controller/AuthController.java` quản lý tài khoản người dùng trên bảng DynamoDB `GearStore_Users`:

#### 1. API Đăng nhập (`POST /auth/login`)

```java
@PostMapping("/login")
public ResponseEntity<?> login(@RequestBody Map<String, String> request) {
    String username = request.get("username");
    String password = request.get("password");

    UserEntity user = userRepository.getUser(username);
    if (user == null || !user.getPassword().equals(password)) {
        return ResponseEntity.status(401).body("Tài khoản hoặc mật khẩu không chính xác!");
    }

    return ResponseEntity.ok(Map.of(
        "username", user.getUsername(),
        "fullName", user.getFullName(),
        "role", user.getRole(),
        "email", user.getEmail(),
        "phone", user.getPhone() != null ? user.getPhone() : "",
        "address", user.getAddress() != null ? user.getAddress() : ""
    ));
}
```

#### 2. API Đăng ký (`POST /auth/register`)

```java
@PostMapping("/register")
public ResponseEntity<?> register(@RequestBody UserEntity newUser) {
    UserEntity existing = userRepository.getUser(newUser.getUsername());
    if (existing != null) {
        return ResponseEntity.badRequest().body("Tên đăng nhập đã tồn tại!");
    }
    newUser.setRole("USER");
    userRepository.saveUser(newUser);
    return ResponseEntity.ok("Đăng ký tài khoản thành công!");
}
```

#### 3. APIs Quản trị Người dùng (`GET /auth/users` & `PUT /auth/users/update`)

Cho phép Quản trị viên (Admin) xem toàn bộ danh sách khách hàng và cập nhật quyền (`role`), họ tên, địa chỉ, số điện thoại.
