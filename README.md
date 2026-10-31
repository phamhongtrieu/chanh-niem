# Chánh Điện Online - TikTok Interactive Live Stream

Hệ thống mô phỏng không gian chánh điện tu tập tương tác thời gian thực dành cho TikTok Live. Dự án tự động phân tích bình luận, điều phối vị trí bồ đoàn và kích hoạt hiệu ứng dâng hoa sen, đọc tên hồi hướng khi có người xem tặng quà[cite: 2].

---

## Tính năng nổi bật

* **Tự động xếp chỗ bồ đoàn:** Tự mở rộng từ 24 đến 100 vị trí ngồi dựa theo lượng tương tác[cite: 2].
* **Tương tác lệnh chat:** Người xem bình luận từ khóa (`nam`, `nữ`, `sư`, `ni`, `bà`, `tiểu`, `cao tăng`) để tự đổi ngoại hình nhân vật tương ứng[cite: 1, 2].
* **Cúng dường & Hồi hướng:** Khi nhận quà donate, nhân vật tự động bước lên dâng hoa và bảng "Công Đức" cập nhật điểm số theo thời gian thực[cite: 1, 2].
* **Giọng đọc AI (TTS):** Tự động phát âm thanh chuông mõ và đọc xướng tên người cúng dường bằng giọng đọc tiếng Việt[cite: 2].
* **Bảng điều khiển cục bộ (Control Panel):** Trang web quản trị riêng để kiểm tra hiệu ứng, đổ bot thử nghiệm hoặc làm trống phòng thiền.

---

## Cấu trúc thư mục

```text
chanh-dien-online/
├── assets/          # Hình ảnh background, sprite nhân vật, âm thanh chuông mõ
├── tts/             # Module xử lý chuyển văn bản thành giọng nói (Text-to-Speech)
├── control.html     # Giao diện quản trị, tạo bot và test sự kiện
├── overlay.html     # Giao diện chính hiển thị lên OBS / TikTok Live Studio
├── server.mjs       # Server Node.js kết nối luồng TikTok Live và WebSocket
└── package.json     # Khai báo thư viện và scripts khởi chạy
```

---

## Hướng dẫn cài đặt & Khởi chạy

### 1. Yêu cầu hệ thống
* [Node.js](https://nodejs.org/) (phiên bản 18 trở lên).
* Phần mềm phát stream: **OBS Studio** hoặc **TikTok Live Studio**.

### 2. Cài đặt các gói phụ thuộc
Mở terminal tại thư mục dự án và chạy lệnh:
```bash
npm install
```

### 3. Cấu hình tài khoản TikTok
* Mở file cấu hình kết nối (hoặc file `server.mjs`).
* Điền `username` của kênh TikTok đang phát live (không cần mật khẩu, chỉ cần tên ID kênh).

### 4. Khởi động máy chủ
```bash
npm run start
```
Server cục bộ sẽ chạy tại:
* Màn hình livestream: `http://localhost:3000/overlay.html`
* Bảng điều khiển admin: `http://localhost:3000/control.html`

---

## Cấu hình đưa lên OBS Studio

1. Mở **OBS Studio**, tạo một Scene mới.
2. Thêm nguồn **Browser** (Trình duyệt).
3. Đặt thông số nguồn:
   * **URL:** `http://localhost:3000/overlay.html`
   * **Width (Chiều rộng):** `1080`
   * **Height (Chiều cao):** `1920` (chuẩn tỉ lệ dọc 9:16 của TikTok)
4. Tích chọn **Control audio via OBS** nếu muốn quản lý âm thanh trực tiếp trên OBS.

---

## Giấy phép & Lời cảm ơn

* Phát triển và tùy biến bởi **Pham Hong Trieu**.
* Mã nguồn được phát hành dưới giấy phép mã nguồn mở [MIT License](LICENSE)[cite: 2, 4].
* Dự án được xây dựng và tối ưu hóa dựa trên nền tảng ban đầu của [Kent Juno](https://github.com/kentjuno/chanh-dien-online)[cite: 2].