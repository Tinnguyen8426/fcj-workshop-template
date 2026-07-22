---
title: "Worklog Tuần 11"
date: 2026-07-13
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

### Mục tiêu tuần 11:
* Cấu hình tinh chỉnh chi tiết plugin `maven-shade-plugin` trong tệp `pom.xml` nhằm tối ưu hóa kích thước artifact đầu ra cho toàn bộ dự án GearStore.
* Loại bỏ tất cả các thư viện phụ thuộc dư thừa (unused transitive dependencies), các thư viện phục vụ testing (`junit`, `mockito`), và các framework logging trùng lặp.
* Thực hiện tiến trình đóng gói biên dịch hệ thống thành một tệp Shaded Uber JAR duy nhất với tên gọi `backend-0.0.1-SNAPSHOT.jar`.
* Đảm bảo tệp JAR có dung lượng siêu nhỏ gọn để tối ưu hóa thời gian tải artifact (Code Download Time) và thời gian giải nén khi hàm Lambda xảy ra Cold Start.

### Các công việc đã thực hiện:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Rà soát toàn bộ cây phụ thuộc Maven bằng lệnh `mvn dependency:tree`, phát hiện các thư viện không cần thiết cho môi trường sản xuất.<br>- Cấu hình bổ sung thẻ `<scope>test</scope>` hoặc thẻ `<exclusions>` để loại bỏ các thư viện này khỏi JAR thực thi. | 14/07/2026   | 14/07/2026      | <https://cloudjourney.awsstudygroup.com/maven-dependency-optimization/> |
| 3   | - Cấu hình khối `<configuration>` chi tiết cho `maven-shade-plugin` trong `pom.xml`.<br>- Thêm quy tắc `<createUnshadedJar>false</createUnshadedJar>` và tinh chỉnh `<artifactSet>` để chỉ chọn lọc những thư viện thực sự cần thiết. | 15/07/2026   | 15/07/2026      | <https://cloudjourney.awsstudygroup.com/maven-shade-advanced/> |
| 4   | - Bổ sung các Resource Transformers: `ManifestResourceTransformer` (khai báo Main-Class / Handler Entry Point) và `ServicesResourceTransformer` (giúp gộp các file `META-INF/services/*` cho Java SPI / Spring factories). | 16/07/2026   | 16/07/2026      | <https://cloudjourney.awsstudygroup.com/maven-shade-advanced/> |
| 5   | - Thực thi lệnh biên dịch nén `mvn clean package -DskipTests`, quan sát quá trình Shade nén các class file.<br>- Kiểm tra kích thước file output `target/backend-0.0.1-SNAPSHOT.jar`: Dung lượng đã được tối ưu siêu nhỏ gọn (chỉ còn ~35 MB so với ~110 MB ban đầu). | 17/07/2026   | 17/07/2026      | <https://cloudjourney.awsstudygroup.com/maven-shade-advanced/> |
| 6   | - Sử dụng công cụ `jar -tf target/backend-0.0.1-SNAPSHOT.jar` để kiểm tra danh sách class bên trong, đảm bảo lớp `StreamLambdaHandler.class` nằm đúng đường dẫn root package.<br>- Bàn giao file JAR hoàn chỉnh cho nhóm để chuẩn bị deploy. | 18/07/2026   | 18/07/2026      | Tài liệu nội bộ dự án |

### Kết quả đạt được tuần 11:
* Hoàn thành tinh chỉnh cấu hình `maven-shade-plugin` đạt chuẩn chuyên nghiệp cho bài toán Serverless Java.
* Loại bỏ thành công 100% các phụ thuộc không dùng tới, cắt giảm tới 68% dung lượng file JAR xuống chỉ còn ~35 MB.
* Biên dịch thành công tệp artifact thực thi duy nhất `backend-0.0.1-SNAPSHOT.jar`, sẵn sàng triển khai lên môi trường AWS Cloud với tốc độ Cold Start tối ưu.