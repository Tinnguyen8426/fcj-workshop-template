---
title: "Nhật ký công việc"
date: 2026-05-04
weight: 1
chapter: false
pre: " <b> 1. </b> "
---

Chương này ghi chép chi tiết toàn bộ tiến trình làm việc, nghiên cứu lý thuyết chuyên sâu về kiến trúc điện toán đám mây (Cloud Computing), các bài thực hành chuyên đề và quá trình nghiên cứu, đóng gói, tối ưu hóa ứng dụng Spring Boot 3 chuyển đổi sang mô hình Serverless trên AWS Lambda trong suốt 12 tuần thực tập tại chương trình First Cloud AI Journey (FCAJ).

Nội dung nhật ký công việc được phân bổ chi tiết theo từng tuần như sau:

**Tuần 1:** [Làm quen với chương trình FCAJ, thiết lập môi trường dòng lệnh AWS CLI, cấu hình bảo mật IAM Profiles và thiết lập ngân sách AWS Budgets](1.1-week1/)

**Tuần 2:** [Nghiên cứu lý thuyết phân quyền chuyên sâu, phân tích kiến trúc IAM Policy (Rules, ARNs, Conditions) và ứng dụng IAM Role cho Serverless Compute](1.2-week2/)

**Tuần 3:** [Tìm hiểu kiến trúc Serverless (Không máy chủ), nguyên lý FaaS của AWS Lambda, cơ chế Trigger sự kiện và tối ưu hóa tài nguyên (Memory/Timeout)](1.3-week3/)

**Tuần 4:** [Phân tích vòng đời hàm Lambda (Execution Environment Lifecycle), hiện tượng Cold Start trên JVM và các chiến lược giảm độ trễ cho ứng dụng Java](1.4-week4/)

**Tuần 5:** [Nghiên cứu ảo hóa và containerization, xây dựng Dockerfile đa tầng (Multi-stage build) tối ưu dung lượng cho Spring Boot và đẩy image lên Amazon ECR](1.5-week5/)

**Tuần 6:** [Nghiên cứu kiến trúc mã nguồn mở AWS Serverless Java Container, cơ chế ánh xạ luồng dữ liệu (Request/Response Mapping) từ Web Framework sang Lambda](1.6-week6/)

**Tuần 7:** [Thực hành quy trình đóng gói tự động với Maven, cơ chế gom tụ nén thư viện phụ thuộc bằng maven-shade-plugin và xử lý trùng lặp artifact](1.7-week7/)

**Tuần 8:** [Khởi tạo kiến trúc dự án cốt lõi GearStore trên nền tảng Spring Boot 3, thiết lập cấu trúc Maven Monorepo và quản lý Dependency tập trung](1.8-week8/)

**Tuần 9:** [Tích hợp thư viện phụ thuộc aws-serverless-java-container-springboot3 vào pom.xml, loại bỏ Overhead của Servlet Container truyền thống](1.9-week9/)

**Tuần 10:** [Xây dựng lớp cổng vào trung tâm StreamLambdaHandler.java, xử lý tiếp nhận luồng dữ liệu nhị phân (Binary Stream) và điều hướng cho Spring Boot](1.10-week10/)

**Tuần 11:** [Cấu hình nâng cao maven-shade-plugin, tối ưu loại bỏ phụ thuộc dư thừa và đóng gói thành công file Shaded JAR (backend-0.0.1-SNAPSHOT.jar) siêu gọn nhẹ](1.11-week11/)

**Tuần 12:** [Triển khai thử nghiệm file JAR lên AWS Lambda Console, tinh chỉnh phân bổ dung lượng RAM, đo lường metrics trên Amazon CloudWatch và nghiệm thu hệ thống](1.12-week12/)