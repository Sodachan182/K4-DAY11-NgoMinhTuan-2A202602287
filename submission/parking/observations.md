# Quan sát vạch ô đỗ

- Các `parking_line` được chọn là những đoạn sơn nhìn thấy có vai trò phân chia từng ô đỗ. Tôi vẽ riêng từng đoạn và dừng ở đầu mút hoặc chỗ phần sơn không còn quan sát rõ; trong XML có 23 polyline, gồm các vạch rõ ở tiền cảnh và các vạch chia ô ở những hàng xa hơn.
- Tôi không gán mép sáng chạy ngang ở cuối mặt bãi, các vết nối/vết sẫm trên mặt đường và biên của xe đỏ vì chúng không phải là đoạn sơn phân chia một ô đỗ riêng.
- Polygon `free_space` gồm phần mặt đường trống nhìn thấy từ mép xa của bãi đến mép trái, phải và mép dưới ảnh. Polygon tạo khoảng tránh quanh xe đỏ và không đi vào khu vực cây, hàng rào hoặc phần ngoài mặt đường ở phía xa.
- Điểm còn mơ hồ: một số đoạn sơn ngắn ở xa bị mờ và biến dạng do phối cảnh; dải sơn dài gần nằm ngang ở phần giữa ảnh cũng cần người soát xác nhận thêm là ranh của hàng ô hay chỉ là vạch dẫn hướng trong bãi.
