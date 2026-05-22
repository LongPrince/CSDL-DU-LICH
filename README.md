### 3.3.1. Địa bàn

| **Tên Use case** | **Quản lý danh mục Địa bàn** |
| :--- | :--- |
| **Mô tả** | Quản trị viên thực hiện xem danh sách, thêm mới, cập nhật và xóa các đơn vị hành chính (Tỉnh/Thành phố, Quận/Huyện, Phường/Xã) trên hệ thống để làm cơ sở dữ liệu gốc phân cấp cho các module khác. |
| **Tác nhân** | Quản trị viên hệ thống (Admin) |
| **Độ phức tạp** | ☑️ Đơn giản  🔲 Trung bình  🔲 Phức tạp |
| **Điều kiện bắt đầu** | Người dùng đăng nhập bằng tài khoản Quản trị viên và truy cập menu "Danh mục" $\rightarrow$ "Địa bàn". |
| **Điều kiện kết thúc** | Thông tin danh mục địa bàn được tạo, cập nhật hoặc xóa thành công khỏi hệ thống. |

---

#### 3.3.1.1. Thêm địa bàn

**a. Thêm địa bàn**
<p align="center"><i>Hình 3.12: Giao diện Thêm mới địa bàn</i></p>

| **Màn hình** | **Thêm mới Địa bàn** |
| :--- | :--- |
| **Mô tả** | Biểu mẫu cho phép Quản trị viên nhập thông tin một đơn vị hành chính mới vào hệ thống. |
| **Màn hình kết nối** | Danh sách địa bàn |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Mã địa bàn | Textfield – String | Nhập mã định danh của địa bàn (VD: HUE, TP_HUE) (Bắt buộc). |
| Tên địa bàn | Textfield – String | Nhập tên đơn vị hành chính (VD: Thừa Thiên Huế) (Bắt buộc). |
| Cấp địa bàn | Combobox | Chọn cấp hành chính: Tỉnh/Thành phố, Quận/Huyện, Phường/Xã. |
| Trực thuộc | Combobox | Chọn địa bàn cha (VD: Nếu chọn cấp Phường/Xã, phải chọn thuộc Quận/Huyện nào). |
| Ghi chú | Textarea | Nhập các thông tin mô tả thêm (không bắt buộc). |
| Trạng thái | Toggle | Bật/tắt trạng thái hiển thị (Đang sử dụng / Ngừng sử dụng). |
| Nút Lưu | Button | Click để thực hiện lưu dữ liệu vào hệ thống. |
| Nút Hủy | Button | Click để đóng form, quay về trang danh sách. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Lưu dữ liệu** | Lưu thông tin địa bàn vừa nhập. | Hiển thị thông báo thành công và chuyển về danh sách. | Hiển thị thông báo lỗi nếu nhập thiếu/sai. |
| **Hủy thao tác** | Đóng biểu mẫu. | Quay về màn hình danh sách địa bàn. | (Không có) |



---

**b. Thêm thành công (Hộp thoại thông báo)**
<p align="center"><i>Hình 3.13: Thông báo thêm địa bàn thành công</i></p>

| **Màn hình** | **Thông báo thêm thành công (Popup)** |
| :--- | :--- |
| **Mô tả** | Hộp thoại thông báo cho người dùng biết thao tác thêm mới địa bàn đã được lưu thành công vào cơ sở dữ liệu hệ thống. |
| **Màn hình kết nối** | Danh sách địa bàn |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Biểu tượng | Icon | Biểu tượng checkmark (✓) màu xanh lá cây thể hiện sự thành công. |
| Nội dung thông báo | Text (static) | Dòng chữ "Thêm mới danh mục địa bàn thành công!". |
| Nút Đóng / OK | Button | Nút bấm xác nhận để đóng hộp thoại thông báo. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Đóng hộp thoại** | Tắt thông báo thành công. | Đóng popup, hệ thống tự động làm mới (refresh) và điều hướng về trang Danh sách địa bàn với dữ liệu mới ở trên cùng. | (Không có) |



---

**c. Thêm thất bại (Hộp thoại cảnh báo)**
<p align="center"><i>Hình 3.14: Thông báo thêm địa bàn thất bại</i></p>

| **Màn hình** | **Thông báo thêm thất bại / Lỗi (Popup)** |
| :--- | :--- |
| **Mô tả** | Hộp thoại hoặc cảnh báo xuất hiện khi người dùng bỏ trống trường bắt buộc hoặc nhập mã địa bàn đã tồn tại. |
| **Màn hình kết nối** | Thêm mới Địa bàn (Giữ nguyên màn hình hiện tại) |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Biểu tượng | Icon | Biểu tượng chấm than (!) hoặc dấu X màu đỏ thể hiện lỗi. |
| Nội dung cảnh báo | Text (dynamic) | Dòng chữ thông báo lỗi: "Vui lòng nhập đầy đủ thông tin bắt buộc" hoặc "Mã địa bàn đã tồn tại". |
| Nút Đóng | Button | Nút bấm để tắt thông báo lỗi. |
| Đánh dấu lỗi | UI Highlight | Các trường nhập liệu bị lỗi sẽ được làm nổi bật (viền đỏ) để người dùng dễ nhận biết. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Tắt cảnh báo** | Đóng thông báo lỗi để tiếp tục nhập liệu. | Đóng popup, hệ thống giữ nguyên giao diện biểu mẫu với các dữ liệu đang nhập dở để người dùng sửa lại cho đúng. | (Không có) |



---

#### 3.3.1.2. Sửa địa bàn
<p align="center"><i>Hình 3.15: Giao diện Chỉnh sửa địa bàn</i></p>

| **Màn hình** | **Chỉnh sửa Địa bàn** |
| :--- | :--- |
| **Mô tả** | Biểu mẫu cho phép thay đổi thông tin (Tên, cấp, trực thuộc, trạng thái) của một địa bàn đã có. |
| **Màn hình kết nối** | Danh sách địa bàn |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Mã địa bàn | Textfield – String | Hiển thị mã địa bàn hiện tại. Thuộc tính: *Read-only* (Không cho phép sửa mã định danh). |
| Tên địa bàn | Textfield – String | Cho phép chỉnh sửa lại tên địa bàn. |
| Cấp địa bàn | Combobox | Thay đổi cấp hành chính. |
| Trực thuộc | Combobox | Cập nhật lại đơn vị hành chính cấp trên. |
| Ghi chú | Textarea | Sửa đổi mô tả. |
| Trạng thái | Toggle | Cập nhật trạng thái (Bật/Tắt). |
| Nút Cập nhật | Button | Lưu đè thay đổi vào CSDL. |
| Nút Hủy | Button | Thoát và không lưu. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Cập nhật** | Ghi nhận các thay đổi chỉnh sửa. | Lưu thành công, thông báo "Cập nhật thành công", quay lại danh sách. | Để trống tên địa bàn $\rightarrow$ Báo lỗi đỏ tại trường Tên. |



---

#### 3.3.1.3. Xóa địa bàn
<p align="center"><i>Hình 3.16: Hộp thoại Xác nhận xóa địa bàn</i></p>

| **Màn hình** | **Xóa Địa bàn (Popup Xác nhận)** |
| :--- | :--- |
| **Mô tả** | Hộp thoại cảnh báo xuất hiện khi người dùng nhấn nút Xóa, nhằm ngăn chặn việc xóa nhầm dữ liệu danh mục gốc. |
| **Màn hình kết nối** | Danh sách địa bàn |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Tiêu đề | Text (static) | "Xác nhận xóa danh mục" |
| Nội dung cảnh báo | Text (dynamic) | "Bạn có chắc chắn muốn xóa địa bàn [Tên_Địa_Bàn]? Lưu ý: Không thể xóa nếu địa bàn này đang có dữ liệu trực thuộc." |
| Nút Xác nhận | Button (Đỏ) | Thực thi lệnh xóa khỏi CSDL. |
| Nút Hủy bộ | Button (Xám) | Đóng cửa sổ cảnh báo, không xóa dữ liệu. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Xác nhận xóa** | Xóa bản ghi khỏi danh mục. | Xóa thành công, làm mới bảng danh sách, hiển thị thông báo. | Báo lỗi: "Không thể xóa do địa bàn này đang có Quận/Huyện/Phường trực thuộc hoặc đang có cơ sở lưu trú gắn liền". |

