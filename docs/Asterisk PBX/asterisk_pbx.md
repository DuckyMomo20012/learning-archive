# Bài tập thực hành 2

Nhóm 05

| Họ và tên          | MSSV     |
| ------------------ | -------- |
| Dương Tiến Vinh    | 19127631 |
| Nguyễn Lê Hữu Sang | 19127538 |

Nhóm 05 -> XX = 05

## 1. Hướng dẫn cài đặt:

- Vào đường link: https://sourceforge.net/projects/asteriskathome/ để tải bản `Trixbox CE` mới nhất **(version 2.8.0.4)**.
- Cài đặt `Trixbox CE` bằng VMware Workstation:
  1. Tạo 1 virtual machine mới.
  2. Chọn Typical.
  3. Chọn "I will install the operating system later".
     > Lưu ý: Không nên chọn option "Installer disc image file" vì nó sẽ gây ra lỗi.
  4. Chọn Guest operating system là "Linux", Version: "CentOS version 5 and earlier 64-bit".
  5. Sau đó khởi động Virtual Machine (VM) và cài đặt bình thường.
  6. Ở màn hình boot, chọn "trixbox-base".
  7. Sau đó đăng nhập vào VM bằng tài khoản:
     - login: `root`.
     - password: Password tạo trong lúc cài đặt.
  8. Sau đó ở máy Host, ta truy cập vào trang web có đường dẫn là **địa chỉ IP của máy VM**. VD: `http://192.168.174.128`.
  9. Xem Asterisk version bằng cách chạy lệnh: `asterisk -v`
     ![asterisk version](https://i.imgur.com/72skYhU.png)
  10. Truy cập vào Asterisk CLI bằng cách chạy lệnh: `asterisk -rvvvvv`
      ![asterisk cli](https://i.imgur.com/cFVXcYG.png)
  11. Ở trang web, ta nhấn nút `switch` để chuyển sang "Admin mode" với thông tin:
      - username: `maint`.
      - password: `password`.

> Lưu ý: Sau khi khởi động thì sẽ hiện dòng chữ: `For access to the trixbox web GUI use this URL: eth0 http://192.168.174.128`, có thể xem ở đây cho tiện truy cập.

## 2. Tạo file âm thanh:

- Tạo file âm thanh:

  - Vào trang https://soundoftext.com/ để nhập nội dung muốn đọc và download file âm thanh ở định dạng mp3:
    ![create sound files](https://i.imgur.com/C6Ja3o0.png)

- Convert từ file `mp3` sang file `wav`:

  - Vào trang: https://www.3cx.com/docs/converting-wav-file/ và dán file mp3 vừa tải. Sau đó tải file wav xuống máy:
    ![convert mp3 file to wav file](https://i.imgur.com/HzpiECY.png)

- Copy file âm thanh vào thư mục: `/var/lib/asterisk/sounds`:

  - Sử dụng phần mềm [FileZilla](https://filezilla-project.org/):
    ![FileZilla demo](https://i.imgur.com/0PG94ON.png)

- Thông tin các đoạn âm thanh:
  - **accounting_department**: "Chúng tôi đang nối máy đến phòng tài vụ, xin quý khách vui lòng đợi trong giây lát"
  - **business_department**: "Chúng tôi đang nối máy đến phòng kinh doanh, xin quý khách vui lòng đợi trong giây lát"
  - **greeting**: "Cảm ơn quý khách đã gọi đến công ty 05".
  - **human_resource_department**: "Chúng tôi đang nối máy đến phòng nhân sự, xin quý khách vui lòng đợi trong giây lát"
  - **incorrect_dial**: "Quý khách đã nhấn sai phím, xin vui lòng nhấn lại theo hướng dẫn"
  - **instruction dial**: "Xin quý khách vui lòng nhấn tiếp số nội bộ hoặc nhấn phím 1 để gặp phòng tài vụ, nhấn phím 2 để gặp phòng nhân sự, nhấn phím 3 để gặp phòng kinh doanh".
  - **open_hours**: "Cảm ơn quý khách đã gọi đến công ty 05. Hiện đang ngoài giờ hành chính, xin quý khách vui lòng gọi lại trong khoảng thời gian từ 7:00 đến 11: 00 hoặc 13:00 đến 17:00. Tạm biệt quý khách"
  - **say_goodbye**: "Cảm ơn quý khách đã gọi đến công ty 05, chúc quý khách một ngày vui vẻ, xin tạm biệt"

## 3. Cài đặt các ứng dụng Softphone:

### 3.1. Tải ứng dụng Softphone:

- Jitsi: version `2.10.5550`:

  - Download tại: https://desktop.jitsi.org/Main/Download.html.
  - Demo:
    ![Jitsi](https://i.imgur.com/AKZ6pAc.png)

- Xlite: version `4.8.0 75944`:
  - Download tại: https://voip24h.vn/file/x-lite-48.exe.
  - Demo:
    ![Xlite demo](https://i.imgur.com/S5YYbeC.png)

### 3.2. Hướng dẫn cài đặt account:

> Lưu ý: Nếu không cài được account thì có thể **reload lại Trixbox** hoặc **thoát hẳn ứng dụng** Jitsi hoặc Xlite.

#### 3.2.1. Cài đặt trên Jitsi:

- Vào File -> Add new account.

![add new account](https://i.imgur.com/5OPftOa.png)

- Sau đó chọn Network là SIP và nhập SIP id là các identity được define trong file `sip.conf` cộng với địa chỉ IP của Trixbox. Sau đó nhập password là `password`.

![account list](https://i.imgur.com/PTLKdPh.png)

- Có thể vào Tools -> Options để xem các số đã cài đặt.

#### 3.2.2. Cài đặt trên Xlite:

- Vào Softphone -> Account settings.

![account settings](https://i.imgur.com/3JQ6fvl.png)

- Sau đó nhập User ID là SIP id là các identity được define trong file `sip.cof`.
- Domain là IP của Trixbox.
- Password là `password`.

## 4. Cấu hình Asterisk:

Cấu hình Asterisk sẽ cần edit các file chính:

- `extensions.conf`: Cấu hình Dialplan.
- `sip.conf`: Cấu hình SIP.
- `voicemail.conf`: Cấu hình Voice mail box.
- `meetme.conf`: Cấu hình Meetme.

## 5. Thông tin chung:

- Tên công ty: `05`.
- Số điện thoại công ty: `7777`.
- Số điện thoại phòng tài vụ (accounting): `6001`.
- Số điện thoại phòng nhân sự (human_resource): `6002`.
- Số điện thoại phòng kinh doanh (business): `6003`.
- Số điện thoại giám đốc (manager): `6004`.
- Số điện thoại để kiểm tra hòm thư Voice Mail: `6500`.
- Số điện thoại để tham gia phòng họp MeetMe: `9059`.
- Ngoài ra còn có số điện thoại sau:
  - `5555`: Số điện thoại bên ngoài để giả lập trường hợp số nội bộ gọi ra bên ngoài.
- Phòng họp MeetMe có số là `0505` với passcode cho nhân viên là `1234` và password quản trị là `123405`.
- Hòm thư Voice Mail có number là `6004` và password là `4321`.

## 6. Cấu hình SIP:

Để cấu hình SIP, ta cần phải chỉnh sửa file `sip.conf`, nên việc backup lại nội dung file `sip.conf` khi mới vừa cài đặt trixbox là cần thiết.

### 6.1. File sip.conf:

```
[default-sip](!)
type=friend
context=internal
host=dynamic
secret=password
disallow=all
allow=ulaw

[accounting](default-sip)

[human_resource](default-sip)

[business](default-sip)

[manager](default-sip)

[outside](default-sip)
context=incoming

[5555](default-sip)
context=incoming
```

### 6.2. Giải thích:

```
[default-sip](!)
type=friend
context=internal
host=dynamic
secret=password
disallow=all
allow=ulaw
```

- Đầu tiên ta có template **"default-sip"** sẽ chứa các settings cần thiết để thiết lập SIP cho các số nội bộ với 1 số settings như sau:
  - `context=internal`: Thuộc nội bộ.
  - `secret=password`: Các danh tính (identity) sẽ có mật khẩu là **"password"**.
  - `disallow=all`: Không cho phép tất cả các loại audio hay video codecs để có thể chấp nhận (accept), hoặc đề nghị (offer).
  - `allow=ulaw`: Chỉ chấp nhận audio codecs là `uLaw`. Hai ứng dụng **Xlite** và **Jitsi** đều hỗ trợ audio codecs này.
    > Lưu ý: Xem thêm các settings khác tại đây: [Asterisk config sip.conf](https://www.voip-info.org/asterisk-config-sipconf/).

---

```
[accounting](default-sip)

[human_resource](default-sip)

[business](default-sip)

[manager](default-sip)

[outside](default-sip)
context=incoming

[5555](default-sip)
context=incoming
```

- Tiếp theo, ta sẽ tạo các identity (hay account) dựa trên template **"default-sip"** (inherit) và override 1 vài settings:
  - `accounting`: identity cho bộ phận tài vụ.
  - `human_resource`: identity cho bộ phận nhân sự.
  - `business`: identity cho bộ phận kinh doanh.
  - `manager`: identity cho giám đốc.
  - `outside`: identity được dùng để giả lập trường hợp gọi từ bên ngoài tới số công ty
    - `context=incoming`: incoming là context mà "outside" sẽ đi vào.
  - `5555`: - `context=incoming`: identity này được dùng để kiểm tra chức năng số nội bộ gọi ra bên ngoài. Ngoài ra, đặt identity này ở context `incoming` để identity `5555` có thể gọi cho số điện thoại công ty.
    > Ngoài ra, nhóm đặt tên là `accounting`, `human_resource`, `business` hay `manager` để khi cấu hình dialplan sẽ dễ nhớ hơn khi đặt tên là `6001`, `6002`, `6003` hay `6004`.

## 7. Cấu hình Dialplan:

Để cấu hình SIP, ta cần phải chỉnh sửa file `extensions.conf`, nên việc backup lại nội dung file `extensions.conf` khi mới vừa cài đặt trixbox là cần thiết.

### 7.1. File extensions.conf:

```
[accounting]
exten => 6001,1,Dial(SIP/accounting)
exten => 6001,n,Hangup()

; Guard to know that incoming call was from outside, not from internal
exten => 7777,1,GotoIf($[${department_num} = 1]?2:4)
exten => 7777,2,Playback(accounting_department)
exten => 7777,3,Dial(SIP/accounting)
exten => 7777,4,Hangup()

[human_resource]
exten => 6002,1,Dial(SIP/human_resource)
exten => 6002,n,Hangup()

exten => 7777,1,GotoIf($[${department_num} = 2]?2:4)
exten => 7777,2,Playback(human_resource_department)
exten => 7777,3,Dial(SIP/human_resource)
exten => 7777,4,Hangup()

[business]
exten => 6003,1,Dial(SIP/business)
exten => 6003,n,Hangup()

exten => 7777,1,GotoIf($[${department_num} = 3]?2:4)
exten => 7777,2,Playback(business_department)
exten => 7777,3,Dial(SIP/business)
exten => 7777,4,Hangup()

[manager]
exten => 6004,1,Dial(SIP/manager,15)
exten => 6004,n,VoiceMail(6004@05-company,u)
exten => 6004,n,Hangup()

; Call 6500 to retrieve the voicemail message.
; When prompted, enter the mailbox number and PIN number: 4321 of the mailbox.
exten => 6500,1,Answer(500)
; Note: You can set 6004@05-company to view specific mailbox
exten => 6500,n,VoiceMailMain(@05-company)

[internal]
include => accounting
include => human_resource
include => business
include => manager
include => meetme

exten => _8.,1,Goto(outgoing,,1)

[outgoing]
; Call 85555 to simulate calling to outside number
exten => _8.,1,Set(outgoing_num=${EXTEN:1})
exten => _8.,n,Dial(SIP/${outgoing_num})
exten => _8.,n,Hangup()

[incoming]
; Check if we are in open hours
exten => 7777,1,GotoIfTime(7:00-11:00,*,*,*?3:2)

; If not then jump to playback line and then hangup
exten => 7777,2,GotoIfTime(13:00-17:00,*,*,*?3:99)

exten => 7777,3,Playback(greeting)

exten => 7777,4,Set(i=0)
exten => 7777,5,While($[${i} < 3])

; Note: terminate string with "#"
exten => 7777,6,Read(department_num,instruction_dial,4)

exten => 7777,7,Verbose(2,${department_num})

exten => 7777,8,GotoIf($[${READSTATUS} = TIMEOUT]?13:9)

exten => 7777,9,GotoIf($[${department_num} = 1]?accounting,7777,1:10)


exten => 7777,10,GotoIf($[${department_num} = 2]?human_resource,7777,1:11)


exten => 7777,11,GotoIf($[${department_num} = 3]?business,7777,1:12)


; If not number 1, 2 or 3, then we will try to search for available
;   extensions in internal context
exten => 7777,12(depart_3),GotoIf($[DIALPLAN_EXISTS(internal,${department_num},1)]?internal,${department_num},1:101)

exten => 7777,13,Set(i=$[${i} + 1])
exten => 7777,14,EndWhile
exten => 7777,15,Playback(say_goodbye)
exten => 7777,16,Hangup()


; This lines can't be put in normal flow, so I
;   have to put it here and finally redirect to hangup line
exten => 7777,99,Playback(open_hours)
exten => 7777,100,Goto(incoming,7777,16)

exten => 7777,101,Playback(incorrect_dial)
exten => 7777,102,Goto(incoming,7777,6)


[meetme]

exten => 9059,1,Goto(conf,1)

exten => conf,1,MeetMe(0505,cM)
exten => conf,n,Hangup()
```

### 7.2. Giải thích:

#### 7.2.1. Gọi điện trong nội bộ:

```
[accounting]
exten => 6001,1,Dial(SIP/accounting)
exten => 6001,n,Hangup()

[human_resource]
exten => 6002,1,Dial(SIP/human_resource)
exten => 6002,n,Hangup()

[business]
exten => 6003,1,Dial(SIP/business)
exten => 6003,n,Hangup()
```

- Đầu tiên, ta tạo 3 context cho từng bộ phận.
- `n` priority tự động tăng giá trị priority lên 1 đơn vị.
- Sau mỗi extension nên chạy Application `Hangup`. Bởi vì sau này ta sẽ `include` các context lại với nhau nên priority `n` có thể thay đổi thất thường. Xem thêm: [Include Statements Basics](https://wiki.asterisk.org/wiki/display/AST/Include+Statements+Basics#:~:text=Be%20careful%20with%20overlapping%20patterns/extensions).
- Tách các bộ phận thành từng context khác nhau để sau này có thể dễ dàng di chuyển tới các context này.

---

```
[internal]
include => accounting
include => human_resource
include => business
```

- Ở context `internal`, ta sẽ `include` các context lại với nhau. Khi các số của các bộ phận gọi tới một số, thì bởi vì người gọi là `accounting`, `human_resource`, `business` thuộc context `internal` nên sẽ vô context này để tìm extension trước, sau khi không match được extension mong muốn sẽ đi tới các context là `accounting`, `human_resource` hay `business` để tìm extension.

#### 7.2.2. Kiểm tra gọi điện trong nội bộ:

![6002 call 6001](https://i.imgur.com/l7yklza.png)

_Gọi từ 6002 (phòng nhân sự) sang 6001 (phòng tài vụ)_

![6001 call 6002](https://i.imgur.com/Zo3PHlz.png)

_Gọi từ 6001 (phòng tài vụ) sang 6002 (phòng nhân sự)_

![6002 call 6003](https://i.imgur.com/AbD00wH.png)

_Gọi từ 6002 (phòng nhân sự) sang 6003 (phòng kinh doanh)_

![6003 call 6002](https://i.imgur.com/HMMXs4G.png)

_Gọi từ 6003 (phòng kinh doanh) sang 6002 (phòng nhân sự)_

#### 7.2.3. Gọi từ nội bộ ra bên ngoài:

```
[internal]
include => accounting
include => human_resource
include => business
include => manager
include => meetme

exten => _8.,1,Goto(outgoing,,1)

[outgoing]
; Call 85555 to simulate calling to outside number
exten => _8.,1,Set(outgoing_num=${EXTEN:1})
exten => _8.,n,Dial(SIP/${outgoing_num})
exten => _8.,n,Hangup()
```

- Đầu tiên, đề yêu cầu nội bộ **phải thêm số 8 vào đầu số muốn gọi ra bên ngoài**. Cho nên extension sẽ dùng pattern `_8.`, nghĩa là số đầu tiên phải là **số 8**, ký tự `.` để match 1 hoặc nhiều ký tự. VD: 85, 877, 834235.
- Sau đó ta sẽ đi đến (`Goto`) context `outgoing` với priority là 1.
  > Lưu ý: Ở đây, Application `Goto` không để extension vì bước sau không thể "cắt" số điện thoại ra được.
- Tiếp theo, ta sẽ "cắt" bỏ số đầu tiên là số 8 khỏi biến `EXTEN`, từ đó ta có được số điện thoại mà nội bộ cần gọi, và lưu số điện thoại đó vào 1 biến tên là `outgoing_num`.
  > Lưu ý: Nếu ta thêm extension vào Application `Goto` ở trên, VD: `exten => _8.,1,Goto(outgoing,_8.,1)`, thì khi này `EXTEN` sẽ có giá trị là `_8.`, khi đó giá trị bị cắt là `8.` chứ không phải số điện thoại được gọi.
- Cuối cùng ta sẽ `Dial` cho account đó.

> Lưu ý: Ở đây có thể cải thiện thêm là có thể kiểm tra xem có extension nào match số được gọi hay không thay vì `Dial` thẳng cho identity (account) đó. Ví dụ như gọi cho 87575 thì extension 7575 có thể có thêm bước phát nhạc hay có thể `Dial` cho account khác.

#### 7.2.4. Kiểm tra gọi từ nội bộ ra ngoài:

Bởi vì ta đã tạo 1 identity là `5555`. Nên ta sẽ bắt đầu gọi cho số `85555` để được điều hướng tới account `5555`:

![6002 call 85555](https://i.imgur.com/PUadlSS.png)

_Gọi từ 6002 (phòng nhân sự) tới 85555 (outgoing)_

#### 7.2.5. Gọi tới công ty:

```
[incoming]
; Check if we are in open hours
exten => 7777,1,GotoIfTime(7:00-11:00,*,*,*?3:2)

; If not then jump to playback line and then hangup
exten => 7777,2,GotoIfTime(13:00-17:00,*,*,*?3:99)

exten => 7777,3,Playback(greeting)

exten => 7777,4,Set(i=0)
exten => 7777,5,While($[${i} < 3])

; Note: terminate string with "#"
exten => 7777,6,Read(department_num,instruction_dial,4)

exten => 7777,7,Verbose(2,${department_num})

exten => 7777,8,GotoIf($[${READSTATUS} = TIMEOUT]?13:9)

exten => 7777,9,GotoIf($[${department_num} = 1]?accounting,7777,1:10)


exten => 7777,10,GotoIf($[${department_num} = 2]?human_resource,7777,1:11)


exten => 7777,11,GotoIf($[${department_num} = 3]?business,7777,1:12)


; If not number 1, 2 or 3, then we will try to search for available
;   extensions in internal context
exten => 7777,12(depart_3),GotoIf($[DIALPLAN_EXISTS(internal,${department_num},1)]?internal,${department_num},1:101)

exten => 7777,13,Set(i=$[${i} + 1])
exten => 7777,14,EndWhile
exten => 7777,15,Playback(say_goodbye)
exten => 7777,16,Hangup()


; This lines can't be put in normal flow, so I
;   have to put it here and finally redirect to hangup line
exten => 7777,99,Playback(open_hours)
exten => 7777,100,Goto(incoming,7777,16)

exten => 7777,101,Playback(incorrect_dial)
exten => 7777,102,Goto(incoming,7777,6)
```

---

```
[incoming]
; Check if we are in open hours
exten => 7777,1,GotoIfTime(7:00-11:00,*,*,*?3:2)

; If not then jump to playback line and then hangup
exten => 7777,2,GotoIfTime(13:00-17:00,*,*,*?3:99)

; This lines can't be put in normal flow, so I
;   have to put it here and finally redirect to hangup line
exten => 7777,99,Playback(open_hours)
exten => 7777,100,Goto(incoming,7777,16)
```

- Đầu tiên thì ta phải kiểm tra xem có trong giờ hành chính (open hours) hay không, nếu không phải thì sẽ nhảy tới priority `99` để phát đoạn âm thanh "open_hours" để báo giờ hành chính và `Hangup`.
  > Lưu ý: Bởi vì đề không yêu cầu là giờ hành chính kéo dài bao nhiêu ngày trong tuần nên ta sẽ thay dấu `*` để không kiểm tra (skip) `weekdays`, `mdays` (days of month), `months` hay `timezone`.
- Ta đặt ở priority `99` bởi vì đoạn âm thanh đó không phù hợp trong flow hiện tại (âm thanh gồm cả đoạn chào quý khách nên đặt sau `Playback(greeting)` cũng không được).

---

```
exten => 7777,3,Playback(greeting)

exten => 7777,4,Set(i=0)
exten => 7777,5,While($[${i} < 3])
```

- Nếu cuộc gọi trong giờ hành chính, ta phát đoạn âm thanh `greeting` để chào quý khách.
- Tiếp theo, ta gán biến `i=0` để sau này chạy vòng `While`.
- Bởi vì đề yêu cầu cho người dùng nhập số 3 lần, nên sẽ cho chạy vòng `While` với: `i < 3`.

---

```
; Note: terminate string with "#"
exten => 7777,6,Read(department_num,instruction_dial,4)

exten => 7777,7,Verbose(2,${department_num})
```

- Application `Read` sẽ lưu số người dùng nhập vào biến `department_num`. Ngoài ra, ta chỉ **cho người dùng nhập đúng 4 số**.
- Người dùng có thể dừng quá trình nhập số bằng cách nhập dấu `#`. VD: `1#`, `2#` hay `3#`.
- Khi yêu cầu người dùng nhập sẽ chạy 1 đoạn âm thanh "instruction_dial" hướng dẫn người dùng.

---

```
; Note: terminate string with "#"
exten => 7777,6,Read(department_num,instruction_dial,4)

exten => 7777,7,Verbose(2,${department_num})

exten => 7777,8,GotoIf($[${READSTATUS} = TIMEOUT]?13:9)

exten => 7777,9,GotoIf($[${department_num} = 1]?accounting,7777,1:10)


exten => 7777,10,GotoIf($[${department_num} = 2]?human_resource,7777,1:11)


exten => 7777,11,GotoIf($[${department_num} = 3]?business,7777,1:12)


; If not number 1, 2 or 3, then we will try to search for available
;   extensions in internal context
exten => 7777,12(depart_3),GotoIf($[DIALPLAN_EXISTS(internal,${department_num},1)]?internal,${department_num},1:101)

exten => 7777,13,Set(i=$[${i} + 1])
exten => 7777,14,EndWhile
exten => 7777,15,Playback(say_goodbye)
exten => 7777,16,Hangup()
```

- Bởi vì Application `Read` sẽ set một biến toàn cục là `READSTATUS`, nên ta có thể đọc thông tin đó.
- Khi người dùng không nhập gì thì `READSTATUS` sẽ được set là `TIMEOUT` thì ta sẽ đi đến priority thứ `11` để tăng giá trị biến `i` lên 1 đơn vị.
- Sau khi timeout 3 lần thì sẽ thoát vòng lặp và phát đoạn âm thanh "say_goodbye" để chào tạm biệt.
- Khi người dùng có nhập 1 số thì sẽ kiểm tra từ đó nhảy tới context tương ứng.
- Nếu không đúng thì sẽ đi tới priortity tiếp theo.
  > Lưu ý: Ở đây bởi vì các trường hợp false clause đi liền mạch với nhau, nên có thể lược bớt false clause ở sau Application `GotoIf` (ngoại trừ priority 12 khi false sẽ nhảy tới priority 101).
- Nếu không phải là 1, 2 hay 3 thì ta sẽ kiểm tra xem trong context `internal` có extension để xử lý hay không.

---

```
exten => 7777,101,Playback(incorrect_dial)
exten => 7777,102,Goto(incoming,7777,6)
```

- Nếu không có trường hợp nào match, nghĩa là người dùng nhập sai thì sẽ phát âm thanh "incorrect_dial" để thông báo cho người nhập sai và vòng lại priority 6 để yêu cầu người dùng nhập lại (nhưng không tăng biến `i`).

> Lưu ý: Ở context `incoming` này ta không dùng priority `n`, kể cả priority alias bởi vì flow không liền mạch (nhảy giữa các context) làm cho flow bị gián đoạn (lặp vòng `While` liên tục) từ đó khó cấu hình hơn.

---

```
; Guard to know that incoming call was from outside, not from internal
exten => 7777,1,GotoIf($[${department_num} = 1]?2:4)
exten => 7777,2,Playback(accounting_department)
exten => 7777,3,Dial(SIP/accounting)
exten => 7777,4,Hangup()

exten => 7777,1,GotoIf($[${department_num} = 2]?2:4)
exten => 7777,2,Playback(human_resource_department)
exten => 7777,3,Dial(SIP/human_resource)
exten => 7777,4,Hangup()

exten => 7777,1,GotoIf($[${department_num} = 3]?2:4)
exten => 7777,2,Playback(business_department)
exten => 7777,3,Dial(SIP/business)
exten => 7777,4,Hangup()
```

- Trong từng bộ phận, ta phải có extension để tiếp nhận cuộc gọi tới `7777` là số điện thoại công ty.
- Sau đó sẽ phát đoạn âm thanh tương ứng với từng bộ phận như: "accounting_department", "human_resource_deparment" hay "business_department".
- Tuy nhiên để các số nội bộ không gọi được cho số `7777` (gọi số công ty rồi lại redirect tới các số phòng ban thì không hợp lý), ta phải đặt một điều kiện là `department_num` (guard), bởi vì biến này chỉ được set khi từ bên ngoài gọi tới số công ty.

---

```
[manager]
exten => 6004,1,Dial(SIP/manager,15)
exten => 6004,n,VoiceMail(6004@05-company,u)
exten => 6004,n,Hangup()
```

- Số điện thoại khi gọi tới phòng giám đốc sẽ có thời gian timeout là **15 giây**.
- Nếu người dùng bận hoặc quá thời gian timeout sẽ được chuyển tới Voice Mail.
- Phần voice mail sẽ được nhắc tới ở phần tiếp theo.

#### 7.2.6. Kiểm tra cuộc gọi tới công ty:

![outside call 6001](https://i.imgur.com/A2KwDw8.png)

_Cuộc gọi từ outside tới 6001 (phòng tài vụ)_

![outside call 6002](https://i.imgur.com/mzZUj6U.png)

_Cuộc gọi từ outside tới 6002 (phòng nhân sự)_

![outside call 6003](https://i.imgur.com/TNUQCv1.png)

_Cuộc gọi từ outside tới 6003 (phòng kinh doanh)_

## 8. Cấu hình VoiceMail:

Để cấu hình Voice Mail, ta cần phải chỉnh sửa file `voicemail.conf` ở cuối file:

### 8.1. File voicemail.conf:

![voicemail.conf file](https://i.imgur.com/23YNn3D.png)

```
conf => 0505,1234,123405
```

- Đầu tiên ta tạo 1 mailbox có number là `6004` và password là `4321`.

![Asterisk CLI to reload voice mail to read mail box](https://i.imgur.com/xUJolRG.png)

- Sau khi cấu hình xong, ta phải chạy lệnh: `voicemail reload` ở Asterisk CLI.
- Sau đó ta có thể xem số lượng thư bằng cách chạy lệnh: `voicemail show users`.

### 8.2. Cấu hình Voice Mail:

```
[manager]
exten => 6004,1,Dial(SIP/manager,15)
exten => 6004,n,VoiceMail(6004@05-company,u)
exten => 6004,n,Hangup()

; Call 6500 to retrieve the voicemail message.
; When prompted, enter the mailbox number and PIN number: 4321 of the mailbox.
exten => 6500,1,Answer(500)
; Note: You can set 6004@05-company to view specific mailbox
exten => 6500,n,VoiceMailMain(@05-company)
```

- Khi cuộc gọi tới giám đốc (6004) **quá 15 giây** hoặc **đang bận** (busy) thì người dùng sẽ tự động chuyển sang Voice Mail với hòm thư số `6004` thuộc context `05-company`.
  > Lưu ý: nếu không set giá trị timeout cho Application `Dial` thì người gọi sẽ phải **đợi 136 năm** mới được chuyển sang Voice Mail.
- Option `u`: Khi người dùng "unvailable" thì sẽ phát 1 đoạn âm thanh thông báo.
- Khi này đoạn voice mail sẽ được lưu vào hòm mailbox là `6004` thuộc context `05-comany`.
- Ngoài ra, ta cũng tạo thêm 1 extension là `6500` để khi gọi tới thì có thể nghe được voice mail.
- Khi gọi tới thì tổng đài sẽ yêu cầu người dùng nhập số mail box, theo sau đó là password.
- Nếu ở Application `VoiceMailMain`, ta set `VoiceMailMain(6004@05-company)` thì lúc này khi gọi tới `6500` để kiểm tra thư thì sẽ kiểm tra đúng một hòm thư là `6004`, nên chỉ cần nhập password là `4321`.

> Lưu ý: Mặc dù extension `6500` được đặt trong context `manager`, tuy nhiên sau này context `manager` sẽ được `include` vào trong context `internal` nên **trong nội bộ ai cũng có thể truy cập extension này**. Nhóm đặt extension `6500` ở context `manager` để cho thấy (ám chỉ) hòm thư này thuộc về giám đốc (manager).

## 9. Cấu hình Meetme:

### 9.1. File meetme.conf:

![meetme.conf file](https://i.imgur.com/V89kACD.png)

```
[rooms]
conf => 0505,1234,123405
```

### 9.2. Giải thích:

```
conf => 0505,1234,123405
```

- Ta sẽ tạo 1 phòng họp có số là `0505` với passcode cho nhân viên là `1234` và password cho quản trị viên là `123405`.

---

```
[meetme]

exten => 9059,1,Goto(conf,1)

exten => conf,1,MeetMe(0505,cM)
exten => conf,n,Hangup()
```

- Đầu tiên ta sẽ tạo context `meetme` và thêm 1 extension là `9059`, khi đó nhân viên gọi tới đầu số này sẽ được thêm vào phòng họp `0505`.
- Các option:
  - `c`: Thông báo số lượng thành viên hiện đang có trong phòng. Nếu phòng có 2 người, thì người mới vô sẽ được thông báo hiện có 2 người trong phòng.
  - `M`: Khi trong phòng chỉ có đúng 1 người thì nhạc chờ trong phòng sẽ được bật lên.
- Khi người tham gia quay số thì sẽ phải nhập password là `1234` cho nhân viên và `123405` cho quản trị viên.

---

```
[internal]
include => accounting
include => human_resource
include => business
include => manager
include => meetme

exten => _8.,1,Goto(outgoing,,1)
```

- Và tất nhiên ta phải `include` context `meetme` vào context `internal` để chỉ có nội bộ mới có thể gọi tới số `9059` và tham gia vào phòng họp `0505`.

### 9.3. Kiểm tra cuộc gọi trong phòng họp:

![conference room](https://i.imgur.com/dTtQLll.png)

_Phòng họp 0505 gồm 4 thành viên là 6001 (phòng tài vụ), 6002 (phòng nhân sự), 6003 (phòng kinh doanh) với password là 1234, và 6004 (giám đốc) là quản trị phòng với password là 123405_

## 10. Tài liệu tham khảo:

- Telecomworld101.com. 2022. Asterisk Configuration files - PBX in a Flash for Newbies. [online] Available at: <https://www.telecomworld101.com/PiaF/ConfigurationFiles.html> [Accessed 8 July 2022].
- 2022. [online] Available at: <https://nsrc.org/workshops/2009/pacnog5/track4/presos/PacNOG5_voip_asterisk_basic.pdf> [Accessed 8 July 2022].
- 2022. Asterisk basic configuration: SIP Extensions. [video] Available at: <https://youtu.be/EnUCYgJ30CM> [Accessed 8 July 2022].
- Wiki.asterisk.org. 2022. Hello World - Asterisk Project - Asterisk Project Wiki. [online] Available at: <https://wiki.asterisk.org/wiki/display/AST/Hello+World> [Accessed 8 July 2022].
- Info, V., 2022. Asterisk config sip.conf - VoIP-Info. [online] VoIP-Info. Available at: <https://www.voip-info.org/asterisk-config-sipconf/> [Accessed 8 July 2022].
- Info, V., 2022. Asterisk config meetme.conf - VoIP-Info. [online] VoIP-Info. Available at: <https://www.voip-info.org/asterisk-config-meetmeconf/> [Accessed 8 August 2022].
- Info, V., 2022. Asterisk cmd MeetMe Command - VoIP-Info. [online] VoIP-Info. Available at: <https://www.voip-info.org/asterisk-cmd-meetme/> [Accessed 8 August 2022].
- Info, V., 2022. Asterisk cmd GotoIfTime - VoIP-Info. [online] VoIP-Info. Available at: <https://www.voip-info.org/asterisk-cmd-gotoiftime/> [Accessed 8 August 2022].
- Ftp.unpad.ac.id. 2022. MeetMe (dialplan application). [online] Available at: <https://ftp.unpad.ac.id/orari/library/library-sw-hw/linux-1/sip/asterisk/asterisk/docs/meetme.html> [Accessed 8 August 2022].
