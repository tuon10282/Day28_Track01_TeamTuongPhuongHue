# Day28_Track01_TeamTuongPhuongHue

> Tối ưu hóa vận hành Chăm sóc Khách hàng với Trợ lý AI tích hợp tra cứu đa nguồn

## 👥 Thành viên nhóm

Dự án được thực hiện bởi nhóm thành viên:

| STT | Họ và Tên | Mã học viên |
| :---: | :--- | :---: |
| 1 | **Cao Các Tường** | 2A202601236 |
| 2 | **Đinh Lê Quỳnh Phương** | 2A202601865 |
| 3 | **Lăng Thị Phương Huế** | 2A202601915 |

## 📌 1. Giới thiệu dự án

- **Product:** Trợ lý AI tích hợp tra cứu đa nguồn (kho tri thức nội bộ, chính sách đổi trả & lịch sử ticket cũ) và hỗ trợ vận hành CSKH.

- **User:** Nhân viên Chăm sóc Khách hàng (CSKH).

- **Workflow:** Tiếp nhận ticket → Tra cứu hệ thống (chính sách + lịch sử) → Tóm tắt vấn đề cốt lõi & Đề xuất phương án xử lý/Soạn email → Kiểm duyệt & Thực thi.

- **Problem:** Nhân viên mất quá nhiều thời gian nhảy qua lại giữa nhiều hệ thống (CRM, file quy chế cũ) và dữ liệu tra cứu tự động thỉnh thoảng bị lỗi trích xuất sai, khiến họ mất lòng tin và tự tra cứu thủ công hoàn toàn.

## 📌 2. Chẩn đoán trước khi chọn giải pháp

### 2.1. Đánh giá Gartner-Lite

- **Direction (Hướng đi):** `ĐẠT` — Mục tiêu tối ưu hóa thời gian xử lý ticket cho khối CSKH đã rõ ràng.

- **Readiness (Sẵn sàng):** `THIẾU` — Kho tài liệu quy chế, chính sách đổi trả và lịch sử ticket nằm phân tán ở nhiều hệ thống rời rạc; chưa có người chịu trách nhiệm chính cập nhật dữ liệu.

- **Absorption (Hấp thụ):** `THIẾU` — Thiếu cơ chế phản hồi lỗi khi thông tin tra cứu tự động bị sai lệch, khiến nhân viên không có cách nào báo cáo để hệ thống cải thiện.

### 2.2. Phân chia Mollick

- **AI hỗ trợ:** Tự động tìm kiếm, gom nhóm dữ liệu cũ, tóm tắt tình trạng khách hàng và đưa ra gợi ý phản hồi ban đầu.

- **Người làm (Giữ quyền quyết định):** Nhân viên CSKH bắt buộc phải rà soát lại kết quả, đối chiếu quy định thực tế và tự quyết định phương án giao tiếp cuối cùng với khách hàng.

### 2.3. Điểm nghẽn ADKAR

- **Desire (Mong muốn):** `NGHẼN` — Nhân viên có tâm lý e ngại, sợ sai sót khi dùng thông tin tra cứu tự động nên chọn cách làm thủ công quen thuộc để an toàn.

- **Knowledge (Kiến thức):** `NGHẼN` — Thiếu kỹ năng kết hợp thông tin gợi ý với bối cảnh thực tế của từng khách hàng.

### 2.4. Bằng chứng thực tế

Quan sát trực tiếp workflow của nhóm CSKH cho thấy nhân viên liên tục phải bật qua lại giữa file quy chế cũ trên Drive và hệ thống CRM, đồng thời thường xuyên gặp tình trạng kết quả tra cứu tự động trích xuất lệch ngữ cảnh, dẫn đến việc họ tự tra cứu thủ công hoàn toàn.

### 2.5. Kết luận nguyên nhân gốc

- **Nguyên nhân gốc 1 (Độ tin cậy & Dữ liệu):** Dữ liệu nguồn thiếu người phụ trách cập nhật và hệ thống tra cứu không có cơ chế trích nguồn, kiểm tra mẫu hay báo lỗi.

- **Nguyên nhân gốc 2 (ADKAR - Desire/Knowledge):** Nhân viên thiếu niềm tin và kỹ năng đối chiếu, dẫn đến tâm lý e ngại và quay lại cách làm thủ công.

---

## 📌 3. Thiết kế cách làm mới (AS-IS → TO-BE)

### 3.1. Sơ đồ AS-IS / TO-BE

| TRƯỚC (AS-IS) | SAU (TO-BE) |
|---|---|
| Nhận ticket → bật qua CRM tra lịch sử thủ công | Nhận ticket → AI tự động tổng hợp lịch sử từ CRM + kho tri thức |
| Tìm chính sách đổi trả → mở file Drive (không rõ bản mới nhất) | AI gợi ý chính sách liên quan + hiển thị **nguồn + ngày cập nhật** |
| Hỏi đồng nghiệp có kinh nghiệm khi không chắc | Nhân viên **kiểm tra nguồn trích dẫn**, tự quyết định → không phụ thuộc người |
| Soạn email/phản hồi từ đầu mỗi lần | AI soạn bản nháp → Nhân viên **rà soát & hiệu chỉnh** theo bối cảnh thực tế |
| Phát hiện sai sót sau khi gửi hoặc bị khách hàng phản hồi | Bước kiểm duyệt bắt buộc trước khi gửi + cơ chế **báo lỗi trích xuất** |
| Không rõ ai chịu trách nhiệm khi dữ liệu cũ/sai | **Data owner được chỉ định** → cập nhật định kỳ + có lịch review |

### 3.2. Ba thay đổi bắt buộc

| # | Thay đổi | Lý do (gắn nguyên nhân gốc) |
|---|---|---|
| 1 | **Nguồn kiểm chứng rõ ràng** — mọi câu trả lời AI phải hiển thị nguồn tài liệu + ngày cập nhật | Nguyên nhân gốc 1: dữ liệu thiếu người phụ trách, hệ thống không trích nguồn |
| 2 | **Người chịu trách nhiệm** — chỉ định Data Owner cho từng nguồn tài liệu (chính sách, quy chế, lịch sử ticket) | Nguyên nhân gốc 1: không ai cập nhật → nhân viên mất niềm tin |
| 3 | **Cơ chế xử lý khi AI không chắc chắn** — nút "Báo sai" trực tiếp trong workflow + quy trình chuyển người khi độ tin cậy thấp | Nguyên nhân gốc 2: nhân viên không có cách báo lỗi → tích lũy mất tin tưởng |

### 3.3. Phân chia công việc Người–AI (Mollick)

| Vùng | Nội dung cụ thể |
|---|---|
| 🧑 **Người làm** (giữ quyền quyết định) | Phê duyệt phương án xử lý cuối cùng · Hiệu chỉnh email/phản hồi theo bối cảnh cụ thể · Chịu trách nhiệm với khách hàng |
| 🤝 **AI hỗ trợ** (AI làm, người kiểm tra) | Tổng hợp lịch sử ticket · Tra cứu chính sách liên quan + trích nguồn · Soạn bản nháp phản hồi · Gợi ý phương án xử lý |
| ⚙️ **AI tự động** (chỉ với tác vụ rõ, rủi ro thấp) | Phân loại sơ bộ ticket theo danh mục · Gắn tag ưu tiên dựa trên SLA · Cảnh báo ticket quá hạn |

### 3.4. Kiến trúc tin cậy

```
Kho tài liệu (có Data Owner + lịch cập nhật)
    ↓
AI tra cứu → Trích nguồn tự động (tên tài liệu + ngày)
    ↓
Nhân viên CSKH → Kiểm tra nguồn + ra quyết định
    ↓
[Nếu AI không chắc] → Cảnh báo rõ → Chuyển người / tra thủ công
    ↓
Nút "Báo sai" → Log lỗi → Data Owner review định kỳ → Cải thiện kho dữ liệu
```

---

## 📌 4. Lộ trình 30–60–90 Ngày

> Mỗi giai đoạn là **cổng quyết định** — chỉ mở rộng khi đạt đủ điều kiện chất lượng, không phải khi hết thời gian.

### 4.1. Bảng lộ trình

| Hạng mục | 0–30 ngày *(Chứng minh vấn đề)* | 31–60 ngày *(Chứng minh chất lượng)* | 61–90 ngày *(Quyết định mở rộng)* |
|---|---|---|---|
| **Mục tiêu cổng** | Xác nhận workflow TO-BE hoạt động với nhóm pilot nhỏ | Xác nhận chất lượng đầu ra và hành vi người dùng thay đổi | Quyết định: mở rộng / điều chỉnh / dừng |
| **Hành động chính** | Vẽ AS-IS/TO-BE · Khoá phạm vi pilot (1 nhóm ~5 người CSKH) · Chỉ định Data Owner cho 2 nguồn ưu tiên (chính sách đổi trả + lịch sử ticket 6 tháng) · Bật tính năng trích nguồn · Ghi mốc ban đầu | Triển khai nút "Báo sai" · QA mẫu 20% câu trả lời/tuần · Tổ chức 2 buổi thực hành (Knowledge + Ability theo ADKAR) · Theo dõi tỷ lệ làm lại | So sánh với mốc ban đầu · Chốt owner vận hành dài hạn · Kiểm tra governance (quyền truy cập, phạm vi tài liệu) · Quyết định rollout toàn bộ khối CSKH |
| **Owner** | Trưởng nhóm CSKH + IT | Trưởng nhóm CSKH + Data Owner | Ban quản lý + Trưởng nhóm CSKH |
| **Dấu hiệu hoàn thành cổng** | ≥80% câu trả lời AI có trích nguồn · Mốc ban đầu đã ghi đủ 5 chỉ số dashboard | Tỷ lệ tra cứu thủ công giảm ≥30% · Tỷ lệ làm lại sau QA <20% · ≥3 báo lỗi được xử lý thành công | Thời gian xử lý ticket giảm ≥20% so với mốc · Nhân viên pilot đánh giá tin tưởng AI ≥3.5/5 |

### 4.2. Xử lý điểm nghẽn ADKAR theo lộ trình

| ADKAR | Tuần | Hành động cụ thể |
|---|---|---|
| **Awareness** | Tuần 1 | Họp kick-off 30': giải thích "tại sao thay đổi" — không phải thay người, mà giảm thời gian nhảy hệ thống |
| **Desire** | Tuần 1–2 | Demo trực tiếp: AI tìm đúng nguồn, trích nguồn rõ → giảm nỗi lo "sợ sai" · Gắn mục tiêu cá nhân (giảm giờ tăng ca cuối ngày) |
| **Knowledge** | Tuần 2–4 | Hướng dẫn 2 kỹ năng: (1) cách đọc trích nguồn để kiểm tra độ tin cậy; (2) cách báo lỗi khi kết quả lệch ngữ cảnh |
| **Ability** | Tuần 3–6 | Thực hành trong ticket thật (có người dẫn dắt tuần 3–4) · Đánh giá lại tuần 6: ai cần thêm hỗ trợ |
| **Reinforcement** | Tuần 7–12 | Chia sẻ case tốt hàng tuần trong nhóm · Trưởng nhóm review dashboard mỗi 2 tuần · Data Owner thông báo khi cập nhật tài liệu mới |

---


