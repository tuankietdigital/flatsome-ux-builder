# Danh Mục 86 Core Elements Schema Chuẩn Flatsome 3.20.5 (Ground Truth)

> **Tác giả:** Quách Trần Tuấn Kiệt  
> **Nguồn thẩm định:** Trực tiếp từ mã nguồn PHP gốc theme Flatsome v3.20.5 (`inc/builder/shortcodes/` & `inc/shortcodes/`).  
> **Nguyên tắc cốt lõi:** 100% không ảo giác (Zero Hallucination), đúng chính xác tên thuộc tính, kiểu dữ liệu, giá trị mặc định và hậu tố Responsive (`__md`, `__sm`).

---

## 📑 BẢNG TRA CỨU HẬU TỐ RESPONSIVE (NATIVE RESPONSIVE SUFFIXES)

Trong Flatsome 3.20.5, các thuộc tính có cờ `'responsive' => true` trong schema PHP được chia làm 3 mốc thiết bị:
* Không có hậu tố: Áp dụng cho **Desktop** ($\ge 850\text{px}$)
* Hậu tố `__md`: Áp dụng riêng cho **Tablet** ($550\text{px} - 849\text{px}$)
* Hậu tố `__sm`: Áp dụng riêng cho **Mobile** ($< 550\text{px}$)

```shortcode
[col span="4" span__md="6" span__sm="12" padding="20px" padding__sm="10px"]
[ux_stack direction="row" direction__sm="col" gap="1.5rem" gap__sm="0.75rem"]
```

---

## NHÓM 1: BỐ CỤC LƯỚI & KHUNG CHỨA (LAYOUT & GRID SYSTEM)

### 1.1. `[section]` — Khung Chứa Toàn Chiều Ngang (Full-Width Section)
* **File nguồn:** `inc/builder/shortcodes/section.php`
* **Loại thẻ:** Container (`wrap="false"`). Cho phép chứa `[row]`, `[ux_stack]`, `[ux_banner]`, `[title]`, `[gap]`...
* **Các thuộc tính quan trọng:**
  * `label`: Tên định danh quản trị (Admin label).
  * `bg`: ID hoặc URL hình ảnh nền.
  * `bg_color`: Màu nền (mã hex `#fff` hoặc `rgb(245, 245, 245)`).
  * `bg_overlay`: Màu lớp phủ (`rgba(0, 0, 0, 0.4)`).
  * `dark`: `true` (chữ trắng cho nền tối) | `false` (chữ đen cho nền sáng).
  * `padding`: Khoảng đệm (`30px`, `60px 0px 60px 0px`). **Hỗ trợ responsive:** `padding`, `padding__md`, `padding__sm`.
  * `height`: Chiều cao tối thiểu (`300px`, `100vh`). **Hỗ trợ responsive:** `height`, `height__md`, `height__sm`.
  * `margin`: Lề ngoài (`0px`, `-50px 0 0 0`).
  * `border`: Kẻ viền (`1px 0px 1px 0px`).
  * `border_color`: Màu viền (`rgb(235, 235, 235)`).
  * `sticky`: `true` | `""` (bám dính khi cuộn).
  * `scroll_for_more`: `true` | `""` (hiện icon mũi tên cuộn xuống).
  * `class`: Class CSS tùy biến.

#### 🌊 Bộ Shape Dividers SVG Native Trong `[section]` (Flatsome 3.20.5):
Hỗ trợ 20 mẫu SVG đáy (`divider`) và đỉnh (`divider_top`):
* **Danh sách shape:** `waves`, `waves-opacity`, `waves-opacity-2`, `waves-opacity-3`, `curve`, `curve-invert`, `curve-2`, `curve-2-invert`, `curve-opacity`, `arrow`, `arrow-invert`, `arrow-2`, `arrow-2-invert`, `tilt`, `triangle`, `triangle-invert`, `triangle-opacity`, `fan`, `book`, `book-invert`.
* **Thuộc tính đáy:** `divider="waves"` | `divider_height="100px"` (hỗ trợ `__md`, `__sm`) | `divider_width="100"` (%) | `divider_fill="rgb(255,255,255)"` | `divider_flip="true"` | `divider_to_front="true"`.
* **Thuộc tính đỉnh:** `divider_top="curve"` | `divider_top_height="80px"` | `divider_top_fill="rgb(255,255,255)"` | `divider_top_flip="true"`.

---

### 1.2. `[row]` — Hàng Lưới 12 Cột (Grid Row)
* **File nguồn:** `inc/builder/shortcodes/row.php`
* **QUY TẮC BẮT BUỘC:** `'allow' => array( 'col' )` — `[row]` **CHỈ ĐƯỢC CHỨA `[col]` TRỰC TIẾP**.
* **Các thuộc tính:**
  * `style`: Khoảng cách giữa các cột (`collapse` = 0px, `small` = 10px, `normal` = 30px, `large` = 60px).
  * `width`: Chiều rộng hàng (`custom` = theo khung web 1080/1200px | `full-width` = tràn 100% màn hình).
  * `col_bg`: Màu nền áp dụng cho tất cả các cột con.
  * `col_bg_radius`: Bo góc tất cả các cột con (`0` đến `100px`).
  * `v_align`: Căn lề dọc (`top`, `middle`, `bottom`, `equal-height`).
  * `h_align`: Căn lề ngang (`left`, `center`, `right`).
  * `depth`: Đổ bóng (`0` đến `5`).
  * `depth_hover`: Đổ bóng khi hover (`0` đến `5`).
  * `class`: Class CSS tùy biến.

---

### 1.3. `[col]` — Cột Lưới (Grid Column)
* **File nguồn:** `inc/builder/shortcodes/col.php`
* **QUY TẮC BẮT BUỘC:** `'require' => array( 'row' )` — `[col]` **PHẢI NẰM TRONG `[row]` HOẶC `[row_inner]`**.
* **Các thuộc tính:**
  * `span`: Độ rộng cột trên Desktop (1-12). **Tổng các cột trong một hàng trên Desktop phải bằng 12**.
  * `span__md`: Độ rộng cột trên Tablet ($550-849\text{px}$). Thường là `6` hoặc `12`.
  * `span__sm`: Độ rộng cột trên Mobile ($<550\text{px}$). **Mặc định bắt buộc: `span__sm="12"`** (trừ bố cục 2 cột sản phẩm/ảnh `span__sm="6"`).
  * `force_first`: Đảo vị trí cột ưu tiên lên đầu mà không cần CSS:
    * `force_first="small"`: Đẩy cột lên đầu tiên trên **Mobile**.
    * `force_first="medium"`: Đẩy cột lên đầu tiên trên **Tablet**.
  * `padding`: Padding (`20px 20px 20px 20px`). **Hỗ trợ:** `padding`, `padding__md`, `padding__sm`.
  * `margin`: Margin (`0px 0px 20px 0px`). **Hỗ trợ:** `margin`, `margin__md`, `margin__sm`.
  * `align`: Căn lề text (`left`, `center`, `right`).
  * `bg_color`: Màu nền (`rgb(...)`).
  * `bg_radius`: Bo viền góc nền (`px`).
  * `color`: Màu chữ (`light` = chữ trắng cho nền tối, `dark` = chữ đen cho nền sáng).
  * `max_width`: Chiều rộng tối đa (`500px`). **Hỗ trợ:** `max_width`, `max_width__md`, `max_width__sm`.
  * `sticky`: Bám dính (`true` | `""`).
  * `sticky_mode`: Chế độ bám (`""` = CSS native | `javascript` = JS nâng cao cho nội dung dài).
  * `animate`: Hiệu ứng xuất hiện (`fadeInUp`, `fadeInLeft`, `fadeInRight`, `bounceIn`...).
  * `border`: Viền (`1px 1px 1px 1px`).
  * `border_color`: Màu viền.
  * `border_radius`: Bo góc viền.

---

### 1.4. `[row_inner]` & `[col_inner]` — Lồng Lưới Đồng Cấp (Self-Nesting)
* **File nguồn:** `inc/builder/core/server/src/Transformers/ArrayToString.php` (dòng 128-135)
* **Quy chuẩn:** Khi muốn chia cột bên trong một `[col]`, **BẮT BUỘC** phải dùng `[row_inner]` và `[col_inner]`.
* **Cú pháp chuẩn:**
```shortcode
[row]
  [col span="8" span__sm="12"]
    [row_inner]
      [col_inner span="6" span__sm="12"][ux_image][/col_inner]
      [col_inner span="6" span__sm="12"][text]Nội dung[/text][/col_inner]
    [/row_inner]
  [/col]
  [col span="4" span__sm="12"]Sidebar[/col]
[/row]
```

---

### 1.5. `[ux_stack]` — Modern Flexbox Container (Đột phá Flatsome 3.20.5)
* **File nguồn:** `inc/builder/shortcodes/ux_stack.php`
* **Loại thẻ:** Flexbox Container (`type="container"`).
* **Mục đích:** Bố trí các component nhỏ (2 nút bấm CTA, cụm avatar + thông tin tác giả, icon + text) cực kỳ thanh thoát mà không làm phình to DOM như `[row]` + `[col]`.
* **Thuộc tính & Hậu tố Responsive:**
  * `direction`: Hướng dàn thẻ (`row` = ngang, `col` = dọc). **Hỗ trợ:** `direction`, `direction__md`, `direction__sm`.
  * `distribute`: Căn chỉnh trục chính (justify-content): `start`, `center`, `end`, `between` (space-between), `around`. **Hỗ trợ:** `distribute`, `distribute__md`, `distribute__sm`.
  * `align`: Căn lề trục phụ (align-items): `stretch`, `start`, `center`, `end`, `baseline`. **Hỗ trợ:** `align`, `align__md`, `align__sm`.
  * `gap`: Khoảng cách giữa các phần tử con (`0` đến `16rem`, bước nhảy `0.25rem`). **Hỗ trợ:** `gap`, `gap__md`, `gap__sm`.
  * `class`: Class CSS tùy biến.

* **Ví dụ mẫu CTA Buttons chuẩn Responsive:**
```shortcode
[ux_stack direction="row" direction__sm="col" distribute="start" align="center" gap="1rem" gap__sm="0.5rem"]
  [button text="Xem Dự Án" size="large" radius="5"]
  [button text="Liên Hệ Báo Giá" color="secondary" style="outline" size="large" radius="5"]
[/ux_stack]
```

---

### 1.6. `[gap]` — Khoảng Trống Cách Dòng Responsive
* **File nguồn:** `inc/builder/shortcodes/gap.php`
* **Thuộc tính:**
  * `height`: Chiều cao Desktop (`30px`).
  * `height__md`: Chiều cao Tablet (`20px`).
  * `height__sm`: Chiều cao Mobile (`15px`).

---

## NHÓM 2: BANNER, SLIDER & HÌNH ẢNH (VISUAL MEDIA)

### 2.1. `[ux_banner]` — Hero Banner Chuyên Nghiệp
* **File nguồn:** `inc/builder/shortcodes/ux_banner.php`
* **QUY TẮC BẮT BUỘC:** `'allow' => array( 'text_box', 'ux_image', 'ux_lottie' )` — Chỉ cho phép chứa `text_box`, `ux_image` và `ux_lottie`. Muốn đặt nút hay text, **bắt buộc bọc trong `[text_box]`**.
* **Các thuộc tính:**
  * `height`: Chiều cao banner (`500px`, `100vh`, `60%`). **Hỗ trợ:** `height`, `height__md`, `height__sm`.
  * `bg`: ID hoặc URL hình ảnh nền.
  * `bg_color`: Màu nền.
  * `bg_overlay`: Màu lớp phủ (`rgba(0, 0, 0, 0.4)`).
  * `bg_pos`: Vị trí ảnh nền (`center center`, `top center`, `bottom center`).
  * `parallax`: Hiệu ứng cuộn thị sai (`0` đến `10`).
  * `effect`: Hiệu ứng nền (`snow`, `sparkle`, `rain`, `confetti`, `sliding-glass`).

---

### 2.2. `[text_box]` — Hộp Văn Bản Trên Banner
* **File nguồn:** `inc/builder/shortcodes/text_box.php`
* **QUY TẮC BẮT BUỘC:** `'require' => array( 'ux_banner' )` — Phải nằm trong `[ux_banner]`.
* **Các thuộc tính:**
  * `width`: Độ rộng theo % (`40` đến `100`). **Hỗ trợ:** `width`, `width__md`, `width__sm`.
  * `position_x`: Vị trí ngang theo % (`0` đến `100`: `50` là chính giữa, `10` là sát trái, `90` là sát phải). **Hỗ trợ:** `position_x`, `position_x__md`, `position_x__sm`.
  * `position_y`: Vị trí dọc theo % (`0` đến `100`: `50` là chính giữa, `10` là trên đỉnh, `90` là sát đáy). **Hỗ trợ:** `position_y`, `position_y__md`, `position_y__sm`.
  * `text_align`: Căn lề chữ (`left`, `center`, `right`).
  * `text_color`: `light` (chữ trắng) | `dark` (chữ đen).
  * `bg`: Màu nền hộp văn bản (`rgba(255, 255, 255, 0.9)`).
  * `padding`: Đệm lót (`20px 20px 20px 20px`).
  * `radius`: Bo góc (`0` đến `30px`).
  * `animate`: Hiệu ứng xuất hiện (`fadeInUp`, `flipInX`...).

---

### 2.3. `[ux_image]` — Hình Ảnh Chuẩn Flatsome
* **File nguồn:** `inc/builder/shortcodes/ux_image.php`
* **QUY TẮC VÀNG ASPECT RATIO:** Chiều cao ảnh được quản lý qua `padding-top: {{ value }}` trên container `.image-cover`. Tuyệt đối không can thiệp CSS làm đè bẹp `padding-top`.
* **Các thuộc tính:**
  * `id`: ID ảnh trong WordPress Media Library.
  * `image_size`: Kích thước ảnh (`thumbnail`, `medium`, `large`, `original`).
  * `width`: Độ rộng % (`100`, `80`). **Hỗ trợ:** `width`, `width__md`, `width__sm`.
  * `height`: Chiều cao hoặc tỉ lệ khung hình (`56.25%`, `75%`, `100%`, `300px`).
  * `margin`: Lề ảnh (`0px 0px 15px 0px`).
  * `image_hover`: Hiệu ứng hover (`zoom`, `zoom-fade`, `glow`, `color`, `fade-in`, `blur`...).
  * `image_hover_alt`: Hiệu ứng hover phụ.
  * `lightbox`: Mở ảnh phóng to dạng popup (`true` | `""`).
  * `link`: Link gắn vào ảnh.
  * `target`: `_blank` | `_self`.

---

### 2.4. `[ux_slider]` — Slider / Carousel Đa Năng
* **File nguồn:** `inc/builder/shortcodes/ux_slider.php`
* **Thẻ con cho phép:** `'allow' => array( 'ux_banner','ux_image','ux_lottie','section','row','ux_banner_grid','logo' )`.
* **Thuộc tính:**
  * `type`: Kiểu chuyển slide (`slide`, `fade`).
  * `slide_width`: Chiều rộng mỗi slide (px). **Hỗ trợ:** `slide_width`, `slide_width__md`, `slide_width__sm`.
  * `slide_align`: Căn lề slide (`center`, `left`, `right`).
  * `arrows`: Hiện mũi tên điều hướng (`true` | `false`).
  * `arrow_style`: Kiểu mũi tên (`circle`, `simple`).
  * `bullets`: Hiện dấu chấm chuyển trang (`true` | `false`).
  * `bullet_style`: Kiểu chấm (`circle`, `dashes`).
  * `auto_slide`: Tự động chạy (`true` | `false`).
  * `timer`: Thời gian chuyển mỗi slide (`4000` = 4 giây).
  * `infinitive`: Vòng lặp vô tận (`true` | `false`).
  * `mobile`: Bật chạy trên Mobile (`true` | `false`).

---

### 2.5. `[ux_lottie]` — Trình Chạy Hoạt Ảnh Lottie JSON Vector (Mới 3.20.5)
* **File nguồn:** `inc/builder/shortcodes/ux_lottie.php`
* **Thuộc tính:**
  * `path`: URL file Lottie animation `.json`.
  * `loop`: Lặp lại liên tục (`true` | `false`).
  * `autoplay`: Tự động chạy (`true` | `false`).
  * `trigger`: Kích hoạt phát hoạt ảnh (`hover`, `click`, `scroll`, `""` = static).
  * `mouseout`: Hành vi khi chuột rời đi (`reverse`, `pause`, `stop`).
  * `width`: Chiều rộng (`100%`, `300px`). **Hỗ trợ responsive**.
  * `height`: Chiều cao (`100%`, `300px`). **Hỗ trợ responsive**.
  * `speed`: Tốc độ (`1`, `1.5`, `2`).

---

### 2.6. `[ux_hotspot]` — Ghim Điểm Tương Tác Hình Ảnh (Shoppable Hotspot)
* **File nguồn:** `inc/builder/shortcodes/ux_hotspot.php`
* **Yêu cầu:** Phải nằm trong `[ux_banner]`.
* **Thuộc tính:**
  * `type`: `text` (hiện văn bản/link) | `product` (hiện thẻ sản phẩm WooCommerce).
  * `prod_id`: ID sản phẩm WooCommerce (khi `type="product"`).
  * `text`: Chữ hiển thị khi rê chuột vào điểm ghim.
  * `link`: Link chuyển tiếp.
  * `position_x`: Vị trí ngang % (`0` đến `100`).
  * `position_y`: Vị trí dọc % (`0` đến `100`).
  * `animate`: Hiệu ứng nhấp nháy thu hút chú ý.

---

## NHÓM 3: NỘI DUNG, TYPOGRAPHY & CHUYỂN ĐỔI (CONTENT & CRO)

### 3.1. `[ux_text]` — Typography Chuyên Sâu (Flatsome 3.20.5)
* **File nguồn:** `inc/builder/shortcodes/text.php`
* **Mục đích:** Được Flatsome render khi có cấu hình kích thước font chữ, chiều cao dòng hoặc khi nằm trong `[ux_stack]`.
* **Thuộc tính:**
  * `font_size`: Cỡ chữ đơn vị `rem` (`0.85rem` đến `4rem`). **Hỗ trợ:** `font_size`, `font_size__md`, `font_size__sm`.
  * `line_height`: Chiều cao dòng (`1.2` đến `2`). **Hỗ trợ:** `line_height`, `line_height__md`, `line_height__sm`.
  * `text_align`: Căn lề (`left`, `center`, `right`). **Hỗ trợ:** `text_align`, `text_align__md`, `text_align__sm`.
  * `text_color`: Màu chữ (`rgb(...)`).

---

### 3.2. `[button]` — Nút Bấm Kêu Gọi Hành Động (CTA Button)
* **File nguồn:** `inc/builder/shortcodes/button.php`
* **Thuộc tính:**
  * `text`: Nhãn nút.
  * `letter_case`: `uppercase` (chữ in hoa) | `default`.
  * `color`: Màu nút (`primary`, `secondary`, `alert`, `success`, `white`).
  * `style`: Kiểu nút (`outline`, `link`, `underline`, `shade`, `bevel`, `gloss`, `flat`).
  * `size`: Kích thước (`xxsmall`, `xsmall`, `small`, `medium`, `large`, `xlarge`).
  * `radius`: Độ bo góc (`0` = vuông, `5` = bo nhẹ, `99` = bo tròn con nhộng).
  * `depth`: Đổ bóng (`0` đến `5`).
  * `expand`: Tràn 100% chiều rộng cột (`true` | `false`).
  * `icon`: Icon hiển thị kèm (tên icon từ thư viện Flatsome).
  * `icon_pos`: Vị trí icon (`left`, `right`).
  * `link`: Đường dẫn.
  * `target`: `_blank` | `_self`.

---

### 3.3. `[title]` & `[divider]` — Tiêu Đề & Đường Phân Cách
* **File nguồn:** `inc/builder/shortcodes/title.php` & `divider.php`
* **Thuộc tính `[title]`:**
  * `text`: Nội dung tiêu đề.
  * `tag_name`: Thẻ HTML sinh ra (`h1`, `h2`, `h3`, `h4`).
  * `style`: Kiểu đường viền kèm theo (`normal`, `center`, `bold`, `bold-center`).
  * `width`: Độ dài đường gạch (px hoặc %).
  * `margin_top`: Khoảng cách trên (`0px` đến `100px`).
  * `margin_bottom`: Khoảng cách dưới (`0px` đến `100px`).
  * `link`: Link khi bấm vào tiêu đề.
  * `link_text`: Chữ hiển thị ở góc phải (ví dụ: "Xem tất cả >").

* **Thuộc tính `[divider]`:**
  * `width`: Độ rộng (`30px`, `100px`, `100%`).
  * `height`: Độ dày đường kẻ (`1px`, `2px`, `3px`).
  * `align`: Căn lề (`left`, `center`, `right`).
  * `color`: Màu đường kẻ.

---

### 3.4. `[accordion]` & `[accordion_item]` — Hỏi Đáp FAQ Chuẩn SEO
* **File nguồn:** `inc/builder/shortcodes/accordion.php`
* **QUY TẮC BẮT BUỘC:** `[accordion]` CHỈ CHỨA `[accordion_item]`.
* **Thuộc tính `[accordion]`:**
  * `title`: Tiêu đề khối hỏi đáp.
  * `auto_open`: Tự động mở mục đầu tiên (`true` | `""`).
  * `faq_schema`: **TÍNH NĂNG VÀNG SEO GOOGLE:** Gán `faq_schema="true"` để Flatsome tự xuất mã Schema JSON-LD FAQPage lên Google!
* **Thuộc tính `[accordion_item]`:**
  * `title`: Câu hỏi (Question).
  * Bên trong thẻ chứa câu trả lời (Answer): Text, hình ảnh, bullet points.

---

### 3.5. `[tabgroup]` & `[tab]` — Hệ Thống Tab Chuyển Đổi
* **File nguồn:** `inc/builder/shortcodes/tabgroup.php`
* **QUY TẮC BẮT BUỘC:** `[tabgroup]` CHỈ CHỨA `[tab]`.
* **Thuộc tính `[tabgroup]`:**
  * `title`: Tiêu đề nhóm tab.
  * `type`: Hướng tab (`horizontal` = ngang | `vertical` = dọc).
  * `style`: Kiểu giao diện (`line`, `tabs`, `pills`, `outline`, `sections`).
  * `nav_style`: `uppercase` | `normal`.
  * `align`: Căn lề thanh tab (`left`, `center`, `right`).
  * `event`: Kích hoạt khi rê chuột (`""` = click | `hover` = hover).
* **Thuộc tính `[tab]`:**
  * `title`: Tên nhãn tab.

---

### 3.6. `[ux_price_table]` & `[bullet_item]` — Bảng Giá Dịch Vụ Native (Mới 3.20.5)
* **File nguồn:** `inc/builder/shortcodes/price_table.php`
* **QUY TẮC BẮT BUỘC:** `'allow' => array( 'text', 'bullet_item', 'button' )`.
* **Thuộc tính `[ux_price_table]`:**
  * `title`: Tên gói dịch vụ (ví dụ: "Gói Tiêu Chuẩn").
  * `price`: Giá tiền (ví dụ: "499.000đ / tháng").
  * `description`: Mô tả ngắn đối tượng sử dụng.
  * `featured`: Làm nổi bật bảng giá (`true` = viền đổi màu, nâng cao hơn các cột khác | `false`).
  * `color`: Màu chữ (`dark` | `light`).
  * `bg_color`: Màu nền gói.
* **Thẻ con `[bullet_item]`:**
  * `text`: Nội dung tính năng đi kèm (ví dụ: `[bullet_item text="Miễn phí tên miền quốc tế"]`).

---

### 3.7. `[ux_menu]`, `[ux_menu_title]`, `[ux_menu_link]` — Menu Cột Chân Trang (Mới 3.20.5)
* **File nguồn:** `inc/builder/shortcodes/ux_menu.php`
* **QUY TẮC BẮT BUỘC:** `'allow' => array( 'ux_menu_link', 'ux_menu_title' )`.
* **Cú pháp chuẩn dựng Footer / Mega Menu:**
```shortcode
[ux_menu divider="solid"]
  [ux_menu_title text="Về Chúng Tôi"]
  [ux_menu_link text="Giới thiệu công ty" link="/gioi-thieu"]
  [ux_menu_link text="Đội ngũ nhân sự" link="/doi-ngu"]
  [ux_menu_link text="Chính sách bảo hành" link="/chinh-sach"]
[/ux_menu]
```

---

### 3.8. `[scroll_to]` — Điều Hướng Cuộn Trang One-Page (Mới 3.20.5)
* **File nguồn:** `inc/builder/shortcodes/scroll_to.php`
* **Thuộc tính:**
  * `title`: Tiêu đề mục hiển thị trên thanh chấm tròn điều hướng bên cạnh trang.
  * `link`: ID neo liên kết (ví dụ: `link="bang-gia"` $\rightarrow$ người dùng bấm link `#bang-gia` sẽ cuộn mượt mà đến vị trí này).
  * `bullet`: Hiện chấm tròn bám mép màn hình (`true` | `false`).
  * `offset`: Khoảng cách bù đắp thanh header cố định (px).

---

### 3.9. `[team_member]` — Thẻ Giới Thiệu Nhân Sự (Mới 3.20.5)
* **File nguồn:** `inc/builder/shortcodes/team_member.php`
* **Thuộc tính:**
  * `name`: Họ tên nhân sự.
  * `title`: Chức vụ / Phòng ban.
  * `img`: ID ảnh đại diện.
  * `image_height`: Chiều cao ảnh (`100%`, `120%`).
  * `image_width`: Chiều rộng ảnh (`80`, `100`).
  * `image_radius`: Bo tròn ảnh (`100` = hình tròn avatar).
  * `style`: Kiểu thẻ (`normal`, `overlay`, `shade`).

---

### 3.10. `[follow]` & `[share]` — Mạng Xã Hội Đầy Đủ Nền Tảng Mới
* **File nguồn:** `inc/builder/shortcodes/follow.php` & `share.php`
* **Thuộc tính `[follow]` (Flatsome 3.20.5 đã hỗ trợ đầy đủ mạng mới):**
  * `style`: `outline`, `fill`, `small`.
  * `scale`: Tỉ lệ kích thước (`100`, `120`%).
  * `facebook`, `instagram`, `tiktok`, `threads`, `x`, `twitter`, `youtube`, `zalo` (link), `email`, `phone`.

---

## NHÓM 4: BÀI VIẾT, SẢN PHẨM & WOOCOMMERCE BUILDER

### 4.1. `[blog_posts]` — Danh Sách Bài Viết Blog / Tin Tức
* **File nguồn:** `inc/builder/shortcodes/blog_posts.php`
* **Thuộc tính Layout:**
  * `type`: Kiểu hiển thị (`slider`, `row`, `masonry`, `grid`).
  * `columns`: Số cột Desktop (`1` đến `8`). **Mặc định:** `3` hoặc `4`.
  * `columns__md`: Số cột Tablet. Thường là `2`.
  * `columns__sm`: Số cột Mobile. Thường là `1`.
  * `col_spacing`: Khoảng cách giữa các bài (`collapse`, `small`, `normal`, `large`).
  * `depth`: Đổ bóng khung bài viết (`0` đến `5`).
  * `depth_hover`: Đổ bóng khi hover (`0` đến `5`).
* **Thuộc tính Thẻ Bài Viết (Card):**
  * `style`: Kiểu thẻ (`default`, `shade`, `overlay`, `vertical`, `bounce`...).
    * *Đặc biệt:* `style="vertical"` là bố cục ảnh bên trái, chữ bên phải.
  * `image_height`: Chiều cao/tỉ lệ thumbnail (`56.25%`, `75%`, `100%`, `89%`).
  * `image_width`: Chiều rộng ảnh khi dùng `style="vertical"` (`30` đến `50`%).
  * `image_size`: Cỡ ảnh WordPress (`thumbnail`, `medium`, `large`).
  * `image_hover`: Hiệu ứng hover (`zoom`, `fade`...).
* **Thuộc tính Chữ & Meta:**
  * `title_size`: Cỡ chữ tiêu đề (`small`, `normal`, `large`).
  * `show_date`: Hiện ngày đăng (`true`, `false`, `badge`).
  * `show_category`: Hiện danh mục (`true`, `false`, `label`).
  * `excerpt`: Hiện tóm tắt (`true` | `false`).
  * `excerpt_length`: Số từ trích dẫn (`15`, `25`).
  * `readmore`: Chữ nút đọc tiếp (ví dụ: `readmore="Đọc Thêm"`).
* **Thuộc tính Truy Vấn (Query):**
  * `posts`: Tổng số bài lấy ra (`posts="4"`).
  * `cat`: ID chuyên mục cần lấy.
  * `offset`: Số bài bỏ qua (phục vụ chia 2 cột tin chính - tin phụ).
  * `orderby`: Sắp xếp (`date`, `title`, `rand`, `comment_count`).
  * `order`: Thứ tự (`DESC`, `ASC`).

---

### 4.2. `[ux_products]` — Danh Sách Sản Phẩm WooCommerce
* **File nguồn:** `inc/builder/shortcodes/ux_products.php`
* **Thuộc tính chính:**
  * `type`: `slider`, `row`, `masonry`, `grid`.
  * `columns`: Số cột Desktop (`4`).
  * `columns__md`: Số cột Tablet (`3` hoặc `2`).
  * `columns__sm`: Số cột Mobile (`2` hoặc `1`).
  * `col_spacing`: Khoảng cách cột (`small`, `normal`).
  * `products`: Số lượng sản phẩm lấy ra (`products="8"`).
  * `cat`: Slug danh mục WooCommerce.
  * `show`: Bộ lọc (`featured` = sản phẩm nổi bật, `onsale` = sản phẩm giảm giá, `""` = tất cả).
  * `orderby`: `sales` (bán chạy), `date` (mới nhất), `price` (giá), `rand` (ngẫu nhiên).
  * `order`: `desc`, `asc`.
  * `out_of_stock`: `exclude` (ẩn sản phẩm hết hàng).
  * `show_rating`, `show_price`, `show_add_to_cart`, `show_quick_view`: `true` | `false`.

---

### 4.3. Bộ 13 Elements Dựng Trang Chi Tiết Sản Phẩm (Custom Single Product Page)
* **File nguồn:** `inc/builder/shortcodes/custom-product.php`
* Dành riêng cho ai muốn tự thiết kế layout trang chi tiết sản phẩm WooCommerce thay vì dùng giao diện mặc định:
  1. `[ux_product_gallery style="normal|vertical|stacked"]`: Thư viện ảnh sản phẩm kèm thumbnail chuyển slide.
  2. `[ux_product_title size="large|xlarge" uppercase="true|false"]`: Tiêu đề sản phẩm.
  3. `[ux_product_rating count="true|false" style="inline|stacked"]`: Đánh giá sao.
  4. `[ux_product_price size="large|xlarge"]`: Giá bán (kèm giá gạch khuyến mãi).
  5. `[ux_product_excerpt]`: Mô tả ngắn sản phẩm.
  6. `[ux_product_add_to_cart style="normal|flat|minimal" size="medium|large"]`: Nút Thêm vào giỏ hàng + chọn số lượng/biến thể.
  7. `[ux_product_meta]`: SKU, Danh mục, Từ khóa.
  8. `[ux_product_tabs style="tabs|tabs_normal|pills|accordian" align="left|center"]`: Tab thông tin chi tiết, đánh giá và mô tả dài.
  9. `[ux_product_related style="slider|grid"]`: Sản phẩm liên quan cùng danh mục.
  10. `[ux_product_upsell style="sidebar|grid"]`: Sản phẩm bán chéo (Up-sells).
  11. `[ux_product_breadcrumbs size="small|normal"]`: Đường dẫn phân cấp danh mục sản phẩm.
  12. `[ux_product_next_prev_nav]`: Nút chuyển sản phẩm trước / sau.
  13. `[ux_product_hook hook="woocommerce_single_product_summary"]`: Chèn các hook WooCommerce từ plugin thứ ba.

---

### 4.4. `[ux_portfolio]` — Thư Viện Dự Án Đã Thực Hiện
* **File nguồn:** `inc/builder/shortcodes/ux_portfolio.php`
* **Thuộc tính:**
  * `type`: `slider`, `row`, `masonry`, `grid`.
  * `filter`: Bật bộ lọc danh mục Isotope (`true` | `false`).
  * `filter_nav`: Kiểu thanh lọc (`line-grow`, `tabs`, `pills`).
  * `filter_align`: Căn lề nút lọc (`center`, `left`, `right`).
  * `columns`: Số cột Desktop (`3`).
  * `columns__sm`: Số cột Mobile (`1`).
  * `lightbox`: Mở xem ảnh dự án phóng to (`true`).

---

## 🚫 BẢNG DANH MỤC CÁC THẺ ẢO GIÁC PHỔ BIẾN (TUYỆT ĐỐI KHÔNG TỒN TẠI TRONG FLATSOME)

| Thẻ Ảo Giác (Do AI Tự Chế) | Hậu Quả Khi Dán Vào Web | Thẻ Chuẩn Flatsome 3.20.5 Thay Thế |
| :--- | :--- | :--- |
| `<!-- ... -->` (Comment HTML) | ❌ Phá vỡ Grid, sinh thẻ `[text]` con trái phép | **Xóa sạch 100% comment trong code** |
| `[container]` | ❌ Vỡ giao diện, text hiện trần | `[section]` hoặc `[row]` |
| `[column]` / `[columns]` | ❌ Không nhận độ rộng, vỡ cột | `[col span="..."]` |
| `[hero]` / `[hero_banner]` | ❌ Không chạy hiệu ứng và ảnh nền | `[ux_banner]` |
| `[flex]` / `[flex_box]` | ❌ Lỗi cú pháp shortcode | `[ux_stack]` (Flexbox native của Flatsome) |
| `[grid]` | ❌ Lỗi cú pháp | `[row]` hoặc `[ux_banner_grid]` |
| `[post_list]` / `[latest_posts]` | ❌ Không hiển thị | `[blog_posts]` |
| `[product_slider]` | ❌ Không nhận WooCommerce | `[ux_products type="slider"]` |
| `[faq]` | ❌ Không tạo schema FAQ | `[accordion faq_schema="true"]` |
| `[pricing_table]` | ❌ Lỗi không nhận css | `[ux_price_table]` |
