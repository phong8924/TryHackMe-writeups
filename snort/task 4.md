# 🐍 Tương tác đầu tiên với Snort

Sau khi cài đặt thành công và làm quen với Snort, chúng ta sẽ tiến hành một vài bước kiểm tra ban đầu để đảm bảo Snort đã được cài đặt đúng cách và cấu hình hoạt động bình thường.

---

## 1. Kiểm tra phiên bản của Snort

Đầu tiên, hãy chạy lệnh sau để xác minh rằng Snort đã được cài đặt và hiển thị phiên bản:

```bash
snort -V
```

Kết quả mẫu:

```
   ,,_     -*> Snort! <*-
  o"  )~   Version 2.9.7.0 GRE (Build 149) 
   ''''    By Martin Roesch & The Snort Team: http://www.snort.org/contact#team
           Copyright (C) 2014 Cisco and/or its affiliates. All rights reserved.
```

> **Câu hỏi:** Chạy lệnh trên và kiểm tra số build của Snort.

> ✅ **Đáp án:** `149`

---

## 2. Kiểm tra cấu hình của Snort

### a. Kiểm tra với file `/etc/snort/snort.conf`

```bash
sudo snort -c /etc/snort/snort.conf -T
```

Nếu cấu hình hợp lệ, Snort sẽ trả về:

```
Snort successfully validated the configuration!
Snort exiting
```

> **Câu hỏi:** Có bao nhiêu rule được load từ file `snort.conf`?

> ✅ **Đáp án:** `4151`

---

### b. Kiểm tra với file `/etc/snort/snortv2.conf`

```bash
sudo snort -c /etc/snort/snortv2.conf -T
```

> **Câu hỏi:** Có bao nhiêu rule được load từ file `snortv2.conf`?

> ✅ **Đáp án:** `1`

---

## 3. Tham số dòng lệnh cơ bản của Snort

| Tham số      | Mô tả |
|--------------|-------|
| `-V` hoặc `--version` | Hiển thị thông tin phiên bản. |
| `-c`         | Chỉ định file cấu hình sử dụng. |
| `-T`         | Kiểm tra file cấu hình (không chạy thực tế). |
| `-q`         | Chế độ yên lặng – không hiển thị banner Snort. |

---

## 4. Tổng kết

✅ Kiểm tra thành công phiên bản Snort  
✅ Xác minh được file cấu hình chính xác và rule đã được load

