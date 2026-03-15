# affect-state

## Trạng thái hiện tại

✅ **Đã hoàn thành Giai đoạn 1: Ý tưởng & Problem Definition** cho đồ án tốt nghiệp.

Mục tiêu của tài liệu này là ghi nhận rõ các quyết định sản phẩm đã được chốt trước khi chuyển sang Giai đoạn 2 (Product & System Design).

---

## 1) Problem Definition (đã chốt)

Người dùng có nhu cầu chia sẻ cảm xúc qua văn bản nhưng không thấy an toàn khi nói với người quen.

`affect-state` hướng tới một kênh trò chuyện riêng tư trên web, trong đó hệ thống:
- nhận diện cảm xúc từ tin nhắn người dùng (**6 cảm xúc cơ bản**),
- trả về phản hồi đồng cảm theo **template/rule-based** (không phán xét),
- hỗ trợ người dùng gọi tên cảm xúc và theo dõi xu hướng cảm xúc theo thời gian.

### Ràng buộc an toàn
- Không tuyên bố thay thế chuyên gia tâm lý.
- Không chẩn đoán lâm sàng.
- Nếu có tín hiệu rủi ro, chỉ ở mức **cảnh báo mềm** và điều hướng người dùng đến nguồn hỗ trợ phù hợp.

---

## 2) Người dùng mục tiêu (đã chốt)

- **Primary persona (P1):** Sinh viên năm 1–4 có stress học tập/quan hệ, cần nơi chia sẻ nhanh và không bị phán xét.
- **Secondary persona (P2):** Người đi làm trẻ (22–30) có xu hướng burnout/cô đơn.
- **Ngôn ngữ chính:** Tiếng Việt.

### JTBD (chuẩn hóa)
"Khi tôi buồn và rối vì bị chia tay, tôi muốn có một nơi an toàn để viết ra suy nghĩ và được phản hồi đồng cảm + được gọi tên cảm xúc của mình, để tôi bình tĩnh lại và định hình bước tiếp theo, mà không cần phải nói với người thật và không sợ bị đánh giá."

---

## 3) Giá trị sản phẩm (Value Proposition)

1. **Labeling cảm xúc rõ ràng:** giúp người dùng gọi tên cảm xúc thay vì chỉ “thấy tệ”.
2. **Phản hồi đồng cảm có cấu trúc:** phản hồi theo mẫu an toàn, giảm rủi ro câu trả lời thiếu kiểm soát.
3. **Theo dõi cảm xúc theo thời gian:** hỗ trợ tự phản tư (self-reflection) theo phiên/chuỗi chat.

---

## 4) Scope MVP (đã chốt)

### Must-have
- Chat UI trên web.
- Nhận diện **6 cảm xúc cơ bản** + confidence cho từng message.
- Biểu đồ cảm xúc theo thời gian.

### Nice-to-have (nếu còn thời gian)
- Soft crisis warning (keyword/pattern + threshold) + hiển thị tài nguyên hỗ trợ.

### Dữ liệu
- Hướng dữ liệu: **kết hợp** public dataset tiếng Việt (nếu có) + tự thu thập qua form + guideline gán nhãn.
- Ưu tiên giảm rủi ro demo: dữ liệu người dùng của MVP lưu local.

---

## 5) Quyết định phạm vi để giảm rủi ro

- **Không login trong MVP** để giảm độ phức tạp bảo mật và tăng xác suất hoàn thành đúng hạn.
- **Lưu local (IndexedDB/Dexie.js)** thay vì server DB trong bản demo.
- Có thể mở rộng login + server DB ở giai đoạn sau mà không thay đổi bản chất bài toán ML cốt lõi.

---

## 6) Non-goals (điều không làm trong MVP)

- Không xây LLM sinh phản hồi tự do.
- Không “phân tích sâu nội tâm” theo kiểu suy đoán nguyên nhân cá nhân.
- Không thu thập dữ liệu nhạy cảm không có consent rõ ràng.
- Không thay thế tư vấn chuyên môn tâm lý.

---

## 7) Tiêu chí nghiệm thu Giai đoạn 1

Giai đoạn 1 được xem là hoàn tất khi đã chốt được:
- Vấn đề sản phẩm cụ thể, có ràng buộc an toàn.
- Persona chính/phụ và JTBD rõ ràng.
- Scope MVP có must-have / nice-to-have.
- Bộ non-goals và định hướng dữ liệu.
- Định hướng metric đánh giá cho các giai đoạn sau (Macro-F1, confusion matrix, mức hữu ích phản hồi).

---

## 8) Ghi chú trước khi sang Giai đoạn 2

Định hướng kỹ thuật hiện tại:
- Frontend: SPA React.
- Lưu trữ local: IndexedDB (Dexie.js).
- ML phù hợp bằng Python (khả năng tách ML service FastAPI nếu cần).

Phần kiến trúc hệ thống chi tiết (module, API contract, schema, trade-off stack) sẽ được đặc tả ở **Giai đoạn 2**.