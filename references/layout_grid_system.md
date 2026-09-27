# Hệ Thống Lưới 12 Cột, Flexbox Stack & Responsive 3 Thiết Bị (Flatsome 3.20.5)

> **Tác giả:** Quách Trần Tuấn Kiệt  
> **Kiến trúc:** Đối chiếu và chuẩn hóa 100% theo hệ thống lưới Flexbox & Media Queries gốc của Flatsome (`assets/css/flatsome.css` & `inc/builder/shortcodes/row.php`, `col.php`, `ux_stack.php`).

---

## 1. MA TRẬN 3 ĐIỂM NGẮT THIẾT BỊ NATIVE (3-BREAKPOINT MATRIX)

Mã nguồn CSS gốc của Flatsome (`flatsome.css`) sử dụng chính xác 2 mốc ngắt phân chia 3 môi trường hiển thị:

| Thiết Bị | Khoảng Kích Thước Màn Hình | Media Query Gốc Của Flatsome | Quy Chuẩn Thuộc Tính Shortcode |
| :--- | :--- | :--- | :--- |
| **Desktop** | $\ge 850\text{px}$ (Large) | `@media screen and (min-width: 850px)` | Không dùng hậu tố (ví dụ: `span="4"`, `gap="1.5rem"`) |
| **Tablet** | $550\text{px} - 849\text{px}$ (Medium) | `@media screen and (min-width: 550px) and (max-width: 849px)` | Hậu tố `__md` (ví dụ: `span__md="6"`, `gap__md="1rem"`) |
| **Mobile** | $< 550\text{px}$ (Small) | `@media screen and (max-width: 549px)` | Hậu tố `__sm` (ví dụ: `span__sm="12"`, `gap__sm="0.5rem"`) |

---

## 2. MA TRẬN QUYẾT ĐỊNH: LƯỚI 12 CỘT (`[row]`) VS FLEXBOX STACK (`[ux_stack]`)

Trong Flatsome hiện đại (3.20.5), lập trình viên có 2 công cụ bố cục cực mạnh. Bảng sau chỉ rõ khi nào nên dùng công cụ nào để đạt hiệu năng tải trang và UI/UX cao nhất:

| Tiêu Chí | Hệ Thống Lưới 12 Cột (`[row]` + `[col]`) | Hệ Thống Flexbox Stack (`[ux_stack]`) |
| :--- | :--- | :--- |
| **Mục đích chính** | Phân chia bố cục trang lớn (Cột nội dung chính, Sidebar, Lưới 3-4 card sản phẩm, Bố cục Magazine so le). | Dàn các cụm component nhỏ (2 nút bấm CTA, Nhóm Icon + Text, Cụm tác giả, Nhãn tags, Thanh lọc). |
| **Độ phức tạp DOM** | Nặng hơn (Cần thẻ bọc ngoài `[row]` và từng thẻ `[col]`). | Siêu nhẹ (Chỉ một thẻ bọc `[ux_stack]`, bên trong là các phần tử con trực tiếp). |
| **Căn lề tự do** | Tuân thủ nghiêm ngặt bước nhảy tỉ lệ chia hết cho 12 (1/12 đến 12/12). | Tự do theo trục Flexbox: `distribute="between|center|start"`, `align="center"`. |
| **Khoảng cách con** | Thuộc tính `style="small|normal|large"` của `[row]`. | Thuộc tính `gap="0.5rem|1rem|2rem"` tùy biến mượt mà mọi kích thước. |
| **Đổi hướng Responsive** | Các cột tự động xếp chồng theo độ rộng `span__sm="12"`. | Đổi hướng tức thì: `direction="row" direction__sm="col"`. |

---

## 3. TOÁN HỌC HỆ THỐNG LƯỚI 12 CỘT (THE 12-COLUMN GRID MATH)

Khung lưới của Flatsome được xây dựng trên hệ thống 12 phần bằng nhau ($100\% / 12 \approx 8.3333\%$ cho mỗi đơn vị `span`).

### 3.1. Định Luật Tổng Cột Bằng 12 Trên Desktop
Trên một hàng `[row]`, tổng `span` của các `[col]` anh em cùng cấp phải bằng chính xác **12**:
* 2 Cột đều nhau: $6 + 6 = 12$ $\rightarrow$ `[col span="6"]` + `[col span="6"]`
* 3 Cột đều nhau: $4 + 4 + 4 = 12$ $\rightarrow$ 3 thẻ `[col span="4"]`
* 4 Cột đều nhau: $3 + 3 + 3 + 3 = 12$ $\rightarrow$ 4 thẻ `[col span="3"]`
* Bố cục Nội dung Chính + Sidebar: $8 + 4 = 12$ $\rightarrow$ `[col span="8"]` + `[col span="4"]`
* Bố cục 3 Cột so le (Lớn ở giữa): $3 + 6 + 3 = 12$ $\rightarrow$ `[col span="3"]` + `[col span="6"]` + `[col span="3"]`

### 3.2. Định Luật Xếp Chồng An Toàn Trên Mobile (`span__sm="12"`)
Màn hình điện thoại ($<550\text{px}$) có không gian hẹp. Quy tắc an toàn tuyệt đối là cho mỗi cột chiếm trọn 1 dòng:
```shortcode
[row]
  [col span="4" span__md="6" span__sm="12"][/col]
  [col span="4" span__md="6" span__sm="12"][/col]
  [col span="4" span__md="12" span__sm="12"][/col]
[/row]
```
* **Desktop ($\ge 850\text{px}$):** 3 cột ngang hàng ($4 + 4 + 4 = 12$).
* **Tablet ($550-849\text{px}$):** Hàng trên 2 cột ($6 + 6 = 12$), hàng dưới 1 cột lớn ($12$).
* **Mobile ($< 550\text{px}$):** 3 cột xếp chồng 100% màn hình, không bị chèn ép chữ.

---

## 4. TÍNH NĂNG NATIVE ĐẢO THỨ TỰ CỘT TRÊN MOBILE (`force_first`)

Trước đây, khi muốn đưa cột hình ảnh lên trước trên thiết bị di động, người dùng thường phải viết mã CSS phức tạp. Trong Flatsome 3.20.5, tính năng này đã có sẵn trực tiếp trong shortcode:

### Cú pháp:
* `[col span="6" force_first="small"]`: Đẩy cột này lên **vị trí đầu tiên khi xem trên Mobile**.
* `[col span="6" force_first="medium"]`: Đẩy cột này lên **vị trí đầu tiên khi xem trên Tablet**.

### Ứng dụng thực chiến (Bố cục Văn bản Trái — Hình ảnh Phải):
* **Trên Desktop:** Người đọc nhìn thấy Văn bản bên trái $\rightarrow$ Ảnh bên phải.
* **Trên Mobile:** Bạn muốn khách hàng xem Ảnh trước để thu hút $\rightarrow$ Gán `force_first="small"` cho cột ảnh!
```shortcode
[row v_align="middle"]
  [col span="6" span__sm="12"]
    <h3>Giới Thiệu Sản Phẩm</h3>
    <p>Nội dung mô tả chi tiết tính năng sản phẩm...</p>
    [button text="Xem Ngay"]
  [/col]
  [col span="6" span__sm="12" force_first="small"]
    [ux_image id="123"]
  [/col]
[/row]
```

---

## 5. CÔNG THỨC TOÁN CÂN BẰNG CHIỀU CAO & BẢO TOÀN ASPECT-RATIO

### 5.1. Bằng chứng mã nguồn về Aspect-Ratio của Container Ảnh
Trong file gốc `inc/builder/shortcodes/ux_image.php` (dòng 62–65), Flatsome điều khiển chiều cao của ảnh bằng cơ chế:
```css
.image-cover {
    padding-top: {{ height }};
}
```
* Container ngoài cùng giữ khoảng không gian chiều cao bằng phần trăm padding-top.
* Thẻ `<img>` bên trong được gán `position: absolute; width: 100%; height: 100%; object-fit: cover;`.
* ⚠️ **CẢNH BÁO SỐNG CÒN:** Nếu vô tình viết CSS `padding-top: 0 !important;` lên class `.image-cover`, container sẽ sập chiều cao về 0px và ảnh lập tức biến mất!

### 5.2. Công thức Cân Bằng Chiều Cao Bố Cục Tạp Chí (Magazine Layout)
Bài toán: Cột trái là **1 Card lớn (Ảnh + Tiêu đề + Trích dẫn)**, Cột phải là **3 Bài viết nhỏ xếp chồng dọc** (`style="vertical"`).
Làm sao để Card bên trái có chiều cao bằng khít với tổng 3 bài bên phải trên Desktop, nhưng không bị méo ảnh trên Mobile?

$$\text{Tổng Chiều Cao Cột Phải} = (3 \times \text{Card Height}) + (2 \times \text{Row Gap})$$

* Giả sử mỗi bài nhỏ bên phải cao khoảng $130\text{px}$, tổng 3 bài $\approx 410\text{px}$.
* Ở cột bên trái, card lớn có tiêu đề + trích dẫn cao khoảng $120\text{px}$.
* Phần ảnh thumbnail bên trái cần cao $\approx 290\text{px}$.
* Tỉ lệ `image_height` chuẩn xác để đạt được kích thước này trên màn hình Desktop thông thường là **$89\%$**!
* Khi xuống Mobile ($<550\text{px}$), cột trái và phải xếp chồng lên nhau. Do đó, tỉ lệ ảnh cần giảm về mức chuẩn **$65\%$** để màn hình điện thoại không bị chiếm trọn bởi 1 bức ảnh quá dài:

```css
/* Tối ưu cân bằng ảnh bài viết nổi bật bên trái */
.featured-post-card .image-cover {
    padding-top: 89% !important; /* Cân bằng với 3 hàng bài viết bên phải trên Desktop */
}

@media (max-width: 549px) {
    .featured-post-card .image-cover {
        padding-top: 65% !important; /* Gọn gàng, chuẩn tỉ lệ vàng trên Mobile */
    }
}
```

---

## 6. QUY TẮC CỘT DÍNH THÔNG MINH (STICKY COLUMN)

Flatsome 3.20.5 hỗ trợ cột bám dính khi cuộn trang dài (rất thích hợp cho Sidebar, Giỏ hàng thu gọn hoặc Form đặt lịch):
* `[col span="4" sticky="true"]`: Dùng CSS `position: sticky`. Yêu cầu thẻ cha không bị gán `overflow: hidden`.
* `[col span="4" sticky="true" sticky_mode="javascript"]`: Dùng JavaScript theo dõi viewport, giúp tính toán khoảng cách mượt mà và dừng lại chính xác ở chân trang `footer`.
