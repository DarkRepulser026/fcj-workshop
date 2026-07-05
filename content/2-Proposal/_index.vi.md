---
title: "Proposal"
date: 2026-06-29
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# ReviewSentinel: Hệ Thống Phân Tích Cảm Xúc Đánh Giá Sản Phẩm Bằng AI
## Giải Pháp Serverless Trên AWS Cho Việc Phân Tích Đánh Giá Tự Động

### 1. Tóm Tắt Dự Án

ReviewSentinel là một dự án học tập/demo nhằm xây dựng một pipeline serverless nhỏ gọn trên AWS để tự động thu thập đánh giá sản phẩm, phân tích cảm xúc bằng AI, và hiển thị kết quả trên dashboard trực tiếp. Dự án được thiết kế cho quy mô vài trăm đến vài nghìn đánh giá chứ không phải lưu lượng production, sử dụng Amazon Comprehend và Amazon Bedrock (Claude 3 Haiku) để phân tích cảm xúc, DynamoDB và S3 để lưu trữ, cùng dashboard React để trực quan hóa. Mục tiêu là chứng minh một pipeline hoàn chỉnh, hoạt động đúng, và bảo mật từ đầu đến cuối — không phải xây dựng một sản phẩm thương mại — đồng thời giữ chi phí hàng tháng gần bằng $0 nhờ tận dụng AWS Free Tier và huỷ tài nguyên (teardown) giữa các phiên làm việc.

### 2. Vấn Đề Cần Giải Quyết

**Vấn đề là gì?**
Việc đọc từng đánh giá sản phẩm một để nắm bắt cảm nhận khách hàng không thể mở rộng dù chỉ ở quy mô nhỏ, và làm thủ công không cho ra một cách nhất quán, lặp lại được để phát hiện phản hồi tiêu cực kịp thời. Hiện chưa có cách nào nhẹ nhàng, chi phí thấp để tự động chấm điểm cảm xúc và xem xu hướng mà không phải xây một hệ thống tùy chỉnh nặng nề hoặc trả tiền cho một nền tảng phân tích thương mại đầy đủ.

**Giải pháp**
ReviewSentinel tiếp nhận các file đánh giá (CSV/JSON) qua S3, tự động kiểm tra và làm sạch dữ liệu bằng Lambda, lưu vào DynamoDB, và chạy từng đánh giá qua Amazon Comprehend để chấm điểm cảm xúc (có thể bổ sung một bước phân tích sâu hơn bằng Amazon Bedrock). Các đánh giá tiêu cực mạnh sẽ kích hoạt cảnh báo email qua SNS. Dashboard React, được bảo vệ bằng đăng nhập Amazon Cognito, hiển thị phân bố cảm xúc và xu hướng theo từng sản phẩm. Toàn bộ hạ tầng được triển khai bằng Terraform để có thể deploy và huỷ toàn bộ môi trường theo yêu cầu.

**Lợi ích**
Dự án mang lại kinh nghiệm thực hành với một kiến trúc serverless + AI thực tế (thu thập theo sự kiện → làm giàu bằng AI → API có xác thực → dashboard) có thể áp dụng cho nhiều trường hợp khác. Kết quả là một hệ thống tham chiếu hoạt động được và một nền tảng Terraform có thể tái sử dụng cho các dự án sau. Vì chạy trên Free Tier ở quy mô demo, chi phí duy trì gần như bằng không miễn là tài nguyên được huỷ giữa các lần sử dụng.

### 3. Kiến Trúc Giải Pháp

Nền tảng sử dụng kiến trúc AWS serverless, hướng sự kiện (event-driven). Một file đánh giá được tải lên S3 sẽ kích hoạt hàm Lambda kiểm tra và làm sạch dữ liệu trước khi lưu vào DynamoDB. Việc ghi vào DynamoDB kích hoạt hàm Lambda thứ hai (qua DynamoDB Streams) gọi Amazon Comprehend để chấm điểm cảm xúc, có thể làm giàu thêm bằng Amazon Bedrock. Kết quả tiêu cực sẽ gửi cảnh báo qua SNS. Lớp API Gateway + Lambda có xác thực Cognito phục vụ dashboard React, nơi trực quan hóa dữ liệu.

```
Tải lên (CSV/JSON)
      │
      ▼
Amazon S3 (bucket raw-reviews)
      │  Sự kiện S3
      ▼
AWS Lambda — review-processor
  (kiểm tra, làm sạch, loại trùng lặp)
      │
      ▼
Amazon DynamoDB (Reviews / Products / Users)
      │  DynamoDB Stream
      ▼
AWS Lambda — sentiment-analyzer
  (Amazon Comprehend + Bedrock tùy chọn)
      │
      ▼
Amazon SNS ── cảnh báo email khi cảm xúc tiêu cực

Amazon Cognito ── API Gateway (authorizer) ── AWS Lambda — api-handler
      │
      ▼
Dashboard React (S3 + CloudFront / Amplify)

Amazon CloudWatch ── logs, dashboard, cảnh báo cho toàn bộ hàm Lambda
```

**Các Dịch Vụ AWS Sử Dụng**
- **Amazon S3**: Lưu trữ file đánh giá thô được tải lên và báo cáo đã xử lý (2 bucket), chặn truy cập công khai, mã hóa khi lưu trữ.
- **AWS Lambda**: Ba hàm — review-processor (kiểm tra/làm sạch), sentiment-analyzer (Comprehend/Bedrock), api-handler (REST API).
- **Amazon DynamoDB**: Ba bảng (Reviews, Products, Users) với GSI cho các mẫu truy vấn và bật Streams cho pipeline phân tích cảm xúc.
- **Amazon Comprehend**: Trích xuất cảm xúc, cụm từ khóa, và thực thể (entity) cơ bản.
- **Amazon Bedrock (Claude 3 Haiku)**: Bước phân tích sâu tùy chọn, chỉ dùng có chọn lọc để kiểm soát chi phí.
- **Amazon API Gateway**: REST API có authorizer Cognito và kiểm tra hợp lệ request.
- **Amazon Cognito**: Xác thực người dùng (JWT) cho dashboard và API.
- **Amazon SNS**: Cảnh báo email khi có đánh giá tiêu cực mạnh.
- **Amazon SQS**: Dead-letter queue cho các sự kiện xử lý thất bại.
- **Amazon CloudWatch**: Logs, dashboard, và cảnh báo (lỗi Lambda, độ trễ API).
- **Terraform**: Infrastructure as Code cho toàn bộ hệ thống, cho phép deploy/huỷ sạch sẽ.

**Thiết Kế Thành Phần**
- **Thu thập dữ liệu**: Người dùng tải lên file đánh giá CSV/JSON qua presigned URL của S3 do API cấp.
- **Xử lý**: Hàm review-processor kiểm tra schema, loại trùng lặp, và làm sạch văn bản trước khi ghi vào DynamoDB; các lỗi được đưa vào dead-letter queue SQS thay vì bị bỏ qua âm thầm.
- **Phân tích AI**: Hàm sentiment-analyzer chạy khi có bản ghi mới trong DynamoDB, gọi Comprehend (và Bedrock nếu cần) để chấm điểm cảm xúc và trích xuất cụm từ khóa/thực thể.
- **Cảnh báo**: SNS gửi thông báo email khi cảm xúc tiêu cực mạnh.
- **API & Xác thực**: Cognito cấp JWT; API Gateway xác minh mọi request trước khi chuyển đến api-handler, phục vụ các endpoint sản phẩm, đánh giá, và phân tích.
- **Dashboard**: Ứng dụng React + TypeScript hiển thị danh sách sản phẩm, giao diện tải lên, và biểu đồ cảm xúc (pie/line/bar bằng Recharts).

### 4. Triển Khai Kỹ Thuật

**Các Giai Đoạn Triển Khai**
Dự án thực hiện theo bốn giai đoạn:
- **Thiết lập nền tảng & IaC**: Thiết lập tài khoản AWS sandbox, khởi tạo Terraform, và định nghĩa S3 bucket, bảng DynamoDB, và IAM role cơ bản (Ngày 1–3).
- **Xử lý backend & pipeline AI**: Xây dựng và triển khai hàm Lambda review-processor và sentiment-analyzer, kết nối sự kiện S3 và DynamoDB Streams, tích hợp Comprehend/Bedrock, và cấu hình cảnh báo SNS (Ngày 4–11).
- **API, xác thực & frontend**: Thiết lập Cognito, triển khai API Gateway có xác thực + hàm Lambda api-handler, và xây dựng/triển khai dashboard React (Ngày 12–18).
- **Kiểm thử & tăng cường bảo mật**: Chạy kiểm thử tích hợp với dữ liệu mẫu, xác minh cấu hình IAM tối thiểu quyền và mã hóa, và hoàn thiện tài liệu (Ngày 19–21).

**Yêu Cầu Kỹ Thuật**
- **Backend**: Python 3.9+ cho hàm Lambda, boto3 để gọi AWS SDK, Terraform cho hạ tầng.
- **Dịch vụ AI**: Amazon Comprehend (cảm xúc, cụm từ khóa, thực thể) và quyền truy cập model Amazon Bedrock (Claude 3 Haiku) được bật trong region triển khai.
- **Frontend**: Node.js 18+, React + TypeScript, Recharts cho biểu đồ, triển khai qua Amplify hoặc S3 + CloudFront.
- **Bảo mật**: Cognito user pool để xác thực, IAM role tối thiểu quyền cho từng hàm Lambda, mã hóa khi lưu trữ (S3/DynamoDB) và khi truyền (TLS/HTTPS), không cho phép truy cập S3 công khai, không có thông tin xác thực (credentials) hard-code trong mã nguồn.
- **Region**: Triển khai một region duy nhất (ap-southeast-1), hoàn toàn serverless — không dùng EC2 hay cơ sở dữ liệu tự quản lý.

### 5. Tiến Độ & Các Mốc Quan Trọng

**Tiến Độ Dự Án** (~3 tuần, làm bán thời gian, một người thực hiện — có thể rút ngắn nếu có thêm người làm song song)
- **Tuần 1**: Thiết lập nền tảng & IaC; pipeline xử lý backend (tải lên → kiểm tra → lưu trữ) hoạt động hoàn chỉnh.
- **Tuần 2**: Pipeline phân tích cảm xúc AI hoạt động (Comprehend + Bedrock tùy chọn); cảnh báo SNS được xác minh; API có xác thực được triển khai.
- **Tuần 3**: Dashboard React được xây dựng và triển khai; kiểm thử tích hợp toàn diện; tự đánh giá bảo mật; hoàn thiện tài liệu và hướng dẫn huỷ tài nguyên.

### 6. Dự Toán Chi Phí

Vì đây là dự án học tập/demo chứ không phải triển khai production, dự toán dưới đây phản ánh cả mức chi phí thực tế ở quy mô demo lẫn một mốc tham chiếu ở quy mô lớn hơn (50.000 đánh giá/tháng) để minh họa khả năng mở rộng của kiến trúc mà không cần thiết kế lại.

**Ở quy mô demo (vài trăm đánh giá, kiểm thử trong vài ngày)**
- Hầu hết các dịch vụ dưới đây nằm trong AWS Free Tier.
- Chi phí sử dụng Comprehend và Bedrock tối đa chỉ vài đô la cho khối lượng kiểm thử.
- Chạy `terraform destroy` giữa các phiên làm việc giúp tránh phát sinh chi phí DynamoDB/CloudWatch liên tục.
- **Chi phí ước tính: dưới $5 cho toàn bộ giai đoạn học tập/demo.**

**Tham chiếu: ở quy mô 50.000 đánh giá/tháng (chỉ để minh họa khả năng mở rộng)**

| Dịch vụ | Chi phí hàng tháng (USD) | Ghi chú |
|---|---|---|
| AWS Lambda | $0.05 | ~100K lượt gọi/tháng, phần lớn trong Free Tier |
| Amazon DynamoDB | $75.00 | Pay-per-request: ~50K ghi, ~200K đọc |
| Amazon S3 | $0.05 | Lưu trữ + lượt gọi API |
| Amazon API Gateway | $3.50 | ~10K request/tháng |
| Amazon Comprehend | $25.00 | 50K văn bản, ~100 unit/đánh giá |
| Amazon Bedrock (tùy chọn) | $15.00 | ~50K văn bản, khuyến nghị dùng có chọn lọc |
| Amazon Cognito | Miễn phí | Dưới 50K người dùng hoạt động/tháng |
| Amazon CloudWatch | $5.00 | Logs, dashboard, cảnh báo |
| Amazon SNS | $0.50 | Thông báo cảnh báo |
| **Tổng** | **≈ $124/tháng** | ≈ $0.0025 mỗi đánh giá ở mức 50K/tháng |

### 7. Đánh Giá Rủi Ro

**Ma Trận Rủi Ro**
- Chi phí/giới hạn tốc độ (throttling) của Bedrock nếu gọi cho mọi đánh giá: Tác động trung bình, xác suất trung bình.
- Cấu hình sai quyền IAM cho một Lambda role: Tác động cao, xác suất thấp.
- Tài nguyên bị bỏ chạy sau khi demo (cache API Gateway, log CloudWatch): Tác động thấp, xác suất trung bình.
- Dữ liệu kiểm thử mẫu/tổng hợp không đủ đại diện để kiểm chứng độ chính xác cảm xúc: Tác động thấp, xác suất thấp.

**Chiến Lược Giảm Thiểu**
- Dùng Comprehend làm phương án chấm điểm cảm xúc mặc định; chỉ gọi Bedrock trên một mẫu hoặc khi cần.
- Rà soát từng IAM role của Lambda theo đúng hành động/tài nguyên thực sự cần thiết; tránh quyền wildcard.
- Ghi lại và chạy `terraform destroy` sau mỗi phiên làm việc; đặt cảnh báo ngân sách (budget alarm) làm phương án dự phòng.
- Sử dụng bộ dữ liệu kiểm thử đa dạng, được gán nhãn thủ công, bao gồm đánh giá tích cực, tiêu cực, và trung lập.

**Kế Hoạch Dự Phòng**
- Nếu Bedrock không khả dụng hoặc vượt ngân sách, chuyển về chấm điểm chỉ bằng Comprehend — pipeline vẫn hoạt động bình thường.
- Nếu một lần `terraform apply` thất bại giữa chừng, chạy `terraform destroy` và triển khai lại từ trạng thái sạch thay vì sửa thủ công.

### 8. Kết Quả Kỳ Vọng

**Cải Tiến Kỹ Thuật**
Một minh chứng hoạt động hoàn chỉnh, đầu-cuối cho pipeline dữ liệu hướng sự kiện, được làm giàu bằng AI: tải lên → kiểm tra → lưu trữ → phân tích → cảnh báo → trực quan hóa, với API có xác thực và dữ liệu được mã hóa xuyên suốt.

**Kết Quả Học Tập**
Kinh nghiệm thực hành với Infrastructure as Code (Terraform), thiết kế serverless hướng sự kiện (sự kiện S3, DynamoDB Streams), tích hợp dịch vụ AI (Comprehend, Bedrock), và áp dụng các nguyên tắc bảo mật cơ bản (IAM tối thiểu quyền, mã hóa, API có xác thực) mà không xây dựng quá mức cần thiết so với quy mô thực tế của dự án.

**Khả Năng Tái Sử Dụng**
Hệ thống Terraform và mã nguồn Lambda có thể dùng làm điểm khởi đầu cho các dự án serverless + AI trong tương lai, còn dữ liệu mẫu và script kiểm thử giúp việc demo lại hoặc mở rộng pipeline sau này trở nên dễ dàng hơn.