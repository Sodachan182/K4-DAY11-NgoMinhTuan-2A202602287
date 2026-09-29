# Đối chiếu chất lượng cục bộ — rectangle

Teaching reference, không phải gold set đã phê duyệt; không có điểm đạt tự động.
Nguồn: export r1_craft đã khóa SHA256 `edcb9be1d072c41fa0daaf17261c52b268be3626d0132b55b9d66f821bd012aa`; slice `B4-dense`.
Ghép hình học greedy một-một theo IoU ≥ 0.50, rồi so class; H ≥ 40 px.
Box trái nằm chủ yếu trong ignore_region reference không tính. Polygon, polyline, track không được chấm.
Đây là phép tính offline của lab, không phải báo cáo hay kết quả tương đương CVAT Premium.

Frame được tính: adasind_258420.jpg, adasind_270517.jpg, adasind_310008.jpg. Frame thiếu trong export: không.
TP=17; FP=3; FN=3; số lần đối chiếu=23; mean IoU của TP=0.875.

| Chỉ số | Micro | Macro | Nhãn thấp nhất |
|---|---:|---:|---:|
| accuracy | 0.739 | 0.935 | 0.870 |
| precision | 0.850 | 0.817 | 0.600 |
| recall | 0.850 | 0.818 | 0.667 |
| jaccard | 0.739 | 0.714 | 0.500 |
| dice | 0.850 | 0.814 | 0.667 |

| Nhãn | TP | FP | FN | Accuracy | Precision | Recall | Jaccard | Dice |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| Bike | 3 | 2 | 1 | 0.870 | 0.600 | 0.750 | 0.500 | 0.667 |
| Car | 2 | 1 | 1 | 0.913 | 0.667 | 0.667 | 0.500 | 0.667 |
| Pedestrian | 6 | 0 | 1 | 0.957 | 1.000 | 0.857 | 0.857 | 0.923 |
| ThreeWheeler | 6 | 0 | 0 | 1.000 | 1.000 | 1.000 | 1.000 | 1.000 |

| Frame | TP | FP | FN | Accuracy | Precision | Recall |
|---|---:|---:|---:|---:|---:|---:|
| adasind_258420.jpg | 6 | 3 | 2 | 0.545 | 0.667 | 0.750 |
| adasind_270517.jpg | 6 | 0 | 1 | 0.857 | 1.000 | 0.857 |
| adasind_310008.jpg | 5 | 0 | 0 | 1.000 | 1.000 | 1.000 |

Confusion matrix: hàng = teaching reference; cột = export đã khóa.
`<missing>` là thiếu box; `<extra>` là box thừa. Xem `local_quality_confusion.csv`.

| Reference \ Export | Bike | Car | Pedestrian | ThreeWheeler | <missing> |
|---|---:|---:|---:|---:|---:|
| Bike | 3 | 0 | 0 | 0 | 1 |
| Car | 0 | 2 | 0 | 0 | 1 |
| Pedestrian | 0 | 0 | 6 | 0 | 1 |
| ThreeWheeler | 0 | 0 | 0 | 6 | 0 |
| <extra> | 2 | 1 | 0 | 0 | 0 |

Chi tiết xung đột trong `local_quality_conflicts.csv`; dữ liệu máy đọc trong `local_quality.json`.
Mismatching label đóng góp một FP cho class vẽ và một FN cho class reference; attribute khác được báo riêng.
Micro accuracy đếm mỗi cặp ghép sai class là một lần đối chiếu; Jaccard đếm cả FP và FN.
Macro/worst bỏ nhãn không xuất hiện ở cả hai phía; chỉ số không có mẫu là N/A.
