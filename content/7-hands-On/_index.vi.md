---
title: "Thực Hành với Python & Mạng"
date: "`r Sys.Date()`"
weight: 7
chapter: false
pre: "<b>7. </b>"
---

### Thực Hành với Python & Mạng
Trong phần cuối cùng của kiến thức cơ bản về Mạng, chúng ta sẽ đề cập đến một số tác vụ và công cụ tự động hóa trong môi trường phòng thí nghiệm mà chúng ta đã tạo ra trong [Xây Dựng Phòng Thí Nghiệm](/6-BuildingOurLab).

Chúng ta sẽ sử dụng một đường hầm SSH để kết nối với các thiết bị từ máy khách thay vì telnet. Đường hầm SSH được tạo ra giữa máy khách và thiết bị được mã hóa.

### Truy cập môi trường giả lập ảo của chúng ta
Để tương tác với các switch, chúng ta cần một máy trạm bên trong mạng EVE-NG hoặc bạn có thể triển khai một máy Linux ở đó với Python đã được cài đặt để thực hiện tự động hóa ([Tài nguyên để thiết lập Linux trong EVE-NG](https://www.youtube.com/watch?v=3Qstk3zngrY)) hoặc bạn có thể làm như tôi và định nghĩa một cloud để truy cập từ máy trạm của mình.
![Xây Dựng Phòng Thí Nghiệm](/images/7.hands-On/001-lab.png) 

Để thực hiện điều này, chúng ta đã nhấp chuột phải vào canvas và chọn mạng, sau đó chọn "Management(Cloud0)" để kết nối với mạng gia đình của chúng ta.
![Xây Dựng Phòng Thí Nghiệm](/images/7.hands-On/002-lab.png) 

Tuy nhiên, chúng ta chưa có gì trong mạng này, vì vậy chúng ta cần thêm kết nối từ mạng mới đến từng thiết bị. (Kiến thức mạng của tôi cần được cải thiện và tôi cảm thấy rằng bạn có thể chỉ cần thực hiện bước tiếp theo này đến router chính và sau đó có kết nối đến phần còn lại của mạng thông qua một cáp này?)

Tôi đã đăng nhập vào từng thiết bị và thực hiện các lệnh sau cho các giao diện áp dụng nơi cloud đến.

```plaintext
enable
config t
int g0/0
IP add DHCP
no sh
exit
exit
sh ip int br
```
Bước cuối cùng cho chúng ta địa chỉ DHCP từ mạng gia đình. Danh sách thiết bị mạng của tôi như sau:

| Node    | Địa chỉ IP     | IP mạng gia đình   |
|---------|----------------|-------------------|
| Router  | 10.10.88.110   | 192.168.169.115   |
| Switch1 | 10.10.88.111   | 192.168.169.178   |
| Switch2 | 10.10.88.112   | 192.168.169.193   |
| Switch3 | 10.10.88.113   | 192.168.169.125   |
| Switch4 | 10.10.88.114   | 192.168.169.197   |

#### SSH đến thiết bị mạng
Với thiết lập trên, chúng ta có thể kết nối đến các thiết bị trên mạng gia đình bằng máy trạm của mình. Tôi đang sử dụng Putty nhưng cũng có thể sử dụng các terminal khác như git bash để SSH đến các thiết bị.

Dưới đây bạn có thể thấy chúng ta có một kết nối SSH tới thiết bị router (R1).
![Xây Dựng Phòng Thí Nghiệm](/images/7.hands-On/003-lab.png)

#### Sử dụng Python để thu thập thông tin từ các thiết bị
Ví dụ đầu tiên về cách chúng ta có thể tận dụng Python là để thu thập thông tin từ tất cả các thiết bị của mình. Tôi đã lưu kịch bản này tại [netmiko_con_multi.py](/Scripts/netmiko_con_multi.py).

Khi tôi chạy kịch bản này, tôi có thể thấy cấu hình từng cổng trên tất cả các thiết bị của mình.
![Xây Dựng Phòng Thí Nghiệm](/images/7.hands-On/004-lab.png)

Điều này có thể hữu ích nếu bạn có nhiều thiết bị khác nhau, tạo ra kịch bản này để bạn có thể kiểm soát trung tâm và hiểu nhanh tất cả các cấu hình ở một nơi.

#### Sử dụng Python để cấu hình các thiết bị
Điều này hữu ích nhưng còn gì về việc sử dụng Python để cấu hình các thiết bị của chúng ta? Trong kịch bản của chúng ta, chúng ta có một cổng trunked giữa `SW1` và `SW2`. Hãy tưởng tượng nếu điều này được thực hiện trên nhiều switch giống nhau, chúng ta muốn tự động hóa điều đó và không phải kết nối thủ công đến từng switch để thực hiện thay đổi cấu hình.

Chúng ta có thể sử dụng [netmiko_sendchange.py](/Scripts/netmiko_sendchange.py) để đạt được điều này. Kịch bản này sẽ kết nối qua SSH và thực hiện thay đổi trên `SW1`, điều này cũng sẽ thay đổi trên `SW2`.
![Xây Dựng Phòng Thí Nghiệm](/images/7.hands-On/005-lab.png)

Với những ai xem mã, bạn sẽ thấy thông điệp xuất hiện và cho chúng ta biết đang gửi cấu hình đến thiết bị nhưng không có xác nhận rằng điều này đã xảy ra. Chúng ta có thể thêm mã bổ sung vào kịch bản của mình để thực hiện kiểm tra và xác nhận trên switch của chúng ta hoặc có thể chỉnh sửa kịch bản trước đó để cho thấy điều này. [netmiko_con_multi_vlan.py](/Scripts/netmiko_con_multi_vlan.py)
![Xây Dựng Phòng Thí Nghiệm](/images/7.hands-On/006-lab.png)

#### Sao lưu cấu hình thiết bị của bạn
Một trường hợp sử dụng khác là để ghi lại các cấu hình mạng của chúng ta và đảm bảo rằng chúng ta đã sao lưu những cấu hình đó. Nhưng một lần nữa, chúng ta không muốn kết nối đến từng thiết bị mà chúng ta có trên mạng, vì vậy chúng ta cũng có thể tự động hóa điều này bằng cách sử dụng [backup.py](/Scripts/backup.py). Bạn cũng sẽ cần điền vào [backup.txt](/Scripts/backup.txt) với các địa chỉ IP mà bạn muốn sao lưu.

Chạy kịch bản của bạn và bạn sẽ thấy một cái gì đó như dưới đây.
![Xây Dựng Phòng Thí Nghiệm](/images/7.hands-On/007-lab.png)

Đó có thể chỉ là một kịch bản print đơn giản trong Python, vì vậy tôi cũng nên cho bạn thấy các tệp sao lưu.
![Xây Dựng Phòng Thí Nghiệm](/images/7.hands-On/008-lab.png)

#### Paramiko
Một mô-đun Python được sử dụng rộng rãi cho SSH. Bạn có thể tìm hiểu thêm tại liên kết GitHub chính thức [tại đây](https://github.com/paramiko/paramiko).

Chúng ta có thể cài đặt mô-đun này bằng lệnh `pip install paramiko`.
![Xây Dựng Phòng Thí Nghiệm](/images/7.hands-On/009-lab.png)

Chúng ta có thể xác nhận cài đặt bằng cách nhập shell Python và nhập mô-đun paramiko.
![Xây Dựng Phòng Thí Nghiệm](/images/7.hands-On/010-lab.png)

#### Netmiko
Mô-đun netmiko nhắm đến các thiết bị mạng cụ thể trong khi paramiko là một công cụ rộng hơn để xử lý các kết nối SSH tổng thể.

Netmiko mà chúng ta đã sử dụng ở trên cùng với paramiko có thể được cài đặt bằng lệnh `pip install netmiko`.

Netmiko hỗ trợ nhiều nhà cung cấp và thiết bị mạng, bạn có thể tìm danh sách các thiết bị được hỗ trợ trên [Trang GitHub](https://github.com/ktbyers/netmiko#supports).

#### Các mô-đun khác
Cũng đáng đề cập đến một vài mô-đun khác mà chúng ta chưa có thời gian tìm hiểu nhưng chúng cung cấp nhiều chức năng hơn khi nói đến tự động hóa mạng. `netaddr` được sử dụng để làm việc và xử lý địa chỉ IP, lại một lần nữa, việc cài đặt rất đơn giản bằng lệnh `pip install netaddr`.

Nếu bạn muốn lưu trữ nhiều cấu hình switch của mình trong một bảng tính Excel, mô-đun `xlrd` sẽ cho phép các kịch bản của bạn đọc workbook Excel và chuyển đổi các hàng và cột thành một ma trận. Cài đặt mô-đun này bằng lệnh `pip install xlrd`.

Một số trường hợp sử dụng khác mà tự động hóa mạng có thể được áp dụng mà tôi chưa có thời gian tìm hiểu có thể được tìm thấy [tại đây](https://github.com/ktbyers/pynet/tree/master/presentations/dfwcug/examples).