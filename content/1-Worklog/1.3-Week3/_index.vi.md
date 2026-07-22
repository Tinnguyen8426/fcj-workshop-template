---
title: "Worklog Tuần 3"
date: 2026-05-18
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Mục tiêu tuần 3:
* Nghiên cứu học phần Module 3 về kiến trúc Không máy chủ (Serverless Architecture) và mô hình Event-Driven Architecture (EDA).
* Tìm hiểu nguyên lý hoạt động của dịch vụ Function-as-a-Service (FaaS) AWS Lambda và cơ chế tính phí dựa trên số lượng request và thời gian thực thi (Gigabyte-seconds).
* Khám phá các nguồn kích hoạt sự kiện (Event Sources/Triggers) phổ biến như S3 events, API Gateway, DynamoDB Streams và SQS.
* Nắm vững phương pháp cấu hình và tối ưu hóa tài nguyên tính toán (dung lượng Memory từ 128 MB đến 10,240 MB và tỷ lệ vCPU tương ứng) cùng hạn mức Timeout phù hợp.

### Các công việc đã thực hiện:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Nghiên cứu tài liệu Module 3 về kiến trúc Serverless, so sánh sự khác biệt về chi phí vận hành (TCO) và khả năng mở rộng giữa máy chủ EC2 truyền thống và FaaS AWS Lambda.<br>- Tìm hiểu mô hình Event-Driven Architecture và luồng xử lý sự kiện trong ứng dụng hiện đại. | 19/05/2026   | 19/05/2026      | <https://cloudjourney.awsstudygroup.com/serverless-intro/> |
| 3   | - Khởi tạo hàm Lambda thử nghiệm trên Console và AWS CLI, cấu hình Runtime environment (Java 17/21).<br>- Phân tích các mô hình gọi hàm: Đồng bộ (Synchronous Invocation), Bất đồng bộ (Asynchronous Invocation) và Polling-based (Event Source Mapping). | 20/05/2026   | 20/05/2026      | <https://cloudjourney.awsstudygroup.com/lambda-invocations/> |
| 4   | - Thực hành kết nối Event Source Triggers với AWS Lambda (thử nghiệm trigger nhận file từ Amazon S3 bucket và nhận HTTP request từ Amazon API Gateway).<br>- Quan sát dữ liệu `JSON Event` truyền vào hàm thông qua tham số `Context` và `InputStream`. | 21/05/2026   | 21/05/2026      | <https://cloudjourney.awsstudygroup.com/lambda-triggers/> |
| 5   | - Thử nghiệm điều chỉnh cấu hình tài nguyên Memory cho hàm Lambda (từ 128MB, 512MB đến 2048MB).<br>- Đo lường mối quan hệ tỷ lệ thuận giữa dung lượng Memory được cấp phát và sức mạnh vCPU được AWS tự động phân bổ, đánh giá tác động đến tốc độ xử lý bài toán. | 22/05/2026   | 22/05/2026      | <https://cloudjourney.awsstudygroup.com/lambda-memory-tuning/> |
| 6   | - Cấu hình hạn mức thời gian thực thi tối đa (Timeout setting, tối đa 15 phút) nhằm tránh tình trạng hàm treo gây lãng phí chi phí.<br>- Tổng hợp tài liệu phân tích hiệu năng Lambda và chia sẻ với nhóm. | 23/05/2026   | 23/05/2026      | Tài liệu nội bộ dự án |

### Kết quả đạt được tuần 3:
* Thấu hiểu bản chất kiến trúc Serverless và mô hình hướng sự kiện (Event-Driven Architecture).
* Làm chủ cách thức cấu hình hàm AWS Lambda, phân biệt rõ các mô hình gọi hàm Đồng bộ / Bất đồng bộ / Event Source Mapping.
* Biết cách tối ưu hóa chi phí và hiệu năng Lambda thông qua việc cân bằng giữa dung lượng bộ nhớ RAM (Memory) và thời gian phản hồi thực tế của ứng dụng.