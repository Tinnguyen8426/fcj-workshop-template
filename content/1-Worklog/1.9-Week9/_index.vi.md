---
title: "Worklog Tuần 9"
date: 2026-06-29
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

### Mục tiêu tuần 9:
* Tích hợp thư viện phụ thuộc trung gian `aws-serverless-java-container-springboot3` vào tập cấu hình `pom.xml` của dự án GearStore.
* Cấu hình loại bỏ Web Server nhúng (Embedded Tomcat Web Container) khỏi tệp đóng gói để chuyển sang chế độ khởi chạy Serverless Asynchronous In-Memory HTTP Adapter.
* Thiết lập môi trường chuyển đổi luồng dữ liệu mạng nội bộ của ứng dụng Spring Boot 3 từ HTTP TCP Sockets sang bộ nhớ RAM trực tiếp.
* Kiểm tra tính tương thích giữa Spring Boot 3.x Context và thư viện AWS Serverless Container Wrapper.

### Các công việc đã thực hiện:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Thêm dependency `com.amazonaws.serverless:aws-serverless-java-container-springboot3` vào tệp `pom.xml` của dự án.<br>- Kiểm tra phiên bản tương thích với Spring Boot 3.2.x và Jakarta Servlet 6.0 specs. | 30/06/2026   | 30/06/2026      | <https://cloudjourney.awsstudygroup.com/aws-serverless-java-container-integration/> |
| 3   | - Cấu hình loại bỏ phụ thuộc `spring-boot-starter-tomcat` bằng thẻ `<exclusions>` trong dependency `spring-boot-starter-web`.<br>- Phân tích lý do loại bỏ Tomcat: Tiết kiệm ~30-50MB RAM và cắt giảm thời gian khởi động Serverless container. | 01/07/2026   | 01/07/2026      | <https://cloudjourney.awsstudygroup.com/aws-serverless-java-container-integration/> |
| 4   | - Khám phá cơ chế hoạt động của `AwsProxyHttpServletRequestReader` và `AwsProxyHttpServletResponseWriter` trong việc tạo bộ đệm in-memory truyền trực tiếp byte stream.<br>- Đánh giá tốc độ truyền nhận request trong bộ nhớ RAM so với qua giao thức mạng HTTP socket nội bộ. | 02/07/2026   | 02/07/2026      | <https://cloudjourney.awsstudygroup.com/aws-serverless-java-container-integration/> |
| 5   | - Cấu hình thuộc tính Spring Profiles (`@Profile("lambda")`) để ứng dụng có thể linh hoạt chọn giữa chế độ chạy Serverless Lambda hoặc chạy Web Server truyền thống khi phát triển ở local. | 03/07/2026   | 03/07/2026      | <https://cloudjourney.awsstudygroup.com/springboot3-profiles/> |
| 6   | - Thực hiện biên dịch thử nghiệm lệnh `mvn clean compile`, sửa đổi các xung đột dependency phát sinh.<br>- Báo cáo kết quả tích hợp thư viện wrapper với nhóm và cập nhật tài liệu kỹ thuật dự án. | 04/07/2026   | 04/07/2026      | Tài liệu nội bộ dự án |

### Kết quả đạt được tuần 9:
* Tích hợp thành công thư viện `aws-serverless-java-container-springboot3` vào cấu hình Maven dự án GearStore.
* Tháo bỏ hoàn toàn Web Server Embedded Tomcat dư thừa, giảm đáng kể dung lượng bộ nhớ RAM tiêu thụ và tăng tốc thời gian khởi tạo Application Context.
* Thiết lập thành công môi trường Adapter chuyển đổi request in-memory, sẵn sàng cho việc lập trình lớp Handler cổng vào ở tuần 10.