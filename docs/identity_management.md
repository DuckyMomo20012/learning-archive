# 19CNTT_Group2_Identity Management: OpenID, OAuth and SAML

## Thành viên

- **Nguyễn Hữu Hiển**
- **Đinh Hải Giang**
- **Trần Trọng Nam**
- **Bùi Phú Thịnh**

## 1) OPENID

### **OpenID là gì?**

- OID là một tiêu chuẩn mở và là một giao thức xác thực phi tập trung được tài trợ phát triển bởi một tổ chức phi lợi nhuận tên là **OpenID Foundation**.
- Nó cho phép user có thể được xác thực bởi nhiều trang web hợp tác (còn gọi là các bên phụ thuộc - Relying Parties - RP) dùng các service của bên thứ ba (IDP). Thông qua việc này, vấn đề thiết lập một ad hoc login systems của webmasters được loại bỏ.
- User có thể đăng nhập tới nhiều website khác nhau mà không cần phải có user name và password riêng cho từng website. User chỉ cần tạo các account bằng cách chọn một **OID Provider** và dùng những account đó để đăng nhập vào bất cứ website nào chấp nhận **OID authentication**.
- Trong OID, chỉ có **Identity Provider** quản lý password của bạn và có nhiệm vụ confirm identity của bạn khi bạn đăng nhập vào bất kì một website nào bằng phương thức OID authentication của provider đó. Do việc không có bất kì một website nào biết được password của bạn ngoài provider nên khả năng bảo mật là tương đối cao.
- Có một phần mở rộng cho OID là **OpenID Attribute Exchange**, nó tạo điều kiện cho việc trao đổi thêm một số thông tin của user giữa **provider** và **RP** như giới tính, tuổi… và tùy thuộc vào nhu cầu mà mỗi RP sẽ yêu cầu một bộ các attributes khác nhau.
- Phiên bản cuối cùng của OpenID là OpenID 2.0 được ra mắt vào tháng 12, năm 2007

### Ưu điểm của OpenID

- Đăng ký thành viên nhanh chóng bằng OpenID. Với OpenID, bạn sẽ chỉ cần một vài thao tác đơn giản để chỉnh sửa các phần thông tin nào có thể được thấy bới website đăng ký. Ngoài ra, bạn hầu như không phải chỉnh sửa nhiều thông tin bởi vì các thông tin như họ tên, tuổi… có thể được RP lấy từ Provider thông qua OpenID và điền vào cho bạn.
- Đăng nhập nhanh và dễ dàng hơn: với OpenID, bạn chỉ cần phải nhớ 1 username và password để login vào website của OID Provider, sau đó bạn chỉ cần dùng OpenID để đăng nhập vào bất kì website nào dùng phương thức xác thực OpenID của provider mà bạn đang dùng. Như vậy bạn sẽ không phải bị hỏi đi hỏi lại thông tin đăng nhập hết lần này đến lần khác, không phải tạo nhiều thông tin đăng nhập khác nhau và nhớ hết chúng vì lí do bảo mật, không cần phải nhấn lưu thông tin đăng nhập trên trình duyệt và gây ra nguy cơ bị đăng nhập trái phép…
- Bởi vì OpenID định danh bạn là duy nhất trên Internet, một khi bạn thiết lập mình như là người sử dụng OpenID, bất cứ khi nào ai đó nhìn thấy OpenID của bạn được sử dụng, bất cứ nơi nào trên Internet, họ sẽ biết rằng đó chính là bạn. Tương tự như vậy, nếu bạn truy cập vào một trang web mới và thấy rằng một người nào đó với OpenID của bạn bạn, bạn có thể gần như chắc chắn rằng đó là bạn của bạn. Điều đó có thể khiến bạn lo lắng rằng OpenID là sẽ làm cho tất cả các hoạt động trực tuyến của bạn trở nên quá rõ ràng và dễ dàng bị phát hiện. Hãy yên tâm, mặc dù OpenID thống nhất thông tin về bạn, nhưng nó chỉ hợp nhất thông tin mà bạn đã cho phép public. Bạn có thể chọn, sử dụng OpenID, thông tin nào ? và thông tin đó ai sẽ thấy được

### Độ an toàn của OpenID

- Thực sự thì OpenID khá an toàn vì bạn không cần phải lộ thông tin đăng nhập quá nhiều lần mỗi khi đăng nhập vào các website khác nhau. Tuy nhiên, nếu kẻ xấu có được thông tin OpenID của bạn (thông tin đăng nhập vào OpenID provider website…) thì tất cả các tài khoản khác của bạn tại các website khác mà bạn có đăng ký bằng OpenID đó đều sẽ bị kẻ xấu truy cập được. Ngoài ra, OpenID của bạn có thể bị đánh cắp bằng một số phương thức khác nhau như Authentication bug, Data Type Confusion Logic Flaw, phishing, authentication hijacking in unsecured connection, covert redirect… - Phishing: một bên chuyển tiếp độc hại (malicious) có thể chuyển tiếp người dùng đến một trang web giả mạo trang web của OID Provider và yêu cầu người dùng điền thông tin đăng nhập vào. Khi người dùng cung cấp thông tin đăng nhập cho trang giả mạo này, bên sở hữu nó sẽ nắm giữ thông tin OpenID của user và từ đó dùng nó để đăng nhập vào các dịch vụ khác mà user đã dùng OpenID để đăng nhập. - Authentication hijacking in unsecured connection: - Một lỗ hổng quan trọng có ở bước cuối cùng trong sơ đồ xác thực khi TLS / SSL không được sử dụng: URL chuyển hướng từ nhà cung cấp danh tính đến bên phụ thuộc. Vấn đề với chuyển hướng này là thực tế là bất kỳ ai có thể lấy được URL này (ví dụ: bằng sniffing the wire) đều có thể phát lại nó và đăng nhập vào trang web với tư cách là người dùng nạn nhân. Một số nhà cung cấp danh tính sử dụng Nonces (number used once) để cho phép người dùng đăng nhập vào trang web một lần và chặn không cho đăng nhập các lần sau đó nếu thấy số đó xuất hiện lại (giống session key). Giải pháp nonce sẽ hiệu quả nếu người dùng là người đầu tiên sử dụng URL. Tuy nhiên, kẻ tấn công nhanh đang đánh hơi dây có thể lấy được URL và ngay lập tức thiết lập lại kết nối TCP của người dùng (vì kẻ tấn công đang dùng sniffing the wire và biết số thứ tự TCP được yêu cầu) và sau đó thực hiện replay attack như mô tả ở trên. Do đó, nonces chỉ bảo vệ khỏi những kẻ tấn công thụ động, nhưng không thể ngăn những kẻ tấn công chủ động. Sử dụng TLS / SSL trong quá trình xác thực có thể giảm đáng kể nguy cơ này.
  ![](https://i.imgur.com/yGbqRKN.png)

### Một số thành phần chính của OpenID và phương thức hoạt động của nó

- OpenID có 3 concept chính là:
  - The OpenID Identifier: Một String xác định duy nhất cho người sử dụng.
  - The OpenID Relying Party (RP): Một nguồn tài nguyên trực tuyến (có thể là một trang web, nhưng nó có thể là một tập tin, hình ảnh, hoặc bất cứ điều gì bạn muốn kiểm soát quyền truy cập vào) có sử dụng OpenID để xác định những người có thể truy cập nó.
  - The OpenID Provider (OP): Một trang web mà người sử dụng có thể yêu cầu một OpenID và sau đó đăng nhập và xác thực danh tính của sử dụng RP.
- Cách thức hoạt động:
  Giả sử một người dùng đang cố gắng truy cập tài nguyên là một phần RP của website, RP dùng OpenID. Để truy cập vào các nguồn tài nguyên, người sử dụng phải xuất trình OpenID của mình trong một form có thể được công nhận (bình thường) như OpenID. OpenID được mã hóa với vị trí của OP. RP sau đó lấy định danh của người dùng và chuyển hướng người dùng đến OP, nơi đó user sẽ được yêu cầu để chứng minh yêu cầu của mình sử dụng ID đó. - OpenID Identifiers: - Là trái tim của OpenID, mỗi một OpenID Identifier là một unique string với các ký tự dùng để xác định một người nào đó. Tất nhiên là sẽ không có chuyện hai người có cùng một string này. RP có thể giải mã định danh để xác định người dùng. Ở đây ta có 2 định danh cần quan tâm đến đó là: - User-Supplied Identifier - Claimed Identifier - Trong đó, User-Supplied Identifier là định danh được cung cấp bởi user tới các RP, User-Supplied Identifier sẽ được biến đổi (quá trình normalize) thành Claimed Identifier (một dạng chuẩn) dùng để xác định OP thông qua quá trình phát hiện. Sau đó OP sẽ xác thực user. - OpenID Relying Party - RP được user đưa một User-Supplied Identifier, thông qua biến đổi tạo ra Claimed Identifier. - Sau quá trình normalize đó, User Agent sẽ được chuyển hướng đến OP đã được xác định nhờ Claimed Identifier và người dùng sẽ thực hiện đăng nhập vào OP và được OP xác thực với RP. - RP chỉ quan tâm đến việc OP có xác thực thành công hay không. Nếu thành công thì RP sẽ cho User truy cập vào các content cá nhân của User và ngược lại thì sẽ chặn không cho truy cập đến các content đó. - Open ID Provider (OP) - Các OP sẽ phải có trách nhiệm phát hành các Identifiers, xác thực user. OP cũng có cơ chế quản lý dựa trên web của OpenID. OP thường sẽ nắm giữ các thông tin cơ bản của User như: - E-mail address - Full name - Date of birth - Postal code - Country - Primary language - Khi OP được yêu cầu xác thực Claimed Identifier, User Agent sẽ được chuyển hướng đến một trang để user điền thông tin đăng nhập. Nếu người dùng đăng nhập thành công thì OP sẽ tiến hành xác thực cho User với bên RP và chuyển hướng đến một URL được RP đưa ra. Ngược lại, người dùng sẽ được OP thông báo quá trình xác thực thất bại.

## Oauth

### Oauth là gì

Nhiều người thắc mắc không biết Oauth là gì. Thực chất, đây là một phương thức chứng chỉ được sử dụng để có thể chia sẻ rộng rãi các tài nguyên với nhau. Việc chia sẻ này không bị giới hạn bởi thông tin như username hoặc password không cần phải chia sẻ như là cách cũ. Bởi thế, ta sẽ thấy từ Auth này được hiểu theo hai nghĩa khác nhau, đó là Authentication và Authorization.

- Authentication là gì? Nghĩa này để chỉ cách xác thực người dùng một cách nhanh chóng và dễ dàng thông qua việc đăng nhập nhanh chóng.
- Authorization là gì? Nghĩa là có thể cấp cho người dùng quyền truy cập vào sử dụng các Resources. Ta có thể hiểu rằng khi đăng ký một tài khoản ở trên Facebook, ta sẽ dùng các tài khoản này để có thể đăng nhập trên đa dạng các ứng dụng khác nhau mà không phải lo tốn công đăng ký hoặc là đăng nhập lại.

### Quá trình phát triển của Oauth ra sao?

- Chia sẻ về quá trình phát triển của Oauth là gì, có thể thấy rằng sau nhiều sửa chữa, việc đến được với thành công và tiếp cận được với đa dạng khách hàng không phải là một điều gì quá dễ dàng.
- Vào năm 2006, lần đầu tiên Twitter đưa được ra chuẩn Oauth với tên gọi là OpenID. Thế nhưng ban đầu, phần mềm này không được đón nhận mạnh mẽ bởi chúng có điểm yếu khiến cho người sử dụng cảm thấy tốn thời gian mỗi khi sử dụng, đó chính là phải cung cấp những thông tin cá nhân như username và password.
- Sau đó 4 năm, vào năm 2010, phiên bản chính thức đầu tiên của Oauth được phát hành và chúng có tên là Oauth 1.0.
- Một thời gian sau khi được đưa ra sử dụng rộng rãi, công ty phát hành phải thu hồi lại bởi phát hiện ra một lỗi bảo mật nghiêm trọng được đặt tên là Session Fixation. (Nếu bạn thắc mắc Session Fixation là gì thì đây là thứ khiến cho hacker được phép chiếm đoạt quyền truy cập của người sử dụng để vào tài nguyên, từ đó thực hiện những hành động với mục đích xấu xa)
- Cho đến năm 2012, thay cho phiên bản cũ, phiên bản Oauth2 được ra đời. Tuy rằng chúng vẫn còn lỗi khiến cho người dùng phải than phiền như vẫn có thể lợi dụng kẽ hở của Chrome để hack nick Facebook mới, thế nhưng cho đến giờ, phiên bản này vẫn được dùng rộng rãi.

### Cách vận hành của Oauth là gì?

- Việc vận hành của Oauth là gì? Trên thực tế, Oauth2 được thiết kế vận hành không có gì quá khó hiểu. Nếu như trong một trang web nào đó, người sử dụng chọn đăng nhập bằng gmail hoặc bằng facebook, trang web đó sẽ dẫn người sử dụng đến phần mềm và đưa ra những quyền mà người dùng cần có để đăng nhập vào và sử dụng dịch vụ.
- Nếu như người dùng đồng ý với những quyền này, trang Facebook sẽ đưa ra một mã token để cho ứng dụng có thể xác minh xem bạn có phải chủ nhân của nick đó không, từ đó mới cấp quyền truy cập vào trang web cho bạn. Nếu như trang web này bị hacker tấn công, nó có thể chỉ lấy được các thông tin hoặc hoạt động của người dùng mà không ảnh hưởng đến người sử dụng. Bởi thế, tựu chung lại, đối với những người không nắm bắt được quá nhiều về công nghệ thì Oauth2 chắc chắn là một phương thức phù hợp đối với những người dùng cuối giống chúng ta.
  ![](https://i.imgur.com/RWoyKin.png)

### Sơ đồ vận hành ra sao?

Dễ dàng nhận thấy, sơ đồ vận hành của Oauth là gì cho ra 5 bước khác nhau.

- Đầu tiên, ứng dụng sẽ yêu cầu được ủy quyền truy cập vào Resource Server thông qua User.
- Sau đó, nếu như người dùng ủy quyền cho những yêu cầu trên thì ứng dụng này sẽ được nhận những ủy quyền ngược lại từ User.
- Ứng dụng sẽ gửi thông tin định danh (ID) của mình đến nhờ User và tới Authorization Server.
- Nếu như thông tin trên được xác thực và hoàn tất ủy quyền, Authorization Server sẽ trả lại cho ứng dụng một mã token. Đây được coi là bước xác thực ủy quyền hoàn tất.
- Muốn truy cập vào resource từ Server và lấy thông tin, ứng dụng sẽ phải đưa ra token để xác thực.

### Ưu điểm của Oauth2 bạn cần biết

Lý do khiến cho nhiều người dùng cài đặt Oauth ứng dụng là bởi vì Oauth2 có rất nhiều ưu điểm nổi bật khác nhau.

- Dễ dàng nhận thấy rằng phiên bản Oauth 2.0 được coi là một giao thức vô cùng linh hoạt được hoạt động dựa trên SSL – hay còn gọi là Secure Sockets Layer và được sử dụng để có thể đảm bảo được quyền riêng tư giữa máy chủ web và trình duyệt. Nhờ có phiên bản này mà chúng có thể lưu token cho việc truy cập của người dùng một cách cực kỳ nhanh chóng và dễ dàng.
- Không chỉ có vậy, Oauth 2.0 còn có thể đảm bảo đến mức tối ưu các giao thức bảo mật tùy biến và sử dụng để có thể làm cơ sở an toàn cho dữ liệu. Nhờ đó mà việc truy cập sẽ được hạn chế vào những dữ liệu của người sử dụng và nó cho phép người dùng truy cập tới khi authorization token bị hết hạn.
- Khả năng chia sẻ dữ liệu của người dùng được nâng cao lên đến mức tối đa khi họ không phải chia sẻ, tiết lộ những thông tin như tên đăng nhập và mật khẩu cá nhân mà vẫn có thể tiếp cận được tới nguồn thông tin mà họ muốn. Đây là một cải tiến rất vượt trội so với phiên bản cũ và nhiều phần mềm khác.
- Được cung cấp xác thực nhanh hơn và dễ dàng hơn so với phiên bản cũ.

### Nhược điểm của Oauth là gì?

Tuy có nhiều điểm mạnh nhưng mà điểm yếu của Oauth là gì vẫn khiến cho người dùng quan tâm. Trên thực tế, nếu như ứng dụng mà bạn sử dụng bị hack, chúng sẽ dẫn đến những ảnh hưởng nghiêm trọng cho trang web trên nhiều mặt thay vì chỉ có một nhược điểm. Nếu như người sử dụng không cẩn trọng, điều này hoàn toàn có thể xảy ra và khiến cho bạn phải gặp khó khăn trong việc tìm cách giải quyết.
![](https://i.imgur.com/AGwkUSY.png)

## 3) SAML

### SAML là gì?

Bài toán mà SAML thường giải quyết tên là SSO (Single Sign On).

- **SSO** nảy sinh từ vấn đề khi các nhà cung cấp dịch vụ muốn người dùng có thể sử dụng các dịch vụ khác nhau mà chỉ cần đăng nhập vào một chỗ duy nhất, giúp cho việc sử dụng được thuận tiện cũng như giúp cho người dùng quản lý các username và password được giảm đi tối thiểu, thì đòi hỏi cần có một cách nào đó có thể **xác thực và ủy quyền** thông tin người dùng mà không cần bắt họ tạo tài khoản khác nhau trên những dịch vụ khác nhau.
- SAML (Security Assertion Markup Language) là một "chuẩn mở" cho phép nhà cung cấp thực thể (Identity Provider - IdP) xác thực người dùng và ủy quyền cho người dùng sử dụng một dịch vụ nào đó của nhà cung cấp dịch vụ (Service Provider - SP) mà không bắt buộc người dùng phải tạo tài khoản đăng nhập vào dịch vụ đó.
  Định nghĩa như trên đọc sẽ khó hiểu, nhưng ví dụ nhưng khi bạn đăng nhập web tiktok mà có nút "Đăng nhập bằng Facebook" thì bạn SAML sẽ giải quyết vấn đề này

### Các thông số trong SAML

- **Subject**: Một thực thể về thông tin bảo mật sẽ được trao đổi. Chủ thể thường đề cập đến một người, nhưng có thể là bất kỳ thực thể nào có khả năng xác thực, bao gồm cả một chương trình phần mềm. Đối với các trường hợp sử dụng mà chúng ta sẽ thảo luận, đối tượng thường là người dùng ứng dụng.
- **SAML Assertion**: Một thông báo dựa trên XML có chứa thông tin bảo mật về một chủ đề.
- **SAML Profile** - Một đặc tả xác định cách sử dụng thông báo SAML cho một trường hợp sử dụng kinh doanh, chẳng hạn như đăng nhập một lần giữa nhiều miền.
- **Identity Provider** - Một vai trò được xác định cho hồ sơ đăng nhập một tên miền chéo SAML. Nhà cung cấp danh tính là một máy chủ đưa ra các xác nhận SAML về một chủ thể đã được xác thực, trong bối cảnh đăng nhập một lần giữa nhiều miền.
- **Service Provider**: Một vai trò khác được xác định cho cấu hình đăng nhập một lần tên miền chéo SAML. Nhà cung cấp dịch vụ ủy quyền xác thực cho nhà cung cấp danh tính và dựa vào thông tin về chủ thể được xác thực trong xác nhận SAML do nhà cung cấp danh tính đưa ra trong bối cảnh đăng nhập một lần giữa nhiều miền.
- **Trust relationship**: Thỏa thuận giữa nhà cung cấp dịch vụ SAML và nhà cung cấp danh tính SAML, theo đó nhà cung cấp dịch vụ tin cậy các xác nhận do nhà cung cấp danh tính đưa ra.
- **SAML Protocol Binding**: Mô tả cách các phần tử thông báo SAML được ánh xạ vào các giao thức truyền thông tiêu chuẩn, chẳng hạn như HTTP, để truyền giữa nhà cung cấp dịch vụ và nhà cung cấp danh tính. Trên thực tế, các thông báo phản hồi và yêu cầu SAML thường được gửi qua HTTPS bằng HTTP-Redirect hoặc HTTP-POST, sử dụng các liên kết HTTP-Redirect và HTTP-POST, tương ứng

### Cách hoạt động của SAML

![](https://i.imgur.com/Ju1uSQw.png)

- User truy cập nhà cung cấp dịch vụ (application)
- SP sẽ tạo SAML request để gửi đến IdP, SAML request này sẽ được đính kèm chữ ký số của SP (chữ ký của SP ở đây là khóa bí mật của SP)
- IdP khi nhận được SAML request từ SP sẽ phải xác minh chữ ký có phải là của SP hay không ? bằng cách sử dụng khóa công khai của SP để xác thực.
- IdP tương tác với user để xác thực thông tin danh tính user
- IdP chuyển hướng browser của user trở lại SP với SAML respone chứa **SAML authentication Assertion**. Phản hồi được gửi đến Assertion Consumer Service (ACS) url của SP.
- SP sử dụng và xác thực SAML respone và phản hồi yêu cầu ban đầu của người dùng (nếu user xác thực thành công)
