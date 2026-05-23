## 3.4 QUẢN LÝ LƯU TRÚ

| **Tên Use case** | **Quản lý lưu trú** |
| :--- | :--- |
| **Mô tả** | Chuyên viên quản lý nghiệp vụ hoặc doanh nghiệp thực hiện xem danh sách, tìm kiếm, lọc, thêm mới, cập nhật thông tin, xóa và phê duyệt thông tin các cơ sở lưu trú du lịch trên địa bàn tỉnh/thành phố. |
| **Tác nhân** | Chuyên viên quản lý nghiệp vụ, Doanh nghiệp lưu trú |
| **Độ phức tạp** | 🔲 Đơn giản  🔲 Trung bình  ☑️ Phức tạp |
| **Điều kiện bắt đầu** | Người dùng có thẩm quyền đã đăng nhập thành công vào phân hệ quản trị hệ thống CSDL Du lịch Huế. |
| **Điều kiện kết thúc** | Hệ thống cập nhật trạng thái hoặc dữ liệu thành công. |

### a. Danh sách cơ sở lưu trú

*Hình 3.4.1: Giao diện Danh sách cơ sở lưu trú*

| **Màn hình** | **Danh sách cơ sở lưu trú** |
| :--- | :--- |
| **Mô tả** | Màn hình hiển thị danh sách tất cả các cơ sở lưu trú, cho phép người dùng tìm kiếm, lọc theo loại hình, địa bàn, trạng thái và thực hiện các thao tác quản lý. |
| **Màn hình kết nối** | Xem chi tiết, Thêm mới, Sửa, Xóa, Phê duyệt, Từ chối phê duyệt cơ sở lưu trú |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Ô tìm kiếm | Textfield – String | Nhập tên cơ sở lưu trú hoặc mã cơ sở để tìm kiếm. |
| Lọc loại hình | Combobox | Lựa chọn loại hình (Khách sạn, Resort, Homestay...). |
| Lọc địa bàn | Combobox | Lựa chọn cấp Phường/Xã/Quận/Huyện. |
| Lọc trạng thái | Combobox | Lựa chọn trạng thái (Hoạt động, Đang chờ duyệt, Bị từ chối...). |
| Nút Thêm mới | Button | Click để mở màn hình Thêm cơ sở lưu trú. |
| Bảng dữ liệu | Table | Hiển thị danh sách các cơ sở lưu trú. |
| *STT* | Label – Number | Số thứ tự dòng. |
| *Tên cơ sở* | Link | Tên cơ sở lưu trú (Click vào sẽ chuyển sang màn hình Xem chi tiết). |
| *Loại hình* | Label – String | Tên loại hình lưu trú. |
| *Địa chỉ* | Label – String | Vị trí, số nhà, đường của cơ sở lưu trú. |
| *Trạng thái* | Badge | Nhãn màu sắc thể hiện trạng thái hiện tại. |
| *Thao tác* | Icon Buttons | Các nút chức năng: Sửa, Xóa, Duyệt (đối với QTV). |
| Phân trang | Pagination | Điều hướng giữa các trang danh sách. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Lọc và tìm kiếm** | Lọc dữ liệu theo các tiêu chí đã chọn. | Bảng dữ liệu cập nhật hiển thị kết quả chính xác. | Không tìm thấy kết quả, bảng trống kèm thông báo. |
| **Điều hướng** | Nhấn vào các nút chức năng để chuyển trang. | Chuyển đến giao diện tương ứng (Thêm/Sửa/Chi tiết). | (Không có) |

---

### b. Xem chi tiết cơ sở lưu trú

*Hình 3.4.2: Giao diện Xem chi tiết cơ sở lưu trú*

| **Màn hình** | **Xem chi tiết cơ sở lưu trú** |
| :--- | :--- |
| **Mô tả** | Màn hình hiển thị đầy đủ thông tin chi tiết về một cơ sở lưu trú, bao gồm hình ảnh, tiện ích, mô tả và vị trí trên bản đồ. |
| **Màn hình kết nối** | Danh sách cơ sở lưu trú |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Tiêu đề trang | Label – String | Hiển thị Tên cơ sở lưu trú cỡ lớn. |
| Ảnh đại diện / Album | Image Slider | Trình chiếu các hình ảnh thực tế của cơ sở lưu trú. |
| Tên doanh nghiệp chủ quản | Label – String | Tên doanh nghiệp đăng ký và quản lý cơ sở. |
| Loại hình lưu trú | Label – String | Phân loại (Ví dụ: Khách sạn 5 sao). |
| Địa chỉ | Label – String | Thông tin địa chỉ chi tiết. |
| Số điện thoại | Label – String | Hotline liên hệ đặt phòng. |
| Mô tả chi tiết | Text / HTML | Đoạn văn bản giới thiệu về dịch vụ, không gian của cơ sở. |
| Bản đồ vị trí | Map View | Khung bản đồ mini có ghim vị trí của cơ sở lưu trú. |
| Danh sách tiện ích | Tag / Badge List | Các tiện ích nổi bật (Wifi, Hồ bơi, Bãi đỗ xe...). |
| Trạng thái | Badge | Trạng thái hoạt động hoặc trạng thái phê duyệt hồ sơ. |
| Nút Quay lại | Button | Quay về danh sách cơ sở lưu trú. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Xem thông tin** | Hệ thống tự động load thông tin khi vào trang. | Hiển thị đầy đủ text và hình ảnh. | Lỗi mạng, không tải được ảnh hoặc bản đồ. |

---

### c. Thêm cơ sở lưu trú

*Hình 3.4.3: Giao diện Thêm cơ sở lưu trú*

| **Màn hình** | **Thêm cơ sở lưu trú** |
| :--- | :--- |
| **Mô tả** | Biểu mẫu cho phép nhập dữ liệu khai báo một cơ sở lưu trú mới trên hệ thống. |
| **Màn hình kết nối** | Danh sách cơ sở lưu trú |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Tên cơ sở lưu trú | Textfield – String | Nhập tên chính thức của cơ sở (Bắt buộc). |
| Loại hình | Combobox | Chọn danh mục loại hình (Bắt buộc). |
| Doanh nghiệp | Combobox | Chọn doanh nghiệp chủ quản (Bắt buộc). |
| Địa bàn | Combobox | Chọn Xã/Phường/Quận/Huyện (Bắt buộc). |
| Địa chỉ chi tiết | Textfield – String | Nhập số nhà, tên đường. |
| Hạng sao | Combobox | Đánh giá hạng sao (Từ 1-5 sao hoặc Không xếp hạng). |
| Mô tả | Textarea | Giới thiệu thông tin cơ sở vật chất. |
| Chọn tiện ích | Checkbox List | Tick chọn các tiện ích đi kèm (Wifi, Nhà hàng...). |
| Vị trí tọa độ | Map Picker / Text | Click trên bản đồ để tự điền tọa độ hoặc nhập tay. |
| Tải ảnh lên | File Upload | Chọn và tải các hình ảnh/logo của cơ sở. |
| Nút Lưu lại | Button (Primary) | Nhấn để gửi dữ liệu khai báo lên hệ thống. |
| Nút Hủy bỏ | Button (Secondary) | Hủy thao tác, quay về màn hình trước. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Lưu dữ liệu** | Ghi nhận thông tin cơ sở lưu trú mới. | Hiển thị popup "Thêm mới thành công" và chuyển về danh sách. | Báo lỗi viền đỏ tại các trường bị bỏ trống hoặc sai định dạng. |

---

### d. Sửa cơ sở lưu trú

*Hình 3.4.4: Giao diện Sửa cơ sở lưu trú*

| **Màn hình** | **Sửa cơ sở lưu trú** |
| :--- | :--- |
| **Mô tả** | Biểu mẫu cho phép cập nhật, thay đổi các thông tin đã khai báo của cơ sở lưu trú. Hệ thống sẽ điền sẵn dữ liệu cũ vào các trường. |
| **Màn hình kết nối** | Danh sách cơ sở lưu trú |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Các trường thông tin nhập liệu | Textfield / Combobox / Checkbox | Tương tự màn hình Thêm mới, nhưng hiển thị sẵn dữ liệu hiện tại của cơ sở lưu trú. |
| Quản lý hình ảnh | Image Grid + Delete Icon | Hiển thị các ảnh đã tải lên, cho phép bấm xóa ảnh cũ và tải thêm ảnh mới. |
| Nút Cập nhật | Button (Primary) | Lưu lại các thay đổi vào hệ thống. |
| Nút Hủy | Button (Secondary) | Bỏ qua các thay đổi. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Cập nhật** | Ghi đè các thông tin chỉnh sửa. | Báo "Cập nhật thành công", lưu vào CSDL và quay lại trang danh sách. | Lỗi xác thực dữ liệu nếu xóa rỗng trường bắt buộc. |

---

### e. Xóa cơ sở lưu trú

*Hình 3.4.5: Giao diện Xóa cơ sở lưu trú (Popup)*

| **Màn hình** | **Xóa cơ sở lưu trú (Popup Xác nhận)** |
| :--- | :--- |
| **Mô tả** | Hộp thoại cảnh báo hiển thị khi người dùng nhấn nút Xóa, nhằm yêu cầu xác nhận trước khi thực hiện. |
| **Màn hình kết nối** | Danh sách cơ sở lưu trú |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Tiêu đề cảnh báo | Label – String | "Xác nhận xóa cơ sở lưu trú". |
| Nội dung thông báo | Label – String | "Bạn có chắc chắn muốn xóa cơ sở lưu trú [Tên cơ sở] không? Hành động này không thể hoàn tác." |
| Nút Xác nhận | Button (Danger) | Nút màu đỏ để thực thi lệnh xóa. |
| Nút Hủy | Button (Secondary) | Đóng popup, không làm gì cả. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Thực hiện xóa** | Gỡ bỏ bản ghi khỏi danh sách quản lý. | Thông báo xóa thành công, reload lại bảng danh sách. | Nếu có dữ liệu ràng buộc (đang có tour, phản hồi), hệ thống sẽ báo lỗi không thể xóa và gợi ý chuyển trạng thái "Ngừng hoạt động". |

---

### f. Phê duyệt cơ sở lưu trú

*Hình 3.4.6: Giao diện Phê duyệt cơ sở lưu trú*

| **Màn hình** | **Phê duyệt cơ sở lưu trú** |
| :--- | :--- |
| **Mô tả** | Màn hình dành cho Quản trị viên/Chuyên viên xem xét thông tin hồ sơ khai báo của doanh nghiệp trước khi cho phép hiển thị công khai. |
| **Màn hình kết nối** | Danh sách cơ sở lưu trú |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Toàn bộ thông tin cơ sở | Lable - String / Image | Hiển thị dạng View (chỉ đọc) giống hệt màn hình Xem chi tiết. |
| Giấy tờ đính kèm | Link / File Icon | Xem các hồ sơ, giấy phép kinh doanh đính kèm để đối chiếu. |
| Nút Phê duyệt | Button (Success) | Nhấn để cấp quyền hoạt động. |
| Nút Từ chối | Button (Danger) | Nhấn để chuyển sang popup nhập lý do từ chối. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Duyệt hồ sơ** | Đổi trạng thái sang "Đã duyệt/Hoạt động". | Thông báo duyệt thành công, gửi email thông báo cho doanh nghiệp. | (Không có) |

---

### g. Từ chối phê duyệt cơ sở lưu trú

*Hình 3.4.7: Giao diện Từ chối phê duyệt (Popup)*

| **Màn hình** | **Từ chối phê duyệt cơ sở lưu trú (Popup)** |
| :--- | :--- |
| **Mô tả** | Hộp thoại yêu cầu Quản trị viên nhập lý do giải thích vì sao hồ sơ khai báo của doanh nghiệp không đạt yêu cầu. |
| **Màn hình kết nối** | Màn hình Phê duyệt cơ sở lưu trú |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Tiêu đề | Label – String | "Từ chối phê duyệt hồ sơ". |
| Ô nhập lý do | Textarea – String | Khu vực để QTV nhập chi tiết lý do từ chối (Bắt buộc). |
| Nút Gửi từ chối | Button (Primary) | Xác nhận hành động từ chối và lưu lý do. |
| Nút Hủy | Button (Secondary) | Tắt popup. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Xác nhận từ chối** | Chuyển trạng thái sang "Từ chối" và gửi phản hồi. | Hồ sơ bị trả lại, doanh nghiệp nhận được thông báo kèm lý do. | Không nhập lý do, hệ thống báo lỗi viền đỏ tại Textarea. |

---

## 3.5 QUẢN LÝ LỮ HÀNH VÀ HƯỚNG DẪN VIÊN

### 3.5.1 Đơn vị lữ hành

#### a. Danh sách đơn vị lữ hành

*Hình 3.5.1: Giao diện Danh sách đơn vị lữ hành*

| **Màn hình** | **Danh sách đơn vị lữ hành** |
| :--- | :--- |
| **Mô tả** | Màn hình danh sách theo dõi và quản lý thông tin các công ty/đơn vị hoạt động kinh doanh lữ hành. |
| **Màn hình kết nối** | Xem chi tiết, Thêm, Sửa, Xóa đơn vị lữ hành |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Ô tìm kiếm | Textfield | Nhập tên công ty lữ hành. |
| Lọc địa bàn | Combobox | Lọc theo Phường/Xã/Quận/Huyện. |
| Bảng dữ liệu | Table | Danh sách các đơn vị lữ hành. |
| *Tên công ty lữ hành* | Link | Click để vào xem chi tiết đơn vị. |
| *Số điện thoại* | Label – String | Số hotline giao dịch. |
| *Thao tác* | Icon Buttons | Sửa, Xóa. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Tra cứu** | Tìm thông tin theo các điều kiện lọc. | Bảng dữ liệu cập nhật danh sách phù hợp. | Không tìm thấy kết quả. |

#### b. Xem chi tiết đơn vị lữ hành

*Hình 3.5.2: Giao diện Xem chi tiết đơn vị lữ hành*

| **Màn hình** | **Xem chi tiết đơn vị lữ hành** |
| :--- | :--- |
| **Mô tả** | Giao diện hiển thị các thông tin giới thiệu, địa chỉ liên hệ và danh sách các tour do đơn vị này tổ chức. |
| **Màn hình kết nối** | Danh sách đơn vị lữ hành |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Tên công ty lữ hành | Label – String | Hiển thị tên đầy đủ công ty. |
| Doanh nghiệp chủ quản | Label – String | Pháp nhân đại diện. |
| Giới thiệu chung | Text | Thông tin mô tả, năng lực lữ hành. |
| Địa chỉ văn phòng | Label – String | Nơi đặt trụ sở hoạt động. |
| Danh sách tour cung cấp | Bảng phụ (Sub-table) | Bảng nhỏ hiển thị các tour mà đơn vị này đang tổ chức mở bán. |
| Danh sách Hướng dẫn viên | Bảng phụ (Sub-table) | Danh sách các HDV trực thuộc đơn vị lữ hành này. |
| Nút Quay lại | Button | Trở về trang trước. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Xem chi tiết** | Load dữ liệu text, bảng phụ. | Hiển thị trực quan dữ liệu. | (Không có) |

---

### 3.5.2 Hướng dẫn viên

#### a. Danh sách hướng dẫn viên

*Hình 3.5.3: Giao diện Danh sách hướng dẫn viên*

| **Màn hình** | **Danh sách hướng dẫn viên** |
| :--- | :--- |
| **Mô tả** | Quản lý danh sách các hướng dẫn viên du lịch trên địa bàn kèm theo số thẻ và phân loại ngôn ngữ. |
| **Màn hình kết nối** | Xem chi tiết HDV |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Ô tìm kiếm | Textfield | Tìm theo tên HDV hoặc Số thẻ HDV. |
| Lọc ngôn ngữ | Combobox | Lọc theo: Tiếng Anh, Tiếng Pháp, Tiếng Trung... |
| Lọc theo Đơn vị lữ hành| Combobox | Lọc HDV thuộc một công ty cụ thể hoặc HDV tự do. |
| Bảng dữ liệu | Table | Hiển thị thông tin HDV. |
| *Họ và tên* | Link | Tên HDV, bấm để xem chi tiết. |
| *Số thẻ hành nghề* | Label – String | Mã số thẻ của HDV. |
| *Ngôn ngữ* | Tag | Các ngôn ngữ HDV thành thạo. |
| *Công ty chủ quản* | Label – String | Tên công ty quản lý HDV này. |
| *Thao tác* | Icon Buttons | Sửa, Xóa. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Lọc và phân trang** | Tra cứu danh sách HDV. | Hệ thống trả về bảng danh sách chính xác. | Không tìm thấy. |

#### b. Xem chi tiết hướng dẫn viên

*Hình 3.5.4: Giao diện Xem chi tiết hướng dẫn viên*

| **Màn hình** | **Xem chi tiết hướng dẫn viên** |
| :--- | :--- |
| **Mô tả** | Giao diện hiển thị hồ sơ cá nhân, thông tin liên lạc và thẻ hành nghề của HDV. |
| **Màn hình kết nối** | Danh sách hướng dẫn viên |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Ảnh chân dung HDV | Image | Hình ảnh đại diện cá nhân của HDV. |
| Họ và tên | Label – String | Tên đầy đủ. |
| Số thẻ hành nghề | Label – String | Thông tin số thẻ. |
| Ngôn ngữ chuyên môn | Tag List | Danh sách ngôn ngữ có thể hướng dẫn. |
| Liên hệ | Label – String | SĐT và Email. |
| Ảnh thẻ HDV 2 mặt | Image Viewer | Hình chụp thẻ hành nghề chứng minh tính hợp lệ. |
| Lịch sử dẫn tour | Bảng phụ | Hiển thị các tour HDV này đã và đang được phân công phụ trách. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Xem hồ sơ** | Hiển thị dữ liệu chi tiết HDV. | Tải đầy đủ hình ảnh và thông tin bảng lịch sử. | (Không có) |

---

### 3.5.3 Tour du lịch

#### a. Danh sách tour du lịch

*Hình 3.5.5: Giao diện Danh sách tour du lịch*

| **Màn hình** | **Danh sách tour du lịch** |
| :--- | :--- |
| **Mô tả** | Quản lý danh sách các gói chương trình tour du lịch đang được cung cấp trên hệ thống. |
| **Màn hình kết nối** | Xem chi tiết Tour |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Bộ lọc tìm kiếm | Textfield | Tìm kiếm tên chương trình tour. |
| Lọc Đơn vị lữ hành | Combobox | Lọc theo công ty tổ chức. |
| Lọc Trạng thái duyệt | Combobox | Đã cấp phép / Chờ duyệt. |
| Bảng dữ liệu | Table | Hiển thị danh sách các tour. |
| *Tên tour du lịch* | Link | Tên gói tour, nhấn để xem. |
| *Thời lượng* | Label – String | Ví dụ: "1 ngày", "2 ngày 1 đêm". |
| *Giá tour* | Label – String | Mức giá niêm yết. |
| *Đơn vị tổ chức* | Label – String | Tên công ty lữ hành. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Xem danh sách** | Truy vấn bảng danh sách tour. | Bảng hiển thị thông tin rõ ràng. | (Không có) |

#### b. Xem chi tiết tour du lịch

*Hình 3.5.6: Giao diện Xem chi tiết tour du lịch*

| **Màn hình** | **Xem chi tiết tour du lịch** |
| :--- | :--- |
| **Mô tả** | Hiển thị lịch trình chi tiết, giá cả và thông tin liên quan đến việc tổ chức tour. |
| **Màn hình kết nối** | Danh sách tour du lịch |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Tên chương trình tour | Label – String | Tiêu đề tour nổi bật. |
| Đơn vị tổ chức | Link | Tên đơn vị lữ hành. |
| Mức giá | Label – String | Giá bán (VNĐ). |
| Thời lượng | Label – String | Tổng thời gian tour. |
| Lịch trình chi tiết | HTML / Text Block | Đoạn văn bản thuyết minh các mốc thời gian, điểm đến, hoạt động trải nghiệm. |
| Danh sách HDV phân công | Bảng phụ | Hiển thị tên các HDV được gán cho tour này kèm lịch trình ngày đi. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Hiển thị thông tin** | Kết xuất dữ liệu lịch trình và HDV liên quan. | Hiển thị đầy đủ thông tin cho Quản trị viên/Du khách xem. | (Không có) |

---

## 3.6 QUẢN LÝ ĂN UỐNG & MUA SẮM

### a. Danh sách quán ăn và mua sắm

*Hình 3.6.1: Giao diện Danh sách quán ăn và mua sắm*

| **Màn hình** | **Danh sách quán ăn và mua sắm** |
| :--- | :--- |
| **Mô tả** | Màn hình hiển thị danh sách các nhà hàng, quán ăn, đặc sản, và trung tâm thương mại/mua sắm. |
| **Màn hình kết nối** | Xem chi tiết cơ sở |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Tìm kiếm | Textfield | Nhập tên quán ăn/điểm mua sắm. |
| Lọc Dịch vụ | Combobox | Lọc loại hình: Nhà hàng, Quán ăn, Siêu thị, Cửa hàng đặc sản... |
| Bảng dữ liệu | Table | Danh sách các cơ sở dịch vụ. |
| *Tên cơ sở* | Link | Tên dịch vụ, click để mở xem chi tiết. |
| *Loại dịch vụ* | Label – String | Phân loại tương ứng. |
| *Địa chỉ* | Label – String | Khu vực, đường, số nhà. |
| *Trạng thái* | Badge | Đang hoạt động / Ẩn. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Tra cứu cơ sở** | Lọc dữ liệu theo tên và loại hình. | Danh sách kết xuất chính xác. | Không tìm thấy bản ghi. |

### b. Xem chi tiết quán ăn và mua sắm

*Hình 3.6.2: Giao diện Xem chi tiết quán ăn và mua sắm*

| **Màn hình** | **Xem chi tiết quán ăn và mua sắm** |
| :--- | :--- |
| **Mô tả** | Màn hình trình bày thông tin, không gian, thực đơn/đặc sản của cơ sở kinh doanh dịch vụ ăn uống, mua sắm. |
| **Màn hình kết nối** | Danh sách quán ăn và mua sắm |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Tên cơ sở dịch vụ | Label – String | Tiêu đề tên quán/nhà hàng. |
| Thư viện ảnh | Image Slider | Các ảnh chụp không gian, món ăn, mặt hàng lưu niệm. |
| Địa chỉ & Tọa độ | Label + Map | Địa chỉ text và bản đồ mini ghim vị trí quán. |
| Giờ mở cửa | Label – String | Khung giờ hoạt động. |
| Mô tả / Thực đơn | Text / HTML | Giới thiệu các món đặc sản, mặt hàng kinh doanh chính. |
| Tiện ích đi kèm | Tag List | Có phòng VIP, máy lạnh, bãi đỗ xe ô tô, thanh toán thẻ... |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Xem chi tiết** | Load thông tin và media của quán. | Hiển thị hình ảnh và thông tin mượt mà. | Lỗi đường truyền ảnh. |

---

## 3.7 QUẢN LÝ ĐIỂM ĐẾN

### a. Danh sách điểm đến

*Hình 3.7.1: Giao diện Danh sách điểm đến*

| **Màn hình** | **Danh sách điểm đến** |
| :--- | :--- |
| **Mô tả** | Quản lý kho dữ liệu tài nguyên du lịch: Di tích lịch sử, danh lam thắng cảnh, làng nghề, khu vui chơi... |
| **Màn hình kết nối** | Xem chi tiết điểm đến |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Ô tìm kiếm | Textfield | Tìm kiếm tên điểm đến (VD: Đại Nội, Lăng Khải Định). |
| Lọc loại hình | Combobox | Lọc theo: Di tích, Thắng cảnh, Làng nghề, Điểm tâm linh. |
| Bảng dữ liệu | Table | Cột: STT, Tên điểm đến, Loại hình, Địa bàn, Trạng thái số hóa. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Lọc dữ liệu** | Tìm tài nguyên điểm đến theo phân loại. | Trả về danh sách chuẩn xác. | Bảng rỗng nếu không khớp. |

### b. Xem chi tiết điểm đến

*Hình 3.7.2: Giao diện Xem chi tiết điểm đến*

| **Màn hình** | **Xem chi tiết điểm đến** |
| :--- | :--- |
| **Mô tả** | Cung cấp bài viết thuyết minh chi tiết, hình ảnh độ phân giải cao và thông tin tham quan của điểm đến. |
| **Màn hình kết nối** | Danh sách điểm đến |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Tên điểm đến | Label – String | Tên khu di tích / thắng cảnh. |
| Media / Hình ảnh | Image/Video | Trình chiếu hình ảnh phong cảnh, video giới thiệu 360 độ. |
| Bài viết thuyết minh | Text Block | Nội dung diễn giải về lịch sử hình thành, kiến trúc, giá trị văn hóa. |
| Thông tin vé / Mở cửa | Text | Giá vé tham quan (nếu có), giờ mở/đóng cửa. |
| Vị trí GPS | Map | Định vị trên bản đồ để hỗ trợ chỉ đường cho du khách. |
| Tiện ích điểm đến | Badge List | Thuyết minh Audio Guide, xe điện, lối đi cho người khuyết tật. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Trải nghiệm thông tin** | Xem hình ảnh và đọc bài thuyết minh điểm đến. | Trình bày đẹp mắt, hỗ trợ hiển thị Multimedia tốt. | Lỗi tải video/ảnh nặng. |

---

## 3.8 QUẢN LÝ LỄ HỘI VÀ SỰ KIỆN

### a. Danh sách lễ hội và sự kiện

*Hình 3.8.1: Giao diện Danh sách lễ hội và sự kiện*

| **Màn hình** | **Danh sách lễ hội và sự kiện** |
| :--- | :--- |
| **Mô tả** | Màn hình quản lý các hoạt động lễ hội văn hóa, Festival, sự kiện thể thao diễn ra trên địa bàn. |
| **Màn hình kết nối** | Xem chi tiết sự kiện |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Tìm kiếm | Textfield | Tên lễ hội, sự kiện. |
| Lọc thời gian | Date Range | Lọc các sự kiện theo khoảng thời gian "Từ ngày - Đến ngày". |
| Lọc trạng thái | Combobox | Sắp diễn ra / Đang diễn ra / Đã kết thúc. |
| Bảng dữ liệu | Table | Cột: Tên sự kiện, Địa điểm, Thời gian bắt đầu - kết thúc, Trạng thái. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Theo dõi sự kiện** | Tra cứu danh sách lịch trình lễ hội. | Cập nhật đúng các sự kiện trong khoảng thời gian đã chọn. | (Không có) |

### b. Xem chi tiết lễ hội và sự kiện

*Hình 3.8.2: Giao diện Xem chi tiết lễ hội và sự kiện*

| **Màn hình** | **Xem chi tiết sự kiện** |
| :--- | :--- |
| **Mô tả** | Màn hình thông báo thông tin chi tiết về chương trình sự kiện, ban tổ chức và sơ đồ địa điểm. |
| **Màn hình kết nối** | Danh sách sự kiện |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Tên Lễ hội / Sự kiện | Label – String | Ví dụ: "Festival Nghề truyền thống Huế". |
| Banner / Poster | Image | Ảnh quảng bá chính thức của sự kiện. |
| Thời gian diễn ra | Label – String | Khung thời gian Khai mạc và Bế mạc. |
| Địa điểm | Label / Map | Vị trí quảng trường, công viên tổ chức sự kiện. |
| Nội dung chương trình | Text | Diễn giải các hoạt động chính trong khuôn khổ sự kiện. |
| Tình trạng | Badge | Nhãn "Sắp diễn ra", "Đang diễn ra" để thu hút sự chú ý. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Xem chi tiết sự kiện** | Cung cấp thông tin lịch trình cho QTV và du khách. | Hiển thị rành mạch thời gian và địa điểm. | (Không có) |

---

## 3.9 QUẢN LÝ PHẢN HỒI

### 3.9.1 Quản lý phản hồi quản trị viên

*Hình 3.9.1: Giao diện Quản lý phản hồi (Dành cho QTV)*

| **Màn hình** | **Quản lý phản hồi (Admin)** |
| :--- | :--- |
| **Mô tả** | Quản trị viên theo dõi toàn bộ đánh giá của du khách đối với các điểm đến, dịch vụ, tiến hành kiểm duyệt nội dung (ẩn các bình luận thô tục, spam). |
| **Màn hình kết nối** | (Không có) |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Lọc số sao | Combobox | Lọc nhanh các đánh giá 1 sao, 2 sao để xử lý. |
| Lọc trạng thái | Combobox | Chưa duyệt / Đã duyệt / Bị ẩn. |
| Bảng danh sách phản hồi | Table | Danh sách các bình luận đánh giá. |
| *Tên du khách* | Label – String | Tên hoặc tài khoản của người gửi đánh giá. |
| *Nội dung* | Text | Chi tiết dòng bình luận, góp ý. |
| *Số sao* | Icon (Stars) | Thể hiện mức độ hài lòng (1 đến 5 sao). |
| *Thời gian* | Label – String | Ngày giờ đăng bình luận. |
| *Thao tác Duyệt/Ẩn* | Switch / Buttons | Nút gạt chuyển trạng thái cho phép hiển thị công khai hoặc ẩn đi. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Kiểm duyệt bình luận** | QTV bấm nút Duyệt hoặc Ẩn đối với một phản hồi. | Hệ thống cập nhật trạng thái hiển thị của bình luận trên nền tảng di động của du khách. | Lỗi mạng, trạng thái duyệt không được cập nhật. |

### 3.9.2 Quản lý phản hồi doanh nghiệp

*Hình 3.9.2: Giao diện Quản lý phản hồi (Dành cho Doanh nghiệp)*

| **Màn hình** | **Phản hồi của khách hàng (Doanh nghiệp)** |
| :--- | :--- |
| **Mô tả** | Giao diện dành riêng cho tài khoản Doanh nghiệp để xem các đánh giá về cơ sở lưu trú, nhà hàng của mình và có quyền nhập câu trả lời giải trình lại du khách. |
| **Màn hình kết nối** | (Không có) |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Bảng danh sách phản hồi | Table | Chỉ hiển thị các đánh giá thuộc về cơ sở của doanh nghiệp này. |
| Chi tiết đánh giá | Card View | Dạng khung thẻ hiển thị Nội dung khách viết và Số sao. |
| Ô nhập câu trả lời | Textfield / Textarea | Khu vực cho doanh nghiệp soạn nội dung phản hồi, xin lỗi hoặc cảm ơn du khách. |
| Nút Gửi phản hồi | Button | Nhấn để đăng câu trả lời. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Trả lời đánh giá** | Doanh nghiệp tương tác với bình luận của khách. | Nội dung trả lời được ghim bên dưới bình luận của du khách. | Không nhập nội dung mà bấm Gửi (báo lỗi). |

---

## 3.10 TÌM KIẾM THÔNG TIN DU LỊCH

*Hình 3.10.1: Giao diện Tìm kiếm tổng hợp toàn hệ thống*

| **Màn hình** | **Tìm kiếm thông tin du lịch (Global Search)** |
| :--- | :--- |
| **Mô tả** | Tính năng tìm kiếm thông minh đa tiêu chí (Full-text search), trả về kết quả trộn lẫn từ các module Điểm đến, Lưu trú, Lữ hành, Sự kiện. |
| **Màn hình kết nối** | Liên kết trực tiếp vào các màn hình Xem chi tiết của đối tượng. |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Thanh tìm kiếm lớn | Textfield | Ô nhập liệu trung tâm, có text gợi ý (Placeholder). Kèm biểu tượng kính lúp. |
| Tab phân loại nhanh | Button Group | Các nút tab: Tất cả, Lưu trú, Ăn uống, Điểm đến, Sự kiện. |
| Lọc theo khoảng cách | Dropdown / Slider | Bộ lọc định vị (Tính bằng Km) từ vị trí hiện tại của thiết bị (Đòi hỏi quyền GPS). |
| Danh sách kết quả | Card Grid/List | Các ô kết quả hiển thị dạng thẻ (Có ảnh thumbnail, tên, số sao, khoảng cách). |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Tìm kiếm thông minh** | Gõ từ khóa không dấu hoặc có dấu (VD: "Bun bo", "Khach san"). | Giao diện tự động xổ ra danh sách gợi ý hoặc load các thẻ kết quả trùng khớp nhất. | Không có kết quả, hiển thị hình ảnh "Không tìm thấy dữ liệu". |

---

## 3.11 QUẢN LÝ API

*Hình 3.11.1: Giao diện Quản lý cấu hình API hệ thống*

| **Màn hình** | **Quản lý cấu hình API** |
| :--- | :--- |
| **Mô tả** | Màn hình dành cho quản trị viên kỹ thuật thiết lập và theo dõi tình trạng kết nối của các dịch vụ bên thứ ba (VNeID, Google Map, Thời tiết...). |
| **Màn hình kết nối** | Popup chỉnh sửa API |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Danh sách API | Table | Hiển thị danh sách các dịch vụ đang được tích hợp. |
| *Tên dịch vụ* | Label – String | Ví dụ: VNeID Authentication, Map Navigation. |
| *Đường dẫn (Base URL)* | Label – String | Endpoint API kết nối tới máy chủ đối tác. |
| *API Key / Token* | Password Text | Chuỗi khóa bí mật (Bị che dấu ***, có nút con mắt để xem). |
| *Trạng thái* | Toggle Switch | Nút gạt bật/tắt (Kết nối / Dừng kết nối). |
| *Kiểm tra (Ping)* | Button | Nút bấm để gửi lệnh test đường truyền ngay lập tức. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Kiểm tra kết nối API** | Nhấn nút Ping để hệ thống gọi thử API. | Trả về thông báo "Kết nối API ổn định (Status 200)". | Thông báo lỗi "Mất kết nối hoặc Sai API Key (Status 401/500)". |

---

## 3.12 BÁO CÁO THỐNG KÊ

*Hình 3.12.1: Giao diện Báo cáo thống kê Dashboard*

| **Màn hình** | **Báo cáo thống kê** |
| :--- | :--- |
| **Mô tả** | Giao diện tổng hợp số liệu dạng biểu đồ (Dashboard) giúp lãnh đạo nắm bắt số lượng doanh nghiệp, cơ sở lưu trú và đánh giá của khách hàng. |
| **Màn hình kết nối** | (Không có) |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Bộ lọc thời gian | Date Picker | Chọn mốc thời gian: Theo tuần, tháng, quý, năm, hoặc "Từ ngày... Đến ngày...". |
| Nút Xuất báo cáo | Button | Nút tải xuống dữ liệu (Export). |
| Thẻ số liệu tổng quan | Scorecard | Các ô số nổi bật: Tổng số doanh nghiệp, Số tour đang mở, Lượt đánh giá. |
| Biểu đồ cơ sở lưu trú | Bar Chart | Biểu đồ cột thể hiện phân bố cơ sở lưu trú theo từng Quận/Huyện. |
| Biểu đồ loại hình điểm đến| Pie Chart | Biểu đồ tròn thể hiện tỷ trọng giữa Di tích, Thắng cảnh, Làng nghề... |
| Bảng top đánh giá | Bảng xếp hạng (Table) | Hiển thị top 5 dịch vụ/điểm đến có điểm đánh giá sao cao nhất. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Hiển thị biểu đồ** | Tự động kết xuất đồ thị khi chọn mốc thời gian. | Các biểu đồ vẽ dữ liệu trực quan, chính xác. | Không có dữ liệu trong khoảng thời gian chọn (Biểu đồ rỗng). |
| **Xuất file (Export)** | Bấm nút xuất báo cáo ra định dạng khác. | Trình duyệt tải xuống file PDF hoặc Excel chứa số liệu hiện tại. | Lỗi tạo file, báo lỗi hệ thống. |
