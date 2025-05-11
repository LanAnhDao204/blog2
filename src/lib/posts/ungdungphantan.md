---
title: "Hệ Thống Phân Tán"
date: "2025-04-28"
categories: ["hệ thống phân tán", "công nghệ phần mềm"]
excerpt: "Hệ thống phân tán ngày càng đóng vai trò quan trọng trong việc xây dựng các ứng dụng lớn và phức tạp. Bài viết này sẽ cung cấp cái nhìn tổng quan về hệ thống phân tán, các khái niệm và thuật ngữ quan trọng, cùng với một ví dụ minh họa."
coverImage: "/images/htpt.png"
---

# Hệ Thống Phân Tán Là Gì?

Hệ thống phân tán là một hệ thống bao gồm nhiều máy tính, các node, hoặc các thành phần phần mềm khác nhau, được kết nối với nhau qua mạng và phối hợp làm việc để thực hiện một nhiệm vụ chung. Các hệ thống này thường không chia sẻ bộ nhớ chung, mà thay vào đó, mỗi thành phần trong hệ thống có thể có bộ nhớ và tài nguyên riêng của nó. Mặc dù các thành phần này phân tán, nhưng chúng hoạt động như một hệ thống duy nhất để xử lý các yêu cầu từ người dùng.

Một cách hiểu đơn giản, hệ thống phân tán giống như một đội làm việc: mỗi thành viên có nhiệm vụ riêng (phân tán), nhưng họ giao tiếp và phối hợp để hoàn thành mục tiêu chung.

# Các Ứng Dụng Của Hệ Thống Phân Tán

Hệ thống phân tán được sử dụng trong nhiều ứng dụng và lĩnh vực khác nhau, bao gồm:

1. **Internet và World Wide Web**: Là một hệ thống phân tán khổng lồ với hàng triệu máy chủ và máy khách kết nối với nhau.
2. **Điện toán đám mây**: AWS, Google Cloud, Microsoft Azure cung cấp dịch vụ dựa trên các hệ thống phân tán quy mô lớn.
3. **Mạng xã hội**: Facebook, Twitter, Instagram xử lý hàng tỷ tương tác người dùng trên các máy chủ phân tán toàn cầu.
4. **Hệ thống phân phối nội dung (CDN)**: Akamai, Cloudflare giúp phân phối nội dung web nhanh chóng đến người dùng trên toàn cầu.
5. **Hệ thống IoT (Internet of Things)**: Kết nối hàng tỷ thiết bị thông minh với nhau và với các hệ thống xử lý dữ liệu.

# Các Khái Niệm Chính Của Hệ Thống Phân Tán

- **Scalability (Khả năng mở rộng)**: Khả năng hệ thống đáp ứng với việc tăng tải công việc bằng cách thêm tài nguyên. Một hệ thống có khả năng mở rộng tốt sẽ hoạt động hiệu quả khi quy mô tăng lên.
- **Fault Tolerance (Khả năng chịu lỗi)**: Khả năng hệ thống tiếp tục hoạt động đúng ngay cả khi một số thành phần gặp sự cố. Hệ thống phân tán cần được thiết kế để duy trì dịch vụ dù có lỗi xảy ra.
- **Availability (Tính sẵn sàng)**: Tỷ lệ thời gian hệ thống hoạt động và sẵn sàng phục vụ yêu cầu. Thường được đo bằng phần trăm (ví dụ: 99.99% uptime).
- **Transparency (Tính trong suốt)**: Khả năng che giấu sự phức tạp và phân tán của hệ thống khỏi người dùng và ứng dụng. Người dùng chỉ thấy một hệ thống đơn nhất, không cần biết về các chi tiết bên trong.
- **Concurrency (Tính đồng thời)**: Khả năng xử lý nhiều tác vụ cùng một lúc. Trong hệ thống phân tán, nhiều thành phần có thể hoạt động đồng thời, yêu cầu cơ chế điều phối.
- **Parallelism (Tính song song)**: Thực hiện nhiều phép tính cùng một lúc, phân chia một vấn đề lớn thành các phần nhỏ hơn để xử lý đồng thời trên nhiều máy tính.
- **Openness (Tính mở)**: Khả năng mở rộng và tích hợp các thành phần mới vào hệ thống, thường thông qua việc sử dụng các tiêu chuẩn và giao thức mở.
- **Vertical Scaling (Mở rộng theo chiều dọc)**: Nâng cấp phần cứng của một máy chủ hiện có (thêm CPU, RAM, ổ cứng) để tăng hiệu suất.
- **Horizontal Scaling (Mở rộng theo chiều ngang)**: Thêm nhiều máy chủ vào hệ thống để phân phối tải. Phương pháp này thường linh hoạt và hiệu quả hơn so với mở rộng theo chiều dọc.
- **Load Balancer (Cân bằng tải)**: Thành phần phân phối tải công việc đến nhiều máy chủ để tối ưu hóa việc sử dụng tài nguyên, tăng thông lượng và giảm thời gian phản hồi.
- **Replication (Sao chép)**: Tạo và duy trì bản sao của dữ liệu hoặc dịch vụ trên nhiều máy chủ để tăng độ tin cậy, khả năng chịu lỗi và hiệu suất.

# Ví Dụ Và Giải Thích Các Thuật Ngữ

Giả sử chúng ta có một dịch vụ web lớn, nơi người dùng có thể tải lên và tải xuống các tệp. Hệ thống phân tán có thể được sử dụng để xử lý các yêu cầu này.

- **Scalability**: Khi lượng người dùng tăng lên, chúng ta có thể mở rộng hệ thống bằng cách thêm nhiều server (Horizontal Scaling).
- **Fault Tolerance**: Nếu một server gặp sự cố, các server khác vẫn có thể tiếp tục cung cấp dịch vụ nhờ vào việc sao chép dữ liệu giữa các node.
- **Availability**: Hệ thống luôn sẵn sàng phục vụ người dùng, ngay cả khi có một số server gặp sự cố, nhờ vào việc cân bằng tải và sao chép.
- **Transparency**: Người dùng không cần quan tâm đến việc hệ thống phân tán được triển khai như thế nào hoặc ở đâu; mọi thứ đều hoạt động như một hệ thống duy nhất.
- **Concurrency**: Hệ thống có thể xử lý nhiều yêu cầu đồng thời từ các người dùng khác nhau.
- **Parallelism**: Khi một tệp lớn được tải lên, hệ thống có thể chia nhỏ tệp đó và xử lý chúng song song trên nhiều server.
- **Openness**: Hệ thống có thể tích hợp các công nghệ khác nhau và tương thích với nhiều nền tảng khác nhau.
- **Vertical Scaling**: Chúng ta có thể nâng cấp một server đơn lẻ để tăng tốc độ xử lý.
- **Horizontal Scaling**: Thêm nhiều server vào hệ thống để chia sẻ gánh nặng và cải thiện hiệu suất.
- **Load Balancer**: Phân phối các yêu cầu tải tệp đều đặn cho tất cả các server trong hệ thống để tránh tình trạng quá tải.
- **Replication**: Dữ liệu tệp có thể được sao chép trên nhiều server để đảm bảo rằng người dùng có thể truy cập tệp ngay cả khi một server bị lỗi.

# Kiến Trúc Của Hệ Thống Phân Tán

Kiến trúc của hệ thống phân tán có thể rất đa dạng, tùy thuộc vào mục đích sử dụng và các yêu cầu của hệ thống. Dưới đây là một số mô hình kiến trúc phổ biến:

1. **Kiến trúc Client-Server**: Trong mô hình này, các client gửi yêu cầu đến server, và server xử lý các yêu cầu này. Hệ thống có thể mở rộng bằng cách thêm nhiều server.
![Minh họa Kiến trúc Client-Server](/images/cilents-server.webp)
   
2. **Kiến trúc Peer-to-Peer (P2P)**: Các node trong hệ thống phân tán hoạt động như peer, chia sẻ tài nguyên và xử lý yêu cầu mà không cần một server trung tâm.
![Minh họa Kiến trúc p2p](/images/p2p.png)

3. **Kiến trúc Serverless**: Nhà cung cấp đám mây quản lý tài nguyên, người dùng chỉ viết mã. Ví dụ: AWS Lambda, Google Cloud Functions.
![Minh họa Kiến trúc svl](/images/svl.webp)

4. **Kiến trúc Microservices**: Các dịch vụ nhỏ độc lập, mỗi dịch vụ thực hiện một tác vụ cụ thể và giao tiếp với nhau qua API. Kiến trúc này rất phổ biến trong các hệ thống phân tán hiện đại.
![Minh họa Kiến trúc Microservices](/images/mcrs.webp)

# Ví dụ : Kiến trúc của Netflix
Netflix sử dụng kiến trúc microservices với hơn 700 dịch vụ độc lập:
![Minh họa Kiến trúc Microservices](/images/cloud-netflix-1.jpeg)

- **API Gateway**: Điểm vào duy nhất cho tất cả các yêu cầu từ thiết bị người dùng.
- **Dịch vụ khuyến nghị**: Phân tích dữ liệu người dùng để đề xuất nội dung.
- **Dịch vụ streaming**: Phụ trách việc cung cấp video đến người dùng.
- **Dịch vụ thanh toán**: Xử lý giao dịch và thanh toán tự động.
- **CDN**: Sử dụng mạng phân phối nội dung toàn cầu để đưa video đến gần người dùng.


