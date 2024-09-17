---
title : "Giới thiệu"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 1. </b> "
---
#### NetDevOps là gì | Network DevOps?
Có thể bạn cũng đã nghe đến các thuật ngữ **Network DevOps** hoặc **NetDevOps**. Có thể bạn đã là một kỹ sư mạng và hiểu rõ về các thành phần mạng trong hạ tầng mà bạn làm việc, cũng như hiểu các yếu tố liên quan đến mạng như DHCP, DNS, NAT, v.v. Bạn cũng sẽ có kiến thức vững về các tùy chọn mạng phần cứng hoặc phần mềm, switch, router, v.v.

Tuy nhiên, nếu bạn không phải là kỹ sư mạng, thì chúng ta cần có kiến thức cơ bản trong một số lĩnh vực đó để có thể hiểu được mục tiêu cuối cùng của **Network DevOps**.

Về mặt các thuật ngữ này, chúng ta có thể coi **NetDevOps** hoặc **Network DevOps** là việc áp dụng các nguyên tắc và thực tiễn DevOps vào mạng, áp dụng kiểm soát phiên bản và các công cụ tự động hóa vào việc tạo dựng, kiểm tra, giám sát và triển khai mạng.

Nếu chúng ta nghĩ về **Network DevOps** như một yêu cầu về tự động hóa, chúng ta đã đề cập trước đây rằng DevOps phá vỡ các rào cản giữa các đội nhóm. Nếu các đội nhóm mạng không thay đổi sang một mô hình và quy trình tương tự, thì họ sẽ trở thành nút thắt cổ chai hoặc thậm chí là điểm thất bại tổng thể.

Việc sử dụng các nguyên tắc tự động hóa xung quanh cung cấp, cấu hình, kiểm tra, kiểm soát phiên bản và triển khai là một khởi đầu tuyệt vời. Tự động hóa sẽ giúp tăng tốc độ triển khai, đảm bảo tính ổn định của hạ tầng mạng và cải thiện liên tục, cũng như quy trình này có thể được chia sẻ qua nhiều môi trường một khi chúng đã được kiểm tra. Ví dụ như một chính sách mạng đã được kiểm tra hoàn toàn trên một môi trường có thể được sử dụng nhanh chóng ở một vị trí khác nhờ tính chất của nó là mã thay vì một quy trình được viết tay như trước đây. Một cái nhìn và phác thảo thật tuyệt vời về tư duy này có thể được tìm thấy tại đây. [Network DevOps](https://www.thousandeyes.com/learning/techtorials/network-devops)

### Cơ Bản về Mạng
Hãy quên đi khía cạnh DevOps để bắt đầu và bây giờ chúng ta cần xem xét rất ngắn gọn về một số kiến thức cơ bản về mạng.
#### Thiết bị mạng
Nếu bạn thích nội dung này dưới dạng video, hãy xem các video từ Practical Networking:

- [Thiết bị mạng - Hosts, Địa chỉ IP, Mạng - Cơ bản về mạng - Bài 1a](https://www.youtube.com/watch?v=bj-Yfakjllc&list=PLIFyRwBY_4bRLmKfP1KnZA6rZbRHtxmXi&index=1)
- [Thiết bị mạng - Hub, Bridge, Switch, Router - Cơ bản về mạng - Bài 1b](https://www.youtube.com/watch?v=H7-NR3Q3BeI&list=PLIFyRwBY_4bRLmKfP1KnZA6rZbRHtxmXi&index=3)

**Host** là bất kỳ thiết bị nào gửi hoặc nhận lưu lượng.

![Host](/Workshop001/images/1.introduce/001-host.png) 

**Địa chỉ IP** là danh tính của mỗi host.

![Địa chỉ IP](/Workshop001/images/1.introduce/002-IPAddress.png) 

**Mạng** là cái gì đó vận chuyển lưu lượng giữa các host. Nếu không có mạng, sẽ có rất nhiều chuyển động dữ liệu thủ công!

Một nhóm logic của các host cần có kết nối tương tự.

![Mạng](/Workshop001/images/1.introduce/003-network.png) 

**Switch** tạo điều kiện cho việc giao tiếp **trong** một mạng. Một switch chuyển tiếp các gói dữ liệu giữa các host. Một switch gửi gói đến trực tiếp các host.

- Mạng: Một nhóm các host cần có kết nối tương tự.
- Các host trên một mạng chia sẻ cùng một không gian địa chỉ IP.

![Switch](/Workshop001/images/1.introduce/004-switches.png) 

**Router** tạo điều kiện cho việc giao tiếp giữa các mạng. Như chúng ta đã nói trước đó, một switch quản lý giao tiếp trong một mạng, trong khi router cho phép chúng ta kết nối các mạng này với nhau hoặc ít nhất là cho phép chúng truy cập lẫn nhau nếu được phép.

Một router có thể cung cấp một điểm kiểm soát lưu lượng (bảo mật, lọc, chuyển tiếp). Ngày càng có nhiều switch cũng cung cấp một số chức năng này.

Router học các mạng mà chúng được kết nối. Những mạng này được gọi là tuyến đường, bảng định tuyến là tất cả các mạng mà router biết đến.

Một router có một địa chỉ IP trong các mạng mà nó được kết nối. Địa chỉ IP này cũng sẽ là cách mà mỗi host ra khỏi mạng cục bộ của chúng, còn được gọi là cổng vào (gateway).

Router cũng tạo ra sự phân cấp trong các mạng mà tôi đã đề cập trước đó.

![Router](/Workshop001/images/1.introduce/005-router.png) 

### Switch so với Router
**Định tuyến** là quá trình di chuyển dữ liệu giữa các mạng.
- Một router là một thiết bị có mục đích chính là định tuyến.

**Chuyển mạch** là quá trình di chuyển dữ liệu trong các mạng.
- Một Switch là một thiết bị có mục đích chính là chuyển mạch.

Đây là cái nhìn tổng quan cơ bản về các thiết bị, vì chúng ta biết rằng có nhiều loại thiết bị mạng khác nhau như:
- Điểm truy cập (Access Points)
- Tường lửa (Firewalls)
- Bộ cân bằng tải (Load Balancers)
- Switch lớp 3 (Layer 3 Switches)
- IDS / IPS
- Proxy
- Switch ảo (Virtual Switches)
- Router ảo (Virtual Routers)

Mặc dù tất cả những thiết bị này đều thực hiện định tuyến và/hoặc chuyển mạch.