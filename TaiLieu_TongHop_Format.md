# TÀI LIỆU TỔNG HỢP

### 3.1 Đăng nhập

| **Tên Use case** | **Đăng nhập** |
| :--- | :--- |
| **Mô tả** | Thành viên (du khách, doanh nghiệp, quản trị viên, quản trị hệ thống) có tài khoản đăng nhập vào hệ thống |
| **Tác nhân** | Thành viên |
| **Độ phức tạp** | ☑️ Đơn giản 🔲 Trung bình 🔲 Phức tạp |
| **Điều kiện bắt đầu** | Người dùng đã có tài khoản được cấp hoặc đăng ký thành công |
| **Điều kiện kết thúc** | Đăng nhập thành công và được chuyển đến trang chủ tương ứng theo vai trò |
| **Kịch bản chính** | 1. Người dùng nhập tên đăng nhập (CCCD/Email/SĐT) và mật khẩu<br>2. Hệ thống xác thực qua JWT hoặc SSO (VNeID/Hue-S)<br>3. Hệ thống phân quyền và chuyển hướng đến giao diện phù hợp |
| **Kịch bản phụ** | - Sai tên đăng nhập/mật khẩu: hiển thị thông báo lỗi<br>- Tài khoản bị khóa: thông báo liên hệ quản trị<br>- Quên mật khẩu: chuyển hướng đến form đặt lại mật khẩu |
| **Các yêu cầu, ràng buộc** | Hệ thống đảm bảo kết nối internet, sử dụng HTTPS, mã hóa mật khẩu bằng bcrypt |

**Form đăng nhập:**

![Hình 1: Form đăng nhập hệ thống](09_Đăng Nhập.png)
<p align="center"><i>Hình 2: Form đăng nhập hệ thống</i></p>

| **Màn hình** | **Đăng nhập** |
| :--- | :--- |
| **Mô tả** | + Chức năng này cho phép Thành viên đăng nhập vào hệ thống |
| **Màn hình kết nối** | Trang chủ hệ thống, Trang đăng ký tài khoản, Trang quên mật khẩu, Hệ thống SSO Hue-S, Hệ thống VNeID |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Tài khoản / Email | Textfield – String | Nhập tài khoản hoặc địa chỉ email đã đăng ký trên hệ thống |
| Mật khẩu | Password – String | Nhập mật khẩu |
| Ghi nhớ đăng nhập | Checkbox | Lưu thông tin đăng nhập cho các lần truy cập tiếp theo |
| Đăng nhập hệ thống | Button | Thực hiện đăng nhập bằng tài khoản nội bộ |
| Đăng nhập qua Hue-S | Button | Đăng nhập bằng tài khoản Hue-S liên kết |
| Đăng nhập bằng VNeID | Button | Đăng nhập bằng tài khoản định danh điện tử VNeID |
| Đăng nhập bằng SSO | Button | Đăng nhập thông qua hệ thống xác thực một lần (Single Sign-On) |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| Đăng nhập | + Người dùng nhập tài khoản/email và mật khẩu để đăng nhập vào hệ thống.<br>+ Hệ thống kiểm tra tính hợp lệ của thông tin đăng nhập. | + Đăng nhập thành công vào hệ thống.<br>+ Chuyển đến giao diện theo đúng vai trò người dùng. | + Sai tài khoản hoặc mật khẩu.<br>+ Tài khoản bị khóa hoặc chưa kích hoạt. |
| Đăng nhập qua Hue-S | + Người dùng chọn đăng nhập bằng Hue-S.<br>+ Hệ thống chuyển sang cổng xác thực Hue-S để xác minh tài khoản. | + Xác thực thành công và đăng nhập vào hệ thống. | + Không xác thực được tài khoản Hue-S.<br>+ Người dùng hủy đăng nhập. |
| Đăng nhập bằng VNeID | + Người dùng chọn đăng nhập bằng VNeID.<br>+ Hệ thống kết nối với nền tảng định danh điện tử VNeID. | + Đăng nhập thành công bằng tài khoản VNeID. | + Không thể kết nối hoặc xác thực VNeID thất bại. |
| Đăng nhập bằng SSO | + Người dùng đăng nhập thông qua hệ thống SSO liên kết. | + Đăng nhập thành công và truy cập hệ thống. | + Lỗi xác thực SSO hoặc không có quyền truy cập. |
| Quên mật khẩu | + Người dùng chọn khôi phục mật khẩu khi quên thông tin đăng nhập. | + Hệ thống gửi hướng dẫn đặt lại mật khẩu qua email/SĐT. | + Không tìm thấy tài khoản tương ứng. |

### 3.2 Quản lý người dùng

| **Tên Use case** | **Quản lý người dùng** |
| :--- | :--- |
| **Mô tả** | Quản trị hệ thống thực hiện xem danh sách, thêm, sửa, xóa, khóa/mở khóa tài khoản người dùng |
| **Tác nhân** | Quản trị hệ thống |
| **Độ phức tạp** | 🔲 Đơn giản ☑️ Trung bình 🔲 Phức tạp |
| **Điều kiện bắt đầu** | Quản trị hệ thống đã đăng nhập |
| **Điều kiện kết thúc** | Thông tin người dùng được cập nhật hoặc tài khoản bị khóa/xóa |
| **Kịch bản chính** | 1. Xem danh sách người dùng (có phân trang, tìm kiếm, lọc theo vai trò, trạng thái)<br>2. Thêm mới: nhập thông tin → lưu → gán vai trò mặc định<br>3. Sửa: chỉnh sửa thông tin → lưu<br>4. Khóa/mở khóa: chọn tài khoản → xác nhận → cập nhật trạng thái<br>5. Xóa: chỉ xóa được tài khoản chưa có dữ liệu liên quan |
| **Kịch bản phụ** | Dữ liệu nhập không hợp lệ → Hiển thị lỗi.<br>Xóa tài khoản có ràng buộc → Gợi ý khóa tài khoản thay thế. |
| **Các yêu cầu, ràng buộc** | Hệ thống đảm bảo đường truyền internet ổn định |

#### a. Hiển thị danh sách người dùng

<p align="center"><i>Hình 3: Giao diện Danh sách người dùng</i></p>

| **Màn hình** | **Danh sách người dùng** |
| :--- | :--- |
| **Mô tả** | + Chức năng này cho phép Quản trị viên quản lý danh sách người dùng trong hệ thống.<br>+ Hỗ trợ tìm kiếm, phân quyền, thêm mới, chỉnh sửa và xóa thông tin người dùng. |
| **Màn hình kết nối** | Thêm mới/chỉnh sửa/xóa/xem chi tiết người dùng |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Tìm tên người dùng | Textfield – String | Nhập tên người dùng để tìm kiếm |
| Vai trò | Combobox – String | Chọn vai trò người dùng cần lọc |
| Thêm mới | Button | Chuyển sang màn hình thêm mới người dùng |
| Danh sách người dùng | Table | Danh sách người dùng (STT, Mã, Tên, Vai trò, Username, Thao tác) |
| STT | Label – Number | Hiển thị số thứ tự người dùng |
| Mã người dùng | Label – String | Hiển thị mã định danh của người dùng |
| Tên người dùng | Button | Hiển thị họ và tên người dùng. Chọn để đi đến trang chi tiết người dùng |
| Vai trò | Label – String | Hiển thị vai trò của người dùng |
| Username | Label – String | Hiển thị tên đăng nhập của người dùng |
| Chỉnh sửa | Icon Button | Chỉnh sửa thông tin người dùng |
| Xóa | Icon Button | Xóa người dùng khỏi hệ thống |
| Phân trang | Pagination | Chuyển đổi giữa các trang danh sách |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| Tìm kiếm | + Nhập tên người dùng để tìm kiếm trong hệ thống.<br>+ Hệ thống lọc dữ liệu phù hợp. | + Hiển thị danh sách người dùng phù hợp với từ khóa tìm kiếm. | + Không tìm thấy người dùng phù hợp. |
| Lọc theo vai trò | + Chọn vai trò để lọc danh sách người dùng. | + Hiển thị đúng danh sách theo vai trò được chọn. | + Không có dữ liệu phù hợp với vai trò đã chọn. |
| Thêm mới | + Quản trị viên chọn thêm mới người dùng.<br>+ Hệ thống chuyển sang màn hình tạo tài khoản mới. | + Chuyển đến màn hình thêm mới người dùng. | + Lỗi hệ thống. |

#### b. Xem chi tiết người dùng

<p align="center"><i>Hình 4: Giao diện Thông tin chi tiết người dùng</i></p>

| **Màn hình** | **Thông tin chi tiết người dùng** |
| :--- | :--- |
| **Mô tả** | Chức năng này cho phép quản trị viên xem thông tin chi tiết người dùng |
| **Màn hình kết nối** | Danh sách người dùng |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Người dùng ID | Text - String | Mã định danh của người dùng |
| VAI TRÒ | Text - String | Vai trò của người dùng trong hệ thống |
| HỌ TÊN | Text - String | Họ và tên đầy đủ của người dùng |
| USER NAME | Text - String | Tên đăng nhập hệ thống |
| EMAIL | Text - String | Địa chỉ email của người dùng |
| SỐ ĐIỆN THOẠI | Text - String | Số điện thoại liên hệ |
| ĐỊA CHỈ | Text - String | Địa chỉ liên hệ của người dùng |
| TRẠNG THÁI | Dropdown | Trạng thái hoạt động của tài khoản |
| Thoát | Button | Chọn để đóng màn hình thông tin chi tiết và quay lại danh sách người dùng |
| Chỉnh sửa | Button | Chọn để mở form chỉnh sửa thông tin người dùng |
| Xóa | Button | Chọn để xóa người dùng (có xác nhận trước khi xóa) |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| Thoát | Đóng màn hình chi tiết | Quay lại màn hình danh sách người dùng | Không thoát khỏi màn hình chi tiết |
| Chỉnh sửa | Mở form chỉnh sửa thông tin người dùng | Điều hướng đến trang chỉnh sửa với dữ liệu hiện tại được tải sẵn | Không điều hướng đến trang chỉnh sửa |
| Xóa | Xóa người dùng khỏi hệ thống | Hiển thị màn hình xác nhận xóa | Không hiển thị màn hình xác nhận |

#### c. Thêm người dùng

<p align="center"><i>Hình 5: Giao diện Thêm mới người dùng</i></p>

| **Màn hình** | **Thêm mới người dùng** |
| :--- | :--- |
| **Mô tả** | Chức năng này cho phép quản trị viên thêm mới thông tin một người dùng vào hệ thống |
| **Màn hình kết nối** | Danh sách người dùng |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Vai trò | Dropdown – String | Chọn vai trò của người dùng trong hệ thống |
| Họ tên | Textfield – String | Nhập họ và tên đầy đủ |
| Username | Textfield – String | Nhập tên đăng nhập hệ thống |
| Email | Textfield – String | Nhập địa chỉ email |
| Số điện thoại | Textfield – String | Nhập số điện thoại liên hệ |
| Địa chỉ | Textfield – String | Nhập địa chỉ liên hệ |
| Mật khẩu | Password – String | Nhập mật khẩu khởi tạo |
| Trạng thái | Dropdown | Chọn trạng thái hoạt động của tài khoản |
| Lưu | Button | Bấm nút Lưu để lưu thông tin người dùng mới |
| Hủy bỏ | Button | Bấm nút Hủy để hủy thao tác thêm mới người dùng |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| Lưu | + Chọn để thêm mới người dùng<br>+ Kiểm tra tính hợp lệ của dữ liệu | + Dữ liệu được cập nhật lên hệ thống.<br>+ Hiển thị thông báo thành công<br>+ Quay lại danh sách | + Dữ liệu không hợp lệ hoặc username/email bị trùng.<br>+ Hiển thị lỗi tương ứng |
| Hủy bỏ | Chọn để hủy yêu cầu thêm mới người dùng | Đóng màn hình thêm mới và quay lại danh sách | Không đóng màn hình thêm mới |

#### d. Sửa thông tin người dùng

<p align="center"><i>Hình 6: Giao diện Chỉnh sửa thông tin người dùng</i></p>

| **Màn hình** | **Chỉnh sửa thông tin người dùng** |
| :--- | :--- |
| **Mô tả** | Chức năng này cho phép quản trị viên chỉnh sửa thông tin của người dùng đã có trong hệ thống |
| **Màn hình kết nối** | Danh sách người dùng, Thông tin chi tiết người dùng |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Người dùng ID | Text - String | Mã định danh duy nhất của người dùng, không cho phép sửa |
| VAI TRÒ | Dropdown – String | Chọn vai trò của người dùng trong hệ thống |
| HỌ TÊN | Textfield - String | Nhập họ và tên đầy đủ |
| USER NAME | Textfield - String | Nhập tên đăng nhập hệ thống |
| EMAIL | Textfield - String | Nhập địa chỉ email của người dùng |
| SỐ ĐIỆN THOẠI | Textfield - String | Nhập số điện thoại liên hệ |
| ĐỊA CHỈ | Textfield - String | Nhập địa chỉ liên hệ của người dùng |
| TRẠNG THÁI | Dropdown | Chọn trạng thái hoạt động của tài khoản |
| Hủy | Button | Chọn để hủy thay đổi, không lưu và quay lại màn hình trước đó |
| Lưu | Button | Chọn để lưu các thay đổi đã nhập vào hệ thống |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| Hủy | Hủy thay đổi và đóng màn hình chỉnh sửa | Quay lại màn hình danh sách hoặc chi tiết người dùng mà không lưu thay đổi | Không đóng màn hình hoặc vẫn giữ trạng thái chỉnh sửa |
| Lưu | Lưu thông tin người dùng đã chỉnh sửa | Cập nhật thành công dữ liệu người dùng, hiển thị thông báo thành công | Không lưu được dữ liệu, hiển thị lỗi validation |

#### e. Xóa người dùng

<p align="center"><i>Hình 7: Giao diện Xóa người dùng</i></p>

| **Màn hình** | **Xóa người dùng** |
| :--- | :--- |
| **Mô tả** | Chức năng này hiển thị hộp thoại xác nhận trước khi xóa vĩnh viễn một người dùng khỏi hệ thống, nhằm tránh thao tác nhầm lẫn |
| **Màn hình kết nối** | Danh sách người dùng, Thông tin chi tiết người dùng |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Tiêu đề hộp thoại | String (static) | Dòng chữ "Xác nhận xóa người dùng" hiển thị ở đầu hộp thoại |
| Câu hỏi xác nhận | String (dynamic) | Dòng chữ xác nhận việc xóa kèm theo thông tin/tên người dùng |
| Cảnh báo logic | String (static) | Cảnh báo: "Việc xóa người dùng này sẽ ảnh hưởng đến các dữ liệu liên quan." |
| Hủy bỏ | Button | Nút bấm để đóng hộp thoại và hủy thao tác xóa |
| Xác nhận Xóa | Button | Nút bấm để thực hiện xóa vĩnh viễn người dùng khỏi hệ thống |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| Xác nhận Xóa | Người dùng nhấn nút "Xác nhận Xóa" để thực hiện xóa người dùng | Xóa thành công người dùng khỏi hệ thống, đóng hộp thoại, hiển thị thông báo "Xóa thành công", làm mới danh sách | Xóa thất bại do lỗi hệ thống hoặc ràng buộc dữ liệu, hiển thị thông báo lỗi |
| Hủy bỏ | Người dùng nhấn nút "Hủy bỏ" để đóng hộp thoại mà không xóa | Đóng hộp thoại, quay lại màn hình trước đó, dữ liệu không thay đổi | Hộp thoại không đóng, vẫn hiển thị |



---



## 3.3 QUẢN LÝ DANH MỤC HỆ THỐNG


---

### 3.3.1 Địa bàn

| **Tên Use case** | **Quản lý danh mục Địa bàn** |
| :--- | :--- |
| **Mô tả** | Quản trị viên hệ thống thực hiện xem danh sách, tìm kiếm, lọc, thêm mới, cập nhật và xóa các đơn vị hành chính (Tỉnh/Thành phố, Quận/Huyện, Phường/Xã) trên hệ thống làm cơ sở dữ liệu nền tảng cho việc định vị và quản lý vùng. |
| **Tác nhân** | Quản trị viên hệ thống (Admin) |
| **Độ phức tạp** | ☑️ Đơn giản  🔲 Trung bình  🔲 Phức tạp |
| **Điều kiện bắt đầu** | Người dùng đăng nhập bằng tài khoản Quản trị viên và truy cập menu "Quản lý danh mục" &rarr; "Địa bàn". |
| **Điều kiện kết thúc** | Thông tin danh mục địa bàn được thêm mới, cập nhật hoặc xóa thành công khỏi hệ thống hoặc người dùng hủy bỏ hành động. |

#### a. Hiển thị danh sách địa bàn

<p align="center"><i>Hình 8: Giao diện Danh sách địa bàn</i></p>

| **Màn hình** | **Danh sách Danh mục Địa bàn** |
| :--- | :--- |
| **Mô tả** | Màn hình hiển thị danh sách tập trung toàn bộ các đơn vị hành chính trên địa bàn, hỗ trợ tìm kiếm nhanh, lọc theo cấp hành chính và thực hiện điều hướng đến các chức năng Thêm, Sửa, Xóa. |
| **Màn hình kết nối** | Biểu mẫu Thêm mới địa bàn, Biểu mẫu Chỉnh sửa địa bàn, Popup Xác nhận xóa |

**Nội dung màn hình (Main Content):**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Ô tìm kiếm địa bàn | Textfield – String | Nhập từ khóa để tìm kiếm địa bàn theo tên hoặc mã địa bàn. |
| Bộ lọc Cấp địa bàn | Combobox | Lọc danh sách địa bàn theo cấp: Tất cả, Tỉnh/Thành phố, Quận/Huyện, Phường/Xã. |
| Bộ lọc Trực thuộc | Combobox | Lọc các địa bàn con thuộc một địa bàn cha cụ thể (ví dụ: lọc các Phường/Xã thuộc Huyện Phú Vang). |
| Nút Tìm kiếm | Button | Thực hiện quét và hiển thị dữ liệu theo từ khóa và bộ lọc đã chọn. |
| Nút Thêm Mới | Button (Primary) | Nút bấm để mở màn hình "Thêm mới Địa bàn". |
| Bảng danh sách địa bàn | Table | Khung chứa dữ liệu danh sách địa bàn dạng hàng và cột. |
| *STT* | Label – Number | Số thứ tự dòng hiển thị. |
| *Mã địa bàn* | Label – String | Mã định danh duy nhất của đơn vị hành chính (VD: HUE, TP_HUE, PV_TT). |
| *Tên địa bàn* | Label – String | Tên gọi của đơn vị hành chính (VD: Thành phố Huế, Phường Thuận Hòa, Huyện Phú Vang). |
| *Cấp địa bàn* | Label – String | Cấp hành chính tương ứng (Tỉnh/Thành phố, Quận/Huyện, Phường/Xã). |
| *Trực thuộc* | Label – String | Hiển thị tên đơn vị hành chính cấp trên quản lý trực tiếp (nếu có). |
| *Trạng thái* | Badge | Nhãn hiển thị trạng thái hoạt động: "Đang sử dụng" (Xanh) hoặc "Ngừng sử dụng" (Xám). |
| *Thao tác* | Icon Buttons | Bộ icon hành động: Icon Sửa (Hình cây bút) và Icon Xóa (Hình thùng rác). |
| Thanh phân trang | Pagination | Các nút điều hướng chuyển trang (Đầu, Trước, Các số trang 1, 2, 3..., Sau, Cuối) kèm thông tin số lượng. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Xem danh sách** | Tự động tải và kết xuất toàn bộ dữ liệu địa bàn từ cơ sở dữ liệu khi truy cập màn hình. | Danh sách hiển thị đầy đủ, chính xác, phân trang mặc định 10 dòng/trang. | Lỗi kết nối máy chủ, bảng hiển thị thông báo "Không thể tải dữ liệu". |
| **Tra cứu & Lọc dữ liệu** | Người dùng nhập từ khóa hoặc chọn bộ lọc và nhấn nút Tìm kiếm. | Bảng dữ liệu làm mới và chỉ hiển thị các bản ghi thỏa mãn điều kiện. | Không tìm thấy kết quả phù hợp, bảng hiển thị thông báo "Không tìm thấy dữ liệu". |
| **Điều hướng Thêm mới** | Người dùng click vào nút "Thêm Mới". | Chuyển hướng sang giao diện Biểu mẫu "Thêm mới Địa bàn". | (Không có) |

#### b. Thêm địa bàn

<p align="center"><i>Hình 9: Giao diện Thêm mới địa bàn</i></p>

| **Màn hình** | **Thêm mới Địa bàn** |
| :--- | :--- |
| **Mô tả** | Biểu mẫu cho phép Quản trị viên khởi tạo và nhập thông tin cho một đơn vị hành chính mới vào hệ thống. |
| **Màn hình kết nối** | Danh sách Danh mục Địa bàn |

**Nội dung màn hình (Main Content):**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Mã địa bàn | Textfield – String | Nhập mã định danh viết liền, không dấu của địa bàn (VD: PHU_VANG) (Bắt buộc). |
| Tên địa bàn | Textfield – String | Nhập tên chính thức của đơn vị hành chính (VD: Huyện Phú Vang) (Bắt buộc). |
| Cấp địa bàn | Combobox | Lựa chọn phân cấp hành chính: Tỉnh/Thành phố, Quận/Huyện, Phường/Xã (Bắt buộc). |
| Trực thuộc | Combobox | Lựa chọn địa bàn cấp trên trực thuộc (Vô hiệu hóa nếu cấp địa bàn là Tỉnh/Thành phố; Bắt buộc điền nếu chọn cấp Quận/Huyện hoặc Phường/Xã). |
| Ghi chú | Textarea | Nhập các thông tin diễn giải hoặc lưu ý thêm (Không bắt buộc). |
| Trạng thái hiển thị | Toggle / Switch | Bật/Tắt trạng thái hoạt động của địa bàn (Mặc định: Đang sử dụng). |
| Nút Lưu lại | Button (Success) | Nhấn để đóng gói dữ liệu và thực hiện gửi yêu cầu lưu vào hệ thống. |
| Nút Hủy bỏ | Button (Secondary) | Nhấn để đóng biểu mẫu, không lưu dữ liệu và quay lại trang danh sách. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Lưu dữ liệu** | Hệ thống kiểm tra tính hợp lệ của dữ liệu đầu vào và ghi nhận vào CSDL. | Kích hoạt luồng "Thêm thành công", hiển thị Popup thông báo và lưu bản ghi vào CSDL. | Kích hoạt luồng "Thêm thất bại", hiển thị thông báo lỗi chi tiết trên màn hình. |
| **Hủy thao tác** | Thoát khỏi biểu mẫu thêm mới hiện tại. | Hệ thống hủy bỏ mọi thông tin đang nhập dở, quay về màn hình Danh sách danh mục địa bàn. | (Không có) |

#### c. Thêm thành công

<p align="center"><i>Hình 10: Thông báo thêm địa bàn thành công (Popup)</i></p>

| **Màn hình** | **Thông báo thêm địa bàn thành công (Popup)** |
| :--- | :--- |
| **Mô tả** | Hộp thoại (Modal/Popup) xuất hiện ở trung tâm màn hình sau khi hệ thống lưu thành công bản ghi địa bàn mới vào CSDL. |
| **Màn hình kết nối** | Danh sách Danh mục Địa bàn (Sau khi đóng popup) |

**Nội dung màn hình (Main Content):**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Biểu tượng thành công | Icon | Hình ảnh dấu Checkmark (✓) màu xanh lá cây chuyển động nhẹ. |
| Tiêu đề thông báo | Text (Static) | Dòng chữ in đậm: "Thành công!" |
| Nội dung chi tiết | Text (Static) | Dòng chữ: "Thêm mới danh mục địa bàn thành công." |
| Nút Xác nhận / Đóng | Button (Primary) | Nút bấm để người dùng xác nhận đã nắm thông tin và đóng hộp thoại. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Đóng hộp thoại** | Tắt popup thông báo và làm mới lại giao diện nền. | Hộp thoại biến mất, hệ thống điều hướng người dùng quay lại màn hình Danh sách địa bàn, bảng dữ liệu tự động cập nhật bản ghi mới ở dòng đầu tiên. | (Không có) |

#### d. Thêm thất bại

<p align="center"><i>Hình 11: Thông báo thêm địa bàn thất bại / Cảnh báo lỗi (Popup)</i></p>

| **Màn hình** | **Thông báo thêm địa bàn thất bại / Cảnh báo lỗi (Popup)** |
| :--- | :--- |
| **Mô tả** | Hộp thoại xuất hiện khi hệ thống phát hiện dữ liệu nhập vào không hợp lệ hoặc trùng lặp mã định danh trong cơ sở dữ liệu. |
| **Màn hình kết nối** | Thêm mới Địa bàn (Giữ nguyên biểu mẫu để người dùng chỉnh sửa) |

**Nội dung màn hình (Main Content):**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Biểu tượng lỗi | Icon | Biểu tượng dấu chấm than (!) nằm trong hình tam giác hoặc dấu X màu đỏ. |
| Tiêu đề cảnh báo | Text (Static) | Dòng chữ in đậm màu đỏ: "Lỗi dữ liệu!" hoặc "Cảnh báo!" |
| Nội dung lỗi chi tiết | Text (Dynamic) | Hiển thị nội dung lỗi tương ứng: "Mã địa bàn đã tồn tại trên hệ thống, vui lòng nhập mã khác" hoặc "Vui lòng nhập đầy đủ các trường thông tin bắt buộc". |
| Nút Đóng / Thử lại | Button (Danger) | Nút bấm tắt hộp thoại lỗi để người dùng tiếp tục thao tác chỉnh sửa thông tin. |
| Đánh dấu đỏ trường lỗi | UI Highlight | Viền các ô nhập liệu bị lỗi (ví dụ: ô Mã địa bàn bị trùng) sẽ đổi sang màu đỏ để người dùng dễ nhận biết. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Tắt cảnh báo lỗi** | Đóng hộp thoại thông báo lỗi để quay lại sửa biểu mẫu nhập dữ liệu. | Hộp thoại đóng lại, toàn bộ dữ liệu người dùng đã nhập trên biểu mẫu "Thêm mới Địa bàn" được giữ nguyên, tập trung con trỏ chuột vào trường lỗi. | (Không có) |

#### e. Sửa địa bàn

<p align="center"><i>Hình 12: Giao diện Chỉnh sửa địa bàn</i></p>

| **Màn hình** | **Chỉnh sửa Địa bàn** |
| :--- | :--- |
| **Mô tả** | Biểu mẫu cho phép Quản trị viên thay đổi các thông tin chi tiết (Tên địa bàn, cấp, đơn vị trực thuộc, trạng thái) của một đơn vị hành chính đã tồn tại trong hệ thống. |
| **Màn hình kết nối** | Danh sách Danh mục Địa bàn |

**Nội dung màn hình (Main Content):**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Mã địa bàn | Textfield – String | Hiển thị mã địa bàn hiện tại của bản ghi. Thuộc tính: **Read-only** (Khóa, không cho phép thay đổi để đảm bảo toàn vẹn dữ liệu gốc). |
| Tên địa bàn | Textfield – String | Hiển thị tên địa bàn hiện tại, cho phép người dùng xóa đi nhập lại tên mới. |
| Cấp địa bàn | Combobox | Hiển thị cấp hiện tại, cho phép chọn lại cấp hành chính khác nếu cần. |
| Trực thuộc | Combobox | Hiển thị đơn vị cấp trên hiện tại, cho phép bấm chọn thay đổi đơn vị quản lý trực tiếp. |
| Ghi chú | Textarea | Hiển thị ghi chú cũ, hỗ trợ cập nhật nội dung mô tả thêm. |
| Trạng thái hiển thị | Toggle / Switch | Chuyển đổi trạng thái hoạt động (Đang sử dụng <-> Ngừng sử dụng). |
| Nút Cập nhật | Button (Success) | Gửi lệnh yêu cầu lưu đè các thông tin thay đổi vào cơ sở dữ liệu. |
| Nút Hủy bỏ | Button (Secondary) | Thoát khỏi màn hình chỉnh sửa, bỏ qua các thay đổi và quay lại danh sách. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Cập nhật dữ liệu** | Hệ thống lưu các thông tin chỉnh sửa mới vào CSDL dựa trên Mã địa bàn. | Thay đổi được cập nhật thành công, hiển thị thông báo popup báo tin vui và tự động chuyển về trang Danh sách địa bàn. | Người dùng xóa trống trường Tên địa bàn rồi bấm cập nhật $
ightarrow$ Hệ thống chặn lại, viền đỏ ô nhập liệu và báo lỗi "Tên địa bàn không được để trống". |
| **Hủy bỏ chỉnh sửa** | Click nút Hủy để hủy thao tác sửa đổi. | Hệ thống không ghi nhận thay đổi, quay trở về giao diện màn hình danh sách gốc. | (Không có) |

#### f. Xóa địa bàn

<p align="center"><i>Hình 13: Xóa Địa bàn (Popup Xác nhận xóa)</i></p>

| **Màn hình** | **Xóa Địa bàn (Popup Xác nhận xóa)** |
| :--- | :--- |
| **Mô tả** | Hộp thoại cảnh báo mức độ nguy hiểm xuất hiện khi Admin nhấn vào icon Xóa tại một dòng trên bảng danh sách, nhằm yêu cầu xác nhận chắc chắn trước khi xóa dữ liệu vĩnh viễn. |
| **Màn hình kết nối** | Danh sách Danh mục Địa bàn |

**Nội dung màn hình (Main Content):**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Tiêu đề popup | Text (Static) | Dòng chữ cảnh báo: "Xác nhận xóa danh mục địa bàn" |
| Nội dung cảnh báo | Text (Dynamic) | Chuỗi nội dung động: "Bạn có chắc chắn muốn xóa địa bàn **[Tên_Địa_Bàn]** ra khỏi hệ thống? Hành động này không thể hoàn tác. *Lưu ý: Hệ thống không cho phép xóa nếu địa bàn này đang chứa các địa bàn cấp dưới hoặc đang có cơ sở du lịch trực thuộc.*" |
| Nút Xác nhận xóa | Button (Danger - Đỏ) | Thực thi lệnh xóa vĩnh viễn bản ghi dữ liệu khỏi hệ thống. |
| Nút Hủy bỏ | Button (Secondary) | Đóng popup, bảo toàn dữ liệu bản ghi địa bàn. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Xác nhận xóa** | Hệ thống kiểm tra ràng buộc khóa ngoại và thực hiện xóa bản ghi. | Bản ghi được xóa khỏi CSDL, popup đóng lại, màn hình danh sách cập nhật (biến mất dòng vừa xóa) và hiển thị Toast thông báo thành công. | Bản ghi đang có ràng buộc dữ liệu con $
ightarrow$ Hệ thống không xóa, giữ nguyên bản ghi và thông báo lỗi: "Không thể xóa do địa bàn đang có dữ liệu trực thuộc hoặc đang có cơ sở kinh doanh đăng ký". |

---

### 3.3.2 Doanh nghiệp

| **Tên Use case** | **Quản lý danh mục và thông tin Doanh nghiệp** |
| :--- | :--- |
| **Mô tả** | Hỗ trợ Quản trị viên quản lý danh mục Loại hình doanh nghiệp, theo dõi hồ sơ tập trung, thực hiện thẩm định xét duyệt hồ sơ tự khai báo của các doanh nghiệp du lịch trên địa bàn thành phố Huế. |
| **Tác nhân** | Quản trị viên hệ thống (Admin), Người dùng Doanh nghiệp |
| **Độ phức tạp** | 🔲 Đơn giản  ☑️ Trung bình  🔲 Phức tạp |
| **Điều kiện bắt đầu** | Người dùng đăng nhập thành công vào hệ thống quản trị với vai trò hợp lệ. |
| **Điều kiện kết thúc** | Hồ sơ doanh nghiệp được số hóa, chuẩn hóa phân loại, phê duyệt trạng thái hợp lệ và lưu trữ vào Cơ sơ dữ liệu du lịch tập trung. |

#### a. Danh sách Loại doanh nghiệp

<p align="center"><i>Hình 14: Giao diện Danh sách Loại hình doanh nghiệp du lịch</i></p>

| **Màn hình** | **Danh sách Loại hình doanh nghiệp du lịch** |
| :--- | :--- |
| **Mô tả** | Màn hình dành cho Admin theo dõi, phân loại và cấu hình các nhóm ngành nghề/loại hình doanh nghiệp du lịch chính (Lưu trú, Lữ hành, Dịch vụ ẩm thực, Mua sắm...). |
| **Màn hình kết nối** | Màn hình danh sách Hồ sơ doanh nghiệp |

**Nội dung màn hình (Main Content):**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Bộ lọc Loại hình chính | Combobox | Chọn phân loại ngành nghề lớn để lọc dữ liệu hiển thị (Mặc định: Tất cả loại hình). |
| Nút Thêm Mới Loại hình | Button (Primary) | Bấm để mở form tạo mới một danh mục loại hình doanh nghiệp du lịch. |
| Khối thống kê tổng số loại hình | Card – Number | Ô hiển thị tổng số lượng phân loại doanh nghiệp hiện hành (Ví dụ: 3). |
| Khối thống kê tổng số doanh nghiệp | Card – Number | Ô hiển thị tổng số lượng doanh nghiệp đang đăng ký trên toàn hệ thống (Ví dụ: 23). |
| Bảng danh mục loại hình | Table | Bảng hiển thị thông tin danh mục loại hình. |
| *STT* | Label – Number | Số thứ tự dòng. |
| *Mã loại hình* | Label – String | Hệ thống tự động sinh chuỗi định danh duy nhất (VD: LH_LUUTRU, LH_LUHANH). |
| *Tên loại hình doanh nghiệp* | Label – String | Tên gọi phân loại doanh nghiệp (VD: Doanh nghiệp Lưu trú, Đơn vị Lữ hành, Dịch vụ du lịch). |
| *Thao tác* | Icon Buttons | Icon Sửa thông tin danh mục hoặc Xóa phân loại ngành nghề (chỉ xóa được khi không có doanh nghiệp trực thuộc). |
| Bộ nút phân trang | Pagination | Các nút điều hướng chuyển trang dữ liệu. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Xem và Lọc danh mục** | Tải danh mục loại hình và thực hiện lọc dữ liệu theo Combobox lựa chọn. | Bảng dữ liệu cập nhật hiển thị chính xác các dòng thông tin phân loại thỏa mãn điều kiện. | Lỗi kết nối CSDL, hệ thống báo lỗi không tải được cấu hình. |

#### b. Xem chi tiết doanh nghiệp

<p align="center"><i>Hình 15: Giao diện Danh sách Hồ sơ doanh nghiệp và Xem chi tiết</i></p>

| **Màn hình** | **Danh sách Hồ sơ doanh nghiệp và Xem chi tiết** |
| :--- | :--- |
| **Mô tả** | Màn hình danh sách tập trung quản lý hồ sơ pháp nhân của tất cả các doanh nghiệp du lịch trên địa bàn thành phố, cho phép tìm kiếm nhanh và bấm xem chi tiết thông tin, trạng thái hoạt động của doanh nghiệp. |
| **Màn hình kết nối** | Danh sách Loại doanh nghiệp, Màn hình Phê duyệt thông tin doanh nghiệp |

**Nội dung màn hình (Main Content):**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Thanh tìm kiếm doanh nghiệp | Textfield – String | Ô nhập từ khóa tra cứu doanh nghiệp theo Tên doanh nghiệp hoặc Mã số thuế (MST). |
| Combobox chọn Loại hình | Combobox | Lọc nhanh danh sách doanh nghiệp theo mảng hoạt động (Tất cả, Lưu trú, Lữ hành, Ăn uống...). |
| Bảng hồ sơ doanh nghiệp | Table | Bảng hiển thị thông tin tổng quan của các doanh nghiệp du lịch. |
| *STT* | Label – Number | Số thứ tự. |
| *Mã số thuế / Mã DN* | Label – String | Mã số doanh nghiệp/Mã số thuế chính thức do cơ quan thẩm quyền cấp (VD: 268935677). |
| *Tên doanh nghiệp* | Label – String | Tên thương mại hoặc pháp nhân đầy đủ (VD: Khách sạn Imperial Huế, Công ty Vietravel Huế). |
| *Địa chỉ trụ sở* | Label – String | Trụ sở hoạt động chính của doanh nghiệp (VD: 54 Hùng Vương, TP Huế). |
| *Mảng loại hình* | Label – String | Thuộc loại hình doanh nghiệp tương ứng (VD: Lưu trú, Lữ hành). |
| *Trạng thái hồ sơ* | Badge | Nhãn màu thể hiện tiến trình duyệt: Đã duyệt (Xanh), Chưa duyệt (Vàng), Từ chối (Đỏ). |
| *Thao tác* | Icon Buttons | Icon kính lúp (Xem chi tiết hồ sơ), Icon cái khiên (Phê duyệt nhanh), Icon thùng rác (Xóa hồ sơ). |
| Thanh điều hướng phân trang | Pagination | Bộ nút chuyển trang dữ liệu cho bảng hồ sơ. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Tra cứu hồ sơ** | Nhập thông tin tìm kiếm và lọc dữ liệu doanh nghiệp. | Bảng dữ liệu hiển thị danh sách doanh nghiệp khớp với từ khóa và bộ lọc loại hình. | Không có bản ghi nào trùng khớp, bảng trả về dòng chữ "Không có dữ liệu". |
| **Xem chi tiết hồ sơ** | Người dùng nhấn vào icon kính lúp tại dòng doanh nghiệp cụ thể. | Hệ thống mở ra vùng hiển thị (hoặc tab phụ) chứa toàn vẹn thông tin chi tiết: người đại diện, số điện thoại, email, tệp giấy phép kinh doanh đính kèm của doanh nghiệp đó để kiểm tra. | Không tải được thông tin chi tiết do lỗi kết nối mạng. |

#### c. Duyệt doanh nghiệp

<p align="center"><i>Hình 16: Giao diện Phê duyệt thông tin doanh nghiệp</i></p>

| **Màn hình** | **Phê duyệt thông tin doanh nghiệp** |
| :--- | :--- |
| **Mô tả** | Giao diện dành riêng cho tài khoản Quản trị viên thực hiện đối chiếu, kiểm tra tính xác thực các thông tin pháp lý do doanh nghiệp tự khai báo, từ đó ra quyết định Phê duyệt cấp quyền hoặc Từ chối hồ sơ. |
| **Màn hình kết nối** | Màn hình Danh sách Hồ sơ doanh nghiệp |

**Nội dung màn hình (Main Content):**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Mã doanh nghiệp / MST | Label – String | Mã số thuế của doanh nghiệp đang chờ thẩm định (Trực quan, không sửa). |
| Tên doanh nghiệp | Label – String | Tên đơn vị đăng ký hồ sơ thẩm định. |
| Loại hình hoạt động | Label – String | Phân mảng ngành nghề kinh doanh đăng ký. |
| Thông tin người đại diện | Label – String | Hiển thị Họ tên, số CCCD/Hộ chiếu và số điện thoại liên hệ của người đại diện pháp luật. |
| Giấy phép kinh doanh đính kèm | Link / Tệp tin | Liên kết để bấm xem trực tiếp hoặc tải xuống tệp văn bản pháp lý dạng PDF/Hình ảnh. |
| Ảnh minh họa cơ sở | Image Gallery | Vùng hiển thị trực quan các hình ảnh về cơ sở vật chất, logo do doanh nghiệp tải lên hệ thống. |
| Lý do từ chối hồ sơ | Textarea – String | Ô nhập văn bản giải trình lý do không chấp thuận phê duyệt hồ sơ (Bắt buộc nhập nếu bấm nút Từ chối). |
| Nút Phê duyệt | Button (Success) | Nhấn vào để đồng ý hồ sơ, hệ thống cập nhật trạng thái thành "Đã duyệt" và cấp quyền tài khoản. |
| Nút Từ chối | Button (Danger) | Nhấn vào để bác bỏ hồ sơ, hệ thống chuyển trạng thái thành "Từ chối" kèm lý do. |
| Nút Quay lại | Button (Secondary) | Thoát khỏi giao diện kiểm duyệt, quay về màn hình Danh sách hồ sơ doanh nghiệp. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Phê duyệt hồ sơ** | Admin bấm nút Phê duyệt khi thấy mọi thông tin, giấy phép đính kèm đều hợp lệ. | Hồ sơ chuyển sang trạng thái "Đã duyệt", hệ thống tự động gửi email/thông báo kích hoạt tài khoản chính thức cho DN và chuyển về trang danh sách. | Lỗi đồng bộ cơ sở dữ liệu, trạng thái hồ sơ bị giữ nguyên, báo lỗi hệ thống. |
| **Từ chối hồ sơ** | Admin nhập lý do tại ô "Lý do từ chối" và nhấn nút Từ chối. | Hồ sơ chuyển sang trạng thái "Từ chối", lưu lại nội dung lý do phản hồi để hiển thị cho doanh nghiệp chỉnh sửa lại, quay về trang danh sách. | Admin bấm nút Từ chối nhưng bỏ trống ô "Lý do từ chối" $
ightarrow$ Hệ thống ngăn lại, báo đỏ tại ô nhập liệu và hiển thị cảnh báo "Vui lòng nhập lý do từ chối hồ sơ". |

#### d. Khai báo / thêm mới doanh nghiệp

<p align="center"><i>Hình 17: Giao diện Khai báo thông tin doanh nghiệp</i></p>

| **Màn hình** | **Khai báo thông tin doanh nghiệp** |
| :--- | :--- |
| **Mô tả** | Màn hình dành cho đại diện Doanh nghiệp tự kê khai năng lực, thông tin liên hệ, tọa độ và đính kèm hồ sơ pháp lý gửi lên hệ thống (hoặc Admin sử dụng để thêm mới hộ một hồ sơ doanh nghiệp từ trang quản trị). |
| **Màn hình kết nối** | Màn hình quản lý chung / Trang đăng ký ban đầu |

**Nội dung màn hình (Main Content):**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Mã số thuế / Mã doanh nghiệp | Textfield – String | Trường bắt buộc nhập mã số thuế doanh nghiệp làm khóa định danh duy nhất (Bắt buộc). |
| Tên doanh nghiệp chính thức | Textfield – String | Trường nhập tên pháp nhân đầy đủ của doanh nghiệp (Bắt buộc). |
| Lựa chọn Loại hình | Combobox | Lựa chọn mảng ngành nghề hoạt động chính (Lưu trú, Lữ hành, Dịch vụ...). |
| Họ và tên người đại diện | Textfield – String | Nhập tên người đại diện pháp luật của doanh nghiệp (Bắt buộc). |
| Số CCCD / Hộ chiếu | Textfield – Number | Số giấy tờ định danh của người đại diện (Bắt buộc). |
| Số điện thoại liên hệ | Textfield – Number | Số điện thoại di động hoặc hotline giao dịch chính (Bắt buộc). |
| Email doanh nghiệp | Textfield – String | Địa chỉ hòm thư điện tử nhận thông báo từ hệ thống (Bắt buộc). |
| Địa chỉ trụ sở chính | Textfield – String | Nhập số nhà, tên đường và chọn Phường/Xã trực thuộc thành phố Huế (Bắt buộc). |
| Vị trí tọa độ GPS | Map Picker / Text | Xác định vĩ độ (Latitude) và kinh độ (Longitude) trên bản đồ số du lịch để định vị cơ sở thực tế. |
| Tải lên Giấy phép kinh doanh | Upload Button | Nút bấm để tải lên tệp hồ sơ pháp lý minh chứng (Định dạng cho phép: .pdf, .jpg, .png; tối đa 10MB) (Bắt buộc). |
| Ảnh đại diện / Logo cơ sở | Upload Button | Tải lên hình ảnh quảng bá, ảnh cổng cơ sở vật chất của đơn vị (Không bắt buộc). |
| Giới thiệu / Mô tả ngắn | Textarea | Đoạn văn bản mô tả khái quát đặc điểm nổi bật, dịch vụ cung cấp của doanh nghiệp. |
| Nút Gửi phê duyệt | Button (Primary) | Đóng gói toàn bộ thông tin đã điền và tệp đính kèm gửi lên hàng đợi thẩm duyệt của Admin. |
| Nút Làm lại | Button (Secondary) | Xóa sạch nội dung ở tất cả các trường thông tin vừa nhập để thiết lập lại từ đầu. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Gửi hồ sơ khai báo** | Thực hiện nhấn nút "Gửi phê duyệt" để nộp hồ sơ lên hệ thống CSDL. | Hệ thống lưu trữ dữ liệu tạm thời, đặt trạng thái hồ sơ là "Chưa duyệt", đưa vào hàng đợi thẩm định của Admin và thông báo "Nộp hồ sơ khai báo thành công!". | Người dùng bỏ trống một trong các trường bắt buộc hoặc tệp đính kèm sai định dạng $
ightarrow$ Hệ thống giữ nguyên biểu mẫu, báo lỗi viền đỏ tại các trường thiếu sót và yêu cầu hoàn thiện. |

---

### 3.3.3 Loại hình lưu trú

| **Tên Use case** | **Quản lý danh mục Loại hình lưu trú** |
| :--- | :--- |
| **Mô tả** | Quản trị viên hệ thống thực hiện xem danh sách, tra cứu và quản lý các phân loại hình thức lưu trú du lịch (Khách sạn, Biệt thự du lịch, Homestay, Resort, Villa...) dùng làm danh mục gốc phân loại cơ sở dữ liệu. |
| **Tác nhân** | Quản trị viên hệ thống (Admin) |
| **Độ phức tạp** | ☑️ Đơn giản  🔲 Trung bình  🔲 Phức tạp |
| **Điều kiện bắt đầu** | Người dùng đăng nhập tài khoản Admin thành công và truy cập menu "Quản lý danh mục" &rarr; "Loại hình lưu trú". |
| **Điều kiện kết thúc** | Danh sách các loại hình lưu trú được kết xuất hiển thị chính xác và đầy đủ phục vụ công tác quản lý. |

#### a. Danh sách loại hình lưu trú

<p align="center"><i>Hình 18: Giao diện Danh sách Loại hình lưu trú</i></p>

| **Màn hình** | **Danh sách Loại hình lưu trú** |
| :--- | :--- |
| **Mô tả** | Giao diện hiển thị danh mục tập trung của các nhóm phân loại cơ sở lưu trú du lịch đang được áp dụng trên cổng dữ liệu toàn thành phố. |
| **Màn hình kết nối** | (Không có biểu mẫu Thêm/Sửa chi tiết riêng biệt, các thao tác được thực hiện trực tiếp trên bảng hoặc biểu mẫu popup thu gọn) |

**Nội dung màn hình (Main Content):**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Ô tìm kiếm loại hình | Textfield – String | Ô nhập từ khóa để tìm nhanh loại hình lưu trú theo tên gọi hoặc mã phân loại. |
| Nút Thêm Mới loại hình | Button (Primary) | Nút bấm để kích hoạt luồng khởi tạo thêm một loại hình lưu trú mới vào hệ thống. |
| Khối thống kê tổng số loại | Card – Number | Khối hiển thị tổng số lượng phân loại lưu trú hiện có trên hệ thống (Ví dụ: 5). |
| Khối thống kê tổng số cơ sở | Card – Number | Khối hiển thị tổng số lượng cơ sở lưu trú thực tế đang hoạt động thuộc mọi nhóm (Ví dụ: 23). |
| Bảng dữ liệu loại hình lưu trú | Table | Khung hiển thị danh sách dạng hàng và cột chứa thông tin danh mục. |
| *STT* | Label – Number | Số thứ tự dòng. |
| *Mã loại hình lưu trú* | Label – String | Mã định danh hệ thống duy nhất của loại hình (VD: LH_HOTEL, LH_HOMESTAY). |
| *Tên loại hình lưu trú* | Label – String | Tên gọi chuẩn hóa của loại hình kinh doanh lưu trú (VD: Khách sạn, Homestay, Resort, Nhà nghỉ). |
| *Mô tả ngắn* | Label – String | Diễn giải khái quát về đặc điểm phân loại loại hình lưu trú này. |
| *Thao tác* | Icon Buttons | Biểu tượng Sửa (Hình bút) hoặc Xóa (Hình thùng rác) bản ghi danh mục gốc. |
| Thanh điều hướng trang | Pagination | Bộ nút phân trang dữ liệu (1, 2, 3...) giúp di chuyển xem danh sách bản ghi lớn. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Tải hiển thị dữ liệu** | Hệ thống tự động truy vấn CSDL và đẩy dữ liệu lên bảng khi vào trang. | Bảng dữ liệu loại hình lưu trú kết xuất đầy đủ thông tin, các thẻ thống kê cập nhật số liệu chính xác. | Lỗi kết nối CSDL, hiển thị màn hình trống và cảnh báo lỗi. |
| **Tìm kiếm loại hình** | Nhập từ khóa vào ô tìm kiếm và nhấn Enter hoặc icon kính lúp. | Bảng tự động làm mới, chỉ giữ lại các dòng loại hình lưu trú chứa từ khóa tìm kiếm. | Từ khóa không khớp với bất kỳ bản ghi nào $
ightarrow$ Bảng trả về trạng thái trống rỗng. |

---

### 3.3.4 Loại hình dịch vụ

| **Tên Use case** | **Quản lý danh mục Loại hình dịch vụ** |
| :--- | :--- |
| **Mô tả** | Quản trị viên hệ thống thực hiện theo dõi, quản lý, tra cứu phân loại các dịch vụ du lịch (Lữ hành, Ăn uống, Mua sắm, Vận chuyển, Vui chơi...) nhằm phục vụ đồng bộ dữ liệu cho phân hệ quản lý nghiệp vụ kinh doanh. |
| **Tác nhân** | Quản trị viên hệ thống (Admin) |
| **Độ phức tạp** | ☑️ Đơn giản  🔲 Trung bình  🔲 Phức tạp |
| **Điều kiện bắt đầu** | Admin đăng nhập tài khoản quản trị thành công và truy cập menu "Quản lý danh mục" &rarr; "Loại hình dịch vụ". |
| **Điều kiện kết thúc** | Danh sách phân loại dịch vụ du lịch kết xuất hiển thị chính xác theo yêu cầu quản trị. |

#### a. Danh sách loại hình dịch vụ

<p align="center"><i>Hình 19: Giao diện Danh sách Loại hình dịch vụ du lịch</i></p>

| **Màn hình** | **Danh sách Loại hình dịch vụ du lịch** |
| :--- | :--- |
| **Mô tả** | Màn hình quản lý hiển thị danh sách tập trung các danh mục phân loại dịch vụ phục vụ du khách trên địa bàn. |
| **Màn hình kết nối** | (Không có biểu mẫu chi tiết riêng, hỗ trợ các thao tác sửa đổi trực tiếp hoặc qua popup) |

**Nội dung màn hình (Main Content):**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Ô tìm kiếm nhanh dịch vụ | Textfield – String | Nhập ký tự để tra cứu nhanh loại hình dịch vụ du lịch theo tên gọi hoặc mã dịch vụ. |
| Nút Thêm Mới dịch vụ | Button (Primary) | Nút bấm dùng để tạo thêm phân loại dịch vụ du lịch mới vào hệ thống danh mục gốc. |
| Thẻ Tổng số loại hình | Card – Number | Khối đếm tổng số lượng loại hình dịch vụ du lịch được cấu hình trên hệ thống (Ví dụ: 5). |
| Thẻ Tổng số cơ sở cung cấp | Card – Number | Khối đếm tổng số lượng cơ sở kinh doanh dịch vụ đang hoạt động thực tế (Ví dụ: 35). |
| Bảng loại hình dịch vụ | Table | Bảng dữ liệu hiển thị danh mục các loại hình dịch vụ. |
| *STT* | Label – Number | Số thứ tự dòng. |
| *Mã loại dịch vụ* | Label – String | Chuỗi ký tự định danh mã loại dịch vụ hệ thống (VD: DV_LUHANH, DV_ANUONG). |
| *Tên loại dịch vụ* | Label – String | Tên gọi chuẩn hóa của loại hình dịch vụ (VD: Đơn vị lữ hành, Dịch vụ ẩm thực, Điểm mua sắm, Vận chuyển du khách). |
| *Thao tác hành động* | Icon Buttons | Biểu tượng Sửa (Cập nhật tên/mô tả) hoặc Xóa (Gỡ bỏ danh mục nếu không bị ràng buộc bản ghi). |
| Phân trang danh sách | Pagination | Thanh điều hướng chuyển đổi giữa các trang dữ liệu của bảng phân loại dịch vụ. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Xem danh sách & Tìm kiếm** | Thực hiện hiển thị danh mục và lọc dữ liệu động theo từ khóa tìm kiếm. | Bảng dữ liệu kết xuất chính xác danh sách các bản ghi loại dịch vụ phù hợp với điều kiện lọc. | Không tìm thấy kết quả trùng khớp với từ khóa, bảng hiển thị thông báo rỗng. |

---

### 3.3.5 Loại hình điểm đến

| **Tên Use case** | **Quản lý danh mục Loại hình điểm đến** |
| :--- | :--- |
| **Mô tả** | Cho phép Quản trị viên quản lý danh mục phân loại các địa điểm tham quan du lịch (Di tích lịch sử - văn hóa, Điểm du lịch tâm linh, Danh lam thắng cảnh, Khu vui chơi giải trí...) phục vụ gán nhãn dữ liệu bản đồ số. |
| **Tác nhân** | Quản trị viên hệ thống (Admin) |
| **Độ phức tạp** | ☑️ Đơn giản  🔲 Trung bình  🔲 Phức tạp |
| **Điều kiện bắt đầu** | Admin đăng nhập tài khoản thành công và chọn menu "Quản lý danh mục" &rarr; "Loại hình điểm đến". |
| **Điều kiện kết thúc** | Thông tin danh mục loại hình điểm đến hiển thị trực quan, đầy đủ phục vụ công tác rà soát thông tin. |

#### a. Danh sách loại hình điểm đến

<p align="center"><i>Hình 20: Giao diện Danh sách Loại hình điểm đến du lịch</i></p>

| **Màn hình** | **Danh sách Loại hình điểm đến du lịch** |
| :--- | :--- |
| **Mô tả** | Giao diện hiển thị danh mục các loại hình điểm đến du lịch được số hóa phục vụ phân cấp dữ liệu hiển thị cho ứng dụng di động du khách. |
| **Màn hình kết nối** | (Thao tác quản trị trực tiếp trên trang hoặc thông qua popup biểu mẫu ngắn) |

**Nội dung màn hình (Main Content):**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Bộ lọc Combobox nhanh | Combobox | Lọc nhanh danh sách phân loại điểm đến theo nhóm lớn. |
| Nút Thêm Mới điểm đến | Button (Primary) | Nhấn nút bấm để thực hiện thêm mới một danh mục phân loại điểm đến du lịch. |
| Bảng điểm đến du lịch | Table | Bảng hiển thị danh sách các phân loại điểm đến hiện có. |
| *STT* | Label – Number | Số thứ tự dòng. |
| *Mã phân loại điểm đến* | Label – String | Chuỗi ký tự định danh duy nhất của danh mục điểm đến (VD: DD_DITICH, DD_TAMLINH). |
| *Tên loại hình điểm đến* | Label – String | Tên danh mục phân loại điểm đến chuẩn hóa (VD: Di tích lịch sử - văn hóa, Danh lam thắng cảnh, Điểm du lịch cộng đồng). |
| *Thao tác quản trị* | Icon Buttons | Icon Sửa (Thay đổi tên phân loại) hoặc Icon Xóa (Xóa danh mục khỏi hệ thống nếu không chứa điểm đến nào). |
| Thanh phân trang danh sách | Pagination | Bộ nút bấm hỗ trợ điều hướng trang bảng dữ liệu (1, 2, 3...). |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Xem danh sách phân loại** | Hệ thống tải dữ liệu danh mục khi người dùng truy cập vào trang. | Danh sách hiển thị đầy đủ, chính xác thông tin cấu hình phân loại từ cơ sở dữ liệu gốc. | Lỗi mạng hoặc máy chủ không phản hồi, không kết xuất được dữ liệu lên bảng. |

---

### 3.3.6 Các tiện ích

| **Tên Use case** | **Quản lý danh mục Các tiện ích** |
| :--- | :--- |
| **Mô tả** | Quản lý danh mục các dịch vụ giá trị gia tăng, tiện ích đi kèm của cơ sở du lịch (Wifi miễn phí, Hồ bơi, Chỗ đỗ xe, Thang máy, Spa, Gym...) phục vụ đồng bộ hiển thị biểu tượng icon tiện ích trên ứng dụng di động du khách. |
| **Tác nhân** | Quản trị viên hệ thống (Admin) |
| **Độ phức tạp** | ☑️ Đơn giản  🔲 Trung bình  🔲 Phức tạp |
| **Điều kiện bắt đầu** | Quản trị viên hệ thống truy cập vào menu "Quản lý danh mục" &rarr; "Các tiện ích". |
| **Điều kiện kết thúc** | Danh sách tiện ích cùng biểu tượng đại diện được hiển thị trực quan và chính xác trên bảng quản trị. |

#### a. Danh sách loại hình tiện ích

<p align="center"><i>Hình 21: Giao diện Danh sách Danh mục Các tiện ích</i></p>

| **Màn hình** | **Danh sách Danh mục Các tiện ích** |
| :--- | :--- |
| **Mô tả** | Giao diện quản lý danh sách các tiện ích dịch vụ đính kèm cùng biểu tượng hình ảnh (icon) đại diện phục vụ việc hiển thị lọc tính năng trên bản đồ số du lịch. |
| **Màn hình kết nối** | (Thao tác quản trị trực tiếp hoặc thông qua popup thêm/sửa tiện ích) |

**Nội dung màn hình (Main Content):**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Tìm kiếm tiện ích | Textfield – String | Ô nhập từ khóa để lọc nhanh tiện ích dịch vụ theo tên gọi (VD: Wifi, Hồ bơi, Điều hòa). |
| Nút Thêm Mới tiện ích | Button (Primary) | Nút bấm kích hoạt mở form/popup để tạo mới một nhãn tiện ích dịch vụ. |
| Bảng danh mục tiện ích | Table | Khung hiển thị danh sách các nhãn tiện ích hiện hành trên hệ thống. |
| *STT* | Label – Number | Số thứ tự dòng. |
| *Biểu tượng (Icon)* | Icon / Image | Hình ảnh icon đại diện thu nhỏ đại diện cho tiện ích hiển thị trên bản đồ/ứng dụng (VD: Biểu tượng sóng sóng cho Wifi). |
| *Tên tiện ích* | Label – String | Tên gọi chuẩn hóa của tiện ích dịch vụ (VD: Wifi miễn phí, Hồ bơi ngoài trời, Massage & Spa, Chỗ đỗ xe ô tô). |
| *Mô tả chi tiết* | Label – String | Đoạn văn bản ngắn diễn giải ngắn gọn về nội dung hoặc tiêu chí áp dụng tiện ích này. |
| *Thao tác* | Icon Buttons | Bộ nút icon chức năng Sửa thông tin tiện ích hoặc Xóa tiện ích khỏi danh mục gốc của hệ thống. |
| Thanh điều hướng phân trang | Pagination | Bộ nút điều hướng chuyển đổi xem dữ liệu theo trang (1, 2, 3...). |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Tìm kiếm & Lọc tiện ích** | Người dùng nhập ký tự tìm kiếm vào ô nhập liệu để lọc bảng dữ liệu. | Bảng dữ liệu tự động cập nhật kết quả lọc, chỉ hiển thị các dòng tiện ích thỏa mãn từ khóa. | Từ khóa không tồn tại, bảng hiển thị trạng thái trống. |
| **Điều hướng phân trang** | Bấm nút chuyển đổi trang danh sách tiện ích trên thanh Pagination. | Bảng dữ liệu tự động truy vấn và tải danh sách bản ghi mới tương ứng với số trang được click chọn. | Lỗi đường truyền, bảng giữ nguyên trang cũ và báo lỗi tải dữ liệu. |


---

## 3.4 QUẢN LÝ LƯU TRÚ

| **Tên Use case** | **Quản lý lưu trú** |
| :--- | :--- |
| **Mô tả** | Chuyên viên quản lý nghiệp vụ hoặc doanh nghiệp thực hiện xem danh sách, tìm kiếm, lọc, thêm mới, cập nhật thông tin, xóa và phê duyệt thông tin các cơ sở lưu trú du lịch trên địa bàn tỉnh/thành phố. |
| **Tác nhân** | Chuyên viên quản lý nghiệp vụ, Doanh nghiệp lưu trú |
| **Độ phức tạp** | 🔲 Đơn giản  🔲 Trung bình  ☑️ Phức tạp |
| **Điều kiện bắt đầu** | Người dùng có thẩm quyền đã đăng nhập thành công vào phân hệ quản trị hệ thống CSDL Du lịch Huế. |
| **Điều kiện kết thúc** | Hệ thống cập nhật trạng thái hoặc dữ liệu thành công. |

### a. Danh sách cơ sở lưu trú

*Hình 22.1: Giao diện Danh sách cơ sở lưu trú*

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

*Hình 23.2: Giao diện Xem chi tiết cơ sở lưu trú*

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

*Hình 24.3: Giao diện Thêm cơ sở lưu trú*

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

*Hình 25.4: Giao diện Sửa cơ sở lưu trú*

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

*Hình 26.5: Giao diện Xóa cơ sở lưu trú (Popup)*

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

*Hình 27.6: Giao diện Phê duyệt cơ sở lưu trú*

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

*Hình 28.7: Giao diện Từ chối phê duyệt (Popup)*

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

*Hình 29.1: Giao diện Danh sách đơn vị lữ hành*

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

*Hình 30.2: Giao diện Xem chi tiết đơn vị lữ hành*

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

*Hình 31.3: Giao diện Danh sách hướng dẫn viên*

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

*Hình 32.4: Giao diện Xem chi tiết hướng dẫn viên*

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

*Hình 33.5: Giao diện Danh sách tour du lịch*

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

*Hình 34.6: Giao diện Xem chi tiết tour du lịch*

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

*Hình 35.1: Giao diện Danh sách quán ăn và mua sắm*

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

*Hình 36.2: Giao diện Xem chi tiết quán ăn và mua sắm*

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

*Hình 37.1: Giao diện Danh sách điểm đến*

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

*Hình 38.2: Giao diện Xem chi tiết điểm đến*

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

*Hình 39.1: Giao diện Danh sách lễ hội và sự kiện*

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

*Hình 40.2: Giao diện Xem chi tiết lễ hội và sự kiện*

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

*Hình 41.1: Giao diện Quản lý phản hồi (Dành cho QTV)*

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

*Hình 42.2: Giao diện Quản lý phản hồi (Dành cho Doanh nghiệp)*

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

*Hình 43.1: Giao diện Tìm kiếm tổng hợp toàn hệ thống*

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

*Hình 44.1: Giao diện Quản lý cấu hình API hệ thống*

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

*Hình 45.1: Giao diện Báo cáo thống kê Dashboard*

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
