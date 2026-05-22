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

| **Tên Use case** | **Quản lý danh mục và thông tin Doanh nghiệp** |
| :--- | :--- |
| **Mô tả** | Cung cấp công cụ quản lý toàn diện vòng đời của một doanh nghiệp du lịch trên hệ thống: từ việc cấu hình danh mục phân loại (Loại hình), tiếp nhận thông tin tự kê khai của doanh nghiệp (Khai báo), xử lý thẩm định cấp quyền (Duyệt), cho đến việc theo dõi danh sách tập trung (Hồ sơ). |
| **Tác nhân** | Quản trị viên hệ thống (Admin/QTV), Người dùng Doanh nghiệp |
| **Độ phức tạp** | ☑️ Đơn giản  🔲 Trung bình  🔲 Phức tạp |
| **Điều kiện bắt đầu** | - Đối với Admin: Đăng nhập thành công và chọn phân hệ "Quản lý danh mục" &rarr; "Doanh nghiệp".<br>- Đối với Doanh nghiệp: Đăng nhập tài khoản doanh nghiệp lần đầu hoặc truy cập phân hệ cập nhật thông tin đơn vị. |
| **Điều kiện kết thúc** | Thông tin doanh nghiệp được chuẩn hóa, phê duyệt hợp lệ và lưu trữ đồng bộ vào Cơ sở dữ liệu du lịch thành phố. |

---

#### a. Loại hình doanh nghiệp

<p align="center"><i>Hình 3.12: Giao diện Danh sách Loại hình doanh nghiệp du lịch</i></p>

| **Màn hình** | **Danh sách Loại hình doanh nghiệp du lịch** |
| :--- | :--- |
| **Mô tả** | Giao diện quản trị dành cho Admin để theo dõi và định cấu hình các nhóm ngành nghề kinh doanh du lịch chính (Lưu trú, Lữ hành, Dịch vụ...). |
| **Màn hình kết nối** | Hồ sơ doanh nghiệp |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Bộ lọc Loại hình | Combobox | Cho phép chọn phân loại cụ thể để lọc nhanh danh sách dữ liệu (Mặc định: Tất cả loại hình). |
| Nút Thêm Mới | Button | Nút bấm để kích hoạt luồng thêm mới phân loại doanh nghiệp. |
| Bảng loại hình | Table | Khung hiển thị danh sách dạng bảng các loại hình doanh nghiệp. |
| *STT* | Label – Number | Số thứ tự dòng. |
| *Mã loại* | Label – String | Mã băm định danh hệ thống tự sinh (VD: 23e4c334, 64e3c812). |
| *Tên loại* | Label – String | Tên gọi phân loại doanh nghiệp (VD: Lưu trú, Lữ hành, Dịch vụ). |
| *Thao tác* | Icon Buttons | Các biểu tượng Xem, Sửa, Xóa bản ghi danh mục. |
| Tổng số loại hình | Card – Number | Khối thống kê tổng số lượng loại hình kinh doanh đang áp dụng (VD: 3). |
| Tổng số doanh nghiệp | Card – Number | Khối thống kê tổng số doanh nghiệp thuộc mọi loại hình (VD: 23). |
| Thanh phân trang | Pagination | Các nút điều hướng trang (1, 2, 3...) kèm dòng thông tin số lượng (VD: "Hiển thị 1 - 4 của 36 đơn vị"). |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Lọc loại hình** | Lọc nhanh các bản ghi theo nhóm ngành nghề được chọn từ Combobox. | Bảng dữ liệu cập nhật và chỉ hiển thị các dòng tương thích. | Không tìm thấy kết quả, bảng trả về trạng thái trống. |

---

#### b. Hồ sơ doanh nghiệp

<p align="center"><i>Hình 3.13: Giao diện Danh sách Hồ sơ doanh nghiệp</i></p>

| **Màn hình** | **Danh sách Hồ sơ doanh nghiệp** |
| :--- | :--- |
| **Mô tả** | Màn hình quản lý tổng thể thông tin, địa chỉ và trạng thái xét duyệt của toàn bộ các doanh nghiệp du lịch trên địa bàn thành phố Huế. |
| **Màn hình kết nối** | Loại hình doanh nghiệp, Phê duyệt thông tin doanh nghiệp |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Tìm kiếm nhanh | Textfield – String | Ô nhập từ khóa tìm kiếm doanh nghiệp theo Tên hoặc Mã số doanh nghiệp. |
| Bộ lọc Loại hình | Combobox | Lọc danh sách doanh nghiệp theo mảng hoạt động (Tất cả, Lưu trú, Lữ hành...). |
| Nút Thêm Mới | Button | Nút bấm hỗ trợ Admin tạo nhanh một hồ sơ doanh nghiệp mới từ phía quản trị. |
| Bảng hồ sơ doanh nghiệp | Table | Bảng dữ liệu hiển thị thông tin tổng quan của các doanh nghiệp. |
| *STT* | Label – Number | Số thứ tự dòng. |
| *Mã DN* | Label – String | Mã số doanh nghiệp hoặc Mã số thuế của đơn vị (VD: 268935677). |
| *Tên DN* | Label – String | Tên thương mại hoặc tên pháp nhân chính thức (VD: Imperial Huế, Vietravel Huế). |
| *Địa chỉ* | Label – String | Trụ sở hoạt động chính (VD: 54 Hùng Vương, 13 Lê Lợi). |
| *Loại hình* | Label – String | Nhóm loại hình doanh nghiệp tương ứng (VD: Lưu trú, Lữ hành, Dịch vụ). |
| *Trạng Thái* | Badge | Nhãn màu thể hiện tiến trình hồ sơ: Đã duyệt (Xanh), Từ chối (Đỏ), Chưa duyệt (Vàng). |
| *Thao tác* | Icon Buttons | Biểu tượng Xem chi tiết, Phê duyệt nhanh hoặc Xóa hồ sơ. |
| Tổng số loại hình | Card – Number | Khối thống kê tổng số lượng loại hình kinh doanh (VD: 3). |
| Tổng số doanh nghiệp | Card – Number | Khối thống kê tổng số doanh nghiệp trên toàn hệ thống (VD: 23). |
| Điều hướng trang | Pagination | Bộ nút phân trang danh sách dữ liệu. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Tra cứu & Lọc hồ sơ** | Tìm kiếm theo từ khóa kết hợp lọc mảng kinh doanh của doanh nghiệp. | Hệ thống lọc và hiển thị danh sách hồ sơ trùng khớp với điều kiện. | Không tìm thấy bản ghi, bảng hiển thị thông báo trống. |

---

#### c. Duyệt doanh nghiệp

<p align="center"><i>Hình 3.14: Giao diện Phê duyệt thông tin doanh nghiệp</i></p>

| **Màn hình** | **Phê duyệt thông tin doanh nghiệp** |
| :--- | :--- |
| **Mô tả** | Màn hình dành riêng cho vai trò Quản trị viên (QTV) kiểm tra tính hợp pháp của các thông tin, giấy phép do doanh nghiệp tự khai báo và tiến hành ra quyết định phê duyệt. |
| **Màn hình kết nối** | Hồ sơ doanh nghiệp |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Mã doanh nghiệp / MST | Label – String | Mã số thuế doanh nghiệp cần thẩm định. |
| Tên doanh nghiệp | Label – String | Tên đơn vị đăng ký. |
| Loại hình hoạt động | Label – String | Phân loại ngành nghề đăng ký. |
| Giấy phép kinh doanh đính kèm | Link / File Icon | Liên kết mở/tải tệp văn bản pháp lý (PDF hoặc hình ảnh) để QTV đối chiếu. |
| Ảnh minh họa cơ sở | Image Preview | Vùng hiển thị các hình ảnh trực quan về cơ sở vật chất do doanh nghiệp tải lên. |
| Lý do từ chối | Textarea – String | Ô nhập lý do không phê duyệt (Bắt buộc điền nếu QTV chọn hành động Từ chối). |
| Nút Phê duyệt | Button (Success) | Nút bấm đồng ý cấp quyền, chuyển trạng thái doanh nghiệp thành "Đã duyệt". |
| Nút Từ chối | Button (Danger) | Nút bấm bác bỏ hồ sơ, chuyển trạng thái doanh nghiệp thành "Từ chối". |
| Nút Quay lại | Button | Nút thoát giao diện thẩm định và trở về màn hình danh sách hồ sơ. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Phê duyệt hồ sơ** | Kích hoạt khi thông tin hợp lệ. Admin bấm nút Phê duyệt. | Hệ thống lưu trạng thái "Đã duyệt", cấp quyền kinh doanh và gửi thông báo cho DN. | Lỗi kết nối CSDL, hồ sơ giữ nguyên trạng thái cũ. |
| **Từ chối hồ sơ** | Kích hoạt khi thông tin sai lệch. Admin nhập lý do từ chối và bấm nút Từ chối. | Hệ thống lưu trạng thái "Từ chối", ghi nhận lý do và phản hồi về tài khoản DN. | Chưa nhập lý do từ chối, hệ thống cảnh báo yêu cầu bổ sung thông tin. |

---

#### d. Khai báo doanh nghiệp

<p align="center"><i>Hình 3.15: Giao diện Khai báo thông tin doanh nghiệp</i></p>

| **Màn hình** | **Khai báo thông tin doanh nghiệp** |
| :--- | :--- |
| **Mô tả** | Màn hình chính dành cho tác nhân Doanh nghiệp tự kê khai thông tin năng lực, vị trí tọa độ và đính kèm hồ sơ pháp lý gửi lên ban quản trị (tương ứng với chức năng khởi tạo từ phía người dùng ngoài). |
| **Màn hình kết nối** | (Không có) |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Nhập Mã doanh nghiệp / MST | Textfield – String | Trường bắt buộc nhập Mã số thuế để định danh doanh nghiệp. |
| Nhập Tên doanh nghiệp | Textfield – String | Trường nhập tên thương hiệu / tên pháp nhân đầy đủ. |
| Lựa chọn Loại hình | Combobox | Lựa chọn mảng hoạt động chính (Lưu trú, Lữ hành, Dịch vụ...). |
| Số điện thoại liên hệ | Textfield – Number | Số hotline phục vụ giao dịch du lịch. |
| Địa chỉ trụ sở | Textfield – String | Nhập số nhà, tên đường, chọn Phường/Xã thuộc Thành phố Huế. |
| Tọa độ bản đồ | Map Picker / Text | Tọa độ GPS (Latitude, Longitude) xác định vị trí thực tế trên bản đồ số du lịch. |
| Tải lên Giấy phép kinh doanh | Upload Button | Nút tải lên tệp hồ sơ pháp lý chứng minh năng lực hoạt động (Định dạng PDF/JPG). |
| Giới thiệu / Mô tả ngắn | Textarea – String | Đoạn văn bản giới thiệu đặc điểm nổi bật hoặc lịch sử của doanh nghiệp. |
| Nút Gửi phê duyệt | Button (Primary) | Nút thực hiện đóng gói dữ liệu và gửi hồ sơ sang hàng đợi xét duyệt của Admin. |
| Nút Hủy bỏ | Button | Nút xóa sạch các trường thông tin vừa nhập và thiết lập lại từ đầu. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Gửi hồ sơ khai báo** | Đóng gói toàn bộ thông tin kê khai gửi lên hệ thống. | Hệ thống lưu hồ sơ ở trạng thái "Chưa duyệt" và đẩy sang giao diện quản trị của Admin. | Nhập thiếu các trường bắt buộc (MST, Tên, Giấy phép), hệ thống báo đỏ tại trường thiếu dữ liệu. |


