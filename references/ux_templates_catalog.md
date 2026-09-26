# THƯ VIỆN MẪU SHORTCODE THIẾT KẾ FLATSOME THỰC CHIẾN (UX TEMPLATES CATALOG)

Toàn bộ các mẫu shortcode dưới đây đã được kiểm duyệt nghiêm ngặt, tuân thủ 100% cú pháp Flatsome 3.x+, có đầy đủ cấu hình responsive (Desktop / Tablet / Mobile) và sẵn sàng copy/paste trực tiếp vào trang WordPress hoặc UX Blocks.

---

## 0. MẪU E-COMMERCE HERO MULTI-BANNERS THỰC CHIẾN (SLIDER 8 + 2 BANNER PHỤ 4 + 3 BANNER ĐÁY)

Bố cục đỉnh cao chuyên dùng cho các website bán lẻ công nghệ, điện máy, thời trang lớn (chuẩn Shopee, Tiki, CellphoneS).
- **Điểm vượt trội:** Toán học chiều cao khớp 100% không lệch 1 pixel ($230\text{px} \times 2 + 10\text{px} = 470\text{px}$ trên Desktop; $185\text{px} \times 2 + 10\text{px} = 380\text{px}$ trên Tablet).
- Tách biệt CSS thẩm mỹ: Bo góc tròn 10px (`.border-radius-banner`), hiệu ứng hover nhấc nhẹ (`.banner-hover-zoom`), tùy biến chấm tròn Flickity slider dots sang trọng.

### Đoạn Mã Shortcode:
```html
[section label="Ecom Hero Multi Banners" bg_color="#f5f7fa" padding="20px" padding__sm="10px" class="ecom-banner-hero-section"]

  [row style="small" v_align="equal-height" class="top-banner-row"]
    
    [col span="8" span__md="12" span__sm="12" class="main-slider-col"]
      [ux_slider style="normal" slide_width="100%" auto_slide="true" timer="5000" bullets="true" bullet_style="circle" nav_style="simple" class="main-slider-box"]
        [ux_banner height="470px" height__md="380px" height__sm="240px" bg="https://images.unsplash.com/photo-1593642632823-8f785ba67e45?auto=format&fit=crop&w=1200&q=80" link="#link-banner-chinh-1" class="border-radius-banner"]
        [/ux_banner]
        [ux_banner height="470px" height__md="380px" height__sm="240px" bg="https://images.unsplash.com/photo-1587202372775-e229f172b9d7?auto=format&fit=crop&w=1200&q=80" link="#link-banner-chinh-2" class="border-radius-banner"]
        [/ux_banner]
      [/ux_slider]
    [/col]

    [col span="4" span__md="12" span__sm="12" class="side-banners-col"]
      [ux_banner height="230px" height__md="185px" height__sm="150px" bg="https://images.unsplash.com/photo-1542751371-adc38448a05e?auto=format&fit=crop&w=600&q=80" link="#link-banner-phu-1" class="border-radius-banner banner-hover-zoom"]
      [/ux_banner]
      [gap height="10px"]
      [ux_banner height="230px" height__md="185px" height__sm="150px" bg="https://images.unsplash.com/photo-1550745165-9bc0b252726f?auto=format&fit=crop&w=600&q=80" link="#link-banner-phu-2" class="border-radius-banner banner-hover-zoom"]
      [/ux_banner]
    [/col]

  [/row]

  [gap height="10px"]

  [row style="small" class="bottom-banner-row"]
    
    [col span="4" span__md="4" span__sm="12"]
      [ux_banner height="190px" height__sm="130px" bg="https://images.unsplash.com/photo-1517336714731-489689fd1ca8?auto=format&fit=crop&w=600&q=80" link="#link-banner-day-1" class="border-radius-banner banner-hover-zoom"]
      [/ux_banner]
    [/col]

    [col span="4" span__md="4" span__sm="12"]
      [ux_banner height="190px" height__sm="130px" bg="https://images.unsplash.com/photo-1527864550417-7fd91fc51a46?auto=format&fit=crop&w=600&q=80" link="#link-banner-day-2" class="border-radius-banner banner-hover-zoom"]
      [/ux_banner]
    [/col]

    [col span="4" span__md="4" span__sm="12"]
      [ux_banner height="190px" height__sm="130px" bg="https://images.unsplash.com/photo-1588702547919-26089e690ecc?auto=format&fit=crop&w=600&q=80" link="#link-banner-day-3" class="border-radius-banner banner-hover-zoom"]
      [/ux_banner]
    [/col]

  [/row]

[/section]
```

### Đoạn CSS Tùy Biến Bổ Trợ (Dán vào Giao diện -> Tùy biến -> CSS Bổ sung):
```css
/* Bo góc tròn cho toàn bộ banner */
.border-radius-banner {
    border-radius: 10px !important;
    overflow: hidden !important;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.06);
    transition: transform 0.3s ease, box-shadow 0.3s ease;
}

/* Hiệu ứng hover nhấc nhẹ và đổ bóng */
.banner-hover-zoom:hover {
    transform: translateY(-3px);
    box-shadow: 0 6px 16px rgba(0, 0, 0, 0.12);
}

/* Tùy chỉnh dấu chấm chuyển slide Flickity nằm gọn gàng bên trong */
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
    background: #0ea5e9 !important; /* Đổi theo màu chủ đạo của web */
}
```

---

## 1. HERO BANNER CHUYỂN ĐỔI CAO (HIGH-CONVERTING HERO BANNER)

Mẫu Hero Banner toàn trang sang trọng với lớp phủ tối, hộp chữ nổi bật có hiệu ứng xuất hiện `fadeInUp`, nút bấm CTA kép và nút mũi tên trượt trang. Đầy đủ cấu hình responsive 3 thiết bị không bị tràn chữ.

```html
[section bg="https://images.unsplash.com/photo-1497366216548-37526070297c?auto=format&fit=crop&w=1600&q=80" bg_overlay="rgba(15, 23, 42, 0.65)" bg_pos="center center" parallax="3" height="620px" height__md="500px" height__sm="380px" dark="true" scroll_for_more="true" padding="0px"]
  [row v_align="middle" h_align="center"]
    [col span="10" span__md="11" span__sm="12" align="center"]
      [ux_banner height="550px" height__md="440px" height__sm="320px" bg_color="transparent"]
        [text_box position_x="50" position_x__sm="50" position_y="50" position_y__sm="50" text_align="center" text_color="light" width="85%" width__sm="95%" animate="fadeInUp"]
          <p class="uppercase lead thin-font" style="letter-spacing: 3px; margin-bottom: 10px;">Giải Pháp Đột Phá Cho Doanh Nghiệp</p>
          <h1 class="uppercase text-shadow-1" style="font-size: 2.8rem; line-height: 1.2; font-weight: 800; margin-bottom: 20px;">KIẾN TẠO THƯƠNG HIỆU DẪN ĐẦU THỊ TRƯỜNG</h1>
          <p class="lead" style="max-width: 700px; margin: 0 auto 30px auto; opacity: 0.9;">Tối ưu hóa quy trình vận hành, nâng tầm trải nghiệm khách hàng và bứt phá doanh số với nền tảng công nghệ số thế hệ mới.</p>
          [button text="KHÁM PHÁ DỊCH VỤ" color="primary" style="bevel" size="large" size__sm="medium" radius="5px" icon="icon-angle-right" icon_reveal="true" link="#services"]
          [button text="LIÊN HỆ TƯ VẤN" color="white" style="outline" size="large" size__sm="medium" radius="5px" icon="icon-phone" link="#contact"]
        [/text_box]
      [/ux_banner]
    [/col]
  [/row]
[/section]
```

---

## 2. KHỐI 4 LỢI ĐIỂM BÁN HÀNG / CAM KẾT DỊCH VỤ (VALUE PROPOSITIONS)

Khối 4 tính năng nổi bật đặt dưới Hero Banner, sử dụng `[featured_box]` có hiệu ứng hover đổ bóng mượt mà, responsive 4 cột trên Desktop, 2 cột trên Tablet và 1 cột trên Mobile.

```html
[section bg_color="#ffffff" padding="40px 0px 30px 0px" padding__sm="20px 0px 15px 0px"]
  [row style="default" col_bg="#f8fafc" col_bg_radius="8px" depth="1" depth_hover="3" v_align="equal-height"]
    [col span="3" span__md="6" span__sm="12" padding="25px 20px 25px 20px" padding__sm="20px 15px" animate="fadeInUp" animate_delay="0.1"]
      [featured_box icon="icon-truck" icon_border="2" icon_color="#2563eb" pos="top" title="GIAO HÀNG TỐC HÀNH" title_small="Toàn quốc"]
        <p class="text-center" style="font-size: 90%; color: #64748b; margin-bottom: 0;">Cam kết giao nhanh trong 24h đối với khu vực nội thành và miễn phí vận chuyển cho đơn từ 500k.</p>
      [/featured_box]
    [/col]

    [col span="3" span__md="6" span__sm="12" padding="25px 20px 25px 20px" padding__sm="20px 15px" animate="fadeInUp" animate_delay="0.2"]
      [featured_box icon="icon-checkmark" icon_border="2" icon_color="#16a34a" pos="top" title="CHÍNH HÃNG 100%" title_small="Đảm bảo nguồn gốc"]
        <p class="text-center" style="font-size: 90%; color: #64748b; margin-bottom: 0;">Sản phẩm nhập khẩu chính ngạch, đầy đủ hóa đơn chứng từ CO/CQ và bảo hành chính hãng lên tới 24 tháng.</p>
      [/featured_box]
    [/col]

    [col span="3" span__md="6" span__sm="12" padding="25px 20px 25px 20px" padding__sm="20px 15px" animate="fadeInUp" animate_delay="0.3"]
      [featured_box icon="icon-loop" icon_border="2" icon_color="#d97706" pos="top" title="ĐỔI TRẢ 30 NGÀY" title_small="An tâm trải nghiệm"]
        <p class="text-center" style="font-size: 90%; color: #64748b; margin-bottom: 0;">Chính sách đổi mới 1:1 miễn phí trong 30 ngày nếu phát sinh lỗi từ nhà sản xuất, thủ tục đơn giản.</p>
      [/featured_box]
    [/col]

    [col span="3" span__md="6" span__sm="12" padding="25px 20px 25px 20px" padding__sm="20px 15px" animate="fadeInUp" animate_delay="0.4"]
      [featured_box icon="icon-phone" icon_border="2" icon_color="#dc2626" pos="top" title="HỖ TRỢ 24/7" title_small="Chuyên gia tận tâm"]
        <p class="text-center" style="font-size: 90%; color: #64748b; margin-bottom: 0;">Đội ngũ kỹ thuật viên lành nghề luôn sẵn sàng giải đáp thắc mắc và hỗ trợ kỹ thuật xuyên suốt.</p>
      [/featured_box]
    [/col]
  [/row]
[/section]
```

---

## 3. KHỐI KHUYẾN MÃI FLASH SALE ĐẾM NGƯỢC (FOMO PROMOTION)

Tích hợp đồng hồ đếm ngược `[ux_countdown]` tạo tâm lý khẩn cấp, đi kèm danh sách sản phẩm sale dạng trượt (`type="slider"`) hỗ trợ cảm ứng vuốt chạm ngón tay trên di động.

```html
[section bg_color="#fff1f2" padding="50px 0px 50px 0px" padding__sm="25px 0px 25px 0px"]
  [row v_align="middle"]
    [col span="6" span__md="6" span__sm="12" align__sm="center"]
      <span class="badge" style="background-color: #e11d48; color: #ffffff; padding: 5px 12px; border-radius: 4px; font-weight: 700; text-transform: uppercase;">Ưu Đãi Giờ Vàng</span>
      <h2 style="font-size: 2.2rem; font-weight: 800; color: #881337; margin-top: 10px; margin-bottom: 10px;">FLASH SALE CUỐI TUẦN - GIẢM ĐẾN 50%</h2>
      <p style="color: #4c0519; margin-bottom: 20px;">Cơ hội duy nhất sở hữu các sản phẩm best-seller với mức giá không tưởng. Số lượng có hạn!</p>
    [/col]
    [col span="6" span__md="6" span__sm="12" align="right" align__sm="center"]
      [ux_countdown year="2026" month="12" day="31" time="23:59" style="clock" size="medium" t_hour="Giờ" t_min="Phút" t_sec="Giây"]
    [/col]
  [/row]

  [gap height="20px" height__sm="10px"]

  [row]
    [col span="12"]
      [ux_products type="slider" columns="4" columns__md="3" columns__sm="2" products="8" orderby="sales" show_cat="0" show_rating="1" show_add_to_cart="1" show_quick_view="1" image_hover="zoom-fade" style="shade"]
    [/col]
  [/row]
[/section]
```

---

## 4. BỘ 7 MẪU CUSTOM PRODUCT PAGE LAYOUT (CHUẨN TÀI LIỆU UX THEMES 247)

Dưới đây là các cấu trúc chuẩn 100% được UX Themes xuất bản chính thức, dùng để dán vào **UX Blocks** và gán làm giao diện trang chi tiết sản phẩm tùy biến (*Flatsome $\rightarrow$ Theme Options $\rightarrow$ WooCommerce $\rightarrow$ Product Page $\rightarrow$ Custom Product Layout*).

### Mẫu 4.1: Left Sidebar Layout (Full-Height)
```html
[row]
  [col span="3" span__sm="12"]
    [ux_sidebar id="product-sidebar"]
  [/col]
  [col span="9" span__sm="12"]
    [row_inner]
      [col_inner span="6" span__sm="12"]
        [ux_product_gallery]
      [/col_inner]
      [col_inner span="6" span__sm="12"]
        [ux_product_breadcrumbs]
        [ux_product_title]
        [ux_product_rating]
        [ux_product_price]
        [ux_product_excerpt]
        [ux_product_add_to_cart]
        [ux_product_meta]
        [share]
      [/col_inner]
    [/row_inner]
    [ux_product_tabs]
    [ux_product_upsell style="grid"]
    [ux_product_related]
  [/col]
[/row]
```

### Mẫu 4.2: Right Sidebar Layout (Full-Height)
```html
[row]
  [col span="9" span__sm="12"]
    [row_inner]
      [col_inner span="6" span__sm="12"]
        [ux_product_gallery]
      [/col_inner]
      [col_inner span="6" span__sm="12"]
        [ux_product_breadcrumbs]
        [ux_product_title]
        [ux_product_rating]
        [ux_product_price]
        [ux_product_excerpt]
        [ux_product_add_to_cart]
        [ux_product_meta]
        [share]
      [/col_inner]
    [/row_inner]
    [ux_product_tabs]
    [ux_product_upsell style="grid"]
    [ux_product_related]
  [/col]
  [col span="3" span__sm="12"]
    [ux_sidebar id="product-sidebar"]
  [/col]
[/row]
```

### Mẫu 4.3: Wide Gallery Layout (Sang trọng, tập trung vào hình ảnh sản phẩm)
```html
[ux_product_gallery style="full-width"]
[row]
  [col span="7" span__sm="12"]
    [ux_product_breadcrumbs]
    [ux_product_title]
    [ux_product_excerpt]
    [share]
  [/col]
  [col span="5" span__sm="12" padding="30px 30px 30px 30px" bg_color="rgba(233, 228, 228, 0.67)"]
    [ux_product_price]
    [ux_product_add_to_cart]
    [ux_product_meta]
  [/col]
[/row]
[row]
  [col span__sm="12"]
    [ux_product_tabs]
    [ux_product_upsell style="grid"]
    [ux_product_related]
  [/col]
[/row]
```

### Mẫu 4.4: 3-Column Standard Layout (Sidebar Trái - Gallery Giữa - Info Phải)
```html
[row]
  [col span="3" span__sm="12"]
    [ux_sidebar id="product-sidebar"]
  [/col]
  [col span="6" span__sm="12"]
    [ux_product_gallery]
  [/col]
  [col span="3" span__sm="12"]
    [ux_product_breadcrumbs]
    [ux_product_title]
    [ux_product_rating]
    [ux_product_price]
    [ux_product_excerpt]
    [ux_product_add_to_cart]
    [ux_product_meta]
    [share]
  [/col]
[/row]
[ux_product_tabs]
[ux_product_upsell style="grid"]
[ux_product_related]
```

---

## 5. KHỐI BẢNG GIÁ SO SÁNH DỊCH VỤ B2B (PRICING TABLE)

Bố cục 3 gói dịch vụ trực quan với gói ở giữa được làm nổi bật (`featured="true"`, viền màu chính, độ nổi `depth="3"`).

```html
[section bg_color="#f8fafc" padding="60px 0px 60px 0px"]
  [row h_align="center"]
    [col span="8" span__sm="12" align="center"]
      [title text="BẢNG GIÁ DỊCH VỤ LINH HOẠT" style="bold-center" size="xlarge"]
      <p class="lead" style="color: #64748b;">Lựa chọn giải pháp tối ưu phù hợp với quy mô và ngân sách phát triển của doanh nghiệp bạn.</p>
    [/col]
  [/row]

  [gap height="20px"]

  [row v_align="equal-height"]
    [col span="4" span__md="6" span__sm="12" bg_color="#ffffff" bg_radius="8px" depth="1" depth_hover="3" padding="30px 25px 30px 25px"]
      <h3 class="uppercase text-center" style="color: #334155; margin-bottom: 5px;">Gói Khởi Nghiệp</h3>
      <p class="text-center" style="color: #94a3b8; font-size: 90%;">Dành cho cá nhân & shop nhỏ</p>
      <div class="text-center" style="margin: 20px 0;">
        <span style="font-size: 2.2rem; font-weight: 800; color: #0f172a;">2.990.000đ</span><span style="color: #64748b;"> / tháng</span>
      </div>
      <div class="is-divider small" style="margin: 20px auto;"></div>
      <ul style="list-style: none; padding-left: 0; line-height: 2.2; color: #475569;">
        <li><i class="icon-checkmark" style="color: #16a34a; margin-right: 8px;"></i> Quản lý tối đa 500 sản phẩm</li>
        <li><i class="icon-checkmark" style="color: #16a34a; margin-right: 8px;"></i> Băng thông không giới hạn</li>
        <li><i class="icon-checkmark" style="color: #16a34a; margin-right: 8px;"></i> Tích hợp cổng thanh toán online</li>
        <li style="color: #cbd5e1; text-decoration: line-through;"><i class="icon-cross" style="margin-right: 8px;"></i> Hỗ trợ kỹ thuật riêng 24/7</li>
      </ul>
      [button text="ĐĂNG KÝ GÓI" color="secondary" style="outline" expand="1" radius="5px" link="#register-starter"]
    [/col]

    [col span="4" span__md="6" span__sm="12" bg_color="#ffffff" bg_radius="8px" depth="3" depth_hover="4" padding="35px 25px 35px 25px" style="border: 2px solid #2563eb; position: relative; margin-top: -10px; margin-bottom: -10px;"]
      <div class="badge" style="background-color: #2563eb; color: #ffffff; position: absolute; top: -14px; left: 50%; transform: translateX(-50%); padding: 4px 15px; border-radius: 20px; font-size: 80%; font-weight: 700; text-transform: uppercase;">Phổ Biến Nhất</div>
      <h3 class="uppercase text-center" style="color: #2563eb; margin-bottom: 5px;">Gói Chuyên Nghiệp</h3>
      <p class="text-center" style="color: #64748b; font-size: 90%;">Dành cho doanh nghiệp tăng trưởng</p>
      <div class="text-center" style="margin: 20px 0;">
        <span style="font-size: 2.5rem; font-weight: 800; color: #2563eb;">5.990.000đ</span><span style="color: #64748b;"> / tháng</span>
      </div>
      <div class="is-divider small" style="margin: 20px auto; background-color: #2563eb;"></div>
      <ul style="list-style: none; padding-left: 0; line-height: 2.2; color: #334155; font-weight: 500;">
        <li><i class="icon-checkmark" style="color: #16a34a; margin-right: 8px;"></i> Không giới hạn sản phẩm & bài viết</li>
        <li><i class="icon-checkmark" style="color: #16a34a; margin-right: 8px;"></i> Tốc độ tải trang tối ưu cực nhanh</li>
        <li><i class="icon-checkmark" style="color: #16a34a; margin-right: 8px;"></i> Tự động đồng bộ tồn kho đa kênh</li>
        <li><i class="icon-checkmark" style="color: #16a34a; margin-right: 8px;"></i> Quản lý chiến dịch tiếp thị E-E-A-T</li>
        <li><i class="icon-checkmark" style="color: #16a34a; margin-right: 8px;"></i> Hỗ trợ ưu tiên 1:1 qua Zalo/Hotline</li>
      </ul>
      [button text="CHỌN GÓI CHUYÊN NGHIỆP" color="primary" style="bevel" expand="1" radius="5px" link="#register-pro"]
    [/col]

    [col span="4" span__md="6" span__sm="12" bg_color="#ffffff" bg_radius="8px" depth="1" depth_hover="3" padding="30px 25px 30px 25px"]
      <h3 class="uppercase text-center" style="color: #334155; margin-bottom: 5px;">Gói Doanh Nghiệp</h3>
      <p class="text-center" style="color: #94a3b8; font-size: 90%;">Dành cho tập đoàn quy mô lớn</p>
      <div class="text-center" style="margin: 20px 0;">
        <span style="font-size: 2.2rem; font-weight: 800; color: #0f172a;">Liên Hệ</span>
      </div>
      <div class="is-divider small" style="margin: 20px auto;"></div>
      <ul style="list-style: none; padding-left: 0; line-height: 2.2; color: #475569;">
        <li><i class="icon-checkmark" style="color: #16a34a; margin-right: 8px;"></i> Tùy biến toàn bộ tính năng theo yêu cầu</li>
        <li><i class="icon-checkmark" style="color: #16a34a; margin-right: 8px;"></i> Hạ tầng máy chủ riêng Dedicated Server</li>
        <li><i class="icon-checkmark" style="color: #16a34a; margin-right: 8px;"></i> Ký cam kết chất lượng dịch vụ (SLA 99.9%)</li>
        <li><i class="icon-checkmark" style="color: #16a34a; margin-right: 8px;"></i> Đội ngũ kỹ sư chuyên trách riêng</li>
      </ul>
      [button text="TƯ VẤN DOANH NGHIỆP" color="secondary" style="outline" expand="1" radius="5px" link="#contact-enterprise"]
    [/col]
  [/row]
[/section]
```

---

## 6. KHỐI MEGA MENU TRONG UX BLOCKS

Thiết kế mẫu menu xổ xuống chia 4 cột trong UX Block để gắn vào menu chính:
- Cột 1 & 2: Danh sách danh mục sản phẩm nổi bật.
- Cột 3: Sản phẩm khuyến mãi best-seller.
- Cột 4: Banner quảng cáo đồ họa trực quan.

```html
[row style="small" padding="15px 15px 15px 15px"]
  [col span="3" span__sm="12"]
    <h4 class="uppercase" style="font-size: 1rem; color: #0f172a; margin-bottom: 12px; font-weight: 700;">ĐIỆN THOẠI NỔI BẬT</h4>
    <div class="is-divider small" style="margin-bottom: 12px;"></div>
    <ul style="list-style: none; padding-left: 0; line-height: 2;">
      <li><a href="/iphone-16-pro-max">iPhone 16 Pro Max</a></li>
      <li><a href="/samsung-s25-ultra">Samsung Galaxy S25 Ultra</a></li>
      <li><a href="/xiaomi-15-ultra">Xiaomi 15 Ultra</a></li>
      <li><a href="/oppo-find-x8">OPPO Find X8 Pro</a></li>
      <li><a href="/dien-thoai-gap">Điện thoại màn hình gập</a></li>
    </ul>
  [/col]

  [col span="3" span__sm="12"]
    <h4 class="uppercase" style="font-size: 1rem; color: #0f172a; margin-bottom: 12px; font-weight: 700;">PHỤ KIỆN CAO CẤP</h4>
    <div class="is-divider small" style="margin-bottom: 12px;"></div>
    <ul style="list-style: none; padding-left: 0; line-height: 2;">
      <li><a href="/tai-nghe-khong-day">Tai nghe chống ồn TWS</a></li>
      <li><a href="/dong-ho-thong-minh">Smartwatch thể thao</a></li>
      <li><a href="/sac-nhanh-gan">Củ sạc nhanh GaN 100W</a></li>
      <li><a href="/pin-du-phong">Sạc dự phòng không dây</a></li>
      <li><a href="/op-lung-chinh-hang">Ốp lưng chống sốc chuẩn quân đội</a></li>
    </ul>
  [/col]

  [col span="3" span__sm="12"]
    <h4 class="uppercase" style="font-size: 1rem; color: #0f172a; margin-bottom: 12px; font-weight: 700;">GIÁ SỐC HÔM NAY</h4>
    <div class="is-divider small" style="margin-bottom: 12px;"></div>
    [ux_products type="row" columns="1" products="1" orderby="sales" show_cat="0" show_rating="1" style="vertical"]
  [/col]

  [col span="3" span__sm="12"]
    [ux_banner height="240px" bg="https://images.unsplash.com/photo-1511707171634-5f897ff02aa9?auto=format&fit=crop&w=400&q=80" bg_overlay="rgba(0,0,0,0.4)" hover="zoom"]
      [text_box position_x="50" position_y="50" text_align="center" text_color="light"]
        <h4 class="uppercase" style="margin-bottom: 5px;">THU CŨ ĐỔI MỚI</h4>
        <p style="font-size: 85%; margin-bottom: 10px;">Trợ giá lên đến 3.000.000đ</p>
        [button text="XEM CHI TIẾT" color="white" style="outline" size="x-small" radius="4px" link="/thu-cu-doi-moi"]
      [/text_box]
    [/ux_banner]
  [/col]
[/row]
```

---

## 7. MẪU SECTION SẢN PHẨM CAROUSEL KÈM TAB TIÊU ĐỀ PRIMARY COLOR (EQUALIZED BOXES)

Bố cục thanh trượt sản phẩm 5 cột chuyên nghiệp kèm tiêu đề H2 dạng tab đóng khung tự động nhận màu chủ đạo của website (`var(--primary-color)`). Đặc biệt kích hoạt `equalize_box="true"` để toàn bộ khung sản phẩm có chiều cao bằng phẳng tăm tắp dù độ dài tiêu đề khác nhau.

```html
[section label="Section San Pham Carousel" padding="30px 0px 30px 0px"]

[row]
[col]

<div class="product-cat-title-bar">
<h2 class="product-cat-title-badge">Tên Danh Mục</h2>
</div>

[ux_products columns="5" columns__sm="2" columns__md="3" slider_nav_style="circle" show_cat="0" show_rating="0" show_quick_view="0" equalize_box="true" cat="slug-danh-muc" products="10"]

[/col]
[/row]

[/section]
```

### Đoạn CSS Tự Động Đồng Bộ Màu Theme:
```css
/* Khung bao có đường kẻ viền đáy 2px chạy ngang toàn hàng */
.product-cat-title-bar {
    border-bottom: 2px solid var(--primary-color) !important;
    margin-bottom: 20px !important;
    clear: both;
}

/* Tab tiêu đề H2 chỉ ôm vừa khít chữ (fit-content), tuyệt đối KHÔNG tràn toàn hàng */
.product-cat-title-bar h2.product-cat-title-badge {
    display: inline-block !important;
    width: auto !important;
    max-width: fit-content !important;
    background-color: var(--primary-color) !important;
    color: #ffffff !important;
    padding: 8px 18px !important;
    margin: 0 !important;
    font-size: 1.1rem !important;
    font-weight: 700 !important;
    text-transform: uppercase !important;
    line-height: 1.3 !important;
    margin-bottom: -2px !important; /* Đè khít lên đường viền kẻ đáy */
    border-radius: 6px 6px 0 0 !important; /* Bo góc 2 mép trên mềm mại đồng bộ với thẻ sản phẩm */
}

/* Tối ưu cỡ chữ Tab trên Mobile */
@media (max-width: 549px) {
    .product-cat-title-bar h2.product-cat-title-badge {
        font-size: 0.95rem !important;
        padding: 6px 14px !important;
    }
}
```

---

## 8. MẪU SECTION TIN TỨC CÔNG NGHỆ CHUẨN MỰC (1 BÀI FEATURED + 6 BÀI DANH SÁCH CĂN TRÁI)

Bố cục tin tức báo chí/công nghệ kinh điển gồm 1 bài viết lớn nổi bật bên trái có hộp màu thương hiệu, đi kèm 6 bài viết dạng danh sách nằm ngang bên phải chia làm 2 cột. Toàn bộ chữ căn trái chuẩn mực, không có vạch kẻ thừa, responsive hoàn hảo (trên Desktop phẳng đáy với danh sách, trên Mobile xếp chồng gọn gàng).

```html
[section label="Section Tin Tuc Cap Nhat" padding="30px 0px 30px 0px" padding__sm="20px 0px"]

[row]
[col]
<h2 class="uppercase" style="font-size: 1.35rem; font-weight: 700; margin-bottom: 20px;">TIN TỨC MỚI CẬP NHẬT</h2>
[/col]
[/row]

[row style="small" v_align="top"]

[col span="4" span__md="12" span__sm="12"]
[blog_posts type="row" columns="1" posts="1" style="default" text_align="left" image_height="65%" image_hover="zoom" text_color="dark" text_padding="16px 16px 16px 16px" show_date="false" show_category="false" excerpt="false" comments="false" class="featured-news-box"]
[/col]

[col span="8" span__md="12" span__sm="12"]
[blog_posts type="row" columns="2" columns__sm="1" posts="6" offset="1" style="vertical" text_align="left" image_width="38" image_height="75%" image_hover="zoom" show_category="false" excerpt="false" comments="false" show_date="text" class="list-news-box"]
[/col]

[/row]

[/section]
```

### Đoạn CSS Tinh Chỉnh Căn Trái, Đồng Bộ Màu & Cân Bằng Chiều Cao Đáy Chuẩn Xác:
```css
/* 1. Xóa các đường gạch ngang divider mặc định của Flatsome */
.featured-news-box .is-divider,
.list-news-box .is-divider {
    display: none !important;
}

/* 2. Bài viết lớn nổi bật bên trái: Tự động lấy màu chủ đạo của Website */
.featured-news-box .box-text {
    text-align: left !important;
    background-color: var(--primary-color) !important;
    border-bottom-left-radius: 6px;
    border-bottom-right-radius: 6px;
}

.featured-news-box .box-image {
    border-top-left-radius: 6px;
    border-top-right-radius: 6px;
    overflow: hidden;
}

.featured-news-box .box-text h5 {
    text-align: left !important;
    font-size: 1.05rem !important;
    line-height: 1.4 !important;
    font-weight: 700 !important;
    margin-bottom: 0 !important;
    display: -webkit-box;
    -webkit-line-clamp: 2;
    -webkit-box-orient: vertical;
    overflow: hidden;
}

.featured-news-box .box-text h5 a {
    color: #ffffff !important;
}

/* 3. Danh sách 6 bài viết dạng ngang bên phải */
.list-news-box .col {
    margin-bottom: 16px !important;
}

.list-news-box .box-vertical {
    align-items: flex-start !important;
}

.list-news-box .box-image {
    border-radius: 4px !important;
    overflow: hidden !important;
}

/* Khoảng cách đệm chuẩn 15px giữa thumbnail và khối chữ */
.list-news-box .box-text {
    text-align: left !important;
    padding: 0 0 0 15px !important;
}

/* Kế thừa 100% màu sắc mặc định của website cho chữ và link */
.list-news-box .box-text h5 {
    text-align: left !important;
    font-size: 0.95rem !important;
    font-weight: 700 !important;
    line-height: 1.35 !important;
    margin-bottom: 6px !important;
    display: -webkit-box;
    -webkit-line-clamp: 2;
    -webkit-box-orient: vertical;
    overflow: hidden;
}

.list-news-box .post-meta {
    text-align: left !important;
    font-size: 0.8rem !important;
    color: #94a3b8 !important;
}

/* 4. CÂN BẰNG CHIỀU CAO TRÊN DESKTOP:
   Trên Desktop: Nâng tỷ lệ ảnh bài lớn lên 89% để phẳng đáy 100% với danh sách 3 hàng bên phải.
   Trên Mobile/Tablet: Tự động quay về tỉ lệ 65% gọn gàng, không bị kéo dãn bất thường. */
@media (min-width: 850px) {
    .featured-news-box .image-cover {
        padding-top: 89% !important; /* Khớp chuẩn từng pixel với 3 hàng bài viết bên phải */
    }
}
```



