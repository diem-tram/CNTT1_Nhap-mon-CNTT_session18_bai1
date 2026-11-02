# CNTT1_nhapmonCNTT_session18_bai1
Phần 1 
Input (Đầu vào): Tên miền URL mà người dùng nhập vào thanh địa chỉ của trình duyệt: phong-dieu-phoi.greenlog.vn.
Output (Đầu ra): Địa chỉ IP dạng số (IPv4 hoặc IPv6) của máy chủ chứa dịch vụ web
Sơ đồ luồng dữ liệu
Browser & OS Cache: Kiểm tra bộ nhớ tạm của trình duyệt và hệ điều hành xem đã lưu IP chưa.
DNS Resolver: Nếu chưa có, gửi truy vấn tới máy chủ phân giải của nhà mạng hoặc DNS công cộng (Google/Cloudflare).
Root Name Server (.): Chỉ đường tới máy chủ quản lý đuôi tên miền cấp cao (.vn).
TLD Name Server (.vn): Chỉ đường tới máy chủ quản lý tên miền chính (greenlog.vn).
Authoritative Name Server (greenlog.vn): Máy chủ thẩm quyền của doanh nghiệp cung cấp địa chỉ IP chính xác của subdomain (phong-dieu-phoi.greenlog.vn).
Trả kết quả & Kết nối: DNS Resolver trả IP về cho trình duyệt để thiết lập kết nối TCP tới máy chủ.
Phần 2
Tiêu chí	Lỗi DNS 	Lỗi HTTP 
Bản chất	Danh bạ DNS không tìm thấy bản ghi IP cho tên miền.	Máy chủ ứng dụng gặp sự cố nội bộ trong quá trình xử lý mã nguồn
Phía phát sinh	Phía Client / DNS: Yêu cầu chưa từng chạm tới máy chủ.	Phía Server: Yêu cầu đã chạm tới máy chủ thành công.
Nguyên nhân chính	- Gõ sai tên miền.
- Tên miền chưa đăng ký/hết hạn.
	- Lỗi code backend.
- Lỗi kết nối CSDL
- Tràn bộ nhớ (RAM/CPU) trên Server.
Phần 3
trạng thái: Tên miền đúng, yêu cầu đã gửi tới máy chủ thành công (không còn lỗi DNS hay mất mạng).
Bản chất lỗi 404 Not Found: Máy chủ hoạt động bình thường, nhưng không tìm thấy tệp hoặc trang web theo đường dẫn (URL) được yêu cầu.
Nguyên nhân chính:
Ghi thiếu đường dẫn con/endpoint (ví dụ: cần vào /login hoặc /dashboard nhưng chỉ gõ tên miền chính).
Máy chủ cấu hình sai thư mục gốc (Root Directory) hoặc thiếu quy tắc chuyển hướng (Rewrite rule).
Mã nguồn trang quản trị chưa được đưa (deploy) lên máy chủ.

