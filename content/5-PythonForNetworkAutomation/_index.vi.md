---
title : "Python cho Tự động hóa Mạng"
date : "`r Sys.Date()`"
weight : 5
chapter : false
pre : " <b> 5. </b> "
---

### Python cho Tự động hóa Mạng

Python là ngôn ngữ tiêu chuẩn được sử dụng cho các hoạt động mạng tự động.

Mặc dù không chỉ dành riêng cho tự động hóa mạng, Python dường như xuất hiện ở khắp nơi khi bạn tìm kiếm tài nguyên và như đã đề cập trước đó, nếu không phải là Python thì thường là Ansible, cũng được viết bằng Python.
- Dễ đọc và dễ sử dụng - Có vẻ như Python dễ hiểu. Dường như không có yêu cầu về `{}` trong mã để bắt đầu và kết thúc các khối. Kết hợp điều này với một IDE mạnh mẽ như VS Code, bạn có một khởi đầu khá dễ dàng khi muốn chạy một số mã Python.

Pycharm có thể là một IDE khác đáng được đề cập ở đây.

- Thư viện - Khả năng mở rộng của Python là kho báu thực sự ở đây, tôi đã đề cập trước đó rằng điều này không chỉ dành cho Tự động hóa Mạng mà thực tế, có rất nhiều thư viện cho tất cả các loại thiết bị và cấu hình. Bạn có thể thấy số lượng lớn ở đây [PyPi](https://pypi.org/)

Khi bạn muốn tải thư viện về máy trạm của mình, bạn sử dụng một công cụ gọi là pip để kết nối với PyPI và tải nó về máy cục bộ. Các nhà cung cấp mạng như Cisco, Juniper và Arista đã phát triển các thư viện để tạo điều kiện truy cập vào thiết bị của họ.

- Mạnh mẽ & Hiệu quả - Nhớ lại trong những ngày Go, tôi đã trải qua kịch bản "Hello World" và chúng ta đã đi qua tôi nghĩ là 6 dòng mã? Trong Python, nó chỉ là
```plaintext
print('hello world')
```

Khi tổng hợp tất cả các điểm trên, dễ dàng thấy được lý do tại sao Python thường được nhắc đến như công cụ mặc định khi làm việc với tự động hóa.

Điều quan trọng cần lưu ý là có thể vài năm trước đã có các script tương tác với thiết bị mạng để tự động hóa sao lưu cấu hình hoặc thu thập nhật ký và thông tin chi tiết khác về thiết bị của bạn. Tự động hóa mà chúng ta đang nói đến ở đây hơi khác một chút vì tổng thể cảnh quan mạng cũng đã thay đổi để phù hợp hơn với cách suy nghĩ này và cho phép tự động hóa nhiều hơn.

- Mạng Định nghĩa bằng Phần mềm - Các bộ điều khiển SDN chịu trách nhiệm cung cấp cấu hình mặt phẳng điều khiển cho tất cả các thiết bị trên mạng, có nghĩa là chỉ cần một điểm liên hệ duy nhất cho bất kỳ thay đổi mạng nào, không còn phải telnet hoặc SSH vào từng thiết bị và cũng không phải dựa vào con người để thực hiện điều này, điều có thể dẫn đến lỗi hoặc cấu hình sai lặp đi lặp lại.

- Điều phối Cấp cao - Đi lên một cấp từ các bộ điều khiển SDN đó và điều này cho phép điều phối các cấp độ dịch vụ, sau đó là tích hợp lớp điều phối này vào các nền tảng bạn chọn, VMware, Kubernetes, Public Clouds, v.v.

- Quản lý dựa trên Chính sách - Bạn muốn có gì? Trạng thái mong muốn là gì? Bạn mô tả điều này và hệ thống có tất cả các chi tiết về cách tìm ra để trở thành trạng thái mong muốn.

### Thiết lập môi trường thử nghiệm
Không phải ai cũng có quyền truy cập vào các bộ định tuyến, switch và các thiết bị mạng vật lý khác.

Tôi muốn cho phép chúng ta xem xét một số công cụ đã đề cập trước đó nhưng cũng thực hành và học cách tự động hóa cấu hình mạng của chúng ta.

Khi nói đến các tùy chọn, có một vài lựa chọn mà chúng ta có thể chọn.

- [GNS3 VM](https://www.gns3.com/software/download-vm)
- [Eve-ng](https://www.eve-ng.net/)
- [Unimus](https://unimus.net/) Không phải là môi trường thử nghiệm nhưng là một khái niệm thú vị.

Chúng ta sẽ xây dựng phòng thí nghiệm của mình bằng [Eve-ng](https://www.eve-ng.net/) như đã đề cập trước đó, bạn có thể sử dụng thiết bị vật lý nhưng để nói thật, môi trường ảo có nghĩa là chúng ta có thể có một môi trường sandbox để thử nghiệm nhiều kịch bản khác nhau. Ngoài ra, có thể chơi với các thiết bị và cấu trúc liên kết khác nhau có thể là điều thú vị.

Chúng ta sẽ làm mọi thứ trên EVE-NG với phiên bản cộng đồng.

#### Bắt đầu
Phiên bản cộng đồng có sẵn dưới dạng ISO và OVF để [tải xuống](https://www.eve-ng.net/index.php/download/)

Chúng ta sẽ sử dụng bản tải xuống OVF nhưng với ISO, có tùy chọn xây dựng trên máy chủ bare metal mà không cần hypervisor.
![Tải xuống Eve](/Workshop001/images/5.PythonForNetworkAutomation/001-downloadEve.png) 

Đối với hướng dẫn của chúng ta, chúng ta sẽ sử dụng VMware Workstation vì tôi có giấy phép thông qua vExpert của mình nhưng bạn cũng có thể sử dụng VMware Player hoặc bất kỳ tùy chọn nào khác được đề cập trong [tài liệu](https://www.eve-ng.net/index.php/documentation/installation/system-requirement/). Rất tiếc, chúng ta không thể sử dụng Virtual box mà chúng ta đã sử dụng trước đó!

Đây cũng là nơi tôi đã gặp vấn đề với GNS3 với Virtual Box mặc dù được hỗ trợ.

[Tải xuống VMware Workstation Player - MIỄN PHÍ](https://www.vmware.com/uk/products/workstation-player.html)

[VMware Workstation PRO](https://www.vmware.com/uk/products/workstation-pro.html) Cũng lưu ý rằng có giai đoạn đánh giá miễn phí!

#### Cài đặt trên VMware Workstation PRO
Bây giờ chúng ta đã tải xuống và cài đặt phần mềm hypervisor của mình, và chúng ta đã tải xuống EVE-NG OVF. Nếu bạn đang sử dụng VMware Player, vui lòng cho tôi biết nếu quy trình này giống nhau.

Bây giờ chúng ta đã sẵn sàng để cấu hình mọi thứ.

Mở VMware Workstation và sau đó chọn `file` và `open`
![Thiết lập VMware](/Workshop001/images/5.PythonForNetworkAutomation/002-vMware.png) 

Khi bạn tải xuống EVE-NG OVF Image, nó sẽ nằm trong một file nén. Giải nén nội dung ra thành một thư mục riêng để nó trông giống như thế này.
![Thiết lập VMware](/Workshop001/images/5.PythonForNetworkAutomation/003-vMware.png) 

Điều hướng đến vị trí nơi bạn đã tải xuống EVE-NG OVF image và bắt đầu nhập.

Đặt cho nó một tên dễ nhận biết và lưu trữ máy ảo ở đâu đó trên hệ thống của bạn.
![Thiết lập VMware](/Workshop001/images/5.PythonForNetworkAutomation/004-vMware.png) 

Khi quá trình nhập hoàn tất, hãy tăng số lượng bộ xử lý lên 4 và bộ nhớ được phân bổ lên 8 GB. (Điều này sẽ được thực hiện sau khi nhập với phiên bản mới nhất, nếu không thì hãy chỉnh sửa cài đặt VM)

Ngoài ra, hãy đảm bảo rằng hộp kiểm Virtualise Intel VT-x/EPT hoặc AMD-V/RVI được bật. Tùy chọn này hướng dẫn VMware workstation chuyển các cờ ảo hóa sang hệ điều hành khách (ảo hóa lồng nhau) Đây là vấn đề tôi đang gặp phải với GNS3 với Virtual Box mặc dù CPU của tôi cho phép điều này.

![Thiết lập VMware](/Workshop001/images/5.PythonForNetworkAutomation/005-vMware.png) 

### Bật nguồn & Truy cập
Lưu ý & Đường vòng: Nhớ rằng tôi đã đề cập rằng điều này sẽ không hoạt động với VirtualBox! Vâng, tôi đã gặp vấn đề tương tự với VMware Workstation và EVE-NG nhưng không phải do lỗi của nền tảng ảo hóa!

Tôi đang chạy WSL2 trên Máy Windows của mình và điều này dường như loại bỏ khả năng chạy bất cứ thứ gì lồng nhau trong môi trường của bạn. Tôi bối rối vì sao VM Ubuntu lại chạy vì nó dường như loại bỏ khía cạnh ảo hóa Intel VT-d của CPU khi sử dụng WSL2.

Để giải quyết vấn đề này, chúng ta có thể chạy lệnh sau trên máy Windows của mình và khởi động lại hệ thống, lưu ý rằng trong khi tắt thì bạn sẽ không thể sử dụng WSL2.

`bcdedit /set hypervisorlaunchtype off`

Khi bạn muốn quay lại và sử dụng WSL2, bạn sẽ cần chạy lệnh này và khởi động lại.

`bcdedit /set hypervisorlaunchtype auto`

Cả hai lệnh này đều phải được chạy với quyền quản trị!

Ok quay lại chương trình, Bây giờ bạn nên có một máy đã được bật trong VMware Workstation và bạn nên có một lời nhắc trông giống như thế này.
![Eve-NG - Thiết lập](/Workshop001/images/5.PythonForNetworkAutomation/006-eVE-ng.png) 

Trên lời nhắc trên bạn có thể sử dụng:

tên người dùng = root mật khẩu = eve

Sau đó bạn sẽ được yêu cầu cung cấp lại mật khẩu root, điều này sẽ được sử dụng để SSH vào máy chủ sau này.

Sau đó chúng ta có thể thay đổi tên máy chủ.
![Eve-NG - Thiết lập](/Workshop001/images/5.PythonForNetworkAutomation/007-eVE-ng.png) 

Tiếp theo, chúng ta xác định Tên miền DNS, tôi đã sử dụng tên dưới đây nhưng tôi không chắc liệu điều này có cần thay đổi sau này hay không.
![Eve-NG - Thiết lập](/Workshop001/images/5.PythonForNetworkAutomation/008-eVE-ng.png) 

Sau đó chúng ta cấu hình mạng, tôi chọn static để địa chỉ IP được cấp sẽ được giữ nguyên sau khi khởi động lại.
![Eve-NG - Thiết lập](/Workshop001/images/5.PythonForNetworkAutomation/009-eVE-ng.png) 

Bước cuối cùng, cung cấp địa chỉ IP tĩnh từ mạng có thể truy cập được từ máy trạm của bạn.
![Eve-NG - Thiết lập](/Workshop001/images/5.PythonForNetworkAutomation/010-eVE-ng.png) 

Có một số bước bổ sung ở đây nơi bạn sẽ phải cung cấp mặt nạ mạng con cho mạng của mình, cổng mặc định và DNS.

Khi hoàn tất, nó sẽ khởi động lại, khi nó hoạt động trở lại, bạn có thể lấy địa chỉ IP tĩnh của mình và đặt nó vào trình duyệt của bạn.
![Bảng điều khiển đăng nhập EVE](/Workshop001/images/5.PythonForNetworkAutomation/011-eVE-ng.png) 

Tên người dùng mặc định cho GUI là `admin` và mật khẩu là `eve` trong khi tên người dùng mặc định cho SSH là `root` và mật khẩu là `eve` nhưng điều này đã được thay đổi nếu bạn đã thay đổi trong quá trình thiết lập.
![Bảng điều khiển đăng nhập EVE](/Workshop001/images/5.PythonForNetworkAutomation/012-eVE-ng.png) 

Tôi đã chọn HTML5 cho bảng điều khiển thay vì native vì điều này sẽ mở một tab mới trong trình duyệt của bạn khi bạn đang điều hướng qua các bảng điều khiển khác nhau.
