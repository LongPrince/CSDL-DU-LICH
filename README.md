### **3.4 QUẢN LÝ LƯU TRÚ**

| **Tên Use case** | **Quản lý lưu trú** |
| :--- | :--- |
| **Mô tả** | Chuyên viên quản lý nghiệp vụ hoặc doanh nghiệp thực hiện xem danh sách, tìm kiếm, lọc, thêm mới, cập nhật thông tin và xóa thông tin các cơ sở lưu trú du lịch trên địa bàn tỉnh/thành phố. |
| **Tác nhân** | Chuyên viên quản lý nghiệp vụ, Quản trị viên hệ thống, Doanh nghiệp lưu trú |
| **Độ phức tạp** | 🔲 Đơn giản  🔲 Trung bình  ☑️ Phức tạp |
| **Điều kiện bắt đầu** | Người dùng có thẩm quyền đã đăng nhập thành công vào phân hệ quản trị hệ thống CSDL Du lịch Huế. |
| **Điều kiện kết thúc** | Thông tin cơ sở lưu trú được cập nhật, lưu trữ thành công vào cơ sở dữ liệu hệ thống hoặc hành động hủy bỏ được thực hiện. |
| **Kịch bản chính** | 1. Người dùng chọn chức năng "Cơ sở lưu trú" tại menu Quản lý nghiệp vụ. Hệ thống tải và hiển thị danh sách cơ sở lưu trú (có phân trang, hỗ trợ tìm kiếm theo tên và lọc theo địa bàn, loại hình, trạng thái).<br>2. **Thêm mới**: Người dùng click "Thêm cơ sở lưu trú mới" $\rightarrow$ Nhập đầy đủ thông tin (tên, loại hình, địa chỉ, số phòng, tiện ích, hình ảnh...) $\rightarrow$ Nhấn "Lưu lại" $\rightarrow$ Hệ thống kiểm tra hợp lệ và lưu dữ liệu.<br>3. **Chỉnh sửa**: Người dùng click vào icon sửa tại dòng dữ liệu $\rightarrow$ Hệ thống tải thông tin cũ lên biểu mẫu $\rightarrow$ Người dùng thay đổi thông tin $\rightarrow$ Nhấn "Lưu lại" $\rightarrow$ Hệ thống cập nhật CSDL.<br>4. **Xóa**: Người dùng click icon xóa $\rightarrow$ Hệ thống hiển thị popup xác nhận $\rightarrow$ Người dùng chọn "Xác nhận Xóa" $\rightarrow$ Hệ thống kiểm tra ràng buộc và thực hiện xóa vĩnh viễn hoặc ẩn dữ liệu. |
| **Kịch bản phụ** | - *Dữ liệu nhập không hợp lệ hoặc thiếu trường bắt buộc:* Hệ thống giữ nguyên giao diện biểu mẫu, đánh dấu đỏ các trường lỗi và hiển thị thông báo yêu cầu hoàn thiện.<br>- *Xóa cơ sở lưu trú có ràng buộc dữ liệu (đang có phản hồi, đánh giá, hoặc dữ liệu thống kê):* Hệ thống từ chối xóa vĩnh viễn, hiển thị thông báo lỗi logic và gợi ý người dùng chuyển trạng thái sang "Tạm dừng hoạt động" hoặc "Ngừng hoạt động". |
| **Các yêu cầu, ràng buộc** | Hệ thống đảm bảo kết nối internet ổn định, sử dụng giao thức bảo mật HTTPS, tối ưu hóa kích thước và dung lượng tải lên của tệp tin hình ảnh, tích hợp bản đồ số để lấy tọa độ địa lý chính xác. |

---

#### **a. Hiển thị danh sách cơ sở lưu trú**

*Hình 3.12: Giao diện danh sách cơ sở lưu trú*

| **Màn hình** | **Danh sách cơ sở lưu trú** |
| :--- | :--- |
| **Mô tả** | Chức năng này cho phép Quản lý nghiệp vụ theo dõi toàn bộ các cơ sở lưu trú trong hệ thống. Hỗ trợ các công cụ tìm kiếm nhanh, lọc dữ liệu nâng cao, thực hiện điều hướng thêm, sửa, xóa và theo dõi tổng quan số lượng. |
| **Màn hình kết nối** | Thêm mới cơ sở lưu trú, Chỉnh sửa thông tin cơ sở lưu trú, Xóa cơ sở lưu trú (Popup) |

**Nội dung màn hình**
| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Tìm tên cơ sở lưu trú | Textfield – String | Nhập từ khóa tên cơ sở lưu trú cần tìm kiếm. |
| Loại hình lưu trú | Combobox – String | Chọn loại hình để lọc danh sách (Tất cả loại hình, Khách sạn, Homestay, Villa, Resort, Nhà nghỉ...). |
| Địa bàn | Combobox – String | Chọn đơn vị hành chính để lọc (Quận/Huyện, Phường/Xã). |
| Trạng thái | Combobox – String | Lọc theo trạng thái hoạt động (Đang hoạt động, Tạm dừng hoạt động, Ngừng hoạt động). |
| Thêm cơ sở lưu trú mới | Button | Nút bấm nổi bật (màu vàng), click để chuyển sang giao diện tạo mới cơ sở lưu trú. |
| Xuất tệp / In dữ liệu | Icon Button | Cho phép xuất dữ liệu danh sách ra file Excel/PDF hoặc thực hiện in nhanh. |
| Danh sách cơ sở lưu trú | Table | Bảng hiển thị thông tin danh sách các cơ sở lưu trú gồm các cột dữ liệu. |
| *STT* | Label – Number | Hiển thị số thứ tự của cơ sở lưu trú trong trang. |
| *Mã cơ sở* | Label – String | Hiển thị mã định danh duy nhất của cơ sở lưu trú trên hệ thống. |
| *Tên cơ sở lưu trú* | Button / Link | Hiển thị tên cơ sở lưu trú dưới dạng liên kết, nhấn vào để xem chi tiết thông tin. |
| *Loại hình* | Label – String | Hiển thị loại hình lưu trú tương ứng. |
| *Địa chỉ* | Label – String | Hiển thị vị trí/địa chỉ chi tiết của cơ sở lưu trú. |
| *Số điện thoại* | Label – String | Hiển thị số điện thoại liên hệ chính thức. |
| *Trạng thái* | Badge / Tag | Hiển thị nhãn trạng thái (Màu xanh: Đang hoạt động; Màu đỏ/Xám: Tạm dừng hoặc Ngừng hoạt động). |
| *Chỉnh sửa* | Icon Button | Biểu tượng cây bút, click để mở trang Chỉnh sửa thông tin cơ sở lưu trú. |
| *Xóa* | Icon Button | Biểu tượng thùng rác, click để kích hoạt hộp thoại popup xác nhận xóa. |
| Phân trang | Pagination | Thành phần chuyển đổi qua lại giữa các trang dữ liệu (Trang đầu, trước, số trang cụ thể, sau, trang cuối). |
| Tổng số cơ sở lưu trú | Card Label – Number | Ô thống kê hiển thị tổng số lượng cơ sở lưu trú đang quản lý trong hệ thống. |

**Các chức năng màn hình**
| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| Tìm kiếm & Lọc dữ liệu | Người dùng nhập từ khóa hoặc chọn các tiêu chí trên thanh bộ lọc và bấm tìm kiếm. | Hệ thống lọc và hiển thị đúng danh sách các cơ sở lưu trú thỏa mãn điều kiện. | Không tìm thấy dữ liệu phù hợp, hệ thống hiển thị bảng trống cùng thông báo "Không tìm thấy dữ liệu". |
| Điều hướng Thêm mới | Người dùng nhấn nút "Thêm cơ sở lưu trú mới". | Điều hướng người dùng sang màn hình biểu mẫu Thêm mới cơ sở lưu trú với các trường trống. | Gặp lỗi điều hướng hoặc lỗi tải trang, hệ thống giữ nguyên màn hình cũ và báo lỗi. |
| Điều hướng Chỉnh sửa | Người dùng nhấn chọn biểu tượng Chỉnh sửa tại dòng dữ liệu mong muốn. | Hệ thống chuyển hướng sang màn hình Chỉnh sửa thông tin cơ sở lưu trú và tải sẵn toàn bộ dữ liệu cũ của cơ sở đó lên biểu mẫu. | Không tải được dữ liệu cơ sở lưu trú do lỗi kết nối CSDL hoặc id không hợp lệ. |
| Yêu cầu Xóa dữ liệu | Người dùng nhấn chọn biểu tượng Xóa tại dòng dữ liệu tương ứng. | Hệ thống hiển thị hộp thoại popup cảnh báo và yêu cầu xác nhận xóa đè lên màn hình danh sách. | Hộp thoại popup không hiển thị được. |

---

#### **b. Thêm mới cơ sở lưu trú**

*Hình 3.13: Biểu mẫu Thêm mới cơ sở lưu trú*

| **Màn hình** | **Thêm mới cơ sở lưu trú** |
| :--- | :--- |
| **Mô tả** | Cung cấp giao diện biểu mẫu cho phép Chuyên viên hoặc Doanh nghiệp nhập và đăng ký một cơ sở lưu trú mới vào cơ sở dữ liệu hệ thống du lịch. |
| **Màn hình kết nối** | Danh sách cơ sở lưu trú (Quay lại sau khi lưu hoặc hủy) |

**Nội dung màn hình**
| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Tên cơ sở lưu trú | Textfield – String | Nhập tên chính thức của cơ sở lưu trú (Trường bắt buộc). |
| Loại hình lưu trú | Dropdown | Chọn một loại hình trong danh mục có sẵn (Khách sạn, Biệt thự, Homestay...) (Trường bắt buộc). |
| Doanh nghiệp sở hữu | Dropdown / Search | Chọn doanh nghiệp chủ quản quản lý cơ sở lưu trú này (nếu có). |
| Quận / Huyện | Dropdown | Chọn quận, huyện, thị xã trực thuộc tỉnh Thừa Thiên Huế (Trường bắt buộc). |
| Phường / Xã | Dropdown | Chọn phường, xã, thị trấn tương ứng dựa theo Quận/Huyện đã chọn (Trường bắt buộc). |
| Địa chỉ chi tiết | Textfield – String | Nhập cụ thể số nhà, ngõ hẻm, tên đường của cơ sở lưu trú (Trường bắt buộc). |
| Số điện thoại | Textfield – String | Nhập số điện thoại liên hệ chính thức của cơ sở (Trường bắt buộc). |
| Email | Textfield – String | Nhập hòm thư điện tử liên hệ. |
| Website | Textfield – String | Nhập địa chỉ website hoặc trang mạng xã hội của cơ sở (nếu có). |
| Số lượng phòng / Sức chứa | Textfield – Number | Nhập tổng số phòng kinh doanh hoặc quy mô sức chứa tối đa. |
| Tiện ích đi kèm | Checkbox List | Tích chọn các tiện ích mà cơ sở cung cấp (Wifi, Hồ bơi, Điều hòa, Bãi đỗ xe, Nhà hàng, Spa...). |
| Hình ảnh cơ sở | Upload Component | Vùng tải lên hình ảnh thực tế của cơ sở lưu trú (Hỗ trợ chọn và tải lên nhiều ảnh đồng thời, hiển thị danh sách ảnh preview). |
| Trạng thái hoạt động | Dropdown | Mặc định chọn trạng thái "Đang hoạt động" khi tạo mới, hoặc có thể tùy chỉnh. |
| Hủy | Button | Nút bấm, click để hủy bỏ toàn bộ dữ liệu đang nhập và quay về màn hình danh sách. |
| Lưu lại | Button | Nút bấm (màu xanh), click để hệ thống kiểm tra và thực hiện lưu dữ liệu vào hệ thống. |

**Các chức năng màn hình**
| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| Lưu thông tin cơ sở lưu trú | Người dùng nhấn nút "Lưu lại" sau khi điền thông tin trên biểu mẫu. | Hệ thống xác thực dữ liệu hợp lệ $\rightarrow$ Tiến hành thêm mới dữ liệu vào CSDL $\rightarrow$ Hiển thị thông báo "Thêm mới cơ sở lưu trú thành công" $\rightarrow$ Tự động chuyển về màn hình danh sách. | Thất bại do: Thiếu trường bắt buộc; dữ liệu sai định dạng (SĐT/Email không hợp lệ); tệp ảnh quá dung lượng cho phép $\rightarrow$ Giữ nguyên màn hình, hiển thị lỗi chi tiết tại các trường dữ liệu sai. |
| Hủy bỏ thao tác | Người dùng nhấn nút "Hủy". | Hệ thống hủy bỏ toàn bộ dữ liệu đang nhập trên form (không lưu vào CSDL) và chuyển hướng ngay về giao diện danh sách cơ sở lưu trú. | Hệ thống không thực hiện điều hướng, giữ nguyên giao diện hiện tại. |

---

#### **c. Chỉnh sửa thông tin cơ sở lưu trú**

*Hình 3.14: Biểu mẫu Chỉnh sửa thông tin cơ sở lưu trú*

| **Màn hình** | **Chỉnh sửa thông tin cơ sở lưu trú** |
| :--- | :--- |
| **Mô tả** | Cho phép người dùng cập nhật, thay đổi thông tin của một cơ sở lưu trú đã có sẵn trên hệ thống. Giao diện tải lại toàn bộ thông tin cũ của cơ sở lưu trú được chọn. |
| **Màn hình kết nối** | Danh sách cơ sở lưu trú |

**Nội dung màn hình**
| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Mã cơ sở lưu trú | Textfield – String | Hiển thị mã định danh duy nhất của cơ sở. Thuộc tính: *Read-only* (Không cho phép chỉnh sửa trường này). |
| Tên cơ sở lưu trú | Textfield – String | Chỉnh sửa tên của cơ sở lưu trú (Trường bắt buộc). |
| Loại hình lưu trú | Dropdown | Thay đổi loại hình lưu trú nếu cần. |
| Doanh nghiệp sở hữu | Dropdown | Cập nhật lại thông tin doanh nghiệp chủ quản liên kết. |
| Quận / Huyện | Dropdown | Thay đổi thông tin địa bàn cấp quận/huyện. |
| Phường / Xã | Dropdown | Thay đổi thông tin địa bàn cấp phường/xã theo quận/huyện mới. |
| Địa chỉ chi tiết | Textfield – String | Thay đổi thông tin địa chỉ chi tiết (Trường bắt buộc). |
| Số điện thoại | Textfield – String | Cập nhật số điện thoại liên hệ mới (Trường bắt buộc). |
| Email | Textfield – String | Thay đổi hòm thư điện tử liên hệ. |
| Website | Textfield – String | Cập nhật link liên kết trang web. |
| Số lượng phòng / Sức chứa | Textfield – Number | Thay đổi thông tin số lượng phòng/sức chứa của cơ sở. |
| Tiện ích đi kèm | Checkbox List | Tích chọn thêm hoặc bỏ chọn các tiện ích dịch vụ đi kèm. |
| Hình ảnh cơ sở | Upload Component | Hiển thị danh sách ảnh hiện tại; cho phép bấm nút xóa ảnh cũ hoặc upload bổ sung ảnh mới. |
| Trạng thái hoạt động | Dropdown | Cập nhật lại trạng thái (Đang hoạt động, Tạm dừng hoạt động, Ngừng hoạt động). |
| Hủy | Button | Nút bấm hủy bỏ các thay đổi vừa sửa, quay lại màn hình danh sách. |
| Lưu lại | Button | Nút bấm lưu lại các thay đổi thông tin vào hệ thống. |

**Các chức năng màn hình**
| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| Lưu lại cập nhật | Người dùng nhấn nút "Lưu lại" sau khi thay đổi thông tin. | Hệ thống kiểm tra dữ liệu hợp lệ $\rightarrow$ Ghi đè cập nhật dữ liệu vào CSDL $\rightarrow$ Hiển thị thông báo "Cập nhật thông tin cơ sở lưu trú thành công" $\rightarrow$ Quay lại trang danh sách. | Thất bại do: Dữ liệu sửa để trống các trường bắt buộc; định dạng sai; lỗi kết nối hệ thống $\rightarrow$ Hiển thị thông báo cảnh báo lỗi cụ thể, dữ liệu cũ chưa bị thay đổi trong CSDL. |
| Hủy chỉnh sửa | Người dùng nhấn nút "Hủy". | Hệ thống bỏ qua các thông tin vừa chỉnh sửa, đóng giao diện biểu mẫu chỉnh sửa và quay lại màn hình danh sách cơ sở lưu trú. | Giữ nguyên trạng thái biểu mẫu hiện tại không điều hướng. |

---

#### **d. Xóa cơ sở lưu trú (Popup xác nhận)**

*Hình 3.15: Hộp thoại Xác nhận xóa cơ sở lưu trú*

| **Màn hình** | **Xóa cơ sở lưu trú (Popup)** |
| :--- | :--- |
| **Mô tả** | Hộp thoại xuất hiện ở dạng modal/popup đè lên màn hình danh sách khi người dùng thực hiện thao tác xóa, nhằm mục đích cảnh báo và yêu cầu xác nhận chắc chắn trước khi xóa vĩnh viễn dữ liệu. |
| **Màn hình kết nối** | Danh sách cơ sở lưu trú |

**Nội dung màn hình**
| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Tiêu đề hộp thoại | String (static) | Dòng chữ văn bản tĩnh hiển thị nổi bật ở phía trên: **"Xác nhận xóa cơ sở lưu trú"**. |
| Câu hỏi xác nhận | String (dynamic) | Dòng chữ chứa nội dung tên động: **"Bạn có chắc chắn muốn xóa cơ sở lưu trú '[Tên_Cơ_Sở]' khỏi hệ thống?"** (với '[Tên_Cơ_Sở]' được lấy tự động từ dòng dữ liệu được chọn). |
| LƯU Ý LOGIC HỆ THỐNG | String (static) | Dòng văn bản tĩnh cảnh báo logic: *"Việc xóa cơ sở lưu trú này sẽ ảnh hưởng đến các dữ liệu liên quan (lịch sử lưu trú, thống kê, phản hồi du khách...)."* |
| Hủy bỏ | Button | Nút bấm, click để hủy bỏ hành động xóa và đóng popup. |
| Xác nhận Xóa | Button | Nút bấm hành động (màu đỏ), click để ra lệnh cho hệ thống thực thi xóa vĩnh viễn dữ liệu. |

**Các chức năng màn hình**
| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| Xác nhận Xóa dữ liệu | Người dùng nhấn chọn nút "Xác nhận Xóa" trên popup. | Hệ thống kiểm tra ràng buộc logic dữ liệu thành công $\rightarrow$ Thực hiện xóa vĩnh viễn cơ sở lưu trú khỏi hệ thống $\rightarrow$ Đóng popup $\rightarrow$ Hiển thị thông báo "Xóa thành công" $\rightarrow$ Làm mới (refresh) lại bảng danh sách dữ liệu. | Thất bại do dữ liệu bị ràng buộc chặt chẽ với các bảng khác (ví dụ: cơ sở lưu trú này đang có liên kết hóa đơn du lịch, hoặc danh sách phòng đang vận hành không thể xóa) $\rightarrow$ Hệ thống từ chối xóa, giữ nguyên popup và hiển thị thông báo lỗi logic dữ liệu. |
| Hủy bỏ thao tác xóa | Người dùng nhấn nút "Hủy bỏ" hoặc click ra vùng ngoài hộp thoại. | Hệ thống đóng hộp thoại popup lại ngay lập tức, thông tin cơ sở lưu trú và bảng danh sách được giữ nguyên không có bất kỳ thay đổi nào. | Hộp thoại popup bị đơ, không đóng được. |

### 3.5. Quản lý lữ hành và HDV

| **Tên Use case** | **Quản lý lữ hành và Hướng dẫn viên (HDV)** |
| :--- | :--- |
| **Mô tả** | Chuyên viên quản lý nghiệp vụ/Quản trị viên thực hiện xem danh sách, thêm, sửa, xóa, cấp phép hoặc tạm khóa hoạt động đối với các Doanh nghiệp kinh doanh lữ hành và Hướng dẫn viên du lịch (Quốc tế/Nội địa) trên địa bàn. |
| **Tác nhân** | Chuyên viên quản lý, Quản trị hệ thống |
| **Độ phức tạp** | 🔲 Đơn giản  🔲 Trung bình  ☑️ Phức tạp |
| **Điều kiện bắt đầu** | Người dùng đã đăng nhập thành công và có quyền truy cập vào module quản lý Lữ hành & HDV. |
| **Điều kiện kết thúc** | Thông tin của doanh nghiệp lữ hành hoặc hướng dẫn viên được tạo mới, cập nhật hoặc xóa/khóa thành công trong hệ thống. |
| **Kịch bản chính** | 1. Chọn menu "Quản lý nghiệp vụ" $\rightarrow$ Chọn tab "Doanh nghiệp lữ hành" hoặc "Hướng dẫn viên".<br>2. Hệ thống hiển thị danh sách tương ứng kèm bộ lọc tìm kiếm.<br>3. **Thêm mới**: Click "Thêm mới" $\rightarrow$ Điền thông tin (MST, Giấy phép lữ hành, Số thẻ HDV, Ngôn ngữ...) $\rightarrow$ Nhấn "Lưu".<br>4. **Chỉnh sửa**: Click icon Sửa $\rightarrow$ Cập nhật thông tin/Gia hạn thẻ/Gia hạn giấy phép $\rightarrow$ Nhấn "Lưu".<br>5. **Xóa/Khóa**: Click icon Xóa/Khóa $\rightarrow$ Xác nhận trên popup $\rightarrow$ Hệ thống cập nhật trạng thái hoạt động. |
| **Kịch bản phụ** | - *Trùng lặp dữ liệu:* Nhập trùng Mã số thuế doanh nghiệp hoặc Số thẻ Hướng dẫn viên $\rightarrow$ Hệ thống báo lỗi và từ chối lưu.<br>- *Thẻ HDV hoặc Giấy phép hết hạn:* Hệ thống tự động bôi đỏ cảnh báo đối với các HDV có thẻ đã quá hạn sử dụng. |
| **Các yêu cầu, ràng buộc** | Mã số thuế và Số thẻ HDV là định danh duy nhất (Unique). Ngày cấp thẻ/giấy phép phải nhỏ hơn Ngày hết hạn. |

---

#### a. Quản lý danh sách Doanh nghiệp Lữ hành

| **Màn hình** | **Danh sách doanh nghiệp lữ hành** |
| :--- | :--- |
| **Mô tả** | Giao diện quản lý toàn bộ các công ty, đại lý du lịch lữ hành. Cho phép lọc theo loại hình kinh doanh (nội địa/quốc tế) và tình trạng giấy phép. |
| **Màn hình kết nối** | Thêm mới / Chỉnh sửa / Xóa Doanh nghiệp lữ hành |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Ô tìm kiếm | Textfield – String | Nhập tên doanh nghiệp hoặc Mã số thuế để tìm kiếm nhanh. |
| Loại hình | Combobox – String | Lọc theo: Lữ hành Quốc tế, Lữ hành Nội địa. |
| Trạng thái | Combobox – String | Lọc theo trạng thái: Đang hoạt động, Tạm dừng, Đã thu hồi giấy phép. |
| Thêm doanh nghiệp | Button | Chuyển sang form đăng ký doanh nghiệp mới. |
| Bảng dữ liệu | Table | Bảng danh sách doanh nghiệp lữ hành. |
| *Mã số thuế* | Label – String | Mã số thuế (Đóng vai trò ID hiển thị). |
| *Tên doanh nghiệp* | Link | Tên công ty lữ hành, click để xem chi tiết. |
| *Số giấy phép* | Label – String | Số giấy phép kinh doanh lữ hành. |
| *Loại hình* | Label – String | Quốc tế / Nội địa. |
| *Người đại diện* | Label – String | Tên người đại diện pháp luật. |
| *Trạng thái* | Badge | Trạng thái hoạt động (Xanh: Hoạt động, Đỏ: Thu hồi). |
| *Thao tác* | Icon Buttons | Biểu tượng Sửa (Bút), Xóa (Thùng rác). |
| Phân trang | Pagination | Chuyển đổi giữa các trang dữ liệu. |

---

#### b. Form Thêm/Sửa Doanh nghiệp Lữ hành

| **Màn hình** | **Thêm mới / Chỉnh sửa Doanh nghiệp Lữ hành** |
| :--- | :--- |
| **Mô tả** | Biểu mẫu nhập liệu để đăng ký mới hoặc cập nhật thông tin giấy phép của một công ty lữ hành. |
| **Màn hình kết nối** | Danh sách doanh nghiệp lữ hành |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Tên doanh nghiệp | Textfield – String | Nhập tên đầy đủ của doanh nghiệp (Bắt buộc). |
| Mã số thuế | Textfield – String | Nhập MST doanh nghiệp (Bắt buộc, không cho sửa nếu ở chế độ Edit). |
| Số giấy phép | Textfield – String | Số giấy phép lữ hành (Bắt buộc). |
| Loại hình kinh doanh | Radio Button | Chọn "Nội địa" hoặc "Quốc tế". |
| Người đại diện | Textfield – String | Tên người đại diện pháp luật. |
| Ngày cấp / Ngày hết hạn | Datepicker | Nhập thời hạn của giấy phép. |
| SĐT / Email | Textfield – String | Thông tin liên hệ công ty. |
| Địa chỉ | Textfield – String | Trụ sở chính của doanh nghiệp. |
| Nút Lưu / Hủy | Button | Lưu dữ liệu vào CSDL hoặc Hủy thao tác. |

---

#### c. Quản lý danh sách Hướng dẫn viên (HDV)

| **Màn hình** | **Danh sách Hướng dẫn viên** |
| :--- | :--- |
| **Mô tả** | Quản lý danh sách thẻ hướng dẫn viên du lịch. Theo dõi sát sao trình độ ngoại ngữ và thời hạn sử dụng thẻ của từng HDV. |
| **Màn hình kết nối** | Thêm mới / Chỉnh sửa hồ sơ HDV / Khóa thẻ |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Ô tìm kiếm | Textfield – String | Nhập Tên HDV hoặc Số thẻ HDV. |
| Loại thẻ | Combobox – String | Lọc: Thẻ Quốc tế, Thẻ Nội địa, Thẻ Tại điểm. |
| Ngôn ngữ | Combobox – String | Lọc theo ngoại ngữ: Tiếng Anh, Pháp, Trung, Nhật... |
| Tình trạng thẻ | Combobox – String | Lọc: Còn hạn, Hết hạn, Bị khóa thẻ. |
| Thêm HDV | Button | Nút mở form tạo hồ sơ cấp thẻ mới. |
| Bảng dữ liệu HDV | Table | Hiển thị danh sách HDV. |
| *Số thẻ HDV* | Label – String | Số hiệu thẻ hướng dẫn viên. |
| *Họ và tên* | Link | Tên HDV (Kèm avatar nhỏ bên cạnh). |
| *Loại thẻ* | Label – String | Hiển thị phân loại thẻ. |
| *Ngôn ngữ* | Label – String | Các ngoại ngữ được cấp phép hướng dẫn. |
| *Hạn thẻ* | Label – Date | Ngày hết hạn của thẻ HDV. |
| *Trạng thái* | Badge | Trạng thái (Xanh: Hợp lệ, Đỏ: Hết hạn, Xám: Khóa). |

---

#### d. Form Thêm/Sửa hồ sơ Hướng dẫn viên

| **Màn hình** | **Thêm mới / Chỉnh sửa hồ sơ Hướng dẫn viên** |
| :--- | :--- |
| **Mô tả** | Biểu mẫu nhập thông tin nhân thân, trình độ ngôn ngữ và thông tin thẻ ngành của hướng dẫn viên. |
| **Màn hình kết nối** | Danh sách Hướng dẫn viên |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Số thẻ HDV | Textfield – String | Nhập mã số thẻ HDV (Bắt buộc, Unique). |
| Họ và tên | Textfield – String | Tên đầy đủ của HDV (Bắt buộc). |
| Số CCCD / CMND | Textfield – String | Số định danh cá nhân. |
| Giới tính / Ngày sinh | Radio / Datepicker | Chọn giới tính và ngày tháng năm sinh. |
| Phân loại thẻ | Dropdown | Chọn: Thẻ Nội địa, Quốc tế, Tại điểm. |
| Ngôn ngữ thành thạo | Multi-select / Checkbox| Chọn nhiều ngôn ngữ HDV có thể sử dụng (Anh, Trung, Pháp...). |
| Ngày cấp / Hết hạn | Datepicker | Thời hạn hiệu lực của thẻ hành nghề. |
| Ảnh thẻ 3x4 | File Upload | Tải lên ảnh chân dung của HDV. |
| Trạng thái | Dropdown | Đang hoạt động, Tạm khóa thẻ. |
| Nút Lưu / Hủy | Button | Lưu hồ sơ HDV hoặc hủy thao tác quay về danh sách. |

**Các chức năng màn hình dùng chung (Form Thêm/Sửa cả Lữ hành & HDV):**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Lưu dữ liệu** | Click nút "Lưu" để lưu vào hệ thống | Dữ liệu hợp lệ $\rightarrow$ Hệ thống báo thành công, lưu CSDL và chuyển về trang danh sách. | Để trống trường bắt buộc, sai format email, hoặc trùng MST/Số thẻ HDV $\rightarrow$ Báo lỗi đỏ. |
| **Hủy bỏ** | Click nút "Hủy" | Hệ thống đóng form, không lưu dữ liệu. | |
### 3.6. Quản lý cơ sở ăn uống & mua sắm

| **Tên Use case** | **Quản lý cơ sở ăn uống & mua sắm** |
| :--- | :--- |
| **Mô tả** | Chuyên viên quản lý nghiệp vụ hoặc doanh nghiệp thực hiện xem danh sách, tìm kiếm, lọc, thêm mới, cập nhật và xóa thông tin các nhà hàng, quán ăn, cửa hàng đặc sản, cơ sở mua sắm đạt chuẩn phục vụ khách du lịch. |
| **Tác nhân** | Chuyên viên quản lý nghiệp vụ, Quản trị viên hệ thống, Doanh nghiệp/Chủ cơ sở |
| **Độ phức tạp** | 🔲 Đơn giản  ☑️ Trung bình  🔲 Phức tạp |
| **Điều kiện bắt đầu** | Người dùng đăng nhập thành công, có quyền truy cập vào chức năng Quản lý ăn uống & mua sắm. |
| **Điều kiện kết thúc** | Thông tin cơ sở dịch vụ được lưu trữ thành công vào hệ thống hoặc thao tác bị hủy. |
| **Kịch bản chính** | 1. Chọn menu "Ăn uống & Mua sắm". Hệ thống hiển thị danh sách cơ sở.<br>2. **Thêm mới**: Click "Thêm cơ sở mới" $\rightarrow$ Nhập thông tin (Tên, Loại hình: Ăn uống/Mua sắm, Địa chỉ, Giờ mở cửa, Hình ảnh) $\rightarrow$ Nhấn "Lưu lại".<br>3. **Chỉnh sửa**: Chọn biểu tượng Sửa $\rightarrow$ Cập nhật thông tin dịch vụ, giá tham khảo, hoặc thay ảnh $\rightarrow$ Nhấn "Lưu lại".<br>4. **Xóa**: Chọn biểu tượng Xóa $\rightarrow$ Xác nhận trên popup $\rightarrow$ Hệ thống cập nhật trạng thái xóa. |
| **Kịch bản phụ** | - *Thiếu dữ liệu bắt buộc:* Hệ thống cảnh báo đỏ yêu cầu nhập đầy đủ tên và địa chỉ.<br>- *Hình ảnh sai định dạng/vượt dung lượng:* Thông báo yêu cầu tải lại ảnh hợp lệ. |
| **Các yêu cầu, ràng buộc** | Hệ thống cần hỗ trợ nhập tọa độ bản đồ để khách du lịch có thể tìm đường dễ dàng qua ứng dụng hoặc trang web. |

---

#### a. Danh sách cơ sở ăn uống & mua sắm

| **Màn hình** | **Danh sách cơ sở ăn uống & mua sắm** |
| :--- | :--- |
| **Mô tả** | Giao diện quản lý danh sách tổng hợp. Hỗ trợ phân loại rõ ràng giữa Dịch vụ Ăn uống và Cơ sở Mua sắm. |
| **Màn hình kết nối** | Thêm mới / Chỉnh sửa / Xóa Cơ sở dịch vụ |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Tìm kiếm | Textfield – String | Nhập tên nhà hàng, quán ăn hoặc cửa hàng để tìm kiếm. |
| Phân loại dịch vụ | Combobox – String | Lọc theo: Tất cả, Dịch vụ Ăn uống, Cơ sở Mua sắm. |
| Địa bàn hành chính | Combobox – String | Lọc theo Quận/Huyện, Phường/Xã. |
| Đạt chuẩn phục vụ | Checkbox | Lọc các cơ sở đã được cấp biển "Đạt chuẩn phục vụ khách du lịch". |
| Thêm cơ sở mới | Button | Nút mở giao diện thêm mới. |
| Bảng danh sách | Table | Hiển thị thông tin tổng quan. |
| *STT* | Label – Number | Số thứ tự. |
| *Tên cơ sở* | Link | Tên cơ sở dịch vụ. |
| *Loại hình* | Label – String | Nhà hàng / Quán ăn / Cửa hàng lưu niệm / Đặc sản... |
| *Địa chỉ* | Label – String | Địa chỉ chi tiết. |
| *Giờ hoạt động* | Label – String | Khung giờ mở cửa - đóng cửa. |
| *Trạng thái* | Badge | Đang hoạt động / Đóng cửa. |
| *Thao tác* | Icon Buttons | Biểu tượng Sửa, Xóa. |
| Phân trang | Pagination | Chuyển trang danh sách. |

---

#### b. Form Thêm mới / Chỉnh sửa cơ sở ăn uống & mua sắm

| **Màn hình** | **Thêm mới / Chỉnh sửa cơ sở ăn uống & mua sắm** |
| :--- | :--- |
| **Mô tả** | Biểu mẫu nhập liệu chi tiết về cơ sở, bao gồm cả vị trí địa lý, các tiện ích đi kèm và minh chứng đạt chuẩn. |
| **Màn hình kết nối** | Danh sách cơ sở ăn uống & mua sắm |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Tên cơ sở | Textfield – String | Nhập tên chính thức (Bắt buộc). |
| Nhóm dịch vụ | Radio Button | Chọn "Ăn uống" hoặc "Mua sắm" (Bắt buộc). |
| Loại hình chi tiết | Dropdown | Tuỳ thuộc nhóm trên: Nhà hàng, Quán Cafe, Lưu niệm, Siêu thị... |
| Tỉnh/Quận/Phường | Dropdown | Chọn đơn vị hành chính. |
| Địa chỉ chi tiết | Textfield – String | Số nhà, tên đường (Bắt buộc). |
| Tọa độ bản đồ | Map Component | Ghim vị trí để lấy Kinh độ / Vĩ độ chính xác. |
| Số điện thoại | Textfield – String | Hotline liên hệ đặt bàn / mua hàng. |
| Giờ mở cửa | Timepicker | Chọn giờ bắt đầu và giờ kết thúc hoạt động. |
| Giá tham khảo | Textfield – String | Khoảng giá (VD: 50.000 VNĐ - 500.000 VNĐ). |
| Đạt chuẩn du lịch | Toggle / Switch | Bật nếu cơ sở đã được chứng nhận đạt chuẩn phục vụ du lịch. |
| Hình ảnh không gian | File Upload | Tải lên ảnh mặt tiền, không gian bên trong, món ăn/sản phẩm nổi bật. |
| Nút Lưu / Hủy | Button | Lưu dữ liệu hoặc hủy thao tác. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Lưu dữ liệu** | Click "Lưu lại" | Dữ liệu hợp lệ $\rightarrow$ Cập nhật CSDL và hiển thị thông báo thành công. | Thiếu thông tin bắt buộc $\rightarrow$ Báo lỗi tại trường tương ứng. |
| **Hủy bỏ** | Click "Hủy" | Đóng form, quay về trang trước. | |

---
---

### 3.7. Quản lý điểm đến (Destinations)

| **Tên Use case** | **Quản lý điểm đến** |
| :--- | :--- |
| **Mô tả** | Quản lý thông tin các điểm đến du lịch tổng hợp (Làng nghề, Cụm du lịch, Tuyến phố đi bộ, Khu du lịch sinh thái lớn) trên địa bàn. |
| **Tác nhân** | Chuyên viên quản lý, Quản trị hệ thống |
| **Độ phức tạp** | 🔲 Đơn giản  ☑️ Trung bình  🔲 Phức tạp |
| **Điều kiện bắt đầu** | Người dùng đăng nhập có quyền truy cập module Quản lý điểm đến. |
| **Điều kiện kết thúc** | Thông tin điểm đến được tạo lập, chỉnh sửa hoặc gỡ bỏ. |
| **Kịch bản chính** | 1. Truy cập menu "Điểm đến".<br>2. **Thêm mới**: Click "Thêm điểm đến" $\rightarrow$ Nhập tên, mô tả tổng quan, tải ảnh/video quảng bá, ghim vùng không gian trên bản đồ $\rightarrow$ Nhấn "Lưu".<br>3. **Chỉnh sửa**: Chọn điểm đến cần sửa $\rightarrow$ Cập nhật nội dung giới thiệu, hình ảnh truyền thông $\rightarrow$ Nhấn "Lưu".<br>4. **Xóa**: Chọn Xóa $\rightarrow$ Xác nhận trên popup cảnh báo $\rightarrow$ Hệ thống ẩn/xóa điểm đến. |
| **Kịch bản phụ** | - *Lỗi media:* Video/ảnh tải lên quá giới hạn dung lượng $\rightarrow$ Hệ thống từ chối upload. |
| **Các yêu cầu, ràng buộc** | Nội dung giới thiệu điểm đến thường ở dạng Rich Text (HTML) để trình bày đẹp mắt trên cổng thông tin du khách. |

---

#### a. Danh sách Điểm đến

| **Màn hình** | **Danh sách Điểm đến** |
| :--- | :--- |
| **Mô tả** | Giao diện hiển thị các điểm đến nổi bật của địa phương, phục vụ cho việc quảng bá trên Cổng thông tin du lịch. |
| **Màn hình kết nối** | Thêm mới / Chỉnh sửa / Xóa Điểm đến |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Tìm kiếm | Textfield – String | Tìm tên điểm đến (VD: Phố Tây, Làng nón Phú Gia...). |
| Danh mục điểm đến | Combobox – String | Lọc: Du lịch sinh thái, Du lịch cộng đồng, Không gian văn hóa... |
| Thêm điểm đến | Button | Nút chuyển đến giao diện tạo mới. |
| Bảng hiển thị | Table | Danh sách các điểm đến. |
| *Tên điểm đến* | Link | Tên gọi phổ biến của khu vực/điểm đến. |
| *Danh mục* | Label – String | Loại hình du lịch chính. |
| *Lượt xem/Check-in* | Label – Number | Thống kê số lượt quan tâm (nếu có liên kết số liệu). |
| *Hiển thị nổi bật* | Toggle | Đánh dấu hiển thị lên trang chủ Cổng thông tin. |
| *Thao tác* | Icon Buttons | Chỉnh sửa, Xóa. |

---

#### b. Form Thêm/Sửa Điểm đến

| **Màn hình** | **Thêm mới / Chỉnh sửa Điểm đến** |
| :--- | :--- |
| **Mô tả** | Giao diện nhập liệu với công cụ soạn thảo văn bản phong phú (Rich Text) để viết bài quảng bá điểm đến, kèm thư viện Media. |
| **Màn hình kết nối** | Danh sách Điểm đến |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Tên điểm đến | Textfield – String | Nhập tên điểm đến (Bắt buộc). |
| Danh mục | Dropdown | Chọn phân loại (Sinh thái, Tâm linh, Cộng đồng...). |
| Tóm tắt | Textarea – String | Đoạn giới thiệu ngắn gọn (hiển thị ở thẻ preview). |
| Nội dung chi tiết | Rich Text Editor | Trình soạn thảo văn bản cho phép chèn định dạng, ảnh bài viết. |
| Địa chỉ / Khu vực | Textfield | Vị trí tọa lạc. |
| Tọa độ trung tâm | Map Component | Ghim vị trí trung tâm của điểm đến trên bản đồ. |
| Thư viện ảnh / Video | Media Upload | Cho phép upload bộ sưu tập ảnh (Gallery) và link video YouTube giới thiệu. |
| Trạng thái xuất bản | Dropdown | Chọn: Bản nháp, Xuất bản, Ẩn. |
| Đặt làm nổi bật | Checkbox | Ưu tiên hiển thị trên banner trang chủ. |
| Nút Lưu / Hủy | Button | Lưu bài viết điểm đến hoặc hủy bỏ. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Lưu & Xuất bản** | Click "Lưu" hoặc "Lưu và Xuất bản" | Lưu bài viết giới thiệu điểm đến thành công, nội dung được đồng bộ ra ứng dụng/web du khách. | Lỗi mạng, hoặc thiếu tiêu đề bắt buộc $\rightarrow$ Thông báo lỗi. |
| **Hủy bỏ** | Click "Hủy" | Bỏ qua các nội dung vừa soạn thảo. | |

---

*(Ghi chú: Cả 2 phân hệ trên đều áp dụng chung cấu trúc hộp thoại Popup Xác nhận Xóa tương tự như mục 3.4)*
