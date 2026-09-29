# Sensor context

- Rig: Cả ba ảnh B4-dense đều cho thấy cảnh đường ở phía trước. Ảnh chỉ cho phép xác nhận hướng quan sát này; repo không cung cấp model camera, vị trí gá chính xác hay thông số calibration nên không suy đoán thêm.

- `ego_body`: Ở vùng trái-dưới và sát mép dưới của cả ba frame có thể quan sát phần thuộc phương tiện gắn camera như cụm tay lái/thân xe. Cánh tay, thân người và chân/bàn chân nhìn thấy ở phía trái là người/người lái, không thuộc `ego_body`.

- Vòng kính: Vùng ảnh hữu ích có biên gần tròn; vùng ngoài vòng kính tối/đen hiện rõ ở mép trên, hai bên và mép dưới. Theo `assets/frames.csv`, tâm và bán kính lần lượt là `(531.4, 1038.6), 813.9 px` cho `adasind_258420.jpg`; `(416.9, 986.6), 811.4 px` cho `adasind_270517.jpg`; và `(630.0, 1021.5), 813.1 px` cho `adasind_310008.jpg`. Ảnh có kích thước 1080×1920 px, nên đường kính vòng kính khoảng 1623–1628 px lớn hơn chiều rộng frame; vì vậy một phần vòng tròn nằm ngoài biên trái/phải của ảnh dọc.
