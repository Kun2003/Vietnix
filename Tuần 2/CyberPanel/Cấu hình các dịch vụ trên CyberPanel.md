**Cấu hình các dịch vụ trên CyberPanel**

1. **Kiểm tra url login**

   ![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/CyberPanel/hinh%20anh/Aspose.Words.29c24d6c-bdbe-4cdb-ad25-6786e8da7486.001.png)

   CyberPanel mặc định sẽ chạy ở port 8090 với url là [https://<địa chỉ IP>:8090](https://14.225.206.83:8090)

1. **Kiểm tra trạng thái OpenLiteSpeed**

   ![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/CyberPanel/hinh%20anh/Aspose.Words.29c24d6c-bdbe-4cdb-ad25-6786e8da7486.002.png)

   Trạng thái active (Running) là hệ thống đang chạy bình thường

   Kiểm tra bằng lệnh: **systemctl status lsws**





1. **Theo dõi nhật ký trực tiếp của OpenLiteSpeed**

   ![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/CyberPanel/hinh%20anh/Aspose.Words.29c24d6c-bdbe-4cdb-ad25-6786e8da7486.003.png)

   Kiểm tra bằng lệnh: 

   **tail –f /usr/local/lsws/logs/error.log**

1. **Kiểm tra cấu trúc CyberPanel dạng cây**

   ![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/CyberPanel/hinh%20anh/Aspose.Words.29c24d6c-bdbe-4cdb-ad25-6786e8da7486.004.png)

   Sử dụng câu lệnh: **tree /usr/local/CyberCP**

1. **Đổi mật khảu cho CyberPanel**

   ![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/CyberPanel/hinh%20anh/Aspose.Words.29c24d6c-bdbe-4cdb-ad25-6786e8da7486.005.png)

   **Gõ câu lệnh adminPass <password mới>**

1. **Giao diện đăng nhập thành công của CyberPanel**

   ![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/CyberPanel/hinh%20anh/Aspose.Words.29c24d6c-bdbe-4cdb-ad25-6786e8da7486.006.png)

   Giao diện sau khi đăng nhập thành công của CyberPanel














1. **Tạo một user mới trong CyberPanel**

   ![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/CyberPanel/hinh%20anh/Aspose.Words.29c24d6c-bdbe-4cdb-ad25-6786e8da7486.007.png)

   Tiến hành tạo user và khai báo các thông tin chi tiết về user đó, đồng **thời set ACL(vai trò của user đó)** và security level là mức bảo vệ tài khoản

   Trong CyberPanel sẽ chia làm **2 cấp độ security để bảo vệ tài khoản bao gồm: High và Low**

   Websites Limit là số lượng website mà user đó có thể tạo, nhập **0 là user đó sẽ không bị giới hạn về số lượng tạo website của user đó gọi là Unlimited**





1. **Tạo website http trên CyberPanel**

   ![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/CyberPanel/hinh%20anh/Aspose.Words.29c24d6c-bdbe-4cdb-ad25-6786e8da7486.008.png)

   Tạo website trên CyberPanel

   ![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/CyberPanel/hinh%20anh/Aspose.Words.29c24d6c-bdbe-4cdb-ad25-6786e8da7486.009.png)

   Tạo thành công một website với giao thức http







1. **Cấu hình SSL trên CyberPanel**

   ![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/CyberPanel/hinh%20anh/Aspose.Words.29c24d6c-bdbe-4cdb-ad25-6786e8da7486.010.png)

   **Lựa chọn manage SSL góc trái màn hình**

   ![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/CyberPanel/hinh%20anh/Aspose.Words.29c24d6c-bdbe-4cdb-ad25-6786e8da7486.011.png)

   Chọn website cần cài đặt ssl

   ![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/CyberPanel/hinh%20anh/Aspose.Words.29c24d6c-bdbe-4cdb-ad25-6786e8da7486.012.png)

   Quá trình cài đặt ssl hoàn tất

   ![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/CyberPanel/hinh%20anh/Aspose.Words.29c24d6c-bdbe-4cdb-ad25-6786e8da7486.013.png)

   Website đã lên được https và không còn bị not secure











1. **Cấu hình email hosting**

   ![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/CyberPanel/hinh%20anh/Aspose.Words.29c24d6c-bdbe-4cdb-ad25-6786e8da7486.014.png)

   Lựa chọn SSL chọn Mailserver để tiến hành cài đặt SSL

   ![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/CyberPanel/hinh%20anh/Aspose.Words.29c24d6c-bdbe-4cdb-ad25-6786e8da7486.015.png)

   Lựa chọn domain mailserver cần cài ssl 


   ![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/CyberPanel/hinh%20anh/Aspose.Words.29c24d6c-bdbe-4cdb-ad25-6786e8da7486.016.png)

   Lựa chọn tên miền cần tạo email

   Mình tạo <test1@neiji.space> 

   ![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/CyberPanel/hinh%20anh/Aspose.Words.29c24d6c-bdbe-4cdb-ad25-6786e8da7486.017.png)

   Mình tiếp tục tạo email thứ 2 với tên là <test2@neiji.space> 

   ![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/CyberPanel/hinh%20anh/Aspose.Words.29c24d6c-bdbe-4cdb-ad25-6786e8da7486.018.png)

   Kiểm tra các email có trong tên miền neiji.space và giao thức IMAP/POP3 

   ![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/CyberPanel/hinh%20anh/Aspose.Words.29c24d6c-bdbe-4cdb-ad25-6786e8da7486.019.png)

   Thông số chi tiết về giao thức IMAP/POP3


![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/CyberPanel/hinh%20anh/Aspose.Words.29c24d6c-bdbe-4cdb-ad25-6786e8da7486.020.png)

Truy cập Access Webmail để tiến hành đăng nhập email hosting

![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/CyberPanel/hinh%20anh/Aspose.Words.29c24d6c-bdbe-4cdb-ad25-6786e8da7486.021.png)

Giao diện đăng nhập mail của Cyberpanel

![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/CyberPanel/hinh%20anh/Aspose.Words.29c24d6c-bdbe-4cdb-ad25-6786e8da7486.022.png)

Tiến hành gửi thư từ <test1@neiji.space> tới <test2@neiji.space> 

![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/CyberPanel/hinh%20anh/Aspose.Words.29c24d6c-bdbe-4cdb-ad25-6786e8da7486.023.png)

<test2@neiji.space> đã nhận được email từ <test1@neiji.space> 

1. **Cài đặt wordpress** 

   ![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/CyberPanel/hinh%20anh/Aspose.Words.29c24d6c-bdbe-4cdb-ad25-6786e8da7486.024.png)

   Lựa chọn Website -> List Website -> Manage -> Kéo xuống cuối tìm mục APPLICATION INSTALLER -> chọn WP + LSCache

   ![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/CyberPanel/hinh%20anh/Aspose.Words.29c24d6c-bdbe-4cdb-ad25-6786e8da7486.025.png)

   Tiến hành tạo user/password để cài đặt Wordpress

   ![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/CyberPanel/hinh%20anh/Aspose.Words.29c24d6c-bdbe-4cdb-ad25-6786e8da7486.026.png)

   Tiến hành quá trình cài đặt Wordpress

   ![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/CyberPanel/hinh%20anh/Aspose.Words.29c24d6c-bdbe-4cdb-ad25-6786e8da7486.027.png)

   Cài đặt thành công

   ![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/CyberPanel/hinh%20anh/Aspose.Words.29c24d6c-bdbe-4cdb-ad25-6786e8da7486.028.png)Website thay đổi sau khi cài đặt thành công wordpress

   ![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/CyberPanel/hinh%20anh/Aspose.Words.29c24d6c-bdbe-4cdb-ad25-6786e8da7486.029.png)

   Giao diện đăng nhập trang quản trị Wordpress

   ![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/CyberPanel/hinh%20anh/Aspose.Words.29c24d6c-bdbe-4cdb-ad25-6786e8da7486.030.png)

   Chỉnh sửa lại code trong wordpress để trở lại giao diện ban đầu

1. **Cài đặt một số plugin cần thiết**

   ![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/CyberPanel/hinh%20anh/Aspose.Words.29c24d6c-bdbe-4cdb-ad25-6786e8da7486.031.png)

   Jetpack- WP Security, Backup, Speed, & Growth

   Là một plugin được phát triển bởi chính Wordpressm rất đa dạng về tính năng như backup, scan các phần mềm độc hại, ngăn chặn brute Force…

   ![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/CyberPanel/hinh%20anh/Aspose.Words.29c24d6c-bdbe-4cdb-ad25-6786e8da7486.032.png)

   Rank Math là một plugin WordPress SEO thân thiện với người dùng đang phát triển nhanh chóng cho phép bạn tối ưu hóa trang web của mình cho các công cụ tìm kiếm và phương tiện truyền thông xã hội.

1. **FTP Account**

   ![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/CyberPanel/hinh%20anh/Aspose.Words.29c24d6c-bdbe-4cdb-ad25-6786e8da7486.033.png)

   Tiến hành vào FTP->Create FTP Account

   ![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/CyberPanel/hinh%20anh/Aspose.Words.29c24d6c-bdbe-4cdb-ad25-6786e8da7486.034.png)Tiến hành lựa chọn website cùng với username và password

   ![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/CyberPanel/hinh%20anh/Aspose.Words.29c24d6c-bdbe-4cdb-ad25-6786e8da7486.035.png)

   Kiểm tra list account FTP

   ![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/CyberPanel/hinh%20anh/Aspose.Words.29c24d6c-bdbe-4cdb-ad25-6786e8da7486.036.png)

   Tiến hành sử dụng winSCP để truy cập vào FTP

   ![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/CyberPanel/hinh%20anh/Aspose.Words.29c24d6c-bdbe-4cdb-ad25-6786e8da7486.037.png)

   Truy cập vào đường dẫn website thành công thông qua FTP account
