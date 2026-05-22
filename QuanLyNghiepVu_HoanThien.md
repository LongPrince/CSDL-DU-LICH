# 3. THIẾT KẾ CHI TIẾT CÁC CHỨC NĂNG (TIẾP THEO)

## 3.4 QUẢN LÝ LƯU TRÚ

| **Tên Use case** | **Quản lý lưu trú** |
| :--- | :--- |
| **Mô tả** | Chuyên viên quản lý nghiệp vụ hoặc doanh nghiệp thực hiện xem danh sách, tìm kiếm, lọc, thêm mới, cập nhật thông tin, xóa và phê duyệt thông tin các cơ sở lưu trú du lịch trên địa bàn tỉnh/thành phố. |
| **Tác nhân** | Chuyên viên quản lý nghiệp vụ, Doanh nghiệp lưu trú |
| **Độ phức tạp** | 🔲 Đơn giản  🔲 Trung bình  ☑️ Phức tạp |
| **Điều kiện bắt đầu** | Người dùng có thẩm quyền đã đăng nhập thành công vào phân hệ quản trị hệ thống CSDL Du lịch Huế. |
| **Điều kiện kết thúc** | Hệ thống cập nhật trạng thái hoặc dữ liệu lưu trú thành công. |

### a. Danh sách cơ sở lưu trú

<p align="center"><i>Hình 3.1: Giao diện Danh sách cơ sở lưu trú</i></p>

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
| *Thao tác* | Icon Buttons | Các nút chức năng: Xem, Sửa, Xóa, Phê duyệt (đối với QTV). |
| Phân trang | Pagination | Điều hướng giữa các trang danh sách. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Lọc và tìm kiếm** | Lọc dữ liệu theo các tiêu chí đã chọn. | Bảng dữ liệu cập nhật hiển thị kết quả chính xác. | Không tìm thấy kết quả, bảng trống kèm thông báo. |
| **Điều hướng** | Nhấn vào các nút chức năng để chuyển trang. | Chuyển đến giao diện tương ứng (Thêm/Sửa/Chi tiết). | (Không có) |

---

### b. Xem chi tiết cơ sở lưu trú

<p align="center"><i>Hình 3.2: Giao diện Xem chi tiết cơ sở lưu trú</i></p>

| **Màn hình** | **Xem chi tiết cơ sở lưu trú** |
| :--- | :--- |
| **Mô tả** | Màn hình hiển thị đầy đủ thông tin chi tiết về một cơ sở lưu trú, bao gồm hình ảnh, tiện ích, mô tả và vị trí trên bản đồ. Không cho phép sửa đổi dữ liệu tại đây. |
| **Màn hình kết nối** | Danh sách cơ sở lưu trú |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Tiêu đề trang | Label – String | Hiển thị Tên cơ sở lưu trú cỡ lớn. |
| Ảnh đại diện / Album | Image Slider | Trình chiếu các hình ảnh thực tế của cơ sở lưu trú. |
| Tên doanh nghiệp chủ quản| Link | Tên doanh nghiệp quản lý cơ sở (click để xem thông tin doanh nghiệp). |
| Loại hình lưu trú | Label – String | Phân loại (Ví dụ: Khách sạn 5 sao). |
| Địa chỉ | Label – String | Thông tin địa chỉ chi tiết. |
| Số điện thoại | Label – String | Hotline liên hệ đặt phòng. |
| Mô tả chi tiết | Text Block | Đoạn văn bản giới thiệu về dịch vụ, không gian của cơ sở. |
| Bản đồ vị trí | Map View | Khung bản đồ có ghim vị trí của cơ sở lưu trú. |
| Danh sách tiện ích | Tag List | Các tiện ích nổi bật (Wifi, Hồ bơi, Bãi đỗ xe...). |
| Trạng thái | Badge | Trạng thái hoạt động hoặc trạng thái phê duyệt hồ sơ. |
| Nút Quay lại | Button | Quay về danh sách cơ sở lưu trú. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Xem thông tin** | Hệ thống tự động load thông tin khi vào trang. | Hiển thị đầy đủ text và hình ảnh. | Lỗi mạng, không tải được ảnh hoặc bản đồ. |

---

### c. Thêm cơ sở lưu trú

<p align="center"><i>Hình 3.3: Giao diện Thêm cơ sở lưu trú</i></p>

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
| Vị trí tọa độ | Map Picker | Click trên bản đồ để tự điền tọa độ hoặc nhập tay. |
| Tải ảnh lên | File Upload | Chọn và tải các hình ảnh/logo của cơ sở. |
| Nút Lưu lại | Button (Primary) | Nhấn để gửi dữ liệu khai báo lên hệ thống. |
| Nút Hủy bỏ | Button (Secondary) | Hủy thao tác, quay về màn hình trước. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Lưu dữ liệu** | Ghi nhận thông tin cơ sở lưu trú mới. | Hiển thị popup "Thêm mới thành công" và chuyển về danh sách. | Báo lỗi viền đỏ tại các trường bị bỏ trống hoặc sai định dạng. |

---

### d. Sửa cơ sở lưu trú

<p align="center"><i>Hình 3.4: Giao diện Sửa cơ sở lưu trú</i></p>

| **Màn hình** | **Sửa cơ sở lưu trú** |
| :--- | :--- |
| **Mô tả** | Biểu mẫu cho phép cập nhật, thay đổi các thông tin đã khai báo của cơ sở lưu trú. Hệ thống sẽ điền sẵn dữ liệu cũ vào các trường. |
| **Màn hình kết nối** | Danh sách cơ sở lưu trú |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Các trường thông tin | Textfield / Combobox | Tương tự màn hình Thêm mới, nhưng hiển thị sẵn dữ liệu hiện tại. |
| Quản lý hình ảnh | Image Grid | Hiển thị các ảnh đã tải lên, cho phép bấm xóa ảnh cũ và tải thêm ảnh mới. |
| Nút Cập nhật | Button (Primary) | Lưu lại các thay đổi vào hệ thống. |
| Nút Hủy | Button (Secondary) | Bỏ qua các thay đổi. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Cập nhật** | Ghi đè các thông tin chỉnh sửa. | Báo "Cập nhật thành công", lưu vào CSDL và quay lại trang danh sách. | Lỗi xác thực dữ liệu nếu xóa rỗng trường bắt buộc. |

---

### e. Xóa cơ sở lưu trú

<p align="center"><i>Hình 3.5: Giao diện Xóa cơ sở lưu trú (Popup)</i></p>

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
| Nút Hủy | Button (Secondary) | Đóng popup. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Thực hiện xóa** | Gỡ bỏ bản ghi khỏi danh sách quản lý. | Thông báo xóa thành công, làm mới bảng danh sách. | Hệ thống báo lỗi nếu cơ sở đang có tour hoặc phản hồi liên quan, gợi ý chuyển sang "Ngừng hoạt động". |

---

### f. Phê duyệt cơ sở lưu trú

<p align="center"><i>Hình 3.6: Giao diện Phê duyệt cơ sở lưu trú</i></p>

| **Màn hình** | **Phê duyệt cơ sở lưu trú** |
| :--- | :--- |
| **Mô tả** | Màn hình dành cho Quản trị viên xem xét thông tin hồ sơ khai báo của doanh nghiệp trước khi cho phép hiển thị công khai. |
| **Màn hình kết nối** | Danh sách cơ sở lưu trú |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Thông tin chi tiết | Label / Image | Hiển thị thông tin giống hệt màn hình Xem chi tiết để QTV rà soát. |
| Giấy tờ đính kèm | Link / File Icon | Xem hoặc tải các giấy phép kinh doanh đính kèm để đối chiếu. |
| Nút Phê duyệt | Button (Success) | Nhấn để cấp quyền hoạt động. |
| Nút Từ chối | Button (Danger) | Nhấn để từ chối duyệt (Mở popup từ chối). |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Duyệt hồ sơ** | Đổi trạng thái sang "Đã duyệt/Hoạt động". | Thông báo duyệt thành công, gửi email cho doanh nghiệp. | (Không có) |

---

### g. Từ chối phê duyệt cơ sở lưu trú

<p align="center"><i>Hình 3.7: Giao diện Từ chối phê duyệt (Popup)</i></p>

| **Màn hình** | **Từ chối phê duyệt cơ sở lưu trú (Popup)** |
| :--- | :--- |
| **Mô tả** | Hộp thoại yêu cầu Quản trị viên nhập lý do giải thích vì sao hồ sơ khai báo của doanh nghiệp bị từ chối. |
| **Màn hình kết nối** | Màn hình Phê duyệt cơ sở lưu trú |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Tiêu đề | Label – String | "Từ chối phê duyệt hồ sơ". |
| Ô nhập lý do | Textarea – String | Khu vực để QTV nhập chi tiết lý do từ chối (Bắt buộc). |
| Nút Xác nhận | Button (Primary) | Xác nhận hành động từ chối và lưu lý do. |
| Nút Hủy | Button (Secondary) | Tắt popup. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Xác nhận từ chối** | Chuyển trạng thái sang "Từ chối" và gửi phản hồi. | Hồ sơ bị trả lại, doanh nghiệp nhận được thông báo kèm lý do. | Không nhập lý do, hệ thống báo lỗi viền đỏ tại trường nhập. |

---

## 3.5 QUẢN LÝ LỮ HÀNH VÀ HDV

### 3.5.1 Đơn vị lữ hành

#### a. Danh sách đơn vị lữ hành

<p align="center"><i>Hình 3.8: Giao diện Danh sách đơn vị lữ hành</i></p>

| **Màn hình** | **Danh sách đơn vị lữ hành** |
| :--- | :--- |
| **Mô tả** | Màn hình danh sách theo dõi và quản lý thông tin các công ty/đơn vị hoạt động kinh doanh lữ hành. |
| **Màn hình kết nối** | Xem chi tiết, Thêm, Sửa, Xóa đơn vị lữ hành |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Ô tìm kiếm | Textfield – String | Nhập tên công ty lữ hành. |
| Lọc địa bàn | Combobox | Lọc theo Phường/Xã/Quận/Huyện. |
| Nút Thêm mới | Button | Mở form tạo đơn vị lữ hành mới. |
| Bảng dữ liệu | Table | Danh sách các đơn vị lữ hành. |
| *STT* | Label – Number | Số thứ tự. |
| *Tên công ty lữ hành* | Link | Click để vào xem chi tiết đơn vị. |
| *Số điện thoại* | Label – String | Số hotline giao dịch. |
| *Địa chỉ* | Label – String | Địa chỉ trụ sở văn phòng. |
| *Thao tác* | Icon Buttons | Xem, Sửa, Xóa. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Tìm kiếm, Lọc** | Tìm thông tin theo các điều kiện lọc. | Bảng dữ liệu cập nhật danh sách phù hợp. | Không tìm thấy kết quả. |

#### b. Xem chi tiết đơn vị lữ hành

<p align="center"><i>Hình 3.9: Giao diện Xem chi tiết đơn vị lữ hành</i></p>

| **Màn hình** | **Xem chi tiết đơn vị lữ hành** |
| :--- | :--- |
| **Mô tả** | Giao diện hiển thị các thông tin giới thiệu, địa chỉ liên hệ và các thông tin phụ thuộc của công ty lữ hành. |
| **Màn hình kết nối** | Danh sách đơn vị lữ hành |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Tên công ty lữ hành | Label – String | Hiển thị tên đầy đủ công ty. |
| Doanh nghiệp chủ quản | Link | Tên pháp nhân đại diện (Click xem chi tiết DN). |
| Giới thiệu chung | Text Block | Thông tin mô tả, năng lực tổ chức tour. |
| Địa chỉ văn phòng | Label – String | Nơi đặt trụ sở hoạt động. |
| Số điện thoại | Label – String | Số liên hệ. |
| Trạng thái | Badge | Đang hoạt động / Ngừng hoạt động. |
| Danh sách tour | Data Table | Bảng hiển thị các tour mà đơn vị này đang tổ chức mở bán. |
| Danh sách HDV | Data Table | Danh sách các Hướng dẫn viên trực thuộc công ty. |
| Nút Quay lại | Button | Trở về trang danh sách. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Xem chi tiết** | Trình bày toàn bộ dữ liệu đơn vị. | Hiển thị rõ ràng các trường dữ liệu và bảng phụ. | (Không có) |

---

### 3.5.2 Hướng dẫn viên

#### a. Danh sách loại hướng dẫn viên

*(Ghi chú: Quản lý danh sách HDV thực tế)*

<p align="center"><i>Hình 3.10: Giao diện Danh sách Hướng dẫn viên</i></p>

| **Màn hình** | **Danh sách Hướng dẫn viên** |
| :--- | :--- |
| **Mô tả** | Quản lý danh sách các hướng dẫn viên du lịch, thông tin thẻ hành nghề và ngôn ngữ. |
| **Màn hình kết nối** | Xem chi tiết HDV |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Ô tìm kiếm | Textfield – String | Tìm theo tên HDV hoặc Số thẻ HDV. |
| Lọc ngôn ngữ | Combobox | Tiếng Anh, Tiếng Pháp, Tiếng Trung... |
| Lọc công ty lữ hành| Combobox | Lọc HDV trực thuộc đơn vị lữ hành nào. |
| Bảng dữ liệu | Table | Hiển thị thông tin HDV. |
| *Họ và tên* | Link | Tên HDV, bấm để xem chi tiết. |
| *Số thẻ hành nghề* | Label – String | Mã số thẻ của HDV. |
| *Ngôn ngữ* | Tag List | Các ngôn ngữ HDV thành thạo. |
| *Công ty chủ quản* | Label – String | Công ty quản lý HDV này. |
| *Trạng thái* | Badge | Đang hoạt động / Nghỉ việc. |
| *Thao tác* | Icon Buttons | Xem, Sửa, Xóa. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Lọc và phân trang** | Tra cứu danh sách HDV. | Hệ thống trả về danh sách chính xác. | Không tìm thấy. |

#### b. Xem chi tiết hướng dẫn viên

<p align="center"><i>Hình 3.11: Giao diện Xem chi tiết HDV</i></p>

| **Màn hình** | **Xem chi tiết hướng dẫn viên** |
| :--- | :--- |
| **Mô tả** | Hiển thị hồ sơ cá nhân, thông tin liên lạc, hình ảnh thẻ hành nghề của HDV. |
| **Màn hình kết nối** | Danh sách Hướng dẫn viên |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Ảnh chân dung | Image | Hình ảnh đại diện của cá nhân. |
| Họ và tên | Label – String | Tên đầy đủ của HDV. |
| Số thẻ hành nghề | Label – String | Số thẻ do Sở cấp. |
| Ngôn ngữ | Tag List | Tiếng Anh, Tiếng Việt... |
| SĐT / Email | Label – String | Thông tin liên lạc của HDV. |
| Ảnh thẻ HDV 2 mặt | Image Viewer | Hình chụp 2 mặt thẻ hành nghề. |
| Lịch sử dẫn tour | Data Table | Hiển thị danh sách các tour HDV này đã/đang phụ trách. |
| Nút Quay lại | Button | Về trang danh sách. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Xem hồ sơ** | Hiển thị dữ liệu. | Tải đầy đủ hình ảnh thẻ và lịch sử tour. | (Không có) |

---

### 3.5.3 Tour du lịch

#### a. Danh sách tour du lịch

<p align="center"><i>Hình 3.12: Giao diện Danh sách tour du lịch</i></p>

| **Màn hình** | **Danh sách tour du lịch** |
| :--- | :--- |
| **Mô tả** | Quản lý danh sách các gói chương trình tour du lịch do các đơn vị lữ hành thiết lập. |
| **Màn hình kết nối** | Xem chi tiết Tour |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Tìm kiếm | Textfield – String | Tìm kiếm theo tên chương trình tour. |
| Lọc đơn vị tổ chức | Combobox | Chọn công ty lữ hành. |
| Lọc trạng thái cấp phép| Combobox | Đã cấp phép / Chờ duyệt. |
| Bảng dữ liệu | Table | Danh sách các gói tour. |
| *Tên tour du lịch* | Link | Tên gói tour, nhấn để xem chi tiết. |
| *Thời lượng* | Label – String | Ví dụ: "2 ngày 1 đêm". |
| *Giá tour* | Label – String | Mức giá niêm yết (VNĐ). |
| *Đơn vị tổ chức* | Label – String | Tên công ty quản lý. |
| *Trạng thái* | Badge | Đang mở bán / Tạm ẩn. |
| *Thao tác* | Icon Buttons | Xem, Sửa, Phân công HDV. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Lọc và tìm kiếm** | Truy vấn bảng danh sách tour. | Bảng hiển thị thông tin khớp yêu cầu. | (Không có) |

#### b. Xem chi tiết tour du lịch

<p align="center"><i>Hình 3.13: Giao diện Xem chi tiết tour du lịch</i></p>

| **Màn hình** | **Xem chi tiết tour du lịch** |
| :--- | :--- |
| **Mô tả** | Hiển thị lịch trình cụ thể, giá cả và thông tin liên quan đến gói tour. |
| **Màn hình kết nối** | Danh sách tour du lịch |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Tên chương trình tour| Label – String | Tiêu đề tour cỡ lớn. |
| Đơn vị tổ chức | Link | Tên đơn vị lữ hành (Click để xem thông tin đơn vị). |
| Giá bán | Label – String | Giá bán (Định dạng VNĐ). |
| Thời lượng | Label – String | Tổng thời gian (1 ngày, 2 ngày...). |
| Lịch trình di chuyển | Text Block / HTML | Văn bản thuyết minh các mốc thời gian, điểm đến, nhà hàng, khách sạn trong tour. |
| Trạng thái cấp phép | Badge | Trạng thái phê duyệt nội dung tour của Sở. |
| Danh sách HDV | Data Table | Danh sách HDV được phân công cho tour này. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Xem chi tiết** | Load dữ liệu text và bảng phụ. | Hiển thị rõ ràng nội dung lịch trình. | (Không có) |

---

## 3.6 QUẢN LÝ ĂN UỐNG & MUA SẮM

### a. Danh sách quán ăn và mua sắm

<p align="center"><i>Hình 3.14: Giao diện Danh sách quán ăn và mua sắm</i></p>

| **Màn hình** | **Danh sách quán ăn và mua sắm** |
| :--- | :--- |
| **Mô tả** | Màn hình hiển thị danh sách các nhà hàng, quán ăn, siêu thị đặc sản và điểm mua sắm. |
| **Màn hình kết nối** | Xem chi tiết cơ sở |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Tìm kiếm | Textfield – String | Nhập tên quán ăn/điểm mua sắm. |
| Lọc Dịch vụ | Combobox | Loại hình: Nhà hàng, Quán ăn, Siêu thị lưu niệm... |
| Lọc khu vực | Combobox | Chọn Phường/Xã/Quận/Huyện. |
| Bảng dữ liệu | Table | Danh sách cơ sở dịch vụ. |
| *Tên cơ sở* | Link | Click để mở xem chi tiết. |
| *Loại dịch vụ* | Label – String | Phân loại (Nhà hàng, Quán ăn). |
| *Địa chỉ* | Label – String | Khu vực, số nhà. |
| *Trạng thái* | Badge | Hoạt động / Ẩn. |
| *Thao tác* | Icon Buttons | Xem, Sửa, Xóa. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Tra cứu cơ sở** | Lọc dữ liệu theo tên/loại hình. | Bảng dữ liệu làm mới chính xác. | Không tìm thấy bản ghi. |

### b. Xem chi tiết quán ăn và mua sắm

<p align="center"><i>Hình 3.15: Giao diện Xem chi tiết quán ăn và mua sắm</i></p>

| **Màn hình** | **Xem chi tiết quán ăn và mua sắm** |
| :--- | :--- |
| **Mô tả** | Trình bày thông tin, không gian, thực đơn/đặc sản của cơ sở kinh doanh dịch vụ ăn uống, mua sắm. |
| **Màn hình kết nối** | Danh sách quán ăn và mua sắm |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Tên cơ sở dịch vụ | Label – String | Tiêu đề tên quán/nhà hàng. |
| Thư viện ảnh | Image Slider | Các ảnh chụp không gian, món ăn, đồ lưu niệm. |
| Doanh nghiệp chủ quản| Link | Tên doanh nghiệp. |
| Địa chỉ | Label – String | Vị trí cụ thể. |
| Bản đồ vị trí | Map View | Bản đồ ghim tọa độ quán. |
| Mô tả / Thực đơn | Text Block | Giới thiệu các món đặc sản, mặt hàng kinh doanh chính. |
| Tiện ích đi kèm | Tag List | Có bãi đỗ xe, phòng lạnh, thanh toán thẻ... |
| Trạng thái | Badge | Đang hiển thị / Tạm ẩn. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Xem chi tiết** | Load thông tin và media. | Hiển thị đầy đủ hình ảnh, không gian quán. | Lỗi không load được ảnh. |

---

## 3.7 QUẢN LÝ ĐIỂM ĐẾN

### a. Danh sách điểm đến

<p align="center"><i>Hình 3.16: Giao diện Danh sách điểm đến</i></p>

| **Màn hình** | **Danh sách điểm đến** |
| :--- | :--- |
| **Mô tả** | Quản lý kho dữ liệu tài nguyên du lịch cốt lõi (Di tích lịch sử, danh lam thắng cảnh, làng nghề...). |
| **Màn hình kết nối** | Xem chi tiết điểm đến |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Tìm kiếm | Textfield – String | Tìm tên điểm đến (VD: Đại Nội). |
| Lọc loại hình | Combobox | Di tích, Thắng cảnh, Làng nghề, Tâm linh. |
| Bảng dữ liệu | Table | Danh sách các điểm tham quan. |
| *Tên điểm đến* | Link | Click để xem chi tiết. |
| *Loại hình* | Label – String | Phân loại điểm đến. |
| *Địa bàn* | Label – String | Tên Phường/Xã khu vực đó. |
| *Trạng thái* | Badge | Đang hoạt động / Ẩn. |
| *Thao tác* | Icon Buttons | Xem, Sửa, Xóa. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Tra cứu** | Tìm tài nguyên theo bộ lọc. | Bảng trả về thông tin chuẩn xác. | Bảng rỗng nếu không khớp. |

### b. Xem chi tiết điểm đến

<p align="center"><i>Hình 3.17: Giao diện Xem chi tiết điểm đến</i></p>

| **Màn hình** | **Xem chi tiết điểm đến** |
| :--- | :--- |
| **Mô tả** | Cung cấp bài viết thuyết minh chi tiết, hình ảnh chất lượng cao và thông tin tham quan của điểm đến. |
| **Màn hình kết nối** | Danh sách điểm đến |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Tên điểm đến | Label – String | Tên khu di tích / thắng cảnh. |
| Media / Hình ảnh | Image Slider | Trình chiếu hình ảnh phong cảnh, ảnh góc rộng. |
| Loại hình | Label – String | Hiển thị loại hình (Di sản văn hóa...). |
| Địa chỉ | Label – String | Vị trí địa lý. |
| Bản đồ định vị | Map View | Bản đồ ghim đúng tọa độ điểm tham quan. |
| Bài viết thuyết minh | Text Block / HTML | Nội dung diễn giải về lịch sử, kiến trúc, giá trị văn hóa. |
| Tiện ích | Tag List | Hỗ trợ xe điện, lối đi xe lăn, Audio Guide. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Xem nội dung** | Đọc bài thuyết minh và xem ảnh. | Layout trình bày đẹp mắt, dễ đọc. | (Không có) |

---

## 3.8 QUẢN LÝ LỄ HỘI VÀ SỰ KIỆN

### a. Danh sách lễ hội và sự kiện

<p align="center"><i>Hình 3.18: Giao diện Danh sách lễ hội và sự kiện</i></p>

| **Màn hình** | **Danh sách lễ hội và sự kiện** |
| :--- | :--- |
| **Mô tả** | Màn hình quản lý các hoạt động lễ hội văn hóa, Festival, sự kiện thể thao diễn ra theo thời gian. |
| **Màn hình kết nối** | Xem chi tiết sự kiện |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Tìm kiếm | Textfield – String | Tên lễ hội, sự kiện. |
| Lọc thời gian | Date Picker | Lọc theo mốc "Từ ngày - Đến ngày". |
| Lọc trạng thái | Combobox | Sắp diễn ra / Đang diễn ra / Đã kết thúc / Hủy. |
| Bảng dữ liệu | Table | Danh sách sự kiện. |
| *Tên sự kiện* | Link | Tên lễ hội (Bấm để xem). |
| *Địa điểm* | Label – String | Nơi tổ chức sự kiện. |
| *Thời gian bắt đầu* | Label – String | Ngày, giờ khai mạc. |
| *Thời gian kết thúc* | Label – String | Ngày, giờ bế mạc. |
| *Trạng thái* | Badge | Hiển thị nhãn tiến độ sự kiện. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Tra cứu sự kiện** | Tìm lịch trình lễ hội. | Cập nhật bảng các sự kiện diễn ra trong tháng. | Không có sự kiện. |

### b. Xem chi tiết lễ hội và sự kiện

<p align="center"><i>Hình 3.19: Giao diện Xem chi tiết lễ hội sự kiện</i></p>

| **Màn hình** | **Xem chi tiết sự kiện** |
| :--- | :--- |
| **Mô tả** | Hiển thị thông tin chi tiết về chương trình sự kiện, ban tổ chức và địa điểm. |
| **Màn hình kết nối** | Danh sách lễ hội và sự kiện |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Tên Lễ hội / Sự kiện | Label – String | Tiêu đề sự kiện (VD: Festival Huế). |
| Banner / Poster | Image | Ảnh quảng bá chính thức của sự kiện. |
| Thời gian tổ chức | Label – String | Thời gian từ Khai mạc đến Bế mạc. |
| Địa điểm | Label – String | Khu vực tổ chức (VD: Quảng trường Ngọ Môn). |
| Nội dung chương trình | Text Block | Diễn giải các hoạt động chính, thông tin vé. |
| Trạng thái | Badge | Nhãn: Đang diễn ra, Đã kết thúc. |
| Tiện ích hỗ trợ | Tag List | Có y tế, bảo vệ, quầy thông tin... |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Xem thông tin** | Cung cấp thông tin chương trình. | Giao diện trực quan, đầy đủ. | (Không có) |

---

## 3.9 QUẢN LÝ PHẢN HỒI

### 3.9.1 Quản lý phản hồi quản trị viên

<p align="center"><i>Hình 3.20: Giao diện Quản lý phản hồi (Admin)</i></p>

| **Màn hình** | **Quản lý phản hồi (Dành cho QTV)** |
| :--- | :--- |
| **Mô tả** | Quản trị viên theo dõi toàn bộ đánh giá của du khách đối với các điểm đến, dịch vụ, tiến hành kiểm duyệt để ẩn/hiện đánh giá. |
| **Màn hình kết nối** | (Không có) |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Lọc số sao | Combobox | Lọc các đánh giá 1 sao, 2 sao... 5 sao. |
| Lọc trạng thái | Combobox | Chưa duyệt / Đã duyệt / Bị ẩn. |
| Bảng phản hồi | Table | Danh sách các bình luận đánh giá. |
| *Du khách* | Label – String | Tên/Tài khoản người gửi. |
| *Nội dung đánh giá* | Text | Chi tiết dòng bình luận góp ý. |
| *Số sao* | Icon (Stars) | Mức độ hài lòng (1 đến 5 sao vàng). |
| *Thời gian* | Label – String | Ngày giờ đăng bình luận. |
| *Thao tác Duyệt/Ẩn* | Switch | Nút gạt bật/tắt (Hiển thị công khai hoặc Ẩn). |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Kiểm duyệt** | QTV gạt nút duyệt/ẩn phản hồi. | Trạng thái bình luận được cập nhật trên app du khách. | (Không có) |

### 3.9.2 Quản lý phản hồi doanh nghiệp

<p align="center"><i>Hình 3.21: Giao diện Quản lý phản hồi (Doanh nghiệp)</i></p>

| **Màn hình** | **Quản lý phản hồi (Dành cho Doanh nghiệp)** |
| :--- | :--- |
| **Mô tả** | Giao diện để doanh nghiệp xem và trả lời lại các đánh giá của du khách đối với cơ sở dịch vụ của mình. |
| **Màn hình kết nối** | (Không có) |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Danh sách đánh giá | List / Card | Các khung (card) hiển thị từng đánh giá. |
| Tên khách & Số sao | Label + Icons | Tên người viết và số sao đánh giá. |
| Nội dung khách viết | Text | Bình luận của du khách. |
| Ô nhập trả lời | Textarea | Nơi doanh nghiệp nhập văn bản trả lời, cảm ơn. |
| Nút Trả lời | Button | Nhấn để gửi câu trả lời. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Trả lời khách** | Doanh nghiệp gửi phản hồi lại khách. | Câu trả lời đính kèm dưới bình luận gốc. | Gửi nội dung rỗng (Báo lỗi). |

---

## 3.10 TÌM KIẾM THÔNG TIN DU LỊCH

<p align="center"><i>Hình 3.22: Giao diện Tìm kiếm tổng hợp</i></p>

| **Màn hình** | **Tìm kiếm thông tin du lịch** |
| :--- | :--- |
| **Mô tả** | Tính năng tìm kiếm thông minh đa tiêu chí, trả về kết quả trộn lẫn từ các module (Điểm đến, Lưu trú, Lữ hành, Sự kiện). |
| **Màn hình kết nối** | Chuyển đến màn hình Xem chi tiết của từng đối tượng. |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Ô Tìm kiếm lớn | Textfield | Ô nhập từ khóa (có placeholder gợi ý). |
| Tab phân loại | Button Group | Tất cả, Điểm đến, Lưu trú, Ăn uống, Sự kiện. |
| Lọc khoảng cách | Dropdown / Slider| Lọc kết quả nằm trong bán kính 1km, 5km... |
| Danh sách kết quả | Card Grid | Các ô kết quả hiển thị dạng thẻ card. |
| *Hình ảnh Thumbnail* | Image | Ảnh đại diện của dịch vụ/điểm đến. |
| *Tên đối tượng* | Label – String | Tiêu đề kết quả. |
| *Khoảng cách* | Label – String | Ví dụ: Cách 2.5 km. |
| *Đánh giá sao* | Icon (Stars) | Điểm số trung bình. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Tìm kiếm tổng hợp**| Gõ từ khóa và nhấn Enter. | Hiển thị thẻ kết quả phù hợp nhất. | Báo "Không tìm thấy kết quả". |

---

## 3.11 QUẢN LÝ API

<p align="center"><i>Hình 3.23: Giao diện Quản lý API</i></p>

| **Màn hình** | **Quản lý cấu hình API hệ thống** |
| :--- | :--- |
| **Mô tả** | Màn hình thiết lập kết nối, quản lý khóa bảo mật API Key của các dịch vụ bên thứ ba (Bản đồ, VNeID, Thời tiết). |
| **Màn hình kết nối** | (Không có) |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Bảng cấu hình API | Table | Danh sách các cổng kết nối API. |
| *Tên dịch vụ* | Label – String | Ví dụ: Google Map, VNeID Auth. |
| *Đường dẫn (URL)* | Label – String | Link Endpoint tới máy chủ. |
| *Khóa bí mật (Key)* | Password Text | Chuỗi Token (bị ẩn dạng ***, có nút con mắt để xem). |
| *Trạng thái* | Switch | Bật/tắt kết nối API. |
| *Thao tác* | Icon Buttons | Sửa thông số, hoặc nút Test (Ping). |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Test kết nối (Ping)**| Gửi lệnh kiểm tra API hoạt động. | Báo "Kết nối thành công (200 OK)". | Báo "Lỗi kết nối / Sai Key". |

---

## 3.12 BÁO CÁO THỐNG KÊ

<p align="center"><i>Hình 3.24: Giao diện Báo cáo thống kê (Dashboard)</i></p>

| **Màn hình** | **Báo cáo thống kê** |
| :--- | :--- |
| **Mô tả** | Dashboard trình bày số liệu trực quan qua biểu đồ giúp lãnh đạo nắm bắt số lượng doanh nghiệp, cơ sở lưu trú và phản hồi du khách. |
| **Màn hình kết nối** | (Không có) |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Bộ lọc thời gian | Date Picker | Lọc báo cáo theo khoảng thời gian (Từ ngày - Đến ngày). |
| Nút Xuất file | Button | Xuất dữ liệu ra PDF / Excel. |
| Thẻ thông số (Cards) | Scorecard | Hiển thị các con số nổi bật: Tổng cơ sở, Tổng điểm đến... |
| Biểu đồ Lưu trú | Bar Chart | Biểu đồ cột phân bố lưu trú theo địa bàn. |
| Biểu đồ Phân loại | Pie Chart | Biểu đồ tròn cơ cấu điểm đến (Di tích, Thắng cảnh...). |
| Bảng Top đánh giá | Table | Danh sách xếp hạng top 5 cơ sở có điểm sao cao nhất. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Thống kê / Xuất file**| Load biểu đồ và bấm xuất báo cáo. | Hiển thị đồ thị trực quan và tải xuống file thành công. | Lỗi không tạo được file. |
