# BÀI LÀM – ÔN TẬP NGÀY 2

- **Họ tên:** Tô Mạnh Hào
- **Lớp:** CNTT1
- **Link repository:**
- **Hệ điều hành (Windows/macOS):** Windows

## Bài 1. Lọc log thủ công

### Lệnh đã chạy

```shell

PS C:\Users\Manh Hao\Downloads\trung-tam-tieng-anh> get-content .\logs\access.log
PS C:\Users\Manh Hao\Downloads\trung-tam-tieng-anh> select-string "ERROR" .\logs\access.log
PS C:\Users\Manh Hao\Downloads\trung-tam-tieng-anh> select-string "ERROR" .\logs\access.log | out-file .\logs\error_report.txt
PS C:\Users\Manh Hao\Downloads\trung-tam-tieng-anh> get-content .\logs\error_report.txt
```

### 2 dòng lỗi đầu tiên trong error_report.txt

```text

- logs\access.log:4:2025-10-18 08:17:59 [ERROR] Khong tim thay trang
/lich-thi (404)
- logs\access.log:6:2025-10-18 08:25:55 [ERROR] Het thoi gian cho (timeout)

```

## Bài 2. Đếm bằng pipeline

### Lệnh

```shell
PS C:\Users\Manh Hao\Downloads\trung-tam-tieng-anh> get-content .\logs\access.log | select-string "WARNING" | Measure-Object
PS C:\Users\Manh Hao\Downloads\trung-tam-tieng-anh> get-content .\logs\payment.log | select-string "ERROR" | Measure-Object

```

### Kết quả đếm (Windows: giá trị Count; macOS: con số in ra)

```text
WARNING trong access.log:
Count    : 4
Average  :
Sum      :
Maximum  :
Minimum  :
Property :

ERROR trong payment.log:
Count    : 3
Average  :
Sum      :
Maximum  :
Minimum  :
Property :
```

## Bài 3. Chạy script auto_warning (.ps1 hoặc .sh)

### Lệnh chạy (Windows: nếu dùng Phụ lục 2 thì ghi cả 2 lệnh)

```shell
PS C:\Users\Manh Hao\Downloads\trung-tam-tieng-anh> .\auto_warning.ps1

```

### Nội dung file logs/warning_report.txt

```text
=== CANH BAO THANH TOAN ===

2025-10-18 09:19:13 [WARNING] Cong thanh toan phan hoi cham
2025-10-18 09:28:16 [WARNING] Nhieu lan nhap sai ma OTP
2025-10-18 09:43:01 [WARNING] So du vi gan bang hoc phi
2025-10-18 09:46:22 [WARNING] So du vi gan bang hoc phi
2025-10-18 09:49:43 [WARNING] So du vi gan bang hoc phi


```

## Bài 4. Báo cáo tổng hợp

### Các lệnh đã chạy

```shell
PS C:\Users\Manh Hao\Downloads\trung-tam-tieng-anh> echo " === TONG HOP ACCESS LOG ===" >> logs\tong_hop_ngay2.txt
PS C:\Users\Manh Hao\Downloads\trung-tam-tieng-anh> get-content .\logs\access.log | select-string "ERROR" >> .\logs\tong_hop_ngay2.txt
PS C:\Users\Manh Hao\Downloads\trung-tam-tieng-anh> get-content .\logs\payment.log | select-string "WARNING" | Measure-Object >> .\logs\tong_hop_ngay2.txt

```

### Nội dung file logs/tong_hop_ngay2.txt

```text
 === TONG HOP ACCESS LOG ===

2025-10-18 08:17:59 [ERROR] Khong tim thay trang /lich-thi (404)
2025-10-18 08:25:55 [ERROR] Het thoi gian cho (timeout)
2025-10-18 08:33:51 [ERROR] Ket noi may chu du lieu that bai
2025-10-18 08:37:19 [ERROR] Ket noi may chu du lieu that bai
2025-10-18 08:49:43 [ERROR] Het thoi gian cho (timeout)
2025-10-18 08:53:11 [ERROR] Het thoi gian cho (timeout)




Count    : 5
Average  : 
Sum      : 
Maximum  : 
Minimum  : 
Property : 



```

## Bài 5. Câu hỏi ngắn

- **a)** 
   - `>` file: ghi chèn, nếu trong file có nỗi dung cũ sẽ bị xóa thay thế bằng nội dung nối
   - `>>` file: ghi nối tiếp, nếu trong file còn nội dung cũ sẽ ghi nối tiếp vào sau nội dung cũ
- **b)**: file tong_hop_ngay2.txt sẽ xóa sạch nội dung "===TONG HOP ACCESS LOG===" thay vào đó là những dòng "ERROR"
- **c)**: vì dùng đường dẫn tương đối tiện lợi, dễ dàng chia sẻ file, và không phụ thuộc vào máy khác có tên miền giống mình hay không

## Tự chấm (điền sau khi có đáp án)

- **Điểm tự chấm:** ..../100
- **Lỗi mình đã mắc và cách sửa:**
