---
title: "Worklog Tuần 6"
date: 2026-06-08
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Mục tiêu tuần 6:
* Nghiên cứu tài liệu mã nguồn mở của dự án AWS Serverless Java Container (`aws-serverless-java-container`).
* Tìm hiểu cơ chế cấu hình và ánh xạ luồng dữ liệu (Request/Response mapping) giữa một Web Framework truyền thống (Spring Boot) sang môi trường thực thi Serverless Lambda.
* Khám phá thiết kế mẫu Adapter Pattern giúp chuyển đổi các `AwsProxyRequest` / `AwsProxyResponse` từ API Gateway / ALB thành `HttpServletRequest` / `HttpServletResponse` chuẩn Java Servlet API.
* Đánh giá giải pháp chạy ứng dụng Web trên Lambda mà không cần sửa đổi cấu trúc Controller hay Business Logic hiện có.

### Các công việc đã thực hiện:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Nghiên cứu kho mã nguồn mở `aws-serverless-java-container` trên GitHub và tài liệu hướng dẫn tích hợp của AWS.<br>- Phân tích bài toán thách thức: Làm thế nào để ứng dụng Spring Boot vốn thiết kế chạy trên Web Server (Tomcat/Jetty) có thể nhận request từ AWS Lambda. | 09/06/2026   | 09/06/2026      | <https://cloudjourney.awsstudygroup.com/aws-serverless-java-container/> |
| 3   | - Nghiên cứu mô hình kiến trúc Adapter Pattern áp dụng trong thư viện `aws-serverless-java-container`.<br>- Phân tích cách thức adapter tiếp nhận sự kiện JSON (`AwsProxyRequest`) gửi từ API Gateway, tạo ra đối tượng giả lập `AwsProxyHttpServletRequest` tuân thủ Servlet API spec. | 10/06/2026   | 10/06/2026      | <https://cloudjourney.awsstudygroup.com/aws-serverless-java-container/> |
| 4   | - Tìm hiểu quy trình xử lý phản hồi ngược: Sau khi Spring Boot Controller trả về dữ liệu, adapter thu gom `HttpServletResponse` và đóng gói thành đối tượng `AwsProxyResponse` nhị phân để trả về cho API Gateway. | 11/06/2026   | 11/06/2026      | <https://cloudjourney.awsstudygroup.com/aws-serverless-java-container/> |
| 5   | - Đánh giá ưu và nhược điểm của việc nạp toàn bộ Spring Boot Application Context vào Lambda Execution Environment so với việc viết các hàm Micro-function đơn lẻ.<br>- Phân tích lợi ích duy trì toàn bộ kiến trúc RESTful Controllers, Security Filter Chain và Dependency Injection. | 12/06/2026   | 12/06/2026      | <https://cloudjourney.awsstudygroup.com/serverless-springboot-architecture/> |
| 6   | - Tổng hợp sơ đồ luồng dữ liệu (Sequence Diagram) từ API Gateway qua Adapter đến Spring Boot Controller.<br>- Báo cáo kết quả nghiên cứu lý thuyết với cán bộ hướng dẫn và nhóm làm dự án. | 13/06/2026   | 13/06/2026      | Tài liệu nội bộ dự án |

### Kết quả đạt được tuần 6:
* Hiểu rõ cơ chế hoạt động của khung giải pháp mã nguồn mở AWS Serverless Java Container.
* Nắm vững nguyên lý ánh xạ dữ liệu (Request/Response mapping) và cách thức Adapter Pattern tương thích giữa AWS Lambda Event format và Java Servlet API.
* Định hình được phương án kiến trúc chuyển đổi ứng dụng Spring Boot 3 sang môi trường Serverless mà giữ nguyên 100% cấu hình Controllers và Business Logic.