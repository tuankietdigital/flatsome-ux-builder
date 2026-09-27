# 🎨 Flatsome UX Builder Architect & Engineer — Quách Trần Tuấn Kiệt

> **Hệ thống AI Assistant chuyên gia tạo mã Shortcode, Element, Layout và tối ưu hóa Responsive 3 thiết bị (Desktop, Tablet, Mobile) chuẩn 100% không ảo giác cho theme WordPress Flatsome 3.20.5.**

[![Author](https://img.shields.io/badge/Author-Quách%20Trần%20Tuấn%20Kiệt-blue.svg)](https://github.com/tuankietdigital)
[![Flatsome Version](https://img.shields.io/badge/Flatsome-3.20.5%20Verified-green.svg)](https://uxthemes.com)
[![Elements](https://img.shields.io/badge/Elements-86%20Native%20Shortcodes-orange.svg)](references/core_elements_schema.md)
[![WordPress](https://img.shields.io/badge/WordPress-6.x+-blue.svg)](https://wordpress.org)
[![License](https://img.shields.io/badge/License-MIT-purple.svg)](LICENSE)

---

## 🌟 Giới Thiệu (About)

**Flatsome UX Builder Skill** là bộ kỹ năng mở rộng cao cấp dành cho trợ lý lập trình **Antigravity / Gemini CLI**, được đối chiếu và dịch ngược trực tiếp từ mã nguồn PHP gốc của **Flatsome phiên bản 3.20.5**. Dự án giải quyết dứt điểm các vấn đề nhức nhối khi thiết kế website Flatsome:

- 🛡️ **Chuẩn xác 100% từ mã nguồn (Ground Truth 86 Elements):** Toàn bộ 86 elements native (bao gồm `[ux_stack]`, `[ux_text]`, `[ux_lottie]`, `[ux_hotspot]`, `[ux_price_table]`, `[ux_menu]`, 13 elements WooCommerce Custom Product) đều được thẩm định trực tiếp từ code PHP gốc của theme.
- 🚫 **Zero-Comment Clean Code:** Thuật toán `StringToArray.php` của Flatsome biến mọi comment HTML `<!-- ... -->` thành thẻ `[text]` con trái phép làm vỡ layout Flexbox. Bộ skill này cam kết **100% mã nguồn sạch không comment rác**.
- 📱 **Kiến Trúc Responsive-First 3 Thiết Bị:** Tự động tối ưu đồng bộ cho cả **Desktop** ($\ge 850\text{px}$), **Tablet** ($550\text{px} - 849\text{px}$ qua hậu tố `__md`), và **Mobile** ($< 550\text{px}$ qua hậu tố `__sm`).
- ⚡ **Flexbox Stack Hiện Đại (`[ux_stack]`):** Dàn trang các cụm nút bấm, icon + chữ nhẹ hơn 75% DOM so với việc lạm dụng `[row]` + `[col]`.
- 🔄 **Đảo Vị Trí Cột Native (`force_first`):** Đưa hình ảnh hoặc form lên đầu trang trên Mobile bằng `[col force_first="small"]` mà không cần viết CSS `order` phức tạp.
- 🔍 **Google FAQ Schema Tự Động:** Tích hợp `[accordion faq_schema="true"]` giúp Flatsome tự xuất dữ liệu có cấu trúc JSON-LD FAQPage lên Google Search.
- 🌊 **20 SVG Shape Dividers Native:** Hỗ trợ đầy đủ các kiểu đáy/đỉnh lượn sóng (`waves`, `curve`, `tilt`, `triangle`...).
- 🎨 **Tôn Trọng Màu Sắc Website:** Kế thừa tự nhiên bảng màu thương hiệu của theme, không tự ý áp đặt mã màu hex lạ.
- 📐 **Bảo Toàn Khung Hình Aspect-Ratio:** Bảo vệ tuyệt đối cơ chế `padding-top` trên `.image-cover`, chấm dứt hoàn toàn lỗi sập chiều cao làm biến mất ảnh.

---

## 🚀 Hướng Dẫn Cài Đặt (Installation)

### Cách 1: Tải nhanh bằng Git (Dành cho Terminal / CLI)
```bash
# Clone trực tiếp vào thư mục skills toàn cục của Antigravity / Gemini:
git clone https://github.com/tuankietdigital/flatsome-ux-builder.git ~/.gemini/config/skills/flatsome-ux-builder
```

### Cách 2: Tải thủ công (Không cần Git)
1. Bấm nút xanh **Code** $\rightarrow$ chọn **Download ZIP** tại repo [tuankietdigital/flatsome-ux-builder](https://github.com/tuankietdigital/flatsome-ux-builder).
2. Giải nén vào thư mục cấu hình:
   * **Windows:** `C:\Users\<Tên_User>\.gemini\config\skills\flatsome-ux-builder\`
   * **macOS / Linux:** `~/.gemini/config/skills/flatsome-ux-builder/`
3. Khởi động lại Antigravity IDE hoặc gõ `/skills` để kiểm tra.

---

## 🧭 Bộ Lệnh Điều Hành (Command Palette)

Bạn có thể kích hoạt trợ lý bằng cách gõ trực tiếp các lệnh tắt sau vào khung chat:

| Lệnh tắt | Cú pháp mẫu | Chức năng chính |
| :--- | :--- | :--- |
| **`UX BUILD`** | `UX BUILD: Thiết kế Hero Banner 2 cột cho shop công nghệ` | Sinh mã shortcode và CSS trọn vẹn cho 1 section/trang hoàn chỉnh, chuẩn 3 thiết bị. |
| **`UX ELEMENT`** | `UX ELEMENT: [ux_stack] dàn 2 nút CTA trên mobile` | Tạo nhanh mã shortcode cho 1 trong 86 element cụ thể với đầy đủ tham số chuẩn. |
| **`UX VALIDATE`** | `UX VALIDATE: [đoạn mã shortcode cần kiểm tra]` | Bộ linter 15 quy tắc tự động phát hiện thẻ quên đóng, lỗi lồng thẻ, bảo vệ aspect-ratio. |
| **`UX TEMPLATE`** | `UX TEMPLATE: Bảng giá dịch vụ SaaS chuyển đổi cao` | Xuất ngay 1 trong 12 mẫu thiết kế thực chiến chuẩn hóa: Hero, Bảng giá, Magazine, FAQ Schema... |
| **`UX EXTEND`** | `UX EXTEND: Bảng thông số kỹ thuật` | Sinh mã nguồn PHP `add_ux_builder_shortcode()` & `ux_builder_edit_element()` cho Child Theme. |

---

## 🗂️ Cấu Trúc Thư Mục Tri Thức

```
flatsome-ux-builder/
├── SKILL.md                                  # Hub điều hành trung tâm & 10 Nguyên tắc vàng v2.0
├── README.md                                 # Tài liệu giới thiệu & Hướng dẫn sử dụng
├── CONTRIBUTING.md                           # Hướng dẫn đóng góp mã nguồn mở
├── LICENSE                                   # Giấy phép MIT (Quách Trần Tuấn Kiệt)
└── references/
    ├── core_elements_schema.md               # Danh mục 86 core elements Flatsome 3.20.5 & Hậu tố Responsive
    ├── layout_grid_system.md                 # Quy chuẩn lưới 12 cột, Flexbox ux_stack & Blueprint Mobile/Tablet
    ├── ux_templates_catalog.md               # 12 Mẫu template chuẩn 100% Responsive, Zero-Comment
    ├── css_classes_utilities.md              # Class tiện ích, Visibility Helpers & Khung Media Queries 4 cấp
    ├── shortcode_validator_rules.md          # 15 Quy tắc Linter soát lỗi cú pháp & responsive
    └── developer_extension_guide.md          # Code mẫu PHP add_ux_builder_shortcode() cho Child Theme
```

---

## 🤝 Đóng Góp Phát Triển (Contributing)

Mọi đóng góp từ cộng đồng đều được hoan nghênh nồng nhiệt! Bạn có thể:
- 💡 Bổ sung thêm các **Template UX Builder** đẹp mắt, hiện đại.
- 📐 Cập nhật thêm các thuộc tính, shortcode add-on nâng cao.
- 🐛 Báo cáo các lỗi phát sinh hoặc đề xuất ý tưởng mới qua [GitHub Issues](https://github.com/tuankietdigital/flatsome-ux-builder/issues).

👉 Xem chi tiết quy chuẩn và cách gửi Pull Request tại **[CONTRIBUTING.md](CONTRIBUTING.md)**.

---

## 👨‍💻 Tác Giả (Author)

- **Tác giả:** **Quách Trần Tuấn Kiệt**
- **Lĩnh vực chuyên môn:** Senior Flatsome & WooCommerce Technical Architect / AI Automation Engineer.
- **GitHub:** [@tuankietdigital](https://github.com/tuankietdigital)

---

## 📄 Bản Quyền (License)

Dự án được phân phối dưới giấy phép mã nguồn mở [MIT License](LICENSE). Bạn hoàn toàn có thể tự do sử dụng, chỉnh sửa và chia sẻ cho cộng đồng.
