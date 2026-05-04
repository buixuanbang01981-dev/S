# AppVeyor Persistent RDP Session (Antigravity) v6.0 (Pro Edition)

Dự án này cung cấp cấu hình để thiết lập một môi trường Windows trên AppVeyor với khả năng truy cập RDP và **duy trì dữ liệu đăng nhập** (Cookies, Passwords, Sessions) xuyên suốt các phiên làm việc.

## Các tính năng "Xịn Xò" Mới (Nâng cấp v6.0)
- **Tích hợp AppVeyor Artifacts**: Dữ liệu sao lưu cuối cùng (trước khi máy ảo tắt do hết giờ hoặc lỗi) sẽ tự động được tải lên tab **Artifacts** trên web AppVeyor. Bạn có thể dễ dàng tải thủ công về máy tính cá nhân để cất giữ cực kỳ an toàn!
- **Tích hợp AppVeyor Messages**: IP, mật khẩu RDP và Link Ngrok được đẩy thẳng ra tab **Messages** của AppVeyor giúp bạn sao chép cực kỳ nhanh và trực quan.
- **Hỗ Trợ Ngrok Tunnel**: Nếu cổng RDP bị chặn, bạn có thể nhập `NGROK_AUTH_TOKEN` vào `appveyor.yml` để tự động tạo một đường truyền ngrok, hiển thị URL truy cập trực tiếp cực nhanh.
- **Tối Ưu Hóa Sức Mạnh Máy Ảo (Performance Booster)**: Tự động vô hiệu hóa Windows Defender (Antivirus) và Windows Search. Giúp lấy lại 100% sức mạnh CPU và tốc độ đọc/ghi ổ cứng cho công việc của bạn.
- **Hệ Thống Chống Ngủ Đông (Anti-AFK)**: Máy ảo có thể duy trì hoạt động liên tục (tùy gói giới hạn của AppVeyor, ví dụ 60 hoặc 360 phút). Script tự động gửi phím êm (F15) để chống lock màn hình.
- **Shortcut Tự Động**: Tạo sẵn biểu tượng ứng dụng Antigravity ngoài màn hình Desktop để bạn chỉ cần click là chạy, không phải đi tìm file nữa.
- **Turbo Backup/Restore**: Thay thế module nén mặc định bằng **7-Zip** (`7z`), giúp giảm đáng kể thời gian nén/giải nén profile Chrome và dữ liệu, tăng tốc quá trình khởi tạo và lưu trữ.

## Hướng dẫn sử dụng
1. **Khởi chạy**: Đẩy code lên GitHub hoặc kích hoạt build trên AppVeyor.
2. **Kết nối**: Sử dụng thông tin RDP trong log của AppVeyor (Mật khẩu mặc định: `HieuDz@123456`).
3. **Làm việc**: Bạn cứ mở Chrome, đăng nhập tài khoản và làm việc bình thường.
4. **Tự động lưu**: Hệ thống sẽ tự động đóng gói và đẩy dữ liệu vào Cache mỗi 5 phút. Khi kết thúc build, AppVeyor sẽ lưu lại bản backup cuối cùng.
5. **Khôi phục**: Ở lần chạy tiếp theo, toàn bộ session của bạn sẽ xuất hiện trở lại như chưa từng rời đi.

## Lưu ý về Bảo mật
- Mật khẩu RDP có thể thay đổi trong phần `environment` của file `appveyor.yml`.
- Tránh để lộ mã nguồn nếu bạn lưu các thông tin nhạy cảm bên trong máy ảo.

---
*Dự án được tối ưu hóa bởi Antigravity AI.*