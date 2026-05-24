# Chatbot Telegram ↔ Trung tâm dữ liệu cho TDT 2026

POC bot Telegram local để hỏi đáp bộ tài liệu `TDT 2026 - Kế hoạch công nghệ` qua Trung tâm dữ liệu.

## Chạy thử

```powershell
cd C:\Users\tdt\.openclaw\workspace\tdt-2026\07-chatbot-notebooklm
python -m pip install -r requirements.txt
copy .env.example .env
# sửa TELEGRAM_BOT_TOKEN trong .env
python bot.py
```

## Biến môi trường

- `TELEGRAM_BOT_TOKEN`: token bot Telegram, không commit.
- `NOTEBOOK_ID`: notebook ID Trung tâm dữ liệu.
- `ALLOWED_TELEGRAM_USER_IDS`: danh sách Telegram user id được phép dùng, phân tách bằng dấu phẩy.

## Lệnh bot

- `/start`: giới thiệu bot.
- `/help`: câu hỏi mẫu.
- Câu hỏi thường: bot gửi sang Trung tâm dữ liệu và trả lời lại Telegram.

## Log

Log JSONL lưu tại:

```text
logs/chatbot-YYYY-MM-DD.jsonl
```

Log gồm câu hỏi, câu trả lời, latency, số citation và trạng thái lỗi/thành công.

## Ghi chú bảo mật

- `.env` đã được ignore.
- Không đưa Telegram token vào GitHub.
- Bot đang giới hạn user qua allowlist.
