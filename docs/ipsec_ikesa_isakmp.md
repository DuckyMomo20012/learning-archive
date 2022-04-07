# **19MMT - Group7 - Cryptography Security for Internet**

---

## _Topic : IPsec, IKE SA, Oakley/ISAKMP (IPSec Kemanagement)_

---

Welcome to Group 7 :tada:

- Hoàng Đức Quang
- Trần Nam Khánh
- Phạm Thành Đăng
- Phạm Duy Tiến

## **I. IPSEC**

### 1.IPSEC là gì?

- IPSec là một bộ giao thức tương tác với nhau để cung cấp thông tin liên lạc riêng tư và an toàn trên mạng IP. Các giao thức này cho phép hệ thống thiết lập và duy trì các tunnel an toàn với các gateways bảo mật.

- IPSec cung cấp một cơ chế tiêu chuẩn, mạnh mẽ và có thể mở rộng để cung cấp bảo mật cho IP và các giao thức lớp trên (ví dụ: UDP hoặc TCP).

- IPSec cung cấp tính bảo mật, tính toàn vẹn của dữ liệu, kiểm soát truy cập và xác thực nguồn dữ liệu IP.

![](https://i.imgur.com/dV3TrOk.png)

### 2.Đặc điểm IPsec

- Từ xưa các gói IP không có bảo mật khi di chuyển trên mạng. Vì vậy nó tương đối dễ dàng bị giả mạo địa chỉ của các gói IP, sửa đổi nội dung của các gói IP, phát lại các gói cũ và kiểm tra nội dung của các gói IP đang chuyển tiếp. Do đó, không có gì đảm bảo rằng các dữ liệu IP nhận được là:

  - (1) từ người gửi được xác nhận quyền sở hữu
  - (2) rằng chúng chứa dữ liệu gốc mà người gửi muốn gửi
  - (3) rằng dữ liệu gốc không bị bên thứ ba kiểm tra trong khi gói đang được gửi từ nguồn đến đích

### 3.Kiến trúc IPsec

![](https://i.imgur.com/df0ggnO.png)

- Kiến trúc IPsec: Xác định cơ sở kiến trúc mà tất cả các triển khai được xây dựng dựa vào đó. Nó xác định các dịch vụ bảo mật được cung cấp bởi IPSec, cách thức và vị trí chúng có thể được sử dụng, cách các gói được xây dựng và xử lý cũng như sự tương tác của quá trình xử lý IPSec với chính sách.

- ESP là giao thức IPSec cung cấp tính bảo mật, tính toàn vẹn của dữ liệu và xác thực nguồn dữ liệu của các gói IP, đồng thời cung cấp khả năng bảo vệ chống lại reply-attack.

![](https://i.imgur.com/j0rqAkv.png)

- Giống như ESP, AH cung cấp tính toàn vẹn của dữ liệu, xác thực nguồn dữ liệu và bảo vệ chống lại replay-attacks. Nhưng khác với ESP 1 điểm là AH không cung cấp tính bảo mật.

### 4.Cách hoạt động của IPsec:

![](https://i.imgur.com/rK1zXGa.png)

:::info

**_Bước 1_**: IPsec được khởi tạo để bảo vệ các traffic. Các thiết bị đầu cuối sẽ thông qua trường đại chỉ để nhận ra các lưu lượng cần được bảo vệ.

**_Bước 2_**: IKE phase 1- IKE xác thực với các bên và các dịch vụ bảo mật được thỏa thuận và công nhận để thiết lập IKE SA. Phase này sẽ thiết lập 1 kênh truyền thông an toàn để tiến hành các trao đổi IPsec SA trong phase 2.

**_Bước 3_**: IKE phase 2 – IKE trao đổi các tham số và thiết lập IPsec SA ở hai phía. Các tham số này được dùng để bảo vệ dữ liệu được trao đổi, từ đó tạo ra kênh truyền bảo mật giữa hai bên.

**_Bước 4_**: Truyền dữ liệu – Dữ liệu được truyền dựa vào các thông số bảo mật và các khóa được lưu cơ sở dữ liệu SA.

**_Bước 5_**: Kết thúc tunnel IPsec.
:::

## **II. IKE SA**

### 1. IKE SA là gì?

- Là giao thức thực hiện quá trình trao đổi khóa và thỏa thuận các thông số bảo mật với nhau như: mã hóa thế nào, mã hóa bằng thuật toán gì, bao lâu trao đổi khóa 1 lần. Sau khi trao đổi xong thì sẽ có được một “thỏa thuận” giữa 2 đầu cuối, khi đó IPSec SA (Security Association) được tạo ra.

- Giao thức IKE có các đặc tính như sau:
  - Tự động làm mới lại chìa khóa.
  - Chống lại các cuộc tấn công làm nghẽn mạch như tấn công từ chối dịch vụ DoS (Denial-of-Service).
  - Sử dụng chữ ký số.
  - Dùng chung khóa.
  - Cung cấp những phương tiện cho hai bên về sự đồng ý những giao thức, thuật toán và những chìa khóa để sử dụng.
  - Đảm bảo trao đổi khóa đến đúng người dùng.
  - Quản lý những chìa khóa sau khi được chấp nhận.
  - Đảm bảo sự điều khiển và trao đổi khóa an toàn.
  - Cho phép sự chứng thực động giữa các đối tượng ngang hàng.

### 2. Các quá trình của IKE

![](https://i.imgur.com/WAXHxeh.png)

**_IKE phase 1_**

- IKE phase 1 đây là giai đoạn bắt buộc phải có. Phase này thực hiện việc xác thực và thỏa thuận các thông số bảo mật, nhằm cung cấp một kênh truyền bảo mật giữa hai đầu cuối. Các thông số sau khi đồng ý giữa hai bên gọi là SA, SA trong pha này gọi là SA ISAKMP hay SA IKE. Các thông số bảo mật bắt buộc phải thỏa thuận trong phase 1 này là:

  - Thuật toán mã hóa: _DES, 3DES, AES_
  - Thuật toán hash: _MD5, SHA_
  - Phương pháp xác thực: _Preshare-key, RSA_
  - Nhóm khóa Diffie-Hellman

**_Main Mode_**

- Sử dụng 6 message để trao đổi thỏa thuận các thông số với nhau:
  - Hai message đầu dùng để thỏa thuận các thông số của chính sách bảo mật.
  - Hai message tiếp theo trao đổi khóa Diffie-Hellman.
  - Hai message cuối cùng thực hiện xác thực giữa các thiết bị.

![](https://i.imgur.com/IeyS1PO.png)

**_Aggressive mode:_**

- Sử dụng 3 message:
  - Message đầu tiên gồm các thông số của chính sách bảo mật, khóa Diffie-Hellman.
  - Message thứ hai sẽ phản hồi lại thông số của chính sách bảo mật được chấp nhận, khóa được chấp nhận và xác thực bên nhận.
  - Message cuối cùng sẽ xác thực bên vừa gửi

![](https://i.imgur.com/PdIKgYp.png)

**_IKE phase 2_**

- IKE phase 2 đây là phase bắt buộc, đến phase này thì thiết bị đầu cuối đã có đầy đủ các thông số cần thiết cho kênh truyền an toàn. Quá trình thỏa thuận các thông số ở phase 2 là để thiết lập SA IPSec dựa trên những thông số của phase 1. Quick mode là phương thức được sử dụng trong phase 2. Các thông số mà Quick mode thỏa thuận trong phase 2:

  - Giao thức IPSec: ESP hoặc AH.
  - IPSec mode: Tunnel hoặc transport.
  - IPSec SA lifetime: dùng để thỏa thuận lại SA IPSec sau một khoảng thời gian mặc định hoặc được chỉ định.
  - Trao đổi khóa Diffie-Hellman.

- SA IPSec của phase 2 hoàn toàn khác với SA IKE ở phase 1, SA IKE chứa các thông số để tạo nên kênh truyền bảo mật, còn SA IPSec chứa các thông số để đóng gói dữ liệu theo ESP hay AH, hoạt động theo tunnel mode hay transport mode.

**_IKE phase 1.5_**

- Là một giai đoạn IKE không bắt buộc. Xác thực IPsec được cung cấp trong phase 1 xác thực các thiết bị hoặc thiết bị đầu cuối sử dụng để thiết lập kết nối IPsec. Xauth bắt người sử dụng phải xác thực trước khi sử dụng các kết nối IPsec.

## **III. Oakley/ISAKMP**

### 1. Oakley là gì?

- Oakley là một sự cải tiến của thuật toán trao đổi khóa Diffie-Hellman. Có thỏa thuận trước về hai tham số toàn cục: q, một số nguyên tố lớn; và aa gốc nguyên thủy của q. A chọn một số nguyên ngẫu nhiên X A làm khóa riêng và truyền cho B khóa công khai Y A = a XA mod q. Tương tự, B chọn một số nguyên ngẫu nhiên X B làm khóa riêng và truyền cho A khóa công khai Y B = a XB mod q. Giờ đây, mỗi bên có thể tính khóa phiên bí mật.

- Thuật toán Diffie-Hellman có hai tính năng hấp dẫn:
  - Khóa bí mật chỉ được tạo khi cần thiết. Không cần thiết phải lưu trữ các khóa bí mật trong một thời gian dài, làm cho chúng dễ bị tổn thương hơn.
  - Sàn giao dịch không yêu cầu cơ sở hạ tầng có sẵn ngoài thỏa thuận về các tham số toàn cầu.

### 2. Đặc điểm Oakley

- Thuật toán Oakley được đặc trưng bởi **_năm tính năng quan trọng_**:

1. Nó sử dụng một cơ chế được gọi là cookie để ngăn chặn các cuộc tấn công làm tắc nghẽn.
1. Nó cho phép hai bên thương lượng một nhóm; về bản chất, điều này chỉ định các tham số toàn cục của trao đổi khóa Diffie-Hellman.
1. Nó sử dụng các nonces để đảm bảo chống lại các cuộc tấn công phát lại.
1. Nó cho phép trao đổi các giá trị khóa công khai Diffie-Hellman.
1. Nó xác thực trao đổi Diffie-Hellman để ngăn chặn các cuộc tấn công của kẻ trung gian.

### 3.ISAKMP là gì?

- Được sử dụng để đàm phán, thiết lập, sửa đổi và xóa SA và các thông số liên quan. Nó xác định các thủ tục và định dạng gói để tạo và quản lý xác thực ngang hàng của SA và các kỹ thuật tạo khóa. Nó cũng bao gồm các cơ chế giảm thiểu các mối đe dọa nhất định - ví dụ: từ chối dịch vụ (DOS) và bảo vệ chống phát lại.
- Trong ISAKMP, SA và quản lý khóa tách biệt với bất kỳ giao thức trao đổi khóa nào; vì vậy, theo một nghĩa nào đó, ISAKMP là một giao thức "trừu tượng" - nó cung cấp một khuôn khổ để xác thực và quản lý khóa và hỗ trợ nhiều giao thức trao đổi khóa thực tế (ví dụ: IKE). ISAKMP xác định các định dạng tiêu đề và tải trọng, nhưng cần một bản khởi tạo cho một bộ giao thức cụ thể. Cách diễn giải như vậy được ký hiệu là ISAKMP Domain Of Interpretation (DOI)

### 4.Các giai đoạn của ISAKMP.

- ISAKMP hoạt động theo hai giai đoạn:

  - Giai đoạn 1: các thực thể ngang hàng thiết lập ISAKMP SA. Cụ thể là chúng xác thực và đồng ý về các cơ chế được sử dụng để bảo đảm các thông tin liên lạc tiếp theo.
  - Giai đoạn 2: ISAKMP SA này được sử dụng để thương lượng các SA giao thức khác (ví dụ: IPsec / ESP SA). Sau khi thiết lập ISAKMP SA ban đầu, nhiều SA giao thức có thể được thiết lập.

### 5. Gói định dạng tiêu đề ISAKMP (ISAKMP Header Format Packet.)

- ISAKMP_Header (28 byte): Chứa thông tin được giao thức yêu cầu để duy trì trạng thái, xử lý tải trọng và có thể ngăn chặn các cuộc tấn công từ chối dịch vụ hoặc phát lại.
- Sơ đồ sau đây cho thấy các trường con được chứa trong ISAKMP Header.

![](https://i.imgur.com/jPZUYRD.png)

---

- Initiator_Cookie (8 byte): Cookie của thực thể bắt đầu thiết lập hiệp hội bảo mật (SA), thông báo SA hoặc xóa SA. Điều này giống với những cookie được chỉ định trong [RFC2408].

- Responder_Cookie (8 byte): Cookie của thực thể đang phản hồi yêu cầu thiết lập SA, thông báo SA hoặc xóa SA. Trong thông điệp đầu tiên, cookie phản hồi bằng 0 Mỗi thương lượng AuthIP được xác định duy nhất bởi cặp cookie trình khởi tạo và trình phản hồi.

- Next_Payload (1 byte): Cho biết loại payload của payload đầu tiên trong thông báo. Giao thức Internet được xác thực (Authenticated Internet Protocol) sử dụng các payload bổ sung trong phạm vi Private Use.

- Major_Version (4 bit): Cho biết phiên bản chính của giao thức ISAKMP đang được sử dụng. Việc triển khai PHẢI đặt phiên bản chính >= 1.

- Minor_Version (4 bit): Cho biết phiên bản nhỏ của giao thức ISAKMP đang được sử dụng. Việc triển khai NÊN đặt phiên bản nhỏ thành 0. Các gói có số phiên bản nhỏ lớn hơn 0 PHẢI được chấp nhận.

- Exchange_Type (1 byte): Các loại trao đổi Giao thức Internet được xác thực nằm trong phạm vi sử dụng riêng.
  ược sử dụng. Flag mã hóa PHẢI được đặt bất cứ khi nào payload được mã hóa được gửi đi. Payload được mã hóa được biểu thị là HDR \* trong các sơ đồ trong thông số kỹ thuật này. Tất cả các flag khác PHẢI được đặt thành 0.

- Message_ID (4 byte): Mã nhận dạng thông điệp duy nhất được sử dụng để phân kênh các thông điệp từ các thương lượng chế độ nhanh đồng thời. Trường này PHẢI được đặt thành 0 trong khi đàm phán chế độ chính và PHẢI được đặt thành 1 trong khi đàm phán Chế độ mở rộng. Giá trị này được tạo bởi trình khởi tạo thương lượng chế độ nhanh.

- Length (4 byte): Độ dài, tính bằng byte, của tổng số message (header + payload).

---
