---
title: "Worklog Tuần 2"
date: 2026-05-11
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

### Mục tiêu tuần 2:
* Hoàn thành học phần Module 1 & Module 2 về ảo hóa máy chủ và mô hình phân quyền nâng cao trên điện toán đám mây.
* Nghiên cứu chuyên sâu cú pháp và cấu trúc JSON của IAM Policy (các khối `Effect`, `Action`, `Resource`, `Condition`, quy tắc ưu tiên Deny over Allow).
* Tìm hiểu định dạng chuẩn của Amazon Resource Name (ARN) đối với các tài nguyên AWS.
* Thiết lập và ứng dụng IAM Role (Execution Role) cho các dịch vụ compute không máy chủ (Serverless Compute) theo nguyên tắc quyền tối thiểu (Least Privilege Principle).

### Các công việc đã thực hiện:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Học Module 1 & 2 tổng quan về kiến trúc Virtual Machines (EC2) và các mô hình quản lý định danh identity-based / resource-based access control.<br>- Phân tích thành phần cấu trúc của một IAM Policy: Statement, Effect (Allow/Explicit Deny), Action, Resource ARN. | 12/05/2026   | 12/05/2026      | <https://cloudjourney.awsstudygroup.com/iam-basics/> |
| 3   | - Thực hành phân tích các chính sách IAM Policy mẫu, nghiên cứu nguyên tắc Explicit Deny đánh bại mọi lệnh Allow trong quy trình đánh giá của IAM Engine.<br>- Viết thử nghiệm các đoạn mã JSON Policy tùy chỉnh hạn chế quyền truy cập theo địa chỉ IP nguồn (Source IP Condition). | 13/05/2026   | 13/05/2026      | <https://cloudjourney.awsstudygroup.com/iam-policies/> |
| 4   | - Tìm hiểu kiến trúc IAM Role và quy trình ủy quyền tạm thời (Temporary Security Credentials) thông qua AWS Security Token Service (STS AssumeRole).<br>- Phân biệt sự khác nhau giữa IAM User (định danh cố định) và IAM Role (định danh linh hoạt gắn cho dịch vụ). | 14/05/2026   | 14/05/2026      | <https://cloudjourney.awsstudygroup.com/iam-roles/> |
| 5   | - Thiết lập IAM Execution Role dành riêng cho môi trường thực thi Serverless Lambda.<br>- Cấu hình Trust Policy cho phép dịch vụ `lambda.amazonaws.com` đóng vai trò AssumeRole và gán Policy cấp quyền ghi log lên CloudWatch (`logs:CreateLogGroup`, `logs:CreateLogStream`, `logs:PutLogEvents`). | 15/05/2026   | 15/05/2026      | <https://cloudjourney.awsstudygroup.com/iam-execution-role/> |
| 6   | - Tiến hành kiểm định phân quyền IAM Role trên AWS CLI bằng câu lệnh `aws iam get-role` và `aws iam list-attached-role-policies`.<br>- Tổng hợp báo cáo nghiên cứu lý thuyết IAM và chia sẻ kết quả với nhóm. | 16/05/2026   | 16/05/2026      | Tài liệu nội bộ dự án |

### Kết quả đạt được tuần 2:
* Nắm vững cơ chế đánh giá quyền hạn của IAM Engine, nguyên tắc Explicit Deny và quy chuẩn xây dựng tệp JSON Policy.
* Hiểu rõ cấu trúc địa chỉ định danh tài nguyên AWS ARN (`arn:aws:service:region:account-id:resource-id`).
* Thành thạo quy trình khởi tạo IAM Execution Role cho các dịch vụ tính toán không máy chủ (Serverless Compute), áp dụng triệt để nguyên tắc Least Privilege để đảm bảo an toàn hệ thống.