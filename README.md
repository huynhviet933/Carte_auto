# Carte_auto

# HƯỚNG DẪN SỬ DỤNG TOOL AUTO CARTE.GG (MANIFOLD)

Đây là công cụ tự động hóa quy trình Claim Credits, Mua Pack và Mở thẻ trên nền tảng Manifold (Carte.gg), hỗ trợ đa luồng qua Proxy và quản lý bản quyền theo HWID.

### 1. YÊU CẦU CÀI ĐẶT
Máy tính cần cài đặt sẵn **Node.js** (Phiên bản 16 trở lên).
Tải Node.js tại: https://nodejs.org/

Sau khi tải code về, mở Terminal (CMD/PowerShell) tại thư mục tool và chạy lệnh sau để cài đặt thư viện:
`npm install`

### 2. CẤU HÌNH CÁC FILE DỮ LIỆU
Bạn cần chuẩn bị các file .txt sau trong cùng thư mục với file `main.js`:

*   **token.txt**: Chứa danh sách Token tài khoản (mỗi dòng 1 token).
*   **proxy.txt**: Chứa danh sách Proxy (mỗi dòng 1 proxy). 
    *   Định dạng: `http://user:pass@ip:port` hoặc `socks5://ip:port` (Nếu không có user/pass thì chỉ cần `ip:port`).
*   **User_agents.txt**: Chứa danh sách User-Agent trình duyệt (mỗi dòng 1 UA). Nếu thiếu, tool sẽ tự dùng UA mặc định.
*   **license.txt**: File này sẽ tự sinh ra khi bạn nhập Key lần đầu, hoặc bạn có thể tạo sẵn và dán Key vào.

### 3. CƠ CHẾ HOẠT ĐỘNG
1.  **Xác thực License**: Khi khởi chạy, tool lấy mã định danh máy (HWID) và gửi lên server cùng với Key của bạn. Nếu Key hợp lệ và chưa dùng cho máy khác, tool sẽ bắt đầu chạy.
2.  **Kiểm tra Proxy**: Tool tự động kiểm tra proxy còn sống hay không trước khi làm việc với ví.
3.  **Quy trình Auto**:
    *   Đăng nhập bằng Token.
    *   Kiểm tra số dư Credits và Diamonds.
    *   Tự động Claim Credits (hồi năng lượng).
    *   Tự động mua Pack (Product ID: 3909690831) khi số dư >= 15 Credits.
    *   Tự động Mở Pack (Reveal) và Chọn thẻ (Select) để nhận vật phẩm.
4.  **Vòng lặp**: Sau khi chạy hết danh sách ví, tool sẽ nghỉ 5 phút để chờ hồi năng lượng rồi tiếp tục chu kỳ mới.

### 4. CÁCH CHẠY TOOL
Mở Terminal tại thư mục tool và gõ lệnh: Nhấn Start.bat 2 lần

### 5. LƯU Ý QUAN TRỌNG
*   **HWID Lock**: Một Key thường chỉ gắn chặt với 1 máy tính (HWID). Nếu bạn muốn đổi máy, hãy liên hệ Admin để reset Key.
*   **Proxy Whitelist**: Nếu bạn dùng Proxy dân cư (như Proxy247, Tinsoft...), hãy nhớ thêm IP mạng của bạn vào danh sách Whitelist trên trang web Proxy để Tool có thể kết nối được.
*   **File profiles.json**: Tool sẽ tự tạo file này để lưu trữ UUID riêng cho từng Token, giúp hạn chế bị hệ thống quét tài khoản ảo. Không nên xóa file này nếu muốn chạy ổn định lâu dài.
