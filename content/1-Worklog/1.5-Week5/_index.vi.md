---
title: "Worklog Tuần 5"
date: 2026-06-01
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Mục tiêu tuần 5:
* Nghiên cứu học phần Module 4 về công nghệ ảo hóa cấp hệ điều hành (OS-level Virtualization) và containerization.
* Thực hành đóng gói ứng dụng bằng Docker engine, viết tệp `.dockerignore` và tối ưu các layer bộ đệm (layer caching).
* Thiết kế Dockerfile đa tầng (Multi-stage build) giúp phân tách môi trường biên dịch (Build environment) và môi trường thực thi (Runtime environment) nhằm tối ưu triệt để dung lượng image cho Java/Spring Boot.
* Tạo kho lưu trữ Amazon Elastic Container Registry (ECR), thực hiện xác thực Docker CLI với ECR và đẩy container image lên cloud repository.

### Các công việc đã thực hiện:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Nghiên cứu Module 4 về Virtualization và Containers, so sánh kiến trúc giữa Virtual Machines (Hypervisor-based) và Docker Containers (Kernel sharing).<br>- Cài đặt Docker Desktop và kiểm tra các câu lệnh quản lý container cơ bản (`docker run`, `docker ps`, `docker images`). | 02/06/2026   | 02/06/2026      | <https://cloudjourney.awsstudygroup.com/docker-basics/> |
| 3   | - Nghiên cứu phương pháp viết Dockerfile chuẩn cho ứng dụng Java/Spring Boot.<br>- Phân tích tác động của các câu lệnh `FROM`, `RUN`, `COPY`, `WORKDIR`, `ENTRYPOINT` lên số lượng layer và kích thước cuối cùng của container image. | 03/06/2026   | 03/06/2026      | <https://cloudjourney.awsstudygroup.com/dockerfile-best-practices/> |
| 4   | - Áp dụng kỹ thuật Multi-stage build trong Dockerfile: Stage 1 sử dụng Maven image (Eclipse Temurin JDK) để biên dịch mã nguồn thành file JAR; Stage 2 chỉ sử dụng JRE siêu gọn nhẹ (Alpine/Distroless JRE) để chạy file JAR.<br>- Kết quả: Giảm dung lượng image từ ~800MB xuống còn ~200MB. | 04/06/2026   | 04/06/2026      | <https://cloudjourney.awsstudygroup.com/docker-multistage/> |
| 5   | - Khởi tạo một Private Container Repository trên dịch vụ Amazon Elastic Container Registry (ECR).<br>- Chạy câu lệnh `aws ecr get-login-password` để xác thực Docker CLI với ECR registry, thực hiện `docker tag` và `docker push` để tải container image lên Amazon ECR. | 05/06/2026   | 05/06/2026      | <https://cloudjourney.awsstudygroup.com/ecr-deployment/> |
| 6   | - Bật tính năng Image Scanning on Push trong ECR để tự động quét lỗ hổng bảo mật (CVE vulnerabilities) của container image.<br>- Tổng hợp báo cáo kỹ thuật containerization và chia sẻ tài nguyên với nhóm. | 06/06/2026   | 06/06/2026      | Tài liệu nội bộ dự án |

### Kết quả đạt được tuần 5:
* Hiểu rõ ưu thế của công nghệ đóng gói containerization so với ảo hóa truyền thống.
* Thành thạo kỹ thuật viết Dockerfile đa tầng (Multi-stage build) giúp cắt giảm tới 75% dung lượng container image cho ứng dụng Java/Spring Boot.
* Làm chủ quy trình đẩy và quản lý container image an toàn trên Amazon Elastic Container Registry (ECR), sẵn sàng tích hợp với các dịch vụ container hoặc Lambda container image.