# 19CNTT_Group05_Deepfake: Nguy hiểm tiềm tàng ẩn sau những gương mặt ảo

Bài viết trên [Notion](https://irradiated-hippodraco-e85.notion.site/Deepfake-Nguy-hi-m-ti-m-t-ng-n-sau-nh-ng-g-ng-m-t-o-570653ce46e64e80a3fa0c8dd5012219)

- Lý Duy Nam

- Nguyễn Đăng Khoa

- Nguyễn Hoàng Long

- Trần Xuân Sơn

<aside>
📢 **Deepfake đã và đang ngày càng phát triển mạnh mẽ với sự lớn mạnh của các phương pháp học sâu Deep Learning. Trong bài viết này, chúng ta hãy cùng tìm hiểu Deepfake chính xác là gì? Sự phát triển của Deepfake sẽ có những ảnh hưởng nào đến khoa học và đời sống. Bên cạnh đó, bài viết này cũng sẽ giới thiệu những phương pháp nổi bật, hiện đại trong việc tạo ra và phát hiện Deepfake. **

</aside>

# 🧐 **Deepfake và ứng dụng**

## Deepfake là gì?

Deepfake (được ghép từ “Deep Learning” và “fake”) là một sản phẩm được tạo ra từ Trí tuệ nhân tạo (Artificial Intelligent - AI) với đầu vào là những ảnh, video, âm thanh,... Nói cách khác, việc tạo ra Deepfake chính là hành động “fake” một thứ gì đó bằng “Deep Learning”.

Cụm từ Deepfake này được xuất hiện lần đầu vào năm 2017 bởi một người dùng trên Reddit có tên là “deepfakes”. Người dùng này đã đăng tải những video “nhạy cảm” sử dụng công nghệ face-swap để hoán đổi gương mặt những người nổi tiếng vào nhân vật xuất hiện trong những video đó. Vì thế, ở thời điểm ban đầu, khi nhắc đến Deepfake, người ta sẽ nghĩ ngay đến việc hoán đổi khuôn mặt của một nhân vật, cá nhân xuất hiện trong ảnh/video bằng một hình ảnh khuôn mặt của người khác, từ đó cho phép chuyển động theo động tác của nhân vật trong ảnh/video gốc. Tuy nhiên hiện nay, Deepfake còn có thể tạo ra những đoạn âm thanh giả giọng của một người.

<figure>
  <img
       src="https://seanbmcgregor.com/images/content/deepfake_example.gif"
  alt="">
  <figcaption>Ví dụ về Deepfake video</figcaption>
</figure>

## **Ứng dụng của Deepfake**

Hiện nay, với những phát triển của mạng xã hội, mọi người (đặc biệt là giới trẻ) thường có xu hướng “sống ảo”, tạo ra những trào lưu mang nhiều yếu tố giải trí khác nhau. Chính vì lẽ đó, sự phát triển ngày càng mạnh mẽ của Deepfake giúp các nền tảng giải trí với video nội dung ngắn như Tik Tok, SnapChat,... tích hợp những bộ lọc (filter) đặc biệt giúp người dùng hóa thân thành một người khác tạo ra các trào lưu vui nhộn, hấp dẫn.

![BytesDance (công ty mẹ của TikTok) cho phép người dùng thay đổi khuôn mặt của họ](https://i.imgur.com/XEnaPIN.png)

BytesDance (công ty mẹ của TikTok) cho phép người dùng thay đổi khuôn mặt của họ

![Ứng dụng ***Zao*** cho phép người dùng hoán đổi khuôn mặt của mình với một trong những diễn viên trong một phân đoạn của phim nào đó](https://i.imgur.com/FZ6ntcA.png)

Ứng dụng **_Zao_** cho phép người dùng hoán đổi khuôn mặt của mình với một trong những diễn viên trong một phân đoạn của phim nào đó

Một lĩnh vực giải trí khác cũng nhận được ảnh hưởng tích cực từ Deepfake, đó chính là điện ảnh. Trong lĩnh vực này, Deepfake giúp các nhà làm phim có thể quay những phân cảnh mà không cảnh có sự có mặt của diễn viên chính. Họ có thể nhờ sự hỗ trợ của các diễn viên đóng thế rồi sau đó hoán đổi gương mặt của diễn viên chính vào hoặc [cải thiện công nghệ CGI](https://www.youtube.com/watch?v=byKy9kGnyvo&ab_channel=Shamook) ,Computer - Generated Imagery, sao cho nhân vật trông chân thật, sống động hơn. Việc này có ý nghĩa rất lớn cho hy vọng “hồi sinh” lại các vai diễn của các diễn viên đã qua đời, tái hiện lại hình ảnh của họ hoặc thay thế các diễn viên thực hiện các phân cảnh còn lại khi họ không thể có mặt tại trường quay ở lúc đó.

Ví dụ trong Fast and furious 7, khi nam diễn viên Paul Walker qua đời trong một vụ tai nạn xe hơi thì em trai Cody Walker trông giống Paul đã hoàn thành cảnh cuối cùng trong phim. Hãy nghĩ xem nếu Paul Walker không có em trai có nét mặt giống với anh ấy thì trong trường hợp đó nhà sản xuất phim phải sử dụng rất nhiều tiền vào CGI và chỉnh sửa video để hoán đổi khuôn mặt trong phim hoặc họ phải bắt đầu quay phim lại từ đầu.

Hay ví dụ khác, trong Star Wars Rogue One, CGI được sử dụng để tạo ra phiên bản trẻ hơn của Công chúa Leia do Carrie Fisher thủ vai, họ đã sử dụng rất nhiều tiền và tìm người có kỹ năng. Nếu có Deepfake, đoàn làm phim sẽ có thể tiết kiệm rất nhiều tiền và thời gian.

Dưới đây là 2 hình ảnh so sánh về việc dùng Deepfake tạo ra phim so với bản gốc.

![[The Mandalorian Luke Skywalker Deepfake - YouTube](https://www.youtube.com/watch?time_continue=24&v=wrHXA2cSpNU&feature=emb_logo)](https://i.imgur.com/ynuyAyN.png)

[The Mandalorian Luke Skywalker Deepfake - YouTube](https://www.youtube.com/watch?time_continue=24&v=wrHXA2cSpNU&feature=emb_logo)

![[Deepfaking Tarkin & Leia in Rogue One: A Star Wars Story [4K] - YouTube](https://www.youtube.com/watch?v=_CXMb_MO3aw)](https://i.imgur.com/jr6CFZ5.png)

[Deepfaking Tarkin & Leia in Rogue One: A Star Wars Story [4K] - YouTube](https://www.youtube.com/watch?v=_CXMb_MO3aw)

Ở một khía cạnh khác của điện ảnh, người ta cũng đang dành sự quan tâm cho việc ứng dụng Deepfake vào việc dịch lời thoại của các nhân vật sang ngôn ngữ khác để giúp khán giả ở nhiều quốc gia có thể cảm nhận được nội dung mà các nhân vật truyền đạt một cách trọn vẹn.

Về lĩnh vực hội họa, Deepfake giúp chúng ta tái tạo lại những phiên bản chân thực của các nhân vật từ tranh vẽ của các thế kỷ trước.

<figure>
  <img
  src="https://i.imgur.com/bnR0Tok.png"
  alt="">
  <figcaption>Tranh vẽ William Shakespeare (bên trái) và ảnh sau khi được Deepfake tái tạo (bên phải)</figcaption>
</figure>

<figure>
  <img
  src="https://i.imgur.com/necHD8I.png"
  alt="">
  <figcaption>Tranh vẽ Mona Lisa (bên trái) và ảnh sau khi được Deepfake tái tạo (bên phải)</figcaption>
</figure>

Các tấm ảnh trên là ví dụ minh họa cho việc phục hồi nhân vật xưa từ tranh vẽ thành các hình ảnh thực hơn (Nguồn ảnh: **[Nathan Shipley](https://www.instagram.com/nathan_shipley_vfx/?hl=en)**).

Ngoài ra, Deepfake còn có thể mang lại hiệu quả tích cực trong việc giáo dục. Việc tái tạo lại những nhân vật lịch sử, những đoạn âm thanh của những vĩ nhân trong quá khứ. Việc này làm tăng sự quan tâm của học sinh đối với bài học. Chẳng hạn, chúng ta hãy tưởng tượng khi chúng ta đang học vật lý và được nghe giảng bởi hình ảnh và giọng nói của Albert Einstein.

Với những ứng dụng như trên thì việc tạo ra Deepfake như thế nào?

# 🤔 **Deepfake video được tạo ra bằng cách nào?**

Với sự phát triển của sức mạnh tính toán từ các máy tính như hiện nay cùng với nguồn dữ liệu hình ảnh cực kỳ lớn, những mô hình học sâu Deep Learning tạo ra Deepfake dần ra đời và ngày càng phát triển vượt bậc. Về mặt tổng quan, các phương pháp tạo ra Deepfake video được phân loại thành bốn loại dựa trên cách thức và mức độ tác động của thao tác: Entire Face Synthesis, Identity Swap, Attribute Manipulation và Face Reenactment. [7]

## Entire Face Synthesis

![Untitled](https://i.imgur.com/HeyoYb9.png)

## Attribute Manipulation

![Untitled](https://i.imgur.com/jxvDqk0.png)

Sử dụng mạng GAN để tạo các khuôn mặt không tồn tại.

Sửa đổi một số vùng cụ thể của gương mặt. Một số ví dụ về thao tác trên khuôn mặt là thay đổi độ tuổi, giới tính, màu tóc và kiểu tóc, ...

## Face Reenactment (Expression Swap)

![Untitled](https://i.imgur.com/Dbftxka.png)

Face reenactment thay đổi, chuyển đổi biểu cảm, chuyển động của ánh mắt, thái độ và miệng của gương mặt

## Identity Swap (Face Swap)

![Untitled](https://i.imgur.com/HsGLipG.png)

Thay thế gương mặt của người trong ảnh/video gốc bằng gương mặt của người khác.

## “Xương sống” của các phương pháp tạo ra Deepfake video

### Autoencoder (AE) [8]

<figure>
  <img
  src="https://i.imgur.com/Y5SlgZy.png"
  alt="">
  <figcaption>Tái tạo gương mặt mới bằng Autoencoder (nguồn: https://www.alanzucconi.com/wp-content/uploads/2018/03/deepfakes_01d.png)</figcaption>
</figure>

Phần encoder sẽ có trách nhiệm nén dữ liệu khuôn mặt thành Latent Space và phần decoder sẽ giải mã trở lại thành hình ảnh khuôn mặt

<figure>
  <img
  src="https://i.imgur.com/brNVPWG.png"
  alt="">
  <figcaption>Hoán đổi Decoders để hoán đổi gương mặt (nguồn: https://www.alanzucconi.com/wp-content/uploads/2018/03/deepfakes_02d.png)
    </figcaption>

</figure>

Ý tưởng của việc hoán đổi gương mặt là sau khi huấn luyện xong, ta sẽ đổi decoder của 2 cặp cho nhau như trên ảnh.

### **Generative Adversarial Networks (GANs) [9]**

<figure>
  <img
  src="https://i.imgur.com/wCPCCy5.png"
  alt="">
  <figcaption>Mô hình GAN</figcaption>
</figure>

Mạng GAN là một mô hình có khả năng sinh ra dữ liệu. Về cơ bản, mạng GAN gồm hai thành phần: Generator (sinh ra dữ liệu) và Discriminator (phân biệt thật và giả). Discriminator sẽ kiểm tra khuôn mặt được sinh ra từ Generator và dữ liệu thật để kiểm tra mức độ chân thật. Nếu khuôn mặt được sinh ra chưa chân thật, Discriminator sẽ báo lại Generator cải thiện lại.

## Một số công cụ/ phần mềm giúp chúng ta tạo ra ảnh/video deepfake:

- [DeepfakesWeb](https://deepfakesweb.com/)
- Ứng dụng FaceApp
- Ứng dụng Reface
- Ứng dụng Zao

## Tạo Face-swapping video bằng DeepFaceFab [10]

Deepfacelab đang là phương pháp/ framework hàng đầu để tạo ra deepfake video, cụ thể là face-swapping. Mô hình của DeepFaceLab được chia thành 3 giai đoạn như sau:

### Face Extraction

![Screenshot 2022-03-26 041209.png](https://i.imgur.com/PvkGiwS.png)

Tại bước này, mô hình sẽ phát hiện gương mặt trong ảnh ra bằng phương pháp S3FD [11]/ RetinaFace [12].

Dùng 2DFAN [26]/ PRNet[27] để thu được face landmarks.

Cuối cùng, thực hiện phân đoạn (segment) bằng XSeg (được đề xuất trong chính bài báo)

### Training

![Untitled](https://i.imgur.com/5aWNVfr.png)

Đây là bước quan trọng, nó quyết định hình ảnh output có được độ chân thực hay không. Ở giai đoạn này, tác giả đề xuất hai cấu trúc DF và LIAE để những sinh ra những gương mặt không khớp nhau giữa Src và Dst. Ví dụ, video Src không có biểu cảm cười còn video Dst thì có, mô hình sẽ huấn luyện để tạo ra gương mặt từ Src có biểu cảm cười. Nhìn vào hình ta sẽ nhận thấy, cấu trúc DF sẽ đơn giản hơn LIAE . Vì thế khi dùng DF trong bước Training, ảnh output sẽ không kế thừa được các đặc tính ở video Dst (ví dụ: ánh sáng).

### Conversion

![Untitled](https://i.imgur.com/Q06hWH9.png)

Ở bước cuối cùng của DeepFaceLab, mô hình trước hết sẽ thực hiện việc hoán đổi gương mặt. Khi hoán đổi xong, những sai lệch về màu da cũng như biên cạnh không phù hợp cũng sẽ được xử lý trước khi hoàn thành việc tạo ra Face-swapping video.

![Bảng xếp hạng Face-swap được đánh giá trên tập FaceForensics++ [13] (nguồn: [PaperWithCode](https://paperswithcode.com/sota/face-swapping-on-faceforensics)). DeepFaceLab đứng đầu với tỷ lệ Pose Error thấp nhất.](https://i.imgur.com/Urto1wH.png)

Bảng xếp hạng Face-swap được đánh giá trên tập FaceForensics++ [13] (nguồn: [PaperWithCode](https://paperswithcode.com/sota/face-swapping-on-faceforensics)). DeepFaceLab đứng đầu với tỷ lệ Pose Error thấp nhất.

Hướng dẫn tự tạo Face-swapping video bằng DeepFaceLab:

[https://youtu.be/xlPdufBzQiE](https://youtu.be/xlPdufBzQiE)

# ⚠️ Deepfake đe dọa đến an ninh như thế nào?

Bênh cạnh những ảnh hưởng tích cực từ Deepfake đã nêu ở trên, sự phát triển của Deepfake cũng để lại nhiều mặt trái cần được quan tâm. Nhiều cá nhân lợi dụng Deepfake để tạo ra những hình ảnh/video “nhạy cảm” chứa gương mặt của người khác gây ảnh hưởng xấu đến hình ảnh và uy tín của những người đó.

Trong lĩnh vực chính trị, những video giả về các lãnh đạo của quốc gia, đảng phái được tạo ra nhằm mục đích xuyên tạc, dẫn dắt dư luận sẽ làm giảm đi độ uy tín của họ nhất là khi họ tham gia tranh cử.

<figure>
  <img
  src="https://i.imgur.com/RE1lgr1.png"
  alt="">
  <figcaption>Ảnh chụp từ video giả dạng Cựu tổng thống Mỹ Donald Trump</figcaption>
</figure>

<figure>
  <img
  src="https://i.imgur.com/g0Dmv9V.png"
  alt="">
  <figcaption>Video deepfake về tổng thống Ukraine Zelensky</figcaption>
</figure>

Bên cạnh đó, hacker cũng có thể tạo ra video hoặc audio clip bắt chước hành vi y hệt của người bị tấn công bằng cách cho hệ thống AI học các chuyển động và giọng nói của video gốc và sau đó phát sinh ra các video hoặc audio clip với hình ảnh giống hệt người bị tấn công đang nói. Đã có trường hợp ghi nhận một công ty ở Mỹ đã lừa khi mà một audio clip được tạo ra bởi Deepfake đã giả dạng giọng nói của CEO công ty đó và đánh mất 243,000 đô la cho sự việc này ([Link](https://www.forbes.com/sites/jessedamiani/2019/09/03/a-voice-deepfake-was-used-to-scam-a-ceo-out-of-243000/?sh=746fcdae2241)).

Deepfake cũng là một mối đe dọa đối với các hệ thống nhận diện khuôn mặt. Với khả năng hoán đổi khuôn mặt của nạn nhân, Deepfake sẽ khiến cho việc nhận dạng của các hệ thống này bị sai lệch và không chính xác. Từ đó, hacker có thể chiếm đoạt các thông tin cá nhân hoặc thực hiện cho mục đích xấu.

Với sự phát triển của Deepfake như ngày nay, những hình ảnh, video được tạo ra ngày càng tinh vi và khó nhận ra. Vì vậy, chúng ta cần những phương pháp phát hiện Deepfake đủ tốt để hạn chế hết mức có thể những tác hại từ nó.

# 👉 Làm thế nào để phát hiện một Deepfake video?

Hiện nay, các phương pháp phát hiện Deepfake video thường là sử dụng Deep Learning. Các phương pháp được đề xuất có thể là những giải pháp tập trung vào việc phát hiện bất thường trong ánh mắt, chuyển động của đầu hoặc là GAN fingerprint [23] và Biological signals [24]. Tuy nhiên, các mô hình phổ biến và có hiệu quả nhất trong lĩnh vực này là dựa trên các mạng Convolutional Neural Networks (CNNs).

<figure>
  <img
  src="https://i.imgur.com/iwbAfTF.png"
  alt="">
  <figcaption>Mạng CNN cho bài toán Classification</figcaption>
</figure>

Phương pháp sử dụng CNN để phát hiện Deepfake như sau: chúng ta cho ảnh đi qua một mạng CNN để trích xuất đặc trưng của ảnh (Phần Feature Learning). Từ những đặc trưng đó, ta thực hiện việc phân loại nhị phân (Binary Classification) để xác định ảnh đó có thật hay là không?

Một số mạng CNN nổi bật đã được đề xuất cho việc phát hiện Deepfake như sau: MesoNet [15] (Meso-4 và MesoInception-4) do Darius cùng các cộng sự của mình đề xuất để chống lại các video được tạo ra từ Deepfake và Face2Face vào năm 2018. Bên cạnh phương pháp này, nhiều thử nghiệm về các mạng CNNs với pre-trained weights trên tập ImageNet cũng đã được đề xuất như VGG19, Inception, Xception, ResNet, DenseNet và đặc biệt là EfficientNet [16] cũng đã dần xuất hiện. Tại Deepfake Detection Challenge **\*\*\*\***năm 2020, mô hình EfficientNet B7 với Noisy Student pre-trained weights trên tập ImageNet do Selim Seferbekov [25] đề xuất đã dành chiến thắng với độ đo AUC là 0.972 và f1-score là 90.6 khi thực nghiệm trên tập dữ liệu DFDC [14], một tập dữ liệu lớn và hoàn thiện với hơn 100,000 videos dành cho việc phát hiện Deepfake được cung cấp bởi Facebook.

Năm 2021, cũng trên tập DFDC, Deepfake Detection Scheme Based on Vision Transformer and Distillation đã cải thiện phương pháp trên một chút để đạt 0.978 điểm AUC và 91.9 điểm f1-score để trở thành State-of-the-art (SOTA) model. Tuy nhiên, cốt lõi của phương pháp này vẫn là dựa trên EfficientNet B7.

<figure>
  <img
  src="https://i.imgur.com/8UxMmGv.png"
  alt="">
  <figcaption>Mô hình EfficientNet để phân loại ảnh Deepfake [26]</figcaption>
</figure>

<figure>
  <img
  src="https://i.imgur.com/cZ53xKT.png"
  alt="">
  <figcaption>So sánh các phương pháp Deepfake Detection trên DFDC (theo [17])</figcaption>
</figure>

Demo sử dụng EfficientNet B7 để phát hiện Deepfake (dựa trên [deepware.ai](https://deepware.ai/)):

[https://youtu.be/svQwmOdrIs0](https://youtu.be/svQwmOdrIs0)

# References

1. [What is a deepfake? (2020)](https://www.theguardian.com/technology/2020/jan/13/what-are-deepfakes-and-how-can-you-spot-them)
2. [Wikipedia - Deepfake](https://en.wikipedia.org/wiki/Deepfake)
3. [Face swap trend on TikTok and Zao](https://techcrunch.com/2020/01/03/tiktok-deepfakes-face-swap/)
4. [Canny AI: Imagine world leaders singing](https://www.fxguide.com/fxfeatured/canny-ai-imagine-world-leaders-singing/)
5. [How deefake bypass facial regconition using GANs](https://towardsdatascience.com/deepfake-to-bypass-facial-recognition-by-using-generative-adversarial-networks-gans-37a8194a87b1)
6. [Deep Learning for Deepfakes Creation and Detection: A Survey (arxiv.org)](https://arxiv.org/pdf/1909.11573.pdf)
7. [DeepFakes and Beyond: A Survey of Face Manipulation and Fake Detection](https://arxiv.org/abs/2001.00179)
8. [Auto-Encoding Variational Bayes](https://arxiv.org/abs/1312.6114)
9. [Generative Adversarial Networks](https://arxiv.org/abs/1406.2661)
10. [DeepFaceLab: Integrated, flexible and extensible face-swapping framework](https://arxiv.org/abs/2005.05535)
11. [S3FD: Single Shot Scale-invariant Face Detector](https://arxiv.org/abs/1708.05237)
12. [RetinaFace: Single-stage Dense Face Localisation in the Wild](https://arxiv.org/abs/1905.00641)
13. [FaceForensics++: Learning to Detect Manipulated Facial Images](https://github.com/ondyari/FaceForensics)
14. [Deepfake Detection Challenge Dataset](https://ai.facebook.com/datasets/dfdc/)
15. [MesoNet: a Compact Facial Video Forgery Detection Network](https://arxiv.org/pdf/1809.00888.pdf)
16. [EfficientNet: Rethinking Model Scaling for Convolutional Neural Networks](https://arxiv.org/abs/1905.11946)
17. [Combining EfficientNet and Vision Transformers for Video Deepfake Detection](https://arxiv.org/abs/2107.02612)
18. [Deepfakes, explained | MIT Sloan](https://mitsloan.mit.edu/ideas-made-to-matter/deepfakes-explained)
19. [DeepFake Detection using 3D-Xception Net with Discrete Fourier Transformation](https://www.researchgate.net/publication/353787043_DeepFake_Detection_using_3D-Xception_Net_with_Discrete_Fourier_Transformation)
20. [DeepFakes: Detecting Forged and Synthetic Media Content Using Machine Learning](https://arxiv.org/pdf/2109.02874.pdf)
21. [Can Forensic Detectors Identify GAN Generated Images?](http://www.apsipa.org/proceedings/2018/pdfs/0000722.pdf)
22. [Deepfake: A Survey on Facial Forgery Technique Using Generative Adversarial Network](https://ieeexplore.ieee.org/document/9065881)
23. [Attributing Fake Images to GANs: Learning and Analyzing GAN Fingerprints](https://arxiv.org/abs/1811.08180)
24. [FakeCatcher: Detection of Synthetic Portrait Videos using Biological Signals](https://arxiv.org/abs/1901.02212)
25. Github: [selimsef/dfdc_deepfake_challenge: A prize winning solution for DFDC challenge (github.com)](https://github.com/selimsef/dfdc_deepfake_challenge)
26. [EfficientNets for DeepFake Detection: Comparison of Pretrained Models](https://ieeexplore.ieee.org/document/9396092)
27. [How far are we from solving the 2D & 3D Face Alignment problem? (and a dataset of 230,000 3D facial landmarks)](https://arxiv.org/abs/1703.07332)
28. [Joint 3D Face Reconstruction and Dense Alignment with Position Map Regression Network](https://arxiv.org/abs/1803.07835)
