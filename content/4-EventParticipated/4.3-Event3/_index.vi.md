---
title: "Event 3: FCAJ Community Day - 2026/06/06"
date: 2026-06-27
weight: 3
chapter: false
pre: " <b> 4.3. </b> "
---

![Proof](/fcj-workshop/images/4-EventParticipated/20260627_pov.jpg)

### **1. Diễn giả 1 (Steve Tran): AgenticOps for your Cloud**
*   **Thách thức của khách hàng:** Khi hệ thống phát triển từ **Microservices** sang **Observability**, các đội ngũ dần chạm phải **"Bức tường phức tạp" (Complexity Wall)**, buộc phải hướng tới hạ tầng có khả năng **tự phục hồi (self-healing infrastructure)**. Sự phát triển này kéo theo nhiều công cụ hơn cho mỗi đội vận hành, cần nhiều kỹ sư hơn cho cloud operations, và **MTTR** (Mean Time to Resolution) trên mỗi sự cố cũng tăng lên.
*   **Giải pháp — CloudThinker:** Một **nền tảng AgenticOps cho doanh nghiệp**, được xây dựng dựa trên nguyên lý rằng các AI agent xử lý và phản ứng nhanh hơn con người rất nhiều.
    *   **Lợi ích chính:** Tối ưu chi phí, xử lý các vấn đề bảo mật và sự cố, đồng thời giúp việc review/debug output trở nên dễ dàng hơn.
    *   **Agent chuyên biệt:** Triển khai các agent tùy chỉnh riêng cho từng vai trò vận hành.
    *   **Vòng lặp quan sát:** Nền tảng liên tục quan sát toàn bộ môi trường, sau đó học hỏi và hành động dựa trên những gì quan sát được.
    *   **Quản lý chi phí:** Hệ thống multi-agent thường làm tăng chi phí, nhưng CloudThinker áp dụng **tối ưu hóa context (context optimization)** để giữ chi phí ở mức hiệu quả.
    *   **Mô hình vận hành:** Tuân theo chu trình **Detect → Resolve → Validate** (Phát hiện → Xử lý → Xác nhận) trên các managed surfaces, có sự phê duyệt của con người và cam kết theo SLA.

### **2. Diễn giả 2 (Trung Vu, Nghi Danh, Kiet Tran): Building Voice Agent (VA) at Scale**
*   **Giới hạn hiện tại:** Công nghệ **speech-to-speech** thực sự vẫn chưa sẵn sàng để đưa vào sản xuất (production-ready).
*   **Cách tiếp cận thực tế:** Các đội thay vào đó sử dụng **TTS (Text-to-Speech)** kết hợp với các mô hình được fine-tune để nghe tự nhiên và giống giao tiếp của con người hơn.
*   **Tối ưu hiệu năng:** Mô hình cần được **"làm nóng" (warm up)** trước để đảm bảo độ trễ thấp và phản hồi nhanh.
*   **Cải tiến liên tục:** Hệ thống cần được xây dựng với **metric và observability** vững chắc, bao gồm cả trace để các nhà phát triển (con người) có thể theo dõi và cải thiện mô hình theo thời gian.

### **3. Diễn giả 3 (Bao Phan, Nguyen Nguyen): AWS DevOps Agent**
*   **Thách thức:** Chi phí cao cho việc điều tra sự cố thủ công, **MTTD** (Mean Time to Detect) và **MTTR** cao, mất context trong quá trình bàn giao, và cách tiếp cận xử lý vấn đề còn mang tính **bị động (reactive)**.
*   **Giải pháp:** Một AI agent tự động, được thiết kế để xử lý và chủ động ngăn ngừa sự cố, xoay quanh 5 trụ cột: **Context Learning, Control, Integration, Collaboration** và **Cost-effectiveness**.
*   **Vòng đời sự cố:** Tuân theo quy trình **Triage → Investigation → Mitigation → Prevention** (Phân loại → Điều tra → Giảm thiểu → Ngăn ngừa).
*   **Trường hợp phù hợp nhất:** Hoạt động tốt nhất trong môi trường có observability trưởng thành (log, metric, alarm rõ ràng) và ở quy mô lớn. Điều quan trọng là agent chỉ **đề xuất** các bước tiếp theo — con người vẫn chịu trách nhiệm phê duyệt và thực thi cuối cùng.

### **4. Diễn giả 4 (Truong Tran, Anh Minh): AI-Powered Productivity Workforce Planning for Enterprise**
*   **HR trong kỷ nguyên AI:** Các quy trình HR truyền thống tốn nhiều thời gian, dễ bỏ sót nhân tài chủ chốt, và thường dựa vào cảm tính hơn là dữ liệu.
*   **Sự thay đổi nhờ AI:** AI giúp giảm công sức sàng lọc thủ công, nâng vai trò của HR lên thành cố vấn nhân tài chiến lược, cho phép ra quyết định tuyển dụng dựa trên dữ liệu, tập trung hơn vào phát triển lãnh đạo, đồng thời cải thiện tiết kiệm chi phí và tốc độ mở rộng quy mô.
*   **Amazon Quick Solutions:** Một bộ "đồng đội AI" (agentic teammates) — bao gồm **Chat Agents, Research, QuickSight, Flows** và **Automate** — giúp chuyển dữ liệu thô thành báo cáo phân tích, trực quan hóa dữ liệu, và tự động hóa các quy trình từ đơn giản đến phức tạp nhiều bước.
*   **Kịch bản ứng dụng trong HR:** Quy trình kết nối dữ liệu → phân tích → tự động tạo báo cáo/trực quan hóa → đánh giá ứng viên → tự động theo dõi. Bao gồm việc tạo câu hỏi phỏng vấn theo mục tiêu, đánh giá ứng viên, tư vấn cho HR ra quyết định cuối cùng, và thiết kế quy trình sàng lọc phù hợp với yêu cầu của công ty.

### **5. Diễn giả 5 (Toan Nguyen, Nghi Danh): Building Secure Private MCP for AWS Quick**
*   **Bối cảnh:** Tổng quan về Amazon Quick và kiến trúc **MCP (Model Context Protocol)** bên dưới.
*   **Vấn đề:** Mặc dù Quick hỗ trợ MCP connector mặc định, nhưng điều này đòi hỏi một **public endpoint**, nghĩa là context và log phải đi qua internet công cộng — làm tăng đáng kể bề mặt tấn công (attack surface).
*   **Giải pháp — Kết nối VPC cho Quick:**
    *   **Private Entry:** Loại bỏ sự phụ thuộc vào public endpoint.
    *   **Private DNS:** Hostname chỉ được phân giải trong nội bộ VPC.
    *   **Đường truyền nội bộ hoàn toàn riêng tư:** Traffic đi qua **ENI → ALB → MCP**, giữ toàn bộ kết nối tách biệt khỏi internet công cộng.