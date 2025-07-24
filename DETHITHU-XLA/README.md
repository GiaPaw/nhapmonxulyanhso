
# Bài Thi Thử – Nhập Môn Xử Lý Ảnh (NM-XLA)

## Cấu trúc thư mục

```
D:\nhapmonxulyanhso\nhapmonxulyanhso\DETHITHU-XLA\NM-XLA
├── a.jpg
├── image1.jpg, image2.jpg, image3.jpg
├── colorful-ripe-tropical-fruits.jpg
├── quang_ninh.jpg
├── pagoda.jpg
├── luuhinh\
│   └── chứa các ảnh đầu ra đã xử lý
└── DETHITHU.ipynb
```

---

## Câu 1: Lọc trung bình, Sobel, đổi màu RGB, tách kênh HSV

- Đọc ảnh gốc `a.jpg` và thực hiện các thao tác:

### 1.1 Lọc trung bình:
```python
mean_filtered = cv2.blur(a, (5, 5))
```
Làm mịn ảnh bằng trung bình vùng lân cận 5x5.

### 1.2 Phát hiện biên Sobel:
```python
sobel_x = cv2.Sobel(gray, 1, 0)
sobel_y = cv2.Sobel(gray, 0, 1)
sobel = cv2.magnitude(sobel_x, sobel_y)
```
Phát hiện cạnh ngang, dọc và tính độ lớn tổng hợp.

### 1.3 Đổi màu RGB ngẫu nhiên:
```python
perm = np.random.permutation(3)
rgb_random = rgb[:, :, perm]
```
Xáo trộn thứ tự kênh màu RGB.

### 1.4 Tách HSV:
```python
hsv = cv2.cvtColor(a, cv2.COLOR_BGR2HSV)
h, s, v = cv2.split(hsv)
```
Tách các kênh H – S – V để quan sát riêng biệt.

---

## Câu 2: Biến đổi cường độ ảnh qua bàn phím

- Nhấn các phím `I`, `G`, `L`, `H`, `C`, `A` để thực hiện biến đổi tương ứng.

| Phím | Biến đổi                         | Giải thích |
|------|----------------------------------|------------|
| I    | Inverse                          | Đảo ngược ảnh |
| G    | Gamma correction (γ random)     | Làm sáng/tối ảnh bằng hàm lũy thừa |
| L    | Log transform                   | Nâng cao chi tiết vùng tối |
| H    | Equalization                    | Cân bằng histogram |
| C    | Contrast stretching             | Kéo giãn tương phản |
| A    | Adaptive Equalization (CLAHE)  | Cân bằng histogram thích nghi từng vùng nhỏ |

```python
key = cv2.waitKey(0)
if key in transformations:
    func, _ = transformations[key]
    out = func(img)
```

---

## Câu 3: Biến đổi hình học, làm mịn và tăng sáng

### 3.1 Resize ảnh:
```python
resized = cv2.resize(img, (150, 150))
```

### 3.2 Xoay ảnh:
```python
M = cv2.getRotationMatrix2D((w/2, h/2), 45, 1)
rotated = cv2.warpAffine(img, M, (w, h))
```

### 3.3 Làm mịn Gaussian:
```python
blurred = cv2.GaussianBlur(img, (11, 11), 0)
```

### 3.4 Tăng sáng và tương phản:
```python
bright_contrast = cv2.convertScaleAbs(img, alpha=1.5, beta=50)
```

- `alpha > 1`: tăng tương phản
- `beta > 0`: tăng độ sáng

---

## Ghi chú

- Toàn bộ ảnh đầu ra sẽ được lưu vào thư mục `luuhinh`.
- Mã được viết trong `DETHITHU.ipynb` với thư viện:
    - `OpenCV`
    - `NumPy`
    - `Matplotlib`

---

