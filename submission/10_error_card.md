# Error analysis card

## Zone × block

| zone | block | what | count |
|---|---|---|---:|
| center | B4 | MISSING | 4 |
| center | B4 | SPURIOUS | 5 |
| edge | B4 | MISSING | 1 |
| edge | B4 | SPURIOUS | 1 |
| mid | B4 | BOX_GEOMETRY | 1 |
| mid | B4 | IGNORE_SCOPE | 1 |
| mid | B4 | MISSING | 6 |
| mid | B4 | SPURIOUS | 13 |
| unknown | B2 | ATTRIBUTE | 2 |
| unknown | B2 | IGNORE_SCOPE | 3 |

## Top defects
- SPURIOUS: 19 (ví dụ frame adasind_258420.jpg)
- MISSING: 11 (ví dụ frame adasind_258420.jpg)
- IGNORE_SCOPE: 4 (ví dụ frame adasind_062370.jpg)

## Phân tích của bạn

Hai bảng trên do `python3 lab11.py card` tính từ `findings.csv`; chạy lại lệnh sẽ cập nhật bảng và giữ nguyên mục này. Viết cho lỗi nổi bật nhất, dẫn frame/`object_ref`.

- Nguyên nhân khả dĩ (`why`) và vì sao bạn nghĩ vậy: Với B4-dense, lỗi điển hình là bỏ sót vật nhỏ nhưng vẫn cao ≥40 px trong vùng mid (`adasind_258420.jpg` R7 Pedestrian và `adasind_270517.jpg` R7 Bike), nên vi phạm phạm vi R01. Ở `adasind_270517.jpg`, L5 bị gán `Car` dù vùng ảnh quá mờ để đọc class; đúng ra phải đánh dấu `ignore_region` với `reason=unreadable` theo R06 và không đặt box trong vùng ignore theo R09. Ba Pedestrian L1/L2/L3 ở `adasind_310008.jpg` nằm trong radial edge nhưng `edge_zone=false`, cho thấy attribute đã được điền theo mặc định mà chưa đối chiếu vị trí. Bảng phía trên cộng cả findings của peer và model, nên các tổng `SPURIOUS/MISSING` đó không được hiểu là toàn bộ đều là lỗi annotation B4-dense; L3/L7 Bike và L8 Car ở frame 258420 được giữ sau khi soi ảnh và không sửa chỉ để khớp teaching reference/model.
- Cách sửa và ai nhận việc (`owner`): Tuấn đã thêm Pedestrian còn thiếu ở `adasind_258420.jpg`; xóa L5 Car, thêm hai polygon `unreadable`, rồi thêm Bike còn thiếu ở `adasind_270517.jpg`; và đặt `edge_zone=true` cho ba Pedestrian ở `adasind_310008.jpg`. Bản rework đã khóa với mã `4359-7226`. Bốn cặp K12, `lens_border` và `ego_body` được giữ nguyên. Lần sau cần rà từng frame theo thứ tự: lọc vật cao ≥40 px, khoanh vùng mờ bằng ignore trước khi gán class, rồi tính/kiểm radial zone trước khi export; owner cho các bước này là Tuấn.
- Bằng chứng (ảnh trong `screenshots/`, dòng findings, rule): `r1_craft/compare.md` và các dòng B4-dense trong `findings.csv` ghi R7 `MISSING` ở hai frame, L5 `IGNORE_SCOPE`, cùng ba `mismatching_attributes` trong `r3_diag/local_quality.json`. `zone_table.md` xác định lỗi L tập trung ở mid, còn ba Pedestrian nói trên thuộc edge. `rework/delta.md` ghi mid cải thiện từ `4 matched / 3 missing / 3 spurious` thành `5 / 2 / 3`; do missing chỉ giảm một và spurious không giảm, đây là bằng chứng có cải thiện nhưng không phải mọi chênh lệch với teaching reference đã được xóa. Cách phát hiện là kết hợp overlay/ảnh gốc với compare, kiểm ignore theo R06/R09 và kiểm attribute theo vị trí; teaching reference/model chỉ là tín hiệu chẩn đoán, không phải lý do tự động xóa hoặc thêm box.
