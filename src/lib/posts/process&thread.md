---
title: "Tiến trình & Luồng: Hiểu Biết và Ứng Dụng"
date: "2025-5-5"
categories: ["hệ thống phân tán", "hệ điều hành", "lập trình"]
excerpt: "Tiến trình và luồng là hai khái niệm nền tảng trong quản lý và tối ưu hóa hiệu suất hệ thống. Bài viết này giải thích về tiến trình, luồng, sự khác biệt và ứng dụng thực tế của chúng trong lĩnh vực CNTT."
coverImage: "/images/a.png"
---

# Tiến trình & Luồng: Hiểu Biết và Ứng Dụng

Trong lĩnh vực công nghệ thông tin (CNTT), tiến trình (process) và luồng (thread) là hai khái niệm nền tảng để quản lý và tối ưu hóa hiệu suất hệ thống. Bài blog này sẽ giải thích rõ ràng về tiến trình, luồng, sự khác biệt, ứng dụng thực tế, và một số bài toán phổ biến sử dụng chúng trong CNTT, dựa trên ghi chú hệ thống phân tán. Ngoài ra, bài viết sẽ tích hợp các nghiên cứu về bài toán đa luồng/đa tiến trình, trường hợp sử dụng, và cách hệ thống phân tán được ứng dụng trong huấn luyện AI như ChatGPT.

## Tiến trình (Process) là gì?

Tiến trình là một chương trình đang chạy trên bộ xử lý ảo của hệ điều hành. Khi mở một ứng dụng như trình duyệt Chrome, nó trở thành một tiến trình, sử dụng CPU, bộ nhớ, và các tài nguyên khác. Mỗi tiến trình có không gian bộ nhớ riêng, đảm bảo tính độc lập và an toàn.

**Ví dụ:**
Mở Chrome, Word, và Excel cùng lúc, mỗi ứng dụng là một tiến trình riêng.

## Luồng (Thread) là gì?
![Minh họa sự khác biệt tiến trình và luồng](/images/luong.png)
Luồng là đơn vị thực thi nhỏ hơn trong một tiến trình. Nhiều luồng trong cùng tiến trình chia sẻ không gian bộ nhớ, giúp chúng hoạt động hiệu quả hơn so với tiến trình. Một tiến trình có thể có một hoặc nhiều luồng.

**Ví dụ:**
Trong ứng dụng máy tính, một luồng quản lý giao diện người dùng, luồng khác thực hiện tính toán, cả hai chia sẻ dữ liệu đầu vào/đầu ra.

## Sự khác biệt giữa Tiến trình và Luồng

![Minh họa sự khác biệt tiến trình và luồng](/images/diff.png)

## Quản lý Tiến trình và Luồng trong Hệ thống

Hệ điều hành sử dụng chuyển đổi ngữ cảnh (context switching) để chạy nhiều tiến trình và luồng trên số lõi CPU hạn chế. Ví dụ, một máy tính với 16 lõi CPU và 32 bộ xử lý logic có thể quản lý 234 tiến trình và 5200 luồng nhờ chuyển đổi ngữ cảnh.

Hệ điều hành cũng sử dụng:

- **Bộ xử lý ảo**: Chia CPU vật lý thành các CPU ảo, giúp tiến trình chạy như trên CPU độc lập.
- **Bộ nhớ ảo**: Dùng ổ đĩa làm bộ nhớ tạm để mở rộng RAM.

## Cách quản lý Luồng

Luồng được quản lý theo ba cách:

- **Chế độ người dùng (User Mode)**: Luồng do ứng dụng quản lý, nhưng nếu một luồng bị chặn (ví dụ, chờ I/O), toàn bộ tiến trình có thể bị đình trệ.
- **Chế độ hạt nhân (Kernel Mode)**: Hệ điều hành quản lý luồng, xử lý I/O và lên lịch độc lập, nhưng phức tạp hơn.
- **Tiến trình nhẹ (LWP)**: Kết hợp ưu điểm của cả hai, được coi là tiến trình nhỏ nhưng chia sẻ bộ nhớ như luồng. LWP phổ biến trong hệ thống hiện đại.

## Luồng trong Hệ thống Phân tán

Trong mô hình client-server, luồng rất quan trọng để xử lý đồng thời nhiều yêu cầu. Có ba kiến trúc server đa luồng:

- **Thread-per-request**: Tạo luồng mới cho mỗi yêu cầu, phù hợp với yêu cầu ngắn nhưng tốn tài nguyên khi tải cao.
- **Thread-per-connection**: Gắn luồng với mỗi kết nối client, như trong ứng dụng chat.
- **Thread-per-object**: Gắn luồng với các dịch vụ (như Payment Service), phù hợp với hệ thống thương mại điện tử.

**Ví dụ:** Một server có bộ điều phối (dispatcher) nhận yêu cầu và chuyển đến luồng xử lý phù hợp, đảm bảo hiệu quả.

## Khi nào nên dùng Tiến trình, Luồng, hay cả hai?

![Minh họa tiến trình và luồng](/images/anh.jpg)



## 12 Bài toán phổ biến trong CNTT sử dụng Đa luồng/Đa tiến trình

1. **Web Server**: Sử dụng đa luồng (thread-per-request) để xử lý đồng thời các yêu cầu HTTP như tải trang, gửi comment.

2. **Ứng dụng Chat**: Dùng thread-per-connection để quản lý kết nối người dùng, mỗi luồng xử lý tin nhắn riêng.

3. **Hệ thống thương mại điện tử**: Dùng cả tiến trình (quản lý dịch vụ như thanh toán, xác thực) và luồng (xử lý yêu cầu người dùng).

4. **Huấn luyện mô hình AI**: Đa tiến trình để phân chia tính toán trên nhiều CPU/node, như trong OpenMPI.

5. **Xử lý video**: Đa tiến trình để mã hóa video, phân tích âm thanh độc lập, tối ưu CPU.

6. **Trình duyệt Web**: Mỗi tab là một tiến trình riêng để cô lập lỗi; luồng trong tab xử lý giao diện và tải nội dung.

7. **Cơ sở dữ liệu**: Đa luồng để xử lý truy vấn đồng thời từ nhiều người dùng (I/O-bound).

8. **Game đa người chơi**: Luồng xử lý hành động người chơi (I/O-bound); tiến trình quản lý vật lý game (CPU-bound).

9. **Hệ thống xử lý log**: Đa luồng đọc và phân tích log từ nhiều nguồn (I/O-bound).

10. **Ứng dụng máy tính khoa học**: Đa tiến trình để thực hiện tính toán song song, như mô phỏng vật lý.

11. **Hệ thống nhúng**: Luồng xử lý tín hiệu từ cảm biến (I/O-bound); tiến trình cho các tác vụ độc lập.

12. **Streaming video**: Luồng xử lý truyền dữ liệu mạng (I/O-bound); tiến trình mã hóa video (CPU-bound).

## Huấn luyện ChatGPT với Hệ thống Phân tán

Huấn luyện các mô hình AI lớn như ChatGPT đòi hỏi xử lý khối lượng dữ liệu khổng lồ, sử dụng hệ thống phân tán với đa tiến trình. Theo nghiên cứu, quá trình huấn luyện thường được thực hiện trên các cụm máy tính với hàng nghìn GPU, sử dụng các framework như TensorFlow hoặc PyTorch. Dữ liệu được chia thành các phần nhỏ, mỗi phần được xử lý bởi một tiến trình riêng trên một node (tương tự cách dùng OpenMPI). Các tiến trình này đồng bộ hóa tham số mô hình qua mạng, đảm bảo tính nhất quán.

Quy trình cơ bản:

1. **Chia dữ liệu**: Dữ liệu huấn luyện (văn bản, hình ảnh) được chia nhỏ và phân phối cho các node.
2. **Đa tiến trình**: Mỗi node chạy một tiến trình để huấn luyện một phần dữ liệu, tận dụng GPU/CPU.
3. **Đồng bộ hóa**: Các tiến trình trao đổi gradient qua mạng để cập nhật mô hình.
4. **Tối ưu hóa**: Sử dụng kỹ thuật như data parallelism và model parallelism để tăng tốc.

Nguồn tham khảo:
- [Distributed Training with TensorFlow](https://www.tensorflow.org/guide/distributed_training)
- [Distributed Training with lifewire](https://www.lifewire.com/large-language-model-7724669)

## Kết luận

Tiến trình và luồng là nền tảng của hệ thống máy tính và lập trình hiện đại. Tiến trình cung cấp sự độc lập, trong khi luồng mang lại hiệu quả và khả năng đồng thời. Hiểu rõ khi nào nên dùng tiến trình, luồng, hay cả hai, cùng với việc áp dụng chúng trong các bài toán CNTT như web server, AI, hay hệ thống thương mại điện tử, là chìa khóa để xây dựng hệ thống hiệu suất cao. Hy vọng bài blog này giúp bạn nắm rõ hơn về hai khái niệm quan trọng này và cách chúng được ứng dụng thực tế!

