### 2.1 Principles of Network Applications
##### Các Dịch Vụ Của Tầng Vận Chuyển 🚚
- Bất kỳ điều gì tầng ứng dụng làm đều phải sử dụng các dịch vụ của tầng vận chuyển ngay bên dưới.  hai hình thức tương tác giữa các thành phần của một ứng dụng tầng ứng dụng:

    - Tương tác ngang hàng (peer-to-peer)
    - Mô hình client-server (mô hình máy khách-máy chủ)
##### Các Giao Thức và Hạ Tầng Phổ Biến 📡
Là tập hợp các quy tắc và định dạng được sử dụng để giao tiếp giữa các ứng dụng trên mạng
- ==HTTP==: Giao thức truyền tải siêu văn bản, hoạt động giữa máy khách web và máy chủ web.
- ==SMTP==: Giao thức truyền tải thư đơn giản, dành cho email.
- ==DNS==: Hệ thống tên miền, dịch từ tên miền  sang địa chỉ IP 32-bit (ví dụ: 128.119.40.186).
- ==Hạ tầng ứng dụng phân tán==: Các hệ thống streaming video và mạng phân phối nội dung (CDN).
- ==API Socket==: Giao diện lập trình ứng dụng.
##### Các Dịch Vụ TCP và UDP
- Tầng ứng dụng sử dụng các dịch vụ được cung cấp bởi tầng vận chuyển (TCP hoặc UDP) để gửi và nhận dữ liệu.
==TCP:==
- Truyền dữ liệu đáng tin cậy.
- Kiểm soát luồng (flow control).
- Kiểm soát tắc nghẽn (congestion control).
- Hướng kết nối (connection-oriented): Cần bắt tay (handshaking) trước khi truyền dữ liệu.
- Không cung cấp đảm bảo về thời gian, thông lượng hoặc bảo mật.
==UDP:==
- Truyền dữ liệu không đáng tin cậy (unreliable data transfer).
- Cố gắng hết sức để chuyển dữ liệu nhưng không đảm bảo.
- Không cung cấp kiểm soát luồng, kiểm soát tắc nghẽn, đảm bảo thời gian, thông lượng hoặc bảo mật.
##### Mô Hình Client-Server và Peer-to-Peer
Khi xây dựng một ứng dụng mạng, có hai mô hình tương tác chính:

==Client-Server:==
==Server:==
Luôn hoạt động.
Có địa chỉ IP cố định để client có thể liên hệ.
Có thể được đặt ở nhà, công ty, trường học, hoặc trung tâm dữ liệu.
==Client:==
Liên hệ và giao tiếp với server.
Thường xuyên kết nối và ngắt kết nối với internet.
Không có địa chỉ IP cố định.
Không giao tiếp trực tiếp với nhau mà thông qua server.
Ví dụ: HTTP (web browser là client, web server là server).
==Peer-to-Peer (P2P):==
Không có server trung tâm.
Các peer giao tiếp trực tiếp với nhau.
Peer yêu cầu và cung cấp dịch vụ cho các peer khác.
Ví dụ: Chia sẻ file.
Các peer thường xuyên kết nối và ngắt kết nối, thay đổi địa chỉ IP.
Quản lý các peer phức tạp hơn so với mô hình client-server.
##### Sockets:

- Socket là một giao diện lập trình ứng dụng (API) cho phép các ứng dụng giao tiếp qua mạng.
- Nó hoạt động như một điểm cuối của một kết nối mạng.
- Mỗi socket được xác định bởi một địa chỉ IP và một số port.
- Các ứng dụng gửi và nhận dữ liệu thông qua socket.

##### Địa Chỉ Hóa 📍
- Để giao tiếp, cần có thông tin địa chỉ:

- Khi tạo một socket, nó sẽ có hai thông tin quan trọng:
    - Địa chỉ IP của host.
    - Số port (port number).
    - Một số port được liên kết với một dịch vụ và giao thức cụ thể.
Ví dụ: Port 80 kết nối đến web server, port 25 kết nối đến email server.
### 2.2 The Web and HTTP
##### Tổng quan về HTTP và Cấu trúc Web
Web bao gồm các tệp HTML và các đối tượng được tham chiếu (ví dụ: hình ảnh, âm thanh) được lưu trữ trên các máy chủ khác nhau, mỗi máy chủ có thể truy cập thông qua một URL.
HTTP hoạt động theo mô hình máy khách-máy chủ, trong đó máy khách (như trình duyệt web) gửi yêu cầu đến máy chủ để phản hồi nội dung được yêu cầu.
Giao dịch HTTP sử dụng kết nối TCP, thường trên cổng 80 và không có trạng thái, nghĩa là máy chủ không lưu giữ thông tin về các yêu cầu trước đó.
##### Các loại kết nối HTTP
- ==Kết nối không liên tục== : Mỗi đối tượng yêu cầu kết nối TCP riêng, dẫn đến độ trễ cao hơn do có nhiều thời gian khứ hồi (RTT) cho mỗi yêu cầu.
- ==Kết nối liên tục== : Được giới thiệu trong HTTP/1.1, kết nối này cho phép nhiều đối tượng được gửi qua một kết nối TCP duy nhất, giảm độ trễ xuống còn một RTT cho các yêu cầu tiếp theo.
Kết nối liên tục hiện là tiêu chuẩn, cải thiện đáng kể hiệu suất web bằng cách giảm thiểu chi phí kết nối.
##### Tin nhắn HTTP: Yêu cầu và Phản hồi
- ==Tin nhắn yêu cầu== : Bắt đầu bằng dòng yêu cầu (phương thức, URL, phiên bản HTTP) theo sau là các dòng tiêu đề cung cấp ngữ cảnh bổ sung (ví dụ: loại trình duyệt, nội dung được chấp nhận).
- ==Tin nhắn phản hồi== : Bắt đầu bằng dòng trạng thái (phiên bản HTTP, mã trạng thái, tin nhắn trạng thái) theo sau là tiêu đề phản hồi và phần nội dung chứa nội dung được yêu cầu.
Mã trạng thái phổ biến bao gồm 200 (OK) và 404 (Không tìm thấy), với thông số kỹ thuật chi tiết có trong RFC 7320.
##### Cookie và Quản lý trạng thái
- Cookie được sử dụng để duy trì trạng thái người dùng trong các giao dịch HTTP, cho phép máy chủ ghi nhớ các tương tác của người dùng.
- Máy chủ gửi cookie đến máy khách, sau đó cookie này sẽ được đưa vào các yêu cầu tiếp theo, cho phép phản hồi được cá nhân hóa dựa trên hành vi trước đó.
- Có những lo ngại về quyền riêng tư liên quan đến cookie, đặc biệt là cookie của bên thứ ba, dẫn đến các quy định như GDPR yêu cầu người dùng phải đồng ý đối với các cookie không cần thiết.
##### Kỹ thuật lưu trữ web
- Bộ nhớ đệm web giúp cải thiện đáng kể hiệu suất của người dùng bằng cách giảm độ trễ và tải máy chủ.
- Bộ nhớ đệm lưu trữ nội dung được yêu cầu thường xuyên, cho phép khách hàng truy xuất dữ liệu mà không cần liên hệ với máy chủ gốc.
- Tiêu đề kiểm soát bộ đệm từ máy chủ gốc quyết định hành vi lưu trữ bộ đệm, tối ưu hóa việc sử dụng tài nguyên.
##### Lợi ích về hiệu suất của bộ nhớ đệm
- Việc triển khai bộ nhớ đệm web có thể giảm thời gian tải trang, giảm lưu lượng truy cập liên kết và giảm tải cho máy chủ gốc.
- Trong trường hợp có liên kết truy cập 1,54 Mbps, bộ nhớ đệm có thể giảm mức sử dụng từ 0,97 xuống 0,58, giảm thiểu độ trễ trong hàng đợi.
- Độ trễ trung bình từ đầu đến cuối có thể giảm từ 2 giây xuống còn khoảng 1,2 giây nhờ các chiến lược lưu trữ đệm hiệu quả.
##### Phương pháp GET có điều kiện
- Phương thức GET có điều kiện cho phép máy khách kiểm tra xem nội dung được lưu trong bộ nhớ đệm của họ có được cập nhật hay không, giúp giảm việc truyền dữ liệu không cần thiết.
- Máy khách gửi tiêu đề "If-Modified-Since", yêu cầu máy chủ phản hồi bằng mã 304 (Không sửa đổi) hoặc phiên bản mới của nội dung.
- Phương pháp này còn nâng cao hiệu suất hơn nữa bằng cách tiết kiệm tài nguyên mạng và cải thiện thời gian tải.

### 2.3 email
##### Tổng quan về Cơ sở hạ tầng Email
Email ra đời năm 1972, là ứng dụng nền tảng trong truyền thông kỹ thuật số.
Nó bao gồm ba thành phần chính: tác nhân người dùng (máy khách thư), máy chủ email và giao thức SMTP.
Tác nhân người dùng cho phép người dùng soạn, đọc và quản lý email, trong khi máy chủ lưu trữ tin nhắn và quản lý hàng đợi.
##### Cơ chế giao thức SMTP
SMTP (Giao thức truyền thư đơn giản) rất cần thiết để truyền tải thư email giữa các máy chủ.
Hoạt động trên TCP, thường sử dụng cổng 25, đảm bảo truyền tải tin nhắn đáng tin cậy.
Giao thức này bao gồm quá trình bắt tay và các giai đoạn truyền tải thông điệp, với các lệnh và phản hồi có thể đọc được bằng con người.
##### Quá trình chuyển tin nhắn email
Khi người dùng gửi email, máy khách sẽ liên hệ với máy chủ email của người dùng, sau đó máy chủ này sẽ liên lạc với máy chủ của người nhận.
Quá trình này bao gồm thiết lập kết nối TCP, gửi email và đặt nó vào hộp thư của người nhận.
Sự tương tác được đặc trưng bởi một loạt mã trạng thái và tin nhắn được trao đổi giữa các máy chủ.
##### So sánh với HTTP
SMTP là giao thức đẩy, trái ngược với cơ chế kéo của HTTP, trong đó máy khách yêu cầu dữ liệu từ máy chủ.
Cả hai giao thức đều sử dụng định dạng và mã trạng thái mà con người có thể đọc được, nhưng SMTP có thể xử lý nhiều đối tượng trong một thông báo.
SMTP yêu cầu tin nhắn phải ở định dạng ASCII 7 bit, với các quy tắc kết thúc cụ thể.
##### Giao thức lấy lại email
IMAP (Giao thức truy cập tin nhắn Internet) là phương pháp phổ biến nhất để lấy email từ máy chủ.
Các phương pháp khác bao gồm sử dụng HTTP để truy cập email từ các máy chủ web được cấu hình cho mục đích này.
Việc hiểu các giao thức này rất quan trọng để nắm bắt toàn bộ cơ sở hạ tầng email và hoạt động của nó.
### 2.4 The Domain Name Service: DNS
##### Tổng quan về chức năng DNS
- Hệ thống tên miền (DNS) dịch tên máy chủ (ví dụ: gaia.cs.umass.edu) thành địa chỉ IP (ví dụ: 128.119.40.186).
- DNS hoạt động như một giao thức lớp ứng dụng, sử dụng TCP và UDP cho các dịch vụ của mình.
- Nó hoạt động như một ==cơ sở dữ liệu phân tán== với ==cấu trúc phân cấp==, đảm bảo khả năng mở rộng và hiệu suất.
##### Việc sử dụng một cách tập trung (centralized DNSDNS) có những hạn chế sau:

- Điểm lỗi duy nhất (Single point of failure): Nếu máy chủ trung tâm gặp sự cố, toàn bộ hệ thống sẽ bị ảnh hưởng.
- Tập trung lưu lượng (Concentration of traffic): Một máy chủ duy nhất sẽ phải xử lý một lượng lớn truy vấn.
- Độ trễ cao (Long RTT delays): Thời gian để phân giải một truy vấn sẽ lâu hơn do khoảng cách địa lý.
- Khả năng mở rộng kém (Doesn't scale): Không thể đáp ứng hàng nghìn tỷ truy vấn mỗi ngày. 
##### ⚙️ Các Chức Năng Của DNS
- Chuyển đổi địa chỉ IP sang tên máy chủ (IP address to hostname translation)
- Chức năng bí danh (Aliasing function): Chuyển đổi từ tên bên ngoài như mail.cs.umass.edu sang một tên máy chủ nội bộ.
- Phân giải dịch vụ (Service resolution): Trả về địa chỉ IP của một máy chủ mail liên quan đến một miền.
- Cân bằng tải (Load balancing): DNS có thể luân phiên giữa các địa chỉ IP có thể thực hiện một dịch vụ được yêu cầu (ví dụ: một web server).
##### 🌲 Cấu Trúc Phân Cấp Của DNS
- DNS là một cơ sở dữ liệu phân cấp phân tán (distributed hierarchical database).

- ==Máy chủ DNS gốc (Root DNS servers)==: Gốc của cây.
- ==Máy chủ tên miền cấp cao nhất (Top Level Domain - TLD servers)==: Chịu trách nhiệm cho các tên miền như .com, .edu, .net.
- ==Máy chủ tên miền có thẩm quyền (Authoritative name servers)==: Chịu trách nhiệm cuối cùng cho việc phân giải tên trong miền của họ (ví dụ: umass.edu, nyu.edu, pbs.org).
  ![alt text](image.png)
  ###### Để phân giải một địa chỉ (ví dụ: www.amazon.com):

1) Máy tính của bạn gửi yêu cầu phân giải tên miền (www.amazon.com) đến máy chủ DNS cục bộ.

2) Máy chủ DNS cục bộ kiểm tra bộ nhớ cache của nó. Nếu nó đã phân giải tên miền này gần đây, nó sẽ trả về địa chỉ IP từ bộ nhớ cache. Nếu không, nó sẽ tiếp tục:

3) Máy chủ DNS cục bộ liên hệ với một trong các máy chủ gốc (Root DNS server).

4) Máy chủ gốc không biết địa chỉ IP của www.amazon.com. Thay vào đó, nó trả về cho máy chủ DNS cục bộ danh sách các máy chủ TLD chịu trách nhiệm cho miền ".com".

5) Máy chủ DNS cục bộ chọn một máy chủ TLD ".com" và gửi một truy vấn đến máy chủ đó.

6) Máy chủ TLD ".com" cũng không biết địa chỉ IP của www.amazon.com. Tuy nhiên, nó biết máy chủ tên miền có thẩm quyền (authoritative name server) cho miền "amazon.com". Nó trả về thông tin này cho máy chủ DNS cục bộ.

7) Máy chủ DNS cục bộ liên hệ với máy chủ tên miền có thẩm quyền cho "amazon.com".

8) Máy chủ tên miền có thẩm quyền cho "amazon.com" biết địa chỉ IP của www.amazon.com. Nó trả về địa chỉ IP này cho máy chủ DNS cục bộ.

9) Máy chủ DNS cục bộ lưu trữ ánh xạ tên miền - địa chỉ IP trong bộ nhớ cache của nó (với thời gian tồn tại - TTL) và trả về địa chỉ IP cho máy tính của bạn.

10) Máy tính của bạn bây giờ có thể kết nối trực tiếp đến www.amazon.com bằng địa chỉ IP đã nhận được.
##### Bảo Mật DNS
- DNS rất quan trọng đối với hoạt động của Internet. Vì vậy, cần bảo vệ DNS khỏi:

- Tấn công từ chối dịch vụ (Denial of Service - DoS): Sử dụng tường lửa (firewall) để bảo vệ.
- Nhập bản ghi trái phép: Sử dụng các dịch vụ xác thực (authentication services) để đảm bảo tính toàn vẹn của dữ liệu.
