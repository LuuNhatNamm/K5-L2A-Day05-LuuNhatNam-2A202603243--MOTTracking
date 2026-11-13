# Báo cáo cá nhân — Lưu Nhật Nam (2A202603243)

Đoạn video: MOT17-09, 150 frame (frame 1–150), nguồn MOTChallenge, giấy phép CC BY-NC-SA 3.0.

## 0. Thông tin học viên

- Họ tên: Lưu Nhật Nam
- MSSV: 2A202603243
- Mã đề (A/B/C): C
- Email: 26ai.namln2@vinuni.edu.vn
- Link repository: https://github.com/LuuNhatNamm/K5-L2A-Day05-LuuNhatNam-2A202603243--MOTTracking
- Giờ bắt đầu: 17h
- Giờ kết thúc: 7h30

## 1. Xem trước đoạn video (CP0)

Đối chiếu bảng nhận diện đề C với ảnh của đoạn MOT17-09 dùng cho job #15. Số frame theo CVAT (0–149). Dấu `~` chỉ mốc ước lượng khi tua xem. Bảng ghi quan sát từ ảnh gốc của đoạn video.

| Mã | Frame xuất hiện | Frame cuối thấy được | Rẽ / dừng / đổi tốc độ ở frame | Bị che ở frame | Ghi chú |
|---|---|---|---|---|---|
| P1 | 0 | 149 | ~60–70: xoay người, rồi bước dần về phía cửa hàng. | ~30–55: người đi ngang tiền cảnh che một phần rồi khuất khỏi tầm nhìn; thấy rõ lại khoảng frame 55. | Người áo đen, quần jeans trong cửa hàng Vodafone. |
| P2 | ~60 (thấy ở frame mẫu 61) | 149 | ~65–85: bước từ bên trái ra, sau đó đi về phía cửa. | ~60–75: phần thân dưới bị quầy và mép cửa kính che khi bước ra. | Người áo sáng có dải màu cam, đi cạnh P1 về cuối đoạn. |
| P3 | 0 (một phần ở mép phải) | 149 | Đi đều về phía camera và dịch dần sang trái trong ảnh, chưa thấy lần dừng rõ. | Đầu đoạn bị mép phải cắt một phần cơ thể. | Người áo polo xanh, đội mũ sáng màu. |
| P4 | 0 | ~105  | ~55–75: bước chậm, cúi hoặc quay về phía trẻ nhỏ trước cửa Woolworths. | Từ ~105–110: khó thấy do người đi ở tiền cảnh che. | Người mang túi hồng, đi cạnh trẻ nhỏ. |
| P5 | 0 (một phần ở mép trái) | 149 (chỉ thấy một phần) | ~35–45: xoay người sang phải; sau đó đi chéo ra xa camera. | ~110–125: đi sau người áo xanh lá; ~135–149: tiếp tục bị hai người ở tiền cảnh che, thấy lại một phần ở frame 149. | Người áo khoác đen, khăn đỏ, quần be. |

## 2. Keyframe và thời gian (CP1, CP4)

Số liệu lấy từ `src/check_submission.py` và `annotations.xml`. Các dòng ghi theo ID của bản xuất CVAT. Khi đối chiếu điểm nhận diện trong `src/lab_variants.json`, box Track 2 chứa điểm P3 tại frame 40 và box Track 1 chứa điểm P5 tại frame 28. Điểm nhận diện P1 (frame 0), P2 (frame 61) và P4 (frame 2) nằm ngoài mọi box hiện diện ở các frame đó. Cần mở bảng nhận diện đề C và rà lại đúng người trước khi chốt mã P1–P5.

| Mã / ID trong bản xuất CVAT | Số keyframe | Keyframe ở frame | Số frame có mặt | Keyframe / 100 frame | Thời gian (phút) | Chỗ khó |
|---|---|---|---|---|---|---|
| Track 0 | 16 | 0, 10, 20, 30, 40, 50, 60, 70, 80, 90, 100, 110, 120, 130, 140, 149 | 150 | 10.7 |  | Có mặt ở frame 0–149. Cần bổ sung chỗ khó. |
| Track 1 | 16 | 10, 20, 30, 40, 50, 60, 70, 80, 90, 100, 110, 118, 119, 120, 130, 149 | 130 | 12.3 | |Có mặt ở frame 10–138 và 149. Cần bổ sung chỗ khó. |
| Track 2 | 18 | 28, 30, 38, 40, 48, 50, 58, 60, 68, 70, 78, 88, 98, 108, 119, 129, 139, 149 | 122 | 14.8 |  | Có mặt ở frame 28–149. Cần bổ sung chỗ khó. |
| Track 3 | 2 | 139, 149 | 11 | 18.2 |  | Có mặt ở frame 139–149. Cần bổ sung chỗ khó. |
| Track 4 | 1 | 145 | 5 | 20.0 |  | Có mặt ở frame 145–149. Cần bổ sung chỗ khó. |
| **Tổng** | **53** | | **418** | **12.7** | | |

Keyframe / 100 frame của cả bài = 53 ÷ 418 × 100 ≈ 12.7.

Bạn đặt keyframe nhiều nhất ở người nào? Vì sao (người đó rẽ, dừng, lại gần camera hay bị che)?

Track 2 có nhiều keyframe nhất (18). Cần bổ sung mã P tương ứng và lý do đặt keyframe.

## 3. Đoạn bị che (CP2)

Track 1 trong bản xuất CVAT (ID 2 trong MOT). Box của track này chứa điểm nhận diện P5 ở frame 28. Đây là số liệu của đoạn `outside` trong bản xuất hiện tại. Cần kiểm tra lại đoạn che của P1 vì CP2 yêu cầu thực hiện trên P1.

| Mốc | Frame |
|---|---:|
| Bắt đầu bị che một phần (bật `occluded`) | 118 |
| Mất hẳn (bật `outside`) | 139 |
| Hiện lại (tắt `outside`) | 149 |
| Thấy rõ trở lại (tắt `occluded`) | Cờ vẫn bật ở frame 149. Cần xem lại trên CVAT. |

- Thời gian khuất hẳn: 10 frame (139–148), khoảng 0,33 giây ở 30 fps.
- Quyết định: Bản xuất giữ cùng ID khi hiện lại ở frame 149.
- Lý do (trả lời 3 câu: khuất bao lâu so với 60 frame, ngoại hình có khớp, chỗ hiện lại có đúng hướng và tốc độ):

Đoạn khuất 10 frame, dưới ngưỡng 60 frame. Cần bổ sung quan sát về ngoại hình, vị trí, hướng và tốc độ khi người này hiện lại.

Ảnh hiện có của Track 1 (P5), sắp theo số frame CVAT. Cần bổ sung ảnh trước, giữa và sau đoạn che của P1 cho CP2.

![Frame 108 — P5 còn thấy trước đoạn che](images/che_3_sau.png)
![Frame 121 — box P5 có cờ occluded](images/che_2_giua.png)
![Frame 131 — P5 vẫn bị che một phần](images/che_1_truoc.png)

## 4. Tự review ID (CP3)

Lượt 1 theo người (đi ngược từ frame 149 về 0 trên CVAT), lượt 2 theo cảnh (nhảy 10 frame). Ít nhất 3 dòng; không có lỗi thì ghi một dòng "đã kiểm hai lượt, không lỗi".

Loại lỗi dùng đúng một trong 7 mã: `id_switch`, `fragmentation`, `lost`, `merge`, `false_track`, `drift`, `flag`.

| Frame | Mã người | Loại lỗi | Mô tả một câu | Phát hiện ở lượt | Đã sửa? |
|---:|---|---|---|---|---|
| | | | | | |
| | | | | | |
| | | | | | |

Tổng hợp số lỗi theo loại:

| `id_switch` | `fragmentation` | `lost` | `merge` | `false_track` | `drift` | `flag` |
|---:|---:|---:|---:|---:|---:|---:|
| | | | | | | |

Lỗi nào chỉ lượt 2 (theo cảnh) mới thấy, lượt 1 (theo người) không thấy? Vì sao?

...

## 5. File xuất và kết quả tự kiểm (CP4)

| Kiểm tra | Kết quả |
|---|---|
| Tên file MOT 1.1 | `LuuNhatNam_mot.zip` (chỉ chứa tệp nhãn) |
| Tên file CVAT for video 1.1 | `LuuNhatNam_cvat_video.zip` (chỉ chứa `annotations.xml`) |
| Số track ID khác nhau trong `gt/gt.txt` (phải là 5) | 5 ID, 418 box |
| Frame `outside` không có dòng trong `gt.txt` (đúng / sai) | Đúng. MOT ID 2 vắng ở frame MOT 140–149 (CVAT 139–148) và có mặt ở frame MOT 150 (CVAT 149). |
| Job đã completed trên CVAT máy cá nhân | Có. Job #15, task đề C, trạng thái `completed` trên CVAT local. |

Kết quả chạy `src/check_submission.py` trên hai ZIP trong repo.

```text
Số frame in theo CVAT (bắt đầu từ 0). Trong gt.txt, frame_id = frame CVAT + 1.

=== File MOT 1.1: LuuNhatNam_mot.zip ===
  Số track ID: 5   |   Tổng số box: 418
  [OK]        Đúng 5 track ID.

  Track | Frame có mặt | Số frame | Đoạn vắng (outside)
      1 |   0–149      |      150 | -
      2 |  10–149      |      130 | 139–148
      3 |  28–149      |      122 | -
      4 | 139–149      |       11 | -
      5 | 145–149      |        5 | -


=== File CVAT for video 1.1: LuuNhatNam_cvat_video.zip ===

  Track | Nhãn   | Frame thấy | Keyframe | KF/100 frame | Frame occluded | Lần bật outside
      0 | person |        150 |       16 |         10.7 |              0 |               0
              Track 0: keyframe ở frame [0, 10, 20, 30, 40, 50, 60, 70, 80, 90, 100, 110, 120, 130, 140, 149]
      1 | person |        130 |       16 |         12.3 |             22 |               1
              Track 1: keyframe ở frame [10, 20, 30, 40, 50, 60, 70, 80, 90, 100, 110, 118, 119, 120, 130, 149]
      2 | person |        122 |       18 |         14.8 |             32 |               0
              Track 2: keyframe ở frame [28, 30, 38, 40, 48, 50, 58, 60, 68, 70, 78, 88, 98, 108, 119, 129, 139, 149]
      3 | person |         11 |        2 |         18.2 |              0 |               0
              Track 3: keyframe ở frame [139, 149]
      4 | person |          5 |        1 |         20.0 |              5 |               0
              Track 4: keyframe ở frame [145]

  Tổng: 53 keyframe / 418 frame có mặt = 12.7 keyframe / 100 frame
  [OK]        Đọc được 5 track từ annotations.xml.

=== Tóm tắt ===
  Lỗi: 0   |   Cảnh báo: 0
  Đạt. Dán phần tóm tắt này vào báo cáo mục 5.
```

## 6. Ba câu kết

1. Nếu được gán lại, bạn sẽ đặt keyframe khác ở đâu? Vì sao?

   Xem frame 130–138 của Track 1. Nếu box bị trôi khi người bị che, thêm keyframe ngay tại frame bắt đầu lệch.

2. Có chỗ nào bạn không chắc "cùng ID hay ID mới"? Bạn đã quyết định và ghi chú thế nào?

   Track 1 khuất ở frame 139–148 và giữ ID khi hiện lại ở frame 149. Ghi mốc này và dấu hiệu bạn thấy để nhận ra cùng người, như trang phục hoặc hướng di chuyển.

3. Một lỗi ID trong job của bạn (nếu không còn sót, chọn lỗi đã sửa) có thể làm xe tự lái dự đoán sai chuyển động của người đó như thế nào? Lỗi đó ảnh hưởng MOTA hay IDF1 nhiều hơn?

   Tôi không phát hiện lỗi ID khi rà soát. Giả sử Track 1 bị đổi ID ở frame 149, hệ thống có thể mất lịch sử quỹ đạo và dự đoán sai hướng hoặc tốc độ của người đó. Nếu ID sai kéo dài qua nhiều frame, IDF1 thường bị ảnh hưởng nhiều hơn MOTA.

## Bonus (nếu làm)

### B1 — Hai người đi sát

...

### B2 — So cách đặt keyframe

| Cách đặt | Số keyframe | Frame trôi nhất | Ghi chú |
|---|---:|---:|---|
| Đều mỗi 30 frame | | | |
| Theo chỗ đổi hướng | | | |

...

### B3 — So với tracker có sẵn

| Frame | Mã người | Tracker làm gì | Nhãn của bạn | Giải thích (đoán rồi sửa / ghép IoU / box score thấp / ngoại hình) |
|---:|---|---|---|---|
| | | | | |
| | | | | |

## 7. Tài liệu tham khảo và công cụ AI đã dùng

- Dữ liệu và nguồn ảnh minh họa: MOT17, MOTChallenge (Milan et al., 2016). Giấy phép CC BY-NC-SA 3.0.
- Codex .s
