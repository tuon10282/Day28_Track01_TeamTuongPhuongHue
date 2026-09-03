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

