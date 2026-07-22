---
title: "Event 1"
date: 2026-05-23
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}

# Bài thu hoạch “Context Is Everything: Making AI Actually Work for You”

### Mục Đích Của Sự Kiện
- Xác định nguyên nhân AI phản hồi kém hiệu quả và làm rõ tầm quan trọng của dữ liệu ngữ cảnh (Context).
- Chuyển đổi tư duy từ viết prompt đơn lẻ sang xây dựng hệ thống quản lý ngữ cảnh đồng bộ.
- Tiếp cận bộ khung Simple Context Framework nhằm tối ưu hóa hiệu suất làm việc giữa lập trình viên và AI.
- Định hướng các ý tưởng dự án AI thực tế, phù hợp với năng lực triển khai của sinh viên.

### Danh Sách Diễn Giả
- **Anh Tính Trương** - Platform Engineer tại GoTymeX (AWS Vietnam phối hợp tổ chức).

### Nội Dung Nổi Bật

#### Khái niệm và vai trò của "Context"
- AI phản hồi sai hướng phần lớn do đầu vào thiếu thông tin nền tảng. AI không thể tự suy luận chính xác mục tiêu nếu người dùng không khai báo rõ ràng.
- Cấu trúc ngữ cảnh hoàn chỉnh bao gồm: Mục tiêu (Goal) + Tình huống (Situation) + Ràng buộc kỹ thuật (Constraints) + Dữ liệu liên quan (Evidence).
- Quản lý ngữ cảnh đầu vào là yếu tố quyết định, trực tiếp ảnh hưởng đến chất lượng kết quả đầu ra của mô hình AI.

#### Bộ khung ngữ cảnh đơn giản (Simple Context Framework)
Thiết lập cấu trúc thông tin 4 phần trước khi đưa ra yêu cầu cho AI:
- **Goal:** Xác định rõ ràng kết quả cụ thể cần đạt được.
- **Relevant info:** Sàng lọc đúng khối lượng dữ liệu cần thiết, loại bỏ hoàn toàn thông tin dư thừa gây nhiễu.
- **Constraints:** Giới hạn nghiêm ngặt về công nghệ (Tech stack, thư viện), thời gian, phong cách triển khai và định dạng đầu ra.
- **Success criteria:** Thiết lập các tiêu chí cụ thể để đánh giá kết quả đạt yêu cầu.

#### Định hướng các dự án AI cho sinh viên
Tư duy cung cấp đủ thông tin nền tảng để AI hoàn thành chính xác tác vụ với 4 hướng phát triển dự án gợi ý:
- AI Study Assistant (Tóm tắt tài liệu và tự tạo bộ câu hỏi ôn tập).
- PDF Chat App (Truy xuất và hỏi đáp thông tin dựa trên kho giáo trình).
- AI Code Reviewer (Phân tích mã nguồn, phát hiện lỗi và đề xuất tối ưu hóa logic Backend).
- Personal Second Brain (Hệ thống hóa ghi chú và tra cứu dữ liệu thông minh theo ngữ cảnh).

### Những Gì Học Được
- **Tư duy xây dựng "Bộ não thứ hai" (Personal Second Brain):** Lưu trữ và liên kết tri thức vào một cơ sở dữ liệu cố định, sử dụng AI để truy xuất nhanh khi cần nhằm giảm tải cho bộ nhớ sinh học và tập trung vào tư duy logic.
- **Kỹ năng Context Engineering (Kỹ nghệ ngữ cảnh):** Trở thành kỹ năng bổ trợ cốt lõi của kỹ sư phần mềm, biết cách cô lập dữ liệu đầu vào để hạn chế hiện tượng AI ảo tưởng thông tin (Hallucination).

### Ứng Dụng Vào Công Việc Và Học Tập
- **Xây dựng kho tri thức số làm đồ án:** Số hóa tài liệu thiết kế, tài liệu tích hợp API bên thứ ba (GHN, Ahamove), giải pháp xử lý lỗi database để dùng AI làm cổng tra cứu nhanh khi phát triển các module Backend.
- **Chuẩn hóa quy trình làm việc với AI:** Áp dụng bộ khung 4 yếu tố (Goal - Info - Constraints - Criteria) để khai báo rõ phiên bản framework, kiến trúc hệ thống và tiêu chí clean code trước khi yêu cầu AI sinh mã nguồn hoặc rà soát lỗi.
- **Tối ưu hóa quy trình tự học:** Sử dụng AI để tự động tạo bài kiểm tra phản biện từ slide bài giảng, chuẩn bị kiến thức nền tảng cho các kỳ thi học phần và bảo vệ học thuật.

### Trải Nghiệm Thực Tế Tại Sự Kiện
- Tiếp thu góc nhìn kỹ thuật thực tế từ chuyên gia doanh nghiệp, hiểu quy trình ứng dụng AI để tối ưu hóa hiệu suất công việc.
- Nhận thức rõ xu hướng ngành: Tương lai là sự cạnh tranh về năng lực khai thác và làm việc cùng AI giữa các nhân sự công nghệ.
- Sự kiện thu hút rất đông sinh viên từ nhiều trường đến tham dự. Do hội trường tầng 26 đã quá đông, em được ban tổ chức sắp xếp linh hoạt lên phòng chuyên dụng khác để theo dõi qua máy chiếu. Dù xem gián tiếp, chất lượng đường truyền và nội dung kiến thức vẫn được đảm bảo trọn vẹn. Đặc biệt, trong suốt buổi, các anh chị hỗ trợ thường xuyên ghé qua phòng để đặt câu hỏi tương tác và giải đáp thắc mắc trực tiếp cho sinh viên. Cuối chương trình, em còn được tham gia minigame giao lưu và nhận các phần quà ý nghĩa từ ban tổ chức.

#### Một số hình ảnh khi tham gia sự kiện
*(Để hiển thị ảnh, bạn lưu file ảnh vào thư mục `static/images/` rồi sửa lại tên file dưới đây)*

![Check-in sự kiện](/images/4-EventParticipated/check1.jpg "Chỗ ngồi trong lúc nghe diễn giả trình bày")
