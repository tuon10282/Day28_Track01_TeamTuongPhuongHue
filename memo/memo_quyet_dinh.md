# Memo Quyết Định — Dashboard Hành Động v2

> **Ghi chú đo lường:** Baseline ghi ngày 1 của pilot · QA lấy mẫu 20% câu trả lời mỗi tuần · Đo hằng tuần từ log hệ thống · Review dashboard mỗi 2 tuần với trưởng nhóm

**Nhóm:** Tường – Phương – Huế

**Track:** 01 – Day 28

**Ngày:** 2026-09-03

**Phạm vi:** Pilot một nhóm khoảng 5 nhân viên CSKH

---

## 1. Vấn đề và nguyên nhân gốc

### Vấn đề

Nhân viên CSKH mất nhiều thời gian chuyển qua lại giữa CRM, file quy chế trên Drive và các nguồn lịch sử ticket. Khi kết quả tra cứu AI trích xuất lệch ngữ cảnh hoặc không có nguồn rõ ràng, nhân viên mất niềm tin và quay lại tra cứu thủ công.

### Nguyên nhân gốc

| # | Nguyên nhân | Bằng chứng trong workflow |
|---|---|---|
| 1 | **Độ tin cậy và dữ liệu:** Nguồn tài liệu phân tán, chưa có Data Owner, câu trả lời chưa luôn có trích nguồn và chưa có cơ chế báo lỗi. | Quan sát trực tiếp buổi làm việc của 3 nhân viên CSKH (tháng 9/2026): cả 3 đều phải mở song song CRM và file Drive để tra cứu; 2/3 bỏ qua kết quả AI vì trích xuất lệch ngữ cảnh. |
| 2 | **ADKAR – Desire/Knowledge:** Nhân viên e ngại sai sót và chưa biết cách kiểm tra nguồn hoặc báo lỗi. | Cùng buổi quan sát: khi được hỏi, nhân viên nói "không biết câu trả lời AI lấy từ đâu" và "sợ gửi nhầm thông tin cho khách" — chọn tra thủ công để an toàn hơn. |

---

## 2. Framework đã dùng và bằng chứng

| Framework | Kết luận | Cách áp dụng | Bằng chứng |
|---|---|---|---|
| **Gartner-Lite** | Direction đạt; Readiness và Absorption thiếu. | Xác định vấn đề có đáng giải quyết không, dữ liệu đã sẵn sàng chưa và tổ chức có hấp thụ cách làm mới không. | Mục tiêu giảm thời gian xử lý đã rõ, nhưng dữ liệu phân tán và thiếu vòng phản hồi lỗi. |
| **Mollick** | Người giữ quyền quyết định; AI hỗ trợ. | AI tìm kiếm, tổng hợp, trích nguồn và soạn nháp; nhân viên kiểm tra, hiệu chỉnh và phê duyệt. | Workflow TO-BE có bước kiểm tra nguồn và kiểm duyệt bắt buộc trước khi gửi. |
| **ADKAR** | Điểm nghẽn ở Desire và Knowledge. | Demo giá trị, hướng dẫn đọc nguồn, hướng dẫn báo lỗi và thực hành trên ticket thật. | Nhân viên sợ sai và thiếu kỹ năng đối chiếu nên quay lại tra cứu thủ công. |

---

## 3. Thay đổi sau phản biện

| # | Thay đổi trong v2 | Lý do và tác động |
|---|---|---|
| 1 | Bổ sung cột **Cách tính & tần suất** cho từng chỉ số. | Phản biện yêu cầu dữ liệu phải thu thập được trong thực tế; cột này biến mỗi metric thành cách đo cụ thể theo tuần, theo mẫu QA hoặc theo các mốc 1/30/60/90 ngày. |
| 2 | Bổ sung và tách rõ các metric **tỷ lệ tra cứu thủ công**, **mức độ tin tưởng AI** và **báo lỗi được xử lý thành công**. | Các metric này bám trực tiếp các cổng 60–90 ngày trong README, tránh chỉ đo mức sử dụng mà bỏ qua thay đổi hành vi, niềm tin và khả năng cải thiện hệ thống. |
| 3 | Chuẩn hóa ngưỡng nguồn kiểm chứng: `>=80%` ở pilot, mục tiêu ổn định `100%`; QA lấy mẫu `20%` câu trả lời mỗi tuần. | Phân biệt rõ ngưỡng cổng pilot với yêu cầu thiết kế cuối cùng: mọi câu trả lời phải có tên tài liệu và ngày cập nhật. |
| 4 | Thêm sheet **Kiểm tra yêu cầu** trong dashboard v2. | Cho phép đối chiếu trực tiếp 5 yêu cầu tối thiểu của mục 6.4: product metric, workflow metric, baseline/target/nguồn/owner, hành động xử lý và khả năng thu thập dữ liệu. |

---

## 4. Quyết định: tiếp tục có điều kiện

Nhóm quyết định **tiếp tục triển khai pilot**, chưa rollout rộng toàn bộ khối CSKH.

| Quyết định | Nội dung |
|---|---|
| Phạm vi | Một nhóm khoảng 5 nhân viên CSKH, tập trung vào tra cứu chính sách đổi trả và lịch sử ticket 6 tháng. |
| Điều kiện kiểm soát | Nhân viên vẫn giữ quyền quyết định; câu trả lời thiếu nguồn hoặc độ tin cậy thấp phải được cảnh báo và chuyển người. |
| Cổng 30 ngày | ≥70% ticket pilot đi đủ workflow AI · ≥80% câu trả lời có trích nguồn · Baseline ghi đủ ngày 1 *(Đo: log hệ thống AI, tuần 1)* |
| Cổng 60 ngày | Tra cứu thủ công giảm ≥30% · Làm lại sau QA <20% · ≥3 báo lỗi được xử lý *(Đo: log hằng tuần, QA mẫu 20%)* |
| Cổng 90 ngày | Thời gian xử lý giảm ≥20% so với baseline · Tin tưởng AI ≥3.5/5 *(Đo: log timestamp CRM + khảo sát ngắn 5 câu)* |
| Nếu không đạt | Sửa phạm vi, dữ liệu hoặc cách hỗ trợ; chỉ dừng rollout khi các lỗi không được kiểm soát hoặc kết quả nghiệp vụ không cải thiện. |

---

## 5. Lý do, bước tiếp theo và owner

### Lý do

Tiếp tục pilot là lựa chọn phù hợp vì vấn đề có thật và mục tiêu nghiệp vụ rõ, nhưng Readiness và Absorption chưa đủ để triển khai rộng. Dashboard v2 giúp nhóm đo được cả mức dùng, hành vi, năng suất, chất lượng, giá trị và rủi ro trước khi quyết định mở rộng.

### Bước tiếp theo

| Thời điểm | Việc cần làm | Owner |
|---|---|---|
| Tuần 1 | Chốt baseline cho 9 metric; chỉ định Data Owner cho chính sách đổi trả và lịch sử ticket; bật trích nguồn. | Trưởng nhóm CSKH + IT + Data Owner |
| Tuần 2–4 | QA mẫu `20%` mỗi tuần; hướng dẫn đọc nguồn và báo lỗi; ghi nhận các ca phải tra cứu thủ công. | Phụ trách QA + Trưởng nhóm CSKH |
| Ngày 30–60 | Review dashboard mỗi 2 tuần; xử lý báo lỗi; đo tỷ lệ làm lại và mức giảm tra cứu thủ công. | Data Owner + Phụ trách AI |
| Ngày 61–90 | So sánh với baseline, khảo sát mức tin tưởng và quyết định mở rộng, sửa hoặc dừng. | Chủ nghiệp vụ + Ban quản lý |

### Tài liệu bàn giao

- Dashboard v2: `dashboard/dashboard_hanh_dong_v2.xlsx`
- Dashboard v1 để đối chiếu: `v1/dashboard_hanh_dong_v1.xlsx`
- README dự án: `README.md`
