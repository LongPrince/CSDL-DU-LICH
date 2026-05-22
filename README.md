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

### 3.3.2. Doanh nghiệp

| **Tên Use case** | **Quản lý danh mục và tài khoản Doanh nghiệp** |
| :--- | :--- |
| **Mô tả** | Quản trị viên (QTV) thực hiện cấu hình phân loại doanh nghiệp, phê duyệt thông tin đăng ký hoạt động của các cơ sở kinh doanh, và quản lý việc thêm mới dữ liệu doanh nghiệp du lịch trên hệ thống. |
| **Tác nhân** | Quản trị viên hệ thống (Admin), Doanh nghiệp (đối với luồng khai báo thông tin) |
| **Độ phức tạp** | 🔲 Đơn giản  ☑️ Trung bình  🔲 Phức tạp |
| **Điều kiện bắt đầu** | Người dùng đăng nhập thành công với vai trò có quyền quản lý module Doanh nghiệp. |
| **Điều kiện kết thúc** | Danh mục loại doanh nghiệp được cập nhật hoặc trạng thái hoạt động/phê duyệt của doanh nghiệp được lưu thành công. |

---

#### 3.3.2.1. Loại doanh nghiệp

##### a. Danh sách loại doanh nghiệp
<p align="center"><i>Hình 3.17: Giao diện Danh sách Loại doanh nghiệp</i></p>

| **Màn hình** | **Danh sách Loại doanh nghiệp** |
| :--- | :--- |
| **Mô tả** | Màn hình hiển thị danh mục các loại hình kinh doanh của doanh nghiệp (VD: Lữ hành, Lưu trú, Ăn uống, Vận chuyển, Mua sắm). |
| **Màn hình kết nối** | Form Thêm mới Loại doanh nghiệp |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Tìm kiếm | Textfield – String | Tìm kiếm loại doanh nghiệp theo tên hoặc mã. |
| Thêm loại DN | Button | Nút mở form tạo mới loại doanh nghiệp. |
| Bảng danh sách | Table | Hiển thị danh mục các loại doanh nghiệp hiện có. |
| *Mã loại DN* | Label – String | Mã định danh phân loại (VD: LMD, DVLT). |
| *Tên loại DN* | Label – String | Tên phân loại (VD: Dịch vụ lưu trú, Nhà hàng). |
| *Trạng thái* | Badge | Đang áp dụng / Ngừng áp dụng. |
| *Thao tác* | Icon Buttons | Biểu tượng chỉnh sửa hoặc xóa loại hình. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Tìm kiếm** | Lọc dữ liệu theo từ khóa nhập vào. | Cập nhật bảng hiển thị đúng kết quả. | Không tìm thấy, bảng trống. |

---

##### b. Form Thêm mới loại doanh nghiệp
<p align="center"><i>Hình 3.18: Form Thêm mới Loại doanh nghiệp</i></p>

| **Màn hình** | **Thêm mới Loại doanh nghiệp** |
| :--- | :--- |
| **Mô tả** | Biểu mẫu nhập thông tin phân loại doanh nghiệp mới. |
| **Màn hình kết nối** | Danh sách loại doanh nghiệp |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Mã loại DN | Textfield – String | Nhập mã viết tắt không trùng lặp (Bắt buộc). |
| Tên loại DN | Textfield – String | Nhập tên loại hình doanh nghiệp (Bắt buộc). |
| Mô tả ngắn | Textarea | Nhập ghi chú hoặc mô tả đặc điểm loại hình. |
| Nút Lưu | Button | Xác nhận gửi dữ liệu lên hệ thống. |
| Nút Hủy | Button | Thoát biểu mẫu, quay lại danh sách. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Lưu thông tin** | Thực hiện đẩy dữ liệu lưu vào CSDL. | Gọi popup thêm thành công. | Điền thiếu thông tin, giữ nguyên form, báo đỏ. |

---

##### c. Popup Thêm loại doanh nghiệp thành công
<p align="center"><i>Hình 3.19: Popup Thông báo Thêm loại doanh nghiệp thành công</i></p>

| **Màn hình** | **Thông báo Thêm thành công (Popup)** |
| :--- | :--- |
| **Mô tả** | Hộp thoại thông báo khi cấu hình loại doanh nghiệp mới thành công. |
| **Màn hình kết nối** | Danh sách loại doanh nghiệp |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Biểu tượng | Icon | Icon dấu tích xanh thể hiện thành công. |
| Thông điệp | Text (static) | "Thêm mới loại doanh nghiệp thành công!" |
| Nút Xác nhận | Button | Đóng popup và chuyển hướng trang. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Xác nhận** | Đồng ý đóng thông báo. | Điều hướng quay lại giao diện danh sách loại doanh nghiệp. | (Không có) |

---

##### d. Popup Thêm loại doanh nghiệp thất bại
<p align="center"><i>Hình 3.20: Popup Thông báo Thêm loại doanh nghiệp thất bại</i></p>

| **Màn hình** | **Thông báo Thêm thất bại (Popup)** |
| :--- | :--- |
| **Mô tả** | Hộp thoại thông báo khi trùng mã loại doanh nghiệp hoặc thiếu dữ liệu. |
| **Màn hình kết nối** | Form Thêm mới loại doanh nghiệp |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Biểu tượng | Icon | Icon chấm than đỏ báo lỗi. |
| Thông điệp | Text (dynamic) | "Mã loại doanh nghiệp đã tồn tại trong hệ thống." |
| Nút Đóng | Button | Tắt thông báo lỗi. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Đóng** | Tắt hộp thoại lỗi. | Popup đóng lại, giữ nguyên biểu mẫu đang điền để hiệu chỉnh. | (Không có) |

---

#### 3.3.2.2. Duyệt doanh nghiệp

##### a. Giao diện Danh sách chờ duyệt
<p align="center"><i>Hình 3.21: Giao diện Danh sách doanh nghiệp chờ phê duyệt</i></p>

| **Màn hình** | **Danh sách Phê duyệt Thông tin Doanh nghiệp** |
| :--- | :--- |
| **Mô tả** | Giao diện dành cho QTV theo dõi các hồ sơ doanh nghiệp tự khai báo thông tin trên cổng du lịch đang ở trạng thái chờ duyệt. |
| **Màn hình kết nối** | Màn hình Chi tiết và Phê duyệt |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Bộ lọc trạng thái | Combobox | Lọc theo trạng thái: Chờ duyệt, Đã duyệt, Từ chối. |
| Tìm tên DN | Textfield – String | Tìm tên cơ sở kinh doanh/doanh nghiệp. |
| Bảng dữ liệu | Table | Danh sách hồ sơ doanh nghiệp. |
| *Tên doanh nghiệp* | Link | Bấm vào để xem chi tiết hồ sơ duyệt. |
| *Mã số thuế* | Label – String | Mã số thuế của cơ sở. |
| *Ngày gửi yêu cầu*| Label – Date | Thời gian doanh nghiệp gửi thông tin lên hệ thống. |
| *Trạng thái* | Badge | Nhãn màu vàng hiển thị chữ "Chờ duyệt". |
| *Thao tác* | Icon Button | Biểu tượng kính lúp/bút để mở form Phê duyệt chi tiết. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Xem chi tiết hồ sơ**| Chuyển tiếp tới màn hình phê duyệt. | Hiển thị giao diện thông tin chi tiết của DN được chọn. | Lỗi tải trang, thông báo thử lại. |

---

##### b. Màn hình Chi tiết và Phê duyệt doanh nghiệp
<p align="center"><i>Hình 3.22: Màn hình Phê duyệt thông tin doanh nghiệp chi tiết</i></p>

| **Màn hình** | **Phê duyệt thông tin doanh nghiệp chi tiết** |
| :--- | :--- |
| **Mô tả** | Giao diện hiển thị toàn bộ hồ sơ đăng ký của doanh nghiệp kèm các nút ra quyết định Phê duyệt hoặc Từ chối. |
| **Màn hình kết nối** | Danh sách doanh nghiệp chờ duyệt |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Khối thông tin chung | View fields | Hiển thị thông tin: Tên DN, Mã số thuế, Loại hình, Địa bàn, Địa chỉ, Số điện thoại, Email, Website. |
| Giấy phép ĐKKD | Link / Image | Tệp đính kèm bản quét Giấy chứng nhận đăng ký kinh doanh. |
| Ý kiến phê duyệt | Textarea | Nhập nội dung lý do (Bắt buộc nhập nếu nhấn Từ chối). |
| Nút Phê duyệt | Button (Xanh) | Chấp thuận thông tin doanh nghiệp hợp lệ. |
| Nút Từ chối | Button (Đỏ) | Từ chối chấp thuận hồ sơ đăng ký thông tin. |
| Nút Quay lại | Button | Quay trở lại danh sách chờ duyệt. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Phê duyệt** | Chấp nhận hồ sơ của doanh nghiệp. | Kích hoạt tài khoản doanh nghiệp, chuyển sang popup thành công. | Lỗi hệ thống, không cập nhật được CSDL. |
| **Từ chối** | Không duyệt hồ sơ thông tin. | Gửi thông báo từ chối về email DN (yêu cầu nhập ý kiến), mở popup từ chối. | Không điền "Ý kiến phê duyệt" $\rightarrow$ Báo lỗi bắt buộc nhập. |

---

##### c. Popup Phê duyệt thành công
<p align="center"><i>Hình 3.23: Popup Thông báo Phê duyệt doanh nghiệp thành công</i></p>

| **Màn hình** | **Thông báo Phê duyệt thành công (Popup)** |
| :--- | :--- |
| **Mô tả** | Hộp thoại thông báo khi QTV bấm duyệt hồ sơ thành công. |
| **Màn hình kết nối** | Danh sách doanh nghiệp chờ duyệt |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Biểu tượng | Icon | Biểu tượng checkmark xanh lá. |
| Nội dung | Text (static) | "Phê duyệt thông tin doanh nghiệp thành công!" |
| Nút Đồng ý | Button | Đóng popup, tự động chuyển về trang danh sách chờ duyệt. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Đồng ý đóng** | Quay lại quản lý danh sách. | Popup đóng, trạng thái doanh nghiệp cập nhật thành "Đã duyệt" trên danh sách. | (Không có) |

---

#### 3.3.2.3. Khai báo / thêm mới doanh nghiệp

##### a. Giao diện Form Khai báo / Thêm mới doanh nghiệp
<p align="center"><i>Hình 3.24: Giao diện Form Khai báo / Thêm mới doanh nghiệp</i></p>

| **Màn hình** | **Khai báo / Thêm mới doanh nghiệp** |
| :--- | :--- |
| **Mô tả** | Biểu mẫu áp dụng cho Doanh nghiệp tự đăng ký thông tin (Khai báo) hoặc Quản trị viên nhập trực tiếp dữ liệu cơ sở kinh doanh mới trên phân hệ Admin. |
| **Màn hình kết nối** | Trang chủ ứng dụng / Giao diện danh sách doanh nghiệp tổng thể |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Tên doanh nghiệp | Textfield – String | Nhập tên chính thức theo giấy phép kinh doanh (Bắt buộc). |
| Mã số thuế | Textfield – String | Nhập mã số thuế (Bắt buộc - Dùng làm thông tin đối chiếu trùng lặp). |
| Loại hình doanh nghiệp| Combobox | Lựa chọn loại hình kinh doanh (Khách sạn, Lữ hành, Nhà hàng...). |
| Địa bàn trực thuộc | Combobox | Chọn Tỉnh/Thành phố, Quận/Huyện quản lý trực tiếp. |
| Địa chỉ chi tiết | Textfield – String | Nhập số nhà, tên đường, phường xã cụ thể. |
| Điện thoại liên hệ | Textfield – String | Nhập số điện thoại liên lạc của cơ sở kinh doanh (Bắt buộc). |
| Email | Textfield – String | Nhập địa chỉ thư điện tử để nhận thông báo từ hệ thống. |
| Tải giấy phép ĐKKD | File Uploader | Đính kèm file ảnh hoặc file PDF giấy đăng ký kinh doanh. |
| Nút Gửi hồ sơ / Lưu | Button | Thực hiện đẩy dữ liệu đăng ký/thêm mới vào hệ thống. |
| Nút Hủy | Button | Thoát khỏi biểu mẫu khai báo dữ liệu. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Gửi hồ sơ / Lưu** | Lưu thông tin bản ghi đăng ký. | Đẩy dữ liệu vào trạng thái chờ duyệt (với DN khai báo) hoặc lưu thẳng (với QTV), mở popup thành công. | Để trống thông tin bắt buộc hoặc định dạng ảnh ĐKKD không hợp lệ $\rightarrow$ Báo lỗi tại trường. |

---

##### b. Popup Đăng ký / Khai báo doanh nghiệp thành công
<p align="center"><i>Hình 3.25: Popup Đăng ký / Khai báo doanh nghiệp thành công</i></p>

| **Màn hình** | **Thông báo Đăng ký / Khai báo thành công (Popup)** |
| :--- | :--- |
| **Mô tả** | Hộp thoại thông báo dữ liệu doanh nghiệp đã được tiếp nhận thành công. |
| **Màn hình kết nối** | Màn hình đăng nhập / Trang danh sách chính |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Biểu tượng | Icon | Hình tròn dấu kiểm màu xanh lá. |
| Thông điệp thông báo | Text (static) | "Khai báo thông tin doanh nghiệp thành công! Hồ sơ của bạn đang chờ phê duyệt từ Ban quản trị." |
| Nút Hoàn tất | Button | Bấm để đóng biểu mẫu và kết thúc luồng xử lý. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Hoàn tất** | Đồng ý đóng thông báo. | Popup đóng lại, chuyển hướng người dùng về màn hình theo quy định. | (Không có) |

---

##### c. Popup Đăng ký / Khai báo doanh nghiệp thất bại
<p align="center"><i>Hình 3.26: Popup Đăng ký / Khai báo doanh nghiệp thất bại</i></p>

| **Màn hình** | **Thông báo Đăng ký / Khai báo thất bại (Popup)** |
| :--- | :--- |
| **Mô tả** | Hộp thoại xuất hiện khi mã số thuế doanh nghiệp bị trùng lập với một cơ sở kinh doanh đã tồn tại. |
| **Màn hình kết nối** | Giữ nguyên Form Khai báo / Thêm mới doanh nghiệp |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Biểu tượng | Icon | Hình tròn chứa dấu X màu đỏ rực. |
| Thông điệp lỗi | Text (dynamic) | "Đăng ký thất bại! Mã số thuế này đã được đăng ký trên hệ thống du lịch." |
| Nút Quay lại chỉnh sửa| Button | Bấm để đóng popup lỗi và chỉnh sửa dữ liệu trên form. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Quay lại chỉnh sửa**| Đóng popup lỗi. | Tắt thông báo, giữ nguyên toàn bộ các thông tin doanh nghiệp vừa điền để chỉnh sửa mã số thuế. | (Không có) |
