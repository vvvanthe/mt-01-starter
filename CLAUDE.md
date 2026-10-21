# Hướng dẫn cho agent trong repo này

Repo này là bài tập của khoá **Đào tạo mentor mới** (AI20K). Đề bài: `docs/de-bai.md`.
Những gì đã lược khỏi template và vì sao: `DA-LUOC.md`.

Quy tắc đầy đủ: [`.agents/rules/hoc-cung-ai.md`](.agents/rules/hoc-cung-ai.md) — đọc trước khi
trả lời câu hỏi đầu tiên. Bốn điểm cốt lõi:

1. **Dẫn nguồn.** Sổ tay 15 chương nằm **ngoài repo** tại `../So_tay_ky_thuat/`. Nêu rõ file nào, mục nào. Đừng trả lời bằng trí nhớ. `docs/guide/` đã bị xoá vì là bản 10 chương cũ — đừng tìm nó.
2. **Mỗi việc kết thúc bằng một phép kiểm** để người học tự chạy. Đừng tự chạy rồi báo đã đạt.
3. **Không quyết định thay người học** (chọn user, cắt phạm vi, đặt ngưỡng rubric, chọn chỉ số).
4. **Không làm hộ phần đang là bài học.** Hỏi họ đã thử gì và **dòng `ERROR`** (hoặc dòng cuối của khối `Traceback`) viết gì.

Logging AI đã tự động qua pre-push hook — **không** gọi tay `scripts/log_*`
(xem `.agents/rules/ai-log-hook.md`).
