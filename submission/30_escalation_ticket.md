# Escalation ticket

## Ticket 1

- **Frame:** `adasind_258420.jpg` — L3/L7 Bike được ảnh gốc hỗ trợ nhưng không có trong teaching reference/model; L8 Car được model hỗ trợ (`LM_noR`) nhưng geometry khác R5. Các ca liên quan cần cùng một quyết định guideline là L5 mờ tại `adasind_270517.jpg` và ba Pedestrian có `edge_zone` sai tại `adasind_310008.jpg`.
- **Ảnh chụp:** `submission/screenshots/B4-dense_258420_reference_conflict.png` (crop từ ảnh gốc; cyan là annotation L đã khóa, vàng là teaching reference R).
- **Expected impact:** Nếu coi teaching reference/model là gold standard, annotator có thể xóa L3/L7 hoặc ép L8 theo R5 dù ảnh chưa chứng minh annotation hiện tại sai; ngược lại, nếu không có tiêu chí chung cho H=40, `unreadable` và radial `edge_zone`, các annotator có thể đưa ra quyết định không nhất quán. Trong `rework/delta.md`, vùng mid sau rework vẫn còn `5 matched / 2 missing / 3 spurious`; các số này có thể bị hiểu nhầm là lỗi annotator chắc chắn dù teaching reference chỉ là bản dạy học.
- **Owner:** `guideline`
- **Recommendation:** Đề nghị lead/teacher xác nhận hai quyết định: (1) với conflict L/R/M nhưng ảnh gốc vẫn hỗ trợ annotation, có cho phép giữ nhãn và ghi `keep_with_reason`/`E0_reference_defect` hoặc `E5_unresolved` thay vì sửa để tăng IoU hay không; (2) tiêu chí thao tác thống nhất cho vật sát H=40, thời điểm chuyển từ class sang `ignore_region.reason=unreadable`, và cách tính `edge_zone` bằng `r/R`. Đề xuất tạm thời là giữ nguyên L3/L7/L8 và bốn cặp K12 trong bản rework khóa `4359-7226`, không sửa thêm chỉ để khớp reference/model; dùng ảnh gốc + rule để xử lý missing thật, vùng unreadable và attribute radial cho đến khi lead trả lời.
