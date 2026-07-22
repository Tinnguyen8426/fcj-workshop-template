---
title: "Worklog Tuần 8"
date: 2026-06-22
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### Mục tiêu tuần 8:
* Khởi tạo cấu trúc dự án Spring Boot 3 (nền tảng Java 17/21, Jakarta EE 10) làm hạt nhân cốt lõi cho hệ thống thương mại điện tử GearStore.
* Thiết lập cấu trúc cây thư mục chuẩn Maven Monorepo / Multi-module dự án, phân tách rõ ràng các layer: Controller, Service, Repository, DTO và Entity.
* Cấu hình đồng bộ hóa toàn bộ các phiên bản Dependency (Spring Web, Spring Data JPA, Hibernate, Validation, Jackson) thông qua khối `<dependencyManagement>` trong `pom.xml`.
* Phân công nhiệm vụ và thống nhất quy chuẩn lập trình backend, quy trình Git Workflow với các thành viên trong nhóm.

### Các công việc đã thực hiện:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Khởi tạo dự án Spring Boot 3 bằng Spring Initializr với Java 17 runtime và bộ thư viện nền tảng: Spring Web, Spring Data JPA, PostgreSQL Driver, Validation, Lombok.<br>- Phân tích các điểm cải tiến của Spring Boot 3 dựa trên Jakarta EE 10 specification (`jakarta.persistence.*`, `jakarta.validation.*`). | 23/06/2026   | 23/06/2026      | <https://cloudjourney.awsstudygroup.com/springboot3-setup/> |
| 3   | - Thiết lập cấu trúc cây thư mục dự án GearStore theo tiêu chuẩn Clean Architecture / Layered Architecture.<br>- Khởi tạo các package chính: `com.gearstore.controller`, `com.gearstore.service`, `com.gearstore.repository`, `com.gearstore.entity`, `com.gearstore.dto`. | 24/06/2026   | 24/06/2026      | <https://cloudjourney.awsstudygroup.com/springboot3-architecture/> |
| 4   | - Xây dựng tệp `pom.xml` trung tâm, chuẩn hóa các phiên bản thư viện dependency.<br>- Đảm bảo tất cả các thành viên trong nhóm sử dụng chung phiên bản Spring Boot 3.2.x, Jakarta Servlet API 6.0 và Jackson Databind để tránh xung đột binary. | 25/06/2026   | 25/06/2026      | <https://cloudjourney.awsstudygroup.com/springboot3-setup/> |
| 5   | - Hiện thực hóa các lớp RESTful Controller mẫu (ProductController, CategoryController) với các annotation chuẩn `@RestController`, `@RequestMapping`, `@GetMapping`, `@PostMapping`.<br>- Kiểm tra chạy ứng dụng ở môi trường local Tomcat port `8080` bằng Swagger UI / Postman. | 26/06/2026   | 26/06/2026      | <https://cloudjourney.awsstudygroup.com/springboot3-rest-api/> |
| 6   | - Đưa dự án lên kho quản lý mã nguồn Git Repository chung của nhóm, thiết lập các chi nhánh (`main`, `develop`, `feature/*`).<br>- Thảo luận quy trình Code Review và họp tổng kết tiến độ tuần 8 với nhóm. | 27/06/2026   | 27/06/2026      | Tài liệu nội bộ dự án |

### Kết quả đạt được tuần 8:
* Khởi tạo thành công cấu trúc dự án Spring Boot 3 cốt lõi cho hệ thống GearStore trên nền tảng Java 17 và Jakarta EE 10.
* Chuẩn hóa cây thư mục dự án theo mô hình Layered Architecture chuyên nghiệp và dễ mở rộng.
* Đồng bộ hóa hoàn toàn tệp cấu hình Maven `pom.xml` và các phiên bản phụ thuộc cho tất cả thành viên trong nhóm phát triển.
* Xây dựng và kiểm thử thành công các API cơ bản chạy ổn định ở môi trường local.