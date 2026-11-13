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

Ảnh nhận diện đề B cung cấp các frame tham chiếu dưới đây. Đây chỉ là frame dùng để nhận diện, không đủ để xác nhận frame xuất hiện đầu tiên, frame cuối cùng hoặc diễn biến che khuất.

| Mã | Frame xuất hiện | Frame cuối thấy được | Rẽ / dừng / đổi tốc độ ở frame | Bị che ở frame | Ghi chú |
|---|---:|---:|---|---|---|
| P1 | Chưa ghi | Chưa ghi | Chưa ghi | Chưa ghi | Frame tham chiếu nhận diện: 0 |
| P2 | Chưa ghi | Chưa ghi | Chưa ghi | Chưa ghi | Frame tham chiếu nhận diện: 0 |
| P3 | Chưa ghi | Chưa ghi | Chưa ghi | Chưa ghi | Frame tham chiếu nhận diện: 40 |
| P4 | Chưa ghi | Chưa ghi | Chưa ghi | Chưa ghi | Frame tham chiếu nhận diện: 0 |
| P5 | Chưa ghi | Chưa ghi | Chưa ghi | Chưa ghi | Frame tham chiếu nhận diện: 2 |

Chưa có ghi chép CP0 trước khi vẽ để điền các mốc và chuyển động còn thiếu.

## 2. Keyframe và thời gian (CP1, CP4)

Kết quả kiểm tra ghi ID track trong file CVAT là 0–4; log không ghi ánh xạ các ID này sang P1–P5. Vì vậy bảng dưới đây giữ nguyên ID track thay vì gán P theo suy đoán.

| P / ID trong CVAT | Số keyframe | Keyframe ở frame | Số frame có mặt | Keyframe / 100 frame | Thời gian (phút) | Chỗ khó |
|---|---:|---|---:|---:|---|---|
| Chưa ánh xạ / Track 0 | 23 | 0, 1, 3, 11, 14, 15, 16, 22, 28, 42, 52, 58, 65, 77, 85, 90, 102, 109, 120, 126, 137, 142, 149 | 150 | 15.3 | Chưa ghi | Chưa ghi |
| Chưa ánh xạ / Track 1 | 27 | 0, 13, 16, 18, 25, 35, 43, 51, 58, 66, 72, 81, 88, 93, 98, 104, 106, 111, 115, 120, 124, 128, 133, 137, 141, 145, 149 | 150 | 18.0 | Chưa ghi | Chưa ghi |
| Chưa ánh xạ / Track 2 | 9 | 0, 3, 5, 8, 13, 18, 24, 30, 37 | 150 | 6.0 | Chưa ghi | Chưa ghi |
| Chưa ánh xạ / Track 3 | 24 | 0, 5, 11, 18, 26, 32, 45, 56, 59, 64, 68, 72, 80, 84, 87, 92, 103, 115, 116, 118, 121, 128, 148, 149 | 150 | 16.0 | Chưa ghi | Chưa ghi |
| Chưa ánh xạ / Track 4 | 1 | 21 | 129 | 0.8 | Chưa ghi | Checker cảnh báo chỉ có 1 keyframe cho 129 frame; cần xem lại box trôi |
| **Tổng** | **84** | — | **729** | **11.5** | Chưa ghi | — |

Keyframe / 100 frame của cả bài = 84 ÷ 729 × 100 = **11.5**.

Track 1 có nhiều keyframe nhất (27; 18.0 keyframe/100 frame). Log chỉ có số lượng và vị trí keyframe, không cho biết lý do đặt nhiều keyframe; chưa có ghi chú quan sát để kết luận về rẽ, dừng, thay đổi kích thước hay che khuất.

## 3. Đoạn bị che (CP2)

Bản xuất được checker báo 0 frame `occluded` và 0 lần bật `outside` trên cả năm track. Do đó file hiện có không ghi một đoạn che khuất để điền các mốc CP2.

| Mốc | Frame |
|---|---:|
| Bắt đầu bị che một phần (bật `occluded`) | Không ghi trong bản xuất |
| Mất hẳn (bật `outside`) | Không ghi trong bản xuất |
| Hiện lại (tắt `outside`) | Không ghi trong bản xuất |
| Thấy rõ trở lại (tắt `occluded`) | Không ghi trong bản xuất |

- Thời gian khuất hẳn: Không tính được từ bản xuất vì không có lần bật `outside`.
- Quyết định giữ cùng ID / tạo track mới: Chưa có thông tin về quyết định CP2.
- Lý do theo ngưỡng 60 frame, ngoại hình, hướng đi và tốc độ: Chưa có ghi chép để xác nhận.

Ba tệp ảnh CP2 có trong `report/individual/images/` và được ghi nhận trong commit `6d43863`. Tuy vậy, log checker vẫn báo 0 frame `occluded` và 0 lần bật `outside`; ảnh tĩnh và tên file chưa đủ để xác nhận các mốc CP2 hoặc việc chúng cùng thể hiện một track liên tục. Vì vậy các mốc và quyết định CP2 phía trên vẫn để chưa xác nhận.

![Ảnh CP2: che_1_truoc](images/che_1_truoc.png)
![Ảnh CP2: che_2_giua](images/che_2_giua.png)
![Ảnh CP2: che_3_sau](images/che_3_sau.png)

## 4. Tự review ID (CP3)

Thông tin được cung cấp chưa có kết quả hai lượt review theo người và theo cảnh. Vì vậy không thể kết luận rằng job không có lỗi hoặc tự đặt số lỗi bằng 0.

| Frame | Mã người | Loại lỗi | Mô tả một câu | Phát hiện ở lượt | Đã sửa? |
|---:|---|---|---|---|---|
| Chưa ghi nhận | Chưa ghi | Chưa xác định | Chưa có ghi chép CP3 được cung cấp. | Chưa xác định | Chưa xác định |

Tổng hợp số lỗi theo loại: **chưa thống kê** (`id_switch`, `fragmentation`, `lost`, `merge`, `false_track`, `drift`, `flag`).

Lỗi chỉ phát hiện ở lượt 2: chưa có kết quả review để xác định.

## 5. File xuất và kết quả tự kiểm (CP4)

| Kiểm tra | Kết quả |
|---|---|
| Tên file MOT 1.1 | `NguyenThanhQuang_mot.zip` |
| Tên file CVAT for video 1.1 | `NguyenThanhQuang_cvat_video.zip` |
| Số track ID khác nhau trong `gt/gt.txt` | 5 — đúng yêu cầu |
| Frame `outside` không có dòng trong `gt.txt` | Đúng theo checker; log báo không có frame nào bật `outside` |
| Job đã completed trên CVAT máy cá nhân | Chưa có thông tin xác nhận; log chỉ cho biết task 16/job 16 đã được tạo |

Khi tạo task, log báo server CVAT `2.74.1` không tương thích hoàn toàn với SDK `2.82.0`; task và job sau đó vẫn được tạo. Mật khẩu không được ghi vào báo cáo.

Tóm tắt `src/check_submission.py` theo log đã cung cấp:

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

Lỗi định dạng: 0; cảnh báo: 1. Cảnh báo duy nhất là Track 4 có 1 keyframe cho 129 frame. Chưa có xác nhận rằng box đã được tua xem hoặc không bị trôi.

## 6. Ba câu kết

1. Theo số liệu hiện có, vị trí cần ưu tiên kiểm tra nếu làm lại là Track 4: checker cảnh báo chỉ có một keyframe trong 129 frame. Cần xem box trên CVAT và chỉ kết luận vị trí cần thêm keyframe sau khi kiểm tra chuyển động thực tế.

2. Chưa có ghi chú về trường hợp phân vân cùng ID hay ID mới, nên chưa thể nêu một quyết định cụ thể hoặc lý do đã ghi trong job.

3. Nếu box Track 4 trôi khỏi người giữa các keyframe, có thể phát sinh box bỏ sót (FN) hoặc box sai vị trí (FP), làm giảm MOTA. Nếu người đó bị gán nhầm ID hoặc đổi ID, tính liên tục định danh bị ảnh hưởng và IDF1 sẽ phản ánh việc giữ ID kém. Đây là giải thích có điều kiện; log hiện tại chưa xác nhận Track 4 thực sự bị trôi hay có lỗi ID.

## Bonus (nếu làm)

Chưa có dữ liệu được cung cấp để ghi nhận B1, B2 hoặc B3.

## 7. Tài liệu tham khảo và công cụ AI đã dùng

- MOT17-09 từ MOTChallenge; đoạn sử dụng gồm 150 frame.
- `docs/GUIDELINE.md` và `docs/MOT_FORMAT.md` trong repository.
- CVAT local server `2.74.1`; log tạo task ghi SDK `2.82.0` và cảnh báo lệch phiên bản.
- `src/check_submission.py`: kết quả được chép từ log người dùng cung cấp.
- ChatGPT: hỗ trợ biên tập báo cáo từ file export và thông tin/log đã cung cấp; không tự điền các quan sát CP0, quyết định CP2, kết quả CP3 hoặc trạng thái completed khi chưa có bằng chứng.
