# AppVeyor Persistent RDP Session (Antigravity)

Dự án này cung cấp cấu hình để thiết lập một môi trường Windows trên AppVeyor với khả năng truy cập RDP và **duy trì dữ liệu đăng nhập** (Cookies, Passwords, Sessions) xuyên suốt các phiên làm việc.

## Các tính năng chính
- **RDP Access**: Cho phép truy cập từ xa vào máy ảo Windows của AppVeyor.
- **Chrome Persistence**: Tự động sao lưu và khôi phục Profile Chrome, bao gồm cả các khóa giải mã DPAPI giúp giữ trạng thái đăng nhập.
- **App Persistence**: Hỗ trợ lưu trữ cấu hình của ứng dụng Antigravity.
- **Quick Backup**: Script trên Desktop giúp sao lưu dữ liệu tức thì trước khi kết thúc phiên.

## Hướng dẫn sử dụng
1. **Khởi chạy**: Đẩy code lên GitHub hoặc kích hoạt build trên AppVeyor.
2. **Kết nối**: Sử dụng địa chỉ IP và mật khẩu (mặc định: `HieuDz@123456`) được cung cấp trong log của AppVeyor để kết nối RDP.
3. **Lưu dữ liệu**: 
   - Sau khi đăng nhập tài khoản trên Chrome hoặc sử dụng App.
   - Trước khi tắt RDP, hãy chạy file **LUU_DU_LIEU.ps1** trên Desktop.
   - Script này sẽ nén dữ liệu và đưa vào Cache của AppVeyor.
4. **Khôi phục**: Ở lần chạy tiếp theo, hệ thống sẽ tự động giải nén và khôi phục lại trạng thái cũ.

## Cấu trúc file
- `appveyor.yml`: File cấu hình chính chứa logic cài đặt và sao lưu.
- `LUU_DU_LIEU.ps1` (Sinh ra khi chạy): Script hỗ trợ người dùng sao lưu thủ công.

---
*Lưu ý: Mật khẩu RDP có thể thay đổi trong phần `environment` của file `appveyor.yml`.*