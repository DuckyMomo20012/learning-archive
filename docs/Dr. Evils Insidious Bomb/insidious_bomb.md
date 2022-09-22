# Đồ án 4

| Họ và tên       | MSSV     |
| --------------- | -------- |
| Dương Tiến Vinh | 19127631 |

## Phase 1:

![Untitled](https://user-images.githubusercontent.com/64480713/191879320-a703d1da-dc43-4840-abe7-5ed058d8159e.png)

- Sử dụng phần mềm IDA, em có thể nhảy tới phase 1 để tìm key
- Có thể thấy chương trình sẽ gọi 1 instruction `string_not_equal` để compare chuỗi nhập vào.
- Khi so sánh chuỗi nhập vào không giống với (equal) `aScienceIsnTAbo` thì sẽ trả về 1 và gán vào thanh ghi `eax`.
- Khi đó ở bước `test eax, eax` thì `eax & eax` = `1 & 1 = 1` thì lúc đó `jz` sẽ nhảy vào bước false là `explode_bomb`.
- Ngược lại, nếu compare chuỗi nhập vào giống với (equal) `aScienceIsnTAbo` thì sẽ trả về 0 và gán vào `eax`.
- Khi đó ở bước `test eax, eax` thì `eax & eax` = `1 & 1 = 1` thì lúc đó `jz` sẽ nhảy vào bước true là kết thúc hàm `phase_1` và giải được phase_1.

![Untitled 1](https://user-images.githubusercontent.com/64480713/191879329-477dd368-bf94-465c-9f19-0c5fcb064c6b.png)

- Khi `Jump to operand`, em có thể chuỗi để so sánh là: **“Science isn't about why, it's about why not?”**

![Untitled 2](https://user-images.githubusercontent.com/64480713/191879335-4ce894f8-bfe0-42f1-b479-d03db139c5a2.png)

- Khi nhập chuỗi đó vào thì sẽ giải được phase 1.

> Key phase 1: **Science isn't about why, it's about why not?**

- Sau đó copy chuỗi key vào file `defuse.txt` để sau này chạy thì chương trình sẽ tự động đọc key phase 1 vào pass qua phase 2.

```
Science isn't about why, it's about why not?
```

> Lưu ý: Phải save file `defuse.txt` dưới dạng `LF`.

## Phase 2:

- Ta sẽ có flow cho phase 2 như sau:

![Untitled 3](https://user-images.githubusercontent.com/64480713/191879336-fddb5a39-7a67-4f44-bceb-d85651bece33.png)

![Untitled 4](https://user-images.githubusercontent.com/64480713/191879340-321d243f-813e-452c-bc09-ab4d375e3ea2.png)

- Đầu tiên ta sẽ disasssembly hàm main trước

![Untitled 5](https://user-images.githubusercontent.com/64480713/191879342-af71b166-4c2e-4ffa-ab46-182b0753e76f.png)

- Hàm `phase_2` ở `main+172`, nên ta sẽ set breakpoint ở điểm đó bằng lệnh:

```
b *main+172
```

![Untitled 6](https://user-images.githubusercontent.com/64480713/191879344-59dab700-e3fd-4fe6-af3b-c7abf6dd5756.png)

- Sau đó ta sẽ chạy chạy chương trình với argument là file `defuse.txt`:

```
run defuse.txt
```

![Untitled 7](https://user-images.githubusercontent.com/64480713/191879348-652d1e6d-77d4-4b08-afc2-a22f207d6e58.png)

- Đầu tiên, ta sẽ thử với chuỗi ngẫu nhiên sau: **“4 2 1 5 3 7”**

![Untitled 8](https://user-images.githubusercontent.com/64480713/191879350-b41ec4f0-efea-4ec7-b254-61d6c7faecf9.png)

- Sau đó chạy lệnh `step` để đi vào function `phase_2`:
- Trong quá trình debug có thể sử dụng các lệnh sau:

  ```
  step: step vào function
  n: Step sang bước tiếp theo
  p $eax: In thanh ghi $eax
  x /w $eax: In thanh ghi $eax
  p /x *(int *)($eax): In thanh ghi $eax
  ```

- Khi step đến hàm `read_six_numbers`, ta có step vô function này để kiểm tra

![Untitled 9](https://user-images.githubusercontent.com/64480713/191879352-2aa1b9d9-97e4-42fe-844c-d2a6ac43907f.png)

- Có thể thấy hàm này cuối cùng sẽ `cmp`, so sánh `$eax` với giá trị `0x5` (=5). Nếu lớn hơn `jg` thì sẽ đi tới vị trí khác, còn nếu nhỏ hơn thì sẽ chạy `explode_bomb`.

> Vì vậy ta có thể biết được chuỗi **key sẽ gồm 6 số.**

![Untitled 10](https://user-images.githubusercontent.com/64480713/191879354-4e5b2d69-74bb-4a8b-a3f7-05c9609114b8.png)

- Sau đó ta sẽ `cmp` giá trị `$eax` với giá trị `[rbp+0x0]`. Sau khi in ra từng giá trị ta có được như sau:
  - `$eax`: 5
  - `$rbp+0x0`: 4
- Để có thể đi tiếp ta thì `$eax` và `$rbp+0x0` phải bằng nhau `je`.

> ~~Vì vậy chuỗi **key phải bắt đầu là số 5**.~~

> Lưu ý: Không nhất thiết phải bắt đầu là số 5, **chỉ cần số thứ 1 bằng số thứ 4**.

![Untitled 11](https://user-images.githubusercontent.com/64480713/191879357-5f70e35a-f430-4a77-a174-eeb552d6489a.png)

- Tiếp theo ta sẽ thử bằng chuỗi: **“5 4 2 1 3 7”**
- Tới bước `cmp` tiếp theo, ta sẽ thấy phải so sánh `$eax` bằng (`je`) với `$rbp+0x0`.
- Nhưng có thể thấy giá trị như sau:
  - `$eax`: 1
  - `$rbp+0x0`: 5

> Từ đó có thể thấy **giá trị thứ 4 của chuỗi key phải là số 5**.

![Untitled 12](https://user-images.githubusercontent.com/64480713/191879359-06bbe37e-9894-42e3-877f-d4f57468680d.png)

- Tiếp theo ta sẽ thử bằng chuỗi: **“5 4 2 5 3 7”**
- Tới bước `cmp` tiếp theo, để có tránh `explode_bomb`, thì `jne` phải **false**, do đó phải so sánh `$rbp` khác (not `jne`) với `$r13`.
- Có thể thấy giá trị như sau:
  - `$rbp`: 4
  - `$r13`: 5
- Ta sẽ quay lại dòng `cmp` trước đó với giá trị như sau:
  - `$eax`: 3
  - `rbp+0x0`: 4

> Từ đó có thể thấy **giá trị thứ 2 và thứ 5 của chuỗi key phải bằng nhau**.

![Untitled 13](https://user-images.githubusercontent.com/64480713/191879360-e7eac635-9c42-457b-8147-94c9b9bb1b96.png)

- Tiếp theo ta sẽ thử bằng chuỗi: **“5 4 2 5 4 7”**
- Có thể thấy giá trị như sau:
  - `$rbp`: 2
  - `$r13`: 5

> Từ đó có thể thấy **giá trị thứ 3 của chuỗi key phải là số 5**.

![Untitled 14](https://user-images.githubusercontent.com/64480713/191879364-7f0fab03-3bfb-4e58-be46-1fdebf46ea13.png)

- Tiếp theo ta sẽ thử bằng chuỗi: **“5 4 5 5 4 7”**
- Sau một hồi chạy `cmp` thì ta sẽ gặp một `cmp` so sánh giữa `$eax` và `$rbp+0x0`, để tránh `explode_bomb` ta phải so sánh bằng `je`.
- Có thể thấy giá trị như sau:
  - `$eax`: 7
  - `$rbp+0x0`: 5

> Từ đó có thể thấy **giá trị thứ 6 của chuỗi key phải là số 5**.

![Untitled 15](https://user-images.githubusercontent.com/64480713/191879369-d960257f-0177-4e08-a3ca-0d9bb3680a0b.png)

- Tiếp theo ta sẽ thử bằng chuỗi: **“5 4 5 5 4 5”**
- Có thể thấy phase đã được giải.

![Untitled 16](https://user-images.githubusercontent.com/64480713/191879371-4e2ab477-3fce-4e71-b468-1f82227968a2.png)

> Vậy key cho phase 2 là: **“5 x 5 5 x 5”** với **x bằng nhau**.

![Untitled 17](https://user-images.githubusercontent.com/64480713/191879374-c6de82bb-fe6d-4c0c-876b-483a0b05fae8.png)

![Untitled 18](https://user-images.githubusercontent.com/64480713/191879376-33e833ad-06d8-4754-bef7-e7cacc70c787.png)

> Key phase 2: **“5 x 5 5 x 5”** với **x bằng nhau**.

- Sau đó copy chuỗi key vào file `defuse.txt` để sau này chạy thì chương trình sẽ tự động đọc key và qua phase tiếp theo.

```
Science isn't about why, it's about why not?
5 4 5 5 4 5
```

## Phase 3:

- Đầu tiên ta sẽ có flow như sau:

![Untitled 19](https://user-images.githubusercontent.com/64480713/191879377-09e7139c-3257-4eb3-a4b8-5daeb06c132c.png)

- Người dùng sẽ phải nhập vào 2 số.
- Và có thể thấy sẽ có 1 hàm `switch` để chạy các trường hợp
- Đầu tiên ta sẽ thử với input **“8 4”**
- Có thể thấy để vượt qua hàm `cmp` thì `$rsp+0xc` phải nhỏ hơn 8:
- Ta có được thông tin sau:
  - `$rsp+0xc`: 8

> Từ đó có thể thấy **giá trị thứ 1 của chuỗi key phải nhỏ hơn 8**.

![Untitled 20](https://user-images.githubusercontent.com/64480713/191879378-ada3e3ab-bb4f-475b-ac3d-e0ee062eb931.png)

- Tiếp theo ta sẽ thử với chuỗi **“1 4”**
- Để vượt qua hàm `cmp` tiếp theo, thì `$eax` phải bằng với `$rsp+0x8`:
- Ta có được thông tin:
  - `$eax`: `0x39e`= 926
  - `$rsp+0x8`: 4

> Từ đó có thể thấy với trường hợp **số đầu tiên là số 1 thì số thứ hai phải là 926**

![Untitled 21](https://user-images.githubusercontent.com/64480713/191879382-16a421e7-865e-45b9-aa31-fa66507bbf5e.png)

- Tiếp theo ta sẽ thử với chuỗi: **“1 926”**
- Có thể thấy phase 3 đã được giải:

![Untitled 22](https://user-images.githubusercontent.com/64480713/191879384-f634e71b-72da-4b00-867b-5e1d6b731056.png)

- Có thể sử dụng phần mềm IDA để xem các trường hợp khác nhanh hơn:

![Untitled 23](https://user-images.githubusercontent.com/64480713/191879385-efe5b717-db2e-43dc-a649-876f7834a8aa.png)

- Sau khi áp dụng cách trên với các trường hợp từ 0 → 7, ta được như sau:

> Key phase 3:
>
> ```
> 0 535
> 1 926
> 2 214
> 3 339
> 4 119
> 5 352
> 6 919
> 7 412
> ```

- Sau đó copy chuỗi key vào file `defuse.txt` để sau này chạy thì chương trình sẽ tự động đọc key và qua phase tiếp theo.

```
Science isn't about why, it's about why not?
5 4 5 5 4 5
0 535
```

## Phase 4:

- Phase 4 có flow như sau:

![Untitled 24](https://user-images.githubusercontent.com/64480713/191879386-59b7ffab-01f2-4122-b250-1a60e087ea8e.png)

![Untitled 25](https://user-images.githubusercontent.com/64480713/191879387-22c5b322-302a-4cf5-a8cc-9729a3900288.png)

- Đầu tiên ta sẽ thử với chuỗi **“0”**:
- Để có thể vượt qua hàm `cmp` thì `$rsp+0xc` phải lớn hơn 0:
- Ta có được thông tin:
  - `$rsp+0xc`: 0

> Từ đó có thể thấy **giá trị thứ 1 của chuỗi key phải lớn hơn 0**

![Untitled 26](https://user-images.githubusercontent.com/64480713/191879389-627ddbeb-d4c7-469b-a284-79d44eb99015.png)

- Tiếp theo ta sẽ thử với chuỗi: **“1”**:
- Sau đó ta sẽ step vào `func4`, để vượt qua được `cmp` thì phải nhỏ hơn bằng 1

![Untitled 27](https://user-images.githubusercontent.com/64480713/191879392-2b4f8a44-f8c2-49e3-bf78-e9ab93102f69.png)

- Nhưng sau đó thì khi tới `cmp` tiếp theo, để vượt qua `cmp` này thì `$eax` phải bằng 55:
- Ta có được thông tin:
  - `$edi`: 1
- Nên sẽ không qua được `cmp` này

> Từ đó có thể thấy **giá trị thứ 1 của chuỗi key phải lớn hơn 1**

![Untitled 28](https://user-images.githubusercontent.com/64480713/191879395-a581ae54-771d-4dda-b1a6-72aeb16bbf7a.png)

- Vì nghi đây là bài toán đệ quy, nên ta sẽ thử lần lượt các số từ 1 → 8 để mò sao cho `$eax` = 55:

```
1 -> $eax = 1
2 -> $eax = 2
3 -> $eax = 3
4 -> $eax = 5
5 -> $eax = 8
6 -> $eax = 13
7 -> $eax = 21
8 -> $eax = 34
```

> Từ đó có thể đoán **đó là dãy số Fibonacci!**

- Hoặc đơn giản hơn là dùng IDA Pro để decompile `func4`:

![Untitled 29](https://user-images.githubusercontent.com/64480713/191879396-5b7650ef-6eab-436d-ac07-d20af0431f5b.png)

- Vậy để `$eax` bằng 55 thì chỉ có thể là 9

![Untitled 30](https://user-images.githubusercontent.com/64480713/191879399-106c354a-20cf-44a1-83e8-eb6315cc6618.png)

> Key phase 4: **“9”**

- Sau đó copy chuỗi key vào file `defuse.txt` để sau này chạy thì chương trình sẽ tự động đọc key và qua phase tiếp theo.

```
Science isn't about why, it's about why not?
5 4 5 5 4 5
0 535
9
```

## Phase 5:

- Ta có flow như sau:

![Untitled 31](https://user-images.githubusercontent.com/64480713/191879400-f8fe42e9-a372-4e9c-acf3-4256a3c628e7.png)

![Untitled 32](https://user-images.githubusercontent.com/64480713/191879403-f4e9f8aa-9ed1-47e8-a472-89c2e3733597.png)

- Ta sẽ nhập 2 số cho phase này:
  - `[rsp+18h+var_C]` là giá trị đầu tiên của chuỗi key
  - `[rsp+18h+var_10]` là giá trị thứ hai của chuỗi key
- Mục tiêu chính của phase này nằm ở hình 2.
- Ta cần phải chú ý `edx` và `ecx`.
- `edx` chỉ được tăng khi chạy lại block `loc_401043`, nên nhiệm vụ của ta để pass được `cmp edx, 12` là lặp lại block `loc_401043` lại **đúng 12 lần**.
- Nhưng vòng lặp chỉ kết thúc khi **giá trị `eax` bằng 15**, mà giá trị `eax` được gán bằng giá trị của `array_3014` tại vị trí (`rax*4`)
- Ở đây `rax` là `eax`, cũng là số tự nhiên đầu tiên của chuỗi key. Bởi vì ở dòng `mov eax, [rsp+18h+var_C]` thì `eax` đã được gán lại giá trị đầu tiên của chuỗi key.
- Ta có `array_3014` như sau:
  - `0x0000000a`: tại vị trí `array_3014[4 * 0]`
  - `0x00000002`: tại vị trí `array_3014[4 * 1]`
  - …
  - `0x00000005`: tại vị trí `array_3014[4 * 15]`
- VD: `rax` = 4 thì giá trị `eax` tiếp theo sẽ được gán bằng `array_3014[rax * 4]` = `array_3014[4 * 4]` = `array_3014[16]` = `0x00000008` = 8.
- Lưu ý: Nếu `rax` lớn hơn 15 thì sẽ về 0 vì đã `and eax 1111`.
  - VD: `16 = 10000 & 01111 = 0`
- Chuyển đổi sang số tự nhiên ta sẽ được như sau:

```
 0| 10 2  14 7
16| 8  12 15 11
32| 0  4  1  13
48| 3  9  6  5
```

![Untitled 33](https://user-images.githubusercontent.com/64480713/191879405-1af582bc-2d43-43ba-a39a-1a8dea8758a8.png)

- Ở `cmp ecx, [rsp+18h+var_10]`, ta chỉ cần nhập số thứ hai của chuỗi chỉ cần bằng `ecx` là pass được.
- Em đã viết chương trình python để giải vấn đề này thay vì phải brute force từ 0 → 15:
- Với:
  - `input_val`: là giá trị `rax` (=`eax`) và là số đầu tiên của chuỗi key
  - `res`: là giá trị `ecx` và sẽ được so sánh với số thứ hai của chuỗi key. Ta cần hai giá trị này bằng nhau để defuse.
  - `i`: là giá trị `edx`

```python
array = [10, 2, 14, 7, 8, 12, 15, 11, 0, 4, 1, 13, 3, 9, 6, 5]

for input_val in range(16):

    # Store the iteration number
    tmp = input_val

    result = 0
    i = 0
    while True:
        i += 1
        input_val = array[input_val % 16]
        result += input_val
        if input_val == 15:
            break

    print("iter: {}, input_val: {}, result: {}".format(i, tmp, result))
```

- Và khi `input_val` bằng 7 thì ta sẽ dừng ở giá trị 15, khi đó `eax` sẽ bằng 15 và ta sẽ pass được `cmp eax, 15`.
- Tiếp theo khi `input_val` bằng 7 thì ta sẽ có đúng 12 iteration, khi đó `edx` sẽ bằng đúng 12 và ta sẽ pass được `cmp edx, 12`.
- Sau khi pass `cmp edx, 12` thì ta sẽ so sánh `ecx` thì ta chỉ cần nhập đúng giá trị thứ hai của chuỗi key là `93` là được.

![Untitled 34](https://user-images.githubusercontent.com/64480713/191879407-8087fa36-0a98-4097-822e-562dfdeeb34c.png)

- Sau đó ta sẽ giải được phase 5:

![Untitled 35](https://user-images.githubusercontent.com/64480713/191879409-9a547987-bd84-42e2-bf6c-9f8994a21540.png)

- Bởi vì giá trị nhập vào đầu tiên sẽ được gán vào `eax` và `AND` với `1111 = 16` nên ta sẽ có công thức cho key phase 5 như sau:

```
Giá trị đầu tiên: (x * 16 + 7), với x: 0...n
Giá trị thứ hai: 93
```

> Key phase 5: **“7 93”**

- Sau đó copy chuỗi key vào file `defuse.txt` để sau này chạy thì chương trình sẽ tự động đọc key và qua phase tiếp theo.

```
Science isn't about why, it's about why not?
5 4 5 5 4 5
0 535
9
7 93
```
