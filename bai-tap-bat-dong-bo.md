# 🧪 BÀI TẬP NGẮN
## 🎯 Mục tiêu

* Hiểu cách dùng `suspend function`
* Biết xử lý bất đồng bộ cơ bản trong app bán hàng
* Tránh block UI
  
## Coroutine trong ứng dụng bán hàng

---

## 🎯 Yêu cầu

Xây dựng chương trình mô phỏng:

👉 **Xem thông tin sản phẩm và tồn kho**

---

## 📌 Nhiệm vụ

### 1. Tạo model (đặt tên tiếng Việt)

```kotlin
data class SanPham(val id: String, val ten: String)
data class TonKho(val sanPhamId: String, val soLuong: Int)
```

---

### 2. Viết hàm giả lập API

```kotlin
suspend fun laySanPham(): SanPham
suspend fun layTonKho(sanPhamId: String): TonKho
```

👉 Yêu cầu:

* Dùng `delay()` để giả lập gọi API
* In log khi bắt đầu và kết thúc

---

### 3. Xử lý dữ liệu

Viết hàm:

```kotlin
suspend fun hienThiChiTietSanPham()
```

👉 Thực hiện:

1. Gọi `laySanPham()`
2. Gọi `layTonKho(sanPham.id)`
3. In ra:

```text
Sản phẩm: iPhone
Tồn kho: 10
```

---

### 4. Chạy chương trình

```kotlin
fun main() = runBlocking {
    hienThiChiTietSanPham()
}
```

 


