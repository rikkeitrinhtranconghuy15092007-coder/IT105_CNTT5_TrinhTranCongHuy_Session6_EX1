# BÁO CÁO THỰC HÀNH: TỔNG HỢP ACTIVITY & USE CASE DIAGRAM HỆ THỐNG RIKKEIBANK

## 1. Mục tiêu và Bối cảnh
Tài liệu này là bản thuyết minh chi tiết cho bài thực hành mô hình hóa quy trình rút tiền không thẻ tại ATM của RikkeiBank. Báo cáo cung cấp các bảng phân rã chức năng và phân tích quan hệ logic.

---

## 2. PHẦN A — Phân tích Activity Diagram
Kịch bản nghiệp vụ: Khách hàng quét mã QR. Hệ thống kiểm tra số dư. Nếu đủ số dư, hệ thống thực hiện hai tác vụ song song: nhả tiền và gửi SMS báo biến động số dư. Nếu không đủ số dư, hệ thống hiển thị lỗi và kết thúc luồng nghiệp vụ.

| Loại Node | Tên Node / Tác vụ | Swimlane phụ trách |
| :--- | :--- | :--- |
| Initial Node | Bắt đầu | — |
| Action | Quét mã QR | Khách hàng |
| Decision | Kiểm tra số dư (Đủ / Không đủ) | Hệ thống |
| Fork | **Tách nhánh đồng thời (khi Đủ số dư)** | **Hệ thống** |
| Action | **Nhả tiền** | **Hệ thống** |
| Action | **Gửi SMS báo biến động số dư** | **Hệ thống** |
| Join | **Gộp nhánh đồng thời (sau khi xử lý xong)** | **Hệ thống** |
| Action | **Hiển thị lỗi (nhánh Không đủ số dư)** | **Hệ thống** |
| Final Node | Kết thúc | — |

---

## 3. PHẦN B — Phân tích Use Case Diagram
Hệ thống yêu cầu khách hàng phải đăng nhập (bắt buộc) trước khi thực hiện chức năng Rút tiền. Sau khi rút tiền, khách hàng có thể chọn in hóa đơn giao dịch (tùy chọn). Chức năng rút tiền được chuyên biệt hóa thành hai dạng: Rút tiền tiêu chuẩn và Rút tiền nhanh.

| Use Case A | Use Case B | Quan hệ | Giải thích logic |
| :--- | :--- | :--- | :--- |
| Rút tiền | Đăng nhập | `<<include>>` | Phải đăng nhập trước khi rút tiền (Bắt buộc). |
| Rút tiền | In hóa đơn giao dịch | `<<extend>>` | **Tính năng in hóa đơn là tùy chọn, khách hàng có thể chọn in hoặc không sau khi rút tiền thành công.** |
| Rút tiền | Rút tiền tiêu chuẩn | `<<generalization>>` | Là một dạng chuyên biệt của Rút tiền (Kế thừa). |
| Rút tiền | **Rút tiền nhanh** | `<<generalization>>` | **Là một dạng chuyên biệt của Rút tiền (Kế thừa, được thiết lập sẵn mệnh giá).** |

---
*Ghi chú: Sinh viên đính kèm file này cùng với hình ảnh xuất từ draw.io để nộp bài.*
