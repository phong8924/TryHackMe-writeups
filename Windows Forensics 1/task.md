## Task 10
Sau khi đăng nhập vào máy ảo, bạn sẽ thấy hai thư mục trên Desktop: triage (chứa dữ liệu thu thập bằng KAPE để phân tích các bằng chứng) và EZtools (chứa các công cụ của Eric Zimmerman để hỗ trợ phân tích forensics, như RegistryExplorer, EZViewer, AppCompatCacheParser.exe). Mặc dù có thể dùng Autopsy, nhưng khuyến nghị sử dụng EZtools theo hướng dẫn của phòng này.

Tình huống đặt ra là một máy tính trong phòng thí nghiệm bị nghi truy cập trái phép, xuất hiện nhiều tài khoản người dùng, nghi ngờ kết nối ổ USB và mạng. Dữ liệu đã được thu thập để bạn điều tra và trả lời các câu hỏi forensics bên dưới.

## Answer the questions below

**1. How many user created accounts are present on the system?**  
Vào EZTools > Registry Explorer chạy với quyền quản trị viên
![alt text](<../png/Windows Forensics 1/1.png>)

Sau đó, Load Hive đến file SAM
Accounts with RIDs starting with 10xx are user created accounts
Trong mục Users, bạn sẽ thấy danh sách các tài khoản người dùng.
![alt text](<../png/Windows Forensics 1/2.png>)

>Đáp án *3*

---

**2. What is the username of the account that has never been logged in?** 
Kiểm tra tài khoản không có thời gian đăng nhập cuối cùng
![alt text](<../png/Windows Forensics 1/3.png>)

---

**3. What's the password hint for the user THM-4n6?**  
![alt text](<../png/Windows Forensics 1/4.png>)
*_____*

---

**4. When was the file 'Changelog.txt' accessed?** 

Chuyển sang câu hỏi thử thách tiếp theo, đó là về việc thực thi một tệp văn bản (.txt). Khi nói đến bằng chứng thực thi, chúng ta sẽ không tìm đâu xa ngoài NTUSER.DAT (trong nhiệm vụ 7). 
![alt text](<../png/Windows Forensics 1/5.png>)

![alt text](<../png/Windows Forensics 1/6.png>)
Sau khi NTUSER.DAT được tải, chúng ta có thể xem các tệp gần đây bằng cách theo đường dẫn này “NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Explorer\RecentDocs”.
![alt text](<../png/Windows Forensics 1/7.png>)

>Đáp án *2021-11-24 18:18:48*

---

**5. What is the complete path from where the python 3.8.2 installer was run?**  
Hint: Check the evidence of execution artifacts

Khi bạn nhìn vào tổ hợp NTUSER.DAT, chúng ta có nhiều tùy chọn để điều tra việc thực thi tệp gần đây, bao gồm UserAssist, ShimCache, AmCache, BAM/DAM. — - UserAssist là một thành phần ghi lại việc sử dụng ứng dụng của từng người dùng. Nó lưu trữ thông tin về những ứng dụng mà người dùng đã chạy và tần suất sử dụng chúng. ShimCache , hay Application Compatibility Cache, được sử dụng để cải thiện khả năng tương thích của các ứng dụng cũ với các phiên bản Windows mới hơn. Nó ghi lại thông tin về các ứng dụng đã thực thi và các DLL liên quan của chúng. AmCache là một thành phần khác liên quan đến khả năng tương thích của ứng dụng. Nó ghi lại dữ liệu về các ứng dụng đã cài đặt, phiên bản của chúng và lịch sử thực thi của chúng. BAM và DAM liên quan đến việc quản lý các ứng dụng và thiết bị trên hệ thống Windows, đặc biệt là trong Windows 8 và các phiên bản mới hơn. BAM ghi lại thông tin về các ứng dụng sử dụng tác vụ nền, trong khi DAM ghi lại thông tin về các ứng dụng thiết bị. Với mô tả về các thành phần này, chúng ta có thể bắt đầu với UserAssist.
![alt text](<../png/Windows Forensics 1/8.png>)
Nhưng kiểm tra thì không có gì wtf!
![alt text](<../png/Windows Forensics 1/9.png>)

Vì Python là một ứng dụng, hãy thử tìm kiếm từ khóa "Ứng dụng" trên thanh tìm kiếm xem sao. 
Trường “RecentApps” này có vẻ thú vị, và hóa ra nó thực sự là nơi chúng ta có thể tìm thấy thông tin về trình cài đặt Python 3.8.2.
![alt text](<../png/Windows Forensics 1/10.png>)

>**Đáp án** Z:\setups\python-3.8.2.exe
---

**6. When was the USB device with the friendly name 'USB' last connected?**  
Đọc Task9 ta có thể thấy 
we can start with the SOFTWARE\Microsoft\Windows Portable Devices\Devices directory.
![alt text](<../png/Windows Forensics 1/11.png>)
Tìm đến : SOFTWARE\Microsoft\Windows Portable Devices\Devices
![alt text](<../png/Windows Forensics 1/12.png>)
Nhưng đây chỉ mới là tên thiết bị :)
Vì vậy, chúng ta có thể tìm thấy số Guid của thiết bị có tên thân thiện là “USB”. Tiếp theo là quay lại vị trí nhận dạng thiết bị (SYSTEM\CurrentControlSet\Enum\USBSTOR hoặc SYSTEM\CurrentControlSet\Enum\USB để tìm thông tin như lần đầu tiên và lần cuối cùng thiết bị được kết nối với máy.
![alt text](<../png/Windows Forensics 1/13.png>)
