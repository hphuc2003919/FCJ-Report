---
title: "Blog 1"
date: 2025-09-09
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---
# Phát trực tuyến trò chơi Windows bằng Proton 9 trên Amazon GameLift Streams

Người chơi mong đợi trải nghiệm tức thì, nhấp-là-chơi trên mọi thiết bị, và Amazon GameLift Streams giúp khách hàng xây dựng những trải nghiệm này cho cả trò chơi lẫn các trường hợp sử dụng ứng dụng phát trực tuyến. Trong khi việc chơi game truyền thống thường phụ thuộc vào hệ điều hành Windows, Amazon GameLift Streams có thể chạy các trò chơi hoặc ứng dụng dựa trên Windows trên môi trường chạy Windows hoặc Proton.

**Proton** là một lớp tương thích cho phép các tệp thực thi Windows chạy trên các hệ điều hành dựa trên Linux. Proton thực hiện được điều này bằng cách dịch các lệnh gọi API của Windows, bao gồm cả đồ họa và đầu vào, sang các lệnh tương đương trên Linux, giúp các nhà phát triển tận dụng máy chủ Linux cho những khối lượng công việc trước đây bị giới hạn trên Windows.

Với cách tiếp cận này, bạn có thể giảm chi phí hạ tầng lên đến 63% khi chạy trò chơi trên cùng chế độ thuê và vẫn duy trì một hiệu suất tương đương với môi trường chạy Windows. Linux cũng cho phép bạn sử dụng chế độ đa thuê và chạy hai luồng từ một GPU duy nhất, từ đó giảm chi phí hơn nữa.

Chúng tôi xin thông báo sự có mặt của **Proton 9** như một tùy chọn môi trường chạy cho Amazon GameLift Streams, cải thiện khả năng tương thích với các bản build Windows hơn bao giờ hết. Chúng tôi sẽ đi sâu hơn vào cách Proton 9 hoạt động và cách bạn có thể sử dụng nó để giảm chi phí phát trực tuyến trò chơi hoặc ứng dụng Windows đến người dùng của bạn.

## Các khái niệm về Amazon GameLift Streams

**Amazon GameLift Streams** giúp bạn phát trực tuyến trò chơi ở độ phân giải lên đến 1080p và 60 khung hình mỗi giây trên bất kỳ thiết bị nào có trình duyệt. Với hạ tầng toàn cầu của AWS và các phiên bản GPU, bạn có thể triển khai và phát trực tuyến trò chơi của mình trong vài phút mà không cần chỉnh sửa, và người chơi có thể bắt đầu chơi chỉ sau vài giây mà không phải chờ cài đặt. Amazon GameLift Streams sử dụng một số thuật ngữ và cấu trúc quan trọng để cho phép thiết lập nhanh hơn và quản lý luồng dễ dàng hơn. Hiểu những thuật ngữ này sẽ giúp bạn cấu hình các tùy chọn sau một cách chính xác:

- **Môi trường chạy** (Runtime environment): Hệ điều hành và phần mềm nền tảng chạy trên các phiên bản Amazon Elastic Compute Cloud (Amazon EC2) để vận hành ứng dụng của bạn. Các tùy chọn bao gồm: Windows, Ubuntu và Proton.

- **Lớp luồng** (Stream class): Xác định loại phiên bản Amazon EC2 và số lượng luồng chạy trên một phiên bản.

- **Nhóm luồng** (Stream group): Một cấu trúc bao gồm ứng dụng, lớp luồng và dung lượng luồng của bạn.

- **Dung lượng luồng** (Stream capacity): Một giá trị số biểu thị số lượng phiên phát trực tuyến mà nhóm luồng có thể chạy đồng thời.

## Hiểu về Proton

Proton là một lớp tương thích mã nguồn mở được phát triển bởi Valve phối hợp với CodeWeavers nhằm cho phép các trò chơi Windows chạy trên hệ thống Linux. Cốt lõi của Proton dựa trên Wine Is Not an Emulator (Wine), công cụ cung cấp khả năng dịch API của Windows. Tuy nhiên, Wine thường gặp khó khăn với đồ họa 3D hiện đại, khiến việc sử dụng nó cho các trò chơi 3D tiên tiến trở nên thiếu ổn định.

Proton tăng cường khả năng của Wine bằng cách cung cấp một lớp dịch nâng cao từ DirectX sang Vulkan (DXVK). Nó dịch các lệnh gọi API đồ họa đặc thù của Windows (DirectX) sang các API đồ họa chạy trên Linux (Vulkan). DXVK hỗ trợ dịch DirectX 9, 10 và 11. Đối với DirectX 12, vkd3d-Proton được bổ sung như một cầu dịch bổ sung. Với những hệ thống này, Proton có thể chuyển đổi các lệnh gọi API đồ họa và phi đồ họa mới nhất của Windows thành các thao tác tương đương trên Linux và Vulkan.

![Figure 1](/images/Blog1-Image-1.png)
> *Hình 1. Sơ đồ hệ thống gọi đến lớp dịch nào.*

Amazon GameLift Streams đóng gói các phiên bản Proton được tùy chỉnh: 8.0-2c, 8.0-5, và mới nhất là 9.0-2 (2024), được tối ưu hóa đặc biệt cho hạ tầng nền tảng và công nghệ phát trực tuyến.

## Ưu điểm kỹ thuật và kinh tế

Việc sử dụng môi trường chạy Proton 9 trong Amazon GameLift Streams thay vì môi trường chạy Windows mang lại lợi ích vượt xa việc tiết kiệm chi phí bản quyền. Các lớp luồng chạy Windows, chẳng hạn như `gen5n_win2022`, phát sinh chi phí bản quyền Windows Server 2022 và chỉ hoạt động ở chế độ đơn thuê (single tenant). Trong chế độ này, mỗi máy chỉ có thể phục vụ một phiên phát trực tuyến duy nhất.

Ngược lại, một nhóm luồng sử dụng lớp luồng dựa trên Linux có thể hoạt động ở chế độ đa thuê; ví dụ, một `gen5n_high` có thể phục vụ hai phiên phát trực tuyến từ một GPU duy nhất, đồng thời loại bỏ chi phí bản quyền. Phiên bản Amazon EC2 nền tảng vẫn dành riêng cho bạn ngay cả khi chạy nhiều phiên phát trực tuyến trên cùng một máy. Đối với các trò chơi hoặc ứng dụng ít yêu cầu tài nguyên hơn, Proton 9 có thể là một cơ chế quan trọng để tối ưu hóa chi phí hạ tầng tổng thể.

Biểu đồ (Hình 2) so sánh chi phí cho mỗi giờ phát trực tuyến giữa các lớp luồng khác nhau tại Khu vực AWS Ohio, với mỗi cột được gắn nhãn theo lớp và tỷ lệ thuê (1:1 hoặc 2:1). Biểu đồ trực quan cho thấy các lớp dựa trên Linux sử dụng Proton 9 hỗ trợ đa thuê (2:1), giúp giảm chi phí bằng cách cho phép nhiều phiên phát trực tuyến trên mỗi máy và loại bỏ phí bản quyền Windows.

![Figure 2](/images/Blog1-Image-2.png)
> *Hình 2: So sánh chi phí cho mỗi giờ phát trực tuyến của các lớp luồng tại Ohio.*

## Kiểm thử khả năng tương thích trò chơi với Proton 9

Tuy nhiên, việc chuyển sang Proton 9 không phải là không có những cân nhắc kỹ thuật. Một số phần mềm chống gian lận (anti-cheat) yêu cầu cấu hình tương thích với Linux hoặc một bản build không tích hợp Anti-Cheat. Bất kỳ hoạt động nào ở cấp nhân (kernel) có thể cần các cấu hình cụ thể. Hơn nữa, trò chơi của bạn có thể sử dụng các thao tác không thể dịch hoàn hảo để sử dụng với API đồ họa Vulkan.

Nếu bạn gặp sự cố tương thích với môi trường chạy Proton, chúng tôi khuyến nghị trước tiên hãy thử bản Proton 9 mới nhất có sẵn trong Amazon GameLift Streams. Nếu vẫn gặp vấn đề, chúng tôi cung cấp hướng dẫn về cách thiết lập một môi trường Amazon EC2 tương đương để kiểm thử và gỡ lỗi các sự cố tương thích với Proton.

## Các phương pháp tối ưu hóa chi phí bổ sung

Việc sử dụng Proton 9 là một cách tuyệt vời để chia sẻ GPU và loại bỏ chi phí bản quyền Windows, cho phép bạn lựa chọn lớp luồng phù hợp nhất với nhu cầu trò chơi. Các tính năng tối ưu chi phí đặc biệt quan trọng đối với các trường hợp hướng tới người tiêu dùng, và Amazon GameLift Streams có thêm nhiều chức năng giúp khách hàng quản lý chi phí cho các trường hợp sử dụng phát trực tuyến.

Điều quan trọng là phải biết dung lượng luồng (stream capacity) của bạn. Dung lượng luồng là khi khách hàng có thể đặt số lượng luồng có sẵn ngay lập tức thông qua lệnh gọi API hoặc qua Bảng điều khiển quản lý AWS. Việc đặt dung lượng luồng bằng hoặc gần với số lượng luồng bạn cần có nghĩa là bạn sẽ không phải trả cho dung lượng thừa. Bạn có thể tăng hoặc giảm dung lượng một cách thủ công, hoặc tự động bằng cách gọi API của Amazon GameLift Streams dựa trên các sự kiện (chẳng hạn như số lượng người chơi tăng, hoặc theo khung thời gian nhất định (ví dụ: cùng một giờ mỗi ngày)).

Đối với các trường hợp sử dụng mà người dùng có thể chờ đến 5 phút để luồng khởi chạy (thường là các trường hợp nội bộ doanh nghiệp), khách hàng có thể sử dụng dung lượng luồng theo nhu cầu. Đây là cơ chế khi dung lượng luồng chỉ được khởi tạo khi có yêu cầu phát, và sẽ được giải phóng khi luồng kết thúc. Điều này có nghĩa là khách hàng chỉ trả tiền cho dung lượng luồng khi nó được yêu cầu bởi người dùng và chỉ trong thời gian phiên phát đó diễn ra.

## Kết luận

Môi trường chạy Proton 9 mới mang đến khả năng tương thích rộng hơn với DirectX 12 và khắc phục các vấn đề đã được phát hiện ở các phiên bản trước đó. Khi kết hợp với các lớp luồng mới nhất trên Amazon GameLift Streams, bạn có thể tối ưu chi phí phát trực tuyến các tựa game AAA, và giảm thêm nữa nhờ tùy chọn đa thuê nếu yêu cầu hiệu năng của trò chơi cho phép.

Hãy liên hệ với đại diện AWS để biết thêm chi tiết về cách chúng tôi có thể giúp tăng tốc hoạt động kinh doanh của bạn.