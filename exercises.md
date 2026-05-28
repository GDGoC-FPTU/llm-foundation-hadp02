# Ngày 1 — Bài Tập & Phản Ánh
## Nền Tảng LLM API | Phiếu Thực Hành

**Thời lượng:** 1:30 giờ  
**Cấu trúc:** Lập trình cốt lõi (60 phút) → Bài tập mở rộng (30 phút)

---

## Phần 1 — Lập Trình Cốt Lõi (0:00–1:00)

Chạy các ví dụ trong Google Colab tại: https://colab.research.google.com/drive/172zCiXpLr1FEXMRCAbmZoqTrKiSkUERm?usp=sharing

Triển khai tất cả TODO trong `template.py`. Chạy `pytest tests/` để kiểm tra tiến độ.

**Điểm kiểm tra:** Sau khi hoàn thành 4 nhiệm vụ, chạy:
```bash
python template.py
```
Bạn sẽ thấy output so sánh phản hồi của GPT-4o và GPT-4o-mini.

---

## Phần 2 — Bài Tập Mở Rộng (1:00–1:30)

### Bài tập 2.1 — Độ Nhạy Của Temperature
Gọi `call_openai` với các giá trị temperature 0.0, 0.5, 1.0 và 1.5 sử dụng prompt **"Hãy kể cho tôi một sự thật thú vị về Việt Nam."**

**Bạn nhận thấy quy luật gì qua bốn phản hồi?** (2–3 câu)
> Khi temperature tăng từ 0.0 lên 1.5, mức độ ngẫu nhiên, sự sáng tạo và biến động của phản hồi tăng rõ rệt. Ở mức thấp (0.0 - 0.5), phản hồi có độ nhất quán cao, lặp lại các sự thật quen thuộc; trong khi ở mức rất cao (1.5), văn bản bắt đầu trở nên lộn xộn, thiếu logic và dễ bị lỗi diễn đạt (hallucination).

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> Tôi sẽ đặt temperature từ **0.0 đến 0.2**. Bởi vì chatbot hỗ trợ khách hàng yêu cầu tính chính xác, nhất quán và đáng tin cậy tuyệt đối về thông tin sản phẩm và chính sách, việc giữ temperature thấp giúp đảm bảo các câu hỏi giống nhau sẽ luôn nhận được câu trả lời chuẩn xác và đồng nhất.

---

### Bài tập 2.2 — Đánh Đổi Chi Phí
Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
> Dựa trên bảng giá `PRICING_1M_TOKENS`, tỷ lệ giá của GPT-4o so với GPT-4o-mini là:
> - Input: $5.00 / $0.150 = **33.33 lần**
> - Output: $20.00 / $0.600 = **33.33 lần**
> Do đó, với bất kỳ tỷ lệ phân bổ input/output nào cho workload này, GPT-4o luôn đắt hơn GPT-4o-mini chính xác **33.33 lần**.

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
> - **GPT-4o xứng đáng:** Khi thực hiện các tác vụ suy luận logic phức tạp, lập trình/sửa lỗi code nâng cao, hoặc trích xuất thông tin có cấu trúc từ các tài liệu pháp lý dày đặc cần độ chính xác tối đa.
> - **GPT-4o-mini tốt hơn:** Khi xử lý các tác vụ quy mô lớn, đơn giản và lặp đi lặp lại như phân tích cảm xúc (sentiment analysis), phân loại nhãn sản phẩm, tóm tắt nhanh đoạn chat ngắn, giúp tối ưu hóa chi phí cực kỳ hiệu quả.

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
> **Streaming quan trọng nhất** trong các ứng dụng chatbot hội thoại tương tác trực tiếp với con người (như trợ lý ảo, chatbot CSKH), nơi phản hồi theo thời gian thực giúp giảm thiểu cảm giác chờ đợi của người dùng (perceived latency) bằng cách hiển thị chữ ngay lập tức. Ngược lại, **non-streaming phù hợp hơn** cho các tác vụ xử lý ngầm (background jobs), phân tích dữ liệu hàng loạt (batch processing), hoặc khi cần gọi API trả về dữ liệu cấu trúc (JSON/XML) để hệ thống phần mềm khác kiểm tra tính toàn vẹn trước khi sử dụng.


## Danh Sách Kiểm Tra Nộp Bài
- [x] Tất cả tests pass: `pytest tests/ -v`
- [x] `call_openai` đã triển khai và kiểm thử
- [x] `call_openai_mini` đã triển khai và kiểm thử
- [x] `compare_models` đã triển khai và kiểm thử
- [x] `streaming_chatbot` đã triển khai và kiểm thử
- [x] `retry_with_backoff` đã triển khai và kiểm thử
- [x] `batch_compare` đã triển khai và kiểm thử
- [x] `format_comparison_table` đã triển khai và kiểm thử
- [x] `exercises.md` đã điền đầy đủ
- [x] Sao chép bài làm vào folder `solution` và đặt tên theo quy định 
