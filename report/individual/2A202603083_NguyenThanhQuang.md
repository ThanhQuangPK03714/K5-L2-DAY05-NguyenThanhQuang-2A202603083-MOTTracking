# Báo cáo cá nhân — Nguyễn Thanh Quang (2A202603083)

Đoạn video: MOT17-09, 150 frame (CVAT frame 0–149; `gt.txt` frame 1–150), nguồn MOTChallenge, giấy phép CC BY-NC-SA 3.0.

## 0. Thông tin học viên

- Họ tên: Nguyễn Thanh Quang
- MSSV: 2A202603083
- Mã đề (A/B/C): B
- Email: nguyenvantuc07102015@gmail.com
- Link repository: https://github.com/ThanhQuangPK03714/K5-L2-DAY05-NguyenThanhQuang-2A202603083-MOTTracking
- Giờ bắt đầu: 16:00
- Giờ kết thúc: 18:00
- CVAT local: task 16, job 16 (`http://localhost:8080/tasks/16/jobs/16`)

## 1. Xem trước đoạn video (CP0)

Đề B trong `src/lab_variants.json` giao các ID nguồn MOT17 `[1, 19, 20, 21, 22]`. Đối chiếu điểm tham chiếu với các box trong `annotations.xml` cho thấy P1–P4 khớp lần lượt Track 3, 0, 1, 2. Ảnh gốc tại mốc P5 cho thấy người cần gán đứng cạnh P4, nhưng không có box nào bao điểm tham chiếu này.

| Mã | ID nguồn | Frame tham chiếu | Track CVAT khớp | Khoảng frame có box trong bản xuất | Rẽ / dừng / đổi tốc độ; che khuất |
|---|---:|---:|---|---|---|
| P1 | 1 | 0 | Track 3 | 0–149 | Ở các mốc ảnh đã đối chiếu, người gần cửa hàng dịch sang phải rồi chậm lại; có người qua lại cắt ngang, cần kiểm tra box quanh chỗ bị che |
| P2 | 19 | 0 | Track 0 | 0–149 | Người mặc áo xanh đi từ phải sang trái và tiến gần camera; áp sát P3 ở nửa sau đoạn |
| P3 | 20 | 40 | Track 1 | 0–149 | Người mặc áo polo xanh, đội mũ, đi từ mép phải sang trái và tiến gần camera; đi gần P2 ở nửa sau |
| P4 | 21 | 0 | Track 2 | 0–149 | Bé mặc váy sáng đứng cạnh người lớn gần bảng quảng cáo; dịch chuyển ít ở các mốc đầu, vùng này bị người đi ngang che ở các mốc muộn |
| P5 | 22 | 2 | Không có box khớp | Không có box P5 được xác nhận | Người mặc áo xanh/xám, đeo túi hồng cạnh P4 nhìn thấy tại điểm tham chiếu `(1331, 508)`; Track 4 bắt đầu ở khu vực khác và không khớp người này |

Các khoảng frame trên là khoảng có box trong bản xuất, không chứng minh người thật sự được bám đúng ở mọi frame. Track 2 giữ nguyên tọa độ box từ frame 37 đến 149; Track 4 chỉ có box từ frame 21 và giữ nguyên tọa độ đến frame 149. Các ghi chú hành vi được đối chiếu lại từ ảnh gốc tại các mốc tham chiếu và mốc cách nhau 10 frame; chúng không phục hồi được hồi tưởng CP0 ban đầu hay xác định chính xác frame bắt đầu/kết thúc từng lần che khuất. Cần xem Track 2 trên CVAT để phân biệt box trôi với P4 bị che; Track 4 không khớp P5.

## 2. Keyframe và thời gian (CP1, CP4)

Ánh xạ P/Track dưới đây được đối chiếu từ điểm tham chiếu của đề B (`src/lab_variants.json`) với tọa độ box trong bản xuất. P5 chưa có box được gán; Track 4 không khớp điểm tham chiếu P5. Thời gian thao tác từng track không có trong hai ZIP nên không thể điền số phút mà không suy đoán.

| P / ID trong CVAT | Số keyframe | Keyframe ở frame | Số frame có box | Keyframe / 100 frame | Thời gian (phút) | Chỗ cần chú ý từ bản xuất |
|---|---:|---|---:|---:|---|---|
| P2 / Track 0 | 23 | 0, 1, 3, 11, 14, 15, 16, 22, 28, 42, 52, 58, 65, 77, 85, 90, 102, 109, 120, 126, 137, 142, 149 | 150 | 15.3 | Không có trong ZIP | P2 khớp điểm tham chiếu frame 0 |
| P3 / Track 1 | 27 | 0, 13, 16, 18, 25, 35, 43, 51, 58, 66, 72, 81, 88, 93, 98, 104, 106, 111, 115, 120, 124, 128, 133, 137, 141, 145, 149 | 150 | 18.0 | Không có trong ZIP | P3 khớp điểm tham chiếu frame 40 |
| P4 / Track 2 | 9 | 0, 3, 5, 8, 13, 18, 24, 30, 37 | 150 | 6.0 | Không có trong ZIP | Box giữ nguyên tọa độ từ frame 37; kiểm tra P4 còn hiện diện hay bị che và xem lại cờ |
| P1 / Track 3 | 24 | 0, 5, 11, 18, 26, 32, 45, 56, 59, 64, 68, 72, 80, 84, 87, 92, 103, 115, 116, 118, 121, 128, 148, 149 | 150 | 16.0 | Không có trong ZIP | P1 khớp điểm tham chiếu frame 0 |
| Track 4 / chưa khớp người được giao | 1 | 21 | 129 | 0.8 | Không có trong ZIP | Box không khớp điểm tham chiếu P5; giữ nguyên tọa độ đến frame 149, cần xác nhận và sửa track |
| **Tổng** | **84** | — | **729** | **11.5** | **120 phút toàn buổi** (16:00–18:00; mục 0) | Không có thời gian tách riêng theo track |

Keyframe / 100 frame của cả bài = 84 ÷ 729 × 100 = **11.5**. Track 1 có nhiều keyframe nhất (27; 18.0/100 frame). Track 4 có 1 keyframe cho 129 frame, đúng với cảnh báo của checker và không khớp P5 tại frame tham chiếu. Track 2 có 9 keyframe nhưng frame cuối cùng có keyframe là 37; các tọa độ từ frame 37 đến 149 đều giống nhau. Hai trường hợp này cần xem lại trong CVAT. Tổng thời gian 120 phút lấy từ giờ bắt đầu/kết thúc ở mục 0; thời gian riêng cho từng track không được lưu trong ZIP hoặc nhật ký.

## 3. Đoạn bị che (CP2)

Trong `annotations.xml`, cả năm track đều có **0 frame `occluded`** và **0 lần bật `outside`**. Vì vậy bản xuất hiện tại không ghi lại các mốc che khuất CP2.

| Mốc | Frame trong bản xuất |
|---|---:|
| Bắt đầu bị che một phần (`occluded` bật) | Không có trong XML |
| Mất hẳn (`outside` bật) | Không có trong XML |
| Hiện lại (`outside` tắt) | Không có trong XML |
| Thấy rõ trở lại (`occluded` tắt) | Không có trong XML |

- Thời gian khuất hẳn: Không tính được vì không có lần bật `outside`.
- Quyết định giữ cùng ID / tạo track mới: Không có thông tin về quyết định CP2 trong hai ZIP.
- Lý do theo ngưỡng 60 frame, ngoại hình, hướng đi và tốc độ: Không có ghi chép trong hai ZIP.

Ba ảnh CP2 nằm trong `report/individual/images/`, nhưng file ảnh không cung cấp mốc frame đủ để đối chiếu và bản xuất không có cờ che khuất. Vì vậy ảnh không xác nhận được bốn mốc CP2 hoặc việc cùng một track được giữ trước và sau đoạn khuất.

![Ảnh CP2: che_1_truoc](images/che_1_truoc.png)
![Ảnh CP2: che_2_giua](images/che_2_giua.png)
![Ảnh CP2: che_3_sau](images/che_3_sau.png)

## 4. Tự review ID (CP3)

Đối chiếu box trong bản xuất với ảnh video theo số frame CVAT 0–149. Lượt 1 rà chuỗi box/keyframe theo từng track; lượt 2 xem toàn cảnh tại các mốc frame 0, 10, …, 140 và 149. Đây là rà soát bản xuất hiện có, chưa xác nhận hoặc sửa lại trên CVAT.

| Frame | Mã người / track CVAT | Loại lỗi | Mô tả | Phát hiện ở lượt | Đã sửa? |
|---:|---|---|---|---|---|
| 2 | P5 / chưa ánh xạ | `lost` | Người tại điểm tham chiếu P5 `(1331, 508)` đang hiện trong ảnh nhưng không có box nào bao phủ. | 1 — rà theo P5 | Chưa; cần thêm track/box đúng người trên CVAT |
| 37–149 | P4 / Track 2 | Cần xác minh `drift` hoặc `flag` | Track 2 không có keyframe sau frame 37 và box giữ nguyên tọa độ. Ở các frame muộn, người đi ngang che vùng box nên chưa đủ căn cứ kết luận box trôi hay P4 bị che/mất khỏi hình; cần tua lại để kiểm tra box và cờ. | 1 và 2 | Chưa; cần kiểm tra CVAT |
| 21–149 | Track 4 / người không khớp P5 | `false_track` | Điểm P5 ở frame 2 nằm gần `(1331, 508)`, còn Track 4 bắt đầu tại vùng `(249, 514)–(293, 581)` ở frame 21 và giữ nguyên box đến frame 149; track này không bám người P5 được giao. | 1 và 2 | Chưa; cần xóa/sửa track sai và gán P5 đúng người trên CVAT |
| 0–149 | P1–P3 / các track đã ánh xạ | Chưa thấy `id_switch`, `fragmentation` hoặc `merge` | Không thấy đổi người, đứt/nối ID hoặc box gộp người tại các mốc cảnh đã đối chiếu; đây chưa phải xác nhận không có lỗi ở mọi frame. | 1 và 2 | — |

**Tổng hợp theo loại lỗi:** `id_switch`: 0 phát hiện tại các mốc đã đối chiếu; `fragmentation`: 0 phát hiện; `lost`: 1 (P5/frame 2); `merge`: 0 phát hiện; `false_track`: 1 (Track 4); `drift`: chưa kết luận ở Track 2 vì cần xem P4 có di chuyển hay bị che ở các frame muộn; `flag`: chưa kết luận — XML hiện không có frame `occluded` hoặc lần bật `outside`, nhưng cần xem lại video để xác định các cờ có bị thiếu hay không.

Các lỗi ghi nhận và mục cần xác minh chưa được sửa trong CVAT. Cần chỉnh track/cờ trên job, xuất lại hai ZIP và cập nhật bảng này theo kết quả kiểm tra mới.

## 5. File xuất và kết quả tự kiểm (CP4)

| Kiểm tra | Kết quả |
|---|---|
| Tên file MOT 1.1 | `NguyenThanhQuang_mot.zip` (chứa `gt/gt.txt`, `gt/labels.txt`) |
| Tên file CVAT for video 1.1 | `NguyenThanhQuang_cvat_video.zip` (chứa `annotations.xml`) |
| Số track ID khác nhau trong `gt/gt.txt` | 5; đúng số lượng ID theo checker, nhưng chưa xác nhận đủ 5 người đề B được gán đúng |
| Số box trong `gt/gt.txt` | 729 |
| Cờ `occluded` / `outside` trong CVAT XML | 0 frame `occluded`, 0 lần bật `outside` |
| Đối chiếu P5 đề B | Điểm tham chiếu frame 2 `(1331, 508)` không nằm trong box nào; Track 4 bắt đầu ở frame 21 tại vùng `(248.74, 513.74)–(292.55, 581.10)` và giữ nguyên box đến frame 149. Cần kiểm tra lại trong CVAT |
| Job đã completed trên CVAT máy cá nhân | Không xác định từ ZIP; `annotations.xml` không lưu trạng thái completed |

Metadata XML ghi job 16, 150 frame, tạo lúc 16:48:14 và cập nhật lúc 17:25:44 (GMT+7); bản xuất được tạo lúc 17:31:43 (GMT+7). Các thời điểm này không chứng minh trạng thái completed. Log tạo task ghi server CVAT `2.74.1` và SDK `2.82.0`; task/job vẫn được tạo. Mật khẩu không được ghi vào báo cáo.

Kết quả chạy `src/check_submission.py` trên hai ZIP hiện tại:

```text
Số frame in theo CVAT (bắt đầu từ 0). Trong gt.txt, frame_id = frame CVAT + 1.

=== File MOT 1.1: NguyenThanhQuang_mot.zip ===
  Số track ID: 5   |   Tổng số box: 729
  [OK]        Đúng 5 track ID.

  Track | Frame có mặt | Số frame | Đoạn vắng (outside)
      1 |   0–149      |      150 | -
      2 |   0–149      |      150 | -
      3 |   0–149      |      150 | -
      4 |   0–149      |      150 | -
      5 |  21–149      |      129 | -

=== File CVAT for video 1.1: NguyenThanhQuang_cvat_video.zip ===

  Track | Nhãn   | Frame thấy | Keyframe | KF/100 frame | Frame occluded | Lần bật outside
      0 | person |        150 |       23 |         15.3 |              0 |               0
      Track 0: keyframe ở frame [0, 1, 3, 11, 14, 15, 16, 22, 28, 42, 52, 58, 65, 77, 85, 90, 102, 109, 120, 126, 137, 142, 149]
      1 | person |        150 |       27 |         18.0 |              0 |               0
      Track 1: keyframe ở frame [0, 13, 16, 18, 25, 35, 43, 51, 58, 66, 72, 81, 88, 93, 98, 104, 106, 111, 115, 120, 124, 128, 133, 137, 141, 145, 149]
      2 | person |        150 |        9 |          6.0 |              0 |               0
      Track 2: keyframe ở frame [0, 3, 5, 8, 13, 18, 24, 30, 37]
      3 | person |        150 |       24 |         16.0 |              0 |               0
      Track 3: keyframe ở frame [0, 5, 11, 18, 26, 32, 45, 56, 59, 64, 68, 72, 80, 84, 87, 92, 103, 115, 116, 118, 121, 128, 148, 149]
      4 | person |        129 |        1 |          0.8 |              0 |               0
      Track 4: keyframe ở frame [21]
      [CẢNH BÁO] Track 4: chỉ 1 keyframe cho 129 frame. Đã tua F kiểm tra box trôi chưa?

  Tổng: 84 keyframe / 729 frame có mặt = 11.5 keyframe / 100 frame
  [OK]        Đọc được 5 track từ annotations.xml.

=== Tóm tắt ===
  Lỗi: 0   |   Cảnh báo: 1
  Không có lỗi định dạng. Mở CVAT xem lại từng [CẢNH BÁO]; cảnh báo đúng ý bạn thì ghi lý do vào báo cáo.
```

Lỗi định dạng: 0; cảnh báo: 1. Cảnh báo là Track 4 có một keyframe cho 129 frame. Checker chỉ kiểm cấu trúc/số liệu; kết quả 5 ID không xác nhận mỗi ID đúng một người, đủ 5 người được giao, hay box không bị trôi.

## 6. Ba câu kết

1. Ưu tiên sửa P5: người tại điểm tham chiếu frame 2 chưa có box, còn Track 4 bắt đầu ở khu vực khác tại frame 21 và không khớp người được giao. Cần sửa track sai, gán đúng P5 rồi xuất lại; sau đó kiểm tra Track 2/P4 từ frame 37 vì box giữ nguyên tọa độ trong khi vùng này bị người đi ngang che ở các mốc muộn.

2. Chưa có ghi chú về trường hợp phân vân cùng ID hay ID mới, nên chưa thể nêu một quyết định cụ thể hoặc lý do đã ghi trong job.

3. P5 không có box tại frame tham chiếu và Track 4 không bám P5 có thể tạo FN cho người bị bỏ sót và FP cho track sai, làm giảm MOTA. Nếu Track 2 không còn bám P4 hoặc thiếu cờ che khuất, chất lượng box và liên tục ID cũng có thể bị ảnh hưởng. Chưa có ground truth đối chiếu hoặc kết quả chấm nên báo cáo không tự ước lượng MOTA/IDF1.

## Bonus (nếu làm)

Hai ZIP hiện tại không chứa dữ liệu bonus; không thể xác nhận B1, B2 hoặc B3 từ các file này.

## 7. Tài liệu tham khảo và công cụ AI đã dùng

- MOT17-09 từ MOTChallenge; đoạn sử dụng gồm 150 frame. Giấy phép CC BY-NC-SA 3.0.
- `docs/GUIDELINE.md`, `docs/MOT_FORMAT.md` và `src/lab_variants.json` trong repository.
- CVAT local server `2.74.1`; log tạo task ghi SDK `2.82.0` và cảnh báo lệch phiên bản.
- `src/check_submission.py`: đã chạy trên hai ZIP trong `src/exports` để lấy thống kê ở mục 5.
- ChatGPT/Codex: hỗ trợ đọc cấu trúc và số liệu trong hai ZIP, đối chiếu điểm tham chiếu đề B với box và ảnh gốc tại các mốc kiểm tra, rà các track có box giữ nguyên lâu, và biên tập các mục 1, 2, 4, 6; không sửa annotation trên CVAT hoặc tự tạo box/track ID.
