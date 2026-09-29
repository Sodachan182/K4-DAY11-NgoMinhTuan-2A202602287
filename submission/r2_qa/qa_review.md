# QA review · B2-center

Reviewer: Tuấn  
Peer: Duy  
Mã khóa: 1865-3F60

| frame | object_ref | rule_id | nhận xét |
|---|---|---|---|
| adasind_062370.jpg | ego_body | R07 | P0 — thiếu polygon `ignore_region` có `reason=ego_body`; XML chỉ có 2 `lens_border`, trong khi phần phương tiện ego nhìn thấy ở trái-dưới. |
| adasind_086220.jpg | ego_body | R07 | P0 — thiếu polygon `ignore_region` có `reason=ego_body`; XML chỉ có 2 `lens_border`, trong khi phần phương tiện ego nhìn thấy ở trái-dưới. |
| adasind_117120.jpg | ego_body | R07 | P0 — thiếu polygon `ignore_region` có `reason=ego_body`; XML chỉ có 2 `lens_border`, trong khi phần phương tiện ego nhìn thấy ở trái-dưới. |
| adasind_062370.jpg | L1 ThreeWheeler | R05 | P2 — `truncated=false` nhưng box `(0,704)–(149,981)` chạm biên trái; hàm `truncated()` của repo trả `true`. |
| adasind_086220.jpg | L2 ThreeWheeler | R05 | P2 — `truncated=false` nhưng box `(658.55,869.28)–(1080,1298.77)` chạm biên phải; hàm `truncated()` của repo trả `true`. |

## PASS đã xác minh

- Export CVAT for images 1.1 có đủ 3 frame 1080×1920 và 21 rectangle hợp lệ; mọi box cao ≥40 px.
- Class đều thuộc tập cho phép; mỗi frame có 2 `lens_border` không rỗng với đúng `reason`.
- Mọi rectangle có đủ `occluded`, `truncated`, `edge_zone`; `edge_zone` khớp radial zone.
- Không box nào nằm ≥50% trong ignore region; không phát hiện duplicate đáng ngờ hay lỗi R03 chắc chắn.

## REVIEW NEEDED

- `adasind_117120.jpg` — L3 `Bus`, cao 48.31 px: xác nhận đây là Bus/minibus hay ThreeWheeler theo R04.
- `adasind_086220.jpg` — L5 `Car`, `occluded=true`: xác nhận class Car và trạng thái bị che.
- XML không chứa tên task: format CVAT 1.1 đã xác nhận nhưng chưa chứng minh được tên task có `raw_fisheye`.

## Kết luận

Peer export chưa đạt hoàn toàn do 3 lỗi thiếu `ego_body` và 2 lỗi attribute `truncated`. Hai ca REVIEW NEEDED chưa được kết luận hoặc ghi finding. Audit P3 này chỉ dùng rules, ảnh gốc, overlay và peer XML; không dùng reference/model.
