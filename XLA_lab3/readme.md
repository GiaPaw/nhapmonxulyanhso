# README 

## 1. Hướng dẫn cài đặt và import

### Cài đặt các thư viện cần thiết:

```bash
pip install numpy scipy matplotlib imageio opencv-python
```

### Import trong Python:

```python
import os
import numpy as np
import cv2
import matplotlib.pyplot as plt
from scipy import ndimage as nd
from scipy.ndimage import rotate, gaussian_filter, map_coordinates
import imageio.v2 as iio
```

## 2. Phân tích các đoạn code quan trọng

### a. Đọc và hiển thị ảnh:

```python
img_path = os.path.join(base_dir, "colorful-ripe-tropical-fruits.jpg")
img = iio.imread(img_path)
```

* Dùng `os.path.join` để đảm bảo tính đa nền.
* Dùng `imageio` để đọc ảnh RGB mà không thay đổi độ sáng.

### b. Các hàm hiển thị tuỳ chỉnh:

```python
def show(img, title=None, cmap='gray'):
    plt.figure(figsize=(5,5))
    plt.imshow(img, cmap=cmap)
    if title: plt.title(title)
    plt.axis('off')
    plt.show()
```

* Giúc hiển thị ảnh nhanh trong Jupyter Notebook.

### c. Các phép biến đổi cơ bản:

```python
translated = nd.shift(img, shift=(50, -30))
rotated = nd.rotate(img, angle=45, reshape=True)
zoomed = nd.zoom(img, 3.0)
```

* Tịnh tiến, xoay, phóng to nhờ sử dụng scipy.ndimage

### d. Áp dụng hiệu ứng wave:

```python
def apply_wave_effect(img, amplitude=10, frequency=0.05):
    rows, cols = img.shape[:2]
    x, y = np.meshgrid(np.arange(cols), np.arange(rows))
    x_wave = x + amplitude * np.sin(2 * np.pi * frequency * y)
    coords = np.array([y.flatten(), x_wave.flatten()])
    waved = np.zeros_like(img)
    for i in range(3):
        waved[..., i] = map_coordinates(img[..., i], coords, order=1, mode='reflect').reshape(rows, cols)
    return waved
```

* Tạo biến dạng sóng theo trục ngang.

### e. Biến đổi hình học tổng quát:

```python
def GeoFun(outcoord):
    a = 10 * np.cos(outcoord[0]/10.0) + outcoord[0]
    b = 10 * np.cos(outcoord[1]/10.0) + outcoord[1]
    return a, b
```

* Dùng trong `geometric_transform` để biến dạng theo hàm tuỳ chỉnh.

### f. Gradient màu và nền trong suốt:

```python
cv2.addWeighted(img1, alpha, img2, beta, gamma)
```

* Trộn hai ảnh theo tỉ lệ để tạo gradient màu mềm.

### g. Warp hình:

```python
offset = int(20 * np.sin(2 * np.pi * i / 100))
nj = (j + offset) % w
warp_img[i, j] = src[i, nj]
```

* Biến đổi theo hàm sin để tạo hiệu ứng lượn sóng.

### h. Xử lý nhị ảnh:

```python
ndi.binary_dilation(...)
ndi.binary_erosion(...)
```

* Dịch trả và bảo vệ đối tượng trong ảnh nhị.

## 3. Cách sử dụng

### a. Chạy file trong VSCode:

* Dùng Jupyter Notebook (\*.ipynb).
* Click chọn cell và nhấn `Shift + Enter` để chạy từng bước.

### b. Để làm đằng project:

* Tạo file Python (để biến đổi ảnh theo menu).
* Gồm code biến đổi, hàm hiển thị, và giao diện tương tác.

---

**Tác giả: Nhóm Xử lý ảnh số - Lab 3**

Mọọi vấn đề/góp ý: vui lòng liên hệ GVHD hoặc nhóm học.

---
