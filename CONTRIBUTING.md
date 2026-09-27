# Hướng Dẫn Đóng Góp (Contributing Guide) — Flatsome UX Builder

Chào mừng và cảm ơn bạn đã quan tâm đóng góp cho dự án **Flatsome UX Builder Architect & Engineer**! Dự án được phát triển nhằm xây dựng một trợ lý AI chuẩn xác 100%, không sinh mã ảo giác cho hệ sinh thái WordPress Flatsome.

Mọi sự đóng góp từ cộng đồng — dù là sửa một lỗi chính tả, tối ưu CSS, bổ sung element mới hay chia sẻ các template UX Builder đẹp mắt — đều vô cùng quý giá!

---

## 🎯 Các Hạng Mục Dự Án Đang Cần Cộng Đồng Đóng Góp

1. **Bổ sung Template mới (`references/ux_templates_catalog.md`):**
   - Các mẫu Landing Page bán hàng chuyên nghiệp (Mỹ phẩm, Bất động sản, Đồ công nghệ...).
   - Custom WooCommerce Product Layouts & Cart/Checkout UX Blocks.
   - Header, Footer & Mega Menu sáng tạo.

2. **Mở rộng Schema Element (`references/core_elements_schema.md`):**
   - Đầy đủ thuộc tính chi tiết của các element nâng cao.
   - Hỗ trợ thêm các shortcode từ các plugin add-on phổ biến cho Flatsome.

3. **Cải tiến Linter & Validator (`references/shortcode_validator_rules.md`):**
   - Bổ sung quy tắc phát hiện shortcode lỗi, thẻ lồng sai quy cách hoặc xung đột CSS.

4. **Tối ưu hóa Responsive (`references/css_classes_utilities.md`):**
   - Các giải pháp CSS tinh gọn xử lý tràn khung (overflow), responsive table, căn chỉnh linh hoạt trên Tablet & Mobile.

---

## 📐 Bộ Quy Tắc Vàng (Bắt Buộc Tuân Thủ)

Để đảm bảo mã shortcode luôn hoạt động 100% khi dán vào Flatsome UX Builder, mọi đóng góp phải tuân thủ nghiêm ngặt:

1. **TUYỆT ĐỐI KHÔNG DÙNG COMMENT HTML:**
   - ❌ Không thêm `<!-- ... -->` bên trong mã shortcode.
   - Flatsome UX Builder sẽ tự parse comment HTML thành một khối thẻ `Text` riêng biệt gây hỏng layout.

2. **CHUẨN RESPONSIVE 3 THIẾT BỊ:**
   - Bố cục phải hiển thị tốt trên cả 3 mốc:
     - **Desktop:** $\ge 850\text{px}$
     - **Tablet:** $550\text{px} - 849\text{px}$
     - **Mobile:** $< 550\text{px}$
   - Tận dụng triệt để các thuộc tính hậu tố native của Flatsome (`__md`, `__sm`) và class tiện ích (`hide-for-small`, `show-for-small`, `text-center-small`...).

3. **BẢO TỒN ASPECT-RATIO CỦA HÌNH ẢNH:**
   - Flatsome sử dụng cơ chế `padding-top: XX%` để tính tỉ lệ khung hình trên `.image-cover`.
   - ❌ Tuyệt đối không can thiệp CSS làm đè bẹp chiều cao ảnh hoặc gán `padding-top: 0 !important`.

4. **TÔN TRỌNG BẢNG MÀU MẶC ĐỊNH CỦA WEBSITE:**
   - Ưu tiên để các thẻ văn bản, tiêu đề thừa hưởng màu sắc mặc định của theme, tránh ép cứng các mã màu lạ trừ khi là chủ đích của template.

---

## 🛠️ Quy Trình Gửi Đóng Góp (Pull Request)

1. **Fork dự án:**
   - Nhấn nút **Fork** ở góc trên bên phải của repository [tuankietdigital/flatsome-ux-builder](https://github.com/tuankietdigital/flatsome-ux-builder).

2. **Tạo nhánh mới (Branch):**
   ```bash
   git checkout -b feature/ten-tinh-nang-moi
   # hoặc: git checkout -b fix/ten-loi-can-sua
   ```

3. **Thực hiện thay đổi & Kiểm thử:**
   - Chỉnh sửa tài liệu hoặc template tương ứng.
   - **Test trực tiếp trên UX Builder của một website WordPress thật** để đảm bảo không bị lỗi giao diện và responsive mượt mà.

4. **Commit & Push:**
   ```bash
   git commit -m "feat: bổ sung template Landing Page Bất Động Sản chuẩn responsive"
   git push origin feature/ten-tinh-nang-moi
   ```

5. **Tạo Pull Request (PR):**
   - Vào GitHub của bạn và bấm **New Pull Request**.
   - Mô tả ngắn gọn: Bạn đã thêm/sửa gì? Đã test trên màn hình nào? Có hình ảnh minh họa đính kèm càng tốt.
   - Tác giả (**Quách Trần Tuấn Kiệt**) sẽ review và merge vào dự án chính!

---

## 💬 Báo Lỗi & Đề Xuất Ý Tưởng Mới

Nếu bạn không rành về Git/Code nhưng phát hiện lỗi hoặc có ý tưởng hay:
- Hãy mở một **[GitHub Issue](https://github.com/tuankietdigital/flatsome-ux-builder/issues)** để chia sẻ.
- Mô tả rõ lỗi bạn gặp phải kèm ảnh chụp màn hình hoặc đoạn shortcode bị lỗi.

Cảm ơn bạn đã chung tay xây dựng cộng đồng WordPress Flatsome & AI ngày càng phát triển! 🚀
