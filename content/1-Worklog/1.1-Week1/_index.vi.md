---
title: "Worklog Tuần 1"
date: 2026-05-04
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

### Mục tiêu tuần 1:
* Tham gia các buổi định hướng (Orientation) của chương trình First Cloud AI Journey (FCAJ), tiếp nhận tài liệu kỹ thuật và thiết lập môi trường phát triển cá nhân.
* Cài đặt và cấu hình thành công công cụ dòng lệnh AWS CLI (v2) trên máy cục bộ, quản lý các tập cấu hình Named Profile bảo mật (`~/.aws/credentials` và `~/.aws/config`).
* Kiểm tra khả năng kết nối an toàn từ máy cá nhân đến hạ tầng AWS Cloud thông qua giao thức Security Token Service (AWS STS).
* Thiết lập các quy tắc cảnh báo ngân sách tự động bằng dịch vụ AWS Budgets & Billing Alarms nhằm kiểm soát chi phí thực thi bài lab.

### Các công việc đã thực hiện:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Tham gia buổi họp Kick-off định hướng chương trình First Cloud AI Journey, tiếp nhận thông tin lộ trình 12 tuần thực tập và quy chuẩn báo cáo.<br>- Nghiên cứu tài liệu tổng quan kiến trúc AWS Cloud và các nguyên tắc bảo mật thông tin ban đầu. | 05/05/2026   | 05/05/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 3   | - Tải xuống và cài đặt bộ công cụ dòng lệnh AWS CLI v2 trên hệ điều hành cục bộ.<br>- Khởi tạo Access Key và Secret Access Key từ giao diện AWS Management Console, thực hiện cấu hình `aws configure` thiết lập Region chính (`ap-southeast-1`) và định dạng đầu ra JSON. | 06/05/2026   | 06/05/2026      | <https://cloudjourney.awsstudygroup.com/1-aws-cli-setup/> |
| 4   | - Nghiên cứu cơ chế cấu hình nhiều profile (`--profile`) để phân tách môi trường Development và Staging trên tệp `~/.aws/credentials`.<br>- Chạy câu lệnh kiểm tra định danh `aws sts get-caller-identity` để xác thực Access Key đã active thành công và đúng IAM Role/User được gán. | 07/05/2026   | 07/05/2026      | <https://cloudjourney.awsstudygroup.com/1-aws-cli-setup/> |
| 5   | - Truy cập dịch vụ AWS Budgets, xây dựng chính sách cảnh báo chi phí chi tiết (Cost Budget Limit) ở ngưỡng 10 USD.<br>- Cấu hình kênh thông báo qua Email để tự động gửi cảnh báo khi mức chi phí thực tế hoặc dự báo (Forecasted) vượt quá 80% hạn mức ban đầu. | 08/05/2026   | 08/05/2026      | <https://cloudjourney.awsstudygroup.com/2-billing-alert/> |
| 6   | - Thực hiện kiểm tra lại Billing Dashboard, phân tích biểu đồ chi phí phát sinh AWS Cost Explorer ban đầu để đảm bảo các dịch vụ không tạo tài nguyên ngầm gây tốn phí.<br>- Tổng hợp báo cáo công việc tuần 1 và họp thảo luận với nhóm phát triển. | 09/05/2026   | 09/05/2026      | Tài liệu nội bộ dự án |

### Kết quả đạt được tuần 1:
* Đã nắm vững lộ trình học tập và yêu cầu kỹ thuật của chương trình First Cloud AI Journey.
* Thiết lập hoàn chỉnh môi trường phát triển với AWS CLI v2, quản lý an toàn thông tin xác thực qua Named Profile mà không cứng mã (hardcode) khóa bảo mật trong dự án.
* Làm chủ câu lệnh kiểm tra kết nối `aws sts get-caller-identity`, đảm bảo tính đúng đắn của quyền hạn IAM User/Role trước khi thao tác các bài lab phức tạp.
* Cấu hình thành công AWS Budgets, thiết lập ngưỡng bảo vệ tài khoản khỏi rủi ro chi phí phát sinh ngoài ý muốn trong suốt quá trình triển khai dự án.