Xử lý ảnh với OpenCV và NumPy - Báo cáo 9 bài tập
📁 Thư mục
input/: chứa ảnh gốc (bird.png, baby.jpeg, balloons_noisy.png, flower.jpeg)

output_mean_filter/: chứa ảnh sau lọc trung bình (mean)

output/: chứa ảnh sau xử lý các bài khác
📌 Câu 1: Tách Kênh Màu RGB
Mục đích: Hiển thị riêng từng kênh màu Red, Green, Blue từ một ảnh màu.

Hoạt động:

Đọc ảnh và chuyển sang hệ màu RGB.

Tạo 3 bản sao và lần lượt loại bỏ 2 kênh còn lại để giữ lại 1 kênh duy nhất.

Lưu ảnh kết quả và hiển thị bằng Matplotlib.

Kết quả:
Thu được 3 ảnh thể hiện riêng từng kênh màu. Dễ dàng nhận thấy ảnh đỏ sáng nhất ở vùng có nhiều màu đỏ, tương tự với xanh lá và xanh dương.

📌 Câu 2: Hoán Đổi Kênh Màu RGB
Mục đích: Biến đổi màu sắc bằng cách hoán đổi vị trí các kênh màu RGB.

Hoạt động:

Hoán đổi vị trí các kênh như sau:
R → G, G → B, B → R.

Lưu và hiển thị ảnh sau hoán đổi.

Kết quả:
Ảnh kết quả có màu sắc bị "lạ hóa", thể hiện sự thay đổi do các kênh bị tráo đổi.

📌 Câu 3: Chuyển ảnh RGB sang HSV và tách các kênh
Mục đích: Phân tích các thành phần Hue, Saturation, Value trong ảnh.

Hoạt động:

Chuyển ảnh RGB sang HSV.

Tách các kênh H, S, V và lưu dưới dạng ảnh xám.

Kết quả:
3 ảnh thể hiện rõ vùng màu (Hue), độ bão hòa (Saturation) và độ sáng (Value). Kênh H có giá trị từ 0–179, S và V từ 0–255.

📌 Câu 4: Điều Chỉnh Hue và Value trong HSV
Mục đích: Biến đổi màu sắc và độ sáng ảnh bằng cách điều chỉnh kênh H và V.

Hoạt động:

Giảm Hue còn 1/3 giá trị.

Giảm Value còn 3/4.

Chuyển ngược HSV về RGB.

Kết quả:
Ảnh kết quả có sắc màu dịu hơn và tối đi so với ảnh gốc.

📌 Câu 5: Lọc Nhiễu Ảnh Xám bằng Mean Filter
Mục đích: Làm mượt ảnh bằng bộ lọc trung bình.

Hoạt động:

Chuyển ảnh sang ảnh xám.

Áp dụng bộ lọc trung bình với kích thước kernel 5x5.

Hiển thị và lưu ảnh kết quả.

Kết quả:
Ảnh sau lọc mượt hơn, nhiễu được giảm nhưng có thể làm mờ biên cạnh.

📌 Câu 6: So Sánh Các Phương Pháp Lọc Nhiễu (Mean, Median, Minimum)
Mục đích: So sánh hiệu quả lọc nhiễu giữa 3 bộ lọc.

Hoạt động:

Áp dụng 3 bộ lọc:

Mean (Trung bình)

Median (Trung vị)

Minimum (Giá trị nhỏ nhất)

Hiển thị và lưu ảnh kết quả.

Kết luận:

Median filter giữ được biên rõ hơn, loại bỏ nhiễu tốt hơn.

Minimum filter làm ảnh tối và có thể mất chi tiết.

Mean filter làm mượt nhưng làm mờ biên.

📌 Câu 7: Xác Định Biên bằng Sobel và Canny
Mục đích: Phát hiện biên trong ảnh sau khi khử nhiễu.

Hoạt động:

Dùng median filter để khử nhiễu trước.

Áp dụng Sobel (tính đạo hàm) và Canny (tự động phát hiện biên).

Lưu và hiển thị ảnh.

Kết quả:

Sobel cho ra ảnh biên rõ nét, nhạy với cả hướng x và y.

Canny cho kết quả tốt, sắc nét và tự động chọn ngưỡng.

📌 Câu 8: Thay Đổi Màu RGB Ngẫu Nhiên
Mục đích: Thử nghiệm thay đổi màu ảnh bằng cách cộng thêm giá trị RGB ngẫu nhiên.

Hoạt động:

Tạo 3 giá trị ngẫu nhiên cho kênh R, G, B.

Cộng vào mỗi kênh tương ứng của ảnh đã khử nhiễu.

Giới hạn giá trị trong [0, 255].

Kết quả:
Mỗi lần chạy chương trình sẽ tạo ảnh với tone màu khác nhau, tạo hiệu ứng "hiệu chỉnh màu".

📌 Câu 9: Thay Đổi Hue Ngẫu Nhiên trong HSV
Mục đích: Tạo hiệu ứng màu độc đáo bằng cách thay đổi Hue.

Hoạt động:

Chuyển ảnh sang HSV.

Gán giá trị Hue ngẫu nhiên cho toàn bộ ảnh.

Chuyển lại về BGR.

Kết quả:
Màu sắc của ảnh thay đổi hoàn toàn nhưng giữ nguyên độ sáng và bão hòa. Hiệu quả cho tạo phong cách màu ngẫu nhiên.

🧰 Công cụ & Thư viện
OpenCV

NumPy

Matplotlib

SciPy (ndimage)

ImageIO

