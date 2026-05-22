
## 3.3 QUẢN LÝ DANH MỤC HỆ THỐNG
Phân hệ Quản lý danh mục hệ thống cung cấp công cụ cho phép Quản trị viên chuẩn hóa, thiết lập và quản lý toàn bộ dữ liệu danh mục gốc (địa bàn hành chính, các loại hình lưu trú, dịch vụ, điểm đến, tiện ích) và thông tin đăng ký hoạt động của các doanh nghiệp du lịch trên địa bàn tỉnh/thành phố. Đây là dữ liệu nền tảng phục vụ phân cấp và liên kết thông tin cho tất cả các nghiệp vụ khác trong hệ thống CSDL Du lịch.

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
