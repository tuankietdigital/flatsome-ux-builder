# BỘ QUY TẮC LINTER & SOÁT LỖI CÚ PHÁP SHORTCODE FLATSOME (VALIDATOR RULES)

Khi kích hoạt lệnh `UX VALIDATE: [đoạn mã]` hoặc trước khi xuất bất kỳ đoạn mã shortcode nào cho người dùng, hệ thống bắt buộc phải kiểm duyệt qua **6 Quy Tắc Vàng** dưới đây để đảm bảo giao diện hiển thị hoàn hảo, không gây lỗi cú pháp PHP và không làm đơ giao diện kéo thả UX Builder.

---

## 1. 6 QUY TẮC LINTER NGUYÊN BẢN (THE 6 VALIDATION RULES)

### Quy Tắc 1: Tính Toàn Vẹn Của Thẻ Mở / Đóng (Tag Pairing Integrity)
- **Yêu cầu:** Mọi thẻ container hoặc thẻ bao bọc nội dung bắt buộc phải có thẻ đóng đối ứng chính xác:
  - `[section]` $\leftrightarrow$ `[/section]`
  - `[row]` $\leftrightarrow$ `[/row]`
  - `[col]` $\leftrightarrow$ `[/col]`
  - `[row_inner]` $\leftrightarrow$ `[/row_inner]`
  - `[col_inner]` $\leftrightarrow$ `[/col_inner]`
  - `[ux_banner]` $\leftrightarrow$ `[/ux_banner]`
  - `[text_box]` $\leftrightarrow$ `[/text_box]`
  - `[tabgroup]` $\leftrightarrow$ `[/tabgroup]`
  - `[tab]` $\leftrightarrow$ `[/tab]`
  - `[accordion]` $\leftrightarrow$ `[/accordion]`
  - `[accordion_item]` $\leftrightarrow$ `[/accordion_item]`
  - `[featured_box]` $\leftrightarrow$ `[/featured_box]`
  - `[lightbox]` $\leftrightarrow$ `[/lightbox]`
- **Cảnh báo lỗi:** Thẻ mở quên đóng sẽ khiến toàn bộ nội dung phía sau trang bị nuốt vào bên trong, làm mất chân trang (footer) và hỏng cấu trúc HTML.

---

### Quy Tắc 2: Thứ Bậc Lồng Thẻ Chuẩn Mực (Strict Nesting Hierarchy)
- **Yêu cầu:** 
  1. `[col]` **bắt buộc** phải là con trực tiếp của `[row]` hoặc `[row_inner]`. Tuyệt đối không để `[col]` đứng độc lập trong `[section]`.
  2. Khi muốn chia thêm cột bên trong một `[col]`, **bắt buộc** phải dùng cặp `[row_inner]` và `[col_inner]`. Cấm dùng trực tiếp `[row]` và `[col]`.
  3. `[text_box]` **bắt buộc** phải nằm trong `[ux_banner]`.
  4. `[tab]` **bắt buộc** phải nằm trong `[tabgroup]`.
  5. `[accordion_item]` **bắt buộc** phải nằm trong `[accordion]`.
- **Cảnh báo lỗi:** Lồng sai cấu trúc sẽ khiến UX Builder báo lỗi *"Element cannot be dropped here"* và làm vỡ gutter CSS.

---

### Quy Tắc 3: Kiểm Tra Toán Học Lưới 12 Cột (12-Column Grid Math)
- **Yêu cầu:** 
  - Tính tổng giá trị `span` của các cột cùng nằm trong một `[row]`.
  - Nếu tổng `\sum \text{span} \ne 12` và không phải là bội số của 12 (khi cố ý làm danh sách nhiều hàng), hệ thống phải cảnh báo người dùng về khoảng trống dư thừa ở cuối hàng.
  - Cấm giá trị `span > 12` trên bất kỳ thẻ `[col]` nào.

---

### Quy Tắc 4: Kiểm Soát Responsive 3 Thiết Bị Chuẩn Xác (Comprehensive 3-Device Responsive Linter)
- **Vấn đề cốt lõi:** Việc chỉ cấu hình cho Desktop ($> 849\text{px}$) sẽ khiến giao diện bị vỡ nát, tràn khung hoặc chữ dồn thành 1 cột hẹp trên Tablet và Mobile.
- **Yêu cầu kiểm duyệt bắt buộc:** 
  1. **Cột (`[col]`):** Với bất kỳ cột nào có `span="6"`, `span="4"`, `span="3"`, `span="2"` trên Desktop, hệ thống **bắt buộc** phải kiểm tra sự hiện diện của `span__sm`:
     - Tự động bổ sung `span__sm="12"` (hoặc `span__sm="6"` đối với danh sách sản phẩm / icon box nhỏ).
     - Với bố cục 3 hoặc 4 cột, tự động bổ sung `span__md="6"` để chia 2 cột đều trên Tablet.
  2. **Banner (`[ux_banner]`):** Kiểm tra bộ 3 chiều cao thu nhỏ dần hợp lý:
     - Phải có `height` (Desktop) $\rightarrow$ `height__md` (Tablet) $\rightarrow$ `height__sm` (Mobile). Cấm giữ nguyên banner `height="500px"` trên điện thoại.
  3. **Hộp chữ (`[text_box]`):** Khi đặt hộp chữ trên banner, nếu Desktop có `width="50%"` hoặc `"60%"`, trên Mobile phải tự động gán `width__sm="90%"` hoặc `"100%"` và `position_x__sm="50"` để tránh tràn khung.
  4. **Danh sách (`[ux_products]`, `[blog_posts]`):** Bắt buộc phải có `columns__md` (thường là `"3"` hoặc `"2"`) và `columns__sm` (thường là `"2"` cho sản phẩm, `"1"` cho tin tức).

---

### Quy Tắc 5: Danh Sách Trắng Thuộc Tính (Attribute Whitelist Sanitization)
- **Yêu cầu:** 
  - Đối chiếu toàn bộ tên thuộc tính với `core_elements_schema.md`.
  - Phát hiện và thay thế ngay các thuộc tính bịa đặt (hallucinated):
    - `columns="6"` trên `[col]` $\rightarrow$ Sửa thành: `span="6"`
    - `background="..."` hoặc `bg_image="..."` $\rightarrow$ Sửa thành: `bg="..."`
    - `background_color="..."` $\rightarrow$ Sửa thành: `bg_color="..."`
    - `border_radius="..."` $\rightarrow$ Sửa thành: `bg_radius="..."` trên `[col]` hoặc `radius="..."` trên `[button]`
    - `text="..."` trên `[featured_box]` $\rightarrow$ Chuyển thành văn bản nằm giữa thẻ mở và đóng.

---

### Quy Tắc 6: Chuẩn Hóa Dấu Ngoặc Kép & Ký Tự (Quote & Syntax Sanitization)
- **Yêu cầu:** 
  - Toàn bộ giá trị thuộc tính phải được bao bọc bởi dấu ngoặc kép thẳng chuẩn lập trình `""`.
  - Tự động thay thế các ký tự ngoặc cong kiểu Word (`“`, `”`, `‘`, `’`) thành `""`.
  - Đảm bảo không có dấu cách thừa trước dấu `=` (ví dụ: `span = "6"` $\rightarrow$ chuyển thành `span="6"`).

---

### Quy Tắc 7: Phòng Chống Lỗi Raw HTML & Entity Escaping (Anti-Raw-HTML Rule)
- **Vấn đề cốt lõi:** Khi nhồi nhét các đoạn mã HTML phức tạp có inline CSS (`style="background-color: ...;"`) vào bên trong `[text_box]` hoặc shortcode, WordPress thường tự động chuyển đổi ký tự `<` thành `&lt;` và `>` thành `&gt;` (đặc biệt khi người dùng dán vào Visual Editor hoặc qua bộ lọc `wpautop`/`wp_kses`). Hậu quả là toàn bộ mã thẻ HTML bị in thô nguyên văn ra màn hình.
- **Yêu cầu bắt buộc:**
  1. **Đối với Banner Khuyến Mãi / Đồ Họa Phức Tạp (như Banner Công Nghệ, Flash Sale):** Tuyệt đối KHÔNG gõ lại chữ và icon bằng inline HTML. Phải sử dụng phương pháp **Graphic Banner chuẩn** (`[ux_banner bg="URL_ANH"]` hoặc `[ux_image]`). Banner đồ họa được thiết kế hoàn thiện từ Photoshop/Canva/Figma sẽ giữ được độ sắc nét và bố cục hoàn hảo trên mọi thiết bị.
  2. **Nếu cần thêm nút bấm hoặc chữ động:** Chỉ dùng các shortcode thành phần nguyên bản của Flatsome như `[button]`, `[title]`, `[featured_box]`. Không bọc thẻ `<span style="...">` hay `<h1>` có inline CSS phức tạp bên trong shortcode.

---

### Quy Tắc 8: Loại Bỏ Hoàn Toàn Ghi Chú HTML `<!-- ... -->` (Zero HTML Comments Rule)
- **Vấn đề cốt lõi:** Khi có các đoạn ghi chú HTML như `<!-- CỘT TRÁI -->` nằm giữa các shortcode, bộ quét parser của Flatsome UX Builder sẽ hiểu nhầm đó là nội dung văn bản và tự động tạo ra một **Element Text** mới trong cây điều hướng (DOM Tree View). Điều này làm rối cấu trúc layout, sinh thẻ `<p>` hoặc `<div>` rác và gây giật khung/khoảng cách thừa.
- **Yêu cầu bắt buộc:**
  - Không bao giờ đặt `<!-- ... -->` bên trong khối mã shortcode.
  - Mã shortcode phải là **100% Pure Clean Shortcode**.
  - Mọi giải thích về bố cục, chia cột phải được trình bày ở phần văn bản giải thích phía trên hoặc phía dưới khối code.

---

### Quy Tắc 9: Tôn Trọng Màu Sắc Mặc Định Của Website (Zero Hardcoded Color Overrides Rule)
- **Vấn đề cốt lõi:** Việc tùy tiện gán mã màu Hex tĩnh (ví dụ: `#1e293b`, `#333333`, v.v.) vào CSS của tiêu đề thẻ hoặc link bài viết sẽ phá vỡ tính nhất quán của bảng màu thương hiệu (Brand Color Palette) mà chủ web đã dày công thiết lập trong Flatsome Theme Options (như màu xanh lá, cam, xanh dương...).
- **Yêu cầu bắt buộc:**
  - Tuyệt đối không hardcode thuộc tính `color: ... !important;` cho thẻ bài viết hay link nếu người dùng không yêu cầu.
  - Hãy để các element tự động kế thừa (inherit) màu sắc mặc định của website, hoặc sử dụng biến chuẩn `var(--primary-color)` khi muốn lấy màu nhấn thương hiệu.

---

### Quy Tắc 10: Giữ Khoảng Đệm Hợp Lý Giữa Ảnh Thumbnail Và Văn Bản (Thumbnail-to-Text Gap Rule)
- **Vấn đề cốt lõi:** Khi người dùng muốn căn chỉnh gọn gàng layout bài viết ngang (`style="vertical"`), việc đặt `padding: 0 !important;` cho `.box-text` sẽ vô tình triệt tiêu toàn bộ khoảng cách giữa mép phải hình ảnh thumbnail và chữ tiêu đề, khiến nội dung bị dính chặt vào hình ảnh rất mất thẩm mỹ.
- **Yêu cầu bắt buộc:**
  - Luôn đảm bảo khoảng đệm ngang tối thiểu: `padding: 0 0 0 15px !important;` hoặc `padding-left: 15px !important;` trên `.box-text` trong các layout dạng ngang.
  - Giữ khoảng thở thị giác sạch sẽ, ngay ngắn giữa thumbnail và nội dung.

---

### Quy Tắc 11: Bảo Toàn Cơ Chế Aspect-Ratio Của Flatsome (Native Aspect-Ratio Protection)
- **Vấn đề cốt lõi:** Flatsome sử dụng cơ chế Padding Aspect-Ratio (`style="padding-top: XX%;"`) trên thẻ `.image-cover` để tính toán chiều cao và giữ khung hiển thị cho ảnh. Việc dùng CSS gán `padding-top: 0 !important;` hoặc ép `position: absolute` sẽ phá vỡ hệ thống tính toán này, làm chiều cao sụp đổ về 0px và khiến **ảnh biến mất hoàn toàn**.
- **Yêu cầu bắt buộc:**
  - Cấm tuyệt đối can thiệp `padding-top: 0 !important;` lên `.image-cover`.
  - Mọi yêu cầu cân bằng chiều cao phải thực hiện bằng cách điều chỉnh tham số `image_height="..."` trong shortcode hoặc ghi đè tỷ lệ `padding-top: XX% !important;` theo tính toán chính xác trên Desktop (`@media (min-width: 850px)`).

---

### Quy Tắc 12: Thiết Kế Tab Tiêu Đề Ôm Khít Chữ (Heading Tab Fit-Content Rule)
- **Vấn đề cốt lõi:** Thẻ `h2` là phần tử khối (Block Element) mặc định chiếm 100% chiều rộng hàng. Khi làm tiêu đề danh mục dạng Tab gắn viền dưới, nếu không khống chế độ rộng thì tab sẽ bị phình to toàn màn hình hoặc kéo dài bất thường.
- **Yêu cầu bắt buộc:**
  - Luôn sử dụng CSS: `display: inline-block !important; width: auto !important; max-width: fit-content !important; margin-bottom: -2px !important; border-radius: 6px 6px 0 0 !important;`
  - Đặt đè lên khung bao `.product-cat-title-bar` có đường viền đáy `border-bottom: 2px solid var(--primary-color)`.

---

### Đoạn Mã Người Dùng Gửi Vào Bị Lỗi Nặng:
```html
[section background="#f4f4f4"]
  [col columns="6"]
    <h3>Tiêu đề lỗi</h3>
    [row]
      [col columns="6"]Cột con 1[/col]
      [col columns="6"]Cột con 2[/col]
    [/row]
  [col columns="6"]
    [button title="Mua ngay" link="https://shop.com"]
  [/col]
[/section]
```

### Báo Cáo Chẩn Đoán Lỗi (Linter Diagnostic Report):
1. **Lỗi Quy Tắc 5 (Attribute Whitelist):** `background` trong `[section]` không tồn tại $\rightarrow$ Sửa thành `bg_color="#f4f4f4"`.
2. **Lỗi Quy Tắc 2 (Hierarchy):** `[col]` nằm trực tiếp trong `[section]` mà thiếu thẻ `[row]` cha $\rightarrow$ Bổ sung thẻ `[row]`.
3. **Lỗi Quy Tắc 5 (Attribute Whitelist):** `columns="6"` không tồn tại trên `[col]` $\rightarrow$ Sửa thành `span="6"`.
4. **Lỗi Quy Tắc 4 (Mobile Responsive):** Thiếu tham số mobile $\rightarrow$ Bổ sung `span__sm="12"`.
5. **Lỗi Quy Tắc 2 (Hierarchy & Nesting):** Lồng trực tiếp `[row]` trong `[col]` $\rightarrow$ Sửa thành `[row_inner]` và `[col_inner]`.
6. **Lỗi Quy Tắc 1 (Tag Pairing):** Cột đầu tiên bị thiếu thẻ đóng `[/col]`.
7. **Lỗi Quy Tắc 5 (Attribute Whitelist):** `title="..."` không tồn tại trên `[button]` $\rightarrow$ Sửa thành `text="Mua ngay"`.

### Đoạn Mã Đã Được Linter Tự Động Sửa Chuẩn 100%:
```html
[section bg_color="#f4f4f4"]
  [row]
    [col span="6" span__sm="12"]
      <h3>Tiêu đề chuẩn</h3>
      [row_inner]
        [col_inner span="6" span__sm="12"]Cột con 1[/col_inner]
        [col_inner span="6" span__sm="12"]Cột con 2[/col_inner]
      [/row_inner]
    [/col]
    [col span="6" span__sm="12"]
      [button text="Mua ngay" link="https://shop.com"]
    [/col]
  [/row]
[/section]
```
