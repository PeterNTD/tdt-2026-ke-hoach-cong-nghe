# KẾ HOẠCH THỬ NGHIỆM CHATBOT TELEGRAM KẾT NỐI Trung tâm dữ liệu CHO PROJECT TDT 2026

## 1. Mục tiêu

Xây dựng bản thử nghiệm chatbot trên Telegram để truy cập và hỏi đáp kho dữ liệu TDT 2026 đã được tạo riêng trên Trung tâm dữ liệu.

Chatbot giúp người dùng hỏi nhanh các nội dung liên quan đến:

- 6 lĩnh vực trọng tâm công nghệ TDT 2026.
- Danh mục 27 dự án công nghệ đề xuất.
- Ngân sách sơ bộ năm 2026.
- KPI chi tiết.
- Tiến độ triển khai 06–12/2026.
- Tài liệu nguồn/QĐ thành lập Ban dự án AI.
- Các tài liệu trình bày, mindmap, sơ đồ và báo cáo liên quan.

Mục tiêu của bản thử nghiệm là kiểm chứng:

- Trung tâm dữ liệu có trả lời tốt trên bộ tài liệu TDT hay không.
- Chất lượng câu trả lời có đủ tin cậy để phục vụ lãnh đạo/đội dự án hay không.
- Telegram có phù hợp làm kênh hỏi đáp nhanh hay không.
- Cần bổ sung dữ liệu, phân quyền, giao diện hoặc cơ chế kiểm soát nào trước khi mở rộng.

---

## 2. Phạm vi thử nghiệm

### 2.1. Kênh sử dụng

- Kênh thử nghiệm: Telegram chat.
- Đối tượng thử nghiệm ban đầu: anh Dũng và nhóm nội bộ được chỉ định.
- Không mở công khai ra ngoài khi chưa có phê duyệt.

### 2.2. Kho dữ liệu sử dụng

Trung tâm dữ liệu hiện có:

- Tên notebook: `TDT 2026 - Ke hoach cong nghe`
- Notebook ID hiện ghi nhận: `5e8e5452-514d-4565-90d8-bd2876ccf5b4`

Các tài liệu cần đưa vào/đồng bộ với Trung tâm dữ liệu:

| Nhóm | Tài liệu |
|---|---|
| Kế hoạch chính | `tdt-2026/01-ke-hoach-chinh/muc-2-linh-vuc-trong-tam-tdt-2026.md` |
| Kế hoạch triển khai | `tdt-2026/01-ke-hoach-chinh/bang-ke-hoach-muc-2-linh-vuc-trong-tam-tdt-2026.md` |
| Thực thi chi tiết | `tdt-2026/01-ke-hoach-chinh/ke-hoach-thuc-thi-sau-cho-tung-hang-muc-tdt-2026.md` |
| Danh mục dự án | `tdt-2026/02-du-an-kpi-ngan-sach/danh-muc-du-an-cong-nghe-2026-theo-6-linh-vuc-tdt.md` |
| Ngân sách | `tdt-2026/02-du-an-kpi-ngan-sach/ngan-sach-du-an-cong-nghe-2026-tdt.md` |
| KPI | `tdt-2026/02-du-an-kpi-ngan-sach/kpi-chi-tiet-muc-2-linh-vuc-trong-tam-tdt-2026.md` |
| Tiến độ | `tdt-2026/03-tien-do/bang-tien-do-trien-khai-06-12-2026-tdt.md` |
| Tài liệu nguồn | `tdt-2026/06-tai-lieu-nguon/22_05_26_TDT_QD_Thanh_lap_BDA_AI_quản_trị_doanh_nghiệp_rv5.docx` |

### 2.3. Loại câu hỏi hỗ trợ

Chatbot thử nghiệm cần hỗ trợ các nhóm câu hỏi:

1. **Tra cứu thông tin**
   - “27 dự án công nghệ gồm những gì?”
   - “Ngân sách trung bình cho nhóm AI là bao nhiêu?”
   - “Tiến độ tháng 8/2026 có những việc gì?”

2. **Tóm tắt tài liệu**
   - “Tóm tắt kế hoạch công nghệ 2026 trong 10 dòng.”
   - “Tóm tắt QĐ thành lập BDA AI.”

3. **So sánh/phân tích**
   - “So sánh nhóm Nền tảng số và AI điều hành thông minh.”
   - “Dự án nào nên ưu tiên triển khai trước?”

4. **Hỗ trợ báo cáo**
   - “Viết báo cáo ngắn về ngân sách 2026.”
   - “Soạn nội dung trình lãnh đạo về 6 lĩnh vực trọng tâm.”

5. **Truy vấn theo tiêu chí**
   - “Liệt kê các dự án có thời gian triển khai tháng 6–9/2026.”
   - “Dự án nào có ngân sách cao nhất?”

---

## 3. Kiến trúc thử nghiệm

### 3.1. Luồng tổng thể

```text
Người dùng hỏi trên Telegram
→ Telegram Bot nhận tin nhắn
→ Gateway/script xử lý câu hỏi
→ Gửi câu hỏi đến Trung tâm dữ liệu TDT
→ Trung tâm dữ liệu trả lời dựa trên nguồn tài liệu
→ Bot chuẩn hóa câu trả lời
→ Trả kết quả về Telegram
```

### 3.2. Thành phần kỹ thuật

| Thành phần | Vai trò |
|---|---|
| Telegram Bot | Kênh nhận câu hỏi và trả lời người dùng. |
| Python handler | Xử lý tin nhắn, gọi CLI/API Trung tâm dữ liệu, định dạng kết quả. |
| `Trung tâm dữ liệu` | Công cụ kết nối Trung tâm dữ liệu. |
| Trung tâm dữ liệu TDT | Kho dữ liệu đã nạp tài liệu nguồn. |
| Log thử nghiệm | Lưu câu hỏi, thời gian, trạng thái, lỗi, đánh giá chất lượng. |

### 3.3. Lệnh Trung tâm dữ liệu dự kiến

Dùng CLI đã xác thực:

```bash
python -m notebooklm ask <notebook_id> "<câu hỏi>" --json
```

Trong đó:

- `<notebook_id>`: ID notebook TDT.
- `<câu hỏi>`: câu hỏi người dùng gửi từ Telegram.
- `--json`: ưu tiên lấy output có cấu trúc để xử lý lại trước khi trả lời.

---

## 4. Phân quyền và bảo mật

### 4.1. Nguyên tắc

- Chỉ cho phép danh sách Telegram user ID được phê duyệt sử dụng bot.
- Không trả lời nếu user không nằm trong allowlist.
- Không đưa tài liệu nhạy cảm ra ngoài nhóm được phép.
- Không tự ý upload thêm tài liệu mới lên Trung tâm dữ liệu nếu chưa được phê duyệt.
- Không lưu thông tin nhạy cảm trong log dạng plaintext nếu không cần thiết.

### 4.2. Allowlist đề xuất

Ban đầu chỉ cho phép:

| Người dùng | Telegram ID | Quyền |
|---|---:|---|
| Anh Dũng | `307152071` | Hỏi đáp, kiểm thử, yêu cầu tóm tắt |

Có thể bổ sung người dùng sau khi anh Dũng duyệt.

### 4.3. Câu trả lời cho user không được phép

Nếu user không thuộc allowlist, bot trả lời:

```text
Bạn chưa được cấp quyền truy cập chatbot TDT 2026. Vui lòng liên hệ quản trị dự án để được phân quyền.
```

---

## 5. Tính năng bản thử nghiệm

### 5.1. Tính năng bắt buộc

| STT | Tính năng | Mô tả | Trạng thái |
|---:|---|---|---|
| 1 | Nhận câu hỏi Telegram | Bot nhận tin nhắn text từ user được phép. | Cần làm |
| 2 | Gọi Trung tâm dữ liệu | Gửi câu hỏi vào notebook TDT và nhận câu trả lời. | Cần làm |
| 3 | Trả lời Telegram | Bot trả nội dung đã định dạng lại cho người dùng. | Cần làm |
| 4 | Allowlist user | Chỉ user được phép mới hỏi được. | Cần làm |
| 5 | Log câu hỏi/lỗi | Ghi lại câu hỏi, thời gian, trạng thái để đánh giá. | Cần làm |
| 6 | Timeout/fallback | Nếu Trung tâm dữ liệu lỗi hoặc quá lâu, bot báo lỗi rõ ràng. | Cần làm |

### 5.2. Tính năng nên có

| STT | Tính năng | Mô tả |
|---:|---|---|
| 1 | Lệnh `/help` | Hướng dẫn cách hỏi và ví dụ câu hỏi. |
| 2 | Lệnh `/sources` | Liệt kê nhóm tài liệu đang có trong notebook. |
| 3 | Lệnh `/status` | Kiểm tra trạng thái bot và Trung tâm dữ liệu auth. |
| 4 | Lệnh `/summary` | Tóm tắt nhanh toàn bộ project TDT 2026. |
| 5 | Lệnh `/budget` | Hỏi nhanh ngân sách 3 mức. |
| 6 | Lệnh `/projects` | Liệt kê 27 dự án. |

---

## 6. Kịch bản sử dụng thử nghiệm

### 6.1. Kịch bản 1 — Hỏi danh mục dự án

**User hỏi:**

```text
27 dự án công nghệ TDT 2026 gồm những gì?
```

**Bot cần trả lời:**

- Liệt kê theo 6 lĩnh vực.
- Có thể tóm gọn nếu quá dài.
- Nếu Trung tâm dữ liệu có citation thì giữ lại phần nguồn/chỉ dẫn tài liệu.

### 6.2. Kịch bản 2 — Hỏi ngân sách

**User hỏi:**

```text
Ngân sách 2026 có mấy kịch bản và tổng tiền là bao nhiêu?
```

**Bot cần trả lời:**

- Mức thấp: 5,51 tỷ VND.
- Mức trung bình: 16,23 tỷ VND.
- Mức cao: 37,55 tỷ VND.
- Nêu rõ đây là dự toán sơ bộ, chưa phải báo giá chốt.

### 6.3. Kịch bản 3 — Tóm tắt QĐ thành lập BDA AI

**User hỏi:**

```text
Tóm tắt QĐ thành lập BDA AI cho anh trong 10 gạch đầu dòng.
```

**Bot cần trả lời:**

- Tóm tắt ngắn gọn.
- Không bịa nội dung nếu Trung tâm dữ liệu không tìm thấy nguồn.
- Nếu chưa nạp file QĐ vào Trung tâm dữ liệu thì báo cần đồng bộ nguồn trước.

### 6.4. Kịch bản 4 — Hỏi ưu tiên triển khai

**User hỏi:**

```text
Nên ưu tiên 5-7 dự án nào trong giai đoạn 1?
```

**Bot cần trả lời:**

- Gợi ý dự án nền tảng trước.
- Nêu lý do ngắn gọn.
- Phân biệt rõ đây là đề xuất phân tích, không phải quyết định phê duyệt.

---

## 7. Tiêu chí nghiệm thu bản thử nghiệm

Bản thử nghiệm được xem là đạt nếu đáp ứng tối thiểu:

| Nhóm tiêu chí | Điều kiện đạt |
|---|---|
| Kết nối | Bot nhận được câu hỏi Telegram và gọi được Trung tâm dữ liệu. |
| Trả lời | Bot trả lời được tối thiểu 10 câu hỏi thử nghiệm về TDT 2026. |
| Độ đúng | Tối thiểu 8/10 câu trả lời đúng hoặc chấp nhận được so với tài liệu nguồn. |
| Bảo mật | User ngoài allowlist không sử dụng được bot. |
| Ổn định | Có timeout/fallback khi Trung tâm dữ liệu lỗi hoặc phản hồi chậm. |
| Log | Có log câu hỏi, thời gian, trạng thái và lỗi. |
| Trải nghiệm | Câu trả lời dễ đọc trên Telegram, không quá dài, có chia đoạn/gạch đầu dòng. |

---

## 8. Lộ trình triển khai thử nghiệm

### Giai đoạn 1 — Chuẩn bị dữ liệu và xác thực

Thời lượng dự kiến: 0,5 ngày.

Công việc:

1. Kiểm tra lại Trung tâm dữ liệu auth.
2. Kiểm tra notebook TDT hiện có.
3. Đảm bảo các tài liệu TDT mới nhất đã được nạp hoặc cập nhật.
4. Test lệnh hỏi đáp trực tiếp bằng CLI.
5. Ghi nhận notebook ID và danh sách source đang dùng.

Đầu ra:

- Notebook TDT sẵn sàng.
- CLI hỏi đáp hoạt động.
- Có danh sách tài liệu nguồn đã nạp.

### Giai đoạn 2 — Xây Telegram bot handler

Thời lượng dự kiến: 0,5–1 ngày.

Công việc:

1. Tạo script nhận/định tuyến câu hỏi Telegram hoặc tích hợp với cơ chế OpenClaw hiện có.
2. Thêm allowlist user ID.
3. Gọi `python -m notebooklm ask` từ handler.
4. Chuẩn hóa câu trả lời.
5. Trả kết quả về Telegram.
6. Thêm timeout và thông báo lỗi.

Đầu ra:

- Bot trả lời được câu hỏi từ Telegram.
- User không có quyền bị chặn.
- Có log câu hỏi/lỗi.

### Giai đoạn 3 — Kiểm thử 10–20 câu hỏi mẫu

Thời lượng dự kiến: 0,5 ngày.

Công việc:

1. Chuẩn bị bộ câu hỏi mẫu.
2. Test các nhóm câu hỏi: dự án, ngân sách, KPI, tiến độ, QĐ, tóm tắt.
3. Chấm điểm độ đúng/dễ hiểu.
4. Ghi lỗi và câu trả lời chưa đạt.
5. Điều chỉnh prompt hệ thống/format trả lời nếu cần.

Đầu ra:

- Báo cáo kiểm thử.
- Danh sách lỗi/cải tiến.
- Kết luận có nên mở rộng không.

---

## 9. Cấu trúc thư mục đề xuất

```text
tdt-2026/
  07-chatbot-Trung tâm dữ liệu/
    ke-hoach-thu-nghiem-chatbot-telegram-Trung tâm dữ liệu-tdt.md
    config.example.json
    chatbot_telegram_Trung tâm dữ liệu.py
    logs/
      .gitkeep
    tests/
      cau-hoi-mau.md
      ket-qua-test.md
```

---

## 10. Cấu hình mẫu

File đề xuất: `config.example.json`

```json
{
  "Trung tâm dữ liệu": {
    "notebook_id": "5e8e5452-514d-4565-90d8-bd2876ccf5b4",
    "python_command": "python",
    "timeout_seconds": 120
  },
  "telegram": {
    "allowed_user_ids": [307152071],
    "reply_max_chars": 3500
  },
  "logging": {
    "enabled": true,
    "log_file": "tdt-2026/07-chatbot-Trung tâm dữ liệu/logs/chatbot.log"
  }
}
```

---

## 11. Prompt định hướng trả lời cho chatbot

Prompt định hướng nên dùng trước khi gửi câu hỏi vào Trung tâm dữ liệu hoặc khi xử lý câu trả lời:

```text
Bạn là chatbot hỗ trợ tra cứu kế hoạch công nghệ TDT 2026. 
Chỉ trả lời dựa trên tài liệu nguồn trong Trung tâm dữ liệu. 
Nếu không tìm thấy thông tin, nói rõ là chưa có trong tài liệu nguồn, không bịa.
Trả lời bằng tiếng Việt, ngắn gọn, có cấu trúc bullet khi phù hợp.
Khi nội dung liên quan ngân sách, nhắc rõ đây là dự toán sơ bộ nếu tài liệu nguồn thể hiện như vậy.
Khi nội dung là đề xuất ưu tiên, phân biệt rõ giữa dữ kiện tài liệu và khuyến nghị phân tích.
```

---

## 12. Rủi ro và biện pháp kiểm soát

| Rủi ro | Ảnh hưởng | Biện pháp kiểm soát |
|---|---|---|
| Trung tâm dữ liệu mất phiên đăng nhập | Bot không trả lời được | Có lệnh kiểm tra auth; hướng dẫn login lại. |
| Trung tâm dữ liệu trả lời thiếu nguồn | Giảm độ tin cậy | Yêu cầu bot nói rõ khi thiếu nguồn; test câu hỏi mẫu. |
| Dữ liệu Trung tâm dữ liệu chưa cập nhật | Trả lời theo tài liệu cũ | Có quy trình đồng bộ source trước khi test. |
| User không được phép truy cập | Rò rỉ thông tin | Allowlist Telegram ID. |
| Câu trả lời quá dài | Khó đọc trên Telegram | Giới hạn độ dài, tóm tắt, chia bullet. |
| Phụ thuộc dịch vụ bên ngoài | Gián đoạn khi Google/Trung tâm dữ liệu lỗi | Có fallback báo lỗi; cân nhắc RAG nội bộ giai đoạn sau. |

---

## 13. Kết luận đề xuất

Nên triển khai bản thử nghiệm Telegram chatbot kết nối Trung tâm dữ liệu theo phạm vi nhỏ trước, chỉ cho user được phép sử dụng. Nếu kết quả hỏi đáp đạt yêu cầu, có thể mở rộng thành web chat nội bộ hoặc chuyển sang hệ thống RAG riêng để chủ động hơn về dữ liệu, phân quyền và vận hành lâu dài.
