---
title: "Mô Hình OSI - 7 Lớp"
date: "`r Sys.Date()`"
weight: 2
chapter: false
pre: "<b> 2. </b>"
---

Nội dung dưới đây chủ yếu đến từ loạt bài "Networking Fundamentals" của Practical Networking. Nếu bạn thích nội dung này dưới dạng video, hãy xem hai video sau:

- [Mô Hình OSI: Góc Nhìn Thực Tiễn - Lớp 1 / 2 / 3](https://www.youtube.com/watch?v=LkolbURrtTs&list=PLIFyRwBY_4bRLmKfP1KnZA6rZbRHtxmXi&index=4)
- [Mô Hình OSI: Góc Nhìn Thực Tiễn - Lớp 4 / 5+](https://www.youtube.com/watch?v=0aGqGKrRE0g&list=PLIFyRwBY_4bRLmKfP1KnZA6rZbRHtxmXi&index=4)

### Mô Hình OSI - 7 Lớp
Mục đích tổng thể của ngành mạng là cho phép hai máy chủ chia sẻ dữ liệu. Trước khi có mạng, nếu tôi muốn lấy dữ liệu từ máy chủ này sang máy chủ khác, tôi phải cắm một cái gì đó vào máy chủ này, mang nó đến máy chủ kia và cắm vào máy chủ đó.

Mạng cho phép chúng ta tự động hóa điều này bằng cách cho phép máy chủ chia sẻ dữ liệu tự động qua dây dẫn. Để làm điều này, chúng phải tuân theo một tập hợp quy tắc.

Điều này không khác gì với bất kỳ ngôn ngữ nào. Tiếng Anh có một tập hợp quy tắc mà hai người nói tiếng Anh phải tuân theo. Tiếng Tây Ban Nha có bộ quy tắc riêng. Tiếng Pháp có bộ quy tắc riêng, trong khi mạng cũng có bộ quy tắc riêng.

Các quy tắc cho mạng được chia thành bảy lớp khác nhau và các lớp đó được gọi là mô hình OSI.

#### Giới Thiệu Về Mô Hình OSI
Mô Hình OSI (Mô Hình Kết Nối Hệ Mở) là một khung công tác được sử dụng để mô tả các chức năng của một hệ thống mạng. Mô hình OSI phân loại các chức năng máy tính thành một tập hợp các quy tắc và yêu cầu chung để hỗ trợ khả năng tương tác giữa các sản phẩm và phần mềm khác nhau. Trong mô hình tham chiếu OSI, các giao tiếp giữa một hệ thống máy tính được chia thành bảy lớp trừu tượng khác nhau: **Vật lý, Liên kết Dữ liệu, Mạng, Vận chuyển, Phiên, Trình bày, và Ứng dụng.**

![Mô Hình OSI](/images/2.OSIModel/001-theOSIModel.png)

#### Lớp Vật Lý
Lớp 1 trong mô hình OSI được gọi là vật lý, đề cập đến việc truyền dữ liệu từ một máy chủ này sang máy chủ khác thông qua một phương tiện, có thể là cáp vật lý hoặc Wi-Fi. Chúng ta cũng có thể thấy một số phần cứng cũ như hub và repeater để vận chuyển dữ liệu từ một máy chủ này sang máy chủ khác.
![Lớp Vật Lý](/images/2.OSIModel/002-physical.png)

#### Lớp Liên Kết Dữ Liệu
Lớp 2, lớp liên kết dữ liệu cho phép chuyển giao dữ liệu từ nút này sang nút khác, nơi dữ liệu được đóng gói thành các khung. Cũng có một mức độ sửa lỗi có thể xảy ra tại lớp vật lý. Đây cũng là nơi chúng ta lần đầu tiên thấy địa chỉ MAC.
![Lớp Liên Kết Dữ Liệu](/images/2.OSIModel/003-dataLink.png)

#### Lớp Mạng
Có lẽ bạn đã nghe thuật ngữ switch lớp 3 hoặc switch lớp 2. Trong mô hình OSI, Lớp 3, Mạng, có mục tiêu là cung cấp dịch vụ từ đầu đến cuối, đây là nơi chúng ta thấy địa chỉ IP được đề cập.
![Lớp Mạng](/images/2.OSIModel/004-network.png)

Vậy tại sao chúng ta cần các sơ đồ địa chỉ ở cả Lớp 2 và Lớp 3? (Địa chỉ MAC so với Địa chỉ IP)

Khi chúng ta nghĩ về việc đưa dữ liệu từ một máy chủ này sang máy chủ khác, mỗi máy chủ có một địa chỉ IP nhưng có nhiều switch và router ở giữa. Mỗi thiết bị có địa chỉ MAC lớp 2.

Địa chỉ MAC lớp 2 sẽ đi từ máy chủ tới switch/router, nó tập trung vào các bước nhảy, trong khi địa chỉ IP lớp 3 sẽ đi cùng với gói dữ liệu cho đến khi nó đến máy chủ đích. (Từ đầu đến cuối)

Địa chỉ IP - Lớp 3 = Dịch vụ từ đầu đến cuối

Địa chỉ MAC - Lớp 2 = Dịch vụ từng bước nhảy

#### Lớp Vận Chuyển
Dịch vụ giao hàng giữa các dịch vụ, Lớp 4 được thiết kế để phân biệt các luồng dữ liệu. Tương tự như cách mà Lớp 3 và Lớp 2 có các sơ đồ địa chỉ của riêng chúng, ở Lớp 4 chúng ta có các cổng.
![Lớp Vận Chuyển](/images/2.OSIModel/005-transport.png)

#### Lớp Phiên, Trình Bày, Ứng Dụng
Sự phân biệt giữa các Lớp 5, 6, 7 đã trở nên khá mơ hồ.

Đáng để xem xét [Mô Hình TCP/IP](https://www.geeksforgeeks.org/tcp-ip-model/) để có được sự hiểu biết gần đây hơn.

Bây giờ hãy cùng giải thích những gì đang xảy ra khi các máy chủ giao tiếp với nhau bằng cách sử dụng ngăn xếp mạng này. Máy chủ nguồn sẽ có một ứng dụng tạo ra dữ liệu mà dự kiến sẽ được gửi đến một máy chủ khác.

Máy chủ nguồn sẽ trải qua quá trình gọi là quá trình đóng gói. Dữ liệu sẽ được gửi đến lớp 4.

Lớp 4 sẽ thêm một tiêu đề vào dữ liệu để thực hiện mục tiêu của lớp 4 là giao hàng giữa các dịch vụ. Điều này sẽ là một cổng sử dụng TCP hoặc UDP. Nó cũng sẽ bao gồm cổng nguồn và cổng đích.

Đoạn dữ liệu này được gọi là một segment (dữ liệu và cổng).

Segment này sẽ được chuyển xuống ngăn xếp OSI đến lớp 3, lớp mạng, và lớp mạng sẽ thêm một tiêu đề khác vào dữ liệu này. Tiêu đề này sẽ thực hiện mục tiêu của lớp 3 là dịch vụ từ đầu đến cuối, nghĩa là trong tiêu đề này bạn sẽ có địa chỉ IP nguồn và địa chỉ IP đích, tiêu đề cộng với dữ liệu cũng có thể được gọi là một gói.

Lớp 3 sẽ lấy gói đó và chuyển nó cho lớp 2, lớp 2 sẽ lại thêm một tiêu đề khác vào dữ liệu đó để hoàn thành mục tiêu của lớp 2 là giao hàng từng bước nhảy, nghĩa là tiêu đề này sẽ bao gồm địa chỉ MAC nguồn và địa chỉ MAC đích. Điều này được gọi là một khung khi bạn có tiêu đề lớp 2 và dữ liệu.
![Mô Hình OSI - Ứng Dụng](/images/2.OSIModel/006-application.png)

Tôi đã đề cập ở trên về cái tên cho mỗi lớp của tiêu đề cộng với dữ liệu nhưng đã quyết định vẽ nó ra như sau.
![Mô Hình OSI - Dữ Liệu](/images/2.OSIModel/007-application.png)

Dữ liệu đến từ một ứng dụng đang được gửi đi, vì vậy việc nhận dữ liệu sẽ diễn ra ngược lại để đưa nó lên ngăn xếp và vào máy chủ nhận.
![Mô Hình OSI - Ứng Dụng](/images/2.OSIModel/008-application.png)