---
title: "Worklog Tuần 12"
date: 2026-07-20
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---

### Mục tiêu tuần 12:
* Thực hiện triển khai thử nghiệm (Deploy) tệp `backend-0.0.1-SNAPSHOT.jar` lên dịch vụ AWS Lambda thông qua AWS Management Console và AWS CLI.
* Khai báo chính xác Handler Entry Point: `com.gearstore.config.StreamLambdaHandler::handleRequest` và gắn IAM Execution Role đã thiết lập ở Tuần 2.
* Tiến hành đo lường hiệu năng thực tế, thử nghiệm tinh chỉnh dung lượng RAM của hàm Lambda (512 MB, 1024 MB, 2048 MB, 3072 MB) để tìm ra điểm cân bằng tối ưu giữa chi phí và tốc độ phản hồi.
* Phân tích các thông số vận hành (Init Duration, Duration, Max Memory Used) trên Amazon CloudWatch Logs, hoàn thiện nghiệm thu phân hệ đóng gói dự án.

### Các công việc đã thực hiện:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Đăng nhập AWS Console, tạo hàm Lambda mới đặt tên `gearstore-backend-service` chạy môi trường Runtime Java 17/21.<br>- Tải tệp `backend-0.0.1-SNAPSHOT.jar` lên Lambda Console và cấu hình Handler string `com.gearstore.config.StreamLambdaHandler::handleRequest`. | 21/07/2026   | 21/07/2026      | <https://cloudjourney.awsstudygroup.com/lambda-deployment-jar/> |
| 3   | - Cấu hình tích hợp Lambda với Amazon API Gateway (HTTP API), thiết lập tuyến đường (Route) `$default` để định hướng toàn bộ traffic web vào hàm Lambda.<br>- Thực hiện kiểm thử gọi API từ Postman, xác nhận hệ thống trả về kết quả thành công HTTP 200 OK. | 22/07/2026   | 22/07/2026      | <https://cloudjourney.awsstudygroup.com/apigateway-lambda-integration/> |
| 4   | - Tiến hành thử nghiệm đo lường hiệu năng (Benchmark Performance) bằng cách thay đổi dung lượng RAM của Lambda theo các mức: 512MB, 1024MB, 1536MB, 2048MB và 3072MB.<br>- Nhận xét: Mức RAM 2048MB mang lại hiệu năng tối ưu nhất (giúp CPU scale tương ứng, giảm thời gian Cold Start Init Duration từ ~4.2s xuống còn ~1.1s). | 23/07/2026   | 23/07/2026      | <https://cloudjourney.awsstudygroup.com/lambda-memory-benchmark/> |
| 5   | - Truy vết vết log vận hành trên Amazon CloudWatch Logs Insights.<br>- Phân tích dòng log `REPORT`: `Init Duration: 1120.45 ms`, `Duration: 145.20 ms`, `Billed Duration: 146 ms`, `Memory Size: 2048 MB`, `Max Memory Used: 215 MB`. Không xảy ra hiện tượng OutOfMemoryError. | 24/07/2026   | 24/07/2026      | <https://cloudjourney.awsstudygroup.com/cloudwatch-logs-analysis/> |
| 6   | - Bật tính năng AWS Lambda SnapStart giúp hạ thời gian Cold Start xuống mức dưới 400ms.<br>- Tổng hợp báo cáo tổng kết 12 tuần thực tập, nghiệm thu toàn bộ phân hệ đóng gói dự án GearStore và bàn giao tài liệu cho giảng viên hướng dẫn. | 25/07/2026   | 28/07/2026      | Tài liệu tổng kết dự án |

### Kết quả đạt được tuần 12:
* Triển khai thành công ứng dụng Spring Boot 3 dạng Serverless Java Container lên AWS Lambda và tích hợp hoàn chỉnh với Amazon API Gateway.
* Tinh chỉnh thành công thông số RAM ở mức 2048 MB, giúp tối ưu hóa hiệu năng CPU và giảm thời gian Cold Start hơn 73%.
* Làm chủ quy trình phân tích log vận hành trên CloudWatch Insights, kiểm soát chính xác dung lượng bộ nhớ thực tế tiêu thụ (`Max Memory Used`).
* Hoàn thành xuất sắc toàn bộ mục tiêu 12 tuần thực tập tại chương trình First Cloud AI Journey (FCAJ).