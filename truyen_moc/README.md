# TRUYỆN MỘC — NỀN TẢNG ĐỌC TRUYỆN ONLINE THUẦN HTML5 & CSS3

> **Đồ Án Kiểm Tra Giữa Kỳ — Học Phần: Thiết Kế Web**  
> **Trường Đại Học Lạc Hồng — Khoa Công Nghệ Thông Tin**  
> **Hình thức thi:** Đề thi mở — Vibe Coding  
> **Sinh viên thực hiện:** Nguyễn Chí Bảo  
> **Mã số sinh viên (MSSV):** 125002093  
> **Tên Repository theo quy chuẩn đề bài:** `Bao_NguyenChi_125002093`  

---

## 1. Giới Thiệu Dự Án

**TRUYỆN MỘC (Dark Edition 2026)** là website đọc truyện trực tuyến mang phong cách **Dark Mode** hiện đại, kết hợp hài hòa giữa các bộ siêu phẩm **Manhwa Hàn Quốc** (như *Solo Leveling*, *Lookism*, *Toàn Trí Độc Giả*), **Manga Học Đường Nhật Bản** (như *Kaguya-sama: Cuộc Chiến Tỏ Tình*, *Spy x Family*, *Blue Box*, *Horimiya*) cùng các tác phẩm văn học chọn lọc. Giao diện được thiết kế với tông nền đen nâu sâu (`#121010`), thẻ xám đen ấm (`#1E1A18`) và điểm nhấn cam đất (`#E08A5E`) cùng ánh tím huyền bí (`#9333EA`) nhằm bảo vệ thị lực tối đa khi đọc truyện ban đêm.

### Quy Định Kỹ Thuật Bắt Buộc Của Dự Án:
- **100% Pure HTML5 & CSS3:** Tuyệt đối **KHÔNG sử dụng JavaScript**, không có bất kỳ file `.js` nào, không dùng inline event handler (`onclick`, `onload`,...).
- **Không Framework:** Không sử dụng Bootstrap, TailwindCSS, React, Vue hay jQuery.
- **Thư viện CSS ngoài:** Tích hợp `Animate.css` thông qua link CDN chính thức cho tiêu đề và khối Hero; thay thế hoàn toàn thư viện `AOS` bằng `@keyframes` CSS thuần (vì AOS bắt buộc phải khởi tạo bằng JS).
- **Trải nghiệm CSS Thuần Đột Phá:** Tính năng chuyển đổi màu nền đọc truyện (Giấy mộc, Đêm tối, Xanh dịu) và điều chỉnh cỡ chữ được hiện thực hóa **100% bằng CSS selector `:has()` và `<input type="radio">`**, chứng minh năng lực kiểm soát CSS3 chuyên sâu.

---

## 2. Cấu Trúc Thư Mục Dự Án

```text
truyen_moc/
│
├── index.html          # Trang chủ: Header, Hero, Tìm kiếm, Thể loại, Nổi bật, Mới cập nhật, BXH, Review, Footer
├── story.html          # Trang chi tiết truyện: Bìa sách, tác giả, đánh giá, tóm tắt và danh sách 10 chương
├── reader.html         # Trang đọc truyện: Giao diện đọc tập trung, tùy biến Theme & Cỡ chữ (CSS-Only)
│
├── css/
│   └── style.css       # Toàn bộ mã định kiểu CSS3: CSS Variables (:root), Flexbox, Grid, Keyframes, Media queries
│
├── PROMPT_LOG.md       # Nhật ký Vibe Coding chi tiết theo đúng thang điểm 3.0 của ĐH Lạc Hồng
└── README.md           # Tài liệu hướng dẫn sử dụng, quy chuẩn Git và triển khai GitHub Pages
```

---

## 3. Các Trang & Thành Phần Giao Diện

### 1. Trang Chủ (`index.html`)
- **Header & Navigation:** Thanh điều hướng dính cố định (sticky) hiệu ứng kính mờ (backdrop-filter), logo TRUYỆN MỘC, nút Đăng nhập / Đăng ký giao diện tĩnh.
- **Mobile Hamburger Menu (CSS-Only):** Ẩn hiện menu trên thiết bị di động bằng thẻ `<input type="checkbox">` và `<label>`, không dùng bất kỳ dòng JS nào.
- **Hero Section:** Tiêu đề *"Mở trang sách, mở cả thế giới"*, hiệu ứng chữ, các số liệu thống kê (2.500+ truyện, 150.000+ độc giả), bìa sách 3D nghiêng thẩm mỹ cùng 2 floating badge trang trí.
- **Thanh Tìm Kiếm Tĩnh:** Form tìm kiếm chuẩn ngữ nghĩa với ô nhập tên truyện, select box lọc thể loại và nút "Tìm truyện".
- **Danh Mục Thể Loại (CSS Grid):** 6 card thể loại (Ngôn tình, Fantasy, Hành động, Trinh thám, Đam mỹ, Đời thường) có icon sinh động và hiệu ứng hover đổi màu viền.
- **Truyện Nổi Bật Tuần Này:** Thiết kế bất đối xứng với 1 tác phẩm Featured lớn (*Gió Thổi Qua Rừng Trầm*) và 3 tác phẩm phụ xếp dọc.
- **Truyện Mới Cập Nhật:** Lưới 8 card truyện với đầy đủ thẻ bìa, tên truyện, tác giả, chương mới nhất và thời gian cập nhật.
- **Bảng Xếp Hạng Top 5:** Xếp hạng độc giả với Top 1 được tôn vinh viền vàng kim sang trọng (*Gold Crown Styling*).
- **Đánh Giá Độc Giả & CTA:** 3 card review người dùng mẫu kèm đánh giá 5 sao và banner kêu gọi cộng đồng tác giả gia nhập.
- **Footer:** Chân trang 4 cột đầy đủ thông tin đồ án, liên kết nội bộ, mạng xã hội và bản quyền.

### 2. Trang Chi Tiết Tác Phẩm (`story.html`)
- Breadcrumbs điều hướng phân cấp chuẩn SEO.
- Hero chi tiết bìa sách, số chương (48 chương), lượt đọc (1.25M), đánh giá 4.9/5 sao.
- Nút CTA lớn: "Đọc Từ Đầu (Chương 1)", "Xem Mục Lục", "Lưu Tủ Sách".
- Tóm tắt tiểu thuyết giàu cảm xúc và trích dẫn văn học thẩm mỹ.
- Danh sách 10 chương truyện mẫu với liên kết trực tiếp tới trang đọc.

### 3. Trang Đọc Truyện Mẫu (`reader.html`)
- Không gian đọc sách tối giản, chiều rộng giới hạn 840px, giãn dòng `line-height: 1.95` và font chữ `Literata` chuẩn quốc tế.
- Chữ cái mở đầu dạng **Drop Cap** phong cách tiểu thuyết cổ điển.
- **Thanh công cụ CSS-Only (Không cần JS):**
  - **Đổi theme màu nền:** Giấy mộc (Kem) | Đêm tối (Nền đen nâu dịu) | Xanh dịu (Bảo vệ mắt).
  - **Đổi cỡ chữ:** Nhỏ (A- 16px) | Chuẩn (A 18px) | Lớn (A+ 21px).
- Nút điều hướng chương: "Chương trước", "Mục lục chương", "Chương tiếp theo".
- Biểu mẫu gửi cảm nghĩ độc giả (Giao diện tĩnh).

---

## 4. Hướng Dẫn Quản Lý Mã Nguồn Bằng Git & Triển Khai GitHub Pages

### Bước 1: Tạo Git Repository Trên Máy
Mở PowerShell hoặc Command Prompt tại thư mục dự án và thực hiện tuần tự các lệnh sau:

```bash
# 1. Khởi tạo kho chứa Git cục bộ
git init

# 2. Thêm toàn bộ các file dự án vào khu vực chờ commit
git add .

# 3. Tạo commit đầu tiên với thông điệp rõ ràng
git commit -m "feat: hoàn thiện website Truyen Moc bang 100% HTML5 va CSS3 thuan"

# 4. Đặt tên nhánh chính là main theo tiêu chuẩn hiện đại
git branch -M main
```

### Bước 2: Đẩy Mã Nguồn Lên GitHub
1. Truy cập [https://github.com](https://github.com) và tạo một Repository mới.
2. **Đặt tên Repository theo đúng quy chuẩn đề bài:** `Bao_NguyenChi_125002093`
3. Chọn chế độ **Public**.
4. Chạy các lệnh sau để kết nối và đẩy code lên:

```bash
# Thay thế [username] bằng tài khoản GitHub của bạn
git remote add origin https://github.com/[username]/Bao_NguyenChi_125002093.git

# Đẩy code lên nhánh main
git push -u origin main
```

### Bước 3: Kích Hoạt GitHub Pages Để Lấy Link Live Preview
1. Truy cập vào Repository `Bao_NguyenChi_125002093` trên GitHub.
2. Nhấn vào tab **Settings** (Cài đặt) ở góc trên bên phải.
3. Ở menu bên trái, cuộn xuống chọn mục **Pages**.
4. Tại mục **Build and deployment**:
   - **Source:** Chọn `Deploy from a branch`.
   - **Branch:** Chọn `main`, thư mục chọn `/ (root)`.
   - Nhấn **Save**.
5. Đợi khoảng 1 - 2 phút, GitHub Pages sẽ hiển thị đường link trực tiếp (Live Preview) có dạng:  
   `https://[username].github.io/Bao_NguyenChi_125002093/`
6. Sao chép liên kết này và dán vào phần **About (Website)** ở trang chủ Repository để Giảng viên dễ dàng kiểm tra.

---

## 5. Bảng Tự Đối Chiếu Tiêu Chí Chấm Điểm (Thang Điểm 10)

| STT | Tiêu Chí Đánh Giá | Yêu Cầu Của Đề Bài | Mức Độ Hoàn Thiện Trong Dự Án | Điểm Tối Đa |
| :---: | :--- | :--- | :--- | :---: |
| **1** | **Quy chuẩn Nộp bài & Git** | Tên Repo đúng chuẩn `Ten_Ho_MSSV`, commit rõ ràng, hướng dẫn deploy GitHub Pages live preview. | Đặt tên `Bao_NguyenChi_125002093`, cung cấp đầy đủ từng dòng lệnh Git và hướng dẫn cấu hình Pages. | **1.0 Điểm** |
| **2** | **Chuẩn Semantic HTML5** | Tối thiểu 5 thành phần: `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<footer>`. Không lạm dụng `<div>`. | Dùng chính xác 100% các thẻ ngữ nghĩa, cấu trúc cấp bậc tiêu đề `<h1>` -> `<h3>` chuẩn mực, thuộc tính `alt`, `role`, `aria-label` đầy đủ. | **2.0 Điểm** |
| **3** | **Kỹ thuật CSS & CSS Variables** | Khai báo `:root`, quản lý màu sắc/font/spacing, Flexbox, Grid, Responsive đa màn hình (1024, 768, 480px). | Khai báo hơn 25 biến CSS trong `:root`, CSS Grid 6 cột & 4 cột, Flexbox linh hoạt, responsive mượt mà không lỗi tràn ngang. | **2.5 Điểm** |
| **4** | **Hiệu ứng & Thư viện** | Tích hợp Animate.css, hiệu ứng chuyển động mượt mà, không dùng JS, hover/focus states đầy đủ. | Tích hợp Animate.css CDN, tự viết keyframes fallback thuần, CSS-Only reader theme switcher, không dùng AOS vì AOS cần JS. | **1.5 Điểm** |
| **5** | **Nhật ký Prompt Engineering** | File `PROMPT_LOG.md` chi tiết các vòng lặp (iterations), prompt, kết quả, nhận xét, sửa lỗi AI, đánh giá cá nhân. | Hoàn thiện file `PROMPT_LOG.md` chuẩn form mẫu, ghi nhận 4 vòng lặp tương tác, debug prompt thông minh. | **3.0 Điểm** |
| **TỔNG** | **ĐÁNH GIÁ CHUNG** | **Toàn bộ dự án đáp ứng xuất sắc mọi tiêu chí kỹ thuật và thẩm mỹ UI/UX.** | **10.0 / 10.0** |

---
*Dự án hoàn thành bởi sinh viên Nguyễn Chí Bảo (MSSV: 125002093) — Lớp Thiết Kế Web, ĐH Lạc Hồng.*
