### **3.4 QUẢN LÝ LƯU TRÚ**

| **Tên Use case** | **Quản lý cơ sở lưu trú** |
| :--- | :--- |
| **Mô tả** | Chuyên viên quản lý nghiệp vụ (QTV) hoặc Doanh nghiệp lưu trú thực hiện theo dõi danh sách, tìm kiếm, xem chi tiết, thêm mới, chỉnh sửa, xóa và phê duyệt/từ chối phê duyệt trạng thái của các cơ sở lưu trú trên địa bàn. |
| **Tác nhân** | Chuyên viên quản lý nghiệp vụ (Admin/QTV), Doanh nghiệp lưu trú |
| **Độ phức tạp** | ☑️ Phức tạp |
| **Điều kiện bắt đầu** | Người dùng có thẩm quyền đã đăng nhập thành công vào phân hệ quản trị hệ thống CSDL Du lịch Huế. |
| **Điều kiện kết thúc** | Thông tin cơ sở lưu trú được cập nhật, lưu trữ thành công vào bảng `DuLich_CoSoLuuTru` và các bảng liên kết liên quan hoặc hành động hủy bỏ được thực hiện. |
| **Kịch bản chính** | 1. Người dùng chọn chức năng "Quản lý lưu trú" tại menu Quản lý nghiệp vụ. Hệ thống tải và hiển thị danh sách cơ sở lưu trú (phân trang, hỗ trợ bộ lọc nâng cao).<br>2. **Xem chi tiết**: Người dùng bấm vào tên cơ sở lưu trú $\rightarrow$ Hệ thống hiển thị toàn bộ thông tin chi tiết dựa trên dữ liệu bảng CSDL.<br>3. **Thêm mới/Sửa**: Người dùng nhập thông tin (tên, loại hình, địa bàn, tọa độ, tiện ích...) $\rightarrow$ Nhấn "Lưu lại" $\rightarrow$ Hệ thống kiểm tra hợp lệ và cập nhật CSDL.<br>4. **Xóa**: Người dùng bấm nút xóa $\rightarrow$ Xác nhận tại popup $\rightarrow$ Hệ thống ẩn hoặc xóa bản ghi theo ràng buộc dữ liệu.<br>5. **Phê duyệt / Từ chối**: QTV xem xét hồ sơ lưu trú do doanh nghiệp nộp, thực hiện bấm phê duyệt hoặc nhập lý do từ chối để cập nhật trạng thái hoạt động. |
| **Kịch bản phụ** | - *Thiếu trường dữ liệu bắt buộc:* Hệ thống hiển thị thông báo lỗi tại trường đó và yêu cầu bổ sung.<br>- *Trùng lặp dữ liệu tọa độ hoặc tên cơ sở:* Hệ thống đưa ra cảnh báo trùng lặp để người dùng kiểm tra lại trước khi lưu. |
| **Các yêu cầu, ràng buộc** | Đồng bộ dữ liệu tệp tin hình ảnh với bảng `DuLich_TepTin`. Liên kết tiện ích qua bảng `LienKet_LuuTru_TienIch`. Tích hợp bản đồ số để kiểm tra trường `ToaDo`. |

---

#### **a. Danh sách cơ sở lưu trú**
<p align="center"><i>Hình 3.4.1: Giao diện Danh sách cơ sở lưu trú</i></p>

| **Màn hình** | **Danh sách cơ sở lưu trú** |
| :--- | :--- |
| **Mô tả** | Cho phép người dùng xem danh sách, lọc theo địa bàn, loại hình lưu trú và tìm kiếm nhanh các cơ sở lưu trú du lịch. |
| **Màn hình kết nối** | Xem chi tiết cơ sở lưu trú, Thêm cơ sở lưu trú, Sửa cơ sở lưu trú, Popup Phê duyệt/Từ chối |

**Nội dung màn hình:**
| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Ô tìm kiếm | Textfield – String | Tìm kiếm theo tên cơ sở lưu trú (`TenCoSo`). |
| Lọc loại hình | Combobox – String | Lọc theo loại hình lưu trú (`LoaiLuuTruID` từ `DanhMuc_LoaiHinhLuuTru`). |
| Lọc địa bàn | Combobox – String | Lọc theo xã/phường/quận/huyện (`PhuongXaID` từ `DanhMuc_PhuongXa`). |
| Lọc trạng thái | Combobox – String | Lọc theo `TrangThai` (0: Ẩn, 1: Hiển thị/Hoạt động, 2: Chờ phê duyệt). |
| Nút Thêm mới | Button | Click để mở biểu mẫu Thêm cơ sở lưu trú mới. |
| Bảng danh sách | Table | Hiển thị danh sách các bản ghi từ bảng `DuLich_CoSoLuuTru`. |
| *STT* | Label – Number | Số thứ tự hiển thị. |
| *Tên cơ sở* | Link | Tên cơ sở lưu trú (`TenCoSo`), bấm vào điều hướng đến màn hình Xem chi tiết. |
| *Loại hình* | Label – String | Tên loại hình hiển thị tương ứng với mã `LoaiLuuTruID`. |
| *Địa chỉ* | Label – String | Địa chỉ cụ thể (`DiaChi`). |
| *Hạng sao* | Label – Number | Hiển thị số lượng sao vàng tương ứng với cột `HangSao` (1-5 sao). |
| *Trạng thái* | Badge | Trạng thái hiển thị (Xanh: Hoạt động, Đỏ: Ẩn, Vàng: Chờ duyệt). |
| *Thao tác* | Icon Buttons | Các nút: Chỉnh sửa (Bút), Xóa (Thùng rác), Phê duyệt nhanh (Tích chọn). |
| Thanh phân trang | Pagination | Điều hướng trang danh sách dữ liệu. |

**Các chức năng màn hình:**
| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| Tìm kiếm và Lọc | Người dùng nhập tên hoặc chọn tiêu chí lọc và nhấn Enter/nút Tìm kiếm. | Hệ thống lọc danh sách và hiển thị các cơ sở lưu trú thỏa mãn điều kiện. | Không có bản ghi nào khớp, hiển thị "Không tìm thấy dữ liệu". |

---

#### **b. Xem chi tiết cơ sở lưu trú**
<p align="center"><i>Hình 3.4.2: Giao diện Xem chi tiết cơ sở lưu trú</i></p>

| **Màn hình** | **Xem chi tiết cơ sở lưu trú** |
| :--- | :--- |
| **Mô tả** | Màn hình hiển thị toàn bộ thông tin chi tiết của một cơ sở lưu trú cụ thể dựa trên cấu trúc cơ sở dữ liệu của bảng `DuLich_CoSoLuuTru`. |
| **Màn hình kết nối** | Danh sách cơ sở lưu trú, Chỉnh sửa cơ sở lưu trú |

**Nội dung màn hình (Thiết kế dựa trên CSDL `DuLich_CoSoLuuTru`):**
| **Mục hiển thị** | **Trường CSDL tương ứng** | **Kiểu dữ liệu hiển thị** | **Mô tả chi tiết** |
| :--- | :--- | :--- | :--- |
| **Mã cơ sở lưu trú** | `LuuTruID` (PK) | Label – UUID | Chuỗi định danh duy nhất của cơ sở lưu trú. |
| **Tên cơ sở lưu trú** | `TenCoSo` | Label – String | Tên chính thức của cơ sở lưu trú. |
| **Doanh nghiệp chủ quản**| `DoanhNghiepID` (FK) | Link – String | Hiển thị tên doanh nghiệp sở hữu (Lấy từ bảng `DuLich_DoanhNghiep`). |
| **Địa bàn (Phường/Xã)** | `PhuongXaID` (FK) | Label – String | Tên đơn vị hành chính cấp xã/phường (Lấy từ `DanhMuc_PhuongXa`). |
| **Loại hình lưu trú** | `LoaiLuuTruID` (FK) | Label – String | Khách sạn, Resort, Homestay, v.v. (Lấy từ `DanhMuc_LoaiHinhLuuTru`). |
| **Địa chỉ chi tiết** | `DiaChi` | Label – String | Số nhà, tên đường, khu vực của cơ sở. |
| **Xếp hạng sao** | `HangSao` | Icon Stars – Number | Biểu tượng sao tương ứng từ 1 đến 5 sao (hoặc chưa xếp sao). |
| **Tọa độ địa lý** | `ToaDo` | Label – String | Tọa độ GPS định vị dạng chuỗi `lat,lng` kèm bản đồ trực quan. |
| **Mô tả chi tiết** | `MoTa` | BlockText – HTML | Nội dung giới thiệu chi tiết về cơ sở vật chất, phòng ốc. |
| **Trạng thái hoạt động** | `TrangThai` | Badge – Smallint | Hiển thị nhãn: 0 (Tạm ẩn/Ngừng hiển thị), 1 (Đang hoạt động/Hiển thị). |
| **Danh sách tiện ích** | Kết nối qua `LienKet_LuuTru_TienIch` | Tags / Badges List | Danh sách các tiện ích đi kèm (Wifi, Hồ bơi, Điều hòa...) lấy từ `DanhMuc_TienIch`. |
| **Hình ảnh / Album ảnh**| Kết nối qua `DuLich_TepTin` | Image Gallery | Bộ sưu tập hình ảnh có `LoaiDoiTuong='LuuTru'` và `DoiTuongID=LuuTruID`. |

**Các chức năng màn hình:**
| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| Tải dữ liệu chi tiết | Tự động chạy khi truy cập bằng ID hợp lệ. | Hiển thị đầy đủ thông tin chi tiết và bản đồ, hình ảnh đính kèm. | ID không tồn tại, báo lỗi "Dữ liệu không hợp lệ hoặc đã bị xóa" và quay lại trang danh sách. |
| Nút Quay lại | Quay về trang danh sách trước đó. | Chuyển hướng thành công. | Không áp dụng. |

---

#### **c. Thêm cơ sở lưu trú**
<p align="center"><i>Hình 3.4.3: Giao diện Thêm mới cơ sở lưu trú</i></p>

| **Màn hình** | **Thêm mới cơ sở lưu trú** |
| :--- | :--- |
| **Mô tả** | Biểu mẫu nhập liệu cho phép tạo mới một cơ sở lưu trú vào hệ thống. |
| **Màn hình kết nối** | Danh sách cơ sở lưu trú |

**Nội dung màn hình (Form nhập liệu):**
| **Trường nhập liệu** | **Thành phần giao diện** | **Ràng buộc / Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- | :--- |
| Tên cơ sở lưu trú | Textbox | String, Bắt buộc, Tối đa 255 ký tự. | Nhập tên chính xác của cơ sở lưu trú. |
| Doanh nghiệp sở hữu | Dropdown | UUID (FK), Bắt buộc. | Chọn doanh nghiệp chủ quản từ danh sách doanh nghiệp lưu trú. |
| Địa bàn (Phường/Xã) | Dropdown | UUID (FK), Bắt buộc. | Chọn Phường/Xã thuộc tỉnh Thừa Thiên Huế. |
| Loại hình lưu trú | Dropdown | UUID (FK), Bắt buộc. | Chọn loại hình (Khách sạn, Resort, Homestay...). |
| Địa chỉ chi tiết | Textbox | String, Bắt buộc, Tối đa 255 ký tự. | Nhập địa chỉ số nhà, tên đường cụ thể. |
| Xếp hạng sao | Dropdown | Smallint, Cho phép chọn từ 1 đến 5 hoặc để trống. | Chọn số sao xếp hạng của cơ sở. |
| Tọa độ GPS | Textbox + Bản đồ số | String (`lat,lng`), Cho phép click chọn vị trí trực tiếp trên bản đồ. | Kinh độ và vĩ độ của cơ sở. |
| Mô tả cơ sở | Rich Text Editor | Text, Tùy chọn nhập. | Nội dung mô tả chi tiết, dịch vụ phòng. |
| Chọn danh sách tiện ích| Checkbox List | Mảng các UUID tiện ích được tick chọn. | Lưu vào bảng trung gian `LienKet_LuuTru_TienIch`. |
| Tải ảnh lên | File Upload Button | File Image (png, jpg), Tối đa 5MB/file. | Upload hình ảnh cơ sở, lưu vào `DuLich_TepTin`. |

**Các chức năng màn hình:**
| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| Lưu dữ liệu | Người dùng bấm nút "Lưu lại" để ghi nhận thông tin. | Hệ thống kiểm tra hợp lệ, thêm dữ liệu vào bảng `DuLich_CoSoLuuTru`, bảng tiện ích, tệp tin và thông báo "Thêm mới thành công". | Thiếu trường bắt buộc hoặc upload sai định dạng file, hiển thị lỗi đỏ tại vị trí đó. |

---

#### **d. Sửa cơ sở lưu trú**
- **Mô tả:** Giao diện tương tự form Thêm mới, nhưng hệ thống tự động đổ (binding) dữ liệu hiện tại của cơ sở lưu trú lên các trường nhập liệu tương ứng dựa vào `LuuTruID`.
- **Thao tác:** Người dùng thay đổi thông tin cần cập nhật và nhấn "Cập nhật". Hệ thống thực hiện lệnh `UPDATE` vào CSDL đối với các trường có sự thay đổi. Trạng thái lưu thành công sẽ có thông báo pop-up "Cập nhật dữ liệu thành công" và quay lại màn hình chi tiết hoặc danh sách.

---

#### **e. Xóa cơ sở lưu trú**
- **Mô tả:** Chức năng này được thực hiện thông qua một Popup xác nhận xóa khi người dùng bấm vào icon thùng rác ở danh sách.
- **Ràng buộc:** Hệ thống sẽ kiểm tra ràng buộc toàn vẹn dữ liệu. Nếu cơ sở lưu trú này đang có các ràng buộc dữ liệu hoạt động phức tạp như đang nằm trong các tour du lịch hiện hành hoặc có phản hồi du khách chưa xử lý, hệ thống sẽ tự động khuyến nghị người dùng thay đổi cột `TrangThai = 0` (Tạm ẩn) thay vì thực hiện lệnh `DELETE` vật lý khỏi CSDL để bảo toàn lịch sử hệ thống.

---

#### **f. Phê duyệt cơ sở lưu trú**
- **Mô tả:** Khi một Doanh nghiệp tự khai báo thông tin cơ sở lưu trú mới, bản ghi ban đầu sẽ ở trạng thái `TrangThai = 2` (Chờ phê duyệt). Chuyên viên nghiệp vụ (QTV) sẽ mở màn hình xem xét và bấm nút **"Phê duyệt"**.
- **Kết quả thành công:** Hệ thống cập nhật trường `TrangThai = 1` (Hiển thị/Hoạt động) trong bảng `DuLich_CoSoLuuTru`, ghi nhận thời gian phê duyệt và cho phép cơ sở này xuất hiện trên ứng dụng di động công cộng của du khách.

---

#### **g. Từ chối phê duyệt cơ sở lưu trú**
- **Mô tả:** Trong giao diện xem xét phê duyệt, nếu hồ sơ không hợp lệ, QTV bấm nút **"Từ chối phê duyệt"**.
- **Giao diện yêu cầu:** Hệ thống hiển thị một Popup yêu cầu QTV nhập lý do từ chối (chuỗi văn bản ký tự tự do).
- **Kết quả thành công:** Hệ thống cập nhật trạng thái bản ghi về dạng từ chối (hoặc tạm khóa), lưu lý do vào hệ thống lịch sử logs, gửi thông báo phản hồi lỗi hồ sơ về tài khoản doanh nghiệp nộp để yêu cầu sửa đổi lại thông tin.

---

### **3.5 QUẢN LÝ LỮ HÀNH VÀ HDV**

#### **3.5.1 Đơn vị lữ hành**

| **Tên Use case** | **Quản lý đơn vị lữ hành** |
| :--- | :--- |
| **Mác nhân** | Chuyên viên quản lý nghiệp vụ, Quản trị viên hệ thống |
| **Mô tả** | Theo dõi và quản lý hồ sơ thông tin hoạt động kinh doanh của các đơn vị, công ty lữ hành trên địa bàn tỉnh, đảm bảo dữ liệu chính xác để kết nối phục vụ quản lý tour du lịch. |

##### **a. Danh sách đơn vị lữ hành**
- **Giao diện:** Bộ lọc tìm kiếm theo Tên công ty lữ hành (`TenCongTy`), lọc theo địa bàn hành chính quận/huyện (`PhuongXaID`).
- **Bảng dữ liệu hiển thị:** STT, Mã lữ hành, Tên công ty lữ hành, Địa chỉ văn phòng, Số điện thoại, Trạng thái (Hoạt động/Tạm ẩn).
- **Chức năng:** Hỗ trợ tìm kiếm, phân trang và nút thêm/sửa/xóa nhanh đơn vị lữ hành.

##### **b. Xem chi tiết đơn vị lữ hành (Thiết kế theo CSDL `DuLich_LuHanh`)**
- **Mã lữ hành:** `LuHanhID` (Label - UUID).
- **Doanh nghiệp chủ quản:** `DoanhNghiepID` (Link kết nối sang bảng `DuLich_DoanhNghiep` để xem thông tin pháp lý, mã số thuế).
- **Tên công ty lữ hành:** `TenCongTy` (Label - NVARCHAR).
- **Địa bàn hành chính:** `PhuongXaID` (Label - Tên đơn vị Phường/Xã từ `DanhMuc_PhuongXa`).
- **Loại hình dịch vụ:** `LoaiDichVuID` (Label - Liên kết từ `DanhMuc_LoaiHinhDichVu`).
- **Địa chỉ văn phòng:** `DiaChi` (Label - NVARCHAR).
- **Mô tả giới thiệu:** `MoTa` (Khung văn bản HTML hiển thị năng lực lữ hành, giấy phép lữ hành quốc tế/nội địa nếu có).
- **Tọa độ văn phòng:** `ToaDo` (Chuỗi tọa độ kết nối định vị bản đồ Map).
- **Trạng thái hoạt động:** `TrangThai` (Badge: 0 - Ẩn, 1 - Hoạt động).
- **Tiện ích đi kèm:** Danh sách tags liên kết lấy từ bảng `LienKet_LuHanh_TienIch`.

---

#### **3.5.2 Hướng dẫn viên**

| **Tên Use case** | **Quản lý hướng dẫn viên** |
| :--- | :--- |
| **Tác nhân** | Chuyên viên quản lý nghiệp vụ, Doanh nghiệp lữ hành chủ quản |
| **Mô tả** | Quản lý thông tin cá nhân, số thẻ hành nghề, ngôn ngữ chuyên môn và trạng thái phân công của đội ngũ hướng dẫn viên du lịch. |

##### **a. Danh sách hướng dẫn viên**
- **Bộ lọc tìm kiếm:** Tìm theo tên hướng dẫn viên (`HoTen`), Số thẻ hành nghề (`SoTheHDV`), lọc theo Ngôn ngữ (`NgonNgu`) (Tiếng Anh, Tiếng Pháp, Tiếng Trung, Tiếng Nhật...) và Công ty lữ hành quản lý.
- **Bảng dữ liệu:** STT, Họ và tên, Số thẻ HDV, Ngôn ngữ chính, Số điện thoại, Tên công ty chủ quản, Trạng thái hoạt động (`TrangThai`).

##### **b. Xem chi tiết hướng dẫn viên (Thiết kế theo CSDL `DuLich_HDV`)**
- **Mã định danh HDV:** `HDVID` (Label - UUID).
- **Đơn vị lữ hành quản lý:** `LuHanhID` (Link kết nối hiển thị tên công ty lữ hành chủ quản của HDV).
- **Họ và tên:** `HoTen` (Label - NVARCHAR).
- **Số thẻ hành nghề:** `SoTheHDV` (Label - String - Mã số thẻ hướng dẫn viên du lịch do sở cấp).
- **Ngôn ngữ hướng dẫn:** `NgonNgu` (Label - Chuỗi danh sách ngôn ngữ thành thạo).
- **Số điện thoại:** `SDT` (Label - String).
- **Email liên hệ:** `Email` (Label - String).
- **Trạng thái hành nghề:** `TrangThai` (Badge: 0 - Nghỉ việc/Tạm dừng thẻ; 1 - Đang hoạt động).
- **Hồ sơ đính kèm:** Hình ảnh chân dung, ảnh chụp 2 mặt của thẻ HDV kết nối từ bảng `DuLich_TepTin` (`LoaiDoiTuong='HDV'`).
- **Lịch sử dẫn tour:** Bảng hiển thị danh sách các tour HDV này đã hoặc đang tham gia phụ trách được kết xuất từ bảng liên kết dữ liệu `LienKet_Tour_HDV`.

---

#### **3.5.3 Tour du lịch**

| **Tên Use case** | **Quản lý chương trình tour du lịch** |
| :--- | :--- |
| **Tác nhân** | Doanh nghiệp lữ hành (Người tạo), Chuyên viên quản lý nghiệp vụ (Người giám sát/Cấp phép) |
| **Mô tả** | Thiết lập thông tin gói chương trình du lịch, lịch trình di chuyển, giá cả, thời gian và thực hiện phân công hướng dẫn viên phụ trách. |

##### **a. Danh sách tour du lịch**
- **Giao diện bộ lọc:** Lọc theo Đơn vị lữ hành tổ chức, Lọc theo khoảng giá tour (`GiaTour`), Lọc theo Địa bàn tập trung chủ yếu (`PhuongXaID`), và trạng thái cấp phép (`CapPhep`).
- **Bảng hiển thị:** STT, Tên chương trình tour, Công ty lữ hành, Thời lượng, Giá bán, Trạng thái cấp phép (Đã cấp phép / Chưa cấp phép), Thao tác (Xem, Sửa, Phân công HDV).

##### **b. Xem chi tiết tour du lịch (Thiết kế theo CSDL `DuLich_Tour`)**
- **Mã số Tour:** `TourID` (Label - UUID).
- **Đơn vị lữ hành tổ chức:** `LuHanhID` (Link hiển thị thông tin chi tiết đơn vị tạo tour).
- **Hướng dẫn viên phụ trách chính:** `HDVID` (Link hiển thị tên HDV được gán mặc định ban đầu nếu có).
- **Địa bàn trọng tâm của tour:** `PhuongXaID` (Label - Xác định tour hoạt động thuộc quận/huyện/xã nào).
- **Tên gọi chương trình tour:** `TenTour` (Label - NVARCHAR, ví dụ: *"Khám phá phá Tam Giang - Phú Vang"*).
- **Thời lượng tour:** `ThoiGian` (Label - String, ví dụ: *"1 ngày"*, *"2 ngày 1 đêm"*).
- **Giá bán của tour du lịch:** `GiaTour` (Label - Decimal hiển thị định dạng tiền tệ VND, ví dụ: *1,250,000 đ*).
- **Mô tả lịch trình chi tiết:** `MoTaLichTrinh` (Khung hiển thị Text dài / HTML trình bày lịch trình chi tiết theo mốc thời gian: Sáng, Trưa, Tối, các điểm dừng chân tham quan).
- **Trạng thái cấp phép:** `CapPhep` (Badge: 0 - Chưa cấp phép / Đang chờ duyệt nội dung; 1 - Đã cấp phép mở bán rộng rãi).
- **Trạng thái kinh doanh:** `TrangThai` (Toggle Switch hiển thị: 0 - Tạm ẩn/Dừng nhận khách; 1 - Đang hoạt động/Mở bán công khai).
- **Ngày tạo lập:** `NgayTao` (Label - Datetime).
- **Danh sách HDV tham gia theo ngày:** Bảng danh sách chi tiết liên kết từ bảng `LienKet_Tour_HDV` gồm các cột: *Tên Hướng dẫn viên*, *Ngày khởi hành phụ trách cụ thể*, *Ghi chú nhiệm vụ*.

---

### **3.6 QUẢN LÝ ĂN UỐNG & MUA SẮM**

| **Tên Use case** | **Quản lý dịch vụ ăn uống và điểm mua sắm** |
| :--- | :--- |
| **Mô tả** | Theo dõi, quản lý, chuẩn hóa thông tin cơ sở dữ liệu về các nhà hàng, quán ăn đặc sản, trung tâm thương mại, cửa hàng quà lưu niệm du lịch trên địa bàn tỉnh Huế. |

#### **a. Danh sách quán ăn và mua sắm**
- **Thành phần lọc:** Ô tìm kiếm tên cơ sở, Combobox phân loại dịch vụ (`LoaiDichVuID`: Nhà hàng, Quán ăn, Cửa hàng đặc sản, Siêu thị lưu niệm...), Dropdown địa bàn xã/phường.
- **Bảng kết quả:** STT, Tên cơ sở ăn uống/mua sắm, Phân loại, Địa chỉ, Số điện thoại, Trạng thái hiển thị trên app du lịch.

#### **b. Xem chi tiết quán ăn và mua sắm (Thiết kế theo CSDL `DuLich_AnUongMuaSam`)**
- **Mã dịch vụ:** `DichVuID` (Label - UUID).
- **Doanh nghiệp khai thác sở hữu:** `DoanhNghiepID` (Link liên kết thông tin chủ quản doanh nghiệp).
- **Địa bàn hành chính:** `PhuongXaID` (Label - Phường/Xã tra cứu từ danh mục).
- **Loại hình dịch vụ:** `LoaiDichVuID` (Label - NVARCHAR hiển thị thể loại cụ thể).
- **Tên cơ sở dịch vụ:** `TenCoSo` (Label - NVARCHAR, tên quán ăn/nhà hàng/điểm mua sắm).
- **Địa chỉ chi tiết:** `DiaChi` (Label - NVARCHAR).
- **Mô tả dịch vụ:** `MoTa` (Khung văn bản RichText mô tả thực đơn đặc sản, không gian, giờ mở cửa, các mặt hàng lưu niệm kinh doanh chủ yếu).
- **Tọa độ vị trí địa lý:** `ToaDo` (Chuỗi `lat,lng` kết nối hiển thị bản đồ số để du khách tìm đường di chuyển).
- **Trạng thái hoạt động:** `TrangThai` (Badge: 0 - Ẩn, 1 - Hiển thị trên hệ thống).
- **Danh mục tiện ích đi kèm:** Lấy dữ liệu qua bảng liên kết `LienKet_AnUong_TienIch` (Ví dụ: Có bãi đỗ xe ô tô đoàn, có phòng VIP, thanh toán thẻ VISA, hỗ trợ đóng gói giao hàng tận nơi).
- **Album hình ảnh thực tế:** Hình ảnh không gian, món ăn, sản phẩm liên kết từ bảng `DuLich_TepTin` có mã `LoaiDoiTuong='AnUongMuaSam'`.

---

### **3.7 QUẢN LÝ ĐIỂM ĐẾN**

| **Tên Use case** | **Quản lý danh mục điểm đến du lịch** |
| :--- | :--- |
| **Mô tả** | Quản lý toàn bộ thông tin tài nguyên du lịch cốt lõi bao gồm di tích lịch sử cố đô, danh lam thắng cảnh tự nhiên, các làng nghề truyền thống và các điểm check-in du lịch cộng đồng. |

#### **a. Danh sách điểm đến**
- **Bộ lọc:** Tìm kiếm tên điểm đến (`TenDiemDen`), Lọc theo phân loại loại hình điểm đến (`LoaiDiemDenID` từ `DanhMuc_LoaiHinhDiemDen`), Lọc theo quận/huyện hành chính.
- **Bảng dữ liệu hiển thị:** STT, Tên điểm đến, Loại hình tài nguyên, Địa chỉ khu vực, Trạng thái số hóa, Nút xem bản đồ trực quan.

#### **b. Xem chi tiết điểm đến (Thiết kế theo CSDL `DuLich_DiemDen`)**
- **Mã điểm đến:** `DiemDenID` (Label - UUID).
- **Loại hình điểm đến:** `LoaiDiemDenID` (Label - Hiển thị thể loại: *Di tích lịch sử, Thắng cảnh thiên nhiên, Làng nghề truyền thống, Điểm du lịch tâm linh*).
- **Địa bàn quản lý:** `PhuongXaID` (Label - Tên phường/xã sở tại).
- **Tên điểm đến:** `TenDiemDen` (Label - NVARCHAR - Ví dụ: *"Đại Nội Huế"*, *"Lăng Khải Định"*, *"Chùa Thiên Mụ"*, *"Làng nón Phú Cam"*).
- **Địa chỉ cụ thể:** `DiaChi` (Label - NVARCHAR).
- **Mô tả nội dung, lịch sử:** `MoTa` (Khung văn bản HTML dung lượng lớn, chứa bài viết thuyết minh giới thiệu chi tiết về lịch sử hình thành, giá trị kiến trúc nghệ thuật, thông tin giá vé tham quan và giờ mở cửa).
- **Tọa độ bản đồ GPS:** `ToaDo` (Mã vị trí chính xác phục vụ chức năng quét định vị xung quanh của ứng dụng di động).
- **Trạng thái hệ thống:** `TrangThai` (Badge: 0 - Ẩn dữ liệu; 1 - Hiển thị công khai phục vụ bản đồ số du lịch).
- **Tiện ích tại điểm đến:** Kết nối qua `LienKet_DiemDen_TienIch` (Ví dụ: Có lối đi cho người khuyết tật, thuyết minh tự động Audio Guide, bãi đỗ xe, nhà vệ sinh công cộng đạt chuẩn).
- **Tệp tin đa phương tiện:** Hình ảnh độ phân giải cao, video giới thiệu 360 độ liên kết từ bảng `DuLich_TepTin`.

---

### **3.8 QUẢN LÝ LỄ HỘI VÀ SỰ KIỆN**

| **Tên Use case** | **Quản lý lịch trình lễ hội và sự kiện du lịch** |
| :--- | :--- |
| **Mô tả** | Lập kế hoạch, quản lý thông tin các chương trình lễ hội văn hóa (Festival Huế, lễ hội điện Hòn Chén, đua ghe truyền thống...) và các sự kiện thể thao, giải trí diễn ra trên địa bàn tỉnh theo thời gian thực. |

#### **a. Danh sách lễ hội và sự kiện**
- **Bộ lọc:** Tìm tên sự kiện (`TenSuKien`), lọc theo trạng thái diễn ra (Sắp diễn ra, Đang diễn ra, Đã kết thúc, Đã hủy), bộ lọc khoảng thời gian (`NgayBatDau` đến `NgayKetThuc`).
- **Bảng dữ liệu hiển thị:** STT, Tên lễ hội/sự kiện, Địa điểm tổ chức, Thời gian bắt đầu, Thời gian kết thúc, Trạng thái (Badge màu sắc phân biệt), Thao tác nhanh.

#### **b. Xem chi tiết lễ hội và sự kiện (Thiết kế theo CSDL `DuLich_LeHoiSuKien`)**
- **Mã số sự kiện:** `SuKienID` (Label - UUID).
- **Địa bàn diễn ra:** `PhuongXaID` (Label - Tên đơn vị hành chính quản lý khu vực tổ chức).
- **Tên lễ hội / sự kiện:** `TenSuKien` (Label - NVARCHAR, Ví dụ: *"Festival Huế 2026"*, *"Lễ hội Áo dài Cố đô"*, *"Giải Chạy VnExpress Marathon Hue"*).
- **Địa điểm tổ chức cụ thể:** `DiaDiem` (Label - NVARCHAR, Ví dụ: *"Quảng trường Ngọ Môn"*, *"Bia Quốc Học"*, *"Trục đường Lê Lợi"*).
- **Mô tả nội dung sự kiện:** `MoTa` (Khung văn bản RichText hiển thị chi tiết chương trình, các hoạt động chính, đơn vị tổ chức thực hiện, thông tin vé mời hoặc miễn phí tham gia).
- **Thời điểm bắt đầu:** `NgayBatDau` (Label - Định dạng ngày giờ DD/MM/YYYY HH:MM).
- **Thời điểm kết thúc:** `NgayKetThuc` (Label - Định dạng ngày giờ DD/MM/YYYY HH:MM).
- **Trạng thái tổ chức:** `TrangThai` (Badge: 0 - Đã hủy tổ chức; 1 - Sắp diễn ra; 2 - Đang diễn ra; 3 - Đã kết thúc).
- **Tiện ích hỗ trợ sự kiện:** Liên kết từ bảng `LienKet_LeHoi_TienIch` (Ví dụ: Có hỗ trợ y tế, sơ đồ chỉ dẫn, quầy thông tin hỗ trợ du khách du lịch).
- **Hình ảnh/Banner truyền thông:** Các tệp tin hình ảnh banner, poster, sơ đồ phân luồng giao thông lấy từ `DuLich_TepTin`.

---

### **3.9 QUẢN LÝ PHẢN HỒI**

#### **3.9.1 Quản lý phản hồi quản trị viên (Admin Mode)**
- **Mô tả chức năng:** QTV thực hiện tiếp nhận toàn bộ các đánh giá, phản hồi, khiếu nại của du khách gửi từ ứng dụng di động công cộng (CSDL nguồn từ bảng `DuLich_PhanHoi`).
- **Giao diện bảng điều khiển:** - Hiển thị danh sách các phản hồi gồm: *Tên du khách (`NguoiDungID` tra cứu họ tên), Nội dung phản hồi (`NoiDung`), Số sao đánh giá (`SoSao` từ 1-5), Trạng thái duyệt xử lý (`TrangThaiDuyet`), Ngày gửi (`NgayGui`)*.
  - Bộ lọc theo số lượng sao (Lọc nhanh các phản hồi tiêu cực 1 sao, 2 sao để ưu tiên giải quyết) và lọc theo trạng thái phê duyệt nội dung.
- **Hành động xử lý của QTV:**
  - **Phê duyệt hiển thị (`TrangThaiDuyet = 1`):** Cho phép đánh giá này hiển thị công khai trên ứng dụng ở mục bình luận của điểm đến/dịch vụ để các du khách khác tham khảo.
  - **Ẩn / Từ chối hiển thị (`TrangThaiDuyet = 2`):** Áp dụng đối với các phản hồi chứa từ ngữ thô tục, spam, sai sự thật thô bạo. Nội dung phản hồi bị ẩn khỏi giao diện công cộng nhưng giữ nguyên trong CSDL quản trị để làm bằng chứng đối soát.

#### **3.9.2 Quản lý phản hồi doanh nghiệp (Business Mode)**
- **Mô tả chức năng:** Phân hệ dành riêng cho tài khoản doanh nghiệp chủ quản (`DoanhNghiepID`) đăng nhập để theo dõi các phản hồi, đánh giá trực tiếp liên quan đến các cơ sở dịch vụ thuộc quyền quản lý của mình (Cơ sở lưu trú, Nhà hàng ăn uống, Gói tour du lịch).
- **Quyền hạn giao diện:** Doanh nghiệp chỉ được xem các phản hồi đã được QTV hệ thống phê duyệt (`TrangThaiDuyet = 1`). Không có quyền xóa dữ liệu phản hồi của khách hàng.
- **Chức năng Phản hồi / Phản biện:** Cung cấp ô nhập liệu văn bản cho phép Doanh nghiệp nhập nội dung giải trình, phản hồi lại ý kiến đóng góp của du khách (Hệ thống ghi nhận vào trường nội dung trao đổi mở rộng hoặc bảng liên kết phản hồi phản biện). Giúp tăng tính tương tác minh bạch giữa đơn vị cung ứng dịch vụ và du khách du lịch.

---

### **3.10 TÌM KIẾM THÔNG TIN DU LỊCH**

- **Mô tả use case:** Đây là module dịch vụ lõi tích hợp tìm kiếm thông minh đa tiêu chí phục vụ cho cả trang cổng thông tin quản trị và các cổng API dịch vụ công cộng.
- **Cơ chế tìm kiếm Full-Text Search:** Cho phép tìm kiếm đồng thời trên nhiều bảng CSDL cốt lõi (`DuLich_DiemDen`, `DuLich_CoSoLuuTru`, `DuLich_AnUongMuaSam`, `DuLich_Tour`) thông qua từ khóa chuỗi nhập vào không dấu hoặc có dấu.
- **Thành phần thanh tìm kiếm tổng hợp (Global Search UI):**
  - **Input Text:** Nhập từ khóa bất kỳ (Ví dụ: *"Khách sạn Hương Giang"*, *"Lăng"*, *"Bún bò"*, *"Tour sông Hương"*).
  - **Phân loại nhanh (Quick Tabs Filters):** Tất cả kết quả, Điểm đến, Lưu trú, Ẩm thực & Mua sắm, Lữ hành & Tour.
  - **Lọc thông minh vị trí (Geo-Distance Filter):** Cho phép kết nối tọa độ hiện tại của thiết bị du khách với cột `ToaDo` trong CSDL để tính toán khoảng cách bán kính (1km, 5km, 10km) và sắp xếp hiển thị ưu tiên các kết quả ở gần du khách nhất.
- **Kết quả trả về:** Trình bày dạng danh sách thẻ (Cards list) có hình ảnh đại diện, tiêu đề, khoảng cách vị trí và đánh giá trung bình sao giúp người dùng dễ dàng đưa ra quyết định lựa chọn.

---

### **3.11 QUẢN LÝ API**

| **Tên Use case** | **Quản lý cấu hình kết nối API hệ thống** |
| :--- | :--- |
| **Tác nhân** | Quản trị viên hệ thống (Technical Admin) |
| **Mô tả** | Thiết lập thông tin kết nối, quản lý khóa bảo mật API Key, Client ID của các dịch vụ liên kết bên thứ ba, phục vụ việc tích hợp dữ liệu đồng bộ. |

- **Thiết kế màn hình dựa trên cấu trúc CSDL bảng `HeThong_CauHinhAPI`:**
  - **Danh sách cấu hình API:** Bảng quản trị hiển thị danh sách các kết nối hiện hành bao gồm các dịch vụ liên kết chủ chốt: `VNeID_OAuth2` (Xác thực tài khoản công dân định danh), `MapAPI` (Bản đồ số định vị tìm đường), `WeatherAPI` (Dữ liệu thời tiết khí hậu thời gian thực tại Huế phục vụ cảnh báo du khách).
  - **Form cấu hình chi tiết / Chỉnh sửa khóa bảo mật:**
    1. *Mã cấu hình:* `ApiConfigID` (Tự động cấp - UUID).
    2. *Tên dịch vụ kết nối:* `TenDichVu` (Textbox - String, Ví dụ: `'VNeID_OAuth2'`, `'GoogleMap_Service'`).
    3. *Đường dẫn API gốc:* `BaseURL` (Textbox - URL, đường dẫn endpoint chính xác phục vụ việc gửi request backend).
    4. *Khóa bảo mật ứng dụng:* `ApiKey` (Password Textfield kèm icon Ẩn/Hiện - Chuỗi mã hóa token/khóa bí mật bảo mật cao dùng để xác thực quyền kết nối hệ thống).
    5. *Mã định danh ứng dụng bên thứ 3:* `ClientID` (Textbox - String, mã định danh ứng dụng đi kèm cặp khóa bí mật).
    6. *Trạng thái hoạt động kết nối:* `TrangThai` (Toggle Switch: 0 - Hết hạn / Tạm dừng kết nối API; 1 - Đang hoạt động ổn định).
  - **Chức năng Kiểm tra kết nối (Ping API Test Button):** Nút bấm cho phép gửi một request mẫu kiểm tra (Healtcheck) ngay lập tức tới `BaseURL` bằng thông số `ApiKey` đã cấu hình để kiểm tra trạng thái hoạt động trực tuyến của cổng kết nối dịch vụ bên thứ ba.

---

### **3.12 BÁO CÁO THỐNG KÊ**

- **Mô tả chức năng:** Hệ thống tổng hợp, tính toán xử lý dữ liệu từ toàn bộ các phân hệ nghiệp vụ để xuất bản các báo cáo số liệu, biểu đồ trực quan giúp lãnh đạo Sở Du lịch và cơ quan quản lý đưa ra dự báo, đánh giá tình hình phát triển ngành du lịch tỉnh Huế.
- **Các mẫu báo cáo thống kê cốt lõi:**
  1. **Thống kê cơ sở lưu trú du lịch:** Tổng số lượng cơ sở phân theo địa bàn hành chính (Quận/Huyện), tổng số lượng phòng cung ứng, tỷ lệ phân bố theo phân hạng sao (Từ 1 đến 5 sao) lấy dữ liệu tổng hợp từ bảng `DuLich_CoSoLuuTru`.
  2. **Thống kê doanh nghiệp & lữ hành:** Số lượng doanh nghiệp mới đăng ký theo tháng, số lượng tour du lịch đã được phê duyệt mở bán của từng đơn vị lữ hành dựa trên bảng `DuLich_Tour`.
  3. **Thống kê mức độ hài lòng du khách:** Tính toán điểm trung bình số sao đánh giá (`SoSao`) từ bảng `DuLich_PhanHoi` để xếp hạng các điểm đến, cơ sở ẩm thực, lưu trú được yêu thích nhất và các đơn vị nhận nhiều phản hồi tiêu cực nhất.
- **Thành phần thành tố giao diện báo cáo (Dashboard & Report UI):**
  - **Thanh chọn khoảng thời gian thống kê:** Từ ngày ... Đến ngày ... (Datepicker) hoặc chọn nhanh theo Quý, năm hành chính.
  - **Biểu đồ trực quan (Charts components):** Biểu đồ cột (so sánh số lượng phòng lưu trú giữa các quận huyện), Biểu đồ tròn (tỷ lệ phần trăm loại hình điểm đến di tích vs thắng cảnh), Biểu đồ đường xu hướng (thể hiện biến động lượng phản hồi du khách theo thời gian).
  - **Chức năng xuất dữ liệu báo cáo:** Nút bấm **"Xuất báo cáo Excel / PDF"** thực hiện kết xuất toàn bộ bảng số liệu tổng hợp định dạng tệp tin văn phòng có đóng dấu tiêu đề và ngày lập báo cáo tự động của hệ thống.
