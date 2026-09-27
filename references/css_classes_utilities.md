# Thư Viện Tiện Ích CSS & Khung Media Queries Chuẩn Flatsome 3.20.5

> **Tác giả:** Quách Trần Tuấn Kiệt  
> **Kiểm chứng:** Trực tiếp từ `assets/css/flatsome.css` và `inc/builder/shortcodes/commons/visibility.php`.

---

## 1. BẢNG TRA CỨU CLASS ẨN/HIỆN THEO THIẾT BỊ (NATIVE VISIBILITY UTILITIES)

Flatsome xây dựng sẵn hệ thống class điều khiển hiển thị theo thiết bị trong file gốc `visibility.php`:

| Class Tiện Ích | Ý Nghĩa / Thiết Bị Hiển Thị | Cơ Chế Hoạt Động Của CSS |
| :--- | :--- | :--- |
| `.hide-for-medium` | **Chỉ hiện trên Desktop** | Ẩn trên màn hình $\le 849\text{px}$ (Tablet & Mobile) |
| `.show-for-small` | **Chỉ hiện trên Mobile** | Chỉ hiển thị trên màn hình $< 550\text{px}$ |
| `.show-for-medium.hide-for-small` | **Chỉ hiện trên Tablet** | Hiện từ $550\text{px} - 849\text{px}$, ẩn trên Desktop và Mobile |
| `.show-for-medium` | **Ẩn trên Desktop** | Hiển thị trên cả Tablet và Mobile ($\le 849\text{px}$) |
| `.hide-for-small` | **Ẩn trên Mobile** | Hiển thị trên cả Desktop và Tablet ($\ge 550\text{px}$) |
| `.hidden` | **Ẩn toàn bộ** | `display: none !important;` |

*Ví dụ áp dụng trong shortcode:*
```shortcode
[col span="6" class="hide-for-small"]
  <!-- Chỉ hiển thị trên máy tính và tablet, tự động giấu trên mobile -->
[/col]
[col span="12" class="show-for-small"]
  <!-- Banner phiên bản thu nhỏ chỉ dành riêng cho điện thoại -->
[/col]
```

---

## 2. CLASS TIỆN ÍCH CĂN LỀ & BỐ CỤC CHỮ (TEXT ALIGNMENT)

* `.text-left`: Căn lề trái trên mọi màn hình.
* `.text-center`: Căn lề giữa trên mọi màn hình.
* `.text-right`: Căn lề phải trên mọi màn hình.
* `.text-center-small`: **CỰC KỲ HỮU ÍCH TRÊN MOBILE.** Bình thường trên Desktop/Tablet căn lề trái, nhưng khi xuống Mobile tự động căn giữa cho cân đối.
* `.text-left-small`: Căn lề trái riêng cho Mobile.
* `.uppercase`: Viết in hoa toàn bộ text.
* `.thin-font`: Chữ nét mảnh hiện đại.
* `.lead`: Đoạn văn mở đầu cỡ lớn (Lead paragraph).

---

## 3. CLASS ĐỔ BÓNG NATIVE (BOX SHADOW & DEPTH)

Flatsome hỗ trợ 5 cấp độ đổ bóng chuẩn, không cần viết mã box-shadow thủ công:
* `.box-shadow-1` / `depth="1"`: Đổ bóng cực nhẹ (Card tin tức, Khung viền mỏng).
* `.box-shadow-2` / `depth="2"`: Đổ bóng trung bình (Thẻ dịch vụ, Hộp nổi bật).
* `.box-shadow-3` / `depth="3"`: Đổ bóng sâu (Khung báo giá, Form tư vấn).
* `.box-shadow-4` / `depth="4"`: Đổ bóng nổi bật cao.
* `.box-shadow-5` / `depth="5"`: Đổ bóng popup/modal.
* **Hiệu ứng hover tương ứng:** `.box-shadow-1-hover` đến `.box-shadow-5-hover` (Tự động nâng thẻ lên khi rê chuột).

---

## 4. CLASS TIỆN ÍCH FLEXBOX NATIVE TRONG THEME

Flatsome tích hợp sẵn bộ class Flexbox cực nhanh:
* `.flex-row`: Dàn theo hàng ngang.
* `.flex-col`: Dàn theo cột dọc.
* `.align-center`: Căn giữa theo trục dọc (`align-items: center`).
* `.justify-between`: Dạt đều ra hai bên mép (`justify-content: space-between`).
* `.justify-center`: Căn giữa theo trục ngang (`justify-content: center`).

---

## 5. BỘ CODE CSS SỬA LỖI ĐỘC QUYỀN (FLATSOME BUG FIXES BOILERPLATE)

Dưới đây là các đoạn mã CSS sửa lỗi kinh điển của Flatsome đã được kiểm chứng qua mã nguồn thực tế:

```css
/* -------------------------------------------------------------
 * 1. FIX KHOẢNG CÁCH THẺ BÀI VIẾT DỌNG (VERTICAL POST CARD)
 * Ngăn tiêu đề và mô tả dính sát mép thumbnail ảnh
 * ----------------------------------------------------------- */
.box-vertical .box-text {
    padding: 0 0 0 15px !important;
}

/* -------------------------------------------------------------
 * 2. CÂN BẰNG CHIỀU CAO THẺ BÀI VIẾT NỔI BẬT BÊN TRÁI (MAGAZINE)
 * Khớp hoàn hảo với 3 bài viết nhỏ bên phải trên Desktop
 * và tự thu gọn tỉ lệ vàng trên Mobile
 * ----------------------------------------------------------- */
.featured-post-card .image-cover {
    padding-top: 89% !important; /* Cân bằng 3 bài bên phải trên Desktop */
}

@media (max-width: 549px) {
    .featured-post-card .image-cover {
        padding-top: 65% !important; /* Tỉ lệ vàng trên màn hình di động */
    }
}

/* -------------------------------------------------------------
 * 3. BẢO TỒN ASPECT-RATIO CHO HÌNH ẢNH (CHỐNG MẤT ẢNH)
 * Tuyệt đối không can thiệp padding-top: 0 lên .image-cover
 * ----------------------------------------------------------- */
.preserve-aspect-ratio .image-cover {
    position: relative !important;
    display: block !important;
}

/* -------------------------------------------------------------
 * 4. THỪA HƯỞNG MÀU CHỮ WEBSITE THUẦN TÚY
 * ----------------------------------------------------------- */
.theme-inherited-text {
    color: inherit !important;
}

.theme-inherited-text a {
    color: inherit;
    transition: color 0.2s ease;
}

.theme-inherited-text a:hover {
    color: var(--primary-color, #446084);
}
```

---

## 6. KHUNG MEDIA QUERIES 4 CẤP CHUẨN FLATSOME (BOILERPLATE)

Khi cần viết thêm CSS responsive tùy biến cho Child Theme, luôn sử dụng khung mẫu sau:

```css
/* ============================================================
 * KHUNG MEDIA QUERIES CHUẨN FLATSOME 3.20.5
 * ============================================================ */

/* 1. TOÀN CỤC & DESKTOP (Mặc định: >= 850px) */
.custom-ux-element {
    display: block;
}

/* 2. DÀNH RIÊNG CHO MÁY TÍNH BẢNG (Tablet: 550px - 849px) */
@media screen and (min-width: 550px) and (max-width: 849px) {
    .custom-ux-element {
        /* CSS cho Tablet */
    }
}

/* 3. DÀNH CHO TABLET & MOBILE (Màn hình nhỏ: <= 849px) */
@media screen and (max-width: 849px) {
    .custom-ux-element {
        /* CSS thu gọn cho cả Tablet & Mobile */
    }
}

/* 4. DÀNH RIÊNG CHO ĐIỆN THOẠI (Mobile: < 550px) */
@media screen and (max-width: 549px) {
    .custom-ux-element {
        /* CSS tối ưu trải nghiệm chạm trên điện thoại */
    }
}
```
