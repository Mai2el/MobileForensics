# Bài Thực Hành: Android Forensics & Reverse Engineering
## AndroidBreach Lab — SecureNotesSync

**Môn học:** Digital Forensics  
**Hình thức:** Cá nhân  
---

## Tình Huống

Phòng IT của công ty **BrightWave** nhận được cảnh báo từ hệ thống DLP:
một nhân viên đã cài đặt ứng dụng **"SecureNotesSync"** từ nguồn không rõ
lên thiết bị Android cá nhân được dùng để truy cập tài nguyên nội bộ.

Thiết bị đã được thu giữ và tạo ảnh forensic.
Bạn được giao nhiệm vụ phân tích APK và các artifact thu thập được
để xác định ứng dụng này đã làm gì trên thiết bị.


Kiểm tra kết quả nếu cần - format flag{...}: http://45.122.249.68:10203

---

## Câu Hỏi

### Phần 1 — Kiểm Tra Toàn Vẹn (0,5 điểm)

**Câu 1.** Xác minh tính toàn vẹn của các file trong evidence package.
Trình bày kết quả kiểm tra và giải thích tại sao bước này là bắt buộc
trong một cuộc điều tra số.

---

### Phần 2 — Phân Tích Tĩnh APK (3,5 điểm)

**Câu 2.** Package name của ứng dụng là gì? minSdk và targetSdk là bao nhiêu?

**Câu 3.** Liệt kê tất cả các quyền (permission) được khai báo trong
`AndroidManifest.xml`. Quyền nào không phù hợp với chức năng được quảng cáo
của ứng dụng?

**Câu 4.** Ngoài permission, còn thuộc tính nào trong `AndroidManifest.xml`
có thể là dấu hiệu đáng ngờ? Giải thích ý nghĩa của nó.

**Câu 5.** Mô tả luồng thực thi của ứng dụng từ khi khởi động đến khi
kết thúc. Liệt kê các class và phương thức liên quan theo đúng thứ tự gọi.

**Câu 6.** Ứng dụng sử dụng tiêu chí gì để lọc dữ liệu?
Liệt kê đầy đủ các tiêu chí đó.

**Câu 7.** Có một hằng số được mã hoá trong source code.
Tìm hằng số đó, giải mã nó, và cho biết ý nghĩa của giá trị thu được.

**Câu 8.** Ứng dụng ghi những file nào xuống thiết bị?
Đường dẫn đầy đủ trên thiết bị là gì?

---

### Phần 3 — Phân Tích Artifact (3,5 điểm)

**Câu 9.** Phân tích `outbox.json`: có bao nhiêu record, chúng được tạo lúc nào,
và cấu trúc của mỗi record gồm những trường gì?

**Câu 10.** Liệt kê tiêu đề của tất cả các ghi chú bị thu thập vào `outbox.json`.
Giải thích tại sao những ghi chú này bị chọn trong khi các ghi chú khác thì không.

**Câu 11.** Đọc nội dung đầy đủ của dataset gốc bên trong APK.
Có bao nhiêu ghi chú tổng cộng? Bao nhiêu ghi chú không bị thu thập?
Điểm chung của các ghi chú không bị thu thập là gì?

**Câu 12.** Phân tích `sync_cache.log`: các trường trong file này
cho biết điều gì về hành vi dự kiến của ứng dụng?

**Câu 13.** So sánh giá trị bạn tìm được ở Câu 7 với nội dung của `sync_cache.log`.
Chúng có liên hệ gì với nhau?

**Câu 14.** Xem `metadata/package_dump.txt` và `metadata/logcat.txt`.
Rút ra ít nhất hai thông tin hữu ích cho cuộc điều tra từ mỗi file.

---

### Phần 4 — Tổng Hợp & Báo Cáo (2,5 điểm)

**Câu 15.** Vẽ sơ đồ mô tả toàn bộ hành vi của ứng dụng, bao gồm:
tên class, tên phương thức, file được tạo, và dữ liệu bị thu thập.

**Câu 16.** Liệt kê ít nhất **5 Indicators of Compromise (IoC)** cụ thể
mà một analyst có thể dùng để phát hiện ứng dụng này trên các thiết bị khác.
Với mỗi IoC, nêu rõ cách phát hiện.

**Câu 17.** Phân tích tĩnh và phân tích artifact bổ sung cho nhau như thế nào
trong bài lab này? Nếu chỉ có một trong hai nguồn, bạn sẽ bỏ sót gì?

**Câu 18.** Đánh giá mức độ nguy hiểm của ứng dụng này nếu nó hoạt động
trong môi trường thực tế. Lập luận dựa trên bằng chứng bạn thu thập được.

---

## Hướng Dẫn Nộp Bài

Nộp **một file ZIP** chứa:

```
MSSV_HoTen_AndroidForensics.zip
├── bao_cao.pdf
└── bao_cao_markdown.zip
└── ioc_list.txt
```

**Yêu cầu báo cáo:**
- Mỗi câu trả lời phải có screenshot hoặc output lệnh làm bằng chứng
- Không chấp nhận câu trả lời không có evidence cụ thể

---

## Lưu Ý

- Đây là ứng dụng mô phỏng giáo dục — tất cả dữ liệu là giả
- Không upload APK hoặc artifact lên bất kỳ dịch vụ online nào
- Chỉ thực hành trên máy ảo cá nhân
