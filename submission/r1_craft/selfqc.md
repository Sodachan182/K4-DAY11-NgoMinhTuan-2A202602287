# Tự soát

- Mã khóa `r1_craft` hiện tại: `EDCB-9BE1`.

## Checklist thủ công
- [x] Phạm vi H=40 và vật cần vẽ — 21 rectangle đều cao ≥40 px; nhỏ nhất là Car L5 của `adasind_270517.jpg`, cao 40.91 px.
- [x] lens_border và ego_body — mỗi frame có 2 polygon `lens_border` và 1 polygon `ego_body`; tất cả đều có ít nhất 40 điểm và đúng `reason`.
- [x] Class sáu nhãn — các rectangle chỉ dùng `Bike`, `Car`, `Pedestrian`, `ThreeWheeler`; không có class ngoài sáu class cho phép.
- [x] Rider và Bike — đối chiếu ảnh gốc: rider và xe hai bánh được bao chung bằng box `Bike`; không thấy box `Pedestrian` tách riêng chồng lên rider.
- [x] Geometry trên ảnh fisheye gốc — export chứa đúng ba ảnh gốc 1080×1920 của slice và box bám từng vật nhìn thấy, không có box phủ cả dãy.
- [x] truncated và occluded — cả 21 rectangle và 4 polygon K12 có đủ hai attribute với giá trị `true`/`false`; self-QC không báo `truncated` khác dự kiến.
- [x] Vật thiếu hoặc box trùng — self-QC không phát hiện cặp cùng class có IoU >0.7; đối chiếu thủ công ba ảnh gốc không thấy vật rõ ràng cao ≥40 px bị bỏ sót. Giới hạn: kiểm tra thiếu vật là kiểm tra bằng mắt, không thể chứng minh hoàn toàn chỉ từ XML.
- [x] ignore_region có reason — 9 polygon `ignore_region` gồm 6 `lens_border` và 3 `ego_body`, tất cả có `reason` hợp lệ; self-QC không báo box nằm ≥50% trong ignore.
- [x] Tên task raw_fisheye và export CVAT 1.1 — XML có version `1.1`, ba phần tử `image` và metadata task `Day11 · ADASIND · B4-dense · raw_fisheye`.

## Fill ratio (K12)
- adasind_270517.jpg box 6 center: 0.661
- adasind_270517.jpg box 7 edge: 0.532
- adasind_310008.jpg box 1 edge: 0.422
- adasind_310008.jpg box 5 edge: 0.359
mean edge: 0.438 (n=3)
mean center: 0.661 (n=1)
