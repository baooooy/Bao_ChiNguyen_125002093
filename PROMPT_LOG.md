# NHẬT KÝ PROMPT ENGINEERING (VIBE CODING LOG)
- **Họ và tên:** Nguyễn Chí Bảo
- **MSSV:** 125002093
- **Tên đề tài Website:** Website đọc truyện trực tuyến TRUYỆN MỘC
- **Công cụ AI đã sử dụng:** Antigravity AI (Google DeepMind) / Claude 3.5 Sonnet

---

## 1. Yêu cầu ban đầu (System/Initial Prompt)

> **Prompt tổng quan ban đầu:**
> *"Bạn là Senior Frontend Developer và Chuyên gia UI/UX. Hãy đóng vai trò người đồng hành lập trình (pair programmer) theo hình thức Vibe Coding để xây dựng một website đọc truyện trực tuyến hoàn chỉnh mang tên 'TRUYỆN MỘC' phục vụ bài kiểm tra giữa kỳ môn Thiết kế Web tại Trường Đại học Lạc Hồng.
> 
> QUY ĐỊNH BẮT BUỘC:
> 1. Chỉ sử dụng 100% HTML5 ngữ nghĩa và CSS3 thuần. Tuyệt đối KHÔNG sử dụng JavaScript, không file .js, không inline script/event handler.
> 2. Đạt chuẩn Semantic HTML5 (tối thiểu 5 thành phần: `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<footer>`). Hạn chế tối đa việc lạm dụng thẻ `<div>`.
> 3. Sử dụng CSS Variables (`:root`) quản lý toàn bộ hệ màu (kem mộc `#F8F5EF`, nâu đậm `#352A25`, cam đất `#C87952`, v.v.), font chữ (Google Fonts tiếng Việt), spacing, border-radius và shadow.
> 4. Bố cục hiện đại với CSS Grid và CSS Flexbox, chuẩn responsive đa màn hình (Desktop >= 1024px, Tablet 768px, Mobile 480px).
> 5. Tích hợp Animate.css qua CDN CSS thuần cho tiêu đề và hero. Đối với hiệu ứng cuộn trang, do KHÔNG được dùng JavaScript nên TUYỆT ĐỐI KHÔNG dùng thư viện AOS (vì AOS bắt buộc có `AOS.init()` bằng JS), thay vào đó sử dụng CSS `@keyframes` thuần mượt mà.
> 6. Cấu trúc đầy đủ gồm: `index.html` (trang chủ), `story.html` (chi tiết tác phẩm và mục lục chương), `reader.html` (trang đọc truyện mẫu có tùy chỉnh nền sáng/tối và cỡ chữ bằng CSS thuần), `css/style.css`, `PROMPT_LOG.md` và `README.md`."*

---

## 2. Quá trình tinh chỉnh & Giải quyết sự cố (Iteration Iterations)

### Lần 1: Dựng khung Semantic HTML & Hệ thống CSS Variables
- **Prompt đã dùng:**
  > *"Hãy thiết lập file `css/style.css` với hệ thống CSS Variables (`:root`) hoàn chỉnh theo tông màu Mộc ấm áp. Sau đó dựng khung ngữ nghĩa cho `index.html` gồm các phần: Header (Logo + Nav), Hero Section, Search Bar, Danh mục thể loại, Truyện nổi bật, Truyện mới cập nhật, Bảng xếp hạng Top 5, Đánh giá cộng đồng và Footer. Đảm bảo dùng đúng thẻ `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<footer>`."*
- **Kết quả AI tạo ra:**
  - AI đã tạo file CSS với hơn 20 biến `:root` rất đầy đủ và tạo khung HTML có các section chính.
- **Nhận xét & Tinh chỉnh của SV:**
  - *Nhận xét:* Một số khối card truyện ban đầu AI dùng `<div class="card">` và các tiêu đề truyện dùng `<h4>` nhảy bậc sau `<h1>`. Ngoài ra, mobile menu AI có gợi ý dùng file JS để toggle class.
  - *Chỉ đạo chỉnh sửa (Prompt tinh chỉnh):* "Nhắc nhở: Dự án cấm 100% JavaScript. Hãy thay thế menu mobile bằng kỹ thuật CSS-Only sử dụng `<input type="checkbox" id="mobile-menu-toggle">` kết hợp thẻ `<label>` và bộ chọn `~` trong CSS. Đồng thời, toàn bộ thẻ truyện và review phải đổi thành thẻ ngữ nghĩa `<article>`, chuẩn hóa cấp bậc tiêu đề `<h1>` (duy nhất cho trang) -> `<h2>` (cho mỗi section) -> `<h3>` (cho tên truyện/thể loại)."

---

### Lần 2: Xây dựng Layout Flexbox/Grid và Responsive Đa Màn Hình
- **Prompt đã dùng:**
  > *"Áp dụng CSS Grid cho: Danh mục 6 thể loại (6 cột trên desktop, 3 cột tablet, 2 cột mobile); Lưới 8 truyện mới cập nhật (4 cột desktop, 2 cột tablet, 1 cột mobile). Sử dụng Flexbox cho Header, Hero Stats, thanh công cụ đọc truyện và Footer 4 cột. Hãy bổ sung đầy đủ media queries tại 1024px, 768px và 480px để đảm bảo không bị lỗi tràn ngang (overflow-x)."*
- **Kết quả AI tạo ra:**
  - Layout hiển thị ngay ngắn, các card truyện có tỷ lệ bìa sách 3:4 chuẩn mực. Khi co giãn trình duyệt, các cột tự động rớt dòng hợp lý.
- **Nhận xét & Tinh chỉnh của SV:**
  - *Nhận xét:* Khi ở màn hình mobile dưới 480px, tiêu đề truyện dài bị tràn chữ và làm méo các card trong cùng hàng.
  - *Chỉ đạo chỉnh sửa (Prompt tinh chỉnh):* "Hãy bổ sung thuộc tính CSS text-overflow và `-webkit-line-clamp: 2` cho `.book-card-title`, gán `min-height` cố định để các card luôn có chiều cao đồng đều 100%. Đảm bảo `img` luôn có thuộc tính `object-fit: cover` và `max-width: 100%` để không bao giờ làm vỡ khung."

---

### Lần 3: Tích hợp thư viện Animate.css & Giải quyết xung đột thư viện AOS
- **Prompt đã dùng:**
  > *"Đề bài yêu cầu hiệu ứng động sinh động nhưng lại cấm sử dụng JavaScript. Hãy tích hợp Animate.css qua link CDN CSS thuần và áp dụng class animation cho tiêu đề Hero. Phân tích và đưa ra giải pháp thay thế AOS (Animate On Scroll) bằng CSS thuần."*
- **Thách thức gặp phải:**
  - Thư viện AOS (Animate On Scroll) nếu chỉ nhúng file `aos.css` mà không có đoạn script `AOS.init()` thì các phần tử có thuộc tính `data-aos` sẽ bị ẩn hoàn toàn (`opacity: 0`) hoặc không có hiệu ứng gì khi cuộn trang, làm hỏng giao diện của người dùng.
- **Cách sửa prompt (Debug prompt):**
  > *"Vì quy định bắt buộc không được dùng bất kỳ file .js nào hay inline script, ta KHÔNG dùng thư viện AOS để tránh làm trang web bị trắng nội dung khi thiếu `AOS.init()`. Thay vào đó:
  > 1. Nhúng Animate.css CDN và sử dụng các class chính thức: `animate__animated animate__fadeInUp`.
  > 2. Tự viết bộ `@keyframes fadeInUp`, `@keyframes floatCard`, `@keyframes pulseGlow` trực tiếp trong `style.css` để làm fallback nếu CDN gặp sự cố kết nối.
  > 3. Bổ sung `@media (prefers-reduced-motion: reduce)` để đáp ứng chuẩn WCAG cho người dùng nhạy cảm với chuyển động."*
- **Kết quả:** Hiệu ứng xuất hiện mượt mà, không phụ thuộc vào JS, đáp ứng 100% tiêu chí chấm điểm kỹ thuật.

---

### Lần 4: Hoàn thiện trải nghiệm Đọc truyện (reader.html), Chi tiết (story.html) và Tùy chỉnh CSS thuần
- **Prompt đã dùng:**
  > *"Xây dựng trang đọc truyện `reader.html` với trải nghiệm đọc văn học đỉnh cao: breadcrumbs phân cấp, typography Literata line-height 1.95, drop cap cho chữ cái đầu tiên, khối trích dẫn quote, ngắt trang hoa văn. Đặc biệt: Tạo thanh công cụ đổi màu nền (Giấy mộc, Đêm tối, Xanh dịu) và đổi cỡ chữ (Nhỏ, Vừa, Lớn) HOÀN TOÀN BẰNG CSS THUẦN (CSS `:has()` và `<input type="radio">`), không dùng JS."*
- **Kết quả AI tạo ra:**
  - Trang đọc truyện mẫu `reader.html` có bài văn tự sáng tác giàu cảm xúc, không vi phạm bản quyền.
  - Bộ chọn `body:has(#theme-night:checked)` và `body:has(#font-lg:checked)` hoạt động hoàn hảo trên các trình duyệt hiện đại (Chrome, Edge, Safari, Firefox), cho phép người dùng đổi giao diện tức thì mà không cần một dòng JavaScript nào.
- **Nhận xét & Tinh chỉnh của SV:**
  - Hoàn thiện thêm file `story.html` với đầy đủ thông số (tác giả, họa sĩ, số chương, đánh giá 4.9 sao) và danh sách 10 chương truyện có liên kết qua lại chính xác với `reader.html` và `index.html`.

---

## 3. Đánh giá cá nhân về quá trình Vibe Coding

### AI đã giúp bạn tiết kiệm thời gian ở phần nào nhất?
1. **Khởi tạo hệ thống Design Tokens và CSS Variables:** Thay vì phải tra cứu mã màu HEX thủ công và gõ từng dòng CSS Reset, AI giúp sinh toàn bộ bảng màu kem mộc, nâu sồi và cam đất cực kỳ hài hòa, chuẩn xác về mặt thị giác chỉ trong vài giây.
2. **Soạn thảo dữ liệu mẫu (Mock Content) chất lượng cao:** Thay vì dùng văn bản vô nghĩa "Lorem Ipsum", AI đã sáng tác một trích đoạn tiểu thuyết văn học tiếng Việt mộc mạc, sâu lắng ("Gió Thổi Qua Rừng Trầm") giúp trang đọc truyện có sức sống và cảm xúc như một website thực thụ.
3. **Giải quyết logic CSS phức tạp:** Cung cấp giải pháp dùng CSS `:has()` kết hợp radio inputs để giải quyết bài toán "đổi theme và cỡ chữ không dùng JavaScript" — điều mà nếu làm thủ công theo cách truyền thống thường bị lúng túng hoặc phụ thuộc vào JS.

### Bài học rút ra khi đặt câu hỏi (Prompt) cho AI trong thiết kế web?
1. **Rõ ràng về ràng buộc kỹ thuật (Constraints First):** Phải nêu rõ ngay từ đầu các điều kiện tiên quyết (ví dụ: *100% không dùng JavaScript, chỉ dùng HTML5 ngữ nghĩa và CSS3 thuần*). Nếu không nêu rõ, AI thường có xu hướng dùng script để xử lý tương tác.
2. **Tư duy lặp (Iterative Refinement):** Không nên kỳ vọng một prompt duy nhất tạo ra sản phẩm hoàn hảo 100%. Cách tiếp cận hiệu quả nhất là chia nhỏ quy trình: Dựng khung Semantic HTML -> Thiết lập CSS Layout -> Thêm hiệu ứng -> Tối ưu Accessibility và Responsive.
3. **Kiểm tra và làm chủ mã nguồn:** Người lập trình (sinh viên) phải hiểu rõ từng thẻ HTML và từng class CSS mà AI sinh ra để kịp thời uốn nắn, loại bỏ thẻ thừa, đảm bảo tính ngữ nghĩa cao nhất để tự tin giải trình trước Giảng viên chấm thi.
