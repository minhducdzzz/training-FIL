# 1.2) The network edge
### 🌐 Access Network
- là mạng ==kết nối== các thiết bị ở rìa mạng (edge devices) vào ==router đầu tiên== để đi vào internet rộng lớn hơn. Đôi khi, nó còn kết nối cả một mạng gia đình vào internet.
- Có ba loại mạng truy cập chính:

==Residential access networks==
==Institutional access networks==: Do công ty, trường học, hoặc chính quyền điều hành.
==Mobile access networks==: Do các nhà mạng di động và mạng Wi-Fi cung cấp.
### 🏠 Mạng Truy Cập Cáp (Cable Access Networks)
- Trong mạng truy cập cáp, một ==cáp vật lý== kết nối nhiều nhà đến một ==head end== cáp duy nhất. Tín hiệu từ các nhà được gửi trên cáp ở các tần số khác nhau để tránh nhiễu.

- ==Frequency Division Multiplexing (FDM)==: Một phương pháp mà các tín hiệu được gửi ở các tần số khác nhau để tránh nhiễu.

- Tuy nhiên, vì số lượng tần số có hạn, người dùng cáp thường phải chia sẻ tần số với hàng xóm.

- Mạng truy cập cáp thường ==bất đối xứng (asymmetric)==, có nghĩa là tốc độ tải xuống (downstream) nhanh hơn tốc độ tải lên (upstream), phản ánh xu hướng tiêu thụ dữ liệu nhiều hơn sản xuất dữ liệu.

==Tốc độ tải xuống==: 40 Mbps - 1.2 Gbps
=Tốc độ tải lên==: 30 - 100 Mbps
### 📞 Mạng Đường Dây Thuê Bao Số (Digital Subscriber Line - DSL)
- Mạng DSL sử dụng đường dây điện thoại hiện có (cặp dây xoắn) để cung cấp dịch vụ internet. Các dây DSL kết nối trực tiếp bạn với ==central office (văn phòng trung tâm)==.

- Tương tự như mạng cáp, DSL cũng bất đối xứng, với tốc độ tải xuống nhanh hơn tốc độ tải lên.
Tốc độ tải xuống: 24 - 52 Mbps
Tốc độ tải lên: 3.5 - 16 Mbps
### 🏡 Mạng Gia Đình Tiêu Biểu
##### Một mạng gia đình điển hình có thể bao gồm:

- ==Đường truyền DSL hoặc cáp==: Từ nhà cung cấp dịch vụ.
- ==Modem cáp hoặc DSL== (modulator demodulator): Kết nối với router.
- ==Router==: Có cả kết nối có dây (Ethernet) và không dây (Wi-Fi) đến các thiết bị trong nhà.
    - ==Ethernet==: 100 Mbps - 1 Gbps
    - ==Wi-Fi==: Hàng chục đến hàng trăm Mbps
### 📶 Mạng Không Dây (Wireless Networks)
Có hai loại mạng không dây chính:

- ==Mạng không dây cục bộ (Local wireless networks)==: Ví dụ: Wi-Fi.
- ==Mạng diện rộng (Wide area networks)==: Ví dụ: Mạng di động 3G, 4G, 5G.
### 🏢 Mạng Doanh Nghiệp (Enterprise Networks)
- Mạng doanh nghiệp có thể giống như mạng gia đình "nâng cấp". Chúng có thể bao gồm cả Ethernet có dây và Wi-Fi không dây. Điểm khác biệt chính là mạng doanh nghiệp thường có nhiều switch và router để xử lý số lượng lớn thiết bị kết nối.
### Host
Khi một ==host== muốn gửi dữ liệu, ví dụ như một file lớn, nó sẽ chia dữ liệu thành các phần nhỏ hơn gọi là ==gói tin (packets)==.
##### Mỗi gói tin bao gồm:
- Dữ liệu (data)
- ==Header==: Thông tin bổ sung, được thêm vào theo một giao thức nhất định.
- Thời gian để gửi một gói tin 1 bit với tốc độ r là 1/r.
r được gọi là ==tốc độ liên kết== (link transmission rate), ==dung lượng liên kết== (link capacity) ==hoặc băng thông liên kết==(link bandwidth).
# 1.3) The network core
### 📦 Chuyển tiếp (Forwarding) và Định tuyến (Routing)
- ==Chuyển tiếp (Forwarding)== (đôi khi còn được gọi là switching): Là một hành động cục bộ, liên quan đến việc di chuyển một gói tin đến từ ==liên kết đầu vào (input link)== của bộ định tuyến đến ==liên kết đầu ra (output link)== thích hợp của bộ định tuyến. Chuyển tiếp được điều khiển bởi một ==bảng chuyển tiếp (forwarding table)==.

- ==Định tuyến (Routing)==: Là hành động toàn cục để xác định đường dẫn (paths) từ nguồn đến đích mà các gói tin sẽ đi theo. Các thuật toán định tuyến (routing algorithms) tính toán các đường dẫn này và tính toán các bảng chuyển tiếp cục bộ trên mỗi bộ định tuyến cần thiết để thực hiện đường dẫn chuyển tiếp đầu cuối này.

### Packet Switching và Circuit Switching
- ##### Packet Switching
- Định nghĩa: Phương pháp truyền dữ liệu trong đó dữ liệu được chia thành các gói nhỏ (packets) và gửi độc lập qua mạng.
- Đặc điểm:
Không cần thiết lập kết nối trước khi truyền dữ liệu.
Các gói tin có thể đi theo các đường khác nhau đến đích.
Sử dụng hiệu quả băng thông hơn vì tài nguyên chỉ được sử dụng khi có dữ liệu để gửi.
- Ưu điểm:
Thích hợp cho dữ liệu bursty (không liên tục).
Đơn giản, không cần thiết lập cuộc gọi hoặc đặt trước tài nguyên .
Nhược điểm:
Có thể xảy ra trễ và mất gói tin do tắc nghẽn mạng.
- ##### Circuit Switching
- Định nghĩa:  Phương pháp truyền dữ liệu trong đó một đường truyền (circuit) được thiết lập và duy trì giữa nguồn và đích trong suốt phiên truyền.
- Đặc điểm:
Cần thiết lập kết nối trước khi truyền dữ liệu.
Tài nguyên mạng (băng thông) được dành riêng cho ền).
- Ưu điểm:
Đảm bảo chất lượng dịch vụ (QoS) ổn định.
- Nhược điểm:
Kém hiệu quả khi không có dữ liệu để gửi vì băng thông vẫn bị chiếm dụng.
Không linh hoạt bằng packet switching.
==Tóm lại==, packet switching linh hoạt và hiệu quả hơn cho dữ liệu không liên tục, trong khi circuit switching đảm bảo chất lượng dịch vụ ổn định nhưng kém hiệu quả hơn về sử dụng tài nguyên.
# 1.4) Performance: Delay, Loss and Throughput 
#### ⏱️ Components of Delay
##### Các Loại Độ Trễ
- Có bốn thành phần chính gây ra độ trễ tại một router:

     - ==Độ trễ xử lý (Processing delay)==: Thời gian cần thiết để router kiểm tra bảng định tuyến, chuyển tiếp gói tin qua bộ chuyển mạch và thực hiện các kiểm tra tính toàn vẹn. Thường rất nhỏ, cỡ micro giây hoặc ít hơn.

     - ==Độ trễ hàng đợi (Queuing delay)==: Thời gian một gói tin phải chờ trong hàng đợi tại một liên kết đầu ra để được truyền đi. Phụ thuộc vào mức độ tắc nghẽn của liên kết.

     - ==Độ trễ truyền dẫn (Transmission delay)==:Thời gian cần thiết để đẩy tất cả các bit của một gói tin vào liên kết đầu ra. Được tính bằng công thức: 
     L/R, trong đó 
     - L là số bit của gói tin và 
     - R là tốc độ truyền dẫn của liên kết.

     - ==Độ trễ lan truyền (Propagation delay)==: Thời gian một bit đi từ đầu gửi đến đầu nhận của liên kết. Tốc độ lan truyền gần bằng tốc độ ánh sáng, nhưng vẫn có thể nhận thấy được.
     - Ví dụ:Từ Trái Đất đến vệ tinh địa tĩnh: 270ms
             Từ bờ Đông Hoa Kỳ đến Châu Âu: 30ms

#### Mất gói tin (Packet Loss) 
- xảy ra khi hàng đợi của router đầy và gói tin mới đến bị loại bỏ.           
 ### 📉 Thông lượng (Throughput)
- Thông lượng là tốc độ truyền dữ liệu thực tế từ người gửi đến người nhận, tính bằng bits trên giây (bps).

- Thông lượng bị giới hạn bởi liên kết nghẽn cổ chai (bottleneck link), là liên kết có băng thông thấp nhất trên đường đi.  
  # 1.5)  Performance: Delay, Loss and Throughput in Computer Networks
  # 1.6) Networks under attack
     #### Mục Tiêu Chính
- 1. ==Các hành động xấu== mà kẻ tấn công có thể thực hiện trong môi trường mạng.
- 2. ==Các biện pháp phòng thủ== có thể được triển khai để ngăn chặn, giảm thiểu và phản ứng với các cuộc tấn công mạng.
#### 🏛️ Kiến Trúc Internet Ban Đầu
- Kiến trúc internet ban đầu không được thiết kế chú trọng đến bảo mật.
- Mô hình ban đầu: "Một nhóm người dùng tin tưởng lẫn nhau, kết nối với một mạng trong suốt".
- Bảo mật không phải là yếu tố thiết kế quan trọng hàng đầu vào thời điểm đó.
#### Các Khía Cạnh Cần Xem Xét
- ==Cách thức tấn công==: Làm thế nào kẻ xấu có thể tấn công hoặc xâm nhập mạng máy tính?

- ==Phòng thủ==: Làm thế nào để phòng thủ trước các cuộc tấn công này?

- ==Thiết kế bảo mật==: Làm thế nào để thiết kế kiến trúc mạng miễn nhiễm với các cuộc tấn công (security by design)?

#### 😈 Các Hành Vi Xấu
- ==Đánh cắp gói tin==: Giả định rằng kẻ xấu có thể sao chép các gói tin truyền trên các phương tiện truyền thông dùng chung (ví dụ: kênh không dây).
  - Ví dụ: Kẻ tấn công (C) có thể đọc tất cả các gói tin mà B gửi cho A.
  - ==Công cụ==: Các công cụ như packet sniffers (ví dụ: Wireshark) có thể được sử dụng để thu thập các gói tin.
- ==Chèn gói tin==: Kẻ tấn công có thể chèn các gói tin giả mạo vào mạng.
    - Ví dụ: C gửi gói tin giả mạo đến A, giả vờ là từ B.
    - Tương tự như email lừa đảo.
- ==Tấn công từ chối dịch vụ (Denial of Service - DoS)==: Tạo ra lượng truy cập lớn để làm quá tải thiết bị mạng.
     - Ví dụ: Máy chủ HTTP bị tấn công bằng các yêu cầu HTTP giả mạo.
     - Ví dụ: Router bị ngập lụt bởi các gói tin cần xử lý đặc biệt (như các gói tin traceroute).
     - Tấn công DDoS (Distributed Denial of Service): Kẻ tấn công xâm nhập vào nhiều máy tính khác và sử dụng chúng để thực hiện tấn công phối hợp vào mục tiêu.
#### 🛡️ Các Biện Pháp Phòng Thủ
- ==Xác thực (Authentication)==: Xác minh danh tính của người dùng trước khi cho phép truy cập vào dịch vụ mạng.
       - Ví dụ: Mật khẩu, thẻ SIM.
- ==Mã hóa (Encryption)==: Mã hóa nội dung gói tin để bảo vệ dữ liệu khỏi bị đánh cắp.
Chữ ký số (Digital Signatures): Xác minh tính toàn vẹn của dữ liệu và đảm bảo dữ liệu không bị thay đổi trên đường truyền.
- ==Kiểm soát truy cập (Access Control)==: Xác định ai có thể thực hiện hành động gì và yêu cầu xác thực trước khi cấp quyền truy cập.     
- ==Tường lửa (Firewalls)==: Các thiết bị phần cứng hoặc phần mềm được lập trình để phát hiện và giảm thiểu các cuộc tấn công.
     - Tường lửa có thể được đặt ở cả mạng biên và mạng lõi.
     - Có thể được lập trình để chỉ cho phép một số người dùng hoặc loại lưu lượng nhất định vào hoặc ra khỏi mạng.
  # 1.7) History of Computer Networking