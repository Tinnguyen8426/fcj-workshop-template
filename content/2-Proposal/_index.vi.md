---
title: "Bản đề xuất"
date: 2026-07-20
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# GearStore E-Commerce Platform  
## Giải pháp Cloud-Native & Serverless hợp nhất cho Hệ thống Thương mại Điện tử Thiết bị Gaming

### 1. Tóm tắt điều hành  
GearStore E-Commerce Platform là hệ thống bán hàng trực tuyến chuyên cung cấp thiết bị công nghệ và phụ kiện gaming (gear), được thiết kế dựa trên kiến trúc Serverless hiện đại. Nền tảng giải quyết các thách thức về tải đột biến (flash sale), tối ưu chi phí vận hành và đảm bảo trải nghiệm mua sắm thời gian thực liền mạch. Hệ thống kết hợp backend **Java 21 / Spring Boot 3** triển khai dạng Serverless trên **AWS Lambda**, cơ sở dữ liệu **Amazon DynamoDB** NoSQL phản hồi mili-giây, kết hợp lưu trữ phương tiện **Amazon S3** và xác thực an toàn qua **Amazon Cognito / JWT**. Giao diện web được tối ưu SEO và tốc độ truyền tải nhờ **Next.js** lưu trữ trên **AWS Amplify**. 

### 2. Tuyên bố vấn đề  
*Vấn đề hiện tại*  
Các hệ thống bán lẻ gear truyền thống thường gặp sự cố nghẽn mạng hoặc sập server vào các đợt đợt khuyến mãi lớn (flash sale) do hạ tầng monolithic khó mở rộng kịp thời. Chi phí duy trì server 24/7 cố định rất cao dù lượng truy cập ngoài giờ cao điểm thấp. Bên cạnh đó, việc quản lý danh mục sản phẩm đa dạng (bàn phím, chuột, tai nghe, màn hình) với các thuộc tính linh hoạt đòi hỏi một cơ sở dữ liệu NoSQL truy vấn cực nhanh thay cho RDBMS truyền thống.
*Giải pháp*  
GearStore áp dụng kiến trúc **AWS Serverless full-stack**:
- **Backend API**: Xây dựng bằng Java 21 & Spring Boot 3, tích hợp thư viện `aws-serverless-java-container` để đóng gói chạy trực tiếp trên **AWS Lambda** thông qua **Amazon API Gateway**.
- **Cơ sở dữ liệu & Lưu trữ**: Sử dụng **Amazon DynamoDB** (AWS SDK v2 DynamoDB Enhanced Client) để lưu trữ danh mục sản phẩm, đơn hàng và tài khoản với tốc độ phản hồi cực cao; **Amazon S3** chịu trách nhiệm lưu trữ hình ảnh sản phẩm chất lượng cao.
- **Quản lý người dùng & Bảo mật**: Tích hợp **Amazon Cognito** và JWT Authentication đảm bảo phân quyền an toàn giữa khách hàng và quản trị viên (Admin).
- **Giao diện Frontend**: Ứng dụng **Next.js (React)** responsive, giao diện chuẩn gaming/modern dark mode, được deploy trên **AWS Amplify**.
*Lợi ích và hoàn vốn đầu tư (ROI)*  
- **Tự động mở rộng (Auto-scaling)**: Hệ thống tự động mở rộng xử lý hàng nghìn truy vấn đồng thời trong đợt sale mà không cần can thiệp thủ công.
- **Tối ưu chi phí theo mô hình Pay-as-you-go**: Nhờ kiến trúc Serverless (Lambda & DynamoDB On-Demand), chi phí vận hành hạ tầng duy trì ở mức cực thấp khi không có truy cập (chỉ từ 0.50 – 1.20 USD/tháng cho quy mô thử nghiệm/lab).
- **Trải nghiệm người dùng vượt trội**: Tối ưu hóa thời gian tải trang dưới 1 giây, phản hồi API cực nhanh nhờ Java 21 runtime tối ưu và DynamoDB.

### 3. Kiến trúc giải pháp  
Nền tảng ứng dụng kiến trúc AWS Serverless đa tầng cho toàn bộ chu trình xử lý từ Frontend đến Database.
*Dịch vụ AWS sử dụng*  
- **AWS Lambda**: Chạy logic Spring Boot 3 backend (API endpoints xử lý Auth, Product, Order, Inventory).
- **Amazon API Gateway**: Tiếp nhận HTTP requests từ client và định tuyến đến AWS Lambda.
- **Amazon DynamoDB**: Lưu trữ dữ liệu NoSQL (Products, Categories, Users, Orders) với khả năng mở rộng không giới hạn.
- **Amazon S3**: Data lake / Object Storage lưu trữ tài nguyên hình ảnh sản phẩm và media.
- **AWS Amplify**: Hosting cho ứng dụng Next.js Frontend với CI/CD tự động từ Git.
- **Amazon Cognito**: Quản lý đăng ký, đăng nhập và phân quyền truy cập an toàn.
*Thiết kế thành phần*  
- **Client Tier**: Ứng dụng Next.js hiển thị catalogue sản phẩm, giỏ hàng, thanh toán và bảng điều khiển Admin.
- **API & Authentication Tier**: API Gateway đóng vai trò Entry Point, phối hợp với Amazon Cognito cấp và kiểm tra JWT token.
- **Business Logic Tier**: AWS Lambda kích hoạt Spring Boot 3 container (`StreamLambdaHandler`) xử lý các request nghiệp vụ mua bán.
- **Data & Storage Tier**: DynamoDB xử lý đọc/ghi dữ liệu thời gian thực; S3 lưu trữ và phân phối hình ảnh.

### 4. Triển khai kỹ thuật  
*Các giai đoạn triển khai*  
Dự án được chia thành 4 giai đoạn chính:  
1. **Nghiên cứu & Thiết kế kiến trúc**: Phân tích yêu cầu hệ thống bán lẻ gear, thiết kế Data Model cho DynamoDB và kiến trúc AWS Serverless (Tháng 1).  
2. **Ước tính chi phí & Xây dựng Backend Core**: Khởi tạo project Spring Boot 3 (Java 21), tích hợp AWS SDK v2 (DynamoDB Enhanced, S3), cấu hình Serverless Container Handler (Tháng 1-2).  
3. **Phát triển Frontend & Tích hợp AWS Services**: Xây dựng UI Next.js, tích hợp API Gateway, Cognito Auth và AWS S3 upload (Tháng 2).  
4. **Kiểm thử, Tối ưu & Triển khai**: Kiểm thử hiệu năng Lambda cold-start, đóng gói Maven Shade Plugin, deploy hoàn chỉnh lên AWS Amplify và AWS Lambda (Tháng 2–3).  
*Yêu cầu kỹ thuật*  
- **Backend**: Java 21, Spring Boot 3.3.0, Lombok, Maven (`maven-shade-plugin`), AWS SDK v2 (`dynamodb-enhanced`, `s3`), AWS Serverless Java Container.
- **Frontend**: Next.js, React, Tailwind CSS / Vanilla CSS, Axios/Fetch API.
- **Cloud & DevOps**: AWS Lambda, API Gateway, DynamoDB, S3, Cognito, AWS Amplify, AWS SAM / CDK.

### 5. Lộ trình & Mốc triển khai  
- **Chuẩn bị (Tháng 0)**: Khảo sát mô hình kinh doanh GearStore và thiết kế hệ thống.  
- **Thực tập / Phát triển (Tháng 1–3)**:  
    - Tháng 1: Thiết kế cơ sở dữ liệu DynamoDB và setup cấu trúc Spring Boot 3 Lambda.  
    - Tháng 2: Xây dựng các RESTful API (Auth, Products, Orders) và giao diện Next.js.  
    - Tháng 3: Tích hợp AWS Amplify, thử nghiệm tải flash sale, tối ưu hóa và đưa vào vận hành.  
- **Sau triển khai**: Theo dõi log qua CloudWatch, nâng cấp tính năng gợi ý sản phẩm thông qua AI/ML.

### 6. Ước tính ngân sách  
*Chi phí hạ tầng (Ước tính theo mô hình Serverless Pay-as-you-go)*  
- **AWS Lambda**: ~0.00 USD/tháng (Nằm trong AWS Free Tier với 1 triệu request/tháng).  
- **Amazon DynamoDB**: ~0.25 USD/tháng (Lưu trữ và dung lượng đọc/ghi On-Demand).  
- **Amazon S3**: ~0.10 USD/tháng (Lưu trữ ảnh sản phẩm & băng thông truyền tải).  
- **Amazon API Gateway**: ~0.05 USD/tháng (Cho khoảng 20.000–50.000 requests).  
- **AWS Amplify**: ~0.35 USD/tháng (Hosting frontend Next.js).  
- **Amazon Cognito**: 0.00 USD/tháng (Miễn phí tới 50.000 MAU).  
*Tổng chi phí cloud ước tính*: ~0.75 USD/tháng (~9.00 USD/12 tháng)  
*Thời gian hoàn vốn (ROI)*: 3–6 tháng nhờ tối ưu 100% chi phí duy trì server vật lý/EC2 cố định.

### 7. Đánh giá rủi ro  
*Ma trận rủi ro*  
- **Độ trễ Cold-start của AWS Lambda**: Ảnh hưởng trung bình, xác suất trung bình (xảy ra khi Lambda khởi tạo lại Java Virtual Machine).  
- **Vượt ngân sách do truy vấn ghi DynamoDB**: Ảnh hưởng trung bình, xác suất thấp.  
- **Gián đoạn dịch vụ Cloud**: Ảnh hưởng cao, xác suất rất thấp.  
*Chiến lược giảm thiểu*  
- **Lambda Cold-start**: Sử dụng Java 21 tối ưu, tối thiểu hóa dependencies và sử dụng Provisioned Concurrency nếu cần thiết.  
- ** DynamoDB**: Tối ưu Index (Global Secondary Indexes - GSI) và bật chế độ Cảnh báo ngân sách (AWS Budget Alerts).  

### 8. Kết quả kỳ vọng  
- **Cải tiến kỹ thuật**: Xây dựng thành công nền tảng E-Commerce chuẩn Cloud-Native Serverless, chịu tải linh hoạt, kiến trúc chuẩn RESTful API với Spring Boot 3 và Java 21.  
- **Giá trị dài hạn**: Cung cấp bộ giải pháp có khả năng nhân rộng cho các cửa hàng bán lẻ khác, dễ dàng tích hợp thêm các tính năng thanh toán (VNPAY, Momo) và quản lý kho hàng tự động trong tương lai.