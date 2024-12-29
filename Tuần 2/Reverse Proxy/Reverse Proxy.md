**Reverse Proxy**

Reverse Proxy là một loại máy chủ (Server) hoạt động như một trung gian giữa người dùng và các máy chủ Back-end (Backend Servers). Trong kiến trúc mạng, Reverse Proxy đảo ngược (hoặc còn gọi là Server đảo ngược) thường được đặt giữa người dùng và các máy chủ backend để thực hiện một số chức năng quan trọng.

![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/Reverse%20Proxy/hình%20ảnh/Aspose.Words.f4104cb1-1ed8-49d5-86d0-7433c65b7b13.001.jpeg)




**Triển khai Reverse Proxy** 

![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/Reverse%20Proxy/hình%20ảnh/Aspose.Words.f4104cb1-1ed8-49d5-86d0-7433c65b7b13.002.png)

Tiến hành cài đặt webserver apache cho máy chủ

**Apt install apache2 –y**

![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/Reverse%20Proxy/hình%20ảnh/Aspose.Words.f4104cb1-1ed8-49d5-86d0-7433c65b7b13.003.png)

**Sau khi cài đặt hoàn tất apache2, ta tiến hành khởi động dịch vụ apache2 thông qua các câu lệnh**

- **Systemctl start apache2**
- **Systemctl enable apache2**
- **Systemctl status apache2**

![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/Reverse%20Proxy/hình%20ảnh/Aspose.Words.f4104cb1-1ed8-49d5-86d0-7433c65b7b13.004.png)

**Ta thấy apache2 đã ở trạng thái active (running)**

![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/Reverse%20Proxy/hình%20ảnh/Aspose.Words.f4104cb1-1ed8-49d5-86d0-7433c65b7b13.005.png)

Tiến hành truy cập website apache2 bằng địa chỉ IP của máy chủ

Như hình thì ta đã cài đặt thành công rồi!

File cấu hình index.html sẽ nằm trong đường dẫn **/var/www/html**

Vì vậy ta có thể truy xuất vào để thay đổi nội dung **index.html**

![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/Reverse%20Proxy/hình%20ảnh/Aspose.Words.f4104cb1-1ed8-49d5-86d0-7433c65b7b13.006.png)

Truy cập lại website sau khi đã đổi nội dung trong file index

Tiến hành cấu hình nginx làm reverse proxy cho website

- Tiến hành tải nginx

![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/Reverse%20Proxy/hình%20ảnh/Aspose.Words.f4104cb1-1ed8-49d5-86d0-7433c65b7b13.007.png)

Câu lệnh tải nginx: apt install nginx –y

Sau khi cài đặt thành công ngix, mình hãy sửa cấu hình máy chủ apache sang một port khác ngoài 80 để không bị đụng port với ngix

Truy cập vi /etc/apache2/ports.conf để thay đổi port của apache2 sang port 8080

![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/Reverse%20Proxy/hình%20ảnh/Aspose.Words.f4104cb1-1ed8-49d5-86d0-7433c65b7b13.008.png)

Vì đã chuyển port của Apache sang cổng 8081 nên file 000-default.conf của apache cũng phải chuyển sang port 8080

Truy xuất đến đường dẫn: vi /etc/apache2/sites-available/000-default.conf

Chỉnh sửa virtualhost thành 8080

![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/Reverse%20Proxy/hình%20ảnh/Aspose.Words.f4104cb1-1ed8-49d5-86d0-7433c65b7b13.009.png)

Sau đó tiến hành khởi động lại dịch vụ apache2 để lưu cấu hình trên port mới

![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/Reverse%20Proxy/hình%20ảnh/Aspose.Words.f4104cb1-1ed8-49d5-86d0-7433c65b7b13.010.png)

Đã truy cập website thành công trên port mới


Ta tiến hành cấu hình Nginx để làm reverse proxy 

Tạo một file mới theo lệnh dưới đây

vi /etc/nginx/sites-available/reverse-proxy.conf

Dán dòng lệnh này nào file reverse-proxy.conf

server {

`    `listen 80;

`    `server\_name <domain hoac ip may chu cua ban>;

`    `location / {

`        `proxy\_pass http://127.0.0.1:8080;

`        `proxy\_set\_header Host $host;

`        `proxy\_set\_header X-Real-IP $remote\_addr;

`        `proxy\_set\_header X-Forwarded-For $proxy\_add\_x\_forwarded\_for;

`        `proxy\_set\_header X-Forwarded-Proto $scheme;

`    `}

}

![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/Reverse%20Proxy/hình%20ảnh/Aspose.Words.f4104cb1-1ed8-49d5-86d0-7433c65b7b13.011.png)

Giải thích về các dòng lệnh:

\+ **Listen 80:** Do cả nginx và apache đều chạy port 80(HTTP) mà ta đã chuyển apache sang port 8080 nên chỉ còn nginx chạy port80, nên ngnix sẽ tiến hành lắng nghe ở port 80(HTTP)

\+ **Server\_name:** Khai báo tên miền hoặc địa chỉ IP mà nginx sẽ chạy khi có request gửi đến tên miền hoặc địa chỉ này.

\+ **proxy\_pass:** Nginx sẽ chuyển tiếp (proxy) tất cả các yêu cầu đến máy chủ backend tại địa chỉ 127.0.0.1:8080.

\+ **proxy\_set\_header Host $host:** Thiết lập tiêu đề HTTP Host với giá trị của biến $host 

\+ **proxy\_set\_header X-Real-IP $remote\_addr**: Gửi địa chỉ IP thực của người dùng (client) qua tiêu đề HTTP X-Real-IP

\+ **proxy\_set\_header X-Forwarded-For $proxy\_add\_x\_forwarded\_for:** Thêm địa chỉ IP của người dùng (client) vào tiêu đề HTTP X-Forwarded-For

\+ **proxy\_set\_header X-Forwarded-Proto $scheme:** Gửi giao thức HTTP được sử dụng (HTTP hoặc HTTPS) qua tiêu đề X-Forwarded-Proto.

Sau khi tạo file cấu hình như trên chúng ta sẽ kích hoạt và liên kết đến thư mục sites-enable

![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/Reverse%20Proxy/hình%20ảnh/Aspose.Words.f4104cb1-1ed8-49d5-86d0-7433c65b7b13.012.png)

sudo ln -s /etc/nginx/sites-available/reverse-proxy.conf /etc/nginx/sites-enabled/

Kiểm tra nginx cấu hình đã hoạt động chưa:

![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/Reverse%20Proxy/hình%20ảnh/Aspose.Words.f4104cb1-1ed8-49d5-86d0-7433c65b7b13.013.png)

Nginx –t

- Hoạt động thành công

Tiến hành restart nginx để lưu cấu hình

![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/Reverse%20Proxy/hình%20ảnh/Aspose.Words.f4104cb1-1ed8-49d5-86d0-7433c65b7b13.014.png)

![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/Reverse%20Proxy/hình%20ảnh/Aspose.Words.f4104cb1-1ed8-49d5-86d0-7433c65b7b13.015.png)

Tiến hành truy cập lại địa chỉ ip của máy chủ

![alt](https://github.com/Kun2003/Vietnix/blob/main/Tuần%202/Reverse%20Proxy/hình%20ảnh/Aspose.Words.f4104cb1-1ed8-49d5-86d0-7433c65b7b13.016.png)

Ta có thể thấy ta cấu hình dịch vụ trên Apache nhưng ở đây hiển thị là nginx như vậy ta đã cấu hình thành công Reverse Proxy

