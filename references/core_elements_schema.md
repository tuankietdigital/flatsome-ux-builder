# BẢNG TRA CỨU CÁC CORE ELEMENTS & THUỘC TÍNH CHUẨN FLATSOME (ZERO-HALLUCINATION MATRIX)

Tài liệu này là từ điển chuẩn xác 100% về toàn bộ các thẻ shortcode và danh sách thuộc tính (attributes) hợp lệ của Flatsome 3.x+. Được biên soạn và đối chiếu trực tiếp từ mã nguồn lõi `inc/builder/shortcodes/` của theme Flatsome, [UX Themes Docs](https://docs.uxthemes.com/) và [Flatsome Demos](https://demos.flatsome.com/).

---

## 📱 CƠ CHẾ ĐẶT TÊN THUỘC TÍNH RESPONSIVE CỦA FLATSOME (RESPONSIVE SUFFIXES)

Trong Flatsome UX Builder, mọi thuộc tính kiểm soát bố cục, kích thước, khoảng cách đều hỗ trợ hệ thống hậu tố 2 dấu gạch dưới (`__`) để tinh chỉnh chuyên biệt theo từng thiết bị:
- **Không có hậu tố:** Thiết lập gốc, áp dụng cho **Desktop** ($\ge 850\text{px}$) hoặc kế thừa xuống dưới.
- **Hậu tố `__md` (Medium):** Thiết lập dành riêng cho **Tablet** ($550\text{px} - 849\text{px}$).
- **Hậu tố `__sm` (Small):** Thiết lập dành riêng cho **Mobile** ($< 550\text{px}$).

| Thuộc tính cơ sở | Desktop | Tablet (`__md`) | Mobile (`__sm`) | Ví dụ áp dụng thực tế |
| :--- | :---: | :---: | :---: | :--- |
| Độ rộng cột | `span` | `span__md` | `span__sm` | `span="4" span__md="6" span__sm="12"` |
| Số cột danh sách | `columns` | `columns__md` | `columns__sm` | `columns="5" columns__md="3" columns__sm="2"` |
| Chiều cao Banner/Gap | `height` | `height__md` | `height__sm` | `height="480px" height__md="350px" height__sm="220px"` |
| Khoảng đệm trong | `padding` | `padding__md` | `padding__sm` | `padding="40px" padding__sm="15px"` |
| Khoảng lề ngoài | `margin` | `margin__md` | `margin__sm` | `margin="20px" margin__sm="0px"` |
| Độ rộng hộp chữ | `width` | `width__md` | `width__sm` | `width="50%" width__sm="90%"` |
| Tọa độ ngang/dọc | `position_x` / `position_y` | `position_x__md` | `position_x__sm` | `position_x="10" position_x__sm="50"` |
| Căn lề nội dung | `align` | `align__md` | `align__sm` | `align="left" align__sm="center"` |
| Kích cỡ nút bấm | `size` | `size__md` | `size__sm` | `size="medium" size__sm="small"` |

---

## 1. NHÓM BỐ CỤC & KHUNG LƯỚI (LAYOUT & GRID)

### 1.1. `[section]`
Thẻ bao bọc toàn màn hình (Full-width Container), thường dùng để thiết lập màu nền, ảnh nền, hiệu ứng parallax hoặc phân cách các khối nội dung.
- **Thẻ đóng:** Bắt buộc (`[/section]`).
- **Nội dung bên trong:** Thường chứa `[row]`, `[ux_banner]`, `[ux_slider]`, `[gap]`, `[title]`.
- **Bảng thuộc tính hợp lệ:**

| Thuộc tính | Kiểu dữ liệu | Giá trị hợp lệ / Mặc định | Chức năng |
| :--- | :--- | :--- | :--- |
| `label` | string | Chuỗi văn bản tùy ý | Tên hiển thị của section trong cây DOM UX Builder. |
| `bg` | string / ID | URL ảnh hoặc ID Media (vd: `"1234"`, `"https://..."`) | Ảnh nền của section. |
| `bg_size` | string | `"original"`, `"large"`, `"medium"` | Kích thước ảnh nền WordPress tải về. |
| `bg_color` | string | Mã màu Hex/RGB/RGBA (vd: `"#f7f7f7"`, `"rgba(0,0,0,0.8)"`) | Màu nền section. |
| `bg_overlay` | string | Mã màu RGBA (vd: `"rgba(0,0,0,0.4)"`) | Lớp phủ màu mờ đè lên ảnh nền. |
| `bg_pos` | string | `"left top"`, `"center center"`, `"right bottom"`, ... | Vị trí neo của ảnh nền (Background position). |
| `parallax` | number | `0` đến `10` (vd: `"3"`, `"5"`) | Hệ số hiệu ứng cuộn trang thị sai (Parallax). |
| `effect` | string | `""`, `"snow"`, `"sparkle"`, `"rain"`, `"confetti"` | Hiệu ứng hạt tuyết, lấp lánh rơi trên nền. |
| `dark` | boolean | `"true"`, `"false"` (mặc định: `"false"`) | Đổi toàn bộ màu chữ của khối sang sáng (trắng) khi nền tối. |
| `padding` | string | Đơn vị px (vd: `"30px"`, `"60px 0px 60px 0px"`) | Khoảng đệm bên trong section. |
| `padding__md` | string | Đơn vị px (vd: `"40px 0px"`) | Đệm bên trong trên Tablet. |
| `padding__sm` | string | Đơn vị px (vd: `"20px 0px"`) | Đệm bên trong trên Mobile. |
| `margin` | string | Đơn vị px (vd: `"0px"`, `"-50px 0px 0px 0px"`) | Khoảng lề bên ngoài. |
| `margin__sm` | string | Đơn vị px | Lề ngoài trên Mobile. |
| `height` | string | `"500px"`, `"100vh"`, `"auto"` | Chiều cao cố định hoặc tối thiểu của section. |
| `scroll_for_more`| boolean | `"true"`, `"false"` | Hiện nút mũi tên trượt xuống ở góc dưới section. |
| `mask` | string | `""`, `"arrow"`, `"waves"`, `"triangle"`, `"slant"` | Mặt nạ phân cách hình lượn sóng/tam giác đáy section. |
| `class` | string | Tên CSS class | Gắn thêm class CSS tùy biến. |
| `visibility` | string | `""`, `"hide-for-medium"`, `"hide-for-small"`, `"show-for-small"` | Ẩn/hiện theo kích thước màn hình. |

---

### 1.2. `[row]`
Hàng chứa lưới cột (Flexbox/Grid Row). Có chiều rộng giới hạn trong khung container (mặc định khoảng 1080px - 1200px tùy theme options) trừ khi đặt `width="full-width"`.
- **Thẻ đóng:** Bắt buộc (`[/row]`).
- **Nội dung bên trong:** Chỉ được chứa `[col]`. Không được chứa trực tiếp text hoặc element khác.
- **Bảng thuộc tính hợp lệ:**

| Thuộc tính | Kiểu dữ liệu | Giá trị hợp lệ / Mặc định | Chức năng |
| :--- | :--- | :--- | :--- |
| `style` | string | `"default"`, `"small"`, `"large"`, `"collapse"`, `"dashed"`, `"divided"`, `"boxed"`, `"outline"` | Kiểu cách hiển thị hàng và khoảng cách giữa các cột (gutters). |
| `width` | string | `"custom"`, `"full-width"` | Chiều rộng hàng. Trống nghĩa là giới hạn container chuẩn. |
| `custom_width` | string | Đơn vị px (vd: `"1200px"`, `"1400px"`) | Đặt độ rộng hàng tối đa khi `width="custom"`. |
| `col_bg` | string | Mã màu Hex/RGBA | Đặt màu nền chung cho tất cả cột bên trong. |
| `col_bg_radius` | string | Đơn vị px (vd: `"8px"`, `"12px"`) | Bo góc nền cho tất cả cột bên trong. |
| `depth` | number | `"1"` đến `"5"` | Độ đổ bóng của các cột trong hàng (Box Shadow Depth). |
| `depth_hover` | number | `"1"` đến `"5"` | Độ đổ bóng khi rê chuột (Hover Box Shadow). |
| `v_align` | string | `"top"`, `"middle"`, `"bottom"`, `"equal-height"` | Canh lề theo chiều dọc giữa các cột. |
| `h_align` | string | `"left"`, `"center"`, `"right"` | Canh lề theo chiều ngang. |
| `class` | string | Tên CSS class | Gắn class bổ sung. |
| `visibility` | string | `"hide-for-small"`, `"hide-for-medium"`, `"show-for-small"`, `"show-for-medium"` | Kiểm soát hiển thị responsive. |

---

### 1.3. `[col]`
Cột phân chia trong hệ thống lưới 12 cột của Flatsome.
- **Thẻ đóng:** Bắt buộc (`[/col]`).
- **Bảng thuộc tính hợp lệ:**

| Thuộc tính | Kiểu dữ liệu | Giá trị hợp lệ / Mặc định | Chức năng |
| :--- | :--- | :--- | :--- |
| `span` | number | `"1"` đến `"12"` (Bắt buộc) | Số cột chiếm dụng trên Desktop (> 850px). |
| `span__md` | number | `"1"` đến `"12"` | Số cột chiếm dụng trên Tablet (550px - 849px). |
| `span__sm` | number | `"1"` đến `"12"` (Bắt buộc phải có) | Số cột chiếm dụng trên Mobile (< 550px). Thường là `"12"` hoặc `"6"`. |
| `align` | string | `"left"`, `"center"`, `"right"` | Canh lề nội dung bên trong cột Desktop. |
| `align__md` | string | `"left"`, `"center"`, `"right"` | Canh lề nội dung trên Tablet. |
| `align__sm` | string | `"left"`, `"center"`, `"right"` | Canh lề nội dung trên Mobile. |
| `animate` | string | `"fadeIn"`, `"fadeInUp"`, `"fadeInDown"`, `"fadeInLeft"`, `"fadeInRight"`, `"bounceIn"`, `"zoomIn"`, `"flipInX"`, `"flipInY"` | Hiệu ứng xuất hiện khi cuộn tới. |
| `animate_delay`| string | Số giây (vd: `"0.2"`, `"0.4"`) | Thời gian trễ animation. |
| `padding` | string | Đơn vị px (vd: `"20px 20px 20px 20px"`) | Đệm bên trong cột Desktop. |
| `padding__md` | string | Đơn vị px | Đệm bên trong trên Tablet. |
| `padding__sm` | string | Đơn vị px (vd: `"15px 10px"`) | Đệm bên trong trên Mobile. |
| `margin` | string | Đơn vị px (vd: `"0px 0px 20px 0px"`) | Lề bên ngoài cột. |
| `margin__sm` | string | Đơn vị px | Lề ngoài cột trên Mobile. |
| `bg_color` | string | Mã màu Hex/RGBA | Màu nền riêng của cột. |
| `bg_radius` | string | Đơn vị px (vd: `"6px"`, `"10px"`) | Bo góc cho riêng cột này. |
| `depth` | number | `"1"` đến `"5"` | Độ đổ bóng riêng của cột. |
| `depth_hover` | number | `"1"` đến `"5"` | Độ đổ bóng khi hover của cột. |
| `parallax` | number | `-10` đến `10` | Hiệu ứng parallax cuộn lệch pha. |
| `sticky` | boolean | `"true"`, `"false"` | Cố định cột khi người dùng cuộn trang (Sticky Column). |
| `tooltip` | string | Chuỗi văn bản | Hiện tooltip giải thích khi hover vào cột. |
| `class` | string | Tên CSS class | Class bổ sung. |
| `visibility` | string | `"hide-for-small"`, `"hide-for-medium"`, `"show-for-small"` | Kiểm soát hiển thị. |

---

### 1.4. `[row_inner]` & `[col_inner]`
Dùng để chia cột lồng bên trong một `[col]` mà không làm hỏng khoảng cách gutters và cấu trúc DOM của Flatsome.
- Cú pháp và thuộc tính tương đương `[row]` và `[col]`.

---

### 1.5. `[gap]`
Tạo khoảng trống phân cách linh hoạt giữa các khối, tự co giãn theo từng thiết bị.
- **Bảng thuộc tính hợp lệ:**
  - `height`: Chiều cao khoảng trống trên Desktop (vd: `"30px"`, `"50px"`).
  - `height__md`: Chiều cao trên Tablet (vd: `"25px"`).
  - `height__sm`: Chiều cao trên Mobile (vd: `"15px"`).
  - `class`, `visibility`.

---

## 2. NHÓM BANNER, SLIDER & GRID TRÌNH DIỄN

### 2.1. `[ux_banner]`
Khối banner đồ họa đỉnh cao của Flatsome hỗ trợ background hình ảnh, video lặp, mặt nạ, và tích hợp `[text_box]`.
- **Thẻ đóng:** Bắt buộc (`[/ux_banner]`).
- **Nội dung bên trong:** Bắt buộc phải chứa `[text_box]` để chứa văn bản/nút CTA.
- **Bảng thuộc tính hợp lệ:**

| Thuộc tính | Kiểu dữ liệu | Giá trị hợp lệ / Mặc định | Chức năng |
| :--- | :--- | :--- | :--- |
| `bg` | string / ID | URL hoặc ID Media | Ảnh nền banner. |
| `bg_size` | string | `"original"`, `"large"`, `"medium"` | Kích thước phân giải ảnh nền. |
| `bg_color` | string | Mã màu Hex/RGBA | Màu nền khi ảnh chưa tải xong hoặc không dùng ảnh. |
| `bg_overlay` | string | Mã màu RGBA (vd: `"rgba(0,0,0,0.5)"`) | Lớp phủ màu mờ trên ảnh nền để nổi bật chữ. |
| `bg_pos` | string | `"50% 50%"`, `"center center"`, `"top left"` | Tọa độ canh vị trí ảnh nền. |
| `height` | string | Đơn vị px hoặc % (vd: `"500px"`, `"600px"`, `"100%"`) | Chiều cao banner trên Desktop. |
| `height__md` | string | Đơn vị px (vd: `"450px"`) | Chiều cao trên Tablet. |
| `height__sm` | string | Đơn vị px (vd: `"320px"`) | Chiều cao trên Mobile. |
| `link` | string | URL (vd: `"https://domain.com/shop"`) | Link khi click vào toàn bộ banner. |
| `target` | string | `"_blank"`, `"_self"` | Mở link tab mới hay cùng tab. |
| `hover` | string | `"zoom"`, `"zoom-long"`, `"fade"`, `"glow"` | Hiệu ứng phóng to/mờ dần khi hover vào banner. |
| `effect` | string | `"snow"`, `"sparkle"`, `"rain"`, `""` | Hiệu ứng hạt rơi trên banner. |
| `parallax` | number | `"0"` đến `"10"` | Độ cuộn parallax của ảnh nền banner. |
| `video_mp4` | string | URL file video MP4 | Video nền chạy tự động không tiếng. |
| `video_sound` | boolean | `"true"`, `"false"` (mặc định `"false"`) | Bật âm thanh video. |
| `video_loop` | boolean | `"true"`, `"false"` (mặc định `"true"`) | Cho phép video lặp vô tận. |

---

### 2.2. `[text_box]`
Hộp văn bản định vị tọa độ tuyệt đối đặt bên trong `[ux_banner]`.
- **Thẻ đóng:** Bắt buộc (`[/text_box]`).
- **Bảng thuộc tính hợp lệ:**
  - `position_x`: Tọa độ ngang trên Desktop (`0` đến `100`, vd: `"10"` = sát trái, `"50"` = chính giữa, `"90"` = sát phải).
  - `position_x__md`: Tọa độ ngang trên Tablet.
  - `position_x__sm`: Tọa độ ngang trên Mobile (khuyên dùng `"50"` để căn giữa trên điện thoại).
  - `position_y`: Tọa độ dọc trên Desktop (`0` đến `100`, vd: `"50"` = giữa theo chiều dọc).
  - `position_y__md`: Tọa độ dọc trên Tablet.
  - `position_y__sm`: Tọa độ dọc trên Mobile.
  - `text_align`: Canh lề chữ bên trong (`"left"`, `"center"`, `"right"`).
  - `text_color`: `"light"` (chữ trắng cho nền tối) hoặc `"dark"` (chữ đen cho nền sáng).
  - `width`: Độ rộng hộp chữ trên Desktop (`"40%"`, `"50%"`, `"60%"`).
  - `width__md`: Độ rộng trên Tablet (`"70%"`, `"80%"`).
  - `width__sm`: Độ rộng trên Mobile (khuyên dùng `"90%"` hoặc `"100%"` để chữ không bị bóp nghẹt).
  - `padding`: Đệm trong hộp chữ (vd: `"20px 20px 20px 20px"`).
  - `padding__sm`: Đệm trong trên Mobile (vd: `"15px 10px"`).
  - `bg`: Màu nền hộp chữ nếu muốn tạo khung card.
  - `animate`: Hiệu ứng xuất hiện (`"fadeInUp"`, `"fadeInLeft"`, ...).

---

### 2.3. `[ux_slider]`
Thanh trượt băng chuyền đa năng hỗ trợ cảm ứng vuốt chạm (Touch-friendly Carousel).
- **Thẻ đóng:** Bắt buộc (`[/ux_slider]`).
- **Nội dung:** Chứa danh sách các `[ux_banner]`, `[ux_image]`, hoặc `[row]`.
- **Bảng thuộc tính hợp lệ:**

| Thuộc tính | Kiểu dữ liệu | Giá trị hợp lệ / Mặc định | Chức năng |
| :--- | :--- | :--- | :--- |
| `style` | string | `"default"`, `"shadow"`, `"normal"` | Kiểu hiển thị slider. |
| `slide_width` | string | `"100%"`, `"300px"`, ... | Độ rộng của từng slide (mặc định là full width 100%). |
| `slide_align` | string | `"center"`, `"left"`, `"right"` | Canh slide hiện hành. |
| `arrows` | string / boolean | `"true"`, `"false"`, `"simple"`, `"circle"` | Nút mũi tên chuyển slide. |
| `bullets` | boolean | `"true"`, `"false"` | Dấu chấm chuyển slide bên dưới. |
| `bullet_style` | string | `"circle"`, `"dashes"` | Kiểu dấu chấm tròn hoặc nét gạch. |
| `auto_slide` | boolean | `"true"`, `"false"` | Tự động trượt slide. |
| `timer` | number | Số mili-giây (vd: `"5000"`, `"7000"`) | Thời gian dừng mỗi slide (5s, 7s). |
| `pause_hover` | boolean | `"true"`, `"false"` | Tạm dừng chạy tự động khi rê chuột. |
| `nav_pos` | string | `"inside"`, `"outside"` | Vị trí nút điều hướng nằm trong hay ngoài khung. |
| `nav_size` | string | `"normal"`, `"large"` | Kích thước mũi tên. |
| `nav_color` | string | `"light"`, `"dark"` | Màu mũi tên (trắng hay đen). |

---

### 2.4. `[ux_banner_grid]`
Lưới ảnh banner ghép sẵn theo các layout chuẩn (Grid layout).
- **Bảng thuộc tính hợp lệ:**
  - `grid`: Số preset từ `"1"` đến `"14"` (các kiểu chia ô to nhỏ ghép nghệ thuật).
  - `height`: Tổng chiều cao khối lưới (vd: `"600px"`).
  - `spacing`: Khoảng cách giữa các ô (`"collapse"`, `"xsmall"`, `"small"`, `"normal"`, `"large"`).

---

## 3. NHÓM NỘI DUNG & THÀNH PHẦN GIAO DIỆN (UI & CONTENT)

### 3.1. `[button]`
Nút bấm hành động (CTA Button) tối ưu chuyển đổi với nhiều kiểu dáng đẹp mắt.
- **Thẻ tự đóng hoặc thẻ mở:** Cả hai dạng `[button text="..."]` hoặc `[button]text[/button]`.
- **Bảng thuộc tính hợp lệ:**

| Thuộc tính | Kiểu dữ liệu | Giá trị hợp lệ / Mặc định | Chức năng |
| :--- | :--- | :--- | :--- |
| `text` | string | Chuỗi văn bản nút bấm | Nội dung hiển thị trên nút. |
| `letter_case` | string | `"default"`, `"lowercase"`, `"uppercase"` | Kiểu chữ in hoa hay thường. |
| `color` | string | `"primary"`, `"secondary"`, `"success"`, `"alert"`, `"white"` | Màu sắc theo theme options Flatsome. |
| `style` | string | `"default"`, `"outline"`, `"link"`, `"shade"`, `"underline"`, `"bevel"`, `"gloss"` | Kiểu viền hoặc phẳng, bóng mờ. |
| `size` | string | `"xx-small"`, `"x-small"`, `"small"`, `"medium"`, `"large"`, `"xlarge"` | Kích cỡ nút trên Desktop. |
| `size__md` | string | `"small"`, `"medium"`, `"large"` | Kích cỡ nút trên Tablet. |
| `size__sm` | string | `"small"`, `"medium"`, `"large"` | Kích cỡ nút trên Mobile (khuyên dùng `"medium"` để dễ chạm). |
| `radius` | string | Đơn vị px (vd: `"0px"`, `"5px"`, `"99px"` cho nút viên thuốc) | Bo góc nút bấm. |
| `depth` | number | `"1"` đến `"5"` | Độ nổi đổ bóng. |
| `depth_hover` | number | `"1"` đến `"5"` | Độ nổi đổ bóng khi hover. |
| `expand` | boolean | `"0"`, `"1"` | Bật `"1"` để nút giãn dài 100% chiều rộng cột (Rất khuyên dùng trên Mobile). |
| `icon` | string | Tên icon (vd: `"icon-shopping-basket"`, `"icon-angle-right"`) | Icon kèm theo nút. |
| `icon_pos` | string | `"left"`, `"right"` | Vị trí icon bên trái hoặc phải chữ. |
| `icon_reveal` | boolean | `"true"`, `"false"` | Chỉ xuất hiện icon khi rê chuột vào nút. |
| `link` | string | URL hoặc anchor (vd: `"https://..."`, `"#contact"`) | Đường dẫn đích. |
| `target` | string | `"_blank"`, `"_self"` | Mở tab mới. |
| `visibility` | string | `"hide-for-small"`, `"show-for-small"`, ... | Kiểm soát ẩn/hiện nút theo thiết bị. |

---

### 3.2. `[title]` & `[divider]`
Tiêu đề phân đoạn và vạch ngăn cách.
- **`[title]`:**
  - `text`: Tiêu đề (vd: `"SẢN PHẨM MỚI NHẤT"`).
  - `style`: `"normal"`, `"center"`, `"bold"`, `"bold-center"`, `"dash"`, `"dash-center"`, `"star"`, `"star-center"`.
  - `size`: `"small"`, `"normal"`, `"medium"`, `"large"`, `"xlarge"`, `"xxlarge"`.
  - `link`, `link_text`, `icon`.
- **`[divider]`:**
  - `width`: `"small"`, `"medium"`, `"full"`, `"100%"`.
  - `height`: `"1px"`, `"2px"`, `"3px"`.
  - `align`: `"left"`, `"center"`, `"right"`.
  - `color`: Mã màu.

---

### 3.3. `[featured_box]` (Icon Box)
Khối giới thiệu tính năng/lợi ích kết hợp giữa icon hoặc ảnh nhỏ với tiêu đề và mô tả.
- **Thẻ đóng:** Bắt buộc (`[/featured_box]`).
- **Nội dung:** Văn bản đoạn mô tả tính năng.
- **Bảng thuộc tính hợp lệ:**
  - `icon`: Tên icon Flatsome (vd: `"icon-phone"`, `"icon-heart"`, `"icon-checkmark"`).
  - `img`: URL hoặc Media ID nếu dùng ảnh thay vì icon font.
  - `icon_border`: Độ dày viền icon (vd: `"1"`, `"2"`).
  - `icon_color`: Mã màu icon.
  - `pos`: Vị trí icon đối với văn bản (`"top"`, `"left"`, `"center"`).
  - `title`: Tiêu đề chính.
  - `title_small`: Tiêu đề phụ nhỏ hơn phía trên.
  - `link`: URL gắn vào box.
  - `tooltip`: Chú thích popup.

---

### 3.4. `[accordion]` & `[accordion_item]`
Khối danh sách câu hỏi thường gặp (FAQ) dạng mở rộng/thu gọn tiết kiệm không gian.
- **Cấu trúc:**
  ```html
  [accordion]
    [accordion_item title="Tiêu đề câu hỏi 1"]Nội dung câu trả lời 1[/accordion_item]
    [accordion_item title="Tiêu đề câu hỏi 2"]Nội dung câu trả lời 2[/accordion_item]
  [/accordion]
  ```
- **Thuộc tính `[accordion]`:**
  - `auto_open`: `"true"`, `"false"` (tự mở mục đầu tiên).
- **Thuộc tính `[accordion_item]`:**
  - `title`: Tiêu đề mục (Bắt buộc).

---

### 3.5. `[tabgroup]` & `[tab]`
Khối chuyển tab nội dung tương tác mượt mà.
- **Cấu trúc:**
  ```html
  [tabgroup style="tabs" align="left"]
    [tab title="Tab 1"]Nội dung Tab 1[/tab]
    [tab title="Tab 2"]Nội dung Tab 2[/tab]
  [/tabgroup]
  ```
- **Thuộc tính `[tabgroup]`:**
  - `style`: `"default"`, `"pills"`, `"tabs"`, `"outline"`, `"line"`, `"divided"`.
  - `align`: `"left"`, `"center"`, `"right"`.

---

### 3.6. `[testimonials]` & `[testimonial]`
Khối đánh giá của khách hàng (Social Proof / E-E-A-T).
- **Cấu trúc:**
  ```html
  [testimonials style="normal"]
    [testimonial name="Nguyễn Văn A" company="CEO Công Ty ABC" stars="5" image="URL_ANH"]
      Đánh giá cực kỳ hài lòng về sản phẩm và dịch vụ!
    [/testimonial]
  [/testimonials]
  ```
- **Thuộc tính `[testimonials]`:** `style` (`"normal"`, `"simple"`, `"focus"`), `type` (`"slider"`, `"row"`).
- **Thuộc tính `[testimonial]`:** `name`, `company`, `stars` (`"1"` đến `"5"`), `image`.

---

### 3.7. `[ux_countdown]`
Đồng hồ đếm ngược giờ vàng khuyến mãi kích thích chuyển đổi (FOMO).
- **Thuộc tính:**
  - `year`: Năm đích (vd: `"2026"`).
  - `month`: Tháng (vd: `"12"`).
  - `day`: Ngày (vd: `"31"`).
  - `time`: Giờ:phút (vd: `"23:59"`).
  - `style`: `"clock"`, `"inline"`, `"text"`.
  - `t_hour`, `t_min`, `t_sec`: Bản địa hóa chữ tiếng Việt (vd: `t_hour="Giờ" t_min="Phút" t_sec="Giây"`).

---

### 3.8. `[lightbox]`
Hộp thoại Popup mở rộng khi người dùng nhấn vào nút/link hoặc tự động mở.
- **Cấu trúc:**
  ```html
  [button text="Nhận Báo Giá Ngay" link="#form-popup"]
  [lightbox id="form-popup" width="600px" padding="30px"]
    <h3>Đăng Ký Tư Vấn Miễn Phí</h3>
    [contact-form-7 id="123" title="Form Tư Vấn"]
  [/lightbox]
  ```
- **Thuộc tính:**
  - `id`: Tên định danh (Bắt buộc, khớp với `#id` ở link gọi).
  - `width`: Độ rộng popup (vd: `"600px"`).
  - `padding`: Đệm trong (vd: `"20px"`, `"30px"`).
  - `auto_open`: `"true"`, `"false"` (tự bật popup khi vào trang).
  - `auto_timer`: Thời gian trễ mili-giây (vd: `"3000"` = 3s).
  - `auto_show`: `"always"` (luôn hiện) hoặc `"once"` (chỉ hiện 1 lần cho mỗi khách truy cập nhờ cookie).

---

### 3.9. `[blog_posts]`
Hiển thị danh sách bài viết tin tức, bài viết chuyên mục chuẩn WordPress blog theo dạng lưới, slider hoặc hàng ngang.
- **Bảng thuộc tính hợp lệ:**

| Thuộc tính | Kiểu dữ liệu | Giá trị hợp lệ / Mặc định | Chức năng |
| :--- | :--- | :--- | :--- |
| `type` | string | `"row"`, `"slider"`, `"grid"`, `"masonry"` | Kiểu bố cục danh sách bài viết. |
| `columns` | number | `"1"`, `"2"`, `"3"`, `"4"` | Số cột hiển thị trên Desktop. |
| `columns__md` | number | `"1"`, `"2"`, `"3"` | Số cột trên Tablet (khuyên dùng `"2"` hoặc `"1"`). |
| `columns__sm` | number | `"1"`, `"2"` (khuyên dùng `"1"`) | Số cột trên Mobile. |
| `posts` | number | Số lượng bài viết (vd: `"6"`, `"8"`) | Tổng số bài viết hiển thị. |
| `offset` | number | Số bài bỏ qua (vd: `"1"`) | Hữu ích khi bài đầu tiên làm bài nổi bật lớn bên cạnh. |
| `category` | string | Slug hoặc ID danh mục bài viết | Lọc bài viết theo danh mục. |
| `style` | string | `"default"`, `"vertical"`, `"shade"`, `"overlay"` | `"vertical"`: ảnh bên trái chữ bên phải; `"default"`: ảnh trên chữ dưới. |
| `image_height` | string | Đơn vị % hoặc px (vd: `"75%"`, `"89%"`, `"200px"`) | Tỷ lệ chiều cao khung ảnh (tạo padding-top trên `.image-cover`). |
| `image_width` | number | Tỷ lệ % (vd: `"38"`, `"40"`) | Độ rộng % của ảnh khi dùng `style="vertical"`. |
| `image_hover` | string | `"zoom"`, `"fade-in"`, `"glow"` | Hiệu ứng khi rê chuột vào ảnh bài viết. |
| `text_align` | string | `"left"`, `"center"`, `"right"` | Canh lề khối chữ. |
| `text_bg` | string | Mã màu Hex/RGBA hoặc biến CSS | Màu nền hộp chữ (vd: `var(--primary-color)`). |
| `text_color` | string | `"light"`, `"dark"` | Đảo màu chữ (dark = nền tối chữ sáng). |
| `text_padding` | string | Đơn vị px (vd: `"16px 16px 16px 16px"`) | Đệm bên trong hộp chữ. |
| `show_date` | string | `"false"`, `"true"`, `"text"`, `"badge"` | Hiển thị ngày đăng dạng chữ hay huy hiệu. |
| `show_category`| string / boolean | `"false"`, `"true"` | Ẩn/hiện tên danh mục bài viết. |
| `excerpt` | string / boolean | `"false"`, `"true"` | Ẩn/hiện đoạn mô tả ngắn trích dẫn. |
| `comments` | string / boolean | `"false"`, `"true"` | Ẩn/hiện số lượt bình luận. |
| `class` | string | Tên CSS class | Class tùy biến. |

---

## 4. NHÓM WOOCOMMERCE & CỬA HÀNG (ECOMMERCE ELEMENTS)

### 4.1. `[ux_products]`
Hiển thị danh sách sản phẩm WooCommerce theo dạng lưới hoặc trượt carousel.
- **Bảng thuộc tính hợp lệ:**

| Thuộc tính | Kiểu dữ liệu | Giá trị hợp lệ / Mặc định | Chức năng |
| :--- | :--- | :--- | :--- |
| `type` | string | `"slider"`, `"grid"`, `"masonry"`, `"row"` | Kiểu dàn trang sản phẩm. |
| `columns` | number | `"2"`, `"3"`, `"4"`, `"5"`, `"6"`, `"8"` | Số cột hiển thị trên Desktop. |
| `columns__md` | number | `"2"`, `"3"`, `"4"` | Số cột trên Tablet. |
| `columns__sm` | number | `"1"`, `"2"` (khuyên dùng `"2"`) | Số cột trên Mobile. |
| `cat` | string / ID | Slug hoặc Category ID (vd: `"ao-thun"`) | Lọc sản phẩm theo danh mục cụ thể. |
| `products` | number | Số lượng (vd: `"8"`, `"12"`) | Tổng số sản phẩm hiển thị. |
| `orderby` | string | `"date"`, `"title"`, `"price"`, `"rand"`, `"sales"`, `"rating"` | Tiêu chí sắp xếp. |
| `order` | string | `"asc"`, `"desc"` | Thứ tự tăng dần / giảm dần. |
| `show_cat` | boolean | `"0"`, `"1"` | Bật/tắt hiển thị tên danh mục trên thẻ sản phẩm. |
| `show_title` | boolean | `"0"`, `"1"` | Bật/tắt tiêu đề sản phẩm. |
| `show_rating` | boolean | `"0"`, `"1"` | Bật/tắt số sao đánh giá. |
| `show_price` | boolean | `"0"`, `"1"` | Bật/tắt hiển thị giá tiền. |
| `show_add_to_cart` | boolean | `"0"`, `"1"` | Bật/tắt nút Thêm vào giỏ. |
| `show_quick_view` | boolean | `"0"`, `"1"` | Bật/tắt nút Xem nhanh (Quick view). |
| `equalize_box` | boolean | `"true"`, `"false"` | Tự động cân bằng chiều cao mọi card sản phẩm, giúp ảnh, tiêu đề dài ngắn và giá tiền luôn thẳng hàng đều đáy. |
| `slider_nav_style` | string | `"circle"`, `"simple"`, `"reveal"` | Kiểu nút mũi tên điều hướng slider tròn hoặc đơn giản. |
| `slider_nav_position` | string | `"normal"`, `"outside"` | Vị trí nút mũi tên slider nằm trong hay ngoài khung sản phẩm. |
| `image_hover` | string | `"fade-in"`, `"zoom"`, `"zoom-fade"`, `"glow"` | Hiệu ứng khi rê chuột vào ảnh sản phẩm. |
| `image_size` | string | `"woocommerce_thumbnail"`, `"medium"`, `"large"` | Kích thước ảnh sản phẩm. |
| `style` | string | `"default"`, `"shade"`, `"overlay"`, `"badge"`, `"vertical"` | Kiểu card sản phẩm. |

*Các biến thể tương đương:* `[ux_featured_products]`, `[ux_sale_products]`, `[ux_best_selling_products]`, `[ux_custom_products]`.

---

### 4.2. Shortcode Dành Riêng Cho Custom Product Page Layout (Trang Chi Tiết Sản Phẩm)
Được hỗ trợ đầy đủ từ bản cập nhật Flatsome 3.x+ (theo tài liệu UX Themes số 247). Các shortcode này cho phép tự do kéo thả, tái cấu trúc trang chi tiết sản phẩm WooCommerce:
- `[ux_product_gallery]` / `[ux_product_gallery style="full-width"]`: Album ảnh và ảnh đại diện sản phẩm.
- `[ux_product_breadcrumbs]`: Đường dẫn phân cấp (Trang chủ > Danh mục > Tên SP).
- `[ux_product_title]`: Tiêu đề tên sản phẩm (thẻ H1).
- `[ux_product_rating]`: Số sao đánh giá và tổng lượt review.
- `[ux_product_price]`: Giá bán thường và giá khuyến mãi.
- `[ux_product_excerpt]`: Đoạn mô tả ngắn sản phẩm.
- `[ux_product_add_to_cart]`: Khung chọn số lượng, biến thể (màu sắc/size) và nút Đặt Mua.
- `[ux_product_meta]`: Mã SKU, Danh mục cha, Thẻ từ khóa (Tags).
- `[ux_product_tabs]`: Khối Tabs Chi tiết sản phẩm, Đánh giá và Chính sách.
- `[ux_product_upsell style="grid"]`: Khối sản phẩm bán kèm / nâng cấp (Upsell).
- `[ux_product_related]`: Khối sản phẩm liên quan (Related Products).
- `[ux_sidebar id="product-sidebar"]`: Nhúng widget sidebar sản phẩm.

---

## 5. KHỐI TÁI SỬ DỤNG (UX BLOCKS)
### `[block id="..."]`
- Nhúng một UX Block được tạo tại `wp-admin -> UX Blocks`.
- Thuộc tính `id`: Nhận slug hoặc ID bài đăng của khối (vd: `[block id="mega-menu-dien-thoai"]` hoặc `[block id="1045"]`).
- **Ưu điểm vượt trội:** Giúp thay đổi nội dung ở một nơi duy nhất và tự động đồng bộ trên toàn trang web (Header, Footer, Mega Menu, Lightbox, Tab sản phẩm).
