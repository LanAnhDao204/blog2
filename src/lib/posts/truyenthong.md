
---
title: "Truyền thông"
date: "2025-5-10"
categories: ["hệ thống phân tán", "hệ điều hành", "lập trình"]
excerpt: 
coverImage: "/images/traodoitt.jpg"
---
# Bài 1 :
1. **Giới thiệu chung** 
![Minh họa RabbitMQ](/images/RabbitMQ.jpg)

    Trong các hệ thống phần mềm hiện đại, đặc biệt là những hệ thống được thiết kế theo kiến trúc phân tán, việc đảm bảo luồng thông tin giữa các thành phần diễn ra hiệu quả và đáng tin cậy là vô cùng quan trọng. RabbitMQ là một trong những hệ thống hàng đợi thông điệp (message broker) được sử dụng rộng rãi nhất hiện nay. Nó cho phép các ứng dụng giao tiếp với nhau thông qua cơ chế gửi và nhận thông điệp một cách bất đồng bộ, giúp tách rời các thành phần và tăng tính linh hoạt cho toàn hệ thống. 

2. **Chức năng chính của RabbitMQ**
    - **Trung gian truyền thông điệp**: RabbitMQ hoạt động như một trạm trung chuyển, giúp các thành phần của hệ thống không cần phải kết nối trực tiếp với nhau.
    - **Hàng đợi tin nhắn (Queue):**: Nó cung cấp các hàng đợi để lưu trữ tạm thời các tin nhắn trước khi chúng được chuyển đến ứng dụng nhận.
    - **Xử lý bất đồng bộ**: Cho phép các tác vụ được thực hiện độc lập mà không làm nghẽn luồng chính, từ đó cải thiện hiệu suất và độ phản hồi của hệ thống.
    - **Định tuyến linh hoạt**: Thông qua các thành phần gọi là Exchange (như direct, topic, fanout), RabbitMQ có khả năng định tuyến thông điệp đến đúng nơi cần nhận một cách thông minh. 
    - **Đảm bảo độ tin cậy**: RabbitMQ cung cấp các cơ chế để xác nhận việc gửi và nhận thông điệp, cũng như khả năng lưu trữ bền vững để đảm bảo không mất mát dữ liệu.

3. **Cơ chế hoạt động**
![Minh họa cơ chế hoạt động RabbitMQ](/images/cochehoatdong.png)
    - (1) Producer đẩy message vào Exchange. Khi tạo Exchange, bạn phải mô tả nó thuộc loại gì. Các loại Exchange sẽ được giải thích phía dưới.
    - (2) Sau khi Exchange nhận Message, nó chịu trách nhiệm định tuyến message. Exchange sẽ chịu trách nhiệm về các thuộc tính của Message, ví dụ routing key, loại Exchange.
    - (3) Việc binding phải được tạo từ Exchange đến Queue (hàng đợi). Trong trường hợp này, ta sẽ có hai binding đến hai hàng đợi khác nhau từ một Exchange. Exchange sẽ định tuyến Message vào các hàng đợi dựa trên thuộc tính của của từng Message.
    - (4) Các Message nằm ở hàng đợi đến khi chúng được xử lý bởi một Consumer.
    - (5) Consumer xử lý Message nhận từ Queue.  
4. **Các loại Exchange trong RabbitMQ**  
    RabbitMQ cung cấp nhiều loại Exchange khác nhau để đáp ứng các kịch bản định tuyến đa dạng:
![Minh họa các loại exchange](/images/m.png)
5. **Ưu điểm của RabbitMQ**  
• Hỗ trợ đa ngôn ngữ: Có thư viện client cho nhiều ngôn ngữ lập trình 
phổ biến như Python, Java, Node.js (JavaScript), .NET, Go, PHP, và 
nhiều ngôn ngữ khác.  
• Giao diện quản lý trực quan: Cung cấp một giao diện web 
(Management Plugin) cho phép người dùng dễ dàng theo dõi, quản lý và 
cấu hình RabbitMQ.   
• Cấu hình linh hoạt và khả năng mở rộng: Dễ dàng cấu hình để phù 
hợp với nhiều yêu cầu khác nhau và có thể mở rộng quy mô bằng cách 
clustering.   
• Tính năng bảo mật: Hỗ trợ xác thực người dùng, phân quyền chi tiết và 
mã hóa SSL/TLS.   
• Quản lý hàng đợi nâng cao: Cung cấp các tính năng như Dead Letter 
Exchanges để xử lý các thông điệp không thành công, cơ chế retry, 
message TTL (Time-To-Live).  
6. **Cài đặt**  
Một trong những cách tiện lợi và nhanh chóng để cài đặt RabbitMQ cho mục 
đích phát triển và thử nghiệm là sử dụng Docker.  
**a. Cài đặt bằng Docker:**     
    Mở cửa sổ dòng lệnh (Terminal, Command Prompt hoặc PowerShell) và thực thi lệnh sau:   
    docker run -d --hostname my-rabbit --name rabbitmq-server \   

    -p 5672:5672 -p 15672:15672 \  

    rabbitmq:3-management   

    content_copydownload  

![Minh họa ](/images/e.png)  

**b. Truy cập giao diện Web:**    
Sau khi container Docker đã khởi chạy, bạn có thể truy cập giao diện quản lý của RabbitMQ qua trình duyệt web:   
• **Địa chỉ**: http://localhost:15672  
• **Tài khoản mặc định**: guest   
• **Mật khẩu mặc định**: guest  
![Minh họa ](/images/f.png)  

**c. Các cổng mặc định quan trọng:**   
• **5672**: Cổng giao tiếp chính sử dụng giao thức AMQP, dành cho Producer 
và Consumer kết nối đến RabbitMQ.   
• **15672**: Cổng dành cho giao diện quản lý web (Management Plugin).   
7. **Ứng dụng thực tế của RabbitMQ**  
RabbitMQ được ứng dụng rộng rãi trong nhiều loại hệ thống và kịch bản khác 
nhau:   
• Gửi email thông báo hoặc các tác vụ nền khác sau khi người dùng thực 
hiện một hành động (ví dụ: đăng ký tài khoản, đặt hàng).   
• Xử lý các quy trình phức tạp như đặt hàng và thanh toán trong các hệ 
thống thương mại điện tử, đảm bảo các bước được thực hiện tuần tự và 
tin cậy.   
• Truyền thông điệp giữa các microservices trong một kiến trúc ứng dụng 
lớn.   
• Thu thập, tổng hợp và chuyển tiếp log hoặc các sự kiện từ nhiều nguồn 
khác nhau đến các hệ thống phân tích hoặc lưu trữ tập trung.   

8. **Kết luận**  
RabbitMQ là một giải pháp message broker mạnh mẽ và linh hoạt, đóng vai trò 
quan trọng trong việc xây dựng các hệ thống phân tán hiện đại. Với khả năng 
định tuyến thông minh, cơ chế xử lý bất đồng bộ và các tính năng đảm bảo độ 
tin cậy, RabbitMQ giúp các nhà phát triển cải thiện đáng kể hiệu suất, độ ổn 
định và khả năng mở rộng của ứng dụng. Việc tìm hiểu và nắm vững RabbitMQ 
mang lại nhiều lợi thế trong việc thiết kế và triển khai các giải pháp phần mềm 
hiệu quả. 
# Bài 3 :
1. **Tổng Quan về RPC và Thư Viện JSON**  
Remote Procedure Call (RPC) là một giao thức cho phép gọi hàm từ xa qua mạng. Trong RPC, client gửi yêu cầu gọi hàm kèm tham số, và server xử lý, trả về kết quả. Thư viện xmlrpc sử dụng XML để mã hóa dữ liệu, nhưng XML thường nặng và phức tạp. JSON (JavaScript Object Notation), với đặc điểm nhẹ và dễ đọc, đã thúc đẩy sự phát triển của JSON-RPC như một giải pháp thay thế.   
**Các Thư Viện RPC Hỗ Trợ JSON**  
Ngoài xmlrpc, một số thư viện hỗ trợ JSON bao gồm:   
• **jsonrpclib (Python)**: Thư viện đơn giản, hỗ trợ JSON-RPC 1.0 và 2.0, 
phù hợp cho ứng dụng Python.   
• **json-rpc (JavaScript)**: Dùng trong ứng dụng web, hỗ trợ JSON-RPC 
qua HTTP hoặc WebSocket.   
• **Apache Thrift**: Framework đa ngôn ngữ, hỗ trợ JSON-RPC và tự sinh 
code.   
• **gRPC**: Hỗ trợ JSON như tùy chọn mã hóa, tối ưu cho hệ thống hiệu 
năng cao.   
• **web3.js (JavaScript)**: Chuyên cho blockchain, sử dụng JSON-RPC để 
giao tiếp với node.     
Tôi sẽ dùng thư viện **jsonrpclib** cho bài này.   
2. **JSON-RPC và thư viện Jonrpclib**  
JSON-RPC là giao thức RPC sử dụng JSON để mã hóa yêu cầu và phản hồi, hoạt động qua HTTP, WebSocket, hoặc TCP. Cấu trúc yêu cầu gồm:   
    • jsonrpc: Phiên bản (thường là "2.0").   
    • method: Tên hàm gọi.   
    • params: Tham số truyền vào.   
    • id: Định danh yêu cầu.   
**Thư viện jsonrpclib** : là thư viện Python hỗ trợ JSON-RPC, cung cấp:   
    • Tương thích JSON-RPC 1.0 và 2.0.   
    • SimpleJSONRPCServer để tạo server dễ dàng.   
    • Hỗ trợ parser JSON hiệu quả (như simplejson). 

Một số hình ảnh demo:

![Minh họa demo](/images/b.png)  
<div style="text-align: center;">Khởi chạy server</div>


![Minh họa các demo](/images/c.png)  
<div style="text-align: center;">Gửi yêu cầu từ phía client</div>

3. **Kết luận** 
JSON-RPC là một giải pháp RPC hiệu quả, tận dụng JSON để giảm độ phức tạp và tăng tốc độ so với XML-RPC. Thư viện jsonrpclib-pelix cung cấp cách triển khai đơn giản. 