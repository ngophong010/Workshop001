+++
title = "Xây Dựng Phòng Thí Nghiệm"
date = 2022
weight = 6
chapter = false
pre = "<b>6. </b>"
+++

### Xây Dựng Phòng Thí Nghiệm
Chúng ta sẽ tiếp tục thiết lập mạng mô phỏng của mình bằng EVE-NG và hi vọng rằng sẽ triển khai một số thiết bị và bắt đầu nghĩ về cách tự động hóa cấu hình của các thiết bị này. Trên [Python cho Tự Động Hóa Mạng](5-PythonForNetworkAutomation/), chúng ta đã đề cập đến việc cài đặt EVE-NG trên máy của mình bằng VMware Workstation.

#### Cài Đặt EVE-NG Client
Cũng có một gói khách cho phép chúng ta lựa chọn ứng dụng nào sẽ được sử dụng khi SSH vào các thiết bị. Nó cũng sẽ thiết lập Wireshark để bắt gói giữa các liên kết. Bạn có thể tải gói khách cho hệ điều hành của mình (Windows, macOS, Linux).

[Tải EVE-NG Client](https://www.eve-ng.net/index.php/download/)
![Tải EVE-NG Client](/Workshop001/images/6.BuildingLab/001-eVE-NGClientDownload.png) 

Mẹo Nhanh: Nếu bạn đang sử dụng Linux làm máy khách, thì có gói [khách này](https://github.com/SmartFinn/eve-ng-integration).

Cài đặt khá đơn giản, chỉ cần tiếp tục và tôi gợi ý để lại các cài đặt mặc định.

#### Lấy Ảnh Mạng
Bước này đã gặp nhiều thử thách, tôi đã theo dõi một số video mà tôi sẽ liên kết ở cuối, cung cấp các nguồn và tải về cho ảnh router và switch của chúng ta đồng thời hướng dẫn cách và nơi tải lên chúng.

Quan trọng lưu ý rằng tôi sử dụng mọi thứ cho mục đích giáo dục. Tôi khuyên bạn nên tải xuống các ảnh chính thức từ các nhà cung cấp mạng.

[Blog & Liên Kết đến Video YouTube](https://loopedback.com/2019/11/15/setting-up-eve-ng-for-ccna-ccnp-ccie-level-studies-includes-multiple-vendor-node-support-an-absolutely-amazing-study-tool-to-check-out-asap/)

[Cách Thêm Ảnh Cisco VIRL vIOS vào Eve-ng](https://networkhunt.com/how-to-add-cisco-virl-vios-image-to-eve-ng/)

Tổng thể, các bước ở đây có phần phức tạp và có thể dễ hơn nhiều, nhưng các blog và video trên hướng dẫn chi tiết quy trình thêm các ảnh vào EVE-NG của bạn.

Tôi đã sử dụng FileZilla để chuyển qcow2 đến VM qua SFTP.

Đối với phòng thí nghiệm của chúng ta, chúng ta cần Cisco vIOS L2 (switches) và Cisco vIOS (router).

#### Tạo Phòng Thí Nghiệm
Trong giao diện web EVE-NG, chúng ta sẽ tạo ra một topo mạng mới. Chúng ta sẽ có bốn switch và một router sẽ hoạt động như cổng kết nối đến các mạng bên ngoài.

| Node    | Địa Chỉ IP     |
|---------|----------------|
| Router  | 10.10.88.110   |
| Switch1 | 10.10.88.111   |
| Switch2 | 10.10.88.112   |
| Switch3 | 10.10.88.113   |
| Switch4 | 10.10.88.114   |

#### Thêm Các Node vào EVE-NG
Khi bạn lần đầu đăng nhập vào EVE-NG, bạn sẽ thấy một màn hình như bên dưới, chúng ta muốn bắt đầu bằng cách tạo phòng thí nghiệm đầu tiên.
![Xây Dựng Phòng Thí Nghiệm](/Workshop001/images/6.BuildingLab/002-lab.png) 

Đặt tên cho phòng thí nghiệm của bạn và các trường khác là tùy chọn.
![Xây Dựng Phòng Thí Nghiệm](/Workshop001/images/6.BuildingLab/003-lab.png) 

Bạn sẽ thấy một bức tranh trống để bắt đầu tạo mạng của mình. Nhấp chuột phải vào canvas của bạn và chọn thêm node.

Từ đây, bạn sẽ có một danh sách dài các tùy chọn node. Nếu bạn đã theo dõi các bước trên, bạn sẽ thấy hai node màu xanh như hình dưới và các node khác sẽ màu xám và không thể chọn.
![Xây Dựng Phòng Thí Nghiệm](/Workshop001/images/6.BuildingLab/004-lab.png) 

Chúng ta muốn thêm các node sau vào phòng thí nghiệm:

- 1 x Cisco vIOS Router
- 4 x Cisco vIOS Switch

Chạy qua wizard đơn giản để thêm chúng vào phòng thí nghiệm và nó sẽ trông giống như hình bên dưới.
![Xây Dựng Phòng Thí Nghiệm](/Workshop001/images/6.BuildingLab/005-lab.png) 

#### Kết Nối Các Node
Chúng ta cần thêm kết nối giữa các router và switch. Chúng ta có thể làm điều này khá dễ dàng bằng cách di chuột qua thiết bị và nhìn thấy biểu tượng kết nối như dưới đây và sau đó kết nối nó với thiết bị mà chúng ta muốn kết nối.
![Xây Dựng Phòng Thí Nghiệm](/Workshop001/images/6.BuildingLab/006-lab.png) 

Khi bạn đã hoàn thành việc kết nối môi trường của mình, bạn cũng có thể muốn thêm một cách nào đó để định nghĩa các ranh giới hoặc vị trí vật lý bằng cách sử dụng hộp hoặc vòng tròn, có thể tìm thấy trong menu nhấp chuột phải. Bạn cũng có thể thêm văn bản, điều này rất hữu ích khi chúng ta muốn định nghĩa tên hoặc địa chỉ IP trong các phòng thí nghiệm của mình.

Tôi đã làm cho phòng thí nghiệm của mình trông như hình bên dưới.
![Xây Dựng Phòng Thí Nghiệm](/Workshop001/images/6.BuildingLab/007-lab.png) 

Bạn cũng sẽ nhận thấy rằng phòng thí nghiệm trên đều tắt nguồn, chúng ta có thể khởi động phòng thí nghiệm của mình bằng cách chọn tất cả và nhấp chuột phải chọn khởi động đã chọn.
![Xây Dựng Phòng Thí Nghiệm](/Workshop001/images/6.BuildingLab/008-lab.png) 

Khi chúng ta đã có phòng thí nghiệm lên và chạy, bạn sẽ có thể console vào từng thiết bị và bạn sẽ nhận thấy rằng vào giai đoạn này chúng đều khá "đần độn" với không có cấu hình. Chúng ta có thể thêm một số cấu hình cho mỗi node bằng cách sao chép hoặc tự tạo trong mỗi terminal.

Tôi sẽ để cấu hình của mình trong thư mục Networking của kho lưu trữ để tham khảo.
| Node    | Cấu Hình |
|---------|----------|
| Router  | [R1](/6-cleanup/config/R1.txt)            |
| Switch1 | [SW1](/6-cleanup/config/SW1.txt)           |
| Switch2 | [SW2](/6-cleanup/config/SW2.txt)           |
| Switch3 | [SW3](/6-cleanup/config/SW3.txt)           |
| Switch4 | [SW4](/6-cleanup/config/SW4.txt)           |