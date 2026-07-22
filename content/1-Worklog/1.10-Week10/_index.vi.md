---
title: "Worklog Tuần 10"
date: 2026-07-06
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---

### Mục tiêu tuần 10:
* Lập trình hiện thực hóa lớp cổng vào trung tâm `StreamLambdaHandler.java` triển khai interface `RequestStreamHandler` của AWS Lambda Java Core.
* Xây dựng phương thức khởi tạo tĩnh (`static initializer`) cho đối tượng `SpringBootLambdaContainerHandler` nhằm kích hoạt Spring Boot Application Context duy nhất một lần trong giai đoạn Init Phase.
* Lập trình phương thức `handleRequest(InputStream input, OutputStream output, Context context)` tiếp nhận và giải mã các Request định dạng nhị phân (Binary Streams), bao gồm JSON REST Payloads và Multipart/form-data.
* Định tuyến luồng xử lý từ môi trường bên ngoài Cloud trực tiếp vào Spring DispatcherServlet và thu gom dữ liệu trả về client.

### Các công việc đã thực hiện:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Khởi tạo tệp mã nguồn `StreamLambdaHandler.java` trong package `com.gearstore.config`.<br>- Khai báo triển khai `RequestStreamHandler` interface của gói thư viện `aws-lambda-java-core`. | 07/07/2026   | 07/07/2026      | <https://cloudjourney.awsstudygroup.com/stream-lambda-handler/> |
| 3   | - Khởi tạo biến tĩnh `SpringBootLambdaContainerHandler<AwsProxyRequest, AwsProxyResponse> handler`.<br>- Đưa mã lệnh `SpringBootLambdaContainerHandler.getHttpApiV2ProxyHandler(GearstoreApplication.class)` vào khối `static` block để Spring Boot chỉ cần Bootstrapping 1 lần duy nhất trong Cold Start Init Phase. | 08/07/2026   | 08/07/2026      | <https://cloudjourney.awsstudygroup.com/stream-lambda-handler/> |
| 4   | - Viết mã xử lý chi tiết trong hàm `handleRequest(InputStream inputStream, OutputStream outputStream, Context context)`.<br>- Sử dụng `handler.proxyStream(inputStream, outputStream, context)` để đọc luồng dữ liệu nhị phân trực tiếp mà không cần nạp toàn bộ vào String buffer. | 09/07/2026   | 09/07/2026      | <https://cloudjourney.awsstudygroup.com/stream-lambda-handler/> |
| 5   | - Cấu hình hỗ trợ đọc định dạng nhị phân (Binary Media Types) cho các loại dữ liệu đặc biệt như hình ảnh, tệp tin đính kèm (`multipart/form-data`, `image/png`, `application/pdf`). | 10/07/2026   | 10/07/2026      | <https://cloudjourney.awsstudygroup.com/binary-data-lambda/> |
| 6   | - Viết Unit Test giả lập dữ liệu `InputStream` truyền vào `StreamLambdaHandler` để kiểm tra khả năng giải mã và điều hướng APIController thành công.<br>- Thảo luận kết quả kiểm thử lớp Handler với nhóm phát triển. | 11/07/2026   | 11/07/2026      | Tài liệu nội bộ dự án |

### Kết quả đạt được tuần 10:
* Đã lập trình hoàn chỉnh lớp cổng vào trung tâm `StreamLambdaHandler.java` cho dự án Spring Boot 3 trên AWS Lambda.
* Ứng dụng kỹ thuật Static Initialization giúp khởi tạo Spring Context ngay từ giai đoạn Lambda Init Phase, tối ưu hóa tốc độ xử lý cho các request tiếp theo.
* Làm chủ kỹ thuật truyền nhận dữ liệu qua Stream (`InputStream` / `OutputStream`), giải mã thành công cả dữ liệu nhị phân và dữ liệu văn bản JSON.
* Viết thành công Unit Test xác nhận tính chính xác của luồng điều hướng request trước khi đóng gói triển khai lên Cloud.