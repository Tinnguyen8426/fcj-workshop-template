---
title: "Tự đánh giá"
date: 2026-07-26
weight: 6
chapter: false
pre: " <b> 6. </b> "
---

Trải qua hành trình 12 tuần thực tập trong khuôn khổ chương trình **First Cloud AI Journey (FCAJ)** do **AWS Vietnam** đồng hành từ **04/05/2026** đến **25/07/2026**, em đã có cơ hội quý giá để cọ xát thực tế, chuyển hóa các nền tảng lý thuyết được học ở trường thành năng lực triển khai thực tiễn.

Suốt kỳ thực tập, em đã tập trung nghiên cứu chuyên sâu về hệ sinh thái Điện toán đám mây AWS, từ cơ chế bảo mật phân quyền IAM, mô hình Serverless FaaS (AWS Lambda), kỹ thuật container hóa ứng dụng với Docker/Amazon ECR, cho đến việc ứng dụng thư viện `aws-serverless-java-container-springboot3`. Kết quả cốt lõi là em đã hoàn thiện dự án **GearStore** trên nền **Spring Boot 3**, giải quyết triệt để bài toán tối ưu file Shaded JAR qua `maven-shade-plugin`, xây dựng bộ điều hướng `StreamLambdaHandler.java` xử lý luồng dữ liệu nhị phân (Binary Stream) và triển khai vận hành thành công trên hạ tầng AWS Lambda.

Về thái độ làm việc, em luôn tuân thủ nghiêm túc lộ trình công việc đề ra theo từng tuần, chủ động tra cứu tài liệu kỹ thuật, rà soát log hệ thống và tích cực kết nối với các thành viên để tối đa hóa tiến độ dự án.

Nhìn nhận lại cả quá trình, em xin đưa ra bảng tự đánh giá cá nhân dựa trên các tiêu chí sau:

### BẢNG TỰ ĐÁNH GIÁ BẢN THÂN

| STT | Tiêu chí | Mô tả | Tốt | Khá | Trung bình |
| --- | ----------------------------------- | ------------------------------------------------------------------------------------------------ | --- | --- | ---------- |
| 1   | **Kiến thức và kỹ năng chuyên môn** | Hiểu biết về ngành, áp dụng kiến thức vào thực tế, kỹ năng sử dụng công cụ, chất lượng công việc | ☐   | ✅   | ☐          |
| 2   | **Khả năng học hỏi**                | Tiếp thu kiến thức mới, học hỏi nhanh                                                            | ✅   | ☐   | ☐          |
| 3   | **Chủ động**                        | Tự tìm hiểu, nhận nhiệm vụ mà không chờ chỉ dẫn                                                  | ✅   | ☐   | ☐          |
| 4   | **Tinh thần trách nhiệm**           | Hoàn thành công việc đúng hạn, đảm bảo chất lượng                                                | ✅   | ☐   | ☐          |
| 5   | **Kỷ luật**                         | Tuân thủ giờ giấc, nội quy, quy trình làm việc                                                   | ☐   | ✅   | ☐          |
| 6   | **Tính cầu tiến**                   | Sẵn sàng nhận feedback và cải thiện bản thân                                                     | ✅   | ☐   | ☐          |
| 7   | **Giao tiếp**                       | Trình bày ý tưởng, báo cáo công việc rõ ràng                                                     | ✅   | ☐   | ☐          |
| 8   | **Hợp tác nhóm**                    | Làm việc hiệu quả với đồng nghiệp, tham gia nhóm                                                 | ✅   | ☐   | ☐          |
| 9   | **Ứng xử chuyên nghiệp**            | Tôn trọng đồng nghiệp, đối tác, môi trường làm việc                                             | ✅   | ☐   | ☐          |
| 10  | **Tư duy giải quyết vấn đề**        | Nhận diện vấn đề, đề xuất giải pháp, sáng tạo                                                    | ☐   | ✅   | ☐          |
| 11  | **Đóng góp vào dự án/tổ chức**      | Hiệu quả công việc, sáng kiến cải tiến, ghi nhận từ team                                         | ✅   | ☐   | ☐          |
| 12  | **Tổng thể**                        | Đánh giá chung về toàn bộ quá trình thực tập                                                     | ✅   | ☐   | ☐          |

### CÁC ĐIỂM CẦN CẢI THIỆN VÀ PHƯƠNG HƯỚNG PHÁT TRIỂN

Bên cạnh những kết quả tích cực đã đạt được, em tự nhận thấy bản thân cần tiếp tục hoàn thiện một số khía cạnh sau:

*   **Rèn luyện tính kỷ luật và quản lý thời gian:** Cần thắt chặt hơn nữa việc tuân thủ các chuẩn mực quản lý mã nguồn trên Git/Maven và quy trình triển khai của nhóm. Đồng thời, sắp xếp hợp lý thời lượng giữa việc hoàn thành các bài lab lý thuyết với giai đoạn thực hành dự án Spring Boot Serverless để đảm bảo tiến độ triển khai luôn ở mức tối ưu.
*   **Nâng cao năng lực chẩn đoán và khắc phục sự cố (Troubleshooting):** Đối với các lỗi hệ thống mang tính chất đặc thù (như độ trễ Cold Start trên môi trường Java JVM, xung đột thư viện Maven Artifact hoặc sự cố ánh xạ luồng nhị phận), em cần rút ngắn thời gian khoanh vùng nguyên nhân. Giải pháp là rèn luyện phương pháp phân tích có hệ thống hơn và khai thác hiệu quả tài nguyên theo dõi log trên Amazon CloudWatch.
*   **Tối ưu kỹ năng truyền tải thông tin và làm việc nhóm:** Em sẽ tập trung cải thiện cách diễn đạt các vấn đề kỹ thuật phức tạp (chẳng hạn như cơ chế FaaS hay kiến trúc Serverless Java Container) theo hướng cô đọng, dễ hiểu. Bên cạnh đó, duy trì thái độ cởi mở trước các góp ý phản biện để tìm ra tiếng nói chung nhanh nhất khi thảo luận giải pháp cùng đồng đội.