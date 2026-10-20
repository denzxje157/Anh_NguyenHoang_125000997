# BẢNG THEO DÕI NGUỒN GỐC & BẢN QUYỀN HÌNH ẢNH (IMAGES.md)

**Dự án:** Hào Khí Trấn Biên - Chiều Sâu Văn Hóa & Di Sản Đất Đồng Nai  
**Sinh viên:** Nguyễn Hoàng Anh - MSSV: 125000997  
**Trạng thái cập nhật:** 100% hình ảnh thực địa và tư liệu lịch sử Đồng Nai đã được tích hợp đầy đủ vào mã nguồn.

---

## 1. Bảng Chi Tiết 11 Vị Trí Ảnh Trong Dự Án

| STT | Vị trí trên giao diện | Tên file hình ảnh | Trạng thái hiện tại | Nội dung ảnh thực tế | Tác giả & Nguồn gốc tư liệu |
|:---:|:---|:---|:---:|:---|:---|
| 1 | **Hero Section** (Trang bìa đầu trang) | `hero-bg.webp` | **ĐÃ CÓ (100%)** | Toàn cảnh khúc quanh sông Đồng Nai và TP. Biên Hòa nhìn từ trên cao | Flycam tư liệu Đồng Nai / Tác giả địa phương |
| 2 | **Khởi nguồn 1698** (Section Giới thiệu) | `hinh-2.webp` | **ĐÃ CÓ (100%)** | Bức ảnh tư liệu lịch sử dòng sông Đồng Nai thuở mở cõi phương Nam | Lưu trữ tư liệu lịch sử Nam Bộ |
| 3 | **Thẻ Di tích 1** (Văn Miếu Trấn Biên) | `anh_van_mieu.jpg` | **ĐÃ CÓ (100%)** | Toàn cảnh khuôn viên Văn Miếu Trấn Biên soi bóng rợp bóng cây cổ thụ | Bùi Thụy Đào Nguyên / Wikimedia Commons |
| 4 | **Thẻ Di tích 2** (Chùa Ông Cù Lao Phố) | `anh_chanh_dien_cu_lao_pho.jpg` | **ĐÃ CÓ (100%)** | Chánh điện Thất Phủ Cổ Miếu lung linh ánh hoa đăng và đèn lồng đỏ đêm hội | Tư liệu Ban trị sự Thất Phủ Cổ Miếu |
| 5 | **Thẻ Di tích 3** (Căn cứ Chiến khu Đ) | `chien-khu-d-1000x672.jpg` | **ĐÃ CÓ (100%)** | Căn cứ địa Chiến khu Đ với nhà lợp lá trung quân huyền thoại | Bảo tàng Đồng Nai / Di tích Chiến khu Đ |
| 6 | **Thẻ Di tích 4** (Danh thắng Bửu Long) | `Danh-thang-Buu-Long-01.jpg` | **ĐÃ CÓ (100%)** | Vách đá dựng đứng kỳ vĩ và mặt hồ Long Ẩn trong xanh | Khu du lịch Bửu Long / Cổng TTĐT Đồng Nai |
| 7 | **Thẻ Di tích 5** (Cầu Ghềnh Lịch Sử) | `Ky-uc-cau-Ghenh-cay-cau-112-tuoi-ivivu-1.jpg` | **ĐÃ CÓ (100%)** | Nhịp vòm thép cầu Ghềnh 112 tuổi lịch sử bắc qua sông Đồng Nai | Tư liệu iVIVU / Ký ức cầu Ghềnh Biên Hòa |
| 8 | **Thẻ Di tích 6** (Hồ Trị An & Rừng Mã Đà) | `go-and-share-hoang-hon-ho-tri-an-7.webp` | **ĐÃ CÓ (100%)** | Ánh hoàng hôn rực rỡ tráng lệ trải dài trên mặt hồ thủy điện Trị An | Go & Share / Nhiếp ảnh gia du lịch Đồng Nai |
| 9 | **Thẻ Làng nghề 1** (Gốm Biên Hòa / Tân Vạn) | `lang-gom-Bien-Hoa-9.jpg` | **ĐÃ CÓ (100%)** | Các sản phẩm chậu gốm men xanh đồng trổ hoa kim truyền thống | Làng gốm cổ Tân Vạn - Biên Hòa |
| 10 | **Thẻ Làng nghề 2** (Lễ hội Nghinh Thần) | `thuyen-ruoc.webp` | **ĐÃ CÓ (100%)** | Đoàn thuyền rước Nghinh Thần rực rỡ cờ hoa trên dòng sông Đồng Nai | Lễ hội Chùa Ông / Báo Đồng Nai |
| 11 | **Kỳ quan Cát Tiên** (Khu Ramsar Bàu Sấu) | `cat_tien.png` | **ĐÃ CÓ (100%)** | Toàn cảnh rừng mưa nhiệt đới nguyên sinh và Bàu Sấu từ trên cao | VQG Cát Tiên / UNESCO Biosphere Reserve |

---

## 2. Tiêu Chuẩn Kỹ Thuật Khi Hiển Thị Trên Giao Diện

- **Không méo / không bẹp ảnh:** Tất cả thẻ `<img>` đều được CSS thiết lập `aspect-ratio: 16/10;` và `object-fit: cover;`. Dù xem trên iPhone màn hình đứng 375px hay màn hình Desktop 1440px, bố cục ảnh luôn giữ đúng tỉ lệ vàng.
- **Tối ưu tốc độ tải trang:** Thẻ `<img>` tích hợp thuộc tính `loading="lazy"` (cho các ảnh dưới màn cuộn), khai báo sẵn `width="800"` và `height="500"` để trình duyệt tính toán Layout Shift (CLS = 0).
- **Hiệu ứng thị giác đỉnh cao:** Khi rê chuột (`:hover`) hoặc chạm trên di động, ảnh tự động phóng to nhẹ nhàng `scale(1.08)` với đường cong chuyển động `cubic-bezier(0.16, 1, 0.3, 1)` mang lại cảm giác chân thực, sống động.
