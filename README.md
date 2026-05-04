# AppVeyor Persistent RDP Session (Antigravity) v7.0 — Maximum Edition

Dự án này cung cấp cấu hình để thiết lập một môi trường Windows trên AppVeyor với khả năng truy cập RDP và **duy trì dữ liệu đăng nhập** (Cookies, Passwords, Sessions) xuyên suốt các phiên làm việc.

## Tính năng v7.0 — Maximum Edition

### 🖥️ System Dashboard
- Khi khởi tạo, hệ thống tự động hiển thị thông tin chi tiết về máy ảo: **CPU, RAM, Disk, Hostname** ngay trên console và tab Messages. Giúp bạn biết chính xác mình đang dùng máy cấu hình gì.

### ⚡ Deep Performance Booster
- Tắt **Windows Defender Realtime** (4 module bảo vệ).
- Tắt **5 dịch vụ hệ thống** ngốn tài nguyên: Windows Search, Diagnostics Tracking, Superfetch, Error Reporting, Maps Broker.
- Chuyển **Power Plan** sang **High Performance** để CPU luôn chạy ở tốc độ tối đa.
- Tắt **hiệu ứng đồ họa** Windows (Visual Effects → Best Performance) để tiết kiệm RAM.

### 📦 Smart Backup Engine (7z + Exclude Junk)
- Sử dụng **7-Zip** với flag `-mx=1 -mmt=on` (nén nhanh nhất + đa luồng).
- Chuyển định dạng sang `.7z` để tiết kiệm dung lượng cache.
- **Loại trừ thư mục rác** khỏi Chrome Profile: `Service Worker`, `Code Cache`, `GPUCache`, `ShaderCache` — giảm 30-50% kích thước backup.
- Backup **mỗi 2 phút** thay vì mỗi phút để giảm tải CPU, nhưng vẫn đủ an toàn.
- Backup cả **Desktop** (shortcuts, file cá nhân) để khôi phục nguyên trạng.

### 📊 Live Build Monitoring
- Hiển thị **kích thước backup** và **thời gian trung bình** mỗi 10 phút.
- Cập nhật **version string** trên giao diện AppVeyor theo thời gian thực (ví dụ: `7.0.42 [Phút 30 | Backup #15]`).
- Hiển thị **RAM Free** mỗi 5 phút để theo dõi sức khỏe máy ảo.

### 🛡️ Triple Safety Net (on_success / on_failure / on_finish)
- `on_success`: Thông báo session kết thúc thành công.
- `on_failure`: **Emergency Backup** — nếu build bị crash hoặc timeout, hệ thống sẽ cố gắng cứu vớt dữ liệu Chrome và Registry ngay lập tức.
- `on_finish`: **Luôn luôn** đẩy toàn bộ dữ liệu lên tab **Artifacts** kèm timestamp, dù build thành công hay thất bại.

### 🌐 Ngrok Tunnel (tùy chọn)
- Nhập `NGROK_AUTH_TOKEN` để tự động tạo đường hầm RDP qua mạng Internet.

### 🔧 Các cải tiến khác
- `shallow_clone: true` + `clone_depth: 1`: Tăng tốc khởi tạo build.
- `max_jobs: 1`: Chống xung đột cache khi chạy nhiều build.
- `matrix.fast_finish: true`: Dừng ngay nếu có lỗi nghiêm trọng.
- Tạo **Shortcut Desktop** cho cả Chrome và Antigravity.
- Dọn dẹp file installer sau khi cài xong.
- Log khôi phục chi tiết với thời gian và kích thước file.

## Hướng dẫn sử dụng
1. **Khởi chạy**: Đẩy code lên GitHub hoặc kích hoạt build trên AppVeyor.
2. **Kết nối**: Sử dụng thông tin RDP trong log của AppVeyor (Mật khẩu mặc định: `HieuDz@123456`).
3. **Làm việc**: Bạn cứ mở Chrome, đăng nhập tài khoản và làm việc bình thường.
4. **Tự động lưu**: Hệ thống sẽ tự động đóng gói và đẩy dữ liệu vào Cache mỗi 2 phút. Khi kết thúc build, AppVeyor sẽ lưu lại bản backup cuối cùng lên Artifacts.
5. **Khôi phục**: Ở lần chạy tiếp theo, toàn bộ session của bạn sẽ xuất hiện trở lại như chưa từng rời đi.

## Lưu ý về Bảo mật
- Mật khẩu RDP có thể thay đổi trong phần `environment` của file `appveyor.yml`.
- Nên sử dụng tính năng **Encrypt YAML** của AppVeyor để mã hóa mật khẩu (vào Settings → Encrypt YAML trên web AppVeyor).
- Tránh để lộ mã nguồn nếu bạn lưu các thông tin nhạy cảm bên trong máy ảo.

---
*Dự án được tối ưu hóa bởi Antigravity AI — v7.0 Maximum Edition.*