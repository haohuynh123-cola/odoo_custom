# Tính Năng Mở Rộng Dịch Vụ Hiện Trường (Custom Field Service)

## Tổng Quan
Mô-đun này mở rộng chức năng dịch vụ hiện trường của Odoo bằng cách thêm các tính năng mới giúp quản lý trạng thái của nhiệm vụ linh hoạt hơn, bao gồm khả năng hủy và từ chối nhiệm vụ.

## Tính Năng Chính

### 1. Hủy Nhiệm Vụ Đang Xử Lý
- Thêm nút "Hủy" cho các nhiệm vụ đang trong quá trình xử lý
- Hiển thị hộp thoại yêu cầu lý do hủy
- Cập nhật trạng thái nhiệm vụ sang "Đã Hủy" (CANCELED)
- Lưu lại lý do hủy để tham khảo sau này
- Tự động dừng bộ đếm thời gian nếu đang chạy

### 2. Từ Chối Nhiệm Vụ Đang Xem Xét
- Thêm nút "Từ Chối" cho các nhiệm vụ đang trong trạng thái xem xét (REVIEW)
- Hiển thị hộp thoại yêu cầu lý do từ chối
- Cập nhật trạng thái nhiệm vụ sang "Đã Từ Chối" (REJECTED)
- Lưu lại lý do từ chối để tham khảo sau này
- Tự động dừng bộ đếm thời gian nếu đang chạy

### 3. Quản Lý Trạng Thái Nâng Cao
- Thêm mã trạng thái (N00, N10, N11, L00, L10, L11) để đánh giá nhiệm vụ dựa trên tiến độ và thời hạn
- Tự động cập nhật mã trạng thái dựa trên việc phân công, tiến độ và thời hạn
- Hiển thị nhiệm vụ khẩn cấp với định dạng đặc biệt

### 4. Quản Lý Nhân Sự Trong Dự Án
- Tự động lọc người dùng trong dự án để phân công nhiệm vụ
- Tự động phân công nhiệm vụ dựa trên cấu hình lịch trình
- Hỗ trợ phân phối nhiệm vụ cân bằng giữa các thành viên dự án

### 5. Theo Dõi Quy Trình Công Việc
- Các nút hành động để chuyển trạng thái: Phân công, Bắt đầu, Xem xét, Phê duyệt
- Lưu thời gian bắt đầu và kết thúc của nhiệm vụ
- Tính điểm đánh giá cho mỗi nhiệm vụ

## Cài Đặt
1. Sao chép thư mục `custom_cancel_field_service` vào đường dẫn `addons` của Odoo
2. Cập nhật danh sách ứng dụng
3. Tìm và cài đặt mô-đun "Custom Field Service"

## Phụ Thuộc
- industry_fsm
- sale
- web

## Cấu Trúc File
```
    custom_cancel_field_service/
    │
    ├── __init__.py                      # Khởi tạo module
    ├── __manifest__.py                  # Manifest mô tả module
    │
    ├── controllers/                     # Controllers xử lý các yêu cầu HTTP
    │   └── __init__.py
    │
    ├── models/                          # Định nghĩa models
    │   ├── __init__.py
    │   └── project_task.py              # Mở rộng model project.task
    │
    ├── wizard/                          # Các wizard (hộp thoại)
    │   ├── __init__.py
    │   ├── cancel_reason_wizard.py      # Wizard cho lý do hủy nhiệm vụ
    │   ├── cancel_reason_wizard_views.xml
    │   ├── reject_reason_wizard.py      # Wizard cho lý do từ chối nhiệm vụ
    │   └── reject_reason_wizard_views.xml
    │
    ├── views/                           # Giao diện người dùng
    │   ├── assets.xml                   # Tài nguyên web (CSS/JS)
    │   ├── project_task_views.xml       # Giao diện nhiệm vụ
    │   └── project_edit_form_views.xml  # Form chỉnh sửa dự án
    │
    └── security/
        └── ir.model.access.csv          # Quyền truy cập model
```
## Giấy Phép
LGPL-3

## Phiên Bản
1.0
