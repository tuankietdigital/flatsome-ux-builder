# 🎨 Flatsome UX Builder Architect & Engineer — Quách Trần Tuấn Kiệt

> **Hệ thống AI Assistant chuyên gia tạo mã Shortcode, Element, Layout và tối ưu hóa Responsive 3 thiết bị (Desktop, Tablet, Mobile) chuẩn 100% không ảo giác cho theme WordPress Flatsome 3.x+.**

[![Author](https://img.shields.io/badge/Author-Quách%20Trần%20Tuấn%20Kiệt-blue.svg)](https://github.com)
[![Flatsome Version](https://img.shields.io/badge/Flatsome-3.x+-green.svg)](https://uxthemes.com)
[![WordPress](https://img.shields.io/badge/WordPress-6.x+-blue.svg)](https://wordpress.org)
[![License](https://img.shields.io/badge/License-MIT-orange.svg)](LICENSE)

---

## 🌟 Giới Thiệu (About)

**Flatsome UX Builder Skill** là bộ kỹ năng mở rộng dành cho trợ lý lập trình **Antigravity / Gemini CLI**, được thiết kế để giải quyết dứt điểm các vấn đề nhức nhối khi làm việc với theme Flatsome:
- ❌ **Không ảo giác thuộc tính (Zero-Hallucination):** 100% thuộc tính được đối chiếu trực tiếp từ mã nguồn lõi Flatsome và [UX Themes Documentation](https://docs.uxthemes.com/).
- ❌ **Zero-Comment Clean Code:** Không sinh thẻ ghi chú HTML `<!-- ... -->` trong mã nguồn làm rác cây DOM (Tree View) và sinh lỗi đệm thừa trong UX Builder.
- ❌ **Không phá màu sắc website:** Kế thừa tự nhiên bảng màu thương hiệu của website hoặc dùng `var(--primary-color)`.
- 📱 **Kiến Trúc Responsive-First 3 Thiết Bị:** Tự động tối ưu đồng bộ cho cả **Desktop** ($\ge 850\text{px}$), **Tablet** ($550\text{px} - 849\text{px}$ qua `__md`), và **Mobile** ($< 550\text{px}$ qua `__sm`).
- 📐 **Toán Học Chiều Cao Khớp Từng Pixel:** Đáy bài viết nổi bật, thanh trượt slider và các banner phụ luôn phẳng đáy đều tăm tắp mà không làm sập khung ảnh (`.image-cover`).

---

## 🚀 Hướng Dẫn Cài Đặt (Installation)

### Cách 1: Cài đặt Toàn Cục (Global Skill - Dùng cho mọi dự án)
Bạn chỉ cần tải hoặc clone thư mục này vào thư mục cấu hình cá nhân của Antigravity / Gemini CLI:

- **Trên Windows:**
  ```powershell
  # Đường dẫn thư mục:
  C:\Users\<Tên_User>\.gemini\config\skills\flatsome-ux-builder\
  ```

- **Trên macOS / Linux:**
  ```bash
  # Clone trực tiếp vào thư mục skills:
  git clone https://github.com/<tai-khoan-cua-ban>/flatsome-ux-builder.git ~/.gemini/config/skills/flatsome-ux-builder
  ```

### Cách 2: Cài đặt cho riêng 1 Workspace / Project
Copy thư mục `flatsome-ux-builder` vào thư mục dự án của bạn tại đường dẫn:
```
<thu-muc-du-an>/.gemini/skills/flatsome-ux-builder/
```

Sau khi copy xong, khởi động lại Antigravity IDE hoặc gõ `/skills` để kiểm tra.

---

## 🧭 Bộ Lệnh Điều Hành (Command Palette)

Bạn có thể kích hoạt trợ lý bằng cách gõ trực tiếp các lệnh tắt sau vào khung chat:

| Lệnh tắt | Cú pháp mẫu | Chức năng chính |
| :--- | :--- | :--- |
| **`UX BUILD`** | `UX BUILD: Thiết kế Hero Banner 2 cột cho shop công nghệ` | Sinh mã shortcode và CSS trọn vẹn cho 1 section/trang hoàn chỉnh, chuẩn 3 thiết bị. |
| **`UX ELEMENT`** | `UX ELEMENT: [ux_products] dạng slider 5 cột` | Tạo nhanh mã shortcode cho 1 element cụ thể với đầy đủ tham số chuẩn. |
| **`UX VALIDATE`** | `UX VALIDATE: [đoạn mã shortcode cần kiểm tra]` | Bộ linter 12 quy tắc tự động phát hiện thẻ quên đóng, lỗi lồng thẻ và sửa code. |
| **`UX TEMPLATE`** | `UX TEMPLATE: Section tin tức 1 lớn 6 nhỏ` | Xuất ngay các mẫu thiết kế thực chiến chuẩn hóa có sẵn trong catalog. |
| **`UX EXTEND`** | `UX EXTEND: Bảng thông số kỹ thuật` | Sinh mã nguồn PHP `add_ux_builder_shortcode()` để tích hợp element vào Child Theme. |

---

## 🛡️ Hệ Thống 10 Quy Tắc Vàng (10 Golden Rules)

1. **Strict Whitelist:** Chỉ dùng thuộc tính chính thức được hỗ trợ bởi Flatsome 3.x+.
2. **Nesting Hierarchy:** Phân cấp an toàn `Section -> Row -> Col` (cấm lồng `[row]` trực tiếp trong `[col]`).
3. **Kiến Trúc Responsive-First 3 Thiết Bị:** Bắt buộc luôn khai báo `span__md` và `span__sm`.
4. **CSS Utilities & Responsive Classes:** Khai thác tối đa `.hide-for-small`, `.show-for-small`, `.text-center-small`.
5. **Reusable UX Blocks:** Đóng gói các khối lặp lại vào UX Blocks (`[block id="..."]`).
6. **Zero-Comment Clean Code:** 100% không chèn comment `<!-- ... -->` trong mã shortcode.
7. **Tôn Trọng Màu Sắc Mặc Định Của Website:** Không gán cứng màu sắc lạ, để chữ và link tự động kế thừa màu theme.
8. **Khoảng Cách Đệm Thumbnail-to-Text $\ge 15\text{px}$:** Giữ `padding: 0 0 0 15px !important;` trên `.box-text` ở layout ngang.
9. **Bảo Toàn Cơ Chế Aspect-Ratio:** Tuyệt đối không xóa `padding-top: 0` trên `.image-cover` làm mất ảnh.
10. **Thiết Kế Tab Tiêu Đề `fit-content`:** Giữ tab H2 ôm khít văn bản, không để tràn hàng.

---

## 🗂️ Cấu Trúc Thư Mục (Folder Structure)

```
flatsome-ux-builder/
├── SKILL.md                                  # Hub điều hành trung tâm & 10 Nguyên tắc vàng
├── README.md                                 # Tài liệu giới thiệu & Hướng dẫn sử dụng
└── references/
    ├── core_elements_schema.md               # Danh mục 35+ core elements, [blog_posts] & Hậu tố Responsive
    ├── layout_grid_system.md                 # Quy chuẩn lưới 12 cột, 3 Breakpoints & Blueprint Mobile/Tablet
    ├── ux_templates_catalog.md               # 8 Mẫu template chuẩn 100% Responsive, Zero-Comment
    ├── css_classes_utilities.md              # Class tiện ích, Responsive Helpers & Khung Media Queries 4 cấp
    ├── shortcode_validator_rules.md          # 12 Quy tắc Linter soát lỗi cú pháp & responsive
    └── developer_extension_guide.md          # Boilerplate code PHP đăng ký Custom Elements cho Child Theme
```

---

## 👨‍💻 Tác Giả (Author)

- **Tác giả:** **Quách Trần Tuấn Kiệt**
- **Lĩnh vực chuyên môn:** Senior Flatsome & WooCommerce Technical Architect / AI Automation Engineer.

---

## 📄 Bản Quyền (License)

Dự án được phân phối dưới giấy phép mã nguồn mở [MIT License](LICENSE). Bạn hoàn toàn có thể tự do sử dụng, chỉnh sửa và chia sẻ cho cộng đồng.
