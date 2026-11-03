# Bài 2: Sự cố phiên làm việc trên hệ thống vận tải

## Phần 1. Phân tích

So sánh sự đánh đổi giữa dung lượng Cache (MB/GB) và Cookies (~4KB) trong việc lưu trữ dữ liệu người dùng.

| Yếu tố | Cookies (~4KB) | Cache (MB - GB) |
|--------|----------------|-----------------|
| Dung lượng | Rất nhỏ. | Rất lớn (lưu cả ảnh, video, dữ liệu web). |
| Đường truyền mạng | Tự động gửi đi mọi lúc, gửi nhiều sẽ làm quá tải mạng. | Nằm yên trong máy, giúp web mở tức thì không tốn mạng. |
| Độ bảo mật | Rất an toàn cho tài khoản (có các bảo vệ như: HttpOnly và Secure). | Kém an toàn hơn, mã độc trên web có thể đọc được. |
| Kiểm soát | Web dễ dàng đổi hoặc xóa bất kỳ lúc nào. | Dễ bị tình trạng người dùng vẫn dữ liệu cũ mặc dù đã sửa lại trước đó. |

## Phần 2. Triển khai

Mô tả cấu trúc mẩu tin Cookie cần thiết (bao gồm Token, Max-Age, và các cờ bảo mật).

```
Set-Cookie: session_token=a8f9c2d1e4b7890123456789abcdef; Max-Age=604800; Path=/; Domain=example.com; Secure; HttpOnly; SameSite=Strict
```

## Phần 3. Kiểm thử

Nếu shipper thay đổi giao diện nhưng trình duyệt vẫn hiện màu cũ, hãy hướng dẫn thao tác Hard Reload để xóa Cache đệm.

Thao tác là: mở một tab ẩn danh (Incognito) rồi truy cập lại link. Vì trình duyệt ẩn danh không dùng phiên bản cũ đã lưu trong cache và luôn tải phiên bản mới nhất từ máy chủ về.
