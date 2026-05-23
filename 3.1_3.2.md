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

![Hình 3.1: Form đăng nhập hệ thống](09_Đăng Nhập.png)
<p align="center"><i>Hình 3.1: Form đăng nhập hệ thống</i></p>

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

<p align="center"><i>Hình 3.2: Giao diện Danh sách người dùng</i></p>

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

<p align="center"><i>Hình 3.3: Giao diện Thông tin chi tiết người dùng</i></p>

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

<p align="center"><i>Hình 3.4: Giao diện Thêm mới người dùng</i></p>

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

<p align="center"><i>Hình 3.5: Giao diện Chỉnh sửa thông tin người dùng</i></p>

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

<p align="center"><i>Hình 3.6: Giao diện Xóa người dùng</i></p>

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

