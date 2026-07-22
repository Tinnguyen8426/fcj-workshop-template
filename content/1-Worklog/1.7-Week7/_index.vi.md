---
title: "Worklog Tuần 7"
date: 2026-06-15
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Mục tiêu tuần 7:
* Thực hành cấu hình xây dựng hệ thống tự động hóa đóng gói ứng dụng bằng công cụ Apache Maven.
* Nghiên cứu cơ chế hoạt động chuyên sâu của `maven-shade-plugin` trong việc gộp (aggregate) và nén toàn bộ mã nguồn compiled cùng tất cả các thư viện phụ thuộc (transitive dependencies) thành một tệp Uber/Fat JAR duy nhất.
* Xử lý vấn đề trùng lặp các tệp cấu hình Spring (`META-INF/spring.handlers`, `META-INF/spring.schemas`, `META-INF/spring.factories`) bằng cách sử dụng các Resource Transformers.
* Loại bỏ các tệp chữ ký số bảo mật dư thừa (`*.SF`, `*.DSA`, `*.RSA`) từ các tệp JAR phụ thuộc để tránh lỗi `Invalid signature file digest` khi thực thi trên Cloud.

### Các công việc đã thực hiện:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Nghiên cứu tài liệu Maven Build Lifecycle (phân biệt các phase `clean`, `compile`, `test`, `package`, `verify`, `install`).<br>- So sánh sự khác nhau giữa file JAR thông thường (Original JAR) và Fat/Uber JAR đóng gói đầy đủ phụ thuộc. | 16/06/2026   | 16/06/2026      | <https://cloudjourney.awsstudygroup.com/maven-packaging-basics/> |
| 3   | - Cấu hình `maven-shade-plugin` trong tệp `pom.xml`, định nghĩa goal `shade` liên kết với build phase `package`.<br>- Phân tích cấu trúc file Shaded JAR đầu ra, kiểm tra sự hiện diện của tất cả các class dependencies cần thiết cho runtime. | 17/06/2026   | 17/06/2026      | <https://cloudjourney.awsstudygroup.com/maven-shade-plugin-guide/> |
| 4   | - Nghiên cứu cơ chế Resource Transformers trong `maven-shade-plugin`.<br>- Cấu hình `AppendingTransformer` cho tệp `META-INF/spring.handlers`, `META-INF/spring.schemas` và `META-INF/spring.factories` để gộp nhiều định nghĩa cấu hình từ các module Spring khác nhau mà không bị ghi đè. | 18/06/2026   | 18/06/2026      | <https://cloudjourney.awsstudygroup.com/maven-shade-plugin-guide/> |
| 5   | - Cấu hình khối `<filters>` loại bỏ các tệp chữ ký số bảo mật của các thư viện bên thứ ba (`META-INF/*.SF`, `META-INF/*.DSA`, `META-INF/*.RSA`).<br>- Khắc phục triệt để rủi ro phát sinh lỗi `SecurityException: Invalid signature file digest` khi JVM khởi chạy file JAR trên AWS Lambda. | 19/06/2026   | 19/06/2026      | <https://cloudjourney.awsstudygroup.com/maven-shade-plugin-guide/> |
| 6   | - Chạy thử nghiệm lệnh `mvn clean package` trên terminal, kiểm tra tính toàn vẹn và dung lượng của tệp Shaded JAR tạo ra.<br>- Đánh giá tốc độ giải nén artifact và chia sẻ cấu hình `pom.xml` chuẩn cho nhóm. | 20/06/2026   | 20/06/2026      | Tài liệu nội bộ dự án |

### Kết quả đạt được tuần 7:
* Làm chủ tiến trình tự động hóa build gói ứng dụng với Apache Maven.
* Hiểu sâu cơ chế hoạt động của `maven-shade-plugin` và kỹ thuật gom tụ các thư viện phụ thuộc thành tệp Uber JAR duy nhất.
* Cấu hình thành công Resource Transformers gộp file cấu hình Spring và Filters loại bỏ signature dư thừa, đảm bảo artifact tương thích tuyệt đối với môi trường thực thi AWS Cloud.