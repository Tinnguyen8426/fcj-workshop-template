---
title: "Worklog Tuần 4"
date: 2026-05-25
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Mục tiêu tuần 4:
* Thực hành các bài lab nâng cao thuộc Module 3 tập trung sâu vào môi trường chạy AWS Lambda.
* Nghiên cứu chi tiết vòng đời của môi trường thực thi Lambda (Execution Environment Lifecycle) bao gồm 3 giai đoạn: Init Phase, Invoke Phase và Shutdown Phase.
* Phân tích nguyên nhân gây ra hiện tượng độ trễ khởi động lạnh (Cold Start) khi chạy ứng dụng trên môi trường ảo hóa JVM (Java Virtual Machine initialization, class loading overhead, JIT compilation).
* Đánh giá các giải pháp giảm thiểu Cold Start cho nền tảng Java như: Provisioned Concurrency, AWS Lambda SnapStart (CRaC - Coordinated Restore at Checkpoint) và tối ưu hóa kích thước gói mã nguồn.

### Các công việc đã thực hiện:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Thực hiện các bài lab chuyên sâu Module 3 về AWS Lambda, phân tích vết log thực thi trên Amazon CloudWatch Logs.<br>- Đọc hiểu các thông số đo lường chuẩn: `Init Duration` (thời gian khởi tạo môi trường), `Duration` (thời gian chạy mã lệnh) và `Billed Duration`. | 26/05/2026   | 26/05/2026      | <https://cloudjourney.awsstudygroup.com/lambda-lifecycle/> |
| 3   | - Nghiên cứu chi tiết 3 giai đoạn trong vòng đời thực thi của Lambda: Init Phase (Extension init, Runtime init, Function init), Invoke Phase và Shutdown Phase.<br>- Xác định chính xác thời điểm xảy ra Cold Start trong Init Phase khi một micro-container mới được khởi chạy. | 27/05/2026   | 27/05/2026      | <https://cloudjourney.awsstudygroup.com/lambda-lifecycle/> |
| 4   | - Tiến hành đo lường hiện tượng Cold Start đối với các hàm viết bằng Java (JVM Runtime).<br>- Phân tích các yếu tố gây ra overhead: Khởi tạo JVM, nạp các class (Classloading), nạp các thư viện phụ thuộc heavyweight và thực thi các đoạn mã tĩnh (Static Initializer). | 28/05/2026   | 28/05/2026      | <https://cloudjourney.awsstudygroup.com/java-coldstart-analysis/> |
| 5   | - Nghiên cứu và thử nghiệm các cơ chế giảm thiểu độ trễ Cold Start cho Java.<br>- Tìm hiểu cơ chế AWS Lambda SnapStart dựa trên công nghệ CRaC (Coordinated Restore at Checkpoint) giúp chụp lại snapshot bộ nhớ của JVM sau khi Init xong để khôi phục nhanh chóng trong các lần gọi sau. | 29/05/2026   | 29/05/2026      | <https://cloudjourney.awsstudygroup.com/lambda-snapstart/> |
| 6   | - So sánh hiệu năng giữa Provisioned Concurrency (duy trì sẵn môi trường ấm) và SnapStart về mặt chi phí vận hành và tốc độ đáp ứng.<br>- Tổng hợp báo cáo kỹ thuật về chiến lược tối ưu Cold Start cho dự án Java/Spring Boot. | 30/05/2026   | 30/05/2026      | Tài liệu nội bộ dự án |

### Kết quả đạt được tuần 4:
* Hiểu sâu sắc kiến trúc vòng đời của môi trường thực thi AWS Lambda (Init, Invoke, Shutdown) và cách đọc các chỉ số log đo lường trên CloudWatch.
* Nhận diện chính xác nguyên nhân gốc rễ gây nên hiện tượng Cold Start đối với ứng dụng Java trên Serverless.
* Nắm vững cơ chế hoạt động của công nghệ AWS Lambda SnapStart (CRaC) và Provisioned Concurrency, làm nền tảng kỹ thuật để tối ưu hóa ứng dụng Spring Boot 3 ở các tuần tiếp theo.