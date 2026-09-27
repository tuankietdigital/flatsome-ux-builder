# Bộ 12 Template Mẫu Thực Chiến Chuẩn Flatsome 3.20.5 (100% Zero-Comment & Responsive 3 Thiết Bị)

> **Tác giả:** Quách Trần Tuấn Kiệt  
> **Tiêu chuẩn kiểm duyệt:** 100% thuần khiết Shortcode (Tuyệt đối không chứa comment HTML chú thích), tương thích tuyệt đối UX Builder, chuẩn Responsive trên Desktop ($\ge 850\text{px}$), Tablet ($550-849\text{px}$) và Mobile ($< 550\text{px}$).

---

## 1. TEMPLATE 1: HERO BANNER SAAS HIỆN ĐẠI KÈM FLEXBOX CTA BUTTONS
* **Đặc điểm:** Tận dụng `[ux_banner]`, `[text_box]` và `[ux_stack]` để xếp 2 nút CTA ngang trên Desktop và tự chuyển thành dọc trên Mobile mà không vỡ khung.
* **Mã Shortcode:**
```shortcode
[ux_banner height="580px" height__md="480px" height__sm="400px" bg_color="rgb(18, 24, 38)" bg_overlay="rgba(0, 0, 0, 0.35)"]
  [text_box width="65" width__md="80" width__sm="90" position_x="50" position_y="50" text_align="center" text_color="light" animate="fadeInUp"]
    <h1 class="uppercase">Giải Pháp Đột Phá Cho Doanh Nghiệp</h1>
    <p class="lead">Tự động hóa quy trình quản trị, tối ưu hóa chi phí vận hành và tăng trưởng doanh thu vượt bậc ngay trong 90 ngày.</p>
    [gap height="20px" height__sm="10px"]
    [ux_stack direction="row" direction__sm="col" distribute="center" align="center" gap="1rem" gap__sm="0.5rem"]
      [button text="Dùng Thử Miễn Phí" size="large" radius="5" depth="2"]
      [button text="Xem Video Demo" color="white" style="outline" size="large" radius="5"]
    [/ux_stack]
  [/text_box]
[/ux_banner]
```

---

## 2. TEMPLATE 2: SECTION CHÂN ĐỒ HỌA LƯỢN SÓNG (SVG WAVES SHAPE DIVIDER)
* **Đặc điểm:** Sử dụng tính năng Shape Divider native `divider="waves"` của Flatsome 3.20.5 kết hợp `[col force_first="small"]` để đưa ảnh lên trước trên Mobile.
* **Mã Shortcode:**
```shortcode
[section label="Wave Hero" bg_color="rgb(244, 247, 250)" padding="80px 0px 100px 0px" padding__sm="50px 0px 70px 0px" divider="waves" divider_height="70px" divider_height__sm="40px" divider_fill="rgb(255, 255, 255)"]
  [row v_align="middle"]
    [col span="6" span__md="6" span__sm="12" class="text-center-small"]
      <span style="color: var(--primary-color); font-weight: 700; text-transform: uppercase; letter-spacing: 1px;">Công Nghệ Tương Lai</span>
      <h2>Kiến Tạo Giá Trị Bền Vững Cùng Chuyên Gia Hàng Đầu</h2>
      <p>Hơn 10 năm kinh nghiệm đồng hành cùng 500+ doanh nghiệp lớn trong và ngoài nước kiến thiết hệ sinh thái số toàn diện.</p>
      [gap height="15px"]
      [ux_stack direction="row" direction__sm="col" distribute="start" distribute__sm="center" align="center" gap="1rem"]
        [button text="Khám Phá Dịch Vụ" radius="99"]
        [button text="Liên Hệ Hotline" style="outline" radius="99"]
      [/ux_stack]
    [/col]
    [col span="6" span__md="6" span__sm="12" force_first="small"]
      [ux_image image_size="large" depth="3" depth_hover="5"]
    [/col]
  [/row]
[/section]
```

---

## 3. TEMPLATE 3: LƯỚI 4 CỘT DỊCH VỤ / TÍNH NĂNG (FEATURE CARDS GRID)
* **Đặc điểm:** Lưới 4 cột Desktop ($3 \times 4 = 12$), tự chuyển thành 2 cột Tablet ($6 \times 2 = 12$) và 1 cột Mobile ($12$).
* **Mã Shortcode:**
```shortcode
[section label="Features Grid" padding="60px 0px 60px 0px" padding__sm="40px 0px 40px 0px"]
  [row h_align="center"]
    [col span="8" span__sm="12" align="center"]
      [title style="center" text="Dịch Vụ Cốt Lõi" tag_name="h2"]
      <p>Cam kết chất lượng dịch vụ chuẩn quốc tế với lộ trình triển khai minh bạch và bảo mật 100%.</p>
    [/col]
  [/row]
  [row style="normal" v_align="equal-height"]
    [col span="3" span__md="6" span__sm="12"]
      [featured_box img_width="60" pos="center" title="Chiến Lược Số" icon_border="2" depth="1" depth_hover="3"]
        <p>Lập bản đồ lộ trình chuyển đổi số tối ưu theo từng giai đoạn phát triển doanh nghiệp.</p>
      [/featured_box]
    [/col]
    [col span="3" span__md="6" span__sm="12"]
      [featured_box img_width="60" pos="center" title="Thiết Kế Web UI/UX" icon_border="2" depth="1" depth_hover="3"]
        <p>Giao diện hiện đại, tối ưu trải nghiệm người dùng và gia tăng tỉ lệ chuyển đổi đơn hàng.</p>
      [/featured_box]
    [/col]
    [col span="3" span__md="6" span__sm="12"]
      [featured_box img_width="60" pos="center" title="Tối Ưu SEO & Content" icon_border="2" depth="1" depth_hover="3"]
        <p>Thống trị kết quả tìm kiếm Google với cấu trúc chuẩn E-E-A-T và Semantic Search.</p>
      [/featured_box]
    [/col]
    [col span="3" span__md="6" span__sm="12"]
      [featured_box img_width="60" pos="center" title="Bảo Trì 24/7" icon_border="2" depth="1" depth_hover="3"]
        <p>Hệ thống giám sát vận hành liên tục, sao lưu dữ liệu tự động và khắc phục sự cố tức thì.</p>
      [/featured_box]
    [/col]
  [/row]
[/section]
```

---

## 4. TEMPLATE 4: TIN TỨC TẠP CHÍ CÂN BẰNG CHIỀU CAO (MAGAZINE BLOG LAYOUT)
* **Đặc điểm:** Cột trái là 1 Card lớn cân bằng chiều cao với 3 bài viết nhỏ bên phải (`image_height="89%"` Desktop và `65%` Mobile). Đệm lót thẻ dọc `padding: 0 0 0 15px !important;` chống dính chữ.
* **Mã Shortcode:**
```shortcode
[section label="Magazine News" padding="50px 0px 50px 0px" padding__sm="30px 0px 30px 0px"]
  [row]
    [col span="12" span__sm="12"]
      [title style="bold" text="Tin Tức & Phân Tích Chuyên Sâu" tag_name="h2" link_text="Xem tất cả bài viết >"]
    [/col]
  [/row]
  [row]
    [col span="6" span__md="6" span__sm="12" class="featured-post-card"]
      [blog_posts posts="1" columns="1" style="default" image_height="89%" show_date="true" excerpt="true" excerpt_length="25" text_align="left"]
    [/col]
    [col span="6" span__md="6" span__sm="12" class="box-vertical-list"]
      [blog_posts offset="1" posts="3" columns="1" style="vertical" image_width="38" image_height="75%" show_date="true" excerpt="false" text_align="left"]
    [/col]
  [/row]
[/section]
```

---

## 5. TEMPLATE 5: BẢNG GIÁ DỊCH VỤ CHUYỂN ĐỔI CAO (SAAS PRICING TABLE)
* **Đặc điểm:** Sử dụng shortcode native `[ux_price_table]` và `[bullet_item]` của Flatsome 3.20.5 với cột trung tâm `featured="true"`.
* **Mã Shortcode:**
```shortcode
[section label="Pricing Table" bg_color="rgb(248, 250, 252)" padding="60px 0px 60px 0px" padding__sm="40px 0px 40px 0px"]
  [row h_align="center"]
    [col span="8" span__sm="12" align="center"]
      [title style="center" text="Bảng Giá Dịch Vụ Minh Bạch" tag_name="h2"]
      <p>Lựa chọn gói giải pháp phù hợp nhất với quy mô và mục tiêu tăng trưởng của bạn.</p>
    [/col]
  [/row]
  [row style="normal" v_align="middle"]
    [col span="4" span__md="6" span__sm="12"]
      [ux_price_table title="Gói Khởi Nghiệp" price="499.000đ" description="Dành cho cá nhân & doanh nghiệp nhỏ"]
        [bullet_item text="Miễn phí 01 Tên miền Quốc tế"]
        [bullet_item text="Lưu trữ SSD 5GB Siêu Tốc"]
        [bullet_item text="Bảo mật SSL Trọn đời"]
        [bullet_item text="Hỗ trợ kỹ thuật qua Email"]
        [gap height="15px"]
        [button text="Đăng Ký Ngay" style="outline" expand="true" radius="5"]
      [/ux_price_table]
    [/col]
    [col span="4" span__md="6" span__sm="12"]
      [ux_price_table title="Gói Doanh Nghiệp" price="1.299.000đ" description="Lựa chọn phổ biến nhất" featured="true" bg_color="rgb(255, 255, 255)"]
        [bullet_item text="Tên miền Quốc tế & Quốc gia"]
        [bullet_item text="Lưu trữ SSD 20GB Không Giới Hạn Băng Thông"]
        [bullet_item text="Hạ tầng Cloud Backup Hàng Ngày"]
        [bullet_item text="Tối ưu SEO On-Page Tự Động"]
        [bullet_item text="Hỗ trợ ưu tiên 24/7 qua Hotline/Zalo"]
        [gap height="15px"]
        [button text="Chọn Gói Này" size="large" expand="true" radius="5" depth="2"]
      [/ux_price_table]
    [/col]
    [col span="4" span__md="12" span__sm="12"]
      [ux_price_table title="Gói Tập Đoàn" price="3.499.000đ" description="Dành cho hệ thống quy mô lớn"]
        [bullet_item text="Hạ tầng Server Riêng Dedicated"]
        [bullet_item text="Lưu trữ SSD NVMe Không Giới Hạn"]
        [bullet_item text="Tường lửa Chống DDoS Độc Quyền"]
        [bullet_item text="Kỹ sư chuyên trách quản trị 1:1"]
        [gap height="15px"]
        [button text="Liên Hệ Tư Vấn" style="outline" expand="true" radius="5"]
      [/ux_price_table]
    [/col]
  [/row]
[/section]
```

---

## 6. TEMPLATE 6: HỎI ĐÁP FAQ TỰ ĐỘNG XUẤT GOOGLE FAQ SCHEMA
* **Đặc điểm:** Tận dụng `faq_schema="true"` trong Flatsome 3.20.5 để tự động xuất dữ liệu có cấu trúc Rich Snippet FAQPage lên Google Search.
* **Mã Shortcode:**
```shortcode
[section label="FAQ Schema Section" padding="50px 0px 50px 0px"]
  [row h_align="center"]
    [col span="10" span__sm="12"]
      [title style="center" text="Câu Hỏi Thường Gặp (FAQ)" tag_name="h2"]
      [accordion auto_open="true" faq_schema="true"]
        [accordion-item title="Dịch vụ của chúng tôi mất bao lâu để hoàn thành?"]
          <p>Thời gian triển khai trung bình từ 7 đến 14 ngày làm việc tùy thuộc vào quy mô và yêu cầu tính năng cụ thể của dự án.</p>
        [/accordion-item]
        [accordion-item title="Tôi có được bàn giao toàn bộ mã nguồn website không?"]
          <p>Có. Bạn sẽ được bàn giao 100% mã nguồn, tài khoản quản trị máy chủ và video hướng dẫn sử dụng chi tiết sau khi nghiệm thu.</p>
        [/accordion-item]
        [accordion-item title="Hệ thống có tương thích hoàn hảo trên điện thoại di động không?"]
          <p>Chắc chắn. Toàn bộ giao diện đều được kiểm thử nghiêm ngặt theo tiêu chuẩn Mobile-First và đạt điểm tối ưu Core Web Vitals của Google.</p>
        [/accordion-item]
        [accordion-item title="Chính sách bảo hành và hỗ trợ sau bàn giao như thế nào?"]
          <p>Chúng tôi cam kết bảo hành kỹ thuật trọn đời đối với các lỗi phát sinh từ hệ thống mã nguồn ban đầu và hỗ trợ kỹ thuật 24/7.</p>
        [/accordion-item]
      [/accordion]
    [/col]
  [/row]
[/section]
```

---

## 7. TEMPLATE 7: TRANG CHI TIẾT SẢN PHẨM WOOCOMMERCE TÙY BIẾN
* **Đặc điểm:** Dùng trọn bộ 13 elements Custom Product của Flatsome 3.20.5 để tạo trang bán hàng chuyển đổi cao.
* **Mã Shortcode:**
```shortcode
[section label="Custom Product Layout" padding="30px 0px 60px 0px"]
  [row]
    [col span="12" span__sm="12"]
      [ux_product_breadcrumbs size="small"]
    [/col]
  [/row]
  [row style="large"]
    [col span="6" span__md="6" span__sm="12"]
      [ux_product_gallery style="normal"]
    [/col]
    [col span="6" span__md="6" span__sm="12"]
      [ux_product_title size="xlarge" uppercase="false"]
      [ux_product_rating style="inline"]
      [ux_product_price size="large"]
      [divider width="100%" height="1px" margin_top="10px" margin_bottom="15px"]
      [ux_product_excerpt]
      [gap height="10px"]
      [ux_product_add_to_cart style="flat" size="large"]
      [divider width="100%" height="1px" margin_top="20px" margin_bottom="15px"]
      [ux_product_meta]
    [/col]
  [/row]
  [gap height="30px"]
  [row]
    [col span="12" span__sm="12"]
      [ux_product_tabs style="tabs" align="left"]
    [/col]
  [/row]
  [gap height="30px"]
  [row]
    [col span="12" span__sm="12"]
      [title style="bold" text="Sản Phẩm Tương Tự" tag_name="h3"]
      [ux_product_related style="slider"]
    [/col]
  [/row]
[/section]
```

---

## 8. TEMPLATE 8: FLASH SALE CAROUSEL KÈM ĐỒNG HỒ ĐẾM NGƯỢC
* **Đặc điểm:** Kết hợp `[ux_countdown]` và `[ux_products type="slider"]`.
* **Mã Shortcode:**
```shortcode
[section label="Flash Sale" bg_color="rgb(238, 77, 45)" dark="true" padding="40px 0px 40px 0px"]
  [row v_align="middle"]
    [col span="6" span__md="6" span__sm="12" class="text-center-small"]
      <h2 style="margin-bottom: 5px;">🔥 SIÊU SALE GIỜ VÀNG</h2>
      <p style="margin-bottom: 0;">Ưu đãi giảm giá lên đến 50% cho các sản phẩm công nghệ bán chạy.</p>
    [/col]
    [col span="6" span__md="6" span__sm="12" align="right"]
      [ux_countdown year="2026" month="12" day="31" time="23:59" style="clock" size="medium"]
    [/col]
  [/row]
  [gap height="20px"]
  [ux_products type="slider" columns="4" columns__md="3" columns__sm="2" col_spacing="small" show="onsale" orderby="sales" products="8"]
[/section]
```

---

## 9. TEMPLATE 9: CHÂN TRANG 4 CỘT CHUẨN MENU NATIVE (`ux_menu`)
* **Đặc điểm:** Xây dựng cột thông tin Footer bằng `[ux_menu]`, `[ux_menu_title]`, `[ux_menu_link]` và mạng xã hội `[follow]`.
* **Mã Shortcode:**
```shortcode
[section label="Footer Columns" bg_color="rgb(15, 23, 42)" dark="true" padding="60px 0px 40px 0px"]
  [row]
    [col span="4" span__md="6" span__sm="12"]
      <h4 class="uppercase">Về Chúng Tôi</h4>
      <p>Thương hiệu cung cấp giải pháp công nghệ và thiết kế giao diện web hàng đầu Việt Nam.</p>
      [follow style="small" facebook="https://facebook.com" instagram="https://instagram.com" tiktok="https://tiktok.com" youtube="https://youtube.com"]
    [/col]
    [col span="3" span__md="6" span__sm="12"]
      [ux_menu divider="solid"]
        [ux_menu_title text="Giải Pháp"]
        [ux_menu_link text="Thiết kế Website Flatsome" link="/thiet-ke-web"]
        [ux_menu_link text="Dịch vụ SEO E-E-A-T" link="/dich-vu-seo"]
        [ux_menu_link text="Tối ưu Tốc độ Tải Trang" link="/toi-uu-toc-do"]
        [ux_menu_link text="Bảo trì & Chăm sóc Web" link="/bao-tri-web"]
      [/ux_menu]
    [/col]
    [col span="3" span__md="6" span__sm="12"]
      [ux_menu divider="solid"]
        [ux_menu_title text="Chính Sách"]
        [ux_menu_link text="Chính sách bảo mật" link="/chinh-sach-bao-mat"]
        [ux_menu_link text="Điều khoản sử dụng" link="/dieu-khoan"]
        [ux_menu_link text="Quy định thanh toán" link="/thanh-toan"]
        [ux_menu_link text="Chính sách hoàn tiền" link="/hoan-tien"]
      [/ux_menu]
    [/col]
    [col span="2" span__md="6" span__sm="12"]
      <h4 class="uppercase">Hotline Hỗ Trợ</h4>
      <p style="font-size: 1.25rem; font-weight: 700; color: #22c55e;">1900 xxxx</p>
      <p>support@domain.com</p>
      <p>Thứ 2 - Thứ 7: 8h00 - 18h00</p>
    [/col]
  [/row]
[/section]
```

---

## 10. TEMPLATE 10: ĐỘI NGŨ NHÂN SỰ CHUYÊN NGHIỆP (`team_member`)
* **Đặc điểm:** Sử dụng element `[team_member]` native với ảnh đại diện bo tròn và thông tin chức vụ.
* **Mã Shortcode:**
```shortcode
[section label="Team Showcase" padding="60px 0px 60px 0px"]
  [row h_align="center"]
    [col span="8" span__sm="12" align="center"]
      [title style="center" text="Đội Ngũ Chuyên Gia" tag_name="h2"]
      <p>Những con người tận tâm, nhiệt huyết và giàu kinh nghiệm tạo nên thành công của mỗi dự án.</p>
    [/col]
  [/row]
  [row]
    [col span="3" span__md="6" span__sm="12"]
      [team_member name="Nguyễn Văn A" title="Giám Đốc Kỹ Thuật" image_height="100%" image_width="80" image_radius="100"]
        <p>12 năm kinh nghiệm kiến trúc hệ thống và an ninh mạng.</p>
      [/team_member]
    [/col]
    [col span="3" span__md="6" span__sm="12"]
      [team_member name="Trần Thị B" title="Trưởng Phòng UI/UX" image_height="100%" image_width="80" image_radius="100"]
        <p>Chuyên gia thiết kế trải nghiệm người dùng đạt giải thưởng quốc tế.</p>
      [/team_member]
    [/col]
    [col span="3" span__md="6" span__sm="12"]
      [team_member name="Lê Hoàng C" title="Senior SEO Strategist" image_height="100%" image_width="80" image_radius="100"]
        <p>Chiến lược gia tăng trưởng lưu lượng truy cập hữu cơ đa kênh.</p>
      [/team_member]
    [/col]
    [col span="3" span__md="6" span__sm="12"]
      [team_member name="Phạm Minh D" title="Chuyên Viên Tư Vấn" image_height="100%" image_width="80" image_radius="100"]
        <p>Đồng hành cùng khách hàng tìm kiếm giải pháp tối ưu chi phí.</p>
      [/team_member]
    [/col]
  [/row]
[/section]
```

---

## 11. TEMPLATE 11: DỰ ÁN TIÊU BIỂU KÈM BỘ LỌC ISOTOPE (`ux_portfolio`)
* **Đặc điểm:** Dùng `[ux_portfolio]` với `filter="true"` và `filter_nav="line-grow"`.
* **Mã Shortcode:**
```shortcode
[section label="Portfolio Showcase" padding="60px 0px 60px 0px"]
  [row h_align="center"]
    [col span="8" span__sm="12" align="center"]
      [title style="center" text="Dự Án Đã Thực Hiện" tag_name="h2"]
      <p>Khám phá các sản phẩm sáng tạo và dự án số tiêu biểu được chúng tôi hoàn thiện.</p>
    [/col]
  [/row]
  [ux_portfolio style="shade" filter="true" filter_nav="line-grow" filter_align="center" columns="3" columns__md="2" columns__sm="1" col_spacing="normal" image_height="75%" image_hover="zoom" lightbox="true"]
[/section]
```

---

## 12. TEMPLATE 12: BANNER GHIM ĐIỂM SẢN PHẨM TƯƠNG TÁC (`ux_hotspot`)
* **Đặc điểm:** Banner hình ảnh chụp không gian nội thất có các chấm tròn `[ux_hotspot]` nhấp nháy dẫn link trực tiếp vào sản phẩm.
* **Mã Shortcode:**
```shortcode
[ux_banner height="520px" height__sm="350px" bg_color="rgb(240, 240, 240)"]
  [ux_hotspot type="text" text="Ghế Sofa Da Cao Cấp - 8.500.000đ" link="/san-pham/sofa" position_x="35" position_y="65" animate="bounce"]
  [ux_hotspot type="text" text="Đèn Bàn Scandinavian - 1.200.000đ" link="/san-pham/den-ban" position_x="68" position_y="40" animate="bounce"]
  [text_box width="35" width__sm="70" position_x="10" position_y="15" text_align="left"]
    <span style="font-weight: 700; text-transform: uppercase;">Bộ Sưu Tập Mới</span>
    <h3>Không Gian Sống Hiện Đại</h3>
    <p>Chạm vào từng điểm ghim để xem chi tiết sản phẩm.</p>
  [/text_box]
[/ux_banner]
```
