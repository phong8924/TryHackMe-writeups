### Task 3: The NTFS File System
**Cau 1:** Parse the `$MFT` file placed in `C:\users\THM-4n6\Desktop\triage\C\` and analyze it. What is the Size of the file located at `.\Windows\Security\logs\SceSetupLog.etl`  
B1:  Xác định tệp `$MFT`
Nó là `C:\users\THM-4n6\Desktop\triage\C\$MFT`
B2:  Phân tích tệp `$MFT`
![alt text](<../png/Windows Forensics 1/15.png>)
Kqua đã được lưu lại
B3: Mở công cụ EZviewer để xem kết quả
![alt text](<../png/Windows Forensics 1/14.png>)
>Đáp án: Kích thước của tệp `.\Windows\Security\logs\SceSetupLog.etl` là `49152` bytes.

**Câu 2:** What is the size of the cluster for the volume from which this triage was taken?
câu này chuyển sang phân tích cluster size của volume (tức là kích thước đơn vị cấp phát của NTFS).
Trong forensic với MFTECmd, thông tin này không nằm trong `$MFT`, mà nằm trong `$Boot` (NTFS boot sector). Ta đi phân tích tệp `$Boot`.
![alt text](<../png/Windows Forensics 1/16.png>)

Lại mở công cụ EZviewer để xem kết quả
![alt text](<../png/Windows Forensics 1/17.png>)
>Đáp án: Kích thước cluster của volume là `4096` bytes.

### Task 4:
Trả lời các câu hỏi dưới đây

**1. Có một tệp xlsx khác đã bị xóa. Tên đầy đủ của tệp đó là gì?**  
*Tryhackme.xlsx*
![alt text](<../png/Windows Forensics 1/18.png>)

**2. Tên của tệp TXT đã bị xóa khỏi đĩa là gì?**  
*TryHackMe2.txt*

---

**3. Khôi phục tệp TXT từ Câu hỏi số 2. Nội dung trong tệp txt này là gì?**  
*thm-4n6-2-4*


### Task 5:
Trả lời các câu hỏi dưới đây

**Câu 1:** gkape.exe được thực thi bao nhiêu lần?
chạy lệnh
![alt text](<../png/Windows Forensics 1/19.png>)
dùng EZviewer để xem kết quả
![alt text](<../png/Windows Forensics 1/20.png>)
>**Đáp án:** gkape.exe được thực thi 2 lần.

**Câu 2:** Thời gian thực thi cuối cùng của gkape.exe là bao lâu?
cay vcl
từ câu trên thấy được đường dẫn của file, phân tích nó
![alt text](<../png/Windows Forensics 1/21.png>)
>**Đáp án:** Thời gian thực thi cuối cùng của gkape.exe là `12/01/2021 13:04`.

**Câu 3:** Khi Notepad.exe được mở vào lúc 10:56 ngày 30/11/2021, nó được giữ nguyên trong bao lâu?
Phân tích tệp dưới với WxTCmd.exe
![alt text](<../png/Windows Forensics 1/22.png>)
rồi mở ra xem 
![alt text](<../png/Windows Forensics 1/23.png>)
mở rộng cột startTime mới xem được
>**Đáp án:** Notepad.exe được giữ nguyên trong `00:00:41`.


**Câu 4:** Chương trình nào được sử dụng để mở `C:\Users\THM-4n6\Desktop\KAPE\KAPE\ChangeLog.txt?`
>**Đáp án:** Chương trình được sử dụng để mở `C:\Users\THM-4n6\Desktop\KAPE\KAPE\ChangeLog.txt` là `Notepad.exe`.
