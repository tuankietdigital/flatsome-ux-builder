# TỔNG HỢP CSS UTILITIES, ICONS & ANIMATIONS TÍCH HỢP SẴN TRONG FLATSOME

Thay vì viết thêm CSS thủ công làm nặng mã nguồn và giảm điểm Google PageSpeed/Core Web Vitals, Flatsome đã tích hợp sẵn một hệ thống tiện ích CSS (CSS Utility Classes), bộ icon font độc quyền và thư viện hiệu ứng chuyển động phong phú.

---

## 1. TIỆN ÍCH CHỮ & ĐỊNH DẠNG VĂN BẢN (TYPOGRAPHY UTILITIES)

| Class Name | Mô tả tác dụng hiển thị | Ví dụ áp dụng |
| :--- | :--- | :--- |
| `uppercase` | Chuyển toàn bộ chữ thành IN HOA (`text-transform: uppercase`). | `<h2 class="uppercase">Tiêu đề</h2>` |
| `lowercase` | Chuyển toàn bộ chữ thành chữ thường (`text-transform: lowercase`). | `<span class="lowercase">email@domain.com</span>` |
| `lead` | Tăng cỡ chữ nhẹ và giãn dòng thanh thoát cho đoạn mở đầu / mô tả. | `<p class="lead">Đoạn tóm tắt</p>` |
| `thin-font` | Font chữ mảnh thanh lịch (`font-weight: 300`). | `<span class="thin-font">Bộ sưu tập</span>` |
| `alt-font` | Sử dụng font phụ (thường là font viết tay hoặc Dancing Script/Serif). | `<span class="alt-font">Special Offer</span>` |
| `heading-font`| Ép buộc văn bản sử dụng font gia đình của tiêu đề Theme Options. | `<div class="heading-font">Ký hiệu</div>` |
| `text-center` | Canh giữa dòng văn bản (`text-align: center`). | `<p class="text-center">Canh giữa</p>` |
| `text-left` | Canh trái văn bản (`text-align: left`). | `<div class="text-left">Canh trái</div>` |
| `text-right` | Canh phải văn bản (`text-align: right`). | `<div class="text-right">Canh phải</div>` |

---

## 2. HIỆU ỨNG ĐỔ BÓNG CHỮ (TEXT SHADOWS)

Cực kỳ hữu ích khi đặt chữ đè lên ảnh nền hoặc banner nhiều màu sắc để chữ không bị chìm:
- `text-shadow-1`: Đổ bóng nhẹ tự nhiên (tạo viền mờ 1px).
- `text-shadow-2`: Đổ bóng trung bình rõ nét.
- `text-shadow-3`: Đổ bóng đậm, phù hợp cho tiêu đề H1 rất lớn trên ảnh phong cảnh sáng tối phức tạp.

```html
<h1 class="uppercase text-shadow-1" style="color: #ffffff;">KHÁM PHÁ BỘ SƯU TẬP MỚI</h1>
```

---

## 3. NGỮ CẢNH MÀU NỀN SÁNG / TỐI (THEME CONTEXTS)

Flatsome có cơ chế tự động đảo màu thông minh dựa trên class bọc bên ngoài:
- `dark`: Khi gắn class `dark` vào một `[section]`, `[row]`, `[col]` hoặc `[text_box]`, Flatsome sẽ tự động nhận diện nền đang tối và **chuyển toàn bộ chữ, đường kẻ, icon và link bên trong sang màu trắng/xám nhạt**.
- `nav-dark`: Thường dùng trên Header hoặc Top Bar để đảo màu menu khi nền trong suốt hoặc có màu tối.
- `light`: Buộc các thành phần quay về màu chữ đen/tối mặc định.

---

## 4. KẺ NGĂN CÁCH & ĐƯỜNG VIỀN (DIVIDERS & BORDERS)

| Cú pháp HTML | Hiển thị thực tế |
| :--- | :--- |
| `<div class="is-divider small"></div>` | Vạch kẻ ngang ngắn (thường dài khoảng 30px, dày 2px, nằm dưới tiêu đề). |
| `<div class="is-divider full-width"></div>`| Đường kẻ ngang chạy hết 100% chiều rộng cột. |
| `<div class="is-border"></div>` | Tạo khung viền trang trí bo quanh nội dung. |
| `<div class="is-border is-dashed"></div>` | Tạo đường viền nét đứt sang trọng (thường dùng trong banner voucher). |
| `<div class="top-divider"></div>` | Đường kẻ mảnh ngăn cách trên đỉnh header/section. |

---

## 5. HIỆU ỨNG ĐỔ BÓNG & TƯƠNG TÁC KHỐI (BOX SHADOW & HOVER)

Các class đổ bóng theo chiều sâu (Depth Elevation) dựa trên Material Design:
- `depth="1"` đến `depth="5"`: Các mức độ đổ bóng tĩnh từ nhẹ đến rất nổi.
- `depth_hover="1"` đến `depth_hover="5"`: Mức độ đổ bóng khi người dùng rê chuột vào.
- `has-hover`: Kích hoạt hiệu ứng chuyển động mượt mà khi hover.
- `has-shadow`: Bật đổ bóng mặc định của theme.
- `box-shadow-1-hover`: Nâng nhẹ khối lên khi rê chuột.
- `circle`: Bo tròn 100% thành hình tròn (thường dùng cho avatar, icon, ảnh tròn).
- `round`: Bo góc tròn mềm mại.

---

## 6. DANH MỤC ICON NỘI BỘ (FLATSOME BUILT-IN FONT ICONS)

Flatsome đi kèm bộ font icon SVG/Icon font siêu nhẹ, sử dụng trực tiếp qua thẻ `<i class="tên-icon"></i>` hoặc thuộc tính `icon="..."` trong các shortcode:

### 6.1. Nhóm Thương Mại Điện Tử & Mua Sắm:
- `icon-shopping-basket`: Giỏ mua hàng dạng lẵng (biểu tượng kinh điển của Flatsome).
- `icon-shopping-cart`: Xe đẩy siêu thị.
- `icon-shopping-bag`: Túi xách thời trang.
- `icon-heart`: Trái tim yêu thích (Wishlist).
- `icon-tag`: Thẻ giảm giá / Khuyến mãi.
- `icon-gift`: Hộp quà tặng.

### 6.2. Nhóm Giao Tiếp & Hỗ Trợ:
- `icon-phone`: Ống nghe điện thoại / Hotline.
- `icon-envelop`: Phong bì thư / Email đăng ký nhận tin.
- `icon-map-pin-fill`: Điểm ghim định vị bản đồ / Cửa hàng.
- `icon-clock`: Đồng hồ / Giờ làm việc.
- `icon-user`: Hình đại diện tài khoản đăng nhập.
- `icon-chat`: Bong bóng hội thoại / Tư vấn trực tuyến.

### 6.3. Nhóm Điều Hướng & Trạng Thái:
- `icon-menu`: Menu 3 gạch (Hamburger icon mobile).
- `icon-search`: Kính lúp tìm kiếm.
- `icon-angle-down`: Mũi tên trỏ xuống (Dropdown menu).
- `icon-angle-right`: Mũi tên trỏ sang phải (Xem thêm, Next slide).
- `icon-angle-left`: Mũi tên trỏ sang trái (Quay lại, Prev slide).
- `icon-checkmark`: Dấu tích chữ V thành công / Cam kết.
- `icon-star`: Ngôi sao đánh giá.
- `icon-cross`: Dấu gạch chéo đóng popup / Hủy bỏ.

### 6.4. Nhóm Mạng Xã Hội:
- `icon-facebook`, `icon-instagram`, `icon-twitter`, `icon-youtube`, `icon-tiktok`, `icon-pinterest`, `icon-linkedin`.

---

## 7. BỘ HIỆU ỨNG CHUYỂN ĐỘNG (ENTRANCE ANIMATIONS)

Khai báo qua thuộc tính `animate="..."` trên `[col]`, `[ux_banner]`, `[button]`, hoặc thuộc tính HTML `data-animate="..."`:

| Giá trị Animation | Hiệu ứng khi người dùng cuộn tới |
| :--- | :--- |
| `fadeIn` | Mờ dần và hiện rõ tại chỗ. |
| `fadeInUp` | Từ phía dưới trượt nhẹ lên trên và hiện rõ (Rất khuyên dùng cho tiêu đề & CTA). |
| `fadeInDown` | Từ phía trên trượt xuống. |
| `fadeInLeft` | Từ bên trái trượt sang phải. |
| `fadeInRight` | Từ bên phải trượt sang trái. |
| `bounceIn` | Nảy nhẹ vào màn hình (phù hợp cho icon hoặc huy hiệu). |
| `zoomIn` | Phóng to dần từ giữa ra. |
| `flipInX` | Lật xoay theo trục ngang 3D. |
| `flipInY` | Lật xoay theo trục dọc 3D. |

*Thuộc tính đi kèm:* `animate_delay="0.2"` (Độ trễ tính bằng giây, hữu ích để tạo hiệu ứng nối đuôi nhau - Staggered entrance).

---

## 8. CSS TÙY BIẾN CHO HERO MULTI-BANNERS & FLICKITY SLIDER

Đoạn CSS mở rộng chuyên dụng cho các layout E-commerce bán lẻ công nghệ cao cấp (dán vào *Giao diện $\rightarrow$ Tùy biến $\rightarrow$ CSS Bổ sung*):

```css
/* 1. Bo góc tròn & đổ bóng nhẹ cho toàn bộ banner */
.border-radius-banner {
    border-radius: 10px !important;
    overflow: hidden !important;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.06);
    transition: transform 0.3s ease, box-shadow 0.3s ease;
}

/* 2. Hiệu ứng hover nhấc nhẹ và tăng độ nổi 3D */
.banner-hover-zoom:hover {
    transform: translateY(-3px);
    box-shadow: 0 6px 16px rgba(0, 0, 0, 0.12);
}

/* 3. Tùy biến dấu chấm chuyển slide Flickity nằm gọn bên trong */
.main-slider-box .flickity-page-dots {
    bottom: 12px !important;
}

.main-slider-box .flickity-page-dots .dot {
    background: #ffffff !important;
    opacity: 0.6;
    width: 8px;
    height: 8px;
    margin: 0 4px;
    transition: all 0.3s;
}

.main-slider-box .flickity-page-dots .dot.is-selected {
    opacity: 1;
    width: 22px;
    border-radius: 6px;
    background: #0ea5e9 !important; /* Đổi thành màu chủ đạo thương hiệu */
}
```

---

## 9. HỆ THỐNG TIỆN ÍCH RESPONSIVE NGUYÊN BẢN CỦA FLATSOME & MEDIA QUERIES

Flatsome xây dựng sẵn hệ thống class tiện ích responsive cực kỳ mạnh mẽ để điều khiển hiển thị và căn chỉnh mà không cần viết thêm CSS phức tạp:

### 9.1. Class Kiểm Soát Ẩn / Hiện Theo Màn Hình (Visibility Classes)
| Class Name | Hành vi hiển thị | Ứng dụng thực tế |
| :--- | :--- | :--- |
| `.hide-for-small` | **Ẩn trên Mobile** ($< 550\text{px}$). Vẫn hiện trên Desktop và Tablet. | Ẩn banner ngang phức tạp, ẩn bảng so sánh nhiều cột trên điện thoại. |
| `.show-for-small` | **Chỉ hiện trên Mobile** ($< 550\text{px}$). Tự động ẩn trên Desktop và Tablet. | Hiện thanh tìm kiếm di động, nút gọi điện nhanh cố định, banner dọc dành riêng cho smartphone. |
| `.hide-for-medium` | **Ẩn trên Tablet & Mobile** ($< 850\text{px}$). Chỉ hiện trên Desktop. | Ẩn các khối trang trí phụ, đồ họa nặng, hiệu ứng chuyển động không cần thiết trên thiết bị di động. |
| `.show-for-medium` | **Chỉ hiện trên Tablet** ($550\text{px} - 849\text{px}$). Ẩn trên Desktop và Mobile. | Bố cục tối ưu riêng cho iPad xoay ngang hoặc máy tính bảng. |
| `.hidden-for-large` | Ẩn trên Desktop ($\ge 850\text{px}$). | Hiện menu hamburger hoặc thanh công cụ di động. |

### 9.2. Tiện Ích Căn Lề Chữ Responsive (Responsive Text Alignment)
| Class Name | Tác dụng |
| :--- | :--- |
| `.text-center-small` | Tự động **canh giữa chữ trên Mobile** (giúp tiêu đề và nút CTA cân đối trên màn hình hẹp), trong khi vẫn giữ canh trái trên Desktop. |
| `.text-left-small` | Canh trái văn bản trên Mobile. |
| `.text-right-small` | Canh phải văn bản trên Mobile. |
| `.text-center-medium` | Canh giữa chữ khi xem trên Tablet. |

### 9.3. Bảng Khung Media Queries Chuẩn Mực Cho Flatsome
Khi bắt buộc phải viết thêm CSS tùy biến vào *Giao diện $\rightarrow$ Tùy biến $\rightarrow$ CSS Bổ sung*, kỹ sư bắt buộc phải sử dụng chính xác các Breakpoint sau để đồng bộ 100% với hệ thống CSS lõi của Flatsome:

```css
/* ==========================================================================
   1. DÀNH RIÊNG CHO MOBILE (< 550px)
   ========================================================================== */
@media (max-width: 549px) {
    /* Ví dụ: Đổi cỡ chữ tiêu đề nhỏ lại, thu nhỏ padding */
    .mobile-title-compact {
        font-size: 1.15rem !important;
        line-height: 1.3 !important;
    }
    
    /* Đảo ngược thứ tự 2 cột trên điện thoại (ảnh hiện trước, chữ hiện sau) */
    .reverse-mobile-row {
        display: flex !important;
        flex-direction: column-reverse !important;
    }
}

/* ==========================================================================
   2. DÀNH RIÊNG CHO TABLET (550px - 849px)
   ========================================================================== */
@media (min-width: 550px) and (max-width: 849px) {
    .tablet-compact {
        padding: 15px !important;
    }
}

/* ==========================================================================
   3. DÀNH CHO CẢ TABLET & MOBILE (< 850px)
   ========================================================================== */
@media (max-width: 849px) {
    /* Vô hiệu hóa hover trên màn hình cảm ứng để tránh giật lag */
    .touch-device-card:hover {
        transform: none !important;
    }
}

/* ==========================================================================
   4. DÀNH RIÊNG CHO DESKTOP (>= 850px)
   ========================================================================== */
@media (min-width: 850px) {
    /* Cân bằng chiều cao đa cột, hiệu ứng hover 3D */
    .desktop-only-flex {
        display: flex !important;
        align-items: stretch !important;
    }
}
```


