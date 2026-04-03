# 📋 SRS - Đặc Tả Yêu Cầu Phần Mềm
## Ứng Dụng Zalo Transfer - Chuyển Dữ Liệu Zalo Giữa Các Thiết Bị Android

**Tên Dự Án:** Zalo Transfer App  
**Phiên Bản:** 1.0  
**Ngày Tạo:** 12/02/2026  
**Trạng Thái:** Chờ Phê Duyệt  
**Tác Giả:** Development Team

---

## 📑 Mục Lục

1. [Giới Thiệu](#giới-thiệu)
2. [Tổng Quan Dự Án](#tổng-quan-dự-án)
3. [Phạm Vi Dự Án](#phạm-vi-dự-án)
4. [Người Dùng & Stakeholder](#người-dùng--stakeholder)
5. [Yêu Cầu Chức Năng](#yêu-cầu-chức-năng)
6. [Yêu Cầu Phi Chức Năng](#yêu-cầu-phi-chức-năng)
7. [Trường Hợp Sử Dụng](#trường-hợp-sử-dụng)
8. [Luồng Dữ Liệu](#luồng-dữ-liệu)
9. [Ràng Buộc & Giả Định](#ràng-buộc--giả-định)
10. [Tiêu Chí Chấp Nhận](#tiêu-chí-chấp-nhận)
11. [Rủi Ro & Giải Pháp](#rủi-ro--giải-pháp)
12. [Lộ Trình Phát Triển](#lộ-trình-phát-triển)

---

## 🎯 Giới Thiệu

### Mục Đích Tài Liệu

Tài liệu này định nghĩa **toàn bộ yêu cầu chức năng và phi chức năng** cho ứng dụng **Zalo Transfer** - một ứng dụng Android cho phép người dùng chuyển dữ liệu Zalo (tin nhắn, ảnh, video, file) từ một thiết bị sang thiết bị khác thông qua kết nối WiFi hoặc Bluetooth.

### Đối Tượng Sử Dụng Tài Liệu

- **Nhóm Phát Triển:** Hiểu rõ yêu cầu để xây dựng ứng dụng
- **Nhóm QA/Testing:** Biết cách kiểm thử từng tính năng
- **Nhóm Product:** Theo dõi tiến độ và xác nhận yêu cầu
- **Nhóm Bảo Mật:** Đánh giá rủi ro bảo mật

---

## 🎪 Tổng Quan Dự Án

### 1. Bối Cảnh & Vấn Đề

#### Vấn Đề Hiện Tại

Khi người dùng Android chuyển sang thiết bị mới, họ gặp khó khăn trong việc chuyển dữ liệu Zalo:

- **Không còn sao lưu Google Drive:** Zalo đã ngừng hỗ trợ sao lưu dữ liệu lên Google Drive như trước đây.
- **Phụ Thuộc Máy Tính:** Cần máy tính để sử dụng ADB hoặc file manager
- **Sao lưu phải trả phí:** Việc sao lưu và khôi phục tin nhắn trên Zalo hiện yêu cầu người dùng trả phí để sử dụng tính năng lưu trữ đám mây.
- **Phức tạp khi chuyển thủ công:** Người dùng phải tự sao chép dữ liệu hoặc dùng các cách thủ công, dễ gây nhầm lẫn.
- **Nguy cơ mất dữ liệu:** Tin nhắn, hình ảnh và file có thể bị mất trong quá trình chuyển thiết bị nếu không sao lưu đúng cách.

#### Giải Pháp Đề Xuất

Xây dựng ứng dụng **Zalo Transfer** cho phép:
- Chuyển dữ liệu Zalo **trực tiếp giữa 2 thiết bị** qua WiFi/Bluetooth
- **Không cần máy tính** hoặc ROOT
- Sử dụng **Shizuku** để truy cập thư mục bảo vệ
- **Giao diện thân thiện** tương tự các app truyền file phổ biến
- **Hệ thống thanh toán** để duy trì ứng dụng

### 2. Mục Tiêu Dự Án

#### Mục Tiêu Chính

1. **Giải Quyết Vấn Đề Chuyển Dữ Liệu Zalo** - Cung cấp cách dễ dàng, an toàn
2. **Trải Nghiệm Người Dùng Tốt** - Giao diện đơn giản, hướng dẫn rõ ràng
3. **Bảo Mật Dữ Liệu** - Mã hóa, không lưu trữ đám mây
4. **Khả Năng Mở Rộng** - Có thể mở rộng cho các ứng dụng khác

#### Mục Tiêu Kinh Doanh

1. **Tạo Doanh Thu** - Thông qua hệ thống coin/mua hàng trong ứng dụng
2. **Xây Dựng Cộng Đồng** - Người dùng tin tưởng và sử dụng lâu dài
3. **Phân Biệt Thị Trường** - Ứng dụng duy nhất chuyên chuyển Zalo

### 3. Lợi Ích Dự Kiến

| Lợi Ích | Mô Tả |
|---------|-------|
| **Tiết Kiệm Thời Gian** | Chuyển dữ liệu trong vài phút thay vì hàng giờ |
| **Dễ Sử Dụng** | Không cần kiến thức kỹ thuật |
| **An Toàn** | Dữ liệu không qua server bên thứ ba |
| **Tiết Kiệm Chi Phí** | Không cần máy tính hoặc dịch vụ khác |
| **Linh Hoạt** | Hỗ trợ WiFi và Bluetooth |

---

## 📊 Phạm Vi Dự Án

### 1. Tính Năng Được Bao Gồm (In Scope)

#### Phase 1 - MVP (Phiên Bản Tối Thiểu Khả Dụng)

| # | Tính Năng | Mô Tả | Ưu Tiên |
|---|----------|-------|--------|
| F1 | Chế Độ Gửi | Chia sẻ thư mục Zalo từ thiết bị cũ | **CRITICAL** |
| F2 | Chế Độ Nhận | Nhận dữ liệu Zalo trên thiết bị mới | **CRITICAL** |
| F3 | Kết Nối WiFi Direct | Truyền qua WiFi Direct P2P | **CRITICAL** |
| F4 | Kết Nối Bluetooth | Truyền qua Bluetooth | **HIGH** |
| F5 | Shizuku Integration | Truy cập `/sdcard/android/data/com.zing.zalo` | **CRITICAL** |
| F6 | Thanh Toán Google Play | Mua coin thông qua Google Play | **HIGH** |
| F7 | Hệ Thống Coin | Tính phí dựa trên dung lượng | **HIGH** |
| F8 | Tiến Độ Truyền | Hiển thị tiến độ, tốc độ, ETA | **HIGH** |
| F9 | Tạm Dừng/Tiếp Tục | Cho phép tạm dừng và tiếp tục truyền | **MEDIUM** |
| F10 | Lịch Sử Truyền | Ghi lại các lần truyền trước | **MEDIUM** |

#### Phase 2 - Enhancement (Cải Tiến)

| # | Tính Năng | Mô Tả | Ưu Tiên |
|---|----------|-------|--------|
| F11 | Hỗ Trợ Ứng Dụng Khác | Mở rộng cho WhatsApp, Telegram | **LOW** |
| F12 | Sao Lưu Đám Mây | Tích hợp Google Drive, OneDrive | **LOW** |
| F13 | Nén Dữ Liệu | Nén trước khi truyền | **MEDIUM** |
| F14 | Mã Hóa End-to-End | Mã hóa tùy chọn cho dữ liệu | **MEDIUM** |

### 2. Tính Năng Không Được Bao Gồm (Out of Scope)

- ❌ Sao lưu tự động theo lịch (Phase 2+)
- ❌ Truyền qua internet (chỉ LAN)
- ❌ Hỗ trợ iOS (chỉ Android)
- ❌ Truyền dữ liệu ứng dụng khác (Phase 2+)
- ❌ Giao diện web (chỉ mobile)

### 3. Giới Hạn Kỹ Thuật

- **Phiên Bản Android Tối Thiểu:** Android 8.0 (API 26)
- **Phiên Bản Android Tối Đa:** Android 14+ (API 34+)
- **Kích Thước Ứng Dụng:** < 50 MB
- **Dung Lượng Tối Đa Mỗi Lần Truyền:** Không giới hạn (tùy vào RAM thiết bị)
- **Tốc độ Truyền Tối Thiểu:** 1 MB/s (WiFi Direct)

---

## 👥 Người Dùng & Stakeholder

### 1. Phân Loại Người Dùng

#### Người Dùng Chính (Primary Users)

| Loại | Mô Tả | Nhu Cầu |
|------|-------|--------|
| **Người Chuyển Thiết Bị** | Người dùng Android mua thiết bị mới | Chuyển dữ liệu Zalo nhanh chóng |
| **Người Sao Lưu** | Người muốn sao lưu dữ liệu Zalo | Bảo vệ dữ liệu quan trọng |
| **Người Dùng Kỹ Thuật** | Người dùng có kiến thức công nghệ | Kiểm soát chi tiết quá trình truyền |

#### Người Dùng Thứ Cấp (Secondary Users)

| Loại | Mô Tả |
|------|-------|
| **Người Dùng Không Kỹ Thuật** | Cần hướng dẫn chi tiết, giao diện đơn giản |
| **Người Dùng Nâng Cao** | Muốn tùy chọn nâng cao, kiểm soát chi tiết |

### 2. Stakeholder

| Stakeholder | Lợi Ích | Mối Quan Tâm |
|-------------|---------|-------------|
| **Người Dùng** | Chuyển dữ liệu dễ dàng | Bảo mật, tốc độ, độ tin cậy |
| **Nhóm Phát Triển** | Xây dựng sản phẩm chất lượng | Yêu cầu rõ ràng, timeline hợp lý |
| **Nhóm Bảo Mật** | Bảo vệ dữ liệu người dùng | Mã hóa, không lưu trữ đám mây |
| **Nhóm Kinh Doanh** | Tạo doanh thu | Tỷ lệ chuyển đổi, giữ chân người dùng |
| **Google Play** | Tuân thủ chính sách | Không vi phạm quy định |
---

## 📝 Yêu Cầu Chức Năng

### 1. Yêu Cầu Chức Năng Chính

#### UC-1: Chế Độ Gửi Dữ Liệu Zalo

**ID:** F1  
**Ưu Tiên:** CRITICAL  
**Mô Tả:** Người dùng có thể chia sẻ dữ liệu Zalo từ thiết bị cũ

**Yêu Cầu Chi Tiết:**

| # | Yêu Cầu | Chi Tiết |
|---|---------|---------|
| 1.1 | Truy cập thư mục Zalo | Sử dụng Shizuku để truy cập `/sdcard/android/data/com.zing.zalo/files` |
| 1.2 | Tính dung lượng | Hiển thị tổng dung lượng thư mục Zalo |
| 1.3 | Tính chi phí | Hiển thị coin cần thiết dựa trên dung lượng (5MB = 1 coin) |
| 1.4 | Tạo phiên làm việc | Tạo ID phiên duy nhất (UUID) |
| 1.5 | Tạo mã ghép nối | Tạo mã QR hoặc mã 6 chữ số |
| 1.6 | Chờ kết nối | Chờ thiết bị khác kết nối |
| 1.7 | Bắt đầu truyền | Gửi dữ liệu sau khi bên nhận kết nối |
| 1.8 | Theo dõi tiến độ | Hiển thị tốc độ, dung lượng đã gửi, ETA |
| 1.9 | Xử lý gián đoạn | Cho phép tạm dừng/tiếp tục hoặc hủy |
| 1.10 | Hoàn thành | Hiển thị thông báo hoàn thành, trừ coin |

**Luồng Chính:**
```
1. Người dùng chọn "Gửi Dữ Liệu Zalo"
2. Ứng dụng yêu cầu quyền Shizuku
3. Ứng dụng quét thư mục Zalo
4. Hiển thị dung lượng và chi phí coin
5. Người dùng chọn WiFi hoặc Bluetooth
6. Ứng dụng tạo mã QR/mã ghép nối
7. Người dùng chia sẻ mã
8. Chờ bên nhận kết nối
9. Bắt đầu truyền dữ liệu
10. Hiển thị tiến độ thực thời
11. Hoàn thành truyền
12. Trừ coin từ tài khoản
```

**Tiêu Chí Chấp Nhận:**
- [ ] Có thể truy cập thư mục Zalo qua Shizuku
- [ ] Dung lượng được tính chính xác
- [ ] Mã QR có thể quét được
- [ ] Truyền dữ liệu không bị lỗi
- [ ] Tiến độ được cập nhật theo thời gian thực
- [ ] Coin được trừ sau khi truyền thành công

#### UC-2: Chế Độ Nhận Dữ Liệu Zalo

**ID:** F2  
**Ưu Tiên:** CRITICAL  
**Mô Tả:** Người dùng có thể nhận dữ liệu Zalo từ thiết bị khác

**Yêu Cầu Chi Tiết:**

| # | Yêu Cầu | Chi Tiết |
|---|---------|---------|
| 2.1 | Quét mã QR | Người dùng quét mã QR từ bên gửi |
| 2.2 | Nhập mã ghép nối | Hoặc nhập mã 6 chữ số thủ công |
| 2.3 | Kết nối đến bên gửi | Thiết lập kết nối WiFi/Bluetooth |
| 2.4 | Hiển thị chi tiết | Hiển thị dung lượng, thời gian ước tính |
| 2.5 | Xác nhận | Người dùng xác nhận để bắt đầu |
| 2.6 | Yêu cầu quyền Shizuku | Cấp quyền ghi vào thư mục Zalo |
| 2.7 | Nhận dữ liệu | Nhận luồng dữ liệu từ bên gửi |
| 2.8 | Xác minh | Kiểm tra tổng kiểm để đảm bảo toàn vẹn |
| 2.9 | Lưu dữ liệu | Lưu vào `/sdcard/android/data/com.zing.zalo/files` |
| 2.10 | Hoàn thành | Hiển thị thông báo hoàn thành |

**Luồng Chính:**
```
1. Người dùng chọn "Nhận Dữ Liệu Zalo"
2. Ứng dụng hiển thị quét QR hoặc nhập mã
3. Người dùng quét QR hoặc nhập mã
4. Ứng dụng kết nối đến bên gửi
5. Hiển thị chi tiết truyền (dung lượng, thời gian)
6. Người dùng xác nhận
7. Ứng dụng yêu cầu quyền Shizuku
8. Bắt đầu nhận dữ liệu
9. Hiển thị tiến độ
10. Xác minh dữ liệu
11. Lưu vào thư mục Zalo
12. Hoàn thành
```

**Tiêu Chí Chấp Nhận:**
- [ ] Có thể quét mã QR chính xác
- [ ] Có thể nhập mã thủ công
- [ ] Kết nối thành công với bên gửi
- [ ] Dữ liệu được nhận đầy đủ
- [ ] Tổng kiểm khớp
- [ ] Dữ liệu được lưu đúng vị trí

#### UC-3: Tích Hợp Shizuku

**ID:** F5  
**Ưu Tiên:** CRITICAL  
**Mô Tả:** Ứng dụng tích hợp Shizuku để truy cập thư mục bảo vệ

**Yêu Cầu Chi Tiết:**

| # | Yêu Cầu | Chi Tiết |
|---|---------|---------|
| 3.1 | Kiểm tra cài đặt | Kiểm tra Shizuku đã cài chưa |
| 3.2 | Hướng dẫn cài đặt | Nếu chưa cài, hiển thị hướng dẫn |
| 3.3 | Yêu cầu quyền | Yêu cầu quyền từ Shizuku |
| 3.4 | Xác minh quyền | Kiểm tra quyền đã được cấp |
| 3.5 | Truy cập thư mục | Truy cập `/sdcard/android/data/com.zing.zalo/files` |
| 3.6 | Xử lý lỗi | Xử lý lỗi từ chối quyền, Shizuku không chạy |

**Tiêu Chí Chấp Nhận:**
- [ ] Phát hiện Shizuku chính xác
- [ ] Hướng dẫn cài đặt rõ ràng
- [ ] Yêu cầu quyền thành công
- [ ] Có thể truy cập thư mục Zalo
- [ ] Xử lý lỗi một cách nhân văn

#### UC-4: Hệ Thống Thanh Toán

**ID:** F6, F7  
**Ưu Tiên:** HIGH  
**Mô Tả:** Người dùng có thể mua coin thông qua Google Play

**Yêu Cầu Chi Tiết:**

| # | Yêu Cầu | Chi Tiết |
|---|---------|---------|
| 4.1 | Hiển thị số dư coin | Hiển thị coin hiện tại ở góc trên cùng |
| 4.2 | Tính chi phí | Tính coin cần thiết trước khi truyền |
| 4.3 | Kiểm tra đủ coin | Nếu không đủ, hiển thị lời nhắc mua |
| 4.4 | Hiển thị gói coin | Hiển thị các gói coin có sẵn |
| 4.5 | Khởi tạo mua | Khởi tạo luồng thanh toán Google Play |
| 4.6 | Xác minh mua | Xác minh chữ ký mua hàng |
| 4.7 | Cập nhật số dư | Thêm coin vào tài khoản |
| 4.8 | Trừ coin | Trừ coin sau khi truyền thành công |
| 4.9 | Hoàn lại coin | Hoàn lại coin nếu truyền thất bại |
| 4.10 | Ghi nhật ký | Ghi nhật ký tất cả giao dịch |

**Công Thức Tính Coin:**
```
Chi Phí Coin = ceil(Dung Lượng MB × 0.2)

Ví Dụ:
- 5 MB = 1 coin
- 10 MB = 2 coin
- 25 MB = 5 coin
- 50 MB = 10 coin
- 100 MB = 20 coin
```

**Tier Miễn Phí:**
```
- Mỗi ngày: 10 MB đầu tiên miễn phí
- Đặt lại: 00:00 UTC
- Tracking: SharedPreferences + timestamp
```

**Gói Coin Khả Dụng:**
| Gói | Coin | Giá |
|-----|------|-----|
| Starter | 10 | $0.99 |
| Popular | 50 | $4.99 |
| Standard | 100 | $9.99 |
| Premium | 500 | $49.99 |
| Ultimate | 1000 | $99.99 |

**Tiêu Chí Chấp Nhận:**
- [ ] Số dư coin hiển thị chính xác
- [ ] Chi phí được tính đúng
- [ ] Mua coin thành công
- [ ] Coin được cập nhật
- [ ] Coin được trừ sau truyền
- [ ] Giao dịch được ghi nhật ký

#### UC-5: Theo Dõi Tiến Độ Truyền

**ID:** F8  
**Ưu Tiên:** HIGH  
**Mô Tả:** Hiển thị tiến độ truyền thực thời

**Yêu Cầu Chi Tiết:**

| # | Yêu Cầu | Chi Tiết |
|---|---------|---------|
| 5.1 | Hiển thị phần trăm | Hiển thị % tiến độ (0-100%) |
| 5.2 | Hiển thị dung lượng | Hiển thị X/Y MB đã truyền |
| 5.3 | Hiển thị tốc độ | Hiển thị tốc độ truyền (MB/s) |
| 5.4 | Tính ETA | Tính thời gian còn lại |
| 5.5 | Cập nhật thực thời | Cập nhật mỗi 500ms |
| 5.6 | Hiển thị file | Hiển thị file đang truyền |
| 5.7 | Xử lý gián đoạn | Xử lý khi kết nối bị gián đoạn |

**Tiêu Chí Chấp Nhận:**
- [ ] Phần trăm tiến độ chính xác
- [ ] Dung lượng được tính đúng
- [ ] Tốc độ được hiển thị
- [ ] ETA được tính hợp lý
- [ ] Cập nhật mượt mà, không giật

#### UC-6: Tạm Dừng & Tiếp Tục

**ID:** F9  
**Ưu Tiên:** MEDIUM  
**Mô Tả:** Người dùng có thể tạm dừng và tiếp tục truyền

**Yêu Cầu Chi Tiết:**

| # | Yêu Cầu | Chi Tiết |
|---|---------|---------|
| 6.1 | Nút Tạm Dừng | Hiển thị nút tạm dừng trong tiến độ |
| 6.2 | Tạm Dừng Truyền | Tạm dừng truyền dữ liệu |
| 6.3 | Lưu Trạng Thái | Lưu vị trí hiện tại |
| 6.4 | Nút Tiếp Tục | Hiển thị nút tiếp tục |
| 6.5 | Tiếp Tục Truyền | Tiếp tục từ vị trí lưu |
| 6.6 | Nút Hủy | Hiển thị nút hủy với xác nhận |
| 6.7 | Hủy Truyền | Hủy truyền và xóa dữ liệu tạm |

**Tiêu Chí Chấp Nhận:**
- [ ] Có thể tạm dừng truyền
- [ ] Có thể tiếp tục từ vị trí tạm dừng
- [ ] Có thể hủy truyền
- [ ] Xác nhận trước khi hủy

#### UC-7: Lịch Sử Truyền

**ID:** F10  
**Ưu Tiên:** MEDIUM  
**Mô Tả:** Ghi lại lịch sử các lần truyền

**Yêu Cầu Chi Tiết:**

| # | Yêu Cầu | Chi Tiết |
|---|---------|---------|
| 7.1 | Ghi Nhật Ký | Ghi nhật ký mỗi lần truyền |
| 7.2 | Hiển Thị Lịch Sử | Hiển thị danh sách các lần truyền |
| 7.3 | Thông Tin Chi Tiết | Hiển thị ngày giờ, dung lượng, trạng thái |
| 7.4 | Tìm Kiếm | Cho phép tìm kiếm lịch sử |
| 7.5 | Xóa Lịch Sử | Cho phép xóa lịch sử |

**Thông Tin Lưu Trữ:**
```json
{
  "id": "uuid",
  "type": "SEND|RECEIVE",
  "size": 52428800,
  "coins": 10,
  "status": "SUCCESS|FAILED|CANCELLED",
  "timestamp": 1707700000000,
  "duration": 120,
  "speed": 7.3
}
```

**Tiêu Chí Chấp Nhận:**
- [ ] Lịch sử được lưu chính xác
- [ ] Có thể xem lịch sử
- [ ] Có thể tìm kiếm lịch sử
- [ ] Có thể xóa lịch sử

### 2. Yêu Cầu Chức Năng Phụ Trợ

#### UC-8: Cài Đặt Ứng Dụng

**ID:** Không áp dụng  
**Ưu Tiên:** MEDIUM  

| # | Yêu Cầu | Chi Tiết |
|---|---------|---------|
| 8.1 | Cài Đặt Chung | Tên ứng dụng, phiên bản, thông tin |
| 8.2 | Cài Đặt Thông Báo | Bật/tắt thông báo |
| 8.3 | Cài Đặt Kết Nối | Chọn loại kết nối mặc định (WiFi/BT) |
| 8.4 | Cài Đặt Bảo Mật | Mã hóa, xác thực |
| 8.5 | Thông Tin Tài Khoản | Hiển thị tài khoản Google Play |
| 8.6 | Giới Thiệu Ứng Dụng | Hướng dẫn sử dụng |
| 8.7 | Phản Hồi | Liên hệ hỗ trợ, báo cáo lỗi |

---

## ⚙️ Yêu Cầu Phi Chức Năng

### 1. Hiệu Năng

| Yêu Cầu | Mục Tiêu | Đo Lường |
|---------|----------|---------|
| **Tốc Độ Khởi Động** | < 3 giây | Thời gian từ nhấn icon đến hiển thị màn hình chính |
| **Tốc Độ Truyền WiFi** | > 5 MB/s | Tốc độ truyền trên WiFi Direct |
| **Tốc Độ Truyền Bluetooth** | > 1 MB/s | Tốc độ truyền trên Bluetooth 5.0+ |
| **Sử Dụng Bộ Nhớ** | < 100 MB | RAM được sử dụng trong quá trình truyền |
| **Sử Dụng CPU** | < 50% | CPU usage trung bình |
| **Tiêu Thụ Pin** | < 10% mỗi giờ | Pin tiêu thụ trong quá trình truyền |
| **Kích Thước APK** | < 50 MB | Kích thước file APK |
| **Thời Gian Build** | < 2 phút | Thời gian build release |

### 2. Khả Năng Mở Rộng

| Yêu Cầu | Mô Tả |
|---------|-------|
| **Kiến Trúc Module** | Chia thành các module độc lập, dễ mở rộng |
| **API Rõ Ràng** | API nội bộ rõ ràng, dễ tích hợp |
| **Cấu Hình Linh Hoạt** | Dễ thêm tính năng mới mà không ảnh hưởng cũ |
| **Database Schema** | Schema có thể mở rộng cho dữ liệu mới |

### 3. Bảo Mật

| Yêu Cầu | Mô Tả |
|---------|-------|
| **Mã Hóa Dữ Liệu** | Sử dụng TLS 1.2+ cho WiFi, Bluetooth encryption |
| **Xác Thực Phiên** | ID phiên duy nhất, không thể dự đoán |
| **Không Lưu Trữ Đám Mây** | Tất cả dữ liệu truyền cục bộ |
| **Không Ghi Nhật Ký Nội Dung** | Không ghi nội dung tệp vào nhật ký |
| **Quyền Tối Thiểu** | Chỉ yêu cầu quyền cần thiết |
| **Xác Minh Tổng Kiểm** | SHA-256 cho tính toàn vẹn tệp |
| **Mã Ghép Nối Bảo Mật** | Mã 6 chữ số + QR, hết hạn sau 10 phút |

### 4. Độ Tin Cậy

| Yêu Cầu | Mô Tả |
|---------|-------|
| **Tỷ Lệ Thành Công** | > 99% truyền hoàn thành không lỗi |
| **Khôi Phục Lỗi** | Tự động kết nối lại khi mất kết nối |
| **Xử Lý Ngoại Lệ** | Xử lý tất cả ngoại lệ, không crash |
| **Kiểm Tra Dữ Liệu** | Xác minh dữ liệu trước/sau truyền |
| **Uptime** | > 99.9% uptime cho dịch vụ backend (nếu có) |

### 5. Tương Thích

| Yêu Cầu | Mô Tả |
|---------|-------|
| **Phiên Bản Android** | Android 8.0 (API 26) đến Android 14+ (API 34+) |
| **Thiết Bị** | Hỗ trợ điện thoại, tablet |
| **Kích Thước Màn Hình** | 4.5" đến 7" (điện thoại), 7"+ (tablet) |
| **Mật Độ Pixel** | ldpi, mdpi, hdpi, xhdpi, xxhdpi, xxxhdpi |
| **Định Hướng** | Hỗ trợ cả chiều dọc và chiều ngang |

### 6. Khả Năng Sử Dụng

| Yêu Cầu | Mô Tả |
|---------|-------|
| **Giao Diện Trực Quan** | Giao diện dễ hiểu, không cần đào tạo |
| **Hướng Dẫn Rõ Ràng** | Hướng dẫn từng bước cho mỗi tính năng |
| **Thông Báo Lỗi** | Thông báo lỗi rõ ràng, có giải pháp |
| **Hỗ Trợ Ngôn Ngữ** | Tiếng Việt, tiếng Anh |
| **Accessibility** | Hỗ trợ screen reader, text scaling |

### 7. Bảo Trì

| Yêu Cầu | Mô Tả |
|---------|-------|
| **Ghi Nhật Ký** | Ghi nhật ký chi tiết cho debugging |
| **Monitoring** | Theo dõi lỗi, hiệu năng |
| **Update** | Có thể cập nhật tính năng mà không ảnh hưởng người dùng |
| **Rollback** | Có thể rollback phiên bản nếu có vấn đề |

---

## 🎬 Trường Hợp Sử Dụng

### Use Case Diagram

```
┌─────────────────────────────────────────────┐
│         Ứng Dụng Zalo Transfer              │
├─────────────────────────────────────────────┤
│                                              │
│  ┌──────────────┐         ┌──────────────┐ │
│  │ Người Gửi    │         │ Người Nhận   │ │
│  └──────┬───────┘         └──────┬───────┘ │
│         │                        │         │
│         ├─────────┬──────────────┤         │
│         │         │              │         │
│    ┌────▼──┐ ┌───▼────┐ ┌──────▼──┐      │
│    │ Gửi   │ │ Nhận   │ │ Thanh   │      │
│    │ Zalo  │ │ Zalo   │ │ Toán    │      │
│    └────────┘ └────────┘ └─────────┘      │
│         │         │         │              │
│         └─────────┼─────────┘              │
│                   │                        │
│            ┌──────▼──────┐                 │
│            │ Shizuku API │                 │
│            └─────────────┘                 │
│                                              │
└─────────────────────────────────────────────┘
```

### Chi Tiết Use Case

#### UC-1: Gửi Dữ Liệu Zalo

**Tham Gia Viên:** Người Gửi  
**Điều Kiện Tiên Quyết:** Ứng dụng đã cài, Shizuku đã cài, có dữ liệu Zalo  
**Kết Quả Mong Muốn:** Dữ liệu Zalo được gửi đến bên nhận

**Luồng Chính:**
```
1. Người dùng mở ứng dụng
2. Chọn "Gửi Dữ Liệu Zalo"
3. Ứng dụng yêu cầu quyền Shizuku
4. Người dùng cấp quyền
5. Ứng dụng quét thư mục Zalo
6. Hiển thị dung lượng (ví dụ: 500 MB)
7. Hiển thị chi phí coin (ví dụ: 100 coin)
8. Người dùng chọn WiFi hoặc Bluetooth
9. Ứng dụng tạo mã QR
10. Người dùng chia sẻ mã
11. Chờ bên nhận kết nối
12. Bên nhận kết nối
13. Bắt đầu truyền dữ liệu
14. Hiển thị tiến độ
15. Truyền hoàn thành
16. Trừ 100 coin từ tài khoản
17. Hiển thị thông báo hoàn thành
```

**Luồng Ngoại Lệ:**
```
- Nếu Shizuku không cài: Hiển thị hướng dẫn cài đặt
- Nếu từ chối quyền: Hiển thị thông báo lỗi
- Nếu kết nối bị gián đoạn: Tự động kết nối lại
- Nếu coin không đủ: Hiển thị lời nhắc mua coin
```

#### UC-2: Nhận Dữ Liệu Zalo

**Tham Gia Viên:** Người Nhận  
**Điều Kiện Tiên Quyết:** Ứng dụng đã cài, Shizuku đã cài, có kết nối WiFi/Bluetooth  
**Kết Quả Mong Muốn:** Dữ liệu Zalo được nhận và lưu

**Luồng Chính:**
```
1. Người dùng mở ứng dụng
2. Chọn "Nhận Dữ Liệu Zalo"
3. Chọn "Quét QR" hoặc "Nhập Mã"
4. Quét mã QR từ bên gửi (hoặc nhập mã)
5. Ứng dụng kết nối đến bên gửi
6. Hiển thị chi tiết truyền (500 MB, 5 phút)
7. Người dùng xác nhận
8. Ứng dụng yêu cầu quyền Shizuku
9. Người dùng cấp quyền
10. Bắt đầu nhận dữ liệu
11. Hiển thị tiến độ
12. Xác minh tổng kiểm
13. Lưu vào thư mục Zalo
14. Nhận hoàn thành
15. Hiển thị thông báo hoàn thành
```

**Luồng Ngoại Lệ:**
```
- Nếu mã QR không hợp lệ: Hiển thị lỗi
- Nếu kết nối thất bại: Hiển thị lỗi kết nối
- Nếu lưu trữ đầy: Hiển thị lỗi lưu trữ
- Nếu tổng kiểm không khớp: Yêu cầu truyền lại
```

#### UC-3: Mua Coin

**Tham Gia Viên:** Người Dùng  
**Điều Kiện Tiên Quyết:** Có tài khoản Google Play, kết nối internet  
**Kết Quả Mong Muốn:** Coin được thêm vào tài khoản

**Luồng Chính:**
```
1. Người dùng chọn "Mua Coin"
2. Hiển thị các gói coin
3. Người dùng chọn gói (ví dụ: 50 coin - $4.99)
4. Ứng dụng khởi tạo luồng thanh toán Google Play
5. Người dùng hoàn thành thanh toán
6. Google Play xác nhận thanh toán
7. Ứng dụng xác minh chữ ký
8. Thêm 50 coin vào tài khoản
9. Cập nhật UI
10. Hiển thị thông báo thành công
```

**Luồng Ngoại Lệ:**
```
- Nếu thanh toán thất bại: Hiển thị lỗi
- Nếu không có kết nối: Hiển thị lỗi mạng
- Nếu xác minh thất bại: Hiển thị lỗi bảo mật
```

---

## 📊 Luồng Dữ Liệu

### Data Flow Diagram (DFD)

#### Level 0 - Context Diagram

```
┌─────────────────────────────────────────────────────┐
│                                                      │
│  ┌────────────────┐      ┌────────────────┐        │
│  │  Người Gửi     │      │  Người Nhận    │        │
│  │  (Thiết Bị 1)  │      │  (Thiết Bị 2)  │        │
│  └────────┬───────┘      └────────┬───────┘        │
│           │                       │                 │
│           └───────────┬───────────┘                 │
│                       │                             │
│                ┌──────▼──────┐                      │
│                │  Zalo       │                      │
│                │  Transfer   │                      │
│                │  App        │                      │
│                └──────┬──────┘                      │
│                       │                             │
│        ┌──────────────┼──────────────┐              │
│        │              │              │              │
│   ┌────▼────┐  ┌─────▼────┐  ┌─────▼────┐        │
│   │Shizuku  │  │Google    │  │WiFi/BT  │        │
│   │API      │  │Play      │  │Network  │        │
│   └─────────┘  └──────────┘  └─────────┘        │
│                                                      │
└─────────────────────────────────────────────────────┘
```

#### Level 1 - Detailed DFD

```
┌─────────────────────────────────────────────────────────────┐
│                    Zalo Transfer System                      │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│  ┌─────────────────────────────────────────────────────┐   │
│  │ 1.0 Transfer Management                             │   │
│  │ ┌──────────────┐  ┌──────────────┐                 │   │
│  │ │ 1.1 Sender   │  │ 1.2 Receiver │                 │   │
│  │ │ Module       │  │ Module       │                 │   │
│  │ └──────┬───────┘  └──────┬───────┘                 │   │
│  │        │                 │                          │   │
│  │        └────────┬────────┘                          │   │
│  │               ┌─▼──────────┐                        │   │
│  │               │ 1.3 Network│                        │   │
│  │               │ Handler    │                        │   │
│  │               └────────────┘                        │   │
│  └─────────────────────────────────────────────────────┘   │
│                                                              │
│  ┌─────────────────────────────────────────────────────┐   │
│  │ 2.0 File Access Management                          │   │
│  │ ┌──────────────────────────────────────────────┐   │   │
│  │ │ 2.1 Shizuku Integration                      │   │   │
│  │ │ - Permission Management                      │   │   │
│  │ │ - File Access                                │   │   │
│  │ │ - Directory Scanning                         │   │   │
│  │ └──────────────────────────────────────────────┘   │   │
│  └─────────────────────────────────────────────────────┘   │
│                                                              │
│  ┌─────────────────────────────────────────────────────┐   │
│  │ 3.0 Payment Management                              │   │
│  │ ┌──────────────────────────────────────────────┐   │   │
│  │ │ 3.1 Google Play Billing                      │   │   │
│  │ │ - Purchase Processing                        │   │   │
│  │ │ - Coin Management                            │   │   │
│  │ │ - Transaction Logging                        │   │   │
│  │ └──────────────────────────────────────────────┘   │   │
│  └─────────────────────────────────────────────────────┘   │
│                                                              │
│  ┌─────────────────────────────────────────────────────┐   │
│  │ 4.0 Storage Management                              │   │
│  │ ┌──────────────────────────────────────────────┐   │   │
│  │ │ 4.1 Local Storage                            │   │   │
│  │ │ - SharedPreferences (Coin, History)          │   │   │
│  │ │ - File System (Zalo Data)                    │   │   │
│  │ └──────────────────────────────────────────────┘   │   │
│  └─────────────────────────────────────────────────────┘   │
│                                                              │
└─────────────────────────────────────────────────────────────┘
```

### Data Dictionary

#### Zalo Folder Structure

```
/sdcard/android/data/com.zing.zalo/files/
├── Chats/
│   ├── chat_1.db
│   ├── chat_2.db
│   └── ...
├── Media/
│   ├── Images/
│   ├── Videos/
│   ├── Audio/
│   └── Documents/
├── Stickers/
├── Profiles/
├── Cache/
└── Other/
```

#### Transfer Packet Structure

```json
{
  "header": {
    "magic": "0xDEADBEEF",
    "type": "0x06",
    "sequence": 12345,
    "payloadSize": 4194304,
    "checksum": "crc32_value",
    "flags": 0,
    "timestamp": 1707700000000
  },
  "payload": {
    "data": "binary_file_data"
  },
  "footer": {
    "endMarker": "0xCAFEBABE"
  }
}
```

#### Coin Transaction Record

```json
{
  "id": "uuid-xxx",
  "type": "TRANSFER_COST|PURCHASE|REFUND",
  "amount": 10,
  "timestamp": 1707700000000,
  "status": "SUCCESS|FAILED|PENDING",
  "details": {
    "transferSize": 52428800,
    "transferId": "uuid-yyy",
    "purchaseToken": "token_xxx",
    "orderId": "order-id-xxx"
  }
}
```

---

## 🔒 Ràng Buộc & Giả Định

### 1. Ràng Buộc Kỹ Thuật

| Ràng Buộc | Mô Tả |
|-----------|-------|
| **Phiên Bản Android** | Tối thiểu Android 8.0 (API 26) |
| **Kích Thước APK** | < 50 MB |
| **Dung Lượng RAM** | Tối thiểu 2 GB |
| **Kết Nối** | WiFi Direct hoặc Bluetooth 4.0+ |
| **Lưu Trữ** | Tối thiểu 100 MB không gian trống |
| **Shizuku** | Phiên bản 13.0+ |

### 2. Ràng Buộc Kinh Doanh

| Ràng Buộc | Mô Tả |
|-----------|-------|
| **Giá Coin** | 1 coin = 5 MB dữ liệu |
| **Tier Miễn Phí** | 10 MB/ngày miễn phí |
| **Gói Coin** | 5 gói từ $0.99 đến $99.99 |
| **Thị Trường** | Chỉ Google Play, không bên thứ ba |
| **Ngôn Ngữ** | Tiếng Việt, tiếng Anh |

### 3. Ràng Buộc Bảo Mật

| Ràng Buộc | Mô Tả |
|-----------|-------|
| **Mã Hóa** | TLS 1.2+ cho WiFi, Bluetooth encryption |
| **Không Lưu Trữ Đám Mây** | Tất cả dữ liệu truyền cục bộ |
| **Quyền** | Chỉ yêu cầu quyền cần thiết |
| **Xác Thực** | Mã ghép nối 6 chữ số + QR |

### 4. Giả Định

| Giả Định | Mô Tả |
|----------|-------|
| **Người Dùng Có Shizuku** | Hầu hết người dùng sẽ cài Shizuku |
| **Kết Nối Ổn Định** | WiFi/Bluetooth ổn định trong quá trình truyền |
| **Dữ Liệu Zalo Không Thay Đổi** | Dữ liệu Zalo không thay đổi trong quá trình truyền |
| **Người Dùng Tin Tưởng** | Người dùng tin tưởng ứng dụng không lưu dữ liệu |
| **Google Play Khả Dụng** | Google Play có sẵn ở tất cả thị trường |

---

## ✅ Tiêu Chí Chấp Nhận

### 1. Tiêu Chí Chấp Nhận Chức Năng

#### Chế Độ Gửi

- [ ] Có thể truy cập thư mục Zalo qua Shizuku
- [ ] Dung lượng được tính chính xác (±1%)
- [ ] Mã QR có thể quét được bằng bất kỳ ứng dụng quét nào
- [ ] Truyền dữ liệu không bị lỗi (0 byte mất)
- [ ] Tiến độ được cập nhật mỗi 500ms
- [ ] Coin được trừ chính xác sau truyền thành công
- [ ] Hoàn lại coin nếu truyền thất bại

#### Chế Độ Nhận

- [ ] Có thể quét mã QR chính xác
- [ ] Có thể nhập mã 6 chữ số thủ công
- [ ] Kết nối thành công với bên gửi (< 5 giây)
- [ ] Dữ liệu được nhận đầy đủ (100% dữ liệu)
- [ ] Tổng kiểm khớp (SHA-256)
- [ ] Dữ liệu được lưu đúng vị trí

#### Thanh Toán

- [ ] Mua coin thành công qua Google Play
- [ ] Coin được cập nhật ngay lập tức
- [ ] Giao dịch được ghi nhật ký
- [ ] Hoàn lại coin nếu giao dịch thất bại

### 2. Tiêu Chí Chấp Nhận Hiệu Năng

- [ ] Khởi động ứng dụng < 3 giây
- [ ] Truyền WiFi > 5 MB/s
- [ ] Truyền Bluetooth > 1 MB/s
- [ ] Sử dụng RAM < 100 MB
- [ ] Tiêu thụ pin < 10% mỗi giờ
- [ ] Không crash trong 1 giờ sử dụng liên tục

### 3. Tiêu Chí Chấp Nhận Bảo Mật

- [ ] Dữ liệu được mã hóa trong quá trình truyền
- [ ] Không có dữ liệu lưu trữ trên server bên thứ ba
- [ ] Mã ghép nối hết hạn sau 10 phút
- [ ] Tổng kiểm được xác minh trước/sau truyền
- [ ] Không ghi nhật ký nội dung tệp

### 4. Tiêu Chí Chấp Nhận Tương Thích

- [ ] Hoạt động trên Android 8.0 - 14+
- [ ] Hỗ trợ cả điện thoại và tablet
- [ ] Hỗ trợ cả chiều dọc và chiều ngang
- [ ] Hỗ trợ tất cả mật độ pixel

---

## ⚠️ Rủi Ro & Giải Pháp

### 1. Rủi Ro Kỹ Thuật

| Rủi Ro | Xác Suất | Tác Động | Giải Pháp |
|--------|----------|---------|----------|
| **Mất Kết Nối WiFi/BT** | HIGH | CRITICAL | Tự động kết nối lại, lưu trạng thái |
| **Lỗi Shizuku** | MEDIUM | CRITICAL | Hướng dẫn cài đặt, fallback |
| **Crash Ứng Dụng** | MEDIUM | HIGH | Xử lý ngoại lệ toàn diện, testing |
| **Tổng Kiểm Không Khớp** | LOW | CRITICAL | Yêu cầu truyền lại, logging |
| **Lưu Trữ Đầy** | MEDIUM | HIGH | Kiểm tra trước truyền, thông báo |
| **Hiệu Năng Kém** | MEDIUM | MEDIUM | Tối ưu hóa, profiling |

### 2. Rủi Ro Bảo Mật

| Rủi Ro | Xác Suất | Tác Động | Giải Pháp |
|--------|----------|---------|----------|
| **Dữ Liệu Bị Chặn** | LOW | CRITICAL | Mã hóa TLS 1.2+ |
| **Mã Ghép Nối Bị Đoán** | LOW | MEDIUM | Mã 6 chữ số + QR, hết hạn 10 phút |
| **Dữ Liệu Lưu Trên Server** | LOW | CRITICAL | Không lưu, chỉ truyền cục bộ |
| **Quyền Quá Mức** | MEDIUM | MEDIUM | Chỉ yêu cầu quyền cần thiết |
| **Lỗi Xác Thực** | LOW | HIGH | Xác minh chữ ký Google Play |

### 3. Rủi Ro Kinh Doanh

| Rủi Ro | Xác Suất | Tác Động | Giải Pháp |
|--------|----------|---------|----------|
| **Người Dùng Không Chấp Nhận Thanh Toán** | MEDIUM | HIGH | Tier miễn phí, giá cạnh tranh |
| **Cạnh Tranh Từ Ứng Dụng Khác** | MEDIUM | MEDIUM | Chuyên chuyên Zalo, chất lượng cao |
| **Bị Từ Chối Google Play** | LOW | CRITICAL | Tuân thủ chính sách, testing |
| **Mất Người Dùng** | MEDIUM | HIGH | Hỗ trợ tốt, cập nhật thường xuyên |

### 4. Kế Hoạch Giảm Thiểu Rủi Ro

#### Rủi Ro Kỹ Thuật

1. **Kiểm Thử Toàn Diện**
   - Unit test: 80%+ code coverage
   - Integration test: Tất cả luồng chính
   - Performance test: Tốc độ, bộ nhớ, pin
   - Security test: Mã hóa, xác thực

2. **Monitoring & Logging**
   - Ghi nhật ký chi tiết cho debugging
   - Theo dõi lỗi, hiệu năng
   - Alert khi có vấn đề

3. **Khôi Phục Lỗi**
   - Tự động kết nối lại
   - Lưu trạng thái truyền
   - Rollback nếu cần

#### Rủi Ro Bảo Mật

1. **Mã Hóa & Xác Thực**
   - TLS 1.2+ cho WiFi
   - Bluetooth encryption
   - Xác thực mã ghép nối

2. **Audit Bảo Mật**
   - Code review bảo mật
   - Penetration testing
   - Compliance check

#### Rủi Ro Kinh Doanh

1. **Chiến Lược Giá**
   - Tier miễn phí hấp dẫn
   - Giá cạnh tranh
   - Khuyến mãi định kỳ

2. **Chất Lượng & Hỗ Trợ**
   - Chất lượng cao
   - Hỗ trợ nhanh
   - Cập nhật thường xuyên

---

## 📅 Lộ Trình Phát Triển

### Phase 1: MVP (Phiên Bản Tối Thiểu Khả Dụng)

**Thời Gian:** 8-10 tuần  
**Mục Tiêu:** Phát hành phiên bản đầu tiên trên Google Play

#### Sprint 1-2: Setup & Architecture (2 tuần)

- [ ] Cài đặt dự án Android
- [ ] Thiết kế kiến trúc
- [ ] Cài đặt CI/CD
- [ ] Setup testing framework

#### Sprint 3-4: Core Features (2 tuần)

- [ ] Triển khai Shizuku integration
- [ ] Triển khai WiFi Direct
- [ ] Triển khai Bluetooth
- [ ] Triển khai transfer logic

#### Sprint 5-6: Payment & UI (2 tuần)

- [ ] Triển khai Google Play Billing
- [ ] Triển khai UI chính
- [ ] Triển khai progress tracking
- [ ] Triển khai settings

#### Sprint 7-8: Testing & Polish (2 tuần)

- [ ] Unit testing
- [ ] Integration testing
- [ ] Performance testing
- [ ] Security testing
- [ ] Bug fixing

#### Sprint 9-10: Release (2 tuần)

- [ ] Final testing
- [ ] Prepare for Google Play
- [ ] Submit to Google Play
- [ ] Monitor & support

### Phase 2: Enhancement (Cải Tiến)

**Thời Gian:** 4-6 tuần (sau MVP)  
**Mục Tiêu:** Thêm tính năng mới, cải tiến hiệu năng

- [ ] Hỗ trợ ứng dụng khác (WhatsApp, Telegram)
- [ ] Sao lưu đám mây
- [ ] Nén dữ liệu
- [ ] Mã hóa end-to-end
- [ ] Cải tiến UI/UX

### Phase 3: Scale (Mở Rộng)

**Thời Gian:** Dài hạn  
**Mục Tiêu:** Mở rộng thị trường, tăng người dùng

- [ ] Hỗ trợ ngôn ngữ khác
- [ ] Tích hợp backend
- [ ] Analytics & monitoring
- [ ] Marketing & promotion

---

## 📊 Bảng Tóm Tắt

### Tóm Tắt Yêu Cầu

| Loại | Số Lượng | Ưu Tiên |
|------|----------|--------|
| **Yêu Cầu Chức Năng Chính** | 7 | CRITICAL |
| **Yêu Cầu Chức Năng Phụ** | 3 | MEDIUM |
| **Yêu Cầu Phi Chức Năng** | 7 | HIGH |
| **Use Case** | 3 | - |
| **Rủi Ro** | 10 | - |

### Tóm Tắt Timeline

| Phase | Thời Gian | Mục Tiêu |
|-------|-----------|---------|
| **MVP** | 8-10 tuần | Phát hành v1.0 |
| **Enhancement** | 4-6 tuần | Thêm tính năng |
| **Scale** | Dài hạn | Mở rộng thị trường |

---

## 📝 Phê Duyệt

| Vai Trò | Tên | Chữ Ký | Ngày |
|---------|-----|--------|------|
| **Product Manager** | _____ | _____ | _____ |
| **Tech Lead** | _____ | _____ | _____ |
| **Security Lead** | _____ | _____ | _____ |
| **QA Lead** | _____ | _____ | _____ |

---

## 📞 Liên Hệ & Hỗ Trợ

**Câu Hỏi Về SRS?**
- Liên hệ Product Manager
- Tạo issue trong project management tool
- Họp review SRS hàng tuần

---

**Phiên Bản:** 1.0  
**Ngày Tạo:** 12/02/2026  
**Cập Nhật Lần Cuối:** 12/02/2026  
**Trạng Thái:** Chờ Phê Duyệt
