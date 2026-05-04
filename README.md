# AppVeyor Persistent RDP Session (Antigravity) v4.1

Dự án này cung cấp cấu hình để thiết lập một môi trường Windows trên AppVeyor với khả năng truy cập RDP và **duy trì dữ liệu đăng nhập** (Cookies, Passwords, Sessions) xuyên suốt các phiên làm việc.

## Các tính năng chính (Nâng cấp v4.1)
- **Turbo Backup/Restore**: Thay thế module nén mặc định bằng **7-Zip** (`7z`), giúp giảm đáng kể thời gian nén/giải nén profile Chrome và dữ liệu, tăng tốc quá trình khởi tạo và lưu trữ.
- **Robust Error Handling**: Thêm Try-Catch để đảm bảo script không bị crash giữa chừng khi sao lưu hoặc khôi phục dữ liệu.
- **RDP Access**: Cho phép truy cập từ xa vào máy ảo Windows của AppVeyor.
- **Smart Auto-Backup**: Tự động sao lưu dữ liệu mỗi **5 phút** một lần vào Cache. Bạn không cần phải nhớ chạy file backup thủ công nữa.
- **File Lock Protection**: Sử dụng công nghệ `robocopy` để sao lưu ngay cả khi Chrome đang mở mà không gây lỗi.
- **DPAPI Persistence**: Khôi phục chính xác các khóa giải mã của Windows để giữ trạng thái đăng nhập tài khoản.

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