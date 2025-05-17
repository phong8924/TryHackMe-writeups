
# Nguyên tắc câu truy vấn
## Capture Filters

Loại filter này được sử dụng để lưu trữ chỉ một phần cụ thể của traffic. Nó được thiết lập trước khi capture và không thể thay đổi trong quá trình capture.

## Display Filters

Loại filter này được sử dụng để điều tra packets bằng cách giảm số lượng hiển thị và có thể thay đổi trong quá trình capture.

> **Note**: Bạn không thể sử dụng display filter expressions để capture traffic và ngược lại.

Thông thường, người dùng sẽ capture toàn bộ và sử dụng display filters để lọc các packets theo sự kiện cần quan tâm. Chỉ những người có kinh nghiệm mới sử dụng capture filters để sniff traffic. Đây là lý do tại sao Wireshark hỗ trợ nhiều loại protocol hơn với display filters. Hãy đảm bảo bạn thành thạo capture filters trước khi sử dụng trong môi trường thực tế.

## Capture Filter Syntax

Các filters này sử dụng byte offsets, giá trị hex và masks cùng với boolean operators. Cú pháp cơ bản:

- **Scope**: `host`, `net`, `port`, `portrange`
- **Direction**: `src`, `dst`, `src or dst`, `src and dst`
- **Protocol**: `ether`, `wlan`, `ip`, `ip6`, `arp`, `rarp`, `tcp`, `udp`

Ví dụ filter để capture traffic cổng 80:

```
tcp port 80
```



## Display Filter Syntax

Đây là tính năng mạnh mẽ nhất của Wireshark, hỗ trợ hơn 3000 protocols. Cho phép phân tích gói tin ở cấp độ protocol breakdown.

Ví dụ filter để lọc traffic cổng 80:

```
tcp.port == 80
```

Wireshark có built-in option là **Display Filter Expression** lưu trữ các cấu trúc protocol để hỗ trợ tạo filters.

> Xem thêm tại menu **Analyse --> Display Filters**.

### Comparison Operators

| English | C-Like | Description | Example |
|---------|--------|-------------|---------|
| eq      | ==     | Equal       | `ip.src == 10.10.10.100` |
| ne      | !=     | Not equal   | `ip.src != 10.10.10.100` |
| gt      | >      | Greater than | `ip.ttl > 250` |
| lt      | <      | Less than   | `ip.ttl < 10` |
| ge      | >=     | Greater than or equal to | `ip.ttl >= 0xFA` |
| le      | <=     | Less than or equal to | `ip.ttl <= 0xA` |

> Wireshark hỗ trợ cả số thập phân và hex trong filter.

### Logical Expressions

Wireshark hỗ trợ boolean syntax.

| English | C-Like | Description | Example |
|---------|--------|-------------|---------|
| and     | &&     | Logical AND | `(ip.src == 10.10.10.100) && (ip.src == 10.10.10.111)` |
| or      | \|\|   | Logical OR  | `(ip.src == 10.10.10.100) || (ip.src == 10.10.10.111)` |
| not     | !      | Logical NOT | `!(ip.src == 10.10.10.222)` |

> **Note**: Không nên dùng `!=` mà hãy dùng `!(value)` để kết quả nhất quán hơn.

## Packet Filter Toolbar

Đây là nơi bạn tạo và áp dụng display filters. Một số lưu ý:

- Được định nghĩa bằng chữ thường
- Có tính năng autocomplete với "dot notation"
- Có hệ thống màu sắc:
  - **Green**: Filter hợp lệ
  - **Red**: Filter không hợp lệ
  - **Yellow**: Cảnh báo - filter có thể hoạt động nhưng không ổn định

> Các tính năng này nằm trong thanh toolbar của Wireshark.

---

Bây giờ, hãy áp dụng các kiến thức đã học để thực hành lọc packets trong nhiệm vụ tiếp theo.
