# 3. THIẾT KẾ CHI TIẾT CÁC CHỨC NĂNG (PHÂN HỆ QUẢN LÝ NGHIỆP VỤ)

Phân hệ Quản lý nghiệp vụ thuộc hệ thống CSDL Du lịch bao gồm các chức năng cốt lõi giúp Chuyên viên quản lý, Quản trị viên và Doanh nghiệp cập nhật thông tin tài nguyên, dịch vụ và thực thể du lịch trên địa bàn tỉnh/thành phố. Dưới đây là thiết kế chi tiết toàn bộ các chức năng trong cấu trúc Quản lý nghiệp vụ.

---

## 3.2 QUẢN LÝ DOANH NGHIỆP LỮ HÀNH

| **Tên Use case** | **Quản lý doanh nghiệp lữ hành** |
| :--- | :--- |
| **Mô tả** | Quản lý danh sách, thông tin giấy phép lữ hành quốc tế/nội địa, người đại diện và trạng thái hoạt động của các công ty lữ hành trên địa bàn. |
| **Tác nhân** | Chuyên viên quản lý nghiệp vụ, Quản trị viên hệ thống, Doanh nghiệp lữ hành |
| **Độ phức tạp** | 🔲 Đơn giản  🔲 Trung bình  ☑️ Phức tạp |
| **Điều kiện bắt đầu** | Người dùng có thẩm quyền đăng nhập hệ thống và chọn menu "Doanh nghiệp lữ hành". |
| **Điều kiện kết thúc** | Thông tin doanh nghiệp lữ hành được cập nhật vào CSDL hoặc thao tác bị hủy bỏ. |
| **Kịch bản chính** | 1. Hệ thống hiển thị danh sách doanh nghiệp lữ hành với các bộ lọc thông minh (loại giấy phép, địa bàn, trạng thái).<br>2. **Thêm mới**: Chọn "Thêm doanh nghiệp" $ightarrow$ Nhập thông tin doanh nghiệp, mã số thuế, số giấy phép lữ hành, ngày cấp $ightarrow$ Nhấn "Lưu" $ightarrow$ Hệ thống kiểm tra trùng lặp mã số thuế/số giấy phép và lưu.<br>3. **Chỉnh sửa**: Chọn biểu tượng Sửa $ightarrow$ Chỉnh sửa thông tin cần thiết $ightarrow$ Nhấn "Lưu" $ightarrow$ Hệ thống cập nhật CSDL.<br>4. **Xóa**: Chọn biểu tượng Xóa $ightarrow$ Xác nhận trên popup $ightarrow$ Hệ thống xóa logic hoặc ẩn dữ liệu doanh nghiệp. |
| **Kịch bản phụ** | - *Trùng số giấy phép/MST:* Hệ thống báo lỗi "Mã số thuế hoặc Số giấy phép đã tồn tại" và yêu cầu kiểm tra lại.<br>- *Doanh nghiệp có ràng buộc tour:* Nếu doanh nghiệp đang vận hành các tour du lịch hiện hành, hệ thống không cho phép xóa vĩnh viễn mà yêu cầu chuyển trạng thái sang "Tạm dừng hoạt động". |
| **Các yêu cầu, ràng buộc** | Mã số thuế và Số giấy phép lữ hành phải đảm bảo tính duy nhất. Định dạng Email và Số điện thoại phải đúng quy chuẩn thanh tra dữ liệu. |

### a. Hiển thị danh sách doanh nghiệp lữ hành
*Hình 3.16: Giao diện danh sách doanh nghiệp lữ hành*

| **Màn hình** | **Danh sách doanh nghiệp lữ hành** |
| :--- | :--- |
| **Mô tả** | Hiển thị toàn bộ danh sách công ty lữ hành. Hỗ trợ tìm kiếm theo tên, mã số thuế và lọc theo phạm vi kinh doanh (Nội địa/Quốc tế). |
| **Màn hình kết nối** | Thêm mới doanh nghiệp, Chỉnh sửa thông tin doanh nghiệp, Xóa doanh nghiệp (Popup) |

**Nội dung màn hình:**
| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Tìm kiếm | Textfield – String | Nhập tên doanh nghiệp hoặc mã số thuế để tìm kiếm. |
| Loại hình lữ hành | Combobox – String | Lọc theo: Tất cả, Lữ hành Quốc tế, Lữ hành Nội địa. |
| Trạng thái | Combobox – String | Lọc theo: Đang hoạt động, Tạm dừng hoạt động, Bị thu hồi giấy phép. |
| Thêm mới | Button | Nút bấm chuyển sang giao diện Thêm doanh nghiệp mới. |
| Bảng danh sách | Table | Hiển thị thông tin doanh nghiệp gồm các cột dữ liệu. |
| *STT* | Label – Number | Số thứ tự dòng. |
| *Mã số thuế* | Label – String | Mã số thuế đồng thời là mã định danh doanh nghiệp. |
| *Tên doanh nghiệp* | Link | Tên doanh nghiệp lữ hành, click để xem chi tiết thông tin. |
| *Số giấy phép* | Label – String | Số giấy phép kinh doanh lữ hành do Cục/Sở Du lịch cấp. |
| *Loại hình* | Label – String | Hiển thị loại hình lữ hành (Nội địa/Quốc tế). |
| *Người đại diện* | Label – String | Tên người đại diện pháp luật của doanh nghiệp. |
| *Trạng thái* | Tag / Badge | Trạng thái hoạt động (Màu xanh: Hoạt động, Đỏ: Thu hồi/Tạm dừng). |
| *Thao tác* | Icon Buttons | Icon Bút (Sửa), Icon Thùng rác (Xóa). |
| Phân trang | Pagination | Điều hướng qua lại giữa các trang dữ liệu. |

**Các chức năng màn hình:**
| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| Tìm kiếm & Lọc | Nhập từ khóa, tiêu chí và chọn Tìm kiếm | Hiển thị danh sách kết quả phù hợp. | Không có dữ liệu, báo "Không tìm thấy kết quả". |
| Điều hướng Thêm mới | Click nút "Thêm mới" | Chuyển đến form Thêm mới doanh nghiệp. | Lỗi hệ thống, giữ nguyên trang. |
| Điều hướng Sửa | Click icon Sửa trên dòng dữ liệu | Chuyển đến form Chỉnh sửa thông tin tương ứng. | Lỗi không tìm thấy ID dữ liệu doanh nghiệp. |

---

### b. Thêm mới doanh nghiệp lữ hành
*Hình 3.17: Biểu mẫu Thêm mới doanh nghiệp lữ hành*

| **Màn hình** | **Thêm mới doanh nghiệp lữ hành** |
| :--- | :--- |
| **Mô tả** | Form nhập thông tin đăng ký doanh nghiệp lữ hành mới vào cơ sở dữ liệu ngành du lịch. |
| **Màn hình kết nối** | Danh sách doanh nghiệp lữ hành |

**Nội dung màn hình:**
| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Tên doanh nghiệp | Textfield – String | Nhập tên đầy đủ theo giấy đăng ký kinh doanh (Bắt buộc). |
| Mã số thuế | Textfield – String | Nhập mã số thuế doanh nghiệp (Bắt buộc, Duy nhất). |
| Số giấy phép | Textfield – String | Nhập số giấy phép lữ hành (Bắt buộc). |
| Loại hình lữ hành | Radio Button | Chọn giữa "Lữ hành Nội địa" hoặc "Lữ hành Quốc tế". |
| Ngày cấp giấy phép | Datepicker | Chọn ngày được cấp giấy phép lữ hành (Bắt buộc). |
| Người đại diện | Textfield – String | Nhập tên người đại diện pháp luật (Bắt buộc). |
| Số điện thoại liên hệ | Textfield – String | Nhập số điện thoại hotline công ty (Bắt buộc). |
| Email doanh nghiệp | Textfield – String | Nhập hòm thư điện tử chính thức. |
| Địa chỉ trụ sở | Textfield – String | Số nhà, tên đường, phường xã của trụ sở chính (Bắt buộc). |
| Nút Lưu lại | Button | Thực hiện kiểm tra validate và lưu dữ liệu. |
| Nút Hủy bỏ | Button | Hủy bỏ thông tin, quay lại màn hình danh sách. |

**Các chức năng màn hình:**
| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| Lưu dữ liệu | Click "Lưu lại" | Lưu thành công vào CSDL, hiển thị alert thông báo thành công và quay lại danh sách. | Báo lỗi đỏ tại các trường trống, trường sai định dạng hoặc trùng MST/Số giấy phép. |
| Hủy bỏ | Click "Hủy bỏ" | Quay lại màn hình danh sách, không lưu bất kỳ thông tin nào. | Giữ nguyên form. |

---

### c. Chỉnh sửa thông tin doanh nghiệp lữ hành
*Hình 3.18: Biểu mẫu Chỉnh sửa thông tin doanh nghiệp lữ hành*

| **Màn hình** | **Chỉnh sửa thông tin doanh nghiệp lữ hành** |
| :--- | :--- |
| **Mô tả** | Tải lên thông tin hiện tại của doanh nghiệp lữ hành và cho phép sửa đổi các trường thông tin cần thiết. |
| **Màn hình kết nối** | Danh sách doanh nghiệp lữ hành |

**Nội dung màn hình:**
| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Mã số thuế | Textfield | Hiển thị mã số thuế cũ. Định dạng: *Read-only* (Không được sửa). |
| Tên doanh nghiệp | Textfield – String | Cho phép chỉnh sửa tên doanh nghiệp. |
| Số giấy phép | Textfield – String | Cho phép cập nhật số giấy phép mới nếu có gia hạn/thay đổi. |
| Trạng thái hoạt động | Dropdown | Cập nhật trạng thái: Đang hoạt động, Tạm dừng, Bị thu hồi giấy phép. |
| Các trường thông tin khác | Thay đổi tùy ý | SĐT, Địa chỉ, Email, Người đại diện... |
| Nút Lưu | Button | Ghi đè thông tin chỉnh sửa vào CSDL. |
| Nút Hủy | Button | Bỏ qua thay đổi và quay lại màn hình danh sách. |

**Các chức năng màn hình:**
| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| Cập nhật dữ liệu | Click "Lưu lại" | Ghi đè dữ liệu thành công, thông báo cập nhật hoàn tất và quay lại danh sách. | Validate lỗi (để trống trường bắt buộc), hệ thống hiển thị thông báo lỗi chi tiết. |

---

### d. Xóa doanh nghiệp lữ hành (Popup xác nhận)
*Hình 3.19: Popup Xác nhận xóa doanh nghiệp lữ hành*

| **Màn hình** | **Xóa doanh nghiệp lữ hành (Popup)** |
| :--- | :--- |
| **Mô tả** | Modal popup cảnh báo xuất hiện xác nhận thao tác xóa doanh nghiệp lữ hành khỏi danh sách hệ thống quản lý. |
| **Màn hình kết nối** | Danh sách doanh nghiệp lữ hành |

**Nội dung màn hình:**
| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Tiêu đề | String (static) | "CẢNH BÁO: XÁC NHẬN XÓA DOANH NGHIỆP" |
| Thông điệp | String (dynamic) | "Bạn có chắc chắn muốn xóa doanh nghiệp lữ hành [Tên_Doanh_Nghiệp] (MST: [MST])? Thao tác này không thể hoàn tác." |
| Nút Xác nhận Xóa | Button (Đỏ) | Thực hiện lệnh xóa dữ liệu logic khỏi hệ thống. |
| Nút Hủy bỏ | Button (Xám) | Đóng popup, giữ nguyên trạng thái dữ liệu. |

**Các chức năng màn hình:**
| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| Thực thi xóa | Chọn "Xác nhận Xóa" | Xóa logic thành công (hoặc ẩn dữ liệu), bảng danh sách cập nhật làm mới lại dữ liệu. | Doanh nghiệp đang có liên kết ràng buộc chặt chẽ với dữ liệu Tour/Tuyến hoạt động $ightarrow$ Hệ thống từ chối xóa và báo lỗi logic. |

---
---

## 3.3 QUẢN LÝ ĐIỂM THAM QUAN / ĐIỂM DU LỊCH

| **Tên Use case** | **Quản lý điểm tham quan / điểm du lịch** |
| :--- | :--- |
| **Mô tả** | Chuyên viên quản lý nghiệp vụ xem danh sách, tìm kiếm, thêm mới, sửa đổi thông tin và tọa độ bản đồ số của các điểm tham quan, di tích văn hóa, điểm check-in du lịch. |
| **Tác nhân** | Chuyên viên quản lý nghiệp vụ, Quản trị viên hệ thống |
| **Độ phức tạp** | 🔲 Đơn giản  ☑️ Trung bình  🔲 Phức tạp |
| **Điều kiện bắt đầu** | Người dùng đăng nhập thành công và truy cập vào menu "Điểm tham quan". |
| **Điều kiện kết thúc** | Thông tin điểm tham quan được lưu vào cơ sở dữ liệu địa lý/hệ thống du lịch hoặc bị hủy bỏ. |
| **Kịch bản chính** | 1. Hệ thống hiển thị danh sách các điểm tham quan hiện hành trên bản đồ và dạng bảng biểu.<br>2. **Thêm mới**: Chọn "Thêm điểm tham quan" $ightarrow$ Nhập tên, loại hình di tích, địa chỉ, giá vé, chấm tọa độ Kinh độ/Vĩ độ trên bản đồ số tích hợp $ightarrow$ Nhấn "Lưu lại".<br>3. **Chỉnh sửa**: Click Sửa $ightarrow$ Form tải dữ liệu cũ kèm ghim vị trí cũ trên bản đồ $ightarrow$ Người dùng sửa thông tin/kéo thả ghim vị trí mới $ightarrow$ Nhấn "Lưu lại".<br>4. **Xóa**: Chọn Xóa $ightarrow$ Xác nhận popup $ightarrow$ Hệ thống gỡ bỏ dữ liệu điểm du lịch. |
| **Kịch bản phụ** | - *Sai lệch tọa độ địa lý:* Hệ thống cảnh báo nếu tọa độ nhập tay nằm ngoài phạm vi ranh giới hành chính của địa phương.<br>- *Ràng buộc dữ liệu:* Nếu điểm tham quan đang gắn liền với các bài viết giới thiệu, tour du lịch đang mở, hệ thống yêu cầu xác nhận ẩn hiển thị thay vì xóa cứng. |
| **Các yêu cầu, ràng buộc** | Tích hợp thư viện bản đồ số (OpenStreetMap / Google Maps API) để lấy chính xác kinh độ (Longitude) và vĩ độ (Latitude). |

### a. Hiển thị danh sách điểm tham quan
*Hình 3.20: Giao diện danh sách điểm tham quan*

| **Màn hình** | **Danh sách điểm tham quan** |
| :--- | :--- |
| **Mô tả** | Hiển thị danh sách các địa danh, điểm tham quan du lịch kèm công cụ lọc theo loại hình di tích/thắng cảnh và địa bàn hành chính. |
| **Màn hình kết nối** | Thêm mới điểm tham quan, Chỉnh sửa điểm tham quan, Xóa điểm tham quan |

**Nội dung màn hình:**
| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Ô tìm kiếm | Textfield – String | Tìm kiếm theo tên địa danh, điểm du lịch. |
| Phân loại điểm | Combobox – String | Lọc theo: Di tích lịch sử, Thắng cảnh tự nhiên, Điểm du lịch tâm linh, Khu vui chơi giải trí. |
| Địa bàn quận/huyện | Combobox – String | Lọc địa danh theo Quận, Huyện, Thị xã. |
| Thêm điểm tham quan | Button | Nút bấm nổi bật điều hướng đến giao diện tạo mới điểm du lịch. |
| Bảng dữ liệu điểm | Table | Bảng thông tin hiển thị các điểm du lịch. |
| *STT* | Label – Number | Số thứ tự điểm. |
| *Mã điểm* | Label – String | Mã định danh duy nhất của điểm du lịch. |
| *Tên điểm tham quan* | Link | Tên địa danh, bấm vào để mở xem chi tiết giới thiệu và hình ảnh. |
| *Loại hình* | Label – String | Loại hình phân loại của điểm du lịch. |
| *Địa chỉ chi tiết* | Label – String | Vị trí hành chính chi tiết của điểm. |
| *Giá vé tham khảo* | Label – String | Mức giá vé người lớn / trẻ em niêm yết công khai. |
| *Tọa độ (X, Y)* | Label – String | Hiển thị dạng chuỗi [Kinh độ, Vĩ độ] phục vụ bản đồ số. |
| *Thao tác* | Icon Buttons | Icon Sửa (Bút), Icon Xóa (Thùng rác). |
| Phân trang | Pagination | Chuyển đổi trang danh sách điểm du lịch. |

**Các chức năng màn hình:**
| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| Bộ lọc và Tìm kiếm | Chọn loại hình, địa bàn và bấm nút Lọc | Hệ thống hiển thị các điểm tham quan thỏa mãn tiêu chí lọc. | Bảng trống nếu không có địa danh nào khớp tiêu chí. |
| Điều hướng biểu mẫu | Click nút Sửa hoặc Thêm mới | Điều hướng sang các biểu mẫu chức năng tương ứng đầy đủ thông tin. | Lỗi hệ thống điều hướng trang. |

---

### b. Thêm mới điểm tham quan
*Hình 3.21: Biểu mẫu Thêm mới điểm tham quan và tích hợp bản đồ*

| **Màn hình** | **Thêm mới điểm tham quan** |
| :--- | :--- |
| **Mô tả** | Cung cấp biểu mẫu điền thông tin chi tiết địa danh du lịch kết hợp cấu phần bản đồ số để chấm/chọn vị trí tọa độ địa lý. |
| **Màn hình kết nối** | Danh sách điểm tham quan |

**Nội dung màn hình:**
| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Tên điểm tham quan | Textfield – String | Nhập tên chính thức của điểm tham quan (Bắt buộc). |
| Phân loại | Dropdown | Chọn danh mục loại hình du lịch (Bắt buộc). |
| Quận/Huyện, Xã/Phường | Dropdown | Chọn phân cấp hành chính nơi điểm tham quan tọa lạc (Bắt buộc). |
| Địa chỉ chi tiết | Textfield – String | Nhập số nhà, thôn, đường chi tiết. |
| Kinh độ (Longitude) | Textfield – Number | Nhập số kinh độ hoặc tự động điền khi click chọn vị trí trên bản đồ. |
| Vĩ độ (Latitude) | Textfield – Number | Nhập số vĩ độ hoặc tự động điền khi click chọn vị trí trên bản đồ. |
| Cấu phần Bản đồ số | Map Component | Khung bản đồ tương tác trực quan, cho phép người dùng click chuột để ghim vị trí lấy tọa độ tự động. |
| Vé người lớn / Trẻ em | Textfield – Number | Điền mức giá vé phục vụ thống kê (Nhập 0 nếu miễn phí). |
| Mô tả/Giới thiệu | Textarea – String | Trình soạn thảo văn bản mô tả tóm tắt lịch sử, nét đặc sắc của điểm. |
| Ảnh đại diện điểm | Upload Component | Tải lên các file ảnh phong cảnh chất lượng cao của điểm du lịch. |
| Nút Lưu dữ liệu | Button | Kiểm tra tính hợp lệ dữ liệu và tiến hành lưu vào hệ thống CSDL không gian GIS. |
| Nút Quay lại | Button | Hủy thao tác, quay về trang danh sách. |

**Các chức năng màn hình:**
| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| Định vị trên bản đồ | Người dùng click vào một điểm trên khung bản đồ số | Hệ thống ghim icon vị trí và tự động trích xuất điền số vào ô Kinh độ, Vĩ độ. | Bản đồ không tải được do lỗi kết nối API bên thứ ba. |
| Lưu dữ liệu | Click chọn nút "Lưu dữ liệu" | Lưu dữ liệu thành công bao gồm cả dữ liệu thuộc tính và không gian tọa độ. | Thiếu trường bắt buộc hoặc tọa độ nằm ngoài ranh giới vùng quy định $ightarrow$ báo lỗi đỏ. |

---

### c. Chỉnh sửa điểm tham quan
*Hình 3.22: Biểu mẫu Chỉnh sửa điểm tham quan*

| **Màn hình** | **Chỉnh sửa điểm tham quan** |
| :--- | :--- |
| **Mô tả** | Giao diện hiển thị thông tin cũ và bản đồ định vị hiện tại của điểm du lịch, cho phép chuyên viên thay đổi mô tả, giá vé hoặc dời ghim vị trí bản đồ. |
| **Màn hình kết nối** | Danh sách điểm tham quan |

**Nội dung màn hình:**
| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Mã điểm tham quan | Textfield | Hiển thị mã điểm du lịch hiện hành (*Read-only*). |
| Tên điểm tham quan | Textfield – String | Thay đổi, cập nhật tên địa danh. |
| Di chuyển ghim bản đồ | Map Component | Người dùng có thể kéo thả ghim cũ sang vị trí mới chính xác hơn trên bản đồ, ô tọa độ tự động cập nhật số mới. |
| Sửa đổi hình ảnh | Upload Component | Cho phép xóa các hình ảnh cũ lỗi thời, tải thêm hình ảnh mới cập nhật. |
| Nút Cập nhật | Button | Lưu đè thông tin chỉnh sửa mới vào CSDL hệ thống. |
| Nút Hủy | Button | Quay lại trang danh sách và hoàn tác các chỉnh sửa vừa nhập tạm. |

**Các chức năng màn hình:**
| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| Lưu cập nhật | Click nút "Cập nhật" | Cập nhật thông tin điểm du lịch thành công, hệ thống chuyển hướng về trang danh sách điểm tham quan. | Gặp lỗi dữ liệu không hợp lệ hoặc lỗi ghi dữ liệu CSDL GIS. |

---

### d. Xóa điểm tham quan (Popup xác nhận)
*Hình 3.23: Hộp thoại Xác nhận xóa điểm tham quan*

| **Màn hình** | **Xóa điểm tham quan (Popup)** |
| :--- | :--- |
| **Mô tả** | Hộp thoại modal thu nhỏ hiển thị đè yêu cầu người dùng xác nhận hành vi xóa điểm tham quan nhằm tránh thao tác nhầm lẫn dữ liệu lịch sử địa danh. |
| **Màn hình kết nối** | Danh sách điểm tham quan |

**Nội dung màn hình:**
| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Tiêu đề popup | String (static) | "XÁC NHẬN XÓA ĐIỂM DU LỊCH / THAM QUAN" |
| Nội dung câu hỏi | String (dynamic) | "Hệ thống sẽ xóa toàn bộ thông tin tọa độ và thuộc tính của điểm tham quan: [Tên_Điểm_Tham_Quan]. Bạn có chắc chắn muốn xóa?" |
| Nút Đồng ý xóa | Button (Đỏ) | Thực thi xóa dữ liệu khỏi hệ thống dữ liệu. |
| Nút Bỏ qua | Button | Đóng cửa sổ popup, bảo toàn dữ liệu. |

**Các chức năng màn hình:**
| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| Xác nhận xóa | Click nút "Đồng ý xóa" | Dữ liệu điểm tham quan bị gỡ bỏ, bảng danh sách tự động làm mới mất dòng dữ liệu đó. | Lỗi ràng buộc hệ thống (điểm tham quan đang nằm trong lộ trình tour cố định không thể xóa cứng) $ightarrow$ Popup hiện thông báo từ chối xóa dữ liệu. |

---
---

## 3.4 QUẢN LÝ CƠ SỞ LƯU TRÚ

| **Tên Use case** | **Quản lý lưu trú** |
| :--- | :--- |
| **Mô tả** | Chuyên viên quản lý nghiệp vụ hoặc doanh nghiệp thực hiện xem danh sách, tìm kiếm, lọc, thêm mới, cập nhật thông tin và xóa thông tin các cơ sở lưu trú du lịch trên địa bàn tỉnh/thành phố. |
| **Tác nhân** | Chuyên viên quản lý nghiệp vụ, Quản trị viên hệ thống, Doanh nghiệp lưu trú |
| **Độ phức tạp** | 🔲 Đơn giản  🔲 Trung bình  ☑️ Phức tạp |
| **Điều kiện bắt đầu** | Người dùng có thẩm quyền đã đăng nhập thành công vào phân hệ quản trị hệ thống CSDL Du lịch. |
| **Điều kiện kết thúc** | Thông tin cơ sở lưu trú được cập nhật, lưu trữ thành công vào cơ sở dữ liệu hệ thống hoặc hành động hủy bỏ được thực hiện. |
| **Kịch bản chính** | 1. Người dùng chọn chức năng "Cơ sở lưu trú" tại menu Quản lý nghiệp vụ. Hệ thống tải và hiển thị danh sách cơ sở lưu trú (có phân trang, hỗ trợ tìm kiếm theo tên và lọc theo địa bàn, loại hình, trạng thái).<br>2. **Thêm mới**: Người dùng click "Thêm cơ sở lưu trú mới" $ightarrow$ Nhập đầy đủ thông tin (tên, loại hình, địa chỉ, số phòng, tiện ích, hình ảnh...) $ightarrow$ Nhấn "Lưu lại" $ightarrow$ Hệ thống kiểm tra hợp lệ và lưu dữ liệu.<br>3. **Chỉnh sửa**: Người dùng click vào icon sửa tại dòng dữ liệu $ightarrow$ Hệ thống tải thông tin cũ lên biểu mẫu $ightarrow$ Người dùng thay đổi thông tin $ightarrow$ Nhấn "Lưu lại" $ightarrow$ Hệ thống cập nhật CSDL.<br>4. **Xóa**: Người dùng click icon xóa $ightarrow$ Hệ thống hiển thị popup xác nhận $ightarrow$ Người dùng chọn "Xác nhận Xóa" $ightarrow$ Hệ thống kiểm tra ràng buộc và thực hiện xóa vĩnh viễn hoặc ẩn dữ liệu. |
| **Kịch bản phụ** | - *Dữ liệu nhập không hợp lệ hoặc thiếu trường bắt buộc:* Hệ thống giữ nguyên giao diện biểu mẫu, đánh dấu đỏ các trường lỗi và hiển thị thông báo yêu cầu hoàn thiện.<br>- *Xóa cơ sở lưu trú có ràng buộc dữ liệu:* Hệ thống từ chối xóa vĩnh viễn nếu có dữ liệu liên quan, hiển thị thông báo lỗi logic và gợi ý người dùng chuyển trạng thái sang "Tạm dừng hoạt động". |
| **Các yêu cầu, ràng buộc** | Hệ thống đảm bảo kết nối internet ổn định, sử dụng giao thức bảo mật HTTPS, tối ưu hóa dung lượng hình ảnh upload, tích hợp bản đồ số để lấy tọa độ địa lý. |

### a. Hiển thị danh sách cơ sở lưu trú
*Hình 3.24: Giao diện danh sách cơ sở lưu trú*

| **Màn hình** | **Danh sách cơ sở lưu trú** |
| :--- | :--- |
| **Mô tả** | Cho phép Quản lý nghiệp vụ theo dõi toàn bộ các cơ sở lưu trú trong hệ thống. Hỗ trợ các công cụ tìm kiếm nhanh, lọc dữ liệu nâng cao, thực hiện điều hướng thêm, sửa, xóa và theo dõi tổng quan số lượng. |
| **Màn hình kết nối** | Thêm mới cơ sở lưu trú, Chỉnh sửa thông tin cơ sở lưu trú, Xóa cơ sở lưu trú (Popup) |

**Nội dung màn hình:**
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

**Các chức năng màn hình:**
| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| Tìm kiếm & Lọc dữ liệu | Người dùng nhập từ khóa hoặc chọn các tiêu chí trên thanh bộ lọc và bấm tìm kiếm. | Hệ thống lọc và hiển thị đúng danh sách các cơ sở lưu trú thỏa mãn điều kiện. | Không tìm thấy dữ liệu phù hợp, hiển thị thông báo "Không tìm thấy dữ liệu". |
| Điều hướng Thêm mới | Người dùng nhấn nút "Thêm cơ sở lưu trú mới". | Điều hướng người dùng sang màn hình biểu mẫu Thêm mới cơ sở lưu trú với các trường trống. | Gặp lỗi điều hướng hoặc lỗi tải trang, hệ thống giữ nguyên màn hình cũ và báo lỗi. |
| Điều hướng Chỉnh sửa | Người dùng nhấn chọn biểu tượng Chỉnh sửa tại dòng dữ liệu mong muốn. | Hệ thống chuyển hướng sang màn hình Chỉnh sửa thông tin cơ sở lưu trú và tải sẵn toàn bộ dữ liệu cũ của cơ sở đó lên biểu mẫu. | Không tải được dữ liệu cơ sở lưu trú do lỗi kết nối CSDL hoặc id không hợp lệ. |
| Yêu cầu Xóa dữ liệu | Người dùng nhấn chọn biểu tượng Xóa tại dòng dữ liệu tương ứng. | Hệ thống hiển thị hộp thoại popup cảnh báo và yêu cầu xác nhận xóa đè lên màn hình danh sách. | Hộp thoại popup không hiển thị được. |

---

### b. Thêm mới cơ sở lưu trú
*Hình 3.25: Biểu mẫu Thêm mới cơ sở lưu trú*

| **Màn hình** | **Thêm mới cơ sở lưu trú** |
| :--- | :--- |
| **Mô tả** | Cung cấp giao diện biểu mẫu cho phép Chuyên viên hoặc Doanh nghiệp nhập và đăng ký một cơ sở lưu trú mới vào cơ sở dữ liệu hệ thống du lịch. |
| **Màn hình kết nối** | Danh sách cơ sở lưu trú (Quay lại sau khi lưu hoặc hủy) |

**Nội dung màn hình:**
| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Tên cơ sở lưu trú | Textfield – String | Nhập tên chính thức của cơ sở lưu trú (Trường bắt buộc). |
| Loại hình lưu trú | Dropdown | Chọn một loại hình trong danh mục có sẵn (Khách sạn, Biệt thự, Homestay...) (Trường bắt buộc). |
| Doanh nghiệp sở hữu | Dropdown / Search | Chọn doanh nghiệp chủ quản quản lý cơ sở lưu trú này (nếu có). |
| Quận / Huyện | Dropdown | Chọn quận, huyện, thị xã trực thuộc địa bàn quản lý (Trường bắt buộc). |
| Phường / Xã | Dropdown | Chọn phường, xã, thị trấn tương ứng dựa theo Quận/Huyện đã chọn (Trường bắt buộc). |
| Địa chỉ chi tiết | Textfield – String | Nhập cụ thể số nhà, ngõ hẻm, tên đường của cơ sở lưu trú (Trường bắt buộc). |
| Số điện thoại | Textfield – String | Nhập số điện thoại liên hệ chính thức của cơ sở (Trường bắt buộc). |
| Email | Textfield – String | Nhập hòm thư điện tử liên hệ. |
| Website | Textfield – String | Nhập địa chỉ website hoặc trang mạng xã hội của cơ sở (nếu có). |
| Số lượng phòng / Sức chứa | Textfield – Number | Nhập tổng số phòng kinh doanh hoặc quy mô sức chứa tối đa. |
| Tiện ích đi kèm | Checkbox List | Tích chọn các tiện ích mà cơ sở cung cấp (Wifi, Hồ bơi, Điều hòa, Bãi đỗ xe, Nhà hàng, Spa...). |
| Hình ảnh cơ sở | Upload Component | Vùng tải lên hình ảnh thực tế của cơ sở lưu trú (Hỗ trợ nhiều ảnh cùng lúc, hiển thị danh sách ảnh preview). |
| Trạng thái hoạt động | Dropdown | Mặc định chọn trạng thái "Đang hoạt động" khi tạo mới, hoặc có thể tùy chỉnh. |
| Hủy | Button | Nút bấm, click để hủy bỏ toàn bộ dữ liệu đang nhập và quay về màn hình danh sách. |
| Lưu lại | Button | Nút bấm (màu xanh), click để hệ thống kiểm tra và thực hiện lưu dữ liệu vào hệ thống. |

**Các chức năng màn hình:**
| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| Lưu thông tin cơ sở lưu trú | Người dùng nhấn nút "Lưu lại" sau khi điền thông tin trên biểu mẫu. | Hệ thống xác thực dữ liệu hợp lệ $ightarrow$ Tiến hành thêm mới dữ liệu vào CSDL $ightarrow$ Hiển thị thông báo thành công $ightarrow$ Tự động chuyển về màn hình danh sách. | Thất bại do: Thiếu trường bắt buộc; dữ liệu sai định dạng; tệp ảnh quá dung lượng $ightarrow$ Giữ nguyên màn hình, hiển thị lỗi chi tiết tại các trường. |
| Hủy bỏ thao tác | Người dùng nhấn nút "Hủy". | Hệ thống hủy bỏ toàn bộ dữ liệu đang nhập trên form (không lưu vào CSDL) và chuyển hướng ngay về giao diện danh sách. | Hệ thống không thực hiện điều hướng, giữ nguyên giao diện hiện tại. |

---

### c. Chỉnh sửa thông tin cơ sở lưu trú
*Hình 3.26: Biểu mẫu Chỉnh sửa thông tin cơ sở lưu trú*

| **Màn hình** | **Chỉnh sửa thông tin cơ sở lưu trú** |
| :--- | :--- |
| **Mô tả** | Cho phép người dùng cập nhật, thay đổi thông tin của một cơ sở lưu trú đã có sẵn trên hệ thống. Giao diện tải lại toàn bộ thông tin cũ của cơ sở lưu trú được chọn. |
| **Màn hình kết nối** | Danh sách cơ sở lưu trú |

**Nội dung màn hình:**
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

**Các chức năng màn hình:**
| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| Lưu lại cập nhật | Người dùng nhấn nút "Lưu lại" sau khi thay đổi thông tin. | Hệ thống kiểm tra dữ liệu hợp lệ $ightarrow$ Ghi đè cập nhật dữ liệu vào CSDL $ightarrow$ Hiển thị thông báo "Cập nhật thành công" $ightarrow$ Quay lại trang danh sách. | Thất bại do dữ liệu sửa để trống các trường bắt buộc hoặc sai định dạng $ightarrow$ Hiển thị thông báo cảnh báo lỗi cụ thể. |
| Hủy chỉnh sửa | Người dùng nhấn nút "Hủy". | Hệ thống bỏ qua các thông tin vừa chỉnh sửa, đóng giao diện biểu mẫu chỉnh sửa và quay lại màn hình danh sách. | Giữ nguyên trạng thái biểu mẫu hiện tại không điều hướng. |

---

### d. Xóa cơ sở lưu trú (Popup xác nhận)
*Hình 3.27: Hộp thoại Xác nhận xóa cơ sở lưu trú*

| **Màn hình** | **Xóa cơ sở lưu trú (Popup)** |
| :--- | :--- |
| **Mô tả** | Hộp thoại xuất hiện ở dạng modal/popup đè lên màn hình danh sách khi người dùng thực hiện thao tác xóa, nhằm mục đích cảnh báo và yêu cầu xác nhận chắc chắn trước khi xóa dữ liệu. |
| **Màn hình kết nối** | Danh sách cơ sở lưu trú |

**Nội dung màn hình:**
| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Tiêu đề hộp thoại | String (static) | Dòng chữ văn bản tĩnh hiển thị nổi bật ở phía trên: **"Xác nhận xóa cơ sở lưu trú"**. |
| Câu hỏi xác nhận | String (dynamic) | Dòng chữ chứa nội dung tên động: **"Bạn có chắc chắn muốn xóa cơ sở lưu trú '[Tên_Cơ_Sở]' khỏi hệ thống?"** |
| LƯU Ý LOGIC HỆ THỐNG | String (static) | Dòng văn bản tĩnh cảnh báo logic: *"Việc xóa cơ sở lưu trú này sẽ ảnh hưởng đến các dữ liệu liên quan (lịch sử lưu trú, thống kê...)."* |
| Hủy bỏ | Button | Nút bấm, click để hủy bỏ hành động xóa và đóng popup. |
| Xác nhận Xóa | Button | Nút bấm hành động (màu đỏ), click để ra lệnh cho hệ thống thực thi xóa vĩnh viễn hoặc ẩn dữ liệu. |

**Các chức năng màn hình:**
| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| Xác nhận Xóa dữ liệu | Người dùng nhấn chọn nút "Xác nhận Xóa" trên popup. | Hệ thống kiểm tra ràng buộc logic thành công $ightarrow$ Thực hiện xóa dữ liệu $ightarrow$ Đóng popup $ightarrow$ Hiển thị thông báo "Xóa thành công" $ightarrow$ Làm mới bảng danh sách dữ liệu. | Thất bại do dữ liệu bị ràng buộc chặt chẽ với các bảng khác đang vận hành không thể xóa $ightarrow$ Hệ thống từ chối xóa, giữ nguyên popup và hiển thị thông báo lỗi logic dữ liệu. |
| Hủy bỏ thao tác xóa | Người dùng nhấn nút "Hủy bỏ" hoặc click ra vùng ngoài. | Hệ thống đóng hộp thoại popup lại ngay lập tức, thông tin được giữ nguyên không có bất kỳ thay đổi nào. | Hộp thoại popup không đóng được. |

---
---

## 3.5 QUẢN LÝ HƯỚNG DẪN VIÊN DU LỊCH

| **Tên Use case** | **Quản lý hướng dẫn viên du lịch** |
| :--- | :--- |
| **Mô tả** | Xem danh sách, tìm kiếm, cấp mới, gia hạn thông tin thẻ hướng dẫn viên du lịch nội địa và quốc tế trên địa bàn quản lý. |
| **Tác nhân** | Chuyên viên quản lý nghiệp vụ, Quản trị viên hệ thống |
| **Độ phức tạp** | 🔲 Đơn giản  ☑️ Trung bình  🔲 Phức tạp |
| **Điều kiện bắt đầu** | Người dùng đăng nhập hệ thống thành công và truy cập vào menu "Hướng dẫn viên". |
| **Điều kiện kết thúc** | Thông tin hồ sơ, số thẻ hướng dẫn viên được cập nhật vào hệ thống lưu trữ hoặc hủy bỏ hành động. |
| **Kịch bản chính** | 1. Hệ thống hiển thị danh sách hướng dẫn viên kèm ảnh thẻ, trạng thái thẻ (Còn hạn/Hết hạn/Bị khóa) và ngôn ngữ hướng dẫn.<br>2. **Thêm mới**: Người dùng click "Cấp thẻ mới" $ightarrow$ Điền thông tin cá nhân, Số thẻ HDV, loại thẻ, ngày cấp, ngày hết hạn, ngoại ngữ thành thạo $ightarrow$ Nhấn "Lưu lại".<br>3. **Chỉnh sửa**: Click Sửa $ightarrow$ Biểu mẫu hiển thị hồ sơ hiện tại $ightarrow$ Thay đổi thông tin hoặc cập nhật ngày gia hạn thẻ $ightarrow$ Nhấn "Lưu lại".<br>4. **Xóa/Khóa thẻ**: Chọn Xóa hoặc Đổi trạng thái khóa $ightarrow$ Hệ thống cập nhật trạng thái thẻ. |
| **Kịch bản phụ** | - *Thẻ hết hạn hệ thống:* Hệ thống tự động chuyển màu cảnh báo đỏ nếu ngày hiện tại vượt quá Ngày hết hạn của thẻ HDV.<br>- *Trùng số thẻ:* Hệ thống báo lỗi nếu Số thẻ hướng dẫn viên nhập vào trùng với một hồ sơ khác đã có sẵn trên hệ thống toàn quốc/tỉnh. |
| **Các yêu cầu, ràng buộc** | Số thẻ hướng dẫn viên du lịch phải chuẩn hóa theo quy định định dạng của Tổng cục Du lịch. Ngày hết hạn phải lớn hơn ngày cấp thẻ. |

### a. Hiển thị danh sách hướng dẫn viên
*Hình 3.28: Giao diện danh sách hướng dẫn viên du lịch*

| **Màn hình** | **Danh sách hướng dẫn viên** |
| :--- | :--- |
| **Mô tả** | Giao diện quản lý danh sách toàn bộ hướng dẫn viên được cấp phép hoạt động, hỗ trợ tra cứu nhanh bằng số thẻ hoặc ngôn ngữ chuyên môn. |
| **Màn hình kết nối** | Cấp thẻ hướng dẫn viên mới, Chỉnh sửa hồ sơ hướng dẫn viên, Khóa/Xóa thẻ (Popup) |

**Nội dung màn hình:**
| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Thanh tìm kiếm | Textfield – String | Tìm kiếm theo Họ và tên hoặc Số thẻ hướng dẫn viên. |
| Phân loại thẻ | Combobox – String | Lọc theo: Thẻ Quốc tế, Thẻ Nội địa. |
| Ngôn ngữ | Combobox – String | Lọc theo ngoại ngữ: Tiếng Anh, Tiếng Trung, Tiếng Nhật, Tiếng Pháp... |
| Trạng thái thẻ | Combobox – String | Lọc theo: Còn hạn hoạt động, Hết hạn, Đang bị tạm khóa thẻ. |
| Cấp thẻ mới | Button | Nút bấm chuyển sang biểu mẫu nhập hồ sơ hướng dẫn viên mới. |
| Danh sách bảng biểu | Table | Hiển thị danh sách chi tiết các hướng dẫn viên. |
| *STT* | Label – Number | Số thứ tự dòng dữ liệu. |
| *Số thẻ HDV* | Label – String | Số hiệu thẻ hướng dẫn viên du lịch chính thức độc nhất. |
| *Họ và tên* | Link | Họ tên hướng dẫn viên, nhấn vào để xem chi tiết lý lịch lịch sử dẫn tour. |
| *Loại thẻ* | Label – String | Hiển thị loại thẻ (Nội địa / Quốc tế). |
| *Ngôn ngữ chính* | Label – String | Danh sách các ngôn ngữ được phép hướng dẫn. |
| *Ngày hết hạn* | Label – Date | Ngày thẻ hết hiệu lực hành nghề. |
| *Trạng thái* | Tag / Badge | Nhãn hiển thị trạng thái thẻ (Xanh: Còn hạn; Đỏ: Hết hạn; Cam: Bị khóa). |
| *Thao tác* | Icon Buttons | Biểu tượng chỉnh sửa hồ sơ hoặc xóa/tạm khóa. |
| Phân trang | Pagination | Thanh phân trang dữ liệu hướng dẫn viên. |

**Các chức năng màn hình:**
| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| Tra cứu hồ sơ | Nhập số thẻ hoặc từ khóa và bấm tìm kiếm | Hệ thống lọc chính xác hướng dẫn viên thỏa mãn điều kiện. | Không tìm thấy, báo "Không tìm thấy thông tin hướng dẫn viên phù hợp". |
| Điều hướng chức năng | Nhấn vào nút Thêm mới hoặc biểu tượng sửa | Hệ thống thực hiện mở form biểu mẫu tương ứng đúng ID đối tượng dữ liệu. | Lỗi hệ thống điều hướng trang không phản hồi. |

---

### b. Thêm mới hồ sơ hướng dẫn viên
*Hình 3.29: Biểu mẫu Đăng ký cấp thẻ hướng dẫn viên*

| **Màn hình** | **Thêm mới hồ sơ hướng dẫn viên** |
| :--- | :--- |
| **Mô tả** | Biểu mẫu cho phép nhập hồ sơ nhân thân và thông tin hành nghề của hướng dẫn viên du lịch mới được cấp phép trên địa bàn. |
| **Màn hình kết nối** | Danh sách hướng dẫn viên |

**Nội dung màn hình:**
| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Họ và tên | Textfield – String | Nhập đầy đủ họ và tên của hướng dẫn viên (Bắt buộc). |
| Số thẻ HDV | Textfield – String | Nhập số hiệu thẻ chính thức (Bắt buộc, Duy nhất). |
| Số CCCD/Hộ chiếu | Textfield – String | Nhập số định danh cá nhân phục vụ đối chiếu xác thực (Bắt buộc). |
| Ngày sinh, Giới tính | Date / Radio | Nhập ngày sinh và chọn giới tính. |
| Số điện thoại, Email | Textfield | Thông tin liên hệ cá nhân (Bắt buộc SĐT). |
| Loại thẻ | Dropdown | Chọn giữa "Thẻ hướng dẫn viên quốc tế" hoặc "Thẻ hướng dẫn viên nội địa". |
| Ngôn ngữ thành thạo | Checkbox List | Chọn các ngôn ngữ được phép hành nghề (Tiếng Việt, Tiếng Anh, Tiếng Pháp, Tiếng Hàn...). |
| Ngày cấp thẻ | Datepicker | Chọn ngày thẻ bắt đầu có hiệu lực (Bắt buộc). |
| Ngày hết hạn thẻ | Datepicker | Chọn ngày thẻ hết hiệu lực (Bắt buộc, phải lớn hơn ngày cấp). |
| Ảnh chân dung HDV | Upload Component | Tải lên file ảnh thẻ 3x4 chính thức của hướng dẫn viên. |
| Nút Lưu hồ sơ | Button | Thực hiện kiểm tra validate toàn bộ và ghi vào cơ sở dữ liệu. |
| Nút Quay lại | Button | Hủy bỏ tác vụ, quay lại màn hình danh sách ban đầu. |

**Các chức năng màn hình:**
| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| Ghi nhận hồ sơ mới | Nhấn chọn nút "Lưu hồ sơ" | Dữ liệu hợp lệ $ightarrow$ Hệ thống tạo mới bản ghi thành công $ightarrow$ Hiển thị alert thông báo và quay lại trang danh sách. | Số thẻ bị trùng hoặc Ngày hết hạn trước ngày cấp $ightarrow$ Hệ thống báo lỗi đỏ tại trường sai phạm, giữ nguyên form nhập liệu. |

---

### c. Chỉnh sửa hồ sơ hướng dẫn viên
*Hình 3.30: Biểu mẫu Chỉnh sửa hồ sơ hướng dẫn viên*

| **Màn hình** | **Chỉnh sửa hồ sơ hướng dẫn viên** |
| :--- | :--- |
| **Mô tả** | Cho phép cập nhật thông tin cá nhân, bổ sung ngôn ngữ hướng dẫn hoặc thực hiện gia hạn thời hạn thẻ hướng dẫn viên khi được cấp đổi. |
| **Màn hình kết nối** | Danh sách hướng dẫn viên |

**Nội dung màn hình:**
| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Số thẻ HDV | Textfield | Hiển thị số thẻ đang chỉnh sửa. Trạng thái: *Read-only*. |
| Thông tin nhân thân | Textfield | Cho phép chỉnh sửa lại Họ tên, SĐT, Email nếu có thay đổi. |
| Cập nhật gia hạn thẻ | Datepicker | Sửa đổi Ngày cấp mới và Ngày hết hạn mới khi hướng dẫn viên làm thủ tục gia hạn thẻ hành nghề thành công. |
| Trạng thái thẻ | Dropdown | Thay đổi trực tiếp trạng thái: Còn hạn, Hết hạn, Tạm khóa thẻ. |
| Nút Lưu cập nhật | Button | Lưu đè toàn bộ các thông tin mới thay đổi vào dữ liệu gốc hệ thống. |
| Nút Hủy | Button | Thoát form chỉnh sửa và không lưu các thông tin vừa thay đổi. |

**Các chức năng màn hình:**
| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| Cập nhật thông tin | Click nút "Lưu cập nhật" | Dữ liệu được ghi đè thành công vào hệ thống, tự động điều hướng quay trở lại trang danh sách hướng dẫn viên. | Nhập sai định dạng thông tin bắt buộc $ightarrow$ Hệ thống giữ nguyên biểu mẫu và đưa ra cảnh báo lỗi cụ thể. |

---

### d. Xóa/Khóa hồ sơ hướng dẫn viên (Popup xác nhận)
*Hình 3.31: Hộp thoại Xác nhận khóa/xóa hồ sơ hướng dẫn viên*

| **Màn hình** | **Khóa/Xóa hồ sơ hướng dẫn viên (Popup)** |
| :--- | :--- |
| **Mô tả** | Cửa sổ popup nhỏ hiển thị đè yêu cầu người dùng xác nhận hành vi xóa vĩnh viễn hồ sơ hướng dẫn viên hoặc chuyển trạng thái sang tạm khóa thẻ hành nghề trên hệ thống. |
| **Màn hình kết nối** | Danh sách hướng dẫn viên |

**Nội dung màn hình:**
| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Tiêu đề cảnh báo | String (static) | "XÁC NHẬN THAO TÁC QUẢN LÝ HỒ SƠ" |
| Nội dung câu hỏi | String (dynamic) | "Bạn có chắc chắn muốn xóa/tạm khóa hồ sơ của hướng dẫn viên: [Họ_Và_Tên] (Số thẻ: [Số_Thẻ]) khỏi danh sách hoạt động?" |
| Nút Xác nhận thực hiện | Button (Đỏ) | Thực thi hành động thay đổi dữ liệu (xóa/khóa). |
| Nút Hủy bỏ | Button | Đóng cửa sổ popup, bảo toàn nguyên trạng dữ liệu gốc. |

**Các chức năng màn hình:**
| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| Xác nhận hành động | Click chọn nút "Xác nhận thực hiện" | Hồ sơ được cập nhật trạng thái xóa logic hoặc khóa thành công, làm mới bảng hiển thị phía dưới. | Gặp lỗi phân quyền hệ thống hoặc lỗi kết nối máy chủ dữ liệu $ightarrow$ Báo lỗi không thực hiện được hành động. |
