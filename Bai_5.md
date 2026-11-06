
# Bài 5: Xây dựng cơ chế xác thực an toàn cho Crypto Wallet

## 1. Thiết kế kiến trúc xác thực MFA

Sử dụng 3 lớp bảo vệ để tăng độ an toàn cho ví tiền điện tử:

- **Lớp 1 – Mật khẩu:** Người dùng nhập mật khẩu để đăng nhập.
- **Lớp 2 – TOTP:** Nhập mã OTP gồm 6 chữ số được tạo từ ứng dụng Google Authenticator.
- **Lớp 3 – Sinh trắc học:** Xác nhận bằng vân tay hoặc Face ID trên thiết bị.

## 2. Sơ đồ luồng dữ liệu

```text
       NGƯỜI DÙNG
            |
            v
     Nhập mật khẩu
            |
            v
     Kiểm tra mật khẩu
            |
            v
       Nhập mã TOTP
            |
            v
      Kiểm tra mã OTP
            |
            v
    Xác nhận vân tay/Face ID
            |
            v
       ĐĂNG NHẬP THÀNH CÔNG
            |
            v
       SỬ DỤNG CRYPTO WALLET
```

Nếu Hacker biết mật khẩu nhưng không có mã TOTP và thiết bị xác thực sinh trắc học thì vẫn khó đăng nhập vào tài khoản.

## 3. Xử lý tình huống không có Internet

- Người dùng vẫn có thể mở Google Authenticator để lấy mã OTP.
- TOTP hoạt động dựa trên khóa bí mật và thời gian trên thiết bị, không cần Internet hoặc sóng điện thoại.
- Mã OTP thường có hiệu lực khoảng 30 giây.
- Cần cài đặt và đồng bộ thời gian trên điện thoại chính xác.

**Lưu ý:** Không có Internet vẫn lấy được mã OTP, nhưng muốn thực hiện giao dịch trực tuyến thì thiết bị cần kết nối mạng khi hệ thống yêu cầu.
