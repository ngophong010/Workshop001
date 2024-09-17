---
title: "Tự động hóa mạng"
date: "`r Sys.Date()`"
weight: 4
chapter: false
pre: " <b> 4. </b> "
---
### Tự động hóa mạng
#### Kiến thức cơ bản về tự động hóa mạng
Các động lực chính cho Tự động hóa Mạng
- Đạt được tính linh hoạt
- Giảm chi phí
- Loại bỏ lỗi
- Đảm bảo tuân thủ
- Quản lý tập trung

Quá trình áp dụng tự động hóa là cụ thể cho từng doanh nghiệp. Không có một giải pháp chung nào khi triển khai tự động hóa; khả năng xác định và áp dụng phương pháp phù hợp nhất cho tổ chức của bạn là rất quan trọng để tiến tới duy trì hoặc tạo ra một môi trường linh hoạt hơn. Luôn luôn tập trung vào giá trị kinh doanh và trải nghiệm người dùng cuối. (Chúng tôi đã đề cập đến điều gì đó tương tự ngay từ đầu về toàn bộ DevOps và sự thay đổi văn hóa mà quy trình tự động hóa này mang lại.)

Để phân tích điều này, bạn cần xác định cách nhiệm vụ hoặc quy trình mà bạn đang cố gắng tự động hóa sẽ đạt được và cải thiện trải nghiệm người dùng cuối hoặc giá trị kinh doanh trong khi tuân theo một phương pháp có hệ thống từng bước.

"Nếu bạn không biết bạn đang đi đâu, bất kỳ con đường nào cũng sẽ đưa bạn đến đó."

Hãy có một khung hoặc cấu trúc thiết kế mà bạn đang cố gắng đạt được, biết được mục tiêu cuối cùng của bạn và sau đó làm việc từng bước để đạt được mục tiêu đó, đo lường sự thành công của tự động hóa ở các giai đoạn khác nhau dựa trên kết quả kinh doanh.

Xây dựng các khái niệm được mô hình hóa xung quanh các ứng dụng hiện có; không cần thiết kế các khái niệm xung quanh tự động hóa trong một không gian kín, vì chúng cần được áp dụng cho ứng dụng, dịch vụ và cơ sở hạ tầng hiện tại của bạn.

#### Cách tiếp cận Tự động hóa Mạng
Chúng ta nên xác định các nhiệm vụ và thực hiện khám phá các yêu cầu thay đổi mạng để có được các vấn đề và sự cố phổ biến nhất cần tự động hóa giải pháp cho chúng.

- Lập danh sách tất cả các yêu cầu thay đổi và quy trình làm việc hiện đang được xử lý thủ công.
- Xác định các hoạt động phổ biến, tốn thời gian và dễ xảy ra lỗi nhất.
- Ưu tiên các yêu cầu theo cách tiếp cận dựa trên kinh doanh.
- Đây là khung cho việc xây dựng một quy trình tự động hóa, những gì cần tự động hóa và những gì không cần.

Chúng ta cũng nên chia nhỏ các nhiệm vụ và phân tích cách các chức năng mạng khác nhau hoạt động và tương tác với nhau.

- Nhóm hạ tầng/Mạng nhận các vé thay đổi ở nhiều lớp để triển khai ứng dụng.
- Dựa trên dịch vụ mạng, chia chúng thành các lĩnh vực khác nhau và hiểu cách chúng tương tác với nhau.
   + Tối ưu hóa ứng dụng
   + ADC (Bộ điều khiển phân phối ứng dụng)
   + Tường lửa
   + DDI (DNS, DHCP, IPAM, v.v.)
   + Định tuyến
   + Khác
- Xác định các phụ thuộc khác nhau để giải quyết sự khác biệt về doanh nghiệp và văn hóa và mang lại sự hợp tác giữa các nhóm.

Chính sách có thể tái sử dụng, định nghĩa và đơn giản hóa các nhiệm vụ dịch vụ có thể tái sử dụng, quy trình và đầu vào/đầu ra.

- Định nghĩa các dịch vụ cho các quy trình khác nhau và đầu vào/đầu ra.
- Đơn giản hóa quy trình triển khai sẽ giảm thời gian ra thị trường cho cả khối lượng công việc mới và hiện có.
- Khi bạn có một quy trình tiêu chuẩn, nó có thể được sắp xếp và căn chỉnh với các yêu cầu cá nhân để có được phương pháp tiếp cận đa luồng và phân phối.

Kết hợp các chính sách với các hoạt động cụ thể cho doanh nghiệp. Việc triển khai chính sách này giúp ích cho doanh nghiệp như thế nào? Tiết kiệm thời gian? Tiết kiệm chi phí? Cung cấp kết quả kinh doanh tốt hơn?

- Đảm bảo rằng các nhiệm vụ dịch vụ có thể tương tác.
- Liên kết các nhiệm vụ dịch vụ gia tăng để tạo ra các dịch vụ kinh doanh.
- Cho phép linh hoạt để liên kết và tái liên kết các nhiệm vụ dịch vụ theo nhu cầu.
- Triển khai khả năng tự phục vụ và mở đường cho hiệu quả hoạt động cải thiện.
- Cho phép nhiều kỹ năng công nghệ khác nhau tiếp tục đóng góp với sự giám sát và tuân thủ.

**Lặp lại** các chính sách và quy trình, thêm vào và cải tiến trong khi duy trì tính khả dụng và dịch vụ.

- Bắt đầu nhỏ bằng cách tự động hóa các nhiệm vụ hiện có.
- Làm quen với quy trình tự động hóa, để bạn có thể xác định các lĩnh vực khác có thể hưởng lợi từ tự động hóa.
- Lặp lại các sáng kiến tự động hóa của bạn, thêm tính linh hoạt từng bước trong khi duy trì tính khả dụng cần thiết.
- Phương pháp tiếp cận từng phần mở đường cho thành công!

Orchestrate dịch vụ mạng!

- Cần tự động hóa quy trình triển khai để cung cấp ứng dụng nhanh chóng.
- Tạo ra một môi trường dịch vụ linh hoạt đòi hỏi phải quản lý nhiều yếu tố khác nhau giữa các kỹ năng công nghệ.
- Chuẩn bị cho việc điều phối toàn diện cung cấp kiểm soát đối với tự động hóa và thứ tự triển khai.

### Công cụ Tự động hóa Mạng
Tin tốt là hầu hết các công cụ chúng ta sử dụng cho Tự động hóa Mạng thường giống như các công cụ chúng ta sẽ sử dụng cho các lĩnh vực tự động hóa khác hoặc những gì chúng ta đã đề cập cho đến nay hoặc sẽ đề cập trong các phiên sau.

Hệ điều hành - Như tôi đã đề cập trong suốt thử thách này, tôi tập trung vào việc học chủ yếu với hệ điều hành Linux, lý do này đã được trình bày trong phần Linux, nhưng gần như tất cả các công cụ mà chúng ta sẽ đề cập, mặc dù là ứng dụng đa hệ điều hành, đều bắt đầu là các ứng dụng hoặc công cụ dựa trên Linux.

Môi trường phát triển tích hợp (IDE) - Một lần nữa không có gì nhiều để nói ở đây ngoài việc tôi sẽ gợi ý Visual Studio Code làm IDE của bạn, dựa trên các plugin phong phú có sẵn cho nhiều ngôn ngữ khác nhau.

Quản lý cấu hình - Chúng ta chưa đến phần quản lý cấu hình, nhưng rất rõ ràng rằng Ansible là một lựa chọn ưa thích trong lĩnh vực này để quản lý và tự động hóa cấu hình. Ansible được viết bằng Python nhưng bạn không cần phải biết Python.

- Không cần agent
- Chỉ yêu cầu SSH
- Cộng đồng hỗ trợ lớn
- Nhiều mô-đun mạng
- Chỉ mô hình đẩy
- Cấu hình bằng YAML
- Mã nguồn mở!

[Liên kết đến các mô-đun mạng Ansible](https://docs.ansible.com/ansible/2.9/modules/list_of_network_modules.html)

Chúng ta cũng sẽ đề cập đến **Ansible Tower** trong phần quản lý cấu hình, hãy xem đây là giao diện GUI cho Ansible.

CI/CD - Một lần nữa chúng ta sẽ đề cập nhiều hơn về các khái niệm và công cụ xung quanh điều này, nhưng điều quan trọng là ít nhất nên đề cập đến vì nó không chỉ bao gồm mạng mà còn tất cả việc cung cấp dịch vụ và nền tảng.

Cụ thể, Jenkins cung cấp hoặc có vẻ là một công cụ phổ biến cho Tự động hóa Mạng.

- Giám sát kho git để phát hiện thay đổi và sau đó khởi động chúng.

Kiểm soát phiên bản - Một lần nữa, chúng ta sẽ tìm hiểu sâu hơn sau này.

- Git cung cấp kiểm soát phiên bản mã của bạn trên thiết bị cục bộ - Đa nền tảng
- GitHub, GitLab, BitBucket, v.v. là các trang web trực tuyến nơi bạn xác định kho lưu trữ và tải mã của bạn lên.

Ngôn ngữ | Kịch bản - Một điều mà chúng ta chưa đề cập ở đây là Python như một ngôn ngữ, tôi quyết định khám phá Go thay vì nhờ vào hoàn cảnh của mình, tôi sẽ nói rằng đó là một sự lựa chọn gần như ngang nhau giữa Golang và Python và Python dường như là lựa chọn hàng đầu cho Tự động hóa Mạng.

- Nornir là một điều cần đề cập ở đây, một khung tự động hóa được viết bằng Python. Điều này dường như thay thế Ansible nhưng cụ thể cho Tự động hóa Mạng. Tài liệu Nornir

Phân tích API - Postman là một công cụ tuyệt vời để phân tích các API RESTful. Giúp xây dựng, kiểm tra và sửa đổi API.

- POST >>> Để tạo các đối tượng tài nguyên.
- GET >>> Để lấy một tài nguyên.
- PUT >>> Để tạo hoặc thay thế các tài nguyên.
- PATCH >>> Để tạo hoặc cập nhật đối tượng tài nguyên.
- DELETE >>> Để xóa một tài nguyên.

[Liên kết tải công cụ Postman](https://www.postman.com/downloads/)

#### Các công cụ khác cần đề cập
[Cisco NSO (Bộ điều phối Dịch vụ Mạng)](https://www.cisco.com/c/en/us/products/cloud-systems-management/network-services-orchestrator/index.html)

[NetYCE - Đơn giản hóa Tự động hóa Mạng](https://netyce.com/)

[Tự động hóa Kiểm tra Mạng](https://pubhub.devnetcloud.com/media/genie-feature-browser/docs/#/)