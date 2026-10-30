# Kế hoạch skill hậu kỳ CapCut

Duyệt ngày 30/10/2026. Tài liệu đầy đủ: Claude Doc "Kế hoạch nâng cấp skill hậu kỳ CapCut".

## Mục tiêu

Người dùng đưa một dự án CapCut đã cắt dựng thô (tự quay, tự cắt, tự sắp cảnh). Claude chỉ làm hậu kỳ sáng tạo:

- **Text & typography**: phân tích lời thoại, chọn từ khoá / câu đắt, tiêu đề, chú thích, chữ nhấn; đặt trong vùng an toàn 9:16.
- **Animation**: xuất hiện / biến mất cho chữ, chuyển động nhẹ; không lạm dụng.
- **Sound effect**: chọn theo nội dung và hành động, nhấn ở từ khoá / minh hoạ / chuyển cảnh; cân giọng, nhạc, SFX.
- **B-roll & minh hoạ**: chỉ khi thật sự cần; ảnh, icon, infographic, mẫu 3D.
- **Hoàn thiện**: chỉnh màu khi cần, giữ chất lượng gốc.

Không viết kịch bản, không tạo giọng, không dựng lại video, không đổi nội dung / thứ tự / phần đã cắt.

## Quyết định đã chốt

1. Không chỉnh sửa clip gốc, không thêm keyframe zoom vào clip gốc. Zoom chỉ áp cho lớp B-roll.
2. Làm trên bản sao dự án CapCut (người dùng tự nhân bản trong CapCut; sao lưu thêm trước khi ghi).
3. Chạy bằng Claude Code trên máy Windows, quyền chỉ ở thư mục dự án và thư mục tư liệu.
4. Sau mỗi giai đoạn: báo cáo và chờ người dùng xác nhận.

## Kiến trúc (7 bước khi skill hoàn chỉnh)

1. Khảo sát chỉ đọc (`inspect_project`, chưa viết).
2. Hiểu nội dung: dựng lại giọng theo timeline (`timeline_map`, chưa viết), gỡ băng tiếng Việt, trích khung hình.
3. Đề xuất hậu kỳ → bảng cho người dùng duyệt.
4. Dựng lớp phủ từ `overlay_plan.json` (chưa viết): chỉ THÊM track mới.
5. Kiểm tra: hash đối tượng gốc không đổi, thời lượng không đổi, vùng an toàn, trùng lặp, đỉnh/LUFS; MP4 xem trước.
6. Cài vào bản sao (`install_to_project`), CapCut đã thoát.
7. Người dùng mở và thoát CapCut; đọc lại file CapCut tự lưu để xác nhận còn nguyên.

## Giới hạn CapCut cần nhớ

- Một số bản mã hoá file timeline (nhất là JianYing 6+): không chỉnh được từ ngoài → dừng.
- CapCut đang mở sẽ lưu đè khi thoát.
- Không có tài liệu chính thức; cấu trúc đổi theo phiên bản → chỉ nhân bản đối tượng từ CapCut của người dùng, ghi phiên bản vào báo cáo.
- Hiệu ứng / bộ lọc / animation / chuyển cảnh / mẫu chữ có sẵn tham chiếu tài nguyên tải từ máy chủ CapCut → không tự tạo; dùng keyframe (vị trí, tỉ lệ, độ mờ, góc xoay) hoặc nhân bản từ dự án mẫu.
- Chưa chắc lưu được chữ chuyển sắc; chưa chắc CapCut Windows đọc video có kênh alpha → kiểm ở Giai đoạn 2.
- CapCut desktop không xuất video bằng dòng lệnh → MP4 xem trước dựng bằng ffmpeg chỉ gần đúng; bản cuối người dùng xuất trong CapCut.
- Clip tốc độ đường cong: báo người dùng, không đoán.
- Ảnh / icon từ mạng: hỏi trước (bản quyền).

## Những gì đã bỏ so với skill gốc

`stitch_vo.py`, `plan_shots.py`, `make_plan.py`, `script-and-voice.md`, `visuals.md`, phụ thuộc Higgsfield (vẫn còn nguyên trong repo `claude-skill-edit-reel-capcut`).
