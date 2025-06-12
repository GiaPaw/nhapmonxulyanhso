
# 🧪 Lab 2 – Xử Lý Ảnh Kỹ Thuật Số & Màu

## 📘 Giới thiệu

Bài thực hành 2 gồm 4 câu về các phương pháp biến đổi ảnh cơ bản và nâng cao:

1. Các phương pháp biến đổi ảnh theo miền không gian: image inverse, gamma, log, histogram, contrast.
2. Các phương pháp lọc ảnh theo miền tần số: Fourier và Butterworth.
3. Áp dụng ngẫu nhiên một biến đổi RGB lên ảnh bất kỳ.
4. Kết hợp biến đổi RGB với lọc Butterworth một cách ngẫu nhiên.

---

## 📁 Cấu trúc thư mục

```plaintext
XLA_lab2/
├── exercise/
│   ├── ha-long-bay-in-vietnam.jpg
│   ├── pagoda.jpg
│   ├── quang_ninh.jpg
├── lab2.ipynb
├── README.md
```

---

## ⚙️ Cài đặt môi trường

Chạy lệnh sau trong terminal:

```bash
pip install opencv-python numpy matplotlib scipy
```

---

## ▶️ Cách chạy

1. Mở `lab2.ipynb` bằng VSCode hoặc Jupyter Lab
2. Chạy từng ô mã từ trên xuống dưới để nạp các hàm
3. Gọi các hàm sau để thực thi các câu:
   ```python
   apply_transform('I')            # Câu 1 - Image Inverse
   apply_filter_menu('L')          # Câu 2 - Butterworth Lowpass
   random_rgb_transform()          # Câu 3 - Ngẫu nhiên biến đổi RGB
   random_combined_transform()     # Câu 4 - Kết hợp RGB + lọc
   ```

---

## 🔍 Giải thích mã nguồn

### 🧩 Thư viện import

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt
from scipy.fftpack import fft2, ifft2, fftshift, ifftshift
```

- `cv2`: đọc, ghi và xử lý ảnh
- `numpy`: toán học ma trận
- `matplotlib.pyplot`: hiển thị ảnh
- `scipy.fftpack`: xử lý biến đổi Fourier

---

### 🖼️ Hàm load và hiển thị ảnh

```python
def load_images():
    return [cv2.imread(path) for path in img_paths]

def show_image(title, img):
    plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
    plt.title(title)
    plt.axis("off")
    plt.show()
```

---

### 📌 Câu 1: Biến đổi ảnh cơ bản

- `image_inverse`: đảo ngược pixel (255 - value)
- `gamma_correction`: điều chỉnh độ sáng dựa theo hàm lũy thừa
- `log_transform`: nén động độ sáng với hàm log
- `histogram_equalization`: cải thiện độ tương phản dựa vào histogram
- `contrast_stretching`: đưa ảnh về dải cường độ 0–255

Hàm chính:

```python
def apply_transform(option):
    images = load_images()
    for i, img in enumerate(images):
        transformed = functions[option](img)
        filename = f'{option}_{img_files[i]}'
        cv2.imwrite(os.path.join(img_dir, filename), transformed)
        show_image(filename, transformed)
```

---

### 📌 Câu 2: Biến đổi tần số

- Sử dụng hàm Fourier để chuyển ảnh sang miền tần số
- Áp dụng bộ lọc Butterworth Lowpass hoặc Highpass

Các bước:
```python
f = fft2(gray_img)
f_shift = fftshift(f)
H = tạo mặt nạ lọc Butterworth
G = H * f_shift
g = ifft2(ifftshift(G))
```

---

### 📌 Câu 3: Ngẫu nhiên biến đổi RGB

```python
def random_rgb_transform():
    idx = random.randint(0, len(img_files) - 1)
    option = random.choice(list(functions.keys()))
    img = load_images()[idx]
    result = functions[option](img)
    ...
```

Chọn ngẫu nhiên một ảnh và một phép biến đổi trong câu 1 để áp dụng.

---

### 📌 Câu 4: Kết hợp RGB + lọc

```python
def random_combined_transform():
    idx = random.randint(0, len(img_files) - 1)
    option = random.choice(list(functions2.keys()))
    img = load_images()[idx]
    filtered = functions2[option](img)

    # Nếu là Butterworth thì áp dụng thêm min/max lọc ảnh
    if option in ['L', 'H']:
        filtered = np.min(filtered, axis=2) if random.random() < 0.5 else np.max(filtered, axis=2)
```

---

## 📤 Kết quả

- Các ảnh sau biến đổi sẽ được lưu trong thư mục `exercise/` với tên theo định dạng:
  - `I_pagoda.jpg`
  - `H_quang_ninh.jpg`
  - `L_filter_ha-long.jpg`, v.v.

---

## 📞 Liên hệ

> Thực hiện bởi: *[Tên bạn]*  
> Môn học: Nhập môn xử lý ảnh số  
> Trường: *[Tên trường nếu cần]*
