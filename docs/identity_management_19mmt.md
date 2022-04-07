# 19MMT_Group8_Identity Management: SAML, OpenID, OAuth

## Group 8

Thành viên nhóm:

- **Võ Hoàng Gia Bảo**
- **Ngô Huy Hoàng**
- **Nguyễn Tuấn Kiệt**
- **Trương Thế Phú**

## **MỞ ĐẦU**

Identity management (ID management) là quá trình mà một tổ chức thực hiện để đảm bảo các cá nhân có quyền truy cập thích hợp vào các tài nguyên công nghệ. Điều này bao gồm việc xác định(identification), xác thực(authentication) và ủy quyền(authorization) một người hoặc nhiều người có quyền truy cập vào các ứng dụng, hệ thống hoặc mạng.

Danh tính được quản lý (Managed identities) cũng có thể liên quan đến các quy trình phần mềm cần quyền truy cập vào hệ thống tổ chức. Quản lý danh tính có thể được coi là một thành phần thiết yếu trong bảo mật.

Quản lý danh tính bao gồm xác thực người dùng và xác định xem họ có được phép truy cập vào các hệ thống cụ thể hay không. Quản lý ID hoạt động song song với các hệ thống quản lý danh tính và truy cập (Identity and Access Management- IAM). Quản lý danh tính tập trung vào việc xác thực, trong khi quản lý truy cập tập chung vào việc ủy quyền.
![](<https://www.tuv.com/content-media-files/master-content/services/ict-business-solutions/1508-tuv-rheinland-identity-and-access-management-(iam)/tuv-rheinland-identity-and-access-management-visual-1-en-update_core_1_x.png>)

### **MỤC LỤC**

1. [Authentication và Authorization](#1.-Authentication-và-Authorization)
   1.1. [Authentication](#1.1.-Authentication)
   1.2. [Authorization](#1.1.-Authorization)
2. [Identity challenges](#2.-Identity-Challenges)
3. [Identity management approaches](#3.-Identity-Management-Approaches)
   3.1. [Pre-Application Identity Silo](#3.1.-Pre-Application-Identity-Silo)
   3.2. [Centralized User Repository](#3.2.-Centralized-User-Repository)
   3.3. [Early SSO Servers](#3.3.-Early-SSO-Servers)
   3.4. [Standard Protocols](#3.4.-Standard-Protocols)
4. [SAML và SAML 2.0](#4.-SAML-và-SAML-2.0)
5. [OpenID](#5.-OpenID)
6. [OAuth và OAuth 2.0](#6.-OAuth-và-OAuth-2.0)
   6.1. [Cách vận hành của OAuth 2.0](#6.1.-Cách-vận-hành-của-OAuth-2.0)
   6.2. [Điểm mạnh của OAuth 2.0](#6.3.-Điểm-mạnh-của-OAuth-2.0)
   6.3. [Điểm trừ của OAuth 2.0](#6.3.-Điểm-trừ-của-OAuth-2.0)
   6.4. [Sự khác nhau của Oauth 1.0 và 2.0](#6.4.-Sự-khác-nhau-của-Oauth-1.0-và-2.0)
7. [OpenID Connect](#7.-OpenID-Connect)
8. [Comparison](#8.-Comparision)

## 1. Authentication và Authorization

### **1.1. Authentication**

**Authentication** là quá trình kiểm tra thông tin đăng nhập trước khi cấp cho người dùng quyền truy cập vào hệ thống. Khi nói đến bảo mật, bạn nên sử dụng ít nhất hai hay nhiều yếu tố xác thực trước khi cấp cho người dùng quyền truy cập vào bất kỳ thứ gì (2FA, MFA, digital và physical tokens, v.v)

### **1.2. Authorization**

**Authorization** xảy ra sau quá trình xác thực bằng cách xác minh các quyền của bạn trước khi cấp cho bạn quyền truy cập vào các tài nguyên cần thiết như cơ sở dữ liệu, tệp, kho lưu trữ, v.v. Khi tạo tài khoản, thường cần chỉ định những gì tài khoản có thể làm, dưới dạng các đặc quyền. Chúng ta sử dụng thuật ngữ **Authorization** để cấp các đặc quyền chi phối những gì một tài khoản được phép thực hiện.

Cả **Authentication** & **Authorization** đều rất quan trọng đối với bảo mật và quản lý truy cập và mặc dù cả hai đều có các khái niệm khác nhau đằng sau chúng, nhưng chúng rất quan trọng đối với cơ sở hạ tầng của hệ thống và hiểu chúng là chìa khóa để quản lý danh tính và truy cập.

![](https://chungtrinh.com/2018/12/authentication-va-authorization/featured.jpg)
<br/>

## 2. Identity Challenges

- **Lực lượng lao động ngày càng phân tán**
  Một cách các tổ chức có thể tuyển dụng và giữ chân nhân tài tốt nhất là loại bỏ những hạn chế về vị trí địa lý và cung cấp một môi trường làm việc linh hoạt. Lực lượng lao động từ xa cho phép các doanh nghiệp tăng năng suất trong khi kiểm soát chi phí — cũng như không làm phiền nhân viên khỏi môi trường văn phòng truyền thống. Tuy nhiên, với việc nhân viên rải rác khắp một quốc gia hoặc thậm chí trên toàn thế giới, các đội CNTT doanh nghiệp phải đối mặt với một thách thức khó khăn hơn nhiều: duy trì trải nghiệm nhất quán cho nhân viên kết nối với các nguồn lực của công ty mà không phải hy sinh tính bảo mật.
- **Ứng dụng phân tán**
  Với sự phát triển của các ứng dụng dựa trên đám mây và Phần mềm như một dịch vụ (SaaS), người dùng giờ đây có quyền đăng nhập vào các ứng dụng kinh doanh quan trọng như Salesforce, Office365, Concur, v.v. bất cứ lúc nào, từ bất kỳ đâu, bằng mọi thiết bị. Tuy nhiên, với sự gia tăng của các ứng dụng phân tán, sự phức tạp của việc quản lý danh tính người dùng cho các ứng dụng đó cũng tăng lên.
- **Cung cấp hiệu quả**
  Nếu không có hệ thống IAM tập trung, nhân viên CNTT phải cung cấp quyền truy cập theo cách thủ công. Người dùng càng mất nhiều thời gian để có quyền truy cập vào các ứng dụng quan trọng của doanh nghiệp, thì người dùng đó sẽ càng làm việc kém hiệu quả hơn. Mặt khác, việc không thu hồi quyền truy cập của những nhân viên đã rời tổ chức hoặc chuyển sang các bộ phận khác nhau có thể gây ra những hậu quả nghiêm trọng về an ninh.
- **Bring your own device (BYOD)**
  Nhân viên, nhà thầu, đối tác và những người khác đang sử dụng thiết bị cá nhân và kết nối với mạng công ty vì lý do nghề nghiệp và cá nhân. Thách thức với BYOD không phải là liệu các thiết bị bên ngoài có được đưa vào mạng doanh nghiệp hay không mà là liệu CNTT có thể phản ứng đủ nhanh để bảo vệ tài sản kinh doanh của tổ chức hay không - mà không làm ảnh hưởng đến năng suất của nhân viên và đồng thời cung cấp quyền tự do lựa chọn.
- **Vấn đề mật khẩu**
  Sự phát triển của các ứng dụng dựa trên đám mây có nghĩa là nhân viên phải nhớ ngày càng nhiều mật khẩu cho các ứng dụng có thể qua các miền và sử dụng nhiều giao thức và tiêu chuẩn chia sẻ thuộc tính và xác thực khác nhau. Sự thất vọng của người dùng có thể tăng lên khi nhân viên ngày càng dành nhiều thời gian hơn để quản lý danh sách mật khẩu.
- **Tuân thủ quy định**
  Các mối quan tâm về tuân thủ và quản trị công ty tiếp tục là động lực chính thúc đẩy chi tiêu của IAM. Đảm bảo hỗ trợ các quy trình như xác định đặc quyền truy cập cho các nhân viên cụ thể, theo dõi sự chấp thuận của ban quản lý đối với quyền truy cập mở rộng và lập hồ sơ ai đã truy cập dữ liệu nào và khi nào họ làm điều đó có thể giúp giảm bớt gánh nặng tuân thủ quy định và đảm bảo quy trình kiểm toán suôn sẻ .

## 3. Identity Management Approaches

### 3.1. Pre-Application Identity Silo

Trong thời kỳ đồ đá của ứng dụng máy tính, mỗi ứng dụng thường triển khai kho lưu trữ danh tính, xác thực và ủy quyền của riêng mình.

Điều này đã không xảy ra một cách đáng tin cậy nếu một công ty có nhiều ứng dụng, do đó, dữ liệu hồ sơ người dùng luôn trở nên không đồng bộ giữa các hệ thống. Người dùng bực tức với các vấn đề toàn vẹn dữ liệu và phải nhớ nhiều mật khẩu đã đủ tệ khi chỉ có một vài ứng dụng. Tuy nhiên, khi số lượng ứng dụng trong một doanh nghiệp ngày càng tăng, việc mọi ứng dụng triển khai giải pháp xác thực và kho lưu trữ danh tính được bảo mật của riêng nó nhanh chóng trở nên không thể chấp nhận được đối với các doanh nghiệp.

### 3.2. Centralized User Repository

Việc tập trung quản trị danh tính và truy cập bằng dịch vụ danh bạ mang lại nhiều lợi thế. Khả năng sao chép thư mục cho phép các ứng dụng được lưu trữ trên khắp thế giới tận dụng cùng một thông tin nhận dạng, loại bỏ các vấn đề không nhất quán về dữ liệu.

Tuy nhiên, đối với tất cả các ưu điểm của chúng, các dịch vụ directory cũng có một số nhược điểm. Bản thân dịch vụ đã không duy trì bất kỳ session nào cho người dùng. Điều này có nghĩa là người dùng chỉ có một tên người dùng và mật khẩu để nhớ, nhưng người dùng vẫn phải nhập thông tin đăng nhập vào màn hình đăng nhập của từng ứng dụng vì mỗi ứng dụng cần thu thập thông tin đăng nhập của người dùng và xác thực chúng bằng cách sử dụng dịch vụ thư mục (trong trường hợp không có công nghệ bổ sung ). Ngoài việc gây bất tiện, điều này làm lộ mật khẩu của người dùng đối với các ứng dụng.

![](https://docs.evolveum.com/iam/enterprise-iam/identity-management-store-2.png)

### 3.3. Early SSO Servers

Single sign-on (SSO) cho phép người dùng đăng nhập bằng một bộ thông tin xác thực và có quyền truy cập vào nhiều ứng dụng và dịch vụ. SSO tăng cường bảo mật và cung cấp trải nghiệm người dùng tốt hơn cho khách hàng, nhân viên và đối tác bằng cách giảm số lượng tài khoản / mật khẩu bắt buộc cho tất cả các ứng dụng và dịch vụ mà họ cần.

Sự ra đời của các máy chủ đăng nhập một lần (SSO) mang lại nhiều lợi thế hơn so với các dịch vụ thư mục. Người dùng được hưởng lợi từ khả năng truy cập nhiều ứng dụng với một xác thực duy nhất. Các nhóm bảo mật đánh giá cao rằng mật khẩu thư mục tĩnh của người dùng chỉ được hiển thị với máy chủ SSO, thay vì đối với từng ứng dụng mà người dùng đã truy cập.

Thật không may, có một số nhược điểm với các máy chủ SSO ban đầu trong thực tế. Một hạn chế đáng kể là đăng nhập một lần dựa trên cookie, do các hạn chế của trình duyệt đối với quyền truy cập cookie, có nghĩa là các giải pháp hoạt động trong một miền Internet chẳng hạn như www.mywebsite.com. Khi nhiều công ty trở nên quan tâm đến các ứng dụng Phần mềm như một dịch vụ (SaaS) bên ngoài, đây là một hạn chế nhất định.

![](https://docs.wso2.com/download/attachments/49088428/image2018-10-29_11-25-19.png?version=1&modificationDate=1540792511000&api=v2)

### 3.4. Standard Protocols

Các giao thức Quản lý Danh tính và Truy cập được thiết kế đặc biệt để truyền thông tin xác thực và bao gồm một loạt các thông báo theo một trình tự đặt trước được thiết kế để bảo vệ dữ liệu khi nó truyền qua các mạng hoặc giữa các máy chủ.

Một số giao thức điển hình như: LDAP, SAML, OpenID, OAuth, Kerberos, RADIUS, Blockchain

## 4. SAML và SAML 2.0

![](https://i2.wp.com/ipwithease.com/wp-content/uploads/2018/11/img_5bfe590779c1e.png?resize=768%2C458&ssl=1)

- Security Assertion Markup Language, hoặc SAML, là một giao thức quản lý danh tính tiêu chuẩn mở thường được sử dụng cho single sign-on (SSO \*), cho phép người dùng chia sẻ cùng một thông tin đăng nhập trên các dịch vụ và ứng dụng khác nhau. SAML liên kết danh tính và thuộc tính của người dùng — có thể được lưu trữ trong các hệ thống quản lý danh tính khác nhau — với SSO để cung cấp trải nghiệm đăng nhập người dùng liền mạch.
- SAML đặc biệt cho phép liên kết danh tính, giúp nhà cung cấp danh tính (IdP) có thể chuyển danh tính đã xác thực và các thuộc tính của họ một cách liền mạch và an toàn cho nhà cung cấp dịch vụ (SP). SAML giữ vị trí thống lĩnh về mức độ chấp nhận của ngành đối với việc triển khai danh tính liên hiệp. Nó không chỉ được triển khai trong hàng trăm nghìn kết nối SSO đám mây mà hàng nghìn doanh nghiệp lớn, cơ quan chính phủ và nhà cung cấp dịch vụ cũng đã chọn SAML làm giao thức tiêu chuẩn để giao tiếp danh tính trên internet.
- Lợi ích của việc sử dụng SAML:
  - Vì SAML được xây dựng trên XML nên nó cực kỳ linh hoạt. Trong trọng tải xác nhận SAML (hay còn gọi là thông báo), hai đối tác liên kết có thể chọn chia sẻ bất kỳ thuộc tính nhận dạng nào mà họ chọn, miễn là các thuộc tính đó có thể được thể hiện bằng XML. Do tính linh hoạt này, các phần của tiêu chuẩn SAML, chẳng hạn như định dạng xác nhận SAML, đã được đưa vào các tiêu chuẩn khác, chẳng hạn như WS-Federation.
  - SAML có lợi thế lớn so với các cơ chế SSO độc quyền vì khả năng tương tác của nó. SSO độc quyền có nghĩa là mỗi kết nối mới yêu cầu triển khai phần mềm mới và khác hoặc các trình kết nối tích hợp độc quyền cho doanh nghiệp. Một triển khai SAML duy nhất có thể hỗ trợ SSO với nhiều đối tác liên kết khác nhau.
- Cách SAML Authentication hoạt động:
  - Các trường hợp sử dụng identity federation SAML trong doanh nghiệp thường xoay quanh việc chia sẻ danh tính giữa hệ thống quản lý truy cập và nhận dạng (Identity and Access Management- IAM) hiện có và các ứng dụng web. Có hai actors trong SAML screnario, Identity Provider (IdP) “xác nhận” danh tính của người dùng và Service Provider (SP) sử dụng “xác nhận” và chuyển thông tin nhận dạng cho ứng dụng. Tương tác giữa hệ thống IAM và máy chủ liên kết được gọi là “first mile” integration, trong khi tương tác giữa máy chủ liên kết và ứng dụng được gọi là “last mile” integration.
- Liên kết danh tính:
  - Thỏa thuận giữa nhà cung cấp danh tính và một hoặc nhiều nhà cung cấp dịch vụ liên quan đến dữ liệu sử dụng mà người dùng sẽ được mô tả:
    - Theo địa chỉ của họ?
    - Bằng số văn phòng và Id nhân viên của họ?
    - Theo vai trò hoặc tư cách thành viên của họ trong các nhóm nhất định?
    - Bằng một số nhận dạng duy nhất (bảo vệ quyền riêng tư) chỉ được biết đến với IdP và SP?
      +Việc tạo thỏa thuận có thể được thực hiện theo nhiều cách khác nhau
    - Thỏa thuận kinh doanh giữa IdP và SP
    - Trong một số trường hợp, có thể yêu cầu cập nhật hàng loạt hoặc đồng bộ hóa các phần của cửa hàng người dùng ở cả hai đầu
- SAML 1.0 là thông số SAML ban đầu đã nhanh chóng được thay thế bằng SAML 1.1. Qua hai phiên bản này, đầu vào từ các tiêu chuẩn liên quan khác (Shibboleth và Liberty ID-FF) đã được đưa vào để vào thời điểm SAML 2.0 xuất hiện trên thị trường, nó là nơi hội tụ của các tiêu chuẩn liên đoàn vào thời điểm đó.
- Điểm khác biệt: 1. SAML 1.1 thiếu một giải pháp mạnh mẽ để đăng xuất đơn lẻ được liên kết 2. SAML 2.0 được chấp nhận rộng rãi nhất và hoàn thiện nhất
  ![](https://lh3.googleusercontent.com/llSvy40UV04W-3S-S1m0T17bUP2ipclQVg3ZzIY39oZBVaHVHbxTJLNqrzmfHO0fd4qPfKWpmTMdmyUTwOJz4Rjr6qQkvzq2k-FeEo_cpjE9A2dzCWJym2EjtpP-ceqQKKJJagX6)

## 5. OpenID

![](https://s3.amazonaws.com/onelogin-screenshots/dev_site/images/oidc-implicit-flow.png)
Được phát triển bởi tổ chức phi lợi nhuận OpenID Foundation, OpenID cho phép người dùng có thể được xác thực bởi rất nhiều website (các bên lệ thuộc) sử dụng service của bên thứ 3. Nó giảm được việc phải thiết lập riêng logic register/login cho mỗi website, cho phép các người dùng có thể login tới nhiều webstie không hề liên quan tới nhau mà không cần phải có những định danh và password riêng cho mỗi site.

Với OpenID, bạn có thể kiếm soát được lượng thông tin mà bạn muốn cho phép các website bạn đến thăm biết được. Chỉ duy nhất Identity Provider quản lý password, và Provider này sẽ xác nhận identity của bạn tới các website mà bạn đến thăm, không có một website nào có thể biết được password của bạn - đây là một yếu tố bảo mật rất cao.

Một vài tổ chức lớn cho phép hoặc phát hành OpenIDs or tái sử dụng lại OpenID ví dụ như Google, Facebook, Yahoo!, Microsoft, AOL, MySpace, Sears, Universal Music Group, France Telecom, Novell, Sun, Telecom Italia, ...

Giao thức OpenID ban đầu đáng được nhắc đến vì khái niệm lấy người dùng làm trung tâm. Với SAML 2.0 chỉ được áp dụng trong các tình huống đối mặt với nhân viên, người dùng vẫn bị buộc phải đăng ký lại trên mỗi trang web dành cho người tiêu dùng. Ngoài các nhà cung cấp danh tính do tổ chức kiểm soát thường được sử dụng với SAML 2.0, OpenID bao gồm ý tưởng về danh tính do người dùng kiểm soát cho trường hợp sử dụng của người tiêu dùng. Người dùng thậm chí có thể thiết lập nhà cung cấp danh tính của riêng họ và đưa các ứng dụng đến đó để xác thực. Giao thức OpenID ban đầu không được sử dụng rộng rãi, nhưng nó đã làm nổi bật nhu cầu về các giải pháp nhận dạng người dùng làm trung tâm và đặt nền tảng cho một giao thức khác có tên [OpenID Connect](#7.-OpenID-Connect)

**Vậy nó hay ở chỗ nào ?**

**Đăng kí thành viên nhanh và dễ dàng**
Một OpenID chính là cách để định danh chính bạn không quan trọng bạn ghé thăm website nào. Nó như là bằng lái xe cho toàn bộ tuyến đường Internet. Nhưng còn hơn thế nữa là bởi vì bạn có thể điều chỉnh được thông tin liên kết tới OpenID như là tên, email, và bạn có thể chọn website nào được quyền thấy nó, thằng nào không. Điều này cũng đồng nghĩa với việc những website sử dụng OpenID sẽ không hỏi đi hỏi lại tên, email mỗi lần.

**Login nhanh và dễ dàng**
Với OpenID bạn chỉ cần nhớ 1 username và 1 password. Bởi vì bạn login vào website với OpenID của bạn, cho nên bạn chỉ cần bảo mật với OpenID là đủ. Password của bạn chỉ được quản lý bởi OpenID provider, không phải là các website bạn đang login, khi bạn login vào OpenID provider sẽ bảo với các website đó là bạn đang login đấy và bạn là ai. Không có bất kì một website nào nhìn được password của bạn, cho nên không cần phải quá bận tâm về vấn đề bảo mật khi sử dụng OpenID.

**Có khả năng nào khiến OpenID trở nên không an toàn không ? Câu trả lời là có.**
OpenID là thực sự cũng không an toàn hơn so với những gì bạn sử dụng ngay bây giờ. Bởi nếu ai đó có được username và password OpenID của bạn, họ có thể chiếm đoạt identity của bạn.
Có thể thấy hầu hết các trang web cung cấp việc reset password thông qua email trong trường hợp nếu bạn đã quên nó, có nghĩa là nếu một người nào đó có được tài khoản email của bạn, họ cũng có thể làm giống như trong trường hợp đó để họ có được username và password OpenID của bạn.
Tương tự như vậy, nếu một ai đó có quyền truy cập vào OpenID của bạn, họ có thể ngồi dò trên Internet đến những nơi mà họ nghĩ rằng bạn có tài khoản và đăng nhập nên không có gì khác biệt về bảo mật ở đây.
Cho nên, không liên quan đến việc bạn sử dụng OpenID hay không, việc bảo mật username và password là việc ai cũng nên làm.

OpenID định danh bạn là duy nhất trên Internet, một khi bạn thiết lập mình như là người sử dụng OpenID, bất cứ khi nào ai đó nhìn thấy OpenID của bạn được sử dụng, bất cứ nơi nào trên Internet, họ sẽ biết rằng đó chính là bạn. OpenID thống nhất thông tin về bạn, nhưng nó chỉ hợp nhất thông tin mà bạn đã cho phép public. Bạn có thể chọn, sử dụng OpenID, thông tin nào ? và thông tin đó ai sẽ thấy được.
OpenID authentication

- **The OpenID Identifier**: Một chuỗi xác định độc nhất cho người dùng.
- **The OpenID Relying Party (RP)**: Một nguồn tài nguyên trực tuyến (là bất cứ điều gì bạn muốn kiểm soát quyền truy cập vào) có sử dụng OpenID để xác định những người có thể truy cập nó
- **The OpenID Provider (OP)**: Một trang web mà người dùng có thể yêu cầu một OpenID và sau đó đăng nhập và xác thực danh tính của người sử dụng RP.

**OpenID hoạt động như thế nào?**

---

![](https://i.imgur.com/NXZSibq.png)

Giả sử ứng dụng A đóng vai trò là RP thông qua một tải khoản đã có của người dùng U được đăng ký trên OpenID Provider để thay cho việc đăng ký tài khoản mới trên A. Thông qua OP, A xác thực được U mà không cần phải đăng ký tài khoản trên A. Như vậy sử dụng một tài khoản duy nhất được đăng ký bởi OP, U có thể sử dụng để đăng nhập trên nhiều ứng dụng khác nhau mà không cần đăng ký tài khoản trên từng ứng dụng này.

Quy trình ứng dụng A sử dụng OpenID để xác thực người dùng U:

- A chuyển tiếp U về một URL của OpenID Provider để đăng nhập. OpenID được mã hóa với vị trí của OP
- Nếu đăng nhập thành công OP sẽ chuyển tiếp U về site của A và thông báo với ứng dụng này rằng người dùng U đã được xác thực.
- Cuối cùng ứng dụng A thực hiện việc xác thực người dùng U mà không cần đăng nhập ( A tin vào kết quả trả về của OP ).

---

**OpenID Identifiers**
Một OpenID Identifier là một String độc nhất các ký tự xác định duy nhất một người nào đó, dạng như token ấy. Không có hai người có cùng một OpenID. OpenID RP có thể giải mã một định danh để xác định được để xác thực người dùng. Có 2 định danh cần quan tâm :

- User-Supplied Identifier
- Claimed Identifier

Như tên nó, định danh *User-Supplied Identifie*r là định danh được cung cấp bởi người dùng tới RP. Các định danh được cung cấp bởi người dùng đã được biến đổi thành một dạng chuẩn (normalize) rồi trở thành định danh _Claimed Identifier_. Các định danh _Claimed Identifier_ sau đó có thể được sử dụng để xác định OP thông qua một quá trình được gọi là detection, sau đó OP sẽ xác thực người dùng.

**OpenID Relying Party (RP)**
Trình duyệt của người dùng ("User Agent") sẽ được chuyển tiếp đến các OP để người dùng có thể nhập mật khẩu và được xác thực.
RP không biết và cũng không cần biết các chi tiết cụ thể về cách thức xác thực. Nó chỉ muốn biết liệu các OP đã xác thực thành công người dùng hay chưa? (như mình đã nói, RP tin tưởng vào kết quả trả về của OP). Nếu đã đc xác thực rồi, User Agent được redirect đến các resource an toàn mà user đang cố gắng để truy cập. Nếu user không thể xác thực, RP từ chối không cho truy cập.

**Open ID Provider (OP)**
Các OpenID Provider (OP) chịu trách nhiệm phát hành Identifiers và thực hiện xác thực người dùng. Các OP cũng cung cấp cơ chế quản lý dựa trên Web của OpenID. Các OP thu thập và giữ thông tin cơ bản của mỗi người dùng như E-mail address, Full name, Date of birth, Gender, Postal code, Country, ...

Khi một OP được hỏi để xác thực định danh _Claimed Identifier_, trình duyệt của người dùng được dẫn đến một trang đăng nhập để người dùng nhập mật khẩu. Tại thời điểm đó, quyền kiểm soát là OP. Nếu người dùng được xác thực thành công, sau đó OP chỉ dấn các trình duyệt đến một vị trí được xác định bởi RP ("return-to" URL). Nếu người dùng không thể xác thực, họ có thể sẽ nhận được một tin nhắn từ OP rằng quá trình xác thực của họ thất bại.

## 6. OAuth và OAuth 2.0

Cũng tượng tự OpenID, cũng được sử dụng bởi các nền tảng xã hội lớn như Twitter, Facebook hay Google.

Có thể hiểu nôm na OAuth là một phương thức chứng thực giúp các ứng dụng có thể chia sẻ tài nguyên với nhau mà không cần chia sẻ thông tin username và password như những cách truyền thống cũ.

---

Giả sử: bạn tải ảnh lên một trang mạng xã hội có thể muốn cho phép một trang web in ảnh truy cập ảnh của bạn trên trang mạng xã hội. Trong trường hợp không có giải pháp tốt hơn, bạn sẽ phải chia sẻ thông tin đăng nhập trên mạng xã hội với trang web in ảnh. Nếu trang web in ảnh bị xâm phạm, điều đó sẽ khiến tài khoản mạng xã hội của bạn gặp rủi ro. Dĩ nhiên bạn đưa cho người ta thông tin đăng nhập thì làm gì có quyền kiểm soát những gì trang web in ảnh có thể thực hiện khi nó có mật khẩu của bạn. Đến đây cần có một giải pháp cho phép người dùng ủy quyền cho một ứng dụng tại một trang web truy xuất nội dung của họ từ API của trang web khác mà người dùng không cần phải tiết lộ thông tin đăng nhập của họ cho trang web đầu tiên.
Dùng 1 tài khoản Facebook hay Google để đăng nhập cả chục cái web, app mà không cần đăng ký tài khoản mới. Trong trường hợp hacker lấy được thông tin người dùng của web hay ứng dụng thì cũng bình thường về này vì ứng dụng bị mất của bạn chỉ được Facebook hay Google chia sẻ cho một token chứa quyền hạn nhất định và không được phép truy cập vào thông tin username cũng như password của bạn.

---

Khác với OpenID là về xác thực (tức là chứng minh bạn là ai), OAuth là về ủy quyền (tức là cấp quyền truy cập vào chức năng / dữ liệu / v.v. mà không cần phải xử lý xác thực ban đầu.

### **6.1. Cách vận hành của OAuth 2.0**

Nếu trong 1 ứng dụng/web nào đó mà bạn chọn đăng nhập bằng Facebook hay Gmail, website sẽ dẫn bạn đến trang (hoặc phần mềm) Facebook và liệt kê những quyền mà nó cần phải có để cho phép bạn đăng nhập và sử dụng dịch vụ. Nếu bạn đồng ý thì lúc này Facebook sẽ cung cấp cho ứng dụng/website một cái token, Token này chứa một số quyền hạn nhất định giúp cho website có thể xác minh bạn là ai cũng như giúp cho website có thể hoạt động được. Nếu website này bị hacker tấn công thì nó chỉ lấy được thông tin hay hoạt động của bạn trên website đó mà không ảnh hưởng đến những website khác mà bạn đang sử dụng. Do đó cách đăng nhập bằng phương thức OAuth này rất an toàn cho người dùng cuối như chúng ta.

**Sơ đồ vận hành thực tế của OAuth2**

![](https://teky.edu.vn/blog/wp-content/uploads/2021/08/giao-dien-cua-oauth-ban-nen-tim-hieu.jpg)

Ứng dụng có thể là website hoặc app điện thoại gửi yêu cầu ủy quyền để truy cập vào Resource Server (Gmail, Facebook, Twitter hay Github…) thông qua người dùng. Nếu người dùng đồng ý ủy quyền cho yêu cầu trên, Ứng dụng sẽ nhận được ủy quyền từ phía User (dưới dạng một token string), Ứng dụng gửi thông tin định danh (ID) của mình kèm theo ủy quyền của User tới Authorization Server. Nếu thông tin định danh được xác thực và ủy quyền hợp lệ, Authorization Server sẽ trả về cho Ứng dụng access token. Đến đây quá trình ủy quyền hoàn tất.
Để truy cập vào tài nguyên (resource) từ Resource Server và lấy thông tin, Ứng dụng sẽ phải đưa ra access token để xác thực. Nếu access token hợp lệ, Resource Server sẽ trả về dữ liệu của tài nguyên đã được yêu cầu cho Ứng dụng.

### **6.2. Điểm mạnh của OAuth 2.0**

Với phiên bản OAuth 2.0 là một giao thức rất linh hoạt dựa trên SSL (Secure Sockets Layer đảm bảo dữ liệu giữa máy chủ web và trình duyệt vẫn giữ được tính riêng tư) để lưu token truy cập của người dùng.
Ngoài ra, OAuth 2.0 dựa trên SSL, được sử dụng để đảm bảo các giao thức bảo mật và đang được sử dụng để giữ an toàn cho dữ liệu. Nó cho phép truy cập hạn chế vào dữ liệu của người dùng và cho phép truy cập khi authorization token hết hạn.
Khả năng chia sẻ dữ liệu cho người dùng mà không phải tiết lộ thông tin cá nhân.
Dễ dàng thực hiện và cung cấp xác thực mạnh mẽ hơn phiên bản cũ 1.0.

### **6.3. Điểm trừ của OAuth 2.0**

Vì vẫn phải lệ thuộc vào trung tâm Google hay Facebook nên nếu ứng dụng/web của bạn được kết nối với trung tâm và tài khoản trung tâm bị hack, thì nó sẽ dẫn đến các ảnh hưởng nghiêm trọng trên một số trang web thay vì chỉ một.

### **6.4. Sự khác nhau của Oauth 1.0 và 2.0**

**Nhiều Luồng Oauth hơn để cho phép hỗ trợ tốt hơn cho các ứng dụng không dựa trên trình duyệt**
Ví dụ: trong OAuth 1.0, các ứng dụng máy tính để bàn hoặc ứng dụng điện thoại di động phải hướng người dùng mở trình duyệt của họ đến dịch vụ mong muốn, xác thực với dịch vụ và sao chép mã thông báo từ dịch vụ trở lại ứng dụng. Lời chỉ trích chính ở đây là chống lại trải nghiệm người dùng. Với OAuth 2.0, giờ đây có nhiều cách mới để ứng dụng có thể cấp quyền cho người dùng.

**OAuth 2.0 không còn yêu cầu các ứng dụng khách phải có mật mã**
Điều này quay ngược trở lại API Twitter Auth cũ, không yêu cầu ứng dụng phải HMAC hash token và request chuỗi. Với OAuth 2.0, ứng dụng có thể thực hiện request chỉ bằng cách sử dụng token phát hành qua HTTPS.

**Signature OAuth 2.0 ít phức tạp hơn nhiều**
Không còn parsing, sorting hay encoding đặc biệt.

**Access token OAuth 2.0 "tồn tại trong thời gian ngắn"**
Thông thường, access token OAuth 1.0 có thể được lưu trữ trong một năm hoặc hơn (Twitter không bao giờ để chúng hết hạn). OAuth 2.0 có khái niệm về refresh token. Có nghĩa nó khiến cho access token của bạn thành lifetime token, vĩnh viễn. Bạn sẽ sử dụng refresh token để có được access token mới thay vì để người dùng ủy quyền lại ứng dụng của bạn.

OAuth 2.0 có sự tách biệt rõ ràng về vai trò giữa server xử lý các OAuth request và server xử lý quyền người dùng.

## 7. OpenID Connect

Như đã nói, OAuth 2.0 cung cấp một khuôn khổ để cho phép các ứng dụng gọi API, nhưng không được thiết kế để xác thực người dùng với các ứng dụng. Giao thức OpenID Connect (OIDC) cung cấp lớp dịch vụ nhận dạng gọi là identity layer trên OAuth 2.0, được thiết kế để cho phép các máy chủ ủy quyền xác thực người dùng cho các ứng dụng và trả về kết quả theo cách tiêu chuẩn.

Trước hết lưu ý là OpenID Connect khác với OpenID:

- OpenID là một giao thức xác thực phi tập trung theo chuẩn mở cho phép hiện thực hoá những việc ở trên.
- OpenID Connect là một lớp xác thực (authentication layer) trên nền tảng OAuth 2.0, một framework dùng cho việc xác thực.

OpenID Connect giúp các client kiểm tra user thông qua các authorization server, đồng thời với đó là lấy các thông tin cơ bản của user đó bằng cách gọi đến REST API. OpenID Connect dùng JSON Web Tokens (JWT) trong đó việc authentication dựa vào các token string trao đổi qua lại giữa client và authentication server. Thông tin mà server gửi về bao gồm một Acess Token, và có thể có (nếu bạn yêu cầu) một ID token.

---

Lấy ví dụ khi ta đăng nhập dùng tài khoản Google:

1. Khi bạn chọn đăng nhập dùng tài khoản Google, Authen server gửi một Authorization Request tới Google để xin được cấp quyền truy cập.
2. Google xác thực thông tin của bạn hoặc yêu cầu bạn login nếu bạn chưa đăng nhập, và sau đó hỏi bạn việc cấp quyền, tức là các quyền truy cập như avatar, email… của bạn.
3. Khi bạn đã chấp thuận việc đăng nhập, Google sẽ gửi một Access Token, và có thể có ID Token cho Authen server.
4. Authen server có thể nhận thông tin người dùng từ ID Token hoặc sử dụng Access Token để truy cập tới Google API.

Trong đó:

- **Access Token** là một mã bí mật dùng cho ứng dụng để có thể truy cập API. Access Token có thể là một string, JWT token, hay một token không phải là JWT. Nó báo cho API biết được là ứng dụng đã được cấp quyền cho một số action nhất định dựa trên scope mà ứng dụng đã được cấp.
- **ID Token** là một JWT chứa các thông tin nhận dạng. Nó được ứng dụng sử dụng để lấy các thông tin của user như username, email… và hiển thị lên giao diện. ID Token tuân theo chuẩn công nghiệp (IETF RFC 7519) và gồm có 3 phần: header, body và chữ ký.
- **JWT Token** chứa các claim là các thông tin về định danh (như là full name, email address) của một thực thể (thông thường là user) và các thông tin metadata khác.

---

OpenID Connect có thể đáp ứng các trường hợp sử dụng tương tự như SAML đối với XML nhưng với giao thức dựa trên _JSON / REST API, HTTP_ đơn giản hơn. OpenID Connect được thiết kế để cũng hỗ trợ các ứng dụng gốc và ứng dụng di động, trong khi SAML chỉ được thiết kế cho các ứng dụng dựa trên Web. SAML và OpenID Connect có khả năng sẽ cùng tồn tại trong một thời gian khá dài, mỗi cái sẽ được triển khai trong các tình huống mà chúng có ý nghĩa.

## 8. Comparison

|                 |                                                                        OAuth                                                                         |                                                OpenID                                                |                      SAML                      |
| :-------------: | :--------------------------------------------------------------------------------------------------------------------------------------------------: | :--------------------------------------------------------------------------------------------------: | :--------------------------------------------: |
|  Year Created   |                                                                         2006                                                                         |                                                 2006                                                 |                      2001                      |
|  Authorization  |                                                                         Yes                                                                          |                                                 Yes                                                  |                      Yes                       |
| Authentication  |                                                                Pseudo-authentication                                                                 |                                                 Yes                                                  |                      Yes                       |
| Protocols Used  |                                                                      JSON, HTTP                                                                      |                                              XRDS, HTTP                                              |              SAM, XML, HTTP, SOAP              |
| Security Risks  |                                                                       Phishing                                                                       |                                               Phishing                                               | XML Signature Wrapping to impersonate any user |
|                 | OAuth 2.0 does not support signature, encryption, channel binding, or client verification. Instead, it relies completely on TLS for confidentiality. | Identity providers have a log of OpenID logins, making a compromised account a bigger privacy breach |                                                |
| Best suited for |                                                        API Authorization Between Applications                                                        |                                        SSO for consumer apps                                         |               SSO for enterprise               |

<br/>

## **References**

Identity Management: SAML vs. OAuth2 vs. OpenID Connect. (2022). Retrieved 27 March 2022, from https://www.linkedin.com/pulse/identity-management-saml-vs-oauth2-openid-connect-jad-karaki

Identity and Access Management Protocols - IAM Protocols. (2022). Retrieved 27 March 2022, from https://identitymanagementinstitute.org/identity-and-access-management-protocols/

SAML and SAML 2.0 [Tutorial] - How a SAML Assertion Works | Ping Identity. (2022). Retrieved 27 March 2022, from https://www.pingidentity.com/en/resources/content-library/articles/saml.htmldw

2.0, S., & Meng, X. (2022). SAML 1x vs SAML 2.0. Retrieved 27 March 2022, from https://stackoverflow.com/questions/42615985/saml-1x-vs-saml-2-0

Solving Identity Access Management Applications (2022). Retrieved 27 March 2022, from https://www.amazon.com/Solving-Identity-Access-Management-Applications/dp/148425094X

Comparing the Top 3 Federated Indentity Providers: OpenID, OAuth, SAML (2022). Retrieved 27 March 2022, from https://www.softwaresecured.com/federated-identities-openid-vs-saml-vs-oauth/?msclkid=2624cb1cad4411ec9c3e6c8c1a81cb5d

What’s the Difference Between OAuth, OpenID Connect, and SAML? | Okta. (2022). Retrieved 27 March 2022, from https://www.okta.com/identity-101/whats-the-difference-between-oauth-openid-connect-and-saml/#:~:text=The%20main%20differentiator%20between%20these,industry%20standards%20for%20federated%20authentication

OpenID và OAuth Khác Nhau Như Thế Nào. (2022). Retrieved 27 March 2022, from https://www.codehub.com.vn/OpenID-va-OAuth-Khac-Nhau-Nhu-The-Nao

OAuth?, W. (2022). What's the difference between OpenID and OAuth?. Retrieved 27 March 2022, from https://stackoverflow.com/questions/1087031/whats-the-difference-between-openid-and-oauth

一番分かりやすい OAuth の説明 - Qiita. (2022). Retrieved 27 March 2022, from https://qiita.com/TakahikoKawasaki/items/e37caf50776e00e733be

Tìm hiểu về OpenID và OpenID Connetct – Khoa học và công nghệ mở. (2022). Retrieved 27 March 2022, from https://opentech.gov.vn/tim-hieu-ve-openid-va-openid-connetct/

**Everything in this article is using for study purposes only. Any copyright violation is a coincident by the writers**
