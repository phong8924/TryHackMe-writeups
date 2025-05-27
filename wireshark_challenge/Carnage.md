# Carnage - Wireshark Challenge

## 1. What was the date and time for the first HTTP connection to the malicious IP?
Vào view chỉnh lại format
**Answer:** `2021-09-24 16:44:38`

---

## 2. What is the name of the zip file that was downloaded?

![alt text](../png/Carnage(Wireshark)/2.png)

**Answer:** `documents.zip`

---

## 3. What was the domain hosting the malicious zip file?

![alt text](../png/Carnage(Wireshark)/3.png)

**Answer:** `attirenepal.com`

---

## 4. Without downloading the file, what is the name of the file in the zip file?
Đề yêu cầu không tải file về, nhưng mà không tìm thấy đành tải file về 
![alt text](../png/Carnage(Wireshark)/4.png)

**Answer:** `chart-1530076591.xls`

---

## 5. What is the name of the webserver of the malicious IP from which the zip file was downloaded?
Vẫn là gói tin chứa file zip, nhấn và follow
![alt text](../png/Carnage(Wireshark)/5.png)
**Answer:** `LiteSpeed`

---

## 6. What is the version of the webserver from the previous question?
![alt text](../png/Carnage(Wireshark)/5.png)
**Answer:** `PHP/7.2.34`


## 7. Malicious files were downloaded to the victim host from multiple domains. What were the three domains involved with this activity?
**Hints** Check HTTPS traffic. Narrow down the timeframe from 16:45:11 to 16:45:30.

HTTPS -> tls, chỉnh ip thành hostname
![alt text](../png/Carnage(Wireshark)/6.png)
lướt các gói tin trong khoảng thời gian trên hints thì thấy 3 địa chỉ
Nhưng vẫn chưa hiểu tại sao lại là các địa chỉ này liên quan gì đến đề bài
**Answer:** `finejewels.com.au, thietbiagt.com, new.americold.com`

---

## 8. Which certificate authority issued the SSL certificate to the first domain from the previous question?

Xác định tổ chức đã cấp chứng chỉ SSL/TLS (Certificate Authority - CA) cho một địa chỉ (domain/IP) nếu dữ liệu bắt được chứa quá trình bắt tay TLS (TLS Handshake) -> Xem gói tin Certificate
![alt text](../png/Carnage(Wireshark)/7.png)
**Answer:** GoDaddy

---

## 9. What are the two IP addresses of the Cobalt Strike servers? (answer format: enter the IP addresses in sequential order)

Lên trang MITRE tìm kiếm thông tin về Cobalt Strike, thấy có các gói tin http, https nên ta sẽ xem các địa chỉ tới các cổng 80,8080, 443

Vào wireshark mở Statistics-> Converstation, tập trung vào TCP, xem phần PORT B thấy có các gói tin tới cổng 80
![alt text](../png/Carnage(Wireshark)/10.png)

Tiếp tục lên trang virustotal.com tìm kiếm về IP xuất hiện
thấy IP 185.106.96.158
![alt text](../png/Carnage(Wireshark)/11.png)

Vào wireshark mở Statistics-> Converstation, tập trung vào TCP, xem phần PORT B thấy có các gói tin tới cổng 8080
![alt text](../png/Carnage(Wireshark)/8.png)
Tiếp tục lên trang virustotal.com tìm kiếm về IP 185.125.204.174
![alt text](../png/Carnage(Wireshark)/9.png)

**Answer:** 
185.106.96.158, 185.125.204.174
---

## 10. What is the Host header for the first Cobalt Strike IP address from the previous question?

![alt text](../png/Carnage(Wireshark)/12.png)
**Answer:** 
ocsp.verisign.com
---

## 11. What is the domain name for the first IP address of the Cobalt Strike server?
**Answer:** 

---

## 12. What is the domain name of the second Cobalt Strike server IP?
**Answer:** 

---

## 13. What is the domain name of the post-infection traffic?
**Answer:** 

---

## 14. What are the first eleven characters that the victim host sends out to the malicious domain involved in the post-infection traffic?
**Answer:** 

---

## 15. What was the length for the first packet sent out to the C2 server?
**Answer:** 

---

## 16. What was the Server header for the malicious domain from the previous question?
**Answer:** 

---

## 17. The malware used an API to check for the IP address of the victim’s machine. What was the date and time when the DNS query for the IP check domain occurred? (answer format: yyyy-mm-dd hh:mm:ss UTC)
**Answer:** 

---

## 18. What was the domain in the DNS query from the previous question?
**Answer:** 

---

## 19. What was the first MAIL FROM address observed in the traffic?
**Answer:** 

---

## 20. How many packets were observed for the SMTP traffic?
**Answer:**

