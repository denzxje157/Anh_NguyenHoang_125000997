# NHẬT KÝ PROMPT ENGINEERING (VIBE CODING LOG)

- **Họ và tên:** Nguyễn Hoàng Anh
- **MSSV:** 125000997
- **Tên Repository:** `Anh_NguyenHoang_125000997`
- **Tên đề tài Website:** Chiều sâu Văn hóa & Di sản Đồng Nai
- **Công cụ AI đã sử dụng:** Gemini 3.8 Flash, Google Antigravity

---

## 1. Yêu cầu ban đầu (System / Initial Prompt)

> *"Hãy đóng vai một Senior Frontend Developer và Chuyên gia UI/UX hàng đầu. Hãy cùng tôi xây dựng một Landing Page chủ đề **'Chiều sâu Văn hóa & Di sản Đồng Nai'** phục vụ bài thi Giữa kỳ môn Thiết kế Web tại Đại học Lạc Hồng. Trang web cần tôn vinh các biểu tượng đặc sắc như Văn Miếu Trấn Biên, Căn cứ Chiến khu Đ, Làng gốm Biên Hòa 300 năm tuổi và Vườn Quốc gia Cát Tiên.*
>
> *Ràng buộc kỹ thuật tối thượng:*
> 1. *Tuân thủ 100% chuẩn Semantic HTML5: Bắt buộc sử dụng đúng ngữ nghĩa các thẻ `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<figure>`, `<figcaption>`, `<footer>`. TUYỆT ĐỐI KHÔNG lạm dụng thẻ `<div>` vô nghĩa ở các khối kiến trúc chính.*
> 2. *CSS hiện đại & Design Tokens trong `:root`: Khai báo hệ thống biến CSS đồng bộ cho màu sắc mang âm hưởng di sản (`--primary-color`, `--secondary-color`, `--accent-color`), font chữ (`--font-heading`, `--font-body`), khoảng cách (`--spacing-*`), đổ bóng và hiệu ứng chuyển cảnh (`--transition-*`). Dựng layout bằng CSS Flexbox và CSS Grid chuẩn responsive.*
> 3. *Tương tác & Thư viện: Nhúng CDN của **Animate.css** (hiệu ứng tiêu đề, Hero, CTA) và **AOS (Animate On Scroll)** cho các section cuộn trang; tự viết hiệu ứng `:hover`, `:focus-visible` bằng CSS thuần cho buttons và cards.*
> 4. *Khởi tạo song song mã nguồn và tài liệu `PROMPT_LOG.md` theo thang điểm chấm 10/10."*

---

## 2. Quá trình tinh chỉnh & Giải quyết sự cố (Iterations)

### Lần 1: Dựng khung Semantic HTML & Thiết lập CSS Variables

- **Prompt đã dùng:**
  > *"Khởi tạo cấu trúc `index.html` và file `style.css` với bảng mã thiết kế (Design Tokens) hoàn chỉnh trong `:root`. Đảm bảo trang web chia rõ 6 section chính: Hero Section, Đôi nét đất Phương Nam, Di tích lịch sử trọng điểm, Làng nghề & Lễ hội, Kỳ quan Cát Tiên, và Form kết nối cẩm nang di sản. Mỗi thẻ card di tích phải là một `<article>` độc lập chứa `<figure>`, `<header>`, nội dung và `<footer>` riêng biệt, không dùng `div` bừa bãi."*

- **Kết quả AI tạo ra:**
  - AI đã sinh ra bộ khung HTML5 khá hoàn chỉnh với cấu trúc `<header>`, `<nav>`, `<main>`, `<section>` và `<footer>`.
  - Trong `style.css`, AI tạo được các biến màu sắc cơ bản: `--primary-color: #9E2A2B` (đỏ son di sản), `--secondary-color: #C68642` (vàng hoàng kim Trấn Biên), cùng các biến font chữ `Playfair Display` kết hợp `Be Vietnam Pro`.
  - Tuy nhiên, trong các thẻ bài viết (`cards`), AI vẫn có xu hướng quen tay bọc các khối ảnh và nhãn phân loại bằng `<div class="card-image">` và `<div class="badge">`.

- **Nhận xét & Tinh chỉnh của SV (Code Review & Direction):**
  - **Phát hiện điểm chưa tối ưu:** Việc AI lạm dụng `<div>` trong card làm giảm điểm Semantic HTML5 (tiêu chí 2.0 điểm). Hơn nữa, hệ thống biến CSS trong `:root` còn thiếu các biến định lượng khoảng cách (`--spacing`), bo góc (`--radius`), và biến màu nhấn men xanh gốm cổ Biên Hòa.
  - **Lệnh tinh chỉnh đưa cho AI:**
    1. Yêu cầu AI thay toàn bộ `<div class="card-image">` thành `<figure class="card-media">` kết hợp thẻ con `<figcaption class="card-category">` để đúng chuẩn mô tả tư liệu hình ảnh di sản trong HTML5.
    2. Yêu cầu bổ sung thêm biến `--accent-color: #2F5D62` (màu men xanh đồng gốm Biên Hòa) và hoàn thiện hệ thống Spacing Tokens từ `--spacing-xs` (4px) đến `--spacing-3xl` (96px).
    3. Bổ sung các trạng thái `:focus-visible` với `outline` rõ ràng cho các nút bấm và liên kết điều hướng để đáp ứng tiêu chuẩn Accessibility (A11y) của UX hiện đại.

---

### Lần 2: Tích hợp thư viện Animate.css & AOS (Animate On Scroll)

- **Prompt đã dùng:**
  > *"Tích hợp thư viện Animate.css vào phần Hero (tiêu đề, phụ đề, nút CTA) và thư viện AOS (Animate On Scroll) vào các `<section>` và danh sách thẻ di tích. Đồng thời, tự viết hiệu ứng CSS `:hover` nâng thẻ (`transform: translateY(-8px)` kèm tăng độ sâu `box-shadow`) cho các thẻ bài viết `<article class="heritage-card">`."*

- **Thách thức gặp phải (Technical Conflicts):**
  Khi chạy thử nghiệm giao diện trên trình duyệt, tôi đã phát hiện **2 lỗi kỹ thuật kinh điển** thường gặp khi kết hợp CSS tự viết với thư viện bên thứ 3:
  1. **Xung đột thuộc tính `transform` giữa AOS và CSS `:hover`:**
     - Thư viện AOS điều khiển hiệu ứng xuất hiện cuộn trang bằng cách can thiệp vào thuộc tính `transform: translate3d(...)` và gán thuộc tính inline/class `.aos-animate`.
     - Khi tôi viết thêm hiệu ứng CSS `:hover { transform: translateY(-8px); }` trực tiếp lên thẻ `<article class="heritage-card" data-aos="fade-up">`, hai thuộc tính `transform` này ghi đè lẫn nhau, khiến thẻ bài viết bị giật khung hình (flickering) hoặc mất hoàn toàn hiệu ứng bay lên khi hover chuột sau khi cuộn trang.
  2. **Lỗi phát sinh thanh cuộn ngang ngoài ý muốn (`overflow-x` bug):**
     - Ở các section sử dụng hiệu ứng `data-aos="fade-left"` và `data-aos="fade-right"` (như khu vực Giới thiệu Làng nghề gốm), các phần tử ban đầu bị dịch chuyển sang hai bên ngoài khung nhìn màn hình trước khi cuộn tới, làm xuất hiện thanh cuộn ngang khó chịu trên các màn hình laptop và thiết bị di động.

- **Cách sửa prompt (Debug Prompt & Kiến trúc tách lớp):**
  > *"AI hãy thực hiện refactor kiến trúc thẻ và tinh chỉnh CSS để giải quyết triệt để 2 lỗi xung đột trên:*
  > 1. *Về xung đột transform: Áp dụng kỹ thuật **'Tách lớp phần tử' (Layer Decoupling)**. Bọc ngoài mỗi thẻ `<article>` một lớp container `<div class="card-wrapper" data-aos="fade-up">` để thư viện AOS chỉ tác động hiệu ứng cuộn lên wrapper này. Còn hiệu ứng `:hover { transform: translateY(-8px); box-shadow: var(--shadow-hover); }` và `transition` sẽ được đặt riêng biệt hoàn toàn cho thẻ `<article class="heritage-card">` bên trong. Bằng cách này, AOS và hiệu ứng hover hoạt động trên hai phần tử DOM độc lập, triệt tiêu 100% hiện tượng xung đột.*
  > 2. *Về lỗi tràn ngang overflow-x: Bổ sung thuộc tính `overflow-x: hidden;` cho cả thẻ `html` và `body` trong `style.css`. Đồng thời trong hàm `AOS.init()`, thiết lập các tham số `{ duration: 800, offset: 80, once: true, easing: 'ease-out-cubic' }` để hiệu ứng cuộn chỉ kích hoạt 1 lần mượt mà và không đẩy lề viewport."*

- **Kết quả sau sửa lỗi:**
  Hiệu ứng chuyển động chạy cực kỳ trơn tru, cuộn trang mượt mà không hề có vệt giật, hiệu ứng hover card nâng nhẹ 8px sang trọng và không còn bất kỳ thanh cuộn ngang nào xuất hiện.

---

## 3. Đánh giá cá nhân về quá trình Vibe Coding

### 1. AI đã giúp bạn tiết kiệm thời gian ở phần nào nhất?
- **Tiết kiệm vượt bậc khâu khởi tạo Boilerplate & Copywriting chuyên sâu:** Thông thường, việc tự gõ toàn bộ khung sườn Semantic HTML5 chuẩn chỉ, thiết lập bảng Design Tokens 20+ biến CSS và tra cứu tư liệu lịch sử chi tiết (về năm thành lập Văn Miếu Trấn Biên 1715, Chiến khu Đ 1946, Làng gốm Biên Hòa 1903, diện tích VQG Cát Tiên 71.187 ha) sẽ mất từ 60 – 75 phút. AI đã hỗ trợ tổng hợp nội dung giàu ý nghĩa văn hóa và sinh mã nguồn ban đầu chỉ trong chưa đầy 2 phút.
- **Tính toán Grid/Flexbox và mã màu chuẩn xác:** AI tính toán rất nhanh các thông số lưới `grid-template-columns: repeat(auto-fit, minmax(320px, 1fr))` và phối màu di sản hài hòa giữa đỏ son, vàng đồng và xanh ngọc gốm cổ, giúp tôi tập trung toàn bộ thời gian vào việc kiểm tra chất lượng code và trải nghiệm người dùng.

### 2. Bài học rút ra khi đặt câu hỏi (Prompt) cho AI trong thiết kế web?
1. **Phải thiết lập Ràng buộc Kỹ thuật (Technical Constraints) ngay từ System Prompt:** Nếu chỉ yêu cầu AI *"Hãy tạo website giới thiệu Đồng Nai"*, AI sẽ sinh ra mã nguồn chung chung, lạm dụng thẻ `<div>` vô tội vạ ("div soup") và dùng màu sắc tùy tiện. Việc ép chặt vai trò Senior Developer cùng các tiêu chí Semantic HTML5 và CSS Variables ngay từ đầu là chìa khóa để nhận được mã nguồn chuẩn chỉnh.
2. **Kỹ năng "Debug Prompt" quan trọng hơn "Prompt sinh code":** AI có thể viết code rất nhanh nhưng thường bỏ qua sự xung đột giữa các thư viện bên thứ 3 (như xung đột `transform` giữa AOS và CSS `:hover`). Người lập trình viên phải nắm vững bản chất CSS Box Model và Render Tree để phát hiện lỗi và đưa ra prompt điều hướng cấu trúc (như giải pháp tách lớp Layer Decoupling).
3. **Sinh viên phải là "Kiến trúc sư trưởng" (Architect & Reviewer):** Trong phương thức Vibe Coding, AI đóng vai trò như một trợ lý lập trình viên tốc độ cao, nhưng con người bắt buộc phải giữ vai trò thẩm định, định hướng thẩm mỹ UI/UX và bảo đảm mã nguồn tuân thủ đúng yêu cầu học thuật của đề thi.

---
*Biên Hòa, ngày 20 tháng 10 năm 2026*  
**Người lập nhật ký:** Nguyễn Hoàng Anh (MSSV: 125000997)
