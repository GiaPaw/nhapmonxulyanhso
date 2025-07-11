
# 📘 README - XLA Lab4: Biến đổi hình học và Phân đoạn ảnh

## 🖼️ 1. Mô tả bài thực hành

Bài thực hành này gồm các phần chính:

- **Cắt ảnh theo vùng quan tâm (ROI)**
- **Áp dụng các kỹ thuật phân ngưỡng (thresholding)**
- **Biến đổi hình học (tịnh tiến, xoay, co giãn, ánh xạ tọa độ)**
- **Tiền xử lý ảnh bằng các phép toán hình thái học**
- **Xây dựng menu chọn chức năng xử lý tương tác**

---

## 📁 2. Cấu trúc thư mục

```
XLA_lab4/
├── exercise/
│   ├── dalat.jpg
│   ├── lang_biang.jpg
│   ├── ho_xuan_huong.jpg
│   ├── quan_truong_lam_vien.jpg
│   └── <các ảnh kết quả khác>
├── lab4_processing.py
└── README.md  ← (file này)
```

---

## ⚙️ 3. Yêu cầu thư viện

Cài đặt thư viện cần thiết:

```bash
pip install opencv-python matplotlib numpy scipy
```

---

## 🔧 4. Các chức năng đã triển khai

### 📍 Biến đổi ảnh theo vùng

1. **LangBiang:**
   - Cắt vùng ở góc trên bên trái
   - Áp dụng ngưỡng Otsu
   - Tịnh tiến sang phải 100px

2. **Hồ Xuân Hương:**
   - Cắt giữa ảnh
   - Áp dụng adaptive threshold
   - Xoay ảnh 45°

3. **Quảng trường Lâm Viên:**
   - Mapping uốn lượn ảnh
   - Ngưỡng nhị phân + đóng ảnh (binary closing)

### 🔄 Biến đổi hình học (dùng menu)

- `Rotate`: Xoay ảnh 45°
- `Scale`: Co ảnh xuống còn 50%
- `Shift`: Tịnh tiến ảnh 50px sang phải, 30px xuống dưới

### 🧩 Phân đoạn ảnh (segmentation)

- `adaptive_thresholding`: Adaptive Gaussian Threshold
- `binary_dilation`: Giãn ảnh nhị phân
- `binary_erosion`: Co ảnh nhị phân
- `otsu`: Phân ngưỡng bằng Otsu

---

## 🕹️ 5. Hướng dẫn sử dụng chương trình chính (lab4_processing.py)

### 1. Chạy script
```bash
python lab4_processing.py
```

### 2. Nhập chức năng cần áp dụng

Chọn 1 hoặc 2 chức năng từ danh sách dưới đây:

```
geometric_transformation:
  - Rotate
  - Scale
  - Shift
segment:
  - Adaptive_thresholding
  - Binary_dilation
  - Binary_erosion
  - Otsu
```

Ví dụ:

```
Nhập chức năng 1 (vd: Rotate, Scale, Otsu...): rotate
Nhập chức năng 2 (hoặc để trống nếu không dùng): otsu
```

### 3. Kết quả hiển thị:

- Ảnh kết quả sẽ được hiển thị bằng Matplotlib.
- Nếu cần, bạn có thể chỉnh sửa để lưu ảnh đầu ra.

---

## 📌 6. Gợi ý cải tiến

- Cho phép người dùng chọn file ảnh khác thay vì cố định `dalat.jpg`
- Thêm chức năng hiển thị ảnh gốc và ảnh kết quả song song
- Giao diện người dùng bằng tkinter hoặc web app

---

## 🧠 7. Kiến thức áp dụng

- Biến đổi affine (`warpAffine`, `getRotationMatrix2D`)
- Thresholding: Otsu, Adaptive
- Xử lý hình thái: dilation, erosion, closing
- Ánh xạ tọa độ (`cv2.remap`)
- Cắt ảnh vùng ROI

---


