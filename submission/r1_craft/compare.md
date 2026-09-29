# So sánh L với R

Chỉ số L/R là thứ tự box cao ≥ H=40 trong từng frame, theo thứ tự XML; bắt đầu từ 1.
Box L trong ignore_region được báo IGNORE_SCOPE, không tính SPURIOUS.

## adasind_258420.jpg
- L3 mid SPURIOUS
- L7 mid SPURIOUS
- L8+R5 mid BOX_GEOMETRY
- R7 mid MISSING
## adasind_270517.jpg
- L5 mid IGNORE_SCOPE
- R7 mid MISSING
## adasind_310008.jpg

## Theo zone
| zone | n_ref | matched | missing | spurious |
|---|---|---|---|---|
| center | 6 | 6 | 0 | 0 |
| mid | 7 | 4 | 3 | 3 |
| edge | 7 | 7 | 0 | 0 |
