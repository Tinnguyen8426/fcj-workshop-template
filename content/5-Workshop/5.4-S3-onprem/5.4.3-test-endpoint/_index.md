---
title : "User Management & Authentication via AuthController"
date : 2026-07-20
weight : 3
chapter : false
pre : " <b> 5.4.3. </b> "
---

#### Analyzing Endpoints in `AuthController.java`

The source code at `gearstore-backend/src/main/java/com/gearstore/backend/controller/AuthController.java` executes user account management against DynamoDB table `GearStore_Users`:

#### 1. Login Endpoint (`POST /auth/login`)

```java
@PostMapping("/login")
public ResponseEntity<?> login(@RequestBody Map<String, String> request) {
    String username = request.get("username");
    String password = request.get("password");

    UserEntity user = userRepository.getUser(username);
    if (user == null || !user.getPassword().equals(password)) {
        return ResponseEntity.status(401).body("Invalid credentials!");
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

#### 2. Registration Endpoint (`POST /auth/register`)

```java
@PostMapping("/register")
public ResponseEntity<?> register(@RequestBody UserEntity newUser) {
    UserEntity existing = userRepository.getUser(newUser.getUsername());
    if (existing != null) {
        return ResponseEntity.badRequest().body("Username already exists!");
    }
    newUser.setRole("USER");
    userRepository.saveUser(newUser);
    return ResponseEntity.ok("User registered successfully!");
}
```

#### 3. User Administration APIs (`GET /auth/users` & `PUT /auth/users/update`)

Allows Administrators to retrieve customer accounts and update user roles, phone numbers, and addresses.
