# Bộ 15 Quy Tắc Soát Lỗi Cú Pháp & Bố Cục UX Builder (Flatsome Linter Rules)

> **Tác giả:** Quách Trần Tuấn Kiệt  
> **Nguyên tắc cốt lõi:** Bất kỳ đoạn mã shortcode nào trước khi xuất cho người dùng **BẮT BUỘC** phải vượt qua 100% các điều kiện kiểm tra (Linter Rules) bên dưới. Nếu vi phạm dù chỉ 1 quy tắc, hệ thống phải tự động hủy bỏ bản nháp và định dạng lại mã nguồn.

---

## 📋 BẢNG TỔNG HỢP 15 QUY TẮC LINTER (LINTER CHECKSUM MATRIX)

| Mã Quy Tắc | Tên Quy Tắc Kiểm Tra | Mức Độ | Hậu Quả Nếu Vi Phạm |
| :--- | :--- | :--- | :--- |
| **RULE-01** | Zero-Comment HTML Check | 🚨 Nghiêm ngặt | Phá vỡ Grid, sinh thẻ `[text]` con trái phép |
| **RULE-02** | Row-Col Structural Purity | 🚨 Nghiêm ngặt | Vỡ layout, thẻ trần không hiển thị |
| **RULE-03** | Banner Child Whitelist Check | 🚨 Nghiêm ngặt | Banner bị biến dạng, không nhận text/nút |
| **RULE-04** | Self-Nesting Depth Suffix Check | 🚨 Nghiêm ngặt | Đóng mở thẻ lộn xộn, hỏng toàn trang |
| **RULE-05** | Image Aspect-Ratio Protection | 🚨 Nghiêm ngặt | Container sập về 0px, ảnh biến mất hoàn toàn |
| **RULE-06** | 12-Column Grid Math Check | ⚠️ Cảnh báo | Tràn hàng, cột bị rớt dòng ngoài ý muốn |
| **RULE-07** | Website Theme Color Inheritance | ⚠️ Cảnh báo | Xung đột màu sắc nhận diện của website |
| **RULE-08** | Vertical Card Text Padding Check | ⚠️ Cảnh báo | Chữ dính sát mép ảnh đại diện |
| **RULE-09** | Tabs Container Fit-Content Check | ⚠️ Cảnh báo | Thanh tab bị giãn toác chiếm trọn 100% |
| **RULE-10** | Flexbox Stack Option Check | ⚠️ Cảnh báo | Thuộc tính lạ không nhận CSS Flexbox |
| **RULE-11** | Menu Whitelist Check | 🚨 Nghiêm ngặt | Menu chân trang bị lỗi render |
| **RULE-12** | Price Table Whitelist Check | 🚨 Nghiêm ngặt | Khối bảng giá bị vỡ bố cục |
| **RULE-13** | Google FAQ Schema Check | 💡 Khuyến nghị | Mất hiển thị Rich Snippet trên Google SERP |
| **RULE-14** | Native Reorder Check | 💡 Khuyến nghị | Trùng lặp hoặc dùng CSS order cồng kềnh |
| **RULE-15** | Shape Divider Whitelist Check | ⚠️ Cảnh báo | Không tải được vector SVG đáy/đỉnh |

---

## CHI TIẾT 15 QUY TẮC LINTER KIỂM DUYỆT

### 🚨 RULE-01: Zero-Comment Guarantee (Tuyệt Đối Không Dùng Comment HTML)
* **Quy chuẩn:** Quét toàn bộ khối code, nếu phát hiện bất kỳ đoạn `<!--` hoặc `-->`, **LINTER PHẢI BÁO LỖI NGAY**.
* **Bằng chứng mã nguồn:** File `StringToArray.php` (dòng 63–98) chứng minh Flatsome tự động bọc bất kỳ ký tự nào nằm ngoài shortcode vào `generate_text_shortcode()`. Comment nằm trong `[row]` sẽ sinh thẻ `[text]` con làm gãy Flexbox.
* **Cách sửa:** Xóa sạch toàn bộ comment HTML trong khối mã shortcode.

---

### 🚨 RULE-02: Row-Col Structural Purity (Độ Thuần Khiết Thẻ Row & Col)
* **Quy chuẩn:**
  1. Thẻ `[row]` chỉ được phép chứa thẻ con trực tiếp là `[col]` hoặc `[col_inner]`.
  2. Tuyệt đối không đặt `[ux_image]`, `[text]`, `[title]`, `[button]` trực tiếp trong `[row]` mà không có `[col]` bọc ngoài.
  3. Thẻ `[col]` bắt buộc phải có thẻ cha là `[row]` hoặc `[row_inner]`.

---

### 🚨 RULE-03: Banner Child Whitelist (Danh Mục Thẻ Con Cho Phép Của Banner)
* **Quy chuẩn:** File `ux_banner.php` (dòng 23) quy định `'allow' => array( 'text_box', 'ux_image', 'ux_lottie' )`.
* **Kiểm tra:**
  * ❌ `[ux_banner] [button text="Click"] [/ux_banner]` $\rightarrow$ **SAI**.
  * ❌ `[ux_banner] [row]...[/row] [/ux_banner]` $\rightarrow$ **SAI**.
  * ✅ `[ux_banner] [text_box] [button text="Click"] [/text_box] [/ux_banner]` $\rightarrow$ **ĐÚNG**.

---

### 🚨 RULE-04: Self-Nesting Depth Suffix (Quy Tắc Lồng Thẻ Đồng Cấp)
* **Quy chuẩn:** File `ArrayToString.php` (dòng 128–135) xác định cơ chế tạo tag chống xung đột:
  * Cấp 1 (Ngoài cùng): `[row]` $\rightarrow$ `[col]`
  * Cấp 2 (Bên trong thẻ `[col]`): Bắt buộc dùng `[row_inner]` $\rightarrow$ `[col_inner]`
  * Cấp 3 (Nếu tiếp tục lồng): Bắt buộc dùng `[row_inner_1]` $\rightarrow$ `[col_inner_1]`
* **Lỗi nghiêm trọng:** Dùng `[row]` bên trong `[col]` mà không có hậu tố `_inner` sẽ khiến trình phân giải đóng nhầm thẻ cha ngoài cùng.

---

### 🚨 RULE-05: Image Aspect-Ratio Protection (Bảo Toàn Tỉ Lệ Khung Hình)
* **Quy chuẩn:** File `ux_image.php` (dòng 62–65) xác nhận Flatsome tính chiều cao ảnh bằng `padding-top` trên `.image-cover`.
* **Kiểm tra CSS:**
  * ❌ Tuyệt đối KHÔNG viết: `.image-cover { padding-top: 0 !important; }`
  * ❌ Tuyệt đối KHÔNG viết: `.image-cover { position: absolute !important; }`
  * ✅ Thay đổi chiều cao phải dùng: `image_height="89%"` hoặc chỉnh `.image-cover { padding-top: 89% !important; }`.

---

### ⚠️ RULE-06: 12-Column Grid Math Verification (Kiểm Tra Toán Học Lưới)
* **Quy chuẩn:**
  1. Trên màn hình Desktop: Tổng `span` của các `[col]` cùng hàng trong một `[row]` phải bằng chính xác **12**.
  2. Trên màn hình Mobile: Ngoại trừ hiển thị dạng lưới 2 cột sản phẩm (`span__sm="6"`), tất cả các cột nội dung/tin tức bắt buộc phải có **`span__sm="12"`** để chống tràn chữ.

---

### ⚠️ RULE-07: Website Theme Color Inheritance (Thừa Hưởng Bảng Màu Theme)
* **Quy chuẩn:**
  * ❌ Không tự ý gán mã màu cố định cho text (ví dụ: `color: #1e293b !important;`).
  * ✅ Để văn bản, tiêu đề thừa hưởng tự nhiên từ cấu hình giao diện `Customize` của theme hoặc dùng biến hệ thống `var(--primary-color)`.

---

### ⚠️ RULE-08: Vertical Card Text Padding Check (Khoảng Đệm Thẻ Bài Viết Dọc)
* **Quy chuẩn:** Khi hiển thị bài viết dạng nằm ngang (Ảnh trái, Chữ phải: `style="vertical"`):
  * **Lỗi thường gặp:** Chữ dính sát sạt vào mép ảnh đại diện.
  * **Quy định:** Bắt buộc bổ sung CSS đệm lót:
    ```css
    .box-vertical .box-text {
        padding: 0 0 0 15px !important;
    }
    ```

---

### ⚠️ RULE-09: Tabs Container Fit-Content Check (Chống Giãn Tab Vô Tội Vạ)
* **Quy chuẩn:**
  * ❌ Không dùng `width: fit-content` hoặc `max-width: fit-content` trên khung chứa tab gây co cụm hoặc giãn toác thanh tab.
  * ✅ Điều khiển căn lề bằng thuộc tính native: `[tabgroup align="left|center|right"]`.

---

### ⚠️ RULE-10: Flexbox Stack Options Check (Kiểm Duyệt Thẻ ux_stack)
* **Quy chuẩn:** File `ux_stack.php` (dòng 17–63):
  * `direction`: Chỉ nhận `row` hoặc `col` (hỗ trợ `direction__md`, `direction__sm`).
  * `distribute`: Chỉ nhận `start`, `center`, `end`, `between`, `around`.
  * `align`: Chỉ nhận `stretch`, `start`, `center`, `end`, `baseline`.
  * `gap`: Đơn vị rem (từ `0` đến `16rem`, bước nhảy `0.25rem`).

---

### 🚨 RULE-11: Menu Whitelist Check (Danh Mục Thẻ Menu Hợp Lệ)
* **Quy chuẩn:** File `ux_menu.php` (dòng 12): `'allow' => array( 'ux_menu_link', 'ux_menu_title' )`.
* **Kiểm tra:** Bên trong `[ux_menu]...[/ux_menu]` chỉ được phép chứa:
  * `[ux_menu_title text="..."]`
  * `[ux_menu_link text="..." link="..."]`
  * Tuyệt đối không đặt `[button]`, `[row]`, `[text]` tự do vào bên trong `[ux_menu]`.

---

### 🚨 RULE-12: Price Table Whitelist Check (Danh Mục Thẻ Bảng Giá)
* **Quy chuẩn:** File `price_table.php` (dòng 8): `'allow' => array('text','bullet_item','button')`.
* **Kiểm tra:** Bên trong `[ux_price_table]...[/ux_price_table]` chỉ được phép chứa:
  * Thẻ con danh sách tính năng `[bullet_item text="..."]`
  * Thẻ chữ mô tả `[text]...[/text]`
  * Thẻ nút bấm đăng ký `[button text="..."]`

---

### 💡 RULE-13: Google FAQ Schema Check (Cấu Trúc Hỏi Đáp Chuẩn SEO)
* **Quy chuẩn:** Khi người dùng yêu cầu tạo mục Hỏi Đáp FAQ:
  * Khuyến nghị bắt buộc: Thêm thuộc tính `faq_schema="true"` vào thẻ `[accordion]`.
  * Mỗi thẻ `[accordion_item]` phải có thuộc tính `title` chứa câu hỏi rõ ràng, không được để trống.

---

### 💡 RULE-14: Native Reorder Check (Ưu Tiên Đảo Cột Bằng Thuộc Tính Native)
* **Quy chuẩn:** Khi cần đưa cột ảnh hoặc form lên đầu trang trên Mobile:
  * Thay vì viết CSS `order: 1` hoặc flex-direction phức tạp, sử dụng ngay thuộc tính native:
  * `[col force_first="small"]` (cho Mobile) hoặc `[col force_first="medium"]` (cho Tablet).

---

### ⚠️ RULE-15: Shape Divider Whitelist Check (Danh Mục 20 Shape Hợp Lệ)
* **Quy chuẩn:** File `values/dividers.php`:
  * Thuộc tính `divider` hoặc `divider_top` của `[section]` chỉ được nhận 1 trong 20 giá trị sau:
  `waves`, `waves-opacity`, `waves-opacity-2`, `waves-opacity-3`, `curve`, `curve-invert`, `curve-2`, `curve-2-invert`, `curve-opacity`, `arrow`, `arrow-invert`, `arrow-2`, `arrow-2-invert`, `tilt`, `triangle`, `triangle-invert`, `triangle-opacity`, `fan`, `book`, `book-invert`.
