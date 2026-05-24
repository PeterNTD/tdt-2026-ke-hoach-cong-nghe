# Kết quả test Trung tâm dữ liệu - TDT 2026

Thời điểm test: 2026-05-24 21:xx GMT+7
Notebook ID: `5e8e5452-514d-4565-90d8-bd2876ccf5b4`

## 1. Auth

Kết quả: PASS

- `python -m notebooklm auth check --test --json` chạy thành công.
- Có cookie Google/Trung tâm dữ liệu hợp lệ.
- Có CSRF và session id.

## 2. Test câu hỏi

### Câu 1
**Hỏi:** TDT 2026 có bao nhiêu lĩnh vực trọng tâm? Liệt kê ngắn gọn.

**Kết quả:** PASS

- Trả lời đúng: 6 lĩnh vực trọng tâm.
- Có liệt kê theo nhóm.
- Có citation.

### Câu 2
**Hỏi:** Danh sách dự án ưu tiên giai đoạn đầu của TDT 2026 gồm những dự án nào?

**Kết quả:** PASS một phần

- Trả lời được nhóm dự án khởi động tháng 06/2026.
- Có citation.
- Tuy nhiên câu trả lời hơi rộng, đang diễn giải theo “hạng mục thực hiện chính tháng 06” thay vì đúng nhóm “ưu tiên triển khai trước” trong file danh mục. Khi làm bot nên prompt rõ: nếu hỏi “ưu tiên”, ưu tiên lấy từ mục “Nhóm dự án ưu tiên triển khai trước từ tháng 6/2026”.

### Câu 3
**Hỏi:** Ngân sách trung bình cho kế hoạch công nghệ 2026 là bao nhiêu và phân bổ theo lĩnh vực như thế nào?

**Kết quả:** FAIL về dữ liệu ngân sách

- Trung tâm dữ liệu trả lời rằng tài liệu không có số ngân sách cụ thể.
- Trong project local hiện đã có file ngân sách định lượng, nhưng notebook hiện tại có thể chưa được cập nhật nguồn `ngan-sach-du-an-cong-nghe-2026-tdt.md` bản mới.
- Cần đồng bộ/upload lại nguồn ngân sách vào Trung tâm dữ liệu trước khi dùng bot chính thức.

### Câu 4
**Hỏi:** Tiến độ tháng 06/2026 gồm những hạng mục chính nào?

**Kết quả:** PASS

- Trả lời đúng giai đoạn tháng 06/2026.
- Nhận diện 11 dự án/hạng mục thực hiện chính.
- Có citation.

### Câu 5
**Hỏi:** Trợ lý AI nội bộ TCT TDT có mục tiêu và điều kiện nghiệm thu gì?

**Kết quả:** PASS

- Trả lời đúng mục tiêu, use case, nhóm người dùng thí điểm.
- Nêu KPI nghiệm thu: đúng nguồn >=80%, dùng hằng tuần >=60%, giảm thời gian >=30%, có log/phản hồi.
- Có citation.

## 3. Nhận xét tổng quan

Trung tâm dữ liệu đủ điều kiện để làm chatbot POC, nhưng cần cập nhật nguồn trước khi mở rộng:

1. Upload/cập nhật file ngân sách định lượng mới.
2. Có thể upload thêm file danh mục 27 dự án và tiến độ bản mới nhất nếu chưa đủ.
3. Bot cần prompt guardrail để câu trả lời ngắn hơn, đúng mục hỏi hơn.
4. Cần log câu hỏi/câu trả lời để đánh giá chất lượng.

## 4. Kết luận

Trạng thái: READY FOR BOT POC, với điều kiện cập nhật thêm nguồn ngân sách vào Trung tâm dữ liệu.

Bước kế tiếp khuyến nghị:

1. Đồng bộ nguồn ngân sách mới vào Trung tâm dữ liệu.
2. Viết bot Telegram local tối giản.
3. Test lại 20 câu hỏi mẫu.

## 5. Cập nhật sau khi bổ sung nguồn ngân sách

Sau test ban đầu, đã bổ sung thêm nguồn ngân sách vào Trung tâm dữ liệu bằng file:

- `ngan-sach-du-an-cong-nghe-2026-tdt.md`
- Source ID: `0658e5ec-cd58-4885-8d5a-22715e2514df`
- Status: `ready`

### Retest câu ngân sách

**Hỏi:** Dựa trên nguồn `ngan-sach-du-an-cong-nghe-2026-tdt.md`, ngân sách trung bình cho kế hoạch công nghệ 2026 là bao nhiêu? Nêu phân bổ theo 6 lĩnh vực, trả lời ngắn gọn.

**Kết quả:** PASS

Trung tâm dữ liệu trả lời đúng:

- Tổng mức trung bình: `16.230.000.000 VNĐ`
- Công nghệ đô thị & BĐS tinh khiết: `4.400.000.000 VNĐ`
- Nền tảng số: `3.300.000.000 VNĐ`
- Công nghệ công nghiệp: `3.200.000.000 VNĐ`
- AI & điều hành thông minh: `2.450.000.000 VNĐ`
- Sản phẩm hóa công nghệ & tài sản trí tuệ: `1.580.000.000 VNĐ`
- Công nghệ vật liệu chiến lược: `1.300.000.000 VNĐ`

Kết luận cập nhật: Trung tâm dữ liệu đã đủ nguồn chính để làm chatbot POC.
