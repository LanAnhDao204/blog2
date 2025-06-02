---
title: "Định danh"
date: "2025-05-18"
categories: ["hệ thống phân tán"]
excerpt: "Định danh"
coverImage: "/images/dd.webp"
---
## Bài 1
![Minh họa bai 1](/images/dinhdanh.jpg)

## Bài 2
## **1. Các nhà cung cấp dịch vụ Internet (ISP) tại Việt Nam**

Tại Việt Nam, những nhà mạng lớn cung cấp dịch vụ Internet bao gồm:

- **VNPT (Vinaphone)** – thuộc Tập đoàn Bưu chính Viễn thông Việt Nam.
- **Viettel** – thuộc Bộ Quốc phòng, có hạ tầng rộng khắp.
- **FPT Telecom** – một trong những nhà cung cấp dịch vụ internet dân dụng hàng đầu.
- **SCTV, Mobifone, CMC Telecom** – cung cấp internet cho hộ gia đình và doanh nghiệp.

---

## **2. Vì sao một số website bị chặn ở Việt Nam nhưng truy cập được ở nước ngoài?**

Hiện tượng này xảy ra vì một số lý do sau:

### **Chính sách kiểm duyệt nội dung (Content Filtering):**
- Nhà nước có thể yêu cầu các ISP **chặn một số trang web vi phạm pháp luật Việt Nam**, bao gồm:
  - Nội dung khiêu dâm, phản động, cờ bạc, v.v.
  - Các nền tảng vi phạm bản quyền hoặc an ninh mạng.

### **Do yêu cầu từ phía doanh nghiệp, quốc tế hoặc vì lý do kỹ thuật:**
- Một số dịch vụ như Spotify, ChatGPT, Netflix… có **giới hạn khu vực địa lý** do bản quyền hoặc chính sách thương mại.
- Nhà mạng có thể **chặn DNS** hoặc chặn IP của một số máy chủ.

---

## **3. DNS là gì và tại sao đổi DNS có thể truy cập được website bị chặn?**

### **DNS (Domain Name System)** là hệ thống giúp "dịch" tên miền như `www.google.com` thành địa chỉ IP để máy tính truy cập.

### Khi truy cập web:
1. Trình duyệt gửi yêu cầu đến máy chủ DNS (thường là của nhà mạng).
2. Nếu website nằm trong danh sách bị chặn, máy chủ DNS của nhà mạng sẽ trả về lỗi hoặc không phản hồi.

##  **4. Đổi DNS sang 8.8.8.8 hoặc 1.1.1.1 có tác dụng gì?
- **8.8.8.8**: DNS công cộng của **Google**
- **1.1.1.1**: DNS của **Cloudflare** – nhanh, riêng tư

###  Khi đổi DNS sang các địa chỉ này:
- Trình duyệt **bỏ qua DNS của nhà mạng**, thay vào đó hỏi Google/Cloudflare để phân giải tên miền.
- Nhờ vậy, **vượt qua được cơ chế chặn ở tầng DNS**, giúp truy cập website bình thường.

 **Lưu ý**: Việc đổi DNS **không vượt được** mọi loại chặn, chẳng hạn như chặn ở tầng IP (deep packet inspection) hoặc tường lửa quốc gia.

##  **5. Cách đổi DNS đơn giản trên máy tính hoặc điện thoại**
###  Windows:
- Vào: `Control Panel → Network & Internet → Change Adapter Settings`
- Chuột phải → `Properties` → chọn `Internet Protocol Version 4 (TCP/IPv4)`
- Đổi DNS thành:  
  - Preferred DNS: `8.8.8.8`  
  - Alternate DNS: `8.8.4.4`

### Trên Android/iOS:
- Vào Wi-Fi settings → Advanced → đổi DNS thủ công thành `1.1.1.1` hoặc `8.8.8.8`

## **Kết luận**
Việc truy cập Internet không đơn thuần là nhập tên miền. Các lớp trung gian như DNS, IP routing, hay chính sách từ nhà mạng đều có thể ảnh hưởng. Việc hiểu rõ cách hoạt động của DNS sẽ giúp chúng ta sử dụng Internet một cách thông minh, linh hoạt và an toàn hơn.