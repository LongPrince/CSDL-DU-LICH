# 3. THIẾT KẾ CHI TIẾT CÁC CHỨC NĂNG

## 3.3 Quản lý danh mục hệ thống
### 3.3.1 Địa bàn

#### 1. Mô tả Use Case

| Tiêu chí | Nội dung |
|---|---|
| **Tên Use case** | Danh mục địa bàn |
| **Mô tả** | Quản trị hệ thống xem danh sách các đơn vị hành chính (thành phố, quận/huyện, phường/xã) chỉnh sửa /thêm / xóa |
| **Tác nhân** | Quản trị hệ thống |
| **Độ phức tạp** | Trung bình |
| **Điều kiện bắt đầu** | Quản trị hệ thống đã đăng nhập |
| **Điều kiện kết thúc** | Danh sách địa bàn được hiển thị hoặc chuyển sang form thêm/sửa/xóa |
| **Kịch bản chính** | 1. Chọn menu "Danh mục" → "Địa bàn"<br>2. Hệ thống hiển thị danh sách địa bàn<br>3. Có thể tìm kiếm/lọc theo tên hoặc cấp địa bàn<br>4. Nhấn "Thêm mới" → chuyển sang form thêm<br>5. Nhấn biểu tượng sửa → chuyển sang form chỉnh sửa<br>6. Nhấn biểu tượng xóa → xóa địa bàn (nếu không có ràng buộc) |
| **Kịch bản phụ** | - Xóa địa bàn đang có điểm đến/cơ sở lưu trú tham chiếu: hệ thống từ chối và thông báo<br>- Xóa quận/huyện đang có phường/xã: từ chối xóa |
| **Các yêu cầu, ràng buộc** | Dữ liệu phân cấp: Thành phố → Quận/Huyện → Phường/Xã; Mỗi địa bàn có mã định danh duy nhất |

---

#### a. Danh sách địa bàn

**Thông tin màn hình**

| Tiêu chí | Nội dung |
|---|---|
| **Màn hình** | Danh mục Phường / Xã (Danh sách địa bàn) |
| **Mô tả** | Chức năng này cho phép Quản trị hệ thống xem và quản lý danh sách các đơn vị hành chính. |
| **Màn hình kết nối** | Thêm mới địa bàn, Sửa thông tin địa bàn, Xóa địa bàn |

**Nội dung màn hình**

| Item | Kiểu dữ liệu | Mô tả |
|---|---|---|
| Thành phố / Phường / Xã | Combobox - String | Lọc danh sách theo cấp đơn vị hành chính hoặc địa bàn cụ thể |
| Trạng thái | Combobox - String | Lọc theo trạng thái hoạt động của địa bàn |
| Thêm Phường/Xã mới | Button | Chuyển sang màn hình thêm mới địa bàn |
| Danh sách đơn vị hành chính | Table | Hiển thị danh sách địa bàn |
| STT | Label - Number | Số thứ tự |
| Mã đơn vị | Label - String | Mã định danh của đơn vị hành chính |
| Tên Phường/Xã | Label - String | Tên của đơn vị hành chính |
| Chỉnh sửa | Icon Button | Mở form chỉnh sửa thông tin địa bàn |
| Xóa | Icon Button | Xóa đơn vị hành chính khỏi hệ thống |
| Phân trang | Pagination | Chuyển đổi giữa các trang danh sách |
| Tổng số phường / xã | Label - Number | Hiển thị thống kê tổng số lượng địa bàn |

**Các chức năng màn hình**

| Tên chức năng | Mô tả | Thành công | Thất bại |
|---|---|---|---|
| Lọc địa bàn | Lọc danh sách theo cấp hành chính hoặc trạng thái | Hiển thị đúng danh sách theo tiêu chí lọc | Không có dữ liệu phù hợp với tiêu chí |
| Thêm mới | Mở form thêm địa bàn | Chuyển sang form thêm mới | |
| Chỉnh sửa | Mở form chỉnh sửa địa bàn đã chọn | Điều hướng đến trang chỉnh sửa với dữ liệu được tải sẵn | |
| Xóa | Xóa địa bàn khỏi hệ thống | Hiển thị form xác nhận xóa | |

---

#### b. Thêm địa bàn

**Thông tin màn hình**

| Tiêu chí | Nội dung |
|---|---|
| **Màn hình** | Thêm mới địa bàn |
| **Mô tả** | Chức năng này cho phép quản trị hệ thống thêm mới một đơn vị hành chính vào hệ thống. |
| **Màn hình kết nối** | Danh sách địa bàn |

**Nội dung màn hình**

| Item | Kiểu dữ liệu | Mô tả |
|---|---|---|
| Cấp hành chính | Combobox - String | Chọn cấp (Thành phố / Quận / Huyện / Phường / Xã) |
| Trực thuộc | Combobox - String | Chọn đơn vị hành chính cấp trên (nếu có) |
| Mã đơn vị | Textfield - String | Nhập mã định danh duy nhất cho địa bàn |
| Tên địa bàn | Textfield - String | Nhập tên đơn vị hành chính |
| Trạng thái | Combobox - String | Chọn trạng thái (Đang hoạt động / Tạm ngưng) |
| Mô tả | Textarea - String | Nhập thêm thông tin mô tả nếu có |
| Lưu | Button | Lưu thông tin địa bàn mới vào hệ thống |
| Hủy bỏ | Button | Hủy thao tác thêm mới và quay lại danh sách |

**Các chức năng màn hình**

| Tên chức năng | Mô tả | Thành công | Thất bại |
|---|---|---|---|
| Lưu | Thêm mới địa bàn vào CSDL | Hiển thị thông báo thành công, quay lại danh sách | Thông báo lỗi (trùng mã, thiếu thông tin bắt buộc) |
| Hủy bỏ | Hủy thao tác | Đóng form thêm mới, quay lại danh sách | |

---

#### c. Sửa thông tin địa bàn

**Thông tin màn hình**

| Tiêu chí | Nội dung |
|---|---|
| **Màn hình** | Chỉnh sửa thông tin địa bàn |
| **Mô tả** | Chức năng này cho phép quản trị hệ thống thay đổi thông tin của một đơn vị hành chính. |
| **Màn hình kết nối** | Danh sách địa bàn |

**Nội dung màn hình**

| Item | Kiểu dữ liệu | Mô tả |
|---|---|---|
| Cấp hành chính | Combobox - String | Không cho phép sửa (Disable) hoặc chọn cấp tương ứng |
| Trực thuộc | Combobox - String | Chọn lại đơn vị hành chính cấp trên |
| Mã đơn vị | Textfield - String | Mã định danh (Disable - Không cho phép sửa) |
| Tên địa bàn | Textfield - String | Sửa tên đơn vị hành chính |
| Trạng thái | Combobox - String | Sửa trạng thái (Đang hoạt động / Tạm ngưng) |
| Mô tả | Textarea - String | Sửa thông tin mô tả |
| Lưu | Button | Cập nhật thông tin đã sửa vào hệ thống |
| Hủy | Button | Hủy thay đổi và quay lại danh sách |

**Các chức năng màn hình**

| Tên chức năng | Mô tả | Thành công | Thất bại |
|---|---|---|---|
| Lưu | Cập nhật thông tin địa bàn | Thông báo thành công, quay về danh sách | Thông báo lỗi validation |
| Hủy | Hủy thao tác | Quay lại danh sách, không lưu thay đổi | |

---

#### d. Xóa địa bàn

**Thông tin màn hình**

| Tiêu chí | Nội dung |
|---|---|
| **Màn hình** | Xóa địa bàn |
| **Mô tả** | Hiển thị hộp thoại xác nhận trước khi xóa địa bàn để tránh thao tác nhầm lẫn. |
| **Màn hình kết nối** | Danh sách địa bàn |

**Nội dung màn hình**

| Item | Kiểu dữ liệu | Mô tả |
|---|---|---|
| Tiêu đề hộp thoại | String (static) | "Xác nhận xóa địa bàn" |
| Câu hỏi xác nhận | String (dynamic) | "Bạn có chắc chắn muốn xóa địa bàn [Tên địa bàn] khỏi hệ thống?" |
| Cảnh báo logic | String (static) | Hiển thị cảnh báo nếu xóa sẽ ảnh hưởng dữ liệu hoặc không cho phép xóa nếu có dữ liệu phụ thuộc |
| Xác nhận Xóa | Button | Thực hiện xóa vĩnh viễn địa bàn |
| Hủy bỏ | Button | Đóng hộp thoại, không xóa |

**Các chức năng màn hình**

| Tên chức năng | Mô tả | Thành công | Thất bại |
|---|---|---|---|
| Xác nhận Xóa | Thực hiện xóa địa bàn khỏi CSDL | Xóa thành công, làm mới danh sách | Xóa thất bại do lỗi ràng buộc (địa bàn đang có dữ liệu con/tham chiếu) |
| Hủy bỏ | Hủy thao tác xóa | Đóng hộp thoại xác nhận | |
