# 19MMT_Group3_Zero Trust Network

**Nhóm thực hiện: Group 03**
Thành viên:

- **Nguyễn Hữu Hoàng An**
- **Tăng Tường Khang**
- **Hồ Đăng Khoa**
- **Nguyễn Thành Luân**

Đây là phần báo cáo của phần tìm hiểu về Zero Trust Network được thực hiện bởi các thành viên trong nhóm 03

**Nội dung - Zero Trust Network**

- Nội dung báo cáo được tham khảo từ sách Zero Trust Networks: Building Secure Systems in Untrusted Networks và một số nguồn tài liệu khác
  [![Zero Trust Network](https://images-na.ssl-images-amazon.com/images/I/51FEu6AhMfL._SX379_BO1,204,203,200_.jpg)](https://www.amazon.com/Zero-Trust-Networks-Building-Untrusted/dp/1491962194)

## **Table of Contents**:

1. [Tại sao lại sử dụng Zero Trust?](#1-Tại-sao-lại-sử-dụng-Zero-Trust)
2. [Nguyên tắc Zero Trust. Định nghĩa Zero Trust](#2-Nguyên-tắc-Zero-Trust-Định-nghĩa-Zero-Trust)
3. [Zero Trust hoạt động như thế nào](#3-Zero-Trust-hoạt-động-như-thế-nào)
4. [Mở rộng](#4-Mở-rộng)
5. [Kết luận](#5-Kết-luận)
6. [References](#References)

### 1. Tại sao lại sử dụng Zero Trust

#### _- Mô hình truyền thống? Còn phù hợp với hiện tại hay đã lỗi thời?_

- **Mô hình truyền bảo mật truyền thống** còn được gọi là Perimeter Security (PS).
  - Được dựa trên ý tưởng các tài sản, thông tin nội bộ của một tổ chức (thiết bị phần cứng, máy chủ, ứng dụng, dữ liệu, … ) sẽ được sẽ được bảo vệ khỏi những tác nhân từ bên ngoài (ứng dụng thứ 3, mạng công cộng,...) bởi rào cản vô hình, được thiết kế để bảo vệ (Firewall, ...).
    - Ví dụ: Khi bạn tới làm cho một công ty A, ngồi trong văn phòng làm việc của công ty A, sử dụng máy tính cá nhân để làm việc. Thì việc bạn truy cập vào hệ thống của công ty A là hoàn toàn hợp lí và không có gì bị nghi ngờ cả.
      --> Nếu máy tính của bạn có mã độc, hacker có thể xâm nhập vào máy bạn. Từ đó truy cập vào mạng nội bộ để lấy cắp dữ liệu thì làm sao ?

#### _- Thách thức đặt ra?_

Ở thời điểm hiện tại, nếu là một tổ chức với với hệ thống bảo mật truyền thống Perimeter Security, bạn sẽ phải đau đầu trong việc giải quyết các vấn đề sau:

- Trong thời buổi dịch bệnh ngày nay, "người dùng nội bộ" không chỉ đơn giản là truy cập từ thiết bị của công ty, mà còn từ thiết bị cá nhân nữa. Vậy phải quản lí làm sao?
- Dữ liệu và các ứng dụng của tổ chức đa số không còn lưu trữ trên các máy chủ mà bạn sở hữu về mặt vật lí nữa, không nằm trong phạm vi an toàn của tổ chức nữa mà thay vào đó là trên các kho dữ liệu, điện toán đám mây, các dịch vụ đưa ra thách thức rất lớn làm sao để có thể kiểm soát truy cập một cách chặt chẽ, an toàn cho cả người dùng bên ngoài và bên trong tổ chức.
- Các dịch vụ web mở rộng ra thế giới bên ngoài (những dịch vụ web nằm ngoài "ranh giới" an toàn, tin cậy của tổ chức) nhằm phục vụ cho khách hàng, đòi hỏi các kết nối ở mọi nơi đều có thể sử dụng dịch vụ, hay đơn giản là để giao tiếp với các dịch vụ khác, nội bộ cũng như bên ngoài tổ chức.
  --> Tổng hợp lại những ý trên, có thể thấy rõ ràng rằng mô hình bảo mật truyền thống PS không còn phù hợp để sử dụng trong môi trường đa kết nối- đa thiết bị- đa môi trường nữa. Cần một giải pháp tiên tiến hơn để có thể lắp lại những lỗ hổng của hệ thống bảo mật hiện nay.

#### _- Tại sao lại là Zero trust?_

Cơ bản vì nó có thể giải quyết những vấn đề trước đây một cách khá tốt bằng 3 yếu tố cốt lõi sau:

- **User/Application Authentication:** Có một số tính ngẫu nhiên bởi vì không phải lúc nào các hành động cũng được thực thi bởi người dùng. Trong trường hợp các hành động tự động được thực thi(Vd như trong datacenter), chúng ta cần xem xét thử ứng dụng truy cập như thế nào (có mã độc các thứ hay không, có hành động gì bất thường không, ..), có đủ tốt để truy cập vào datacenter hay không
- **Device Authentication:** Xác thực và ủy quyền cho thiết bị cũng quan trọng như làm như vậy đối với người dùng / ứng dụng. Chúng ta xác thực bằng việc kiểm tra xem thiết bị có đủ "sức khoẻ" để truy cập hay không(vượt qua những yêu cầu tối thiểu để truy cập). Đây là một tính năng hiếm khi được nhìn thấy trong các dịch vụ và tài nguyên được bảo vệ bởi các mạng PS.triển khai bằng cách sử dụng NAC or VPN, đặc biệt là trong các mạng trưởng thành(nhiều lớp, bảo mật cao), nó thường được thực hiện giữa các endpoint(máy chúng ta sử dụng) thay vì ở các tầng trung gian mạng.
- **Trust:** Cuối cùng, một "điểm tin cậy" được tính toán, và ứng dụng, thiết bị và điểm số được liên kết để tạo thành một agent để đăng nhập. Chính sách sau đó được áp dụng đối với agent để ủy quyền cho yêu cầu đăng nhập. Sự phong phú của thông tin có trong agent làm cho việc xác thực rất phức tạp, nhưng cũng rất linh hoạt, có thể thích ứng với các điều kiện khác nhau bằng cách bao gồm thành phần điểm trong các chính sách của bạn.

### 2. Nguyên tắc Zero Trust. Định nghĩa Zero Trust

#### _- Định nghĩa:_

- Zero Trust không phải là một thứ mà bạn có thể kiếm trên mạng và cài đặt nó. Nó cũng không phải là sản phẩm hay dịch vụ mà bạn có thể ra mua nó. Zero Trust là một chiến lược hay khuôn mẫu về mặt an ninh dành cho người dùng bất kể người đó thuộc bên trong hay bên ngoài hệ thống. Zero Trust được bắt đầu nghiên cứu và phát triển bởi nhóm nghiên cứu NIST và NCCoE ở bên Mỹ với cơ chế là luôn luôn xác thực, xác mình và xem xét lại ủy quyền của một người dùng mỗi lần khi người dó được cấp hoặc tiếp tục giữ được quyền truy cập tới ứng dụng và dữ liệu của hệ thống đã áp kiến thúc Zero Trust (ZTA) vào.

#### _- Nguyên tắc:_

- Để có thể treo sự "tin tưởng" từ hệ thống cho người dùng thì hệ thống áp dụng kiến trúc Zero Trust vào sẽ luôn thực hiện bốn nguyên tắc bắt buộc sau:
  - Never Trust, Always Verified (Không bao giờ tin tưởng, Luôn phải xác minh)
  - Luôn bạn là ai bất kể bản thân đang đeo 1 thứ chứng minh mình là ai vì vẫn có thể ai giả danh được bạn
  - Implemented Least Privilege (Triển khai đặc quyền truy cập ít nhất)
  - Như quyền admin, quyền quản lý
  - Assume Breach (Giả sử vi phạm)
  - Chúng ta cần phải lập ra tình huống xấu nhất => xây dựng các kế hoạch ứng phó mạnh mẽ và được kiểm tra độ thành công nhiều lần => thu nhỏ các vùng tấn công và ảnh hưởng của việc tấn công => thời gian phản hồi nhanh chóng và đạt được hiểu quả cao
  - Micro-segmentation
  - Micro-segmentation là một phương pháp để tạo các phân đoạn mạng hoặc "micro-perimeters" xung quanh các nội dung cụ thể. Điều này làm giảm bề mặt tấn công và cho phép các nhóm bảo mật CNTT của doanh nghiệp triển khai các biện pháp kiểm soát chính sách chi tiết. Mục đích là hạn chế sự di chuyển theo chiều của những kẻ tấn công và do đó, bảo vệ tổ chức khỏi các vi phạm.

### 3. Zero Trust hoạt động như thế nào

![Introduction](https://assets-global.website-files.com/5ecfe3add0194393eabdf182/618b007756edd86ecb738143_zero-trust.svg)

#### _- Single Sign-On_

- Single Sign-On cho phép người dùng truy cập vào tất cả tài khoản và ứng dụng bằng một bộ thông tin xác thực. SSO tăng cường bảo mật bằng cách loại bỏ mật khẩu, đồng thời tăng khả năng sử dụng và sự hài lòng của nhân viên.
- Mô hình Zero Trust tận dụng SSO như một phương pháp để xác thực người dùng trước khi họ được cấp quyền truy cập vào các ứng dụng và nội dung có giá trị.
  - Ví dụ: Mỗi khi người dùng muốn truy cập một ứng dụng, mã thông báo sẽ được sử dụng một cách minh bạch để xác thực danh tính của họ. Mật khẩu không thể được sử dụng để đăng nhập.
- Điều này có nghĩa là với Zero Trust, người dùng chỉ có thể kết nối dựa trên danh tính của họ. Vì không thể chuyển đổi danh tính, điều này đảm bảo truy cập an toàn.

#### _- Xác thực đa yếu tố_

- Xác thực đa yếu tố (Multi-factor authentication - MFA) xác minh danh tính của người dùng bằng cách yêu cầu họ cung cấp nhiều thông tin xác thực. Với MFA, người dùng phải cung cấp nhiều phương pháp nhận dạng.
  - Ví dụ: Người dùng có thể cần cả USB và mật khẩu. Nếu không có một trong hai yếu tố, người đó sẽ không thể có quyền truy cập.
- Xác thực đa yếu tố hỗ trợ mạng zero trust bằng cách tăng số lượng thông tin xác thực người dùng cụ thể cần thiết để truy cập. Sử dụng MFA có thể tăng độ khó cho tin tặc lên gấp hai, ba, bốn hoặc hơn.

#### _- Làm việc từ xa_

- Làm việc từ xa đã trở thành bình thường mới đối với hàng nghìn tổ chức trong thế giới hậu COVID. Tuy nhiên, mô hình mới này cũng tạo ra những thách thức nghiêm trọng về an ninh mạng.
- Khi mọi người làm việc tại nhà, họ thường sử dụng các thiết bị gia đình không an toàn, các kênh từ xa và các công cụ cộng tác. Tội phạm mạng lợi dụng những điểm yếu này để tấn công các tổ chức và đánh cắp dữ liệu của họ.
- Từ tháng 2 đến tháng 5 năm 2020, tin tặc đã đánh cắp dữ liệu cá nhân của hơn 500.000 người dùng tổ chức hội nghị truyền hình và bán nó trên dark web.
- Kể từ khi bắt đầu đại dịch, các cuộc tấn công ransomware đã tăng gần 500%. Các cuộc tấn công lừa đảo theo chủ đề COVID cũng gia tăng. Có thời điểm, các cuộc tấn công như vậy đã tăng lên 220% trong thời kỳ cao điểm của đại dịch vào năm 2020.

#### _- Vấn đề gặp phải khi sử dụng VPN_

- Nhiều tổ chức đã triển khai Virtual Private Network (VPN). VPN cho phép nhân viên từ xa truy cập vào tài sản mạng và dữ liệu mà họ cần để thực hiện công việc của mình. Tuy nhiên, VPN có thể xâm phạm an ninh mạng của công ty:
  - VPN không thể bảo vệ hoàn toàn mạng doanh nghiệp, dữ liệu hoặc nhân viên khỏi phần mềm độc hại, tin tặc hoặc vi phạm bảo mật.
  - VPN cũng không thể tạo hoặc thực thi các chính sách để bảo vệ thông tin xác thực, chẳng hạn như mật khẩu. Nếu nhà cung cấp bên thứ ba có quyền truy cập vào mạng hoặc dữ liệu của tổ chức, thì tin tặc độc hại có thể khai thác các giao thức VPN yếu để gây ra vi phạm dữ liệu.
  - Ngay cả một nhân viên từ xa bị xâm nhập sử dụng VPN cũng có thể mở ra cánh cửa cho một cuộc tấn công mạng.

#### _- Zero Trust Network Access_

- Zero Trust Network Access (ZTNA) cung cấp quyền truy cập từ xa an toàn vào các ứng dụng và dịch vụ.
- ZTNA dựa trên các chính sách kiểm soát truy cập đã xác định, từ chối quyền truy cập theo mặc định và cung cấp cho người dùng quyền truy cập vào các dịch vụ khi được cấp phép rõ ràng.
- ZTNA thiết lập quyền truy cập an toàn sau khi xác thực người dùng thông qua một đường hầm bảo mật, được mã hóa, cho phép người dùng chỉ xem các ứng dụng và dịch vụ mà họ có quyền truy cập.
- Phương pháp bảo vệ này ngăn chặn sự di chuyển của kẻ tấn công ngang, một lỗ hổng mà tội phạm mạng tận dụng để quét và xoay trục sang các dịch vụ khác.
- Với ZTNA, các tổ chức có thể triển khai các chính sách kiểm soát truy cập theo vị trí và thiết bị cụ thể, ngăn các thiết bị có thể bị xâm phạm kết nối với các dịch vụ của nó.

#### _- Lợi ích của mô hình Zero Trust_

- Bảo vệ dữ liệu khách hàng: Thời gian lãng phí và sự thất vọng do mất dữ liệu khách hàng sẽ bị loại bỏ, cũng như cái giá phải trả là mất đi những khách hàng không còn tin tưởng vào doanh nghiệp.
- Giảm sự dư thừa và phức tạp của ngăn xếp bảo mật: Khi hệ thống không tin cậy xử lý tất cả các chức năng bảo mật, bạn có thể loại bỏ các ngăn xếp tường lửa dự phòng, cổng web và các thiết bị bảo mật phần cứng và ảo khác.
- Giảm nhu cầu thuê và đào tạo các chuyên gia bảo mật: Hệ thống không tin cậy trung tâm có nghĩa là bạn không cần phải thuê nhiều người để quản lý, giám sát, bảo mật, tinh chỉnh và cập nhật các biện pháp kiểm soát bảo mật.

### 4. Mở rộng

#### _“Moving the U.S. Government Toward Zero Trust Cybersecurity Principles”_

_("Chính phủ Hoa Kỳ hướng tới các nguyên tắc an ninh mạng Zero Trust")
Nhiều mục trong bản ghi nhớ này có thể còn vượt xa những gì các doanh nghiệp hay các công ty về công nghệ thông tin đang làm hiện nay. Trong bản bản ghi nhớ bao gồm những mục như xác thực (authentication), phân mạng (network segmentation) và quyền truy cập dựa trên vai trò (role-based access control), đó là những thứ ta thường nghĩ đến khi nhắc tới Zero Trust._
Zero trust được sử dụng theo nhiều cách khác nhau, nhưng có thể hiếu một các đơn giản:

#### Không cung cấp tính năng duy trì thông tin đăng nhập cho người dùng.

- Điều này cũng rất hợp lý, nếu không cung cấp cho người dùng tính năng duy trì thông tin đăng nhập, thì không cần phải lo lắng về việc thiết bị của họ bị xâm nhập khi họ rời tổ chức.
- Nó cũng đề cập rằng kiểm soát truy cập dựa vào vai trò là tốt tuy nhiên không nên phụ thuộc quá nhiều vào “các vai trò được xác định trước - quyền truy cập tĩnh không thay đổi”. Thay vào đó quyền truy cập nên “ chi tiết” và “động”. (giống như kiểm soát truy cập Just-In-Time (JIT)), trong đó người dùng chỉ được cấp quyền truy cập vào tài nguyên khi học cần và quyền truy cập sẽ được thu hồi lại sau khi hoàn thành.

#### Sử dụng MFA nào?

_“discontinue support for authentication methods that fail to resist phishing, including protocols that register phone numbers for SMS or voice calls, supply one-time codes, or receive push notifications.”_

- Loại bỏ sử 2FA dựa trên SMS or voice calls,... được biết là dễ bị tấn công lừa đảo hay có thể bị tráo đổi sim.Trong bản ghi nhớ cũng đề cập loại bỏ các phương pháp tiếp cận mã một lần phổ biến TOTP (vd: google authenticator)
- Thay vào đó, sử dụng PIV card hay yubikeys. Nhưng nó có thể sẽ khó thực hiện với một số dịch vụ.

![MFA Img](https://i.rada.vn/data/image/2016/08/26/Google-Authenticator-xac-thuc.jpg)

#### Thêm ngữ cảnh khi truy cập.

_“Agency authorization systems should work to incorporate at least one device-level signal alongside identity information about the authenticated user when regulating access to enterprise resources.“_

- Đăng nhập sẽ kết hợp với ít nhất một tín hiệu được cấp từ thiết bị cùng thông tin nhận dạng, với thiết bị đấy phải là một thiết bị “đáng tin cậy”. Việc này khá khó, vì yêu cầu nhóm CNTT sẽ phải kiểm tra thiết bị của người dùng. Ngoài ra hệ thông sẽ phải “học tập” để đưa ra quyết định là truy cập này an toàn ở mức nào.

#### Mật khẩu không được dùng nữa!

_“Agencies are encouraged to pursue greater use of passwordless multi-factor authentication as they modernize their authentication systems. However, when passwords are in use, they are a “factor” in multi-factor authentication. ..... These policies should be removed by agencies as soon as is practical and should not be contingent on adopting other protections"_

- Các cơ quan được khuyến khích sử dụng nhiều hơn xác thực đa yếu tố không cần mật khẩu khi họ hiện đại hóa hệ thống xác thực của mình. Tuy nhiên, khi mật khẩu được sử dụng, chúng là một “yếu tố” trong xác thực đa yếu tố. Nếu các yêu cầu mật khẩu lỗi thời khiến nhân viên sử dụng lại mật khẩu từ đời sống cá nhân họ, hay lưu trữ mật khẩu không an toàn, hay sử dụng mật khẩu yếu, thì kẻ tấn công sẽ dễ dàng truy cập tài khoản trái phép hơn nhiều - ngay cả khi sử dụng MFA.”

#### VPN không được sử dụng nữa

_“In the current threat environment, the Federal Government can no longer depend on conventional perimeter-based defenses to protect critical systems and data”
“Users should log into applications, rather than networks”_

- Nếu VPN không đủ tốt, người dùng nên đăng nhập vào ứng dụng thay vì đăng nhập vào mạng, sử dụng xác thực Zero trust. Vậy Tại sao xác thực trên ứng dụng lại tốt hơn trên mạng? Khi truy cập vào mạng, như việc ta vào được một tòa nhà, nó rộng và khó kiểm soát. Còn khi đó, truy cập vào từng ứng dụng phản ánh các hành động của cá nhân người dùng.(ủng hộ tiếp cận beyondcorp https://cloud.google.com/beyondcorp)
  _“Users should log into applications, rather than networks, and enterprise applications should eventually be able to be used over the public internet”_

### 5. Kết luận

### References

- [Zero Trust Security: A Comprehensive Guide for Effective Security](https://www.onelogin.com/learn/zero-trust)
- [What is zero trust?](https://www.ibm.com/topics/zero-trust)
- [Mô hình bảo mật Zero Trust an toàn tuyệt đối cho doanh nghiệp](https://www.emerald.com.vn/tin-chi-tiet/mo-hinh-bao-mat-zero-trust-an-toan-tuyet-doi-cho-doanh-nghiep)
- [Zero Trust Network](https://crawshaw.io/blog/zero-trust)
- [When Implementing Zero Trust, Context Is Everything](https://securityintelligence.com/posts/when-implementing-zero-trust-context-is-everything/?_ga=2.34079393.1042217001.1647936732-1957902151.1647936732)
- [The Far Reach of the White House’s Zero Trust Memo](https://www.pomerium.com/blog/white-house-zt-memo/)
- [MEMORANDUM FOR THE HEADS OF EXECUTIVE DEPARTMENTS AND AGENCIES](https://www.whitehouse.gov/wp-content/uploads/2022/01/M-22-09.pdf)
- https://www.privacyaffairs.com/zero-trust-network/
