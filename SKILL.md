---
name: hau-ky-capcut
description: Hậu kỳ sáng tạo cho video ĐÃ CẮT DỰNG THÔ trong CapCut desktop (Windows/Mac) bằng cách ghi thêm lớp vào bản sao file dự án, không mở CapCut, không computer use. Thêm text/typography, animation chữ bằng keyframe, sound effect, cân nhạc dưới giọng, B-roll/hình minh hoạ, lớp chỉnh màu; giữ nguyên tuyệt đối clip gốc, thứ tự, thời lượng. Dùng khi người dùng nói "hậu kỳ dự án CapCut", "thêm chữ / SFX / B-roll vào dự án CapCut", "làm đẹp video đã cắt sẵn trong CapCut", hoặc đưa tên một dự án CapCut đã dựng thô kèm ý muốn hoàn thiện. KHÔNG dùng để dựng video từ đầu hay làm video không lộ mặt.
---

# Hậu kỳ CapCut

> **Trạng thái: Giai đoạn 0 xong (cấu trúc repo).** Skill CHƯA dựng được lớp hậu kỳ. Chỉ làm đúng giai đoạn người dùng đã duyệt (bảng "Lộ trình" bên dưới). Gặp yêu cầu thuộc giai đoạn chưa duyệt → báo người dùng, không tự làm.

Trả lời bằng tiếng Việt, dễ hiểu (người dùng không phải dân code). Báo rõ làm được gì, chưa làm được gì, vì sao.

## Luật bất khả xâm phạm

1. **Lớp gốc là vùng cấm.** Không sửa, xoá, dời, đổi thời lượng, đổi tốc độ, thêm keyframe (kể cả zoom) vào bất kỳ track, clip, material hay keyframe nào đã có. Chỉ được THÊM track mới.
2. **Chỉ làm trên bản sao dự án.** Người dùng tự nhân bản dự án trong CapCut; Claude chỉ ghi vào bản nhân bản. Không bao giờ ghi vào dự án gốc.
3. **Chỉ xin quyền 2 thư mục**: thư mục dự án CapCut (bản sao) và thư mục tư liệu. Không đọc/ghi chỗ khác.
4. **Trước mọi lần ghi:** gửi MP4 xem trước, hỏi người dùng đã thoát hẳn CapCut chưa, sao lưu dự án, kiểm md5/thời điểm sửa file. CapCut đang mở sẽ lưu đè khi thoát.
5. **Không tự xoá file** của người dùng. Không chạy script có thể ghi vào dự án (`scripts/install_to_project.py`, mọi thứ trong `legacy/`) khi chưa được người dùng duyệt rõ ràng trong cuộc trò chuyện.
6. **Không tự chế trường dữ liệu CapCut.** Chỉ nhân bản đối tượng mà CapCut của chính người dùng đã lưu (`assets/capcut_templates.json` hiện là mẫu CapCut 9.5 macOS, phải thay bằng mẫu thu từ máy người dùng ở Giai đoạn 2).
7. **Gặp lỗi thì dừng và báo.** File timeline không bắt đầu bằng `{` = dự án bị mã hoá → dừng (xem `references/troubleshooting.md`, "Encrypted project").

## Lộ trình

| GĐ | Việc | Trạng thái |
|---|---|---|
| 0 | Tạo repo, tổ chức lại cấu trúc | xong |
| 1 | Khảo sát CHỈ ĐỌC bản sao file dự án: phiên bản CapCut, mã hoá, khung hình, fps, track, clip, tốc độ, keyframe | chờ duyệt |
| 2 | Cổng khả thi: thu mẫu từ dự án mẫu người dùng tự làm, thử thêm 1 chữ + 1 SFX vào dự án thử, người dùng mở/thoát CapCut, đọc lại | chờ duyệt |
| 3 | Gỡ băng, đề xuất từ khoá / chữ / SFX / B-roll để người dùng duyệt nội dung | chưa |
| 4 | Text, typography, animation keyframe, SFX, cân nhạc → MP4 xem trước | chưa |
| 5 | B-roll, hình minh hoạ, mẫu 3D → MP4 xem trước | chưa |
| 6 | Lớp chỉnh màu, kiểm tra toàn bộ, cài vào bản sao, kiểm tra mở lại | chưa |
| 7 | Hoàn thiện tài liệu, đóng gói | chưa |

Chi tiết kế hoạch, giới hạn CapCut và quyết định đã chốt: `references/ke-hoach.md`.

## Cấu trúc

| Thư mục | Nội dung | Ghi chú |
|---|---|---|
| `scripts/` | `common`, `analyze_audio`, `scan_library`, `textfit`, `check_env`, `prep_images`, `align_vo`, `install_to_project`, `package_offline` | Lấy nguyên từ skill auto-edit-capcut. `align_vo` sẽ thêm chế độ gỡ băng không cần kịch bản. `install_to_project` GHI vào dự án → chỉ chạy khi đã duyệt |
| `references/` | `ke-hoach.md` (kế hoạch skill này); `capcut-edit.md`, `setup.md`, `troubleshooting.md` (tài liệu gốc) | Ở tài liệu gốc chỉ dùng: `capcut-edit.md` mục 5 (nghề dựng âm thanh/chữ) và mục 9 (cách CapCut lưu dự án), phần tìm thư mục dự án ở mục 2, `troubleshooting.md` |
| `assets/` | `capcut_templates.json`, `sfx_cues.json`, `fonts/` (Be Vietnam Pro, Metropolis, Anton + giấy phép), `installers/` | `scripts/common.py` tìm `assets/` ngay cạnh `scripts/`, giữ nguyên cấu trúc này |
| `legacy/` | `build_capcut.py`, `preview.py` | Bộ dựng/xem trước cũ. **Dựng lại toàn bộ timeline = xoá phần dựng thô.** Đã chặn chạy; chỉ đọc để tách hàm ở Giai đoạn 4 |

Môi trường: Claude Code trên máy Windows của người dùng. Python 3.10–3.12, `ffmpeg` (hoặc `imageio-ffmpeg`), xem `requirements.txt`. Kiểm môi trường: `python scripts/check_env.py --whisper --lang vi` (chỉ cài thư viện, không đụng dự án).

Thư mục dự án CapCut trên Windows: `%LOCALAPPDATA%\CapCut\User Data\Projects\com.lveditor.draft\<tên dự án>`. Tìm dự án theo `draft_name` trong `draft_meta_info.json`, không theo tên thư mục. File timeline: `draft_content.json` (Windows) hoặc `draft_info.json` (Mac).
