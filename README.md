# claude-skill-hau-ky-capcut

Skill Claude Code làm **hậu kỳ** cho video đã cắt dựng thô trong CapCut desktop: thêm chữ, typography, animation, sound effect, cân nhạc, B-roll và chỉnh màu bằng cách ghi thêm lớp vào **bản sao** file dự án. Clip gốc, thứ tự và thời lượng giữ nguyên; dự án vẫn chỉnh tiếp được trong CapCut.

**Trạng thái:** Giai đoạn 0 (cấu trúc repo). Chưa dùng được để hậu kỳ. Lộ trình: `SKILL.md`; kế hoạch: `references/ke-hoach.md`.

## Nguồn gốc

Tách từ [claude-skill-edit-reel-capcut](https://github.com/myduyen939393-afk/claude-skill-edit-reel-capcut) (skill auto-edit-capcut: làm video không lộ mặt rồi dựng timeline CapCut). Repo đó và [claude-skill-edit-reel-digi](https://github.com/myduyen939393-afk/claude-skill-edit-reel-digi) giữ nguyên, không bị sửa.

Thay đổi so với bản gốc:

- Khôi phục cấu trúc `scripts/`, `references/`, `assets/` mà mã nguồn và SKILL.md gốc đòi hỏi (repo gốc đang để mọi file ở thư mục gốc nên đường dẫn trong hướng dẫn bị sai).
- Bỏ phần tạo kịch bản, giọng đọc Higgsfield, ảnh minh hoạ AI.
- Chuyển bộ dựng và bộ xem trước cũ vào `legacy/`, chặn không cho chạy, vì chúng dựng lại toàn bộ timeline.

## Giấy phép

- Font: Be Vietnam Pro, Anton (SIL OFL 1.1, `assets/fonts/OFL.txt`, `LICENSE-BeVietnamPro.txt`); Metropolis (public domain, `LICENSE-Metropolis.txt`).
- Mã nguồn: **chưa xác định**. Repo gốc không có file giấy phép cho phần mã. Cần bổ sung nguồn gốc và giấy phép trước khi công khai.
