---
title: "Event 2"
date: 2026-05-23
weight: 2
chapter: false
pre: " <b> 4.2. </b> "
---

# Bài thu hoạch “FCAJ Community Day (23-05-2026)”

### Mục Đích Của Sự Kiện

- Cập nhật định hướng nghề nghiệp và xu hướng việc làm trong kỷ nguyên AI.
- Hiểu rõ về tầm quan trọng của ngữ cảnh (context) khi làm việc với các công cụ AI.
- Tìm hiểu giải pháp phân tích dữ liệu kinh doanh với Amazon Q Business.
- Nắm bắt cơ chế tối ưu chi phí và bảo mật hạ tầng web với AWS CloudFront.
- Khám phá phương pháp phát triển phần mềm và xây dựng hệ thống Multi-Agent cấp doanh nghiệp (Enterprise Grade).

### Danh Sách Diễn Giả

- **Anh Nguyễn Gia Hưng** - Solution Architect AWS Việt Nam, Founder FCAJ
- **Anh Tịnh Trương** - Platform Engineer tại Got It
- **Anh Hải Anh** - Kỹ sư tại Pacific Việt Nam
- **Anh Nguyễn Hữu Thịnh** - DevOps Engineer
- **Team UTM Morpo (Uyển, Thảo, Mạch)** - Nhóm thắng giải cuộc thi Hackathon

### Nội Dung Nổi Bật

#### Định Hướng Nghề Nghiệp Kỷ Nguyên AI
- **Tình hình thị trường:** Khi chi phí phát triển phần mềm rẻ đi nhờ AI, nhu cầu xây dựng sản phẩm sẽ tăng đột biến. Điều này tạo ra một luồng công việc mới: Sửa chữa, duy trì và vận hành (Platform Engineering) những hệ thống được sinh ra hàng loạt từ AI.
- **Yêu cầu đối với kỹ sư:** Bằng đại học và kiến thức nền tảng vẫn mang tính quyết định. Tuy nhiên, để cạnh tranh, ứng viên cần có thêm kiến thức nghiệp vụ (Business Context) và phải có "Sản phẩm thực tế" thay vì chỉ làm các demo đơn thuần.

#### Tối Ưu Hóa LLM & Vấn Đề Context
- **Tầm quan trọng của Context:** AI cần hiểu ngữ cảnh cụ thể (domain của doanh nghiệp, coding style của team) để không sinh ra các đoạn code hoặc luồng xử lý vô dụng.
- **Hội chứng "Internet Puller":** Cảnh báo về thói quen copy/paste code hoặc kéo các công cụ, thư viện trên mạng về một cách bừa bãi mà không hiểu bản chất. Điều này dẫn đến phình to source code và mất kiểm soát khi dự án lớn lên.
- **Tính bất định của LLM:** Mặc dù đã cấu hình độ sáng tạo thấp (Temperature = 0), AI đôi khi vẫn trả về các output khác nhau. Do đó, cần phải test sâu và thiết kế hệ thống luôn sẵn sàng xử lý các output bị lỗi format.

#### Giải Pháp Dữ Liệu & Hạ Tầng Cloud
- **Amazon Q Business:** Trình diễn khả năng kết nối Agent từ các nguồn dữ liệu (như Excel) để tự động phân tích và tạo dashboard trực quan (BI) hỗ trợ quản trị mà không cần viết code.
- **AWS CloudFront:** Giới thiệu mô hình tính giá Flat Rate thay thế cho Pay-as-you-go, giúp doanh nghiệp tránh rủi ro "Bill Spike" (đội giá) do bị tấn công DDoS. Cập nhật thêm các tính năng hỗ trợ HTTP/3, tự động nén dữ liệu và sử dụng VBC Origin để bảo mật hạ tầng.

#### Xây Dựng Hệ Thống Multi-Agent Cho Doanh Nghiệp
- **Kiến trúc Multi-Agent:** Đối với các bài toán phức tạp (như đánh giá tín dụng doanh nghiệp), cần chia nhỏ bài toán. Mỗi Agent sẽ đảm nhận một vai trò chuyên biệt (Financial Analyst, Market Researcher) dưới sự điều phối của một Orchestrator. Tránh gộp chung vào Single-Agent vì sẽ làm quá tải giới hạn Context.
- **Bảo mật và Tuân thủ:** Việc tích hợp Tool (như MCP) tùy tiện trong môi trường doanh nghiệp là cực kỳ nguy hiểm. Cần thiết lập ranh giới an toàn (Guardrails), phân quyền rõ ràng và ghi log (Audit) mọi quyết định do AI đưa ra để đảm bảo tính tuân thủ pháp lý và rủi ro (Compliance & Security).

### Những Gì Học Được

#### Tư Duy Thiết Kế & Kỹ Thuật
- Nắm được cách tối ưu hóa LLM không chỉ qua prompt mà còn qua việc cung cấp ngữ cảnh đúng và kiểm soát sự bất định của mô hình.
- Hiểu được nguyên lý thiết kế hệ thống Multi-Agent an toàn, đáp ứng tiêu chuẩn khắt khe của doanh nghiệp (Enterprise Grade) thay vì chỉ làm các công cụ AI thử nghiệm.
- Mở rộng kiến thức về hạ tầng Cloud, cách CloudFront bảo vệ server gốc và tối ưu hóa chi phí truyền tải.

#### Chiến Lược Công Việc & Mindset
- **ROI & Business Value:** Xây dựng hệ thống phần mềm không chỉ để "chạy được" mà phải an toàn, đáng tin cậy và giải quyết đúng bài toán kinh doanh. Luôn có góc nhìn về hiệu quả đầu tư (ROI).
- **Tư duy Vận hành:** Nhận ra giá trị của việc viết mã hạ tầng (Infrastructure as Code - Terraform) để quản lý hạ tầng minh bạch, lưu vết các lần cập nhật.
- **Kỷ luật làm Product:** Tránh tham lam tính năng ("Feature Creep"), tập trung hoàn thiện Core Value cốt lõi nhất khi nguồn lực và thời gian có hạn (bài học từ việc thi Hackathon).

### Ứng Dụng Vào Công Việc

- **Áp dụng AI có chắt lọc:** Chấm dứt thói quen "Internet Puller", thay vào đó tự review và chọn lọc các prompt, công cụ AI thực sự phù hợp với ngữ cảnh dự án thực tế của công ty.
- **Nâng cấp bảo mật khi dùng AI:** Kiểm duyệt kỹ đầu vào và đầu ra của LLM trước khi tích hợp vào hệ thống để đảm bảo không rò rỉ dữ liệu nhạy cảm của khách hàng.
- **Thực hành Cloud Architecture:** Chủ động tìm hiểu sâu hơn về kiến trúc Serverless, áp dụng Terraform trong việc triển khai hạ tầng cơ bản thay vì thao tác tay trên console.
- **Lấy nghiệp vụ làm trọng tâm:** Mỗi khi đề xuất tích hợp tính năng mới hoặc ứng dụng AI, luôn bắt đầu bằng việc phân tích nghiệp vụ (Business Context) và giá trị thực tế mang lại cho tổ chức.

### Trải nghiệm trong event

Buổi **FCAJ Community Day** ngày 23/05/2026 mang lại những góc nhìn cực kỳ sắc bén về khoảng cách giữa việc "làm demo" và "làm sản phẩm thực tế cho doanh nghiệp". Một số trải nghiệm đáng chú ý:

#### Góc nhìn thực tế từ chuyên gia
- Rất ấn tượng với phần phân tích về xu hướng việc làm, giúp tôi định vị lại bản thân: phải tạo ra sản phẩm hoàn chỉnh và hiểu sâu business thay vì chỉ trau dồi bề nổi của kỹ thuật lập trình.
- Lần đầu tiên tôi hiểu được sự khắc nghiệt trong việc tuân thủ bảo mật cấp doanh nghiệp, nơi yếu tố "Security" quan trọng hơn việc chạy đua áp dụng công nghệ AI mới nhất.

#### Những bài học không có trên sách vở
- Bài học về sự tham lam tính năng khi giới hạn nguồn lực (từ nhóm thắng giải Hackathon) giúp tôi nhìn nhận lại cách làm đồ án cá nhân hiệu quả hơn.
- Việc một hệ thống dù có AI tiên tiến đến đâu cũng phải được thiết kế để xử lý cho những lúc nó "trả lời sai" (hallucinate) đã thay đổi hoàn toàn cách tôi nghĩ về việc thiết kế hệ thống phần mềm tích hợp trí tuệ nhân tạo.

#### Một số hình ảnh khi tham gia sự kiện
* Thêm các hình ảnh của các bạn tại đây
> Sự kiện đã trang bị cho tôi một tư duy thiết kế hệ thống vững vàng, luôn đặt yếu tố bảo mật, nghiệp vụ và khả năng vận hành lên hàng đầu – một hành trang tuyệt vời để bước tiếp trong chặng đường thực tập tại FCAJ.