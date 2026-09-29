# Zone table (slice của bạn)

Lệnh `python3 lab11.py model` tự ghi bảng số (cùng cách đếm với `r1_craft/compare.md` và `model_compare.md`); chạy lại lệnh sẽ cập nhật bảng và giữ nguyên phần nhận xét. Bạn chỉ viết mục Nhận xét.

| Zone | n_ref | L missing | L spurious | M missing (`LR_noM` + `R_only`) | M thừa (`LM_noR` + `M_only`) | Lỗi L chính (`what`) |
|---|---:|---:|---:|---:|---:|---|
| center | 6 | 0 | 0 | 4 | 5 | — |
| mid | 7 | 3 | 3 | 2 | 9 | SPURIOUS (2) |
| edge | 7 | 0 | 0 | 1 | 1 | — |

## Nhận xét

- **L center:** ổn định ở cả ba ngưỡng IoU, luôn `6 matched / 0 missing / 0 spurious`.
- **L mid:** là zone L gãy nhiều nhất. Kết quả đổi từ `5/2/2` ở IoU 0.30 thành `4/3/3` ở 0.50 và giữ nguyên ở 0.70; một cặp mất match khi tăng ngưỡng cho thấy có nhạy với geometry/localization. Các missing/spurious đã tồn tại ngay ở 0.30 nên không thể giải thích toàn bộ chỉ bằng ngưỡng IoU.
- **L edge:** ổn định nhất cùng center, luôn `7/0/0` qua IoU 0.30, 0.50 và 0.70.
- **M center:** matched thấp và missing/spurious cao, giữ nguyên `2/4/5` ở cả ba ngưỡng. Việc không đổi theo ngưỡng cho thấy đây chủ yếu là bất đồng về tập object được ghép, không phải chỉ do box sát ngưỡng IoU.
- **M mid:** xấu nhất về số box thừa và giảm rõ khi tăng IoU: `6/1/8` → `4/3/10` → `3/4/11`. Phần matched giảm đồng thời missing và spurious tăng là bằng chứng có vấn đề localization/geometry; đồng thời 8 spurious đã có ở IoU 0.30 cho thấy còn bất đồng object ngoài geometry.
- **M edge:** tương đối tốt hơn M center/mid ở IoU 0.30 và 0.50 (`6/1/1`), nhưng giảm còn `5/2/2` tại IoU 0.70, nên vẫn có một cặp nhạy với yêu cầu chồng khít cao.
- **Giới hạn kết luận:** đây chỉ là slice ba frame. Các số cho phép phân biệt độ nhạy geometry khi thay ngưỡng với missing/spurious còn tồn tại ở ngưỡng thấp; chúng chưa đủ để kết luận nguyên nhân là méo fisheye, lỗi model hay lỗi teaching reference nếu chưa soi từng conflict trên ảnh và luật.
