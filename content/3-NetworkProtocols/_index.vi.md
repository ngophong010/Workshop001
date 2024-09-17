---
title: "Giao thức Mạng"
date: "`r Sys.Date()`"
weight: 3
chapter: false
pre: " <b> 3. </b> "
---

### Giao thức Mạng
Một tập hợp các quy tắc và thông điệp tạo thành một tiêu chuẩn. Một Tiêu chuẩn Internet.
- ARP - Giao thức Phân giải Địa chỉ

Nếu bạn muốn tìm hiểu sâu về ARP, bạn có thể đọc Tiêu chuẩn Internet tại đây. [RFC 826](https://datatracker.ietf.org/doc/html/rfc826)

Kết nối địa chỉ IP với các địa chỉ máy cố định, còn được gọi là địa chỉ MAC trên một mạng lớp 2.
![Giao thức Mạng](/Workshop001/images/3.NetworkProtocols/001-networkProtocols.png)

- FTP - Giao thức Chuyển File

Cho phép chuyển file từ nguồn đến đích. Quá trình này thường được xác thực nhưng có khả năng sử dụng truy cập ẩn danh nếu được cấu hình. Hiện nay, bạn sẽ thấy FTPS nhiều hơn, cung cấp kết nối SSL/TLS đến các máy chủ FTP từ phía khách hàng để tăng cường bảo mật. Giao thức này sẽ được tìm thấy trong lớp Ứng dụng của Mô hình OSI.
![Giao thức Mạng - FTP](/Workshop001/images/3.NetworkProtocols/002-ftp.png)

- SMTP - Giao thức Chuyển Giao Thư Đơn

Được sử dụng để truyền tải email, các máy chủ mail sử dụng SMTP để gửi và nhận tin nhắn thư. Ngay cả với Microsoft 365, giao thức SMTP vẫn được sử dụng cho cùng mục đích.
![Giao thức Mạng - SMTP](/Workshop001/images/3.NetworkProtocols/003-smtp.png)

- HTTP - Giao thức Truyền Tải Siêu Văn Bản

HTTP là nền tảng của internet và việc duyệt nội dung. Cho phép chúng ta dễ dàng truy cập vào các trang web yêu thích. HTTP vẫn được sử dụng nhiều nhưng HTTPS hiện nay được sử dụng nhiều hơn hoặc nên được sử dụng trên hầu hết các trang web yêu thích của bạn.
![Giao thức Mạng - HTTP](/Workshop001/images/3.NetworkProtocols/004-http.png)

- SSL - Lớp Sockets Bảo mật | TLS - Bảo mật Giao vận

TLS đã thay thế SSL, TLS là một **Giao thức Mã hóa** cung cấp các giao tiếp an toàn qua một mạng. Nó có thể và sẽ được tìm thấy trong mail, nhắn tin nhanh và các ứng dụng khác, nhưng phổ biến nhất là được sử dụng để bảo mật HTTPS.
![Giao thức Mạng - TLS/SSL](/Workshop001/images/3.NetworkProtocols/005-tlsssl.png)

- HTTPS - HTTP được bảo mật bằng SSL/TLS

Là một phần mở rộng của HTTP, được sử dụng cho các giao tiếp an toàn qua một mạng, HTTPS được mã hóa bằng TLS như đã đề cập ở trên. Mục tiêu ở đây là cung cấp xác thực, quyền riêng tư và toàn vẹn trong khi dữ liệu được trao đổi giữa các máy chủ.
![Giao thức Mạng - HTTPS](/Workshop001/images/3.NetworkProtocols/006-https.png)

- DNS - Hệ thống Tên Miền

DNS được sử dụng để ánh xạ các tên miền thân thiện với con người, ví dụ như chúng ta đều biết [google.com](https://www.google.com/) nhưng nếu bạn mở trình duyệt và nhập [8.8.8.8](https://dns.google/) bạn sẽ thấy Google như chúng ta đã biết. Tuy nhiên, thật khó để nhớ tất cả các địa chỉ IP cho tất cả các trang web mà một số trong đó chúng ta thậm chí sử dụng Google để tìm kiếm thông tin.

Đây là nơi DNS xuất hiện, đảm bảo rằng các máy chủ, dịch vụ và tài nguyên khác đều có thể tiếp cận được.

Trên tất cả các máy chủ, nếu họ cần kết nối internet thì họ phải có DNS để có thể phân giải các tên miền. DNS là một lĩnh vực mà bạn có thể dành cả Ngày và Năm để học hỏi. Tôi cũng sẽ nói từ kinh nghiệm rằng DNS thường là nguyên nhân chính của tất cả các lỗi khi nói đến Mạng. Không biết liệu một kỹ sư mạng có đồng ý với điều đó không.
![Giao thức Mạng - DNS](/Workshop001/images/3.NetworkProtocols/007-dns.png)

- DHCP - Giao thức Cấp phát Địa chỉ Động

Chúng ta đã thảo luận rất nhiều về các giao thức cần thiết để làm cho các máy chủ hoạt động, cho dù là truy cập internet hay chuyển file giữa nhau.

Có 4 điều mà chúng ta cần trên mỗi máy chủ để có thể thực hiện cả hai nhiệm vụ đó.

- Địa chỉ IP
- Mặt nạ Subnet
- Cổng Mặc định
- DNS

Chúng ta đã đề cập đến địa chỉ IP là một địa chỉ duy nhất cho máy chủ của bạn trên mạng mà nó nằm, chúng ta có thể nghĩ đến điều này như số nhà của chúng ta.

Mặt nạ subnet sẽ được đề cập sau, nhưng bạn có thể nghĩ về điều này như mã bưu điện hoặc mã zip.

Cổng mặc định là IP của bộ định tuyến trên mạng của chúng ta cung cấp cho chúng ta kết nối Lớp 3. Bạn có thể nghĩ về điều này như con đường duy nhất cho phép chúng ta ra khỏi phố của mình.

Sau đó, chúng ta có DNS như đã đề cập để giúp chúng ta chuyển đổi các địa chỉ IP công cộng phức tạp thành các tên miền dễ nhớ hơn. Có thể chúng ta có thể nghĩ về điều này như một văn phòng phân loại khổng lồ để đảm bảo chúng ta nhận được đúng bưu phẩm.

Như tôi đã nói, mỗi máy chủ cần 4 thứ này, nếu bạn có 1000 hoặc 10.000 máy chủ thì điều đó sẽ mất rất nhiều thời gian để xác định từng cái một. Đây là nơi DHCP xuất hiện và cho phép bạn xác định một phạm vi cho mạng của bạn và sau đó giao thức này sẽ phân phối cho tất cả các máy chủ có sẵn trong mạng của bạn.

Một ví dụ khác là bạn vào một quán cà phê, lấy một tách cà phê và ngồi xuống với máy tính xách tay hoặc điện thoại của bạn, hãy gọi đó là máy chủ của bạn. Bạn kết nối máy chủ của mình với WiFi quán cà phê và bạn có quyền truy cập vào internet, tin nhắn và thư bắt đầu ping qua và bạn có thể duyệt các trang web và mạng xã hội. Khi bạn kết nối với WiFi quán cà phê, máy của bạn sẽ nhận được một địa chỉ DHCP từ một máy chủ DHCP chuyên dụng hoặc có thể là từ bộ định tuyến cũng xử lý DHCP.
![Giao thức Mạng - DHCP](/Workshop001/images/3.NetworkProtocols/008-dhcp.png)

#### Phân đoạn Mạng
Một subnet là một phân vùng logic của một mạng IP.

Các subnet chia các mạng lớn thành các mạng nhỏ hơn, dễ quản lý hơn và hoạt động hiệu quả hơn.

Mỗi subnet là một phân vùng logic của mạng lớn hơn. Các thiết bị kết nối đủ subnet chia sẻ các định danh địa chỉ IP chung, cho phép chúng giao tiếp với nhau.

Các bộ định tuyến quản lý giao tiếp giữa các subnet.

Kích thước của một subnet phụ thuộc vào yêu cầu kết nối và công nghệ mạng được sử dụng.

Một tổ chức có trách nhiệm xác định số lượng và kích thước của các subnet trong giới hạn không gian địa chỉ có sẵn, và các chi tiết này vẫn là địa phương đối với tổ chức đó. Các subnet cũng có thể được phân đoạn thành các subnet nhỏ hơn cho các liên kết Point-to-Point hoặc các mạng con hỗ trợ một vài thiết bị.

Giữa các lợi ích khác, việc phân đoạn các mạng lớn thành các subnet cho phép tái phân bổ địa chỉ IP và giảm tắc nghẽn mạng, tối ưu hóa giao tiếp và hiệu suất mạng.

Các subnet cũng có thể cải thiện bảo mật mạng. Nếu một phần của mạng bị xâm nhập, nó có thể được cách ly, làm cho kẻ xấu khó khăn trong việc di chuyển xung quanh mạng lớn hơn.
![Giao thức Mạng - Subnets](/Workshop001/images/3.NetworkProtocols/009-subnets.png)