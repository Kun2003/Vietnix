**WinServer và Firewall trên WinServer**

1. **Winserver là gì?**

   Windows Server là một hệ điều hành của Microsoft được thiết kế đặc biệt để phục vụ môi trường doanh nghiệp và máy chủ. Các phiên bản phổ biến bao gồm Windows Server 2016, 2019 và 2022.

1. **Chức năng của Winserver?**

   **Một số chức năng chính của Windows Server:**

   + Quản lý người dùng và quyền truy cập: Sử dụng Active Directory để quản lý tài khoản, nhóm và quyền.

   + Cấu hình và quản lý mạng: DHCP, DNS, VPN, v.v.

   + Chia sẻ tài nguyên: Quản lý tệp, thư mục dùng chung, và ổ đĩa.

   + Ảo hóa: Dùng Hyper-V để tạo và quản lý máy ảo.

   + Bảo mật: Sử dụng tường lửa (Firewall) và các tính năng bảo mật tích hợp.

1. **Firewall trên WinServer**

   Firewall trong Windows Server giúp kiểm soát lưu lượng truy cập mạng đến và đi từ máy chủ. Nó đóng vai trò quan trọng trong bảo mật mạng.




   **Cách cấu hình Windows Firewall:**

   **2.1. Truy cập Firewall**

Mở Windows Firewall:

**Nhấn Win + R, gõ wf.msc và nhấn Enter**.

Hoặc truy cập qua Control Panel > System and Security > Windows Defender Firewall.

Giao diện Windows Firewall:

Bao gồm các quy tắc **Inbound Rules (lưu lượng vào)** và **Outbound Rules (lưu lượng ra).**

**2.2. Tạo quy tắc mới (New Rule)**

Trong cửa sổ Windows Firewall with Advanced Security, chọn Inbound Rules hoặc Outbound Rules.

Chọn New Rule ở bảng bên phải.

Làm theo hướng dẫn để:

Chọn loại quy tắc (Port, Program, Predefined, Custom).

Cấu hình cổng hoặc ứng dụng cụ thể.

Chọn hành động (Allow, Block, hoặc Allow if secure).

Đặt tên cho quy tắc.



**2.3. Quản lý Firewall trên PowerShell**

**Kiểm tra trạng thái Firewall:**

`Get-NetFirewallProfile

**Kích hoạt hoặc vô hiệu hóa Firewall:**

Set-NetFirewallProfile -Profile Domain,Public,Private -Enabled True

**Thêm quy tắc Firewall:**
**
`New-NetFirewallRule -DisplayName "Allow HTTP" -Direction Inbound -Protocol TCP -LocalPort 80 -Action Allow


4. **Các lưu ý khi sử dụng Firewall trong Window Server**
- Đảm bảo kiểm tra kỹ các quy tắc trước khi áp dụng để tránh làm gián đoạn dịch vụ.
- Theo dõi log Firewall để phát hiện các vấn đề về bảo mật.
- Kết hợp Firewall với các giải pháp bảo mật khác như VPN, mã hóa dữ liệu, và phần mềm chống mã độc.
