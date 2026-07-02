---
title: "Event 1"
date: 2026-05-09
weight: 1
chapter: false
pre: " <b> 2.5. </b> "
---

# Bài thu hoạch “FCAJ Community Day”

### Mục Đích Của Sự Kiện

- Chia sẻ phương pháp "hack não bộ" để duy trì động lực học tập bền vững.
- Hướng dẫn kỹ năng Prompt Engineering để tối ưu hóa đầu ra của AI.
- Định hướng tư duy nghề nghiệp, tầm quan trọng của nền tảng (foundation) và sự liêm chính (integrity) cho sinh viên/fresher.
- Giới thiệu phương pháp BMX Method giúp tối ưu hóa quy trình phát triển phần mềm với sự hỗ trợ của AI.

### Danh Sách Diễn Giả

- **Anh Khang** - Chia sẻ về động lực học tập và định hướng mindset nghề nghiệp
- **Speaker (Chưa rõ tên)** - Chia sẻ về kỹ năng Prompt Engineering và demo dự án AI Serverless trên AWS
- **Anh Thảo** - Software Developer tại VIB, trình bày về phương pháp phát triển phần mềm BMX

### Nội Dung Nổi Bật

#### Động lực học tập và "Hack" não bộ
- **Bản chất của sự trì hoãn:** Các nền tảng mạng xã hội và game online lợi dụng cơ chế tiết dopamine (phần thưởng nhanh, tính tò mò) để giữ chân người dùng. Trong khi đó, việc học mang lại kết quả chậm.
- **Phương pháp khắc phục:** 
  - Tạo các "streak" (chuỗi) học tập hàng ngày để dùng nỗi sợ "mất chuỗi" làm động lực duy trì.
  - Chia nhỏ mục tiêu học (ví dụ: chia nhỏ từng dịch vụ AWS thay vì dồn học 5 tiếng/ngày) để tránh cảm giác bị ngợp.
  - Tự tạo ra các phần thưởng nhỏ ngẫu nhiên cho bản thân sau mỗi phiên học.

#### Ultimate Prompt Engineering
- **7 thành phần của một Prompt chuẩn:** Role, Task, Context, Input, Example, Output format, và Constraint.
- **Kỹ thuật tối ưu hóa:** Cần cung cấp đầy đủ thông tin, sử dụng dấu phân cách để chia section, chia nhỏ input dài và đặc biệt tránh gộp nhiều chủ đề không liên quan vào một luồng chat để hạn chế tình trạng AI bị "hallucination" (ảo giác).
- **AWS Architecture Demo:** Giới thiệu hệ thống thực tế tối ưu prompt sử dụng kiến trúc Serverless (CloudFront, S3, API Gateway, Lambda, Amazon Bedrock, DynamoDB, Cognito).

#### Tư duy nghề nghiệp & Mindset đi làm
- **AI Amplify (Khuếch đại):** AI không thay thế lập trình viên, nó chỉ làm nền tảng hiện tại của bạn lớn hơn (người giỏi sẽ giỏi hơn, người tệ sẽ tệ hơn). Do đó, "Foundation" (nền tảng cốt lõi) luôn là thứ quan trọng nhất.
- **Mindset "Why":** Luôn đặt câu hỏi "Tại sao?" thay vì chỉ tập trung vào "Làm gì?" khi tiếp cận một công nghệ hay kiến trúc hệ thống.
- **Sự liêm chính (Integrity):** Là tính tự giác hoàn thiện đến cùng các trường hợp ngoại lệ (edge cases) trong code dù không bị quản lý giám sát trực tiếp. 
- **Đánh giá lợi ích công việc:** Không chỉ nhìn vào mức lương ngắn hạn, mà cần cân nhắc tới kinh nghiệm, network, và kiến thức thực tế thu nạp được.

#### BMX Method - Ứng dụng AI trong SDLC
- **Vấn đề của cách làm cũ:** Liên tục prompt yêu cầu cho AI mà không có thiết kế tổng quan sẽ sinh ra "code rác", dễ bị gãy hệ thống khi update.
- **Giải pháp BMX Method:**
  - Áp dụng triết lý "Document-driven": Viết document chuẩn xác để AI tự đọc và code.
  - Tách nhỏ dự án theo quy trình: Epic -> Story -> Sub-tasks.
  - Phân vai rõ ràng cho các AI Agents (PM, Architect, Scrum Master, Developer, Reviewer) để giữ AI luôn trong đúng ngữ cảnh, tránh overlap.

### Những Gì Học Được

#### Tư Duy Thiết Kế & Lập Trình
- **Foundation-first approach:** Doanh nghiệp đề cao tư duy giải quyết vấn đề và nền tảng hạ tầng vững chắc hơn là việc biết dùng thật nhiều frameworks bề nổi.
- **Tư duy chất lượng mã nguồn:** Việc ứng dụng AI phải gắn liền với thiết kế kiến trúc chuẩn từ đầu, không thể giao phó toàn bộ vòng đời sản phẩm cho LLM mà thiếu sự kiểm soát của con người.

#### Kiến Trúc Kỹ Thuật
- **Prompt Architecture:** Cách setup role, context và constrain cho AI để tăng tính chính xác.
- **Tích hợp mô hình:** Nắm bắt luồng hoạt động cơ bản của một ứng dụng GenAI trên môi trường AWS (sử dụng Amazon Bedrock kết hợp Lambda backend).

#### Chiến Lược Công Việc
- **Nhìn nhận dài hạn:** Ưu tiên môi trường cung cấp trải nghiệm, network và bài học thực chiến ở giai đoạn fresher.
- **Chấp nhận sai lầm:** Sai lầm là một phần để phát triển kỹ năng nhanh chóng, miễn là biết phân tích gốc rễ (why) và có integrity để chủ động sửa lỗi.

### Ứng Dụng Vào Công Việc

- **Áp dụng Prompt Engineering chuẩn:** Cấu trúc lại các lời nhắc (prompts) khi dùng AI trong công việc hàng ngày thành 7 bước rõ ràng để rút ngắn thời gian debug.
- **Triển khai BMX Method:** Ở các task lập trình sắp tới, tôi sẽ tập trung viết Document và vẽ Architecture phân tích tính năng trước khi nhờ AI hỗ trợ sinh code hay refactor.
- **Tạo Daily Streak:** Lên lịch duy trì việc commit code hoặc học tài liệu kỹ thuật về AWS mỗi ngày, liên tục không ngắt quãng để xây dựng thói quen.
- **Luyện tập câu hỏi "Why":** Phân tích kỹ lý do đằng sau các pattern đang được sử dụng trong codebase hiện tại của công ty.

### Trải nghiệm trong event

Tham gia sự kiện **“FCAJ Community Day”** là một trải nghiệm rất thực tế và mang tính định hướng cao. Nó không chỉ cung cấp cho tôi các kỹ thuật hiện đại mà còn làm rõ kỳ vọng thực sự của doanh nghiệp. Một số trải nghiệm nổi bật:

#### Tiếp cận kiến thức từ đa góc nhìn
- Được lắng nghe những góc nhìn chân thật từ Senior và nhà tuyển dụng giúp tôi nhận ra rằng thái độ làm việc, sự liêm chính (integrity) và kiến thức nền tảng (foundation) đôi khi còn quyết định sự nghiệp lớn hơn cả các công nghệ bề nổi.
- Được mổ xẻ trực tiếp nguyên nhân tâm lý khiến bản thân hay trì hoãn, từ đó có phương pháp khắc phục thực tế.

#### Trải nghiệm kỹ thuật thực tế
- Phần trình bày về **BMX Method** thực sự thay đổi cách tôi sử dụng AI. Thay vì chat một cách ngẫu hứng và nhận lại code lỗi bối cảnh (hallucinate), tôi hiểu được tầm quan trọng của việc chia nhỏ dự án (Epic/Story) và giao task cho từng AI Agent cụ thể.
- Nhìn thấy trực tiếp mô hình kết nối giữa các dịch vụ của AWS Serverless (CloudFront, API Gateway, Lambda, DynamoDB) với Amazon Bedrock.

#### Định hình tư duy cốt lõi
- Xóa bỏ nỗi lo "AI cướp việc", tôi hiểu rằng AI chỉ đóng vai trò bộ khuếch đại (Amplify). Nếu mình nắm vững cốt lõi, AI sẽ làm mình xuất sắc hơn; ngược lại, nếu hổng kiến thức, AI sẽ khuếch đại cái sai.
- Bài học về việc luôn đặt câu hỏi **"Tại sao?" (Why)** giúp tôi tránh việc lập trình như một cái máy và tư duy sâu hơn về các quyết định kiến trúc.

#### Một số hình ảnh khi tham gia sự kiện
* Thêm các hình ảnh của các bạn tại đây
> Tổng thể, sự kiện đã giúp tôi trang bị cả "vũ khí kỹ thuật" (Prompt Engineering, BMX) lẫn "áo giáp tâm lý" (Mindset học tập, Integrity), tạo hành trang vững chắc để tự tin hơn trong kỳ thực tập tại FCAJ Cloud Journey.