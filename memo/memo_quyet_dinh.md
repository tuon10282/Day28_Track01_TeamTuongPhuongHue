# Memo Quyết Định — Dashboard Hành Động v1

**Nhóm:** Tường – Phương – Huế | **Track 01 – Day 28**
**Ngày:** 2026-09-03 | **Giai đoạn:** Checkpoint phút 80

---

## 1. Phạm vi đã khoá

| Hạng mục | Nội dung |
|---|---|
| **Product** | Trợ lý AI tích hợp tra cứu đa nguồn (kho tri thức nội bộ + chính sách đổi trả + lịch sử ticket) |
| **User** | Nhân viên Chăm sóc Khách hàng (CSKH) |
| **Workflow** | Tiếp nhận ticket → Tra cứu hệ thống → Tóm tắt & Đề xuất phương án → Kiểm duyệt & Thực thi |
| **Problem** | Nhân viên mất thời gian nhảy giữa nhiều hệ thống + mất niềm tin vào AI do trích xuất sai → quay lại thủ công hoàn toàn |

---

## 2. Nguyên nhân gốc đã xác nhận

| # | Nguyên nhân | Framework | Bằng chứng |
|---|---|---|---|
| 1 | **Độ tin cậy & Dữ liệu**: Dữ liệu nguồn thiếu người phụ trách · Không có trích nguồn · Không có cách báo lỗi | Gartner-Lite (Readiness THIẾU) | Quan sát trực tiếp: kết quả AI trích xuất lệch ngữ cảnh → nhân viên bỏ qua AI |
| 2 | **ADKAR – Desire/Knowledge**: Nhân viên e ngại sai sót · Chưa biết cách đối chiếu nguồn | ADKAR (Desire NGHẼN + Knowledge NGHẼN) | Nhân viên chọn tra thủ công dù AI có sẵn |

---

## 3. Quyết định thiết kế workflow TO-BE

**Ba thay đổi không thể thiếu:**
1. Mọi câu trả lời AI **phải trích nguồn** (tên tài liệu + ngày cập nhật)
2. **Data Owner được chỉ định** cho từng nguồn tài liệu — có lịch review định kỳ
3. **Nút "Báo sai"** tích hợp trực tiếp trong workflow → log lỗi → Data Owner xử lý

**Lý do không mặc định giải bằng đào tạo:**
Training là chưa đủ khi nguyên nhân gốc nằm ở Readiness (dữ liệu) và Absorption (cơ chế phản hồi lỗi). Phải sửa hệ thống trước, đào tạo song song.

---

## 4. Dashboard Hành Động v1 — Quyết định đo lường

| Tầng | Chỉ số | Mốc đầu | Mục tiêu | Nguồn dữ liệu | Phụ trách | Khi chỉ số xấu |
|---|---|---|---|---|---|---|
| **Sử dụng** | Tỷ lệ ticket được xử lý qua workflow AI (không bỏ qua bước AI) | Đo tuần 1 pilot | ≥70% ticket qua đủ workflow | Log hệ thống AI | Trưởng nhóm CSKH | Phỏng vấn nhanh → tìm điểm vướng cụ thể |
| **Hành vi** | Tỷ lệ nhân viên kiểm tra nguồn trích dẫn trước khi dùng | 0% (chưa có tính năng) | ≥80% sau khi bật trích nguồn | Log click vào nguồn tài liệu | Trưởng nhóm CSKH | Review lại UX hiển thị nguồn |
| **Năng suất** | Thời gian trung bình xử lý 1 ticket (từ tiếp nhận đến gửi phản hồi) | Đo baseline tuần 1 | Giảm ≥20% so với baseline | Log timestamp hệ thống ticket | Chủ quy trình CSKH | Xem lại bước nào chưa được AI hỗ trợ |
| **Chất lượng & Tin cậy** | Tỷ lệ câu trả lời AI bị báo sai / tổng câu trả lời AI | 0 (chưa có cơ chế) | <5% báo sai/tuần sau tháng 2 | Log nút "Báo sai" | Data Owner | Tăng tần suất QA mẫu · Review nguồn dữ liệu |
| **Giá trị** | Tỷ lệ ticket được giải quyết không cần leo thang lên cấp trên | Đo baseline tuần 1 | Tăng ≥15% so với baseline | Hệ thống CRM (trường escalation) | Chủ nghiệp vụ | Điều chỉnh phạm vi AI · Tăng hỗ trợ Knowledge |

---

## 5. Lộ trình — Cổng quyết định

| Cổng | Điều kiện thông qua | Hành động nếu không đạt |
|---|---|---|
| **Cổng 30 ngày** | ≥80% câu trả lời có trích nguồn · Mốc baseline đã ghi đủ | Xem lại tính năng trích nguồn · Kiểm tra Data Owner đã vào vị trí chưa |
| **Cổng 60 ngày** | Tra cứu thủ công giảm ≥30% · Làm lại <20% · ≥3 báo lỗi được xử lý | Tăng cường buổi đồng hành · Review lại nguồn dữ liệu |
| **Cổng 90 ngày** | Thời gian ticket giảm ≥20% · Tin tưởng AI ≥3.5/5 | Quyết định: điều chỉnh phạm vi hoặc dừng rollout |

---

## 6. Quyết định cuối — Trước khi nộp

| Câu hỏi | Quyết định của nhóm |
|---|---|
| Có rollout rộng ngay không? | **Không** — pilot 1 nhóm ~5 người trước, chờ cổng 30 ngày |
| Ưu tiên sửa gì đầu tiên? | **Trích nguồn + chỉ định Data Owner** — trước khi làm bất cứ đào tạo nào |
| Đào tạo bao giờ? | Song song từ tuần 2 — chỉ sau khi tính năng trích nguồn hoạt động |
| Chỉ số nào quyết định mở rộng? | Tỷ lệ làm lại <20% + thời gian ticket giảm ≥20% (cổng 60 và 90 ngày) |

---

*Memo này là đầu ra Checkpoint phút 80 — Dashboard v1. Bản v2 sẽ được hoàn thiện sau kiểm tra chéo.*
