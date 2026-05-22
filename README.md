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

<p align="center"><i>Hình 3.12: Giao diện Thêm mới địa bàn</i></p>

**b. Thêm thành công**
- **Mô tả kịch bản:** Sau khi người dùng điền đầy đủ và chính xác các thông tin (Mã địa bàn không bị trùng, điền đủ Tên và Cấp địa bàn) $\rightarrow$ Nhấn nút **"Lưu"**.
- **Kết quả:** - Hệ thống ghi nhận dữ liệu vào CSDL.
  - Hiển thị thông báo Popup (màu xanh): *"Thêm mới danh mục địa bàn thành công!"*.
  - Biểu mẫu tự động đóng lại, chuyển hướng người dùng về màn hình Danh sách địa bàn. Dữ liệu vừa thêm xuất hiện trên cùng của bảng danh sách.

<p align="center"><i>Hình 3.13: Thông báo thêm địa bàn thành công</i></p>

**c. Thêm thất bại**
- **Mô tả kịch bản:** Người dùng bỏ trống các trường bắt buộc (Mã địa bàn, Tên địa bàn) hoặc nhập Mã địa bàn đã tồn tại trên hệ thống $\rightarrow$ Nhấn nút **"Lưu"**.
- **Kết quả:**
  - Hệ thống từ chối lưu dữ liệu.
  - Hiển thị thông báo cảnh báo (màu đỏ): *"Vui lòng nhập đầy đủ thông tin bắt buộc"* hoặc *"Mã địa bàn đã tồn tại. Vui lòng kiểm tra lại!"*.
  - Các trường dữ liệu bị lỗi sẽ được làm nổi bật (viền đỏ) để người dùng sửa lại. Giao diện biểu mẫu vẫn giữ nguyên, không bị đóng.

<p align="center"><i>Hình 3.14: Thông báo thêm địa bàn thất bại</i></p>

---

#### 3.3.1.2. Sửa địa bàn

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

<p align="center"><i>Hình 3.15: Giao diện Chỉnh sửa địa bàn</i></p>

---

#### 3.3.1.3. Xóa địa bàn

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

<p align="center"><i>Hình 3.16: Hộp thoại Xác nhận xóa địa bàn</i></p>
