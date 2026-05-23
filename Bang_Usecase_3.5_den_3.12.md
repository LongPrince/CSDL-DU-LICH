### 3.5 Quản lý lữ hành và HDV
#### 3.5.1 Đơn vị lữ hành

| | |
| :--- | :--- |
| **Tên Use case** | **Quản lý đơn vị lữ hành** |
| **Mô tả** | Quản trị viên/Chuyên viên xem danh sách, thêm mới, sửa, xóa hoặc phê duyệt các đơn vị lữ hành hoạt động trên địa bàn. |
| **Tác nhân** | Quản trị viên, Chuyên viên quản lý nghiệp vụ |
| **Độ phức tạp** | 🔲 Đơn giản <br> ☑️ Trung bình <br> 🔲 Phức tạp |
| **Điều kiện bắt đầu** | Người dùng có tài khoản hợp lệ và được cấp quyền quản lý lữ hành. |
| **Điều kiện kết thúc** | Thông tin đơn vị lữ hành được cập nhật/lưu trữ thành công vào CSDL. |
| **Kịch bản chính** | 1. Người dùng truy cập chức năng "Đơn vị lữ hành".<br>2. Xem danh sách các đơn vị lữ hành hiện có.<br>3. Chọn Thêm/Sửa/Xóa đơn vị lữ hành.<br>4. Nhập thông tin và lưu lại. |
| **Kịch bản phụ** | - Lỗi thiếu thông tin bắt buộc: Hệ thống cảnh báo đỏ và yêu cầu nhập lại.<br>- Lỗi trùng lặp mã đơn vị/tên đơn vị: Hệ thống cảnh báo. |
| **Các yêu cầu, ràng buộc** | Hệ thống đảm bảo kết nối internet, dữ liệu được xác thực trước khi lưu. |

#### 3.5.2 Hướng dẫn viên

| | |
| :--- | :--- |
| **Tên Use case** | **Quản lý Hướng dẫn viên** |
| **Mô tả** | Chức năng cho phép quản lý danh sách thông tin, thẻ hướng dẫn viên (HDV), ngôn ngữ và chuyên môn của các HDV du lịch. |
| **Tác nhân** | Quản trị viên, Chuyên viên quản lý nghiệp vụ, Đơn vị lữ hành |
| **Độ phức tạp** | 🔲 Đơn giản <br> ☑️ Trung bình <br> 🔲 Phức tạp |
| **Điều kiện bắt đầu** | Người dùng đăng nhập hệ thống với phân quyền tương ứng. |
| **Điều kiện kết thúc** | Thông tin hồ sơ HDV được cập nhật chính xác trên hệ thống. |
| **Kịch bản chính** | 1. Truy cập danh sách Hướng dẫn viên.<br>2. Tìm kiếm, lọc HDV theo ngôn ngữ, trạng thái thẻ.<br>3. Thêm mới hoặc cập nhật hồ sơ, hạng thẻ HDV.<br>4. Lưu thông tin hồ sơ. |
| **Kịch bản phụ** | Thẻ HDV hết hạn: Hệ thống tự động đánh dấu trạng thái "Hết hạn" và cảnh báo khi sắp xếp tour. |
| **Các yêu cầu, ràng buộc** | Hệ thống đảm bảo kết nối internet. File đính kèm (ảnh thẻ, chứng chỉ) đúng định dạng và dung lượng quy định. |

#### 3.5.3 Tour du lịch

| | |
| :--- | :--- |
| **Tên Use case** | **Quản lý Tour du lịch** |
| **Mô tả** | Đơn vị lữ hành đăng ký, cập nhật tour; Quản trị viên kiểm duyệt danh sách các tour du lịch được phép khai thác. |
| **Tác nhân** | Quản trị viên, Đơn vị lữ hành |
| **Độ phức tạp** | 🔲 Đơn giản <br> 🔲 Trung bình <br> ☑️ Phức tạp |
| **Điều kiện bắt đầu** | Đơn vị lữ hành đã được cấp tài khoản doanh nghiệp hoạt động trên hệ thống. |
| **Điều kiện kết thúc** | Tour du lịch được tạo, phê duyệt và hiển thị trên ứng dụng/cổng thông tin. |
| **Kịch bản chính** | 1. Doanh nghiệp tạo mới Tour (nhập lịch trình, giá, ngày khởi hành).<br>2. Gửi yêu cầu phê duyệt.<br>3. Quản trị viên xem xét và nhấn Duyệt/Từ chối.<br>4. Tour được chuyển trạng thái "Đang hoạt động". |
| **Kịch bản phụ** | - Nếu Quản trị viên từ chối: Nhập lý do từ chối và trả lại trạng thái "Bản nháp" cho doanh nghiệp chỉnh sửa. |
| **Các yêu cầu, ràng buộc** | Hệ thống đảm bảo kết nối internet. Thời gian khởi hành tour phải lớn hơn thời gian hiện tại. |

### 3.6 Quản lý ăn uống & mua sắm

| | |
| :--- | :--- |
| **Tên Use case** | **Quản lý cơ sở ăn uống & mua sắm** |
| **Mô tả** | Quản lý danh sách, thông tin chi tiết, hình ảnh của các nhà hàng, quán ăn, cửa hàng đặc sản, siêu thị. |
| **Tác nhân** | Quản trị viên, Chuyên viên, Doanh nghiệp |
| **Độ phức tạp** | 🔲 Đơn giản <br> ☑️ Trung bình <br> 🔲 Phức tạp |
| **Điều kiện bắt đầu** | Người dùng có tài khoản hợp lệ để truy cập hệ thống. |
| **Điều kiện kết thúc** | Thông tin cơ sở ăn uống/mua sắm được cập nhật, hiển thị chính xác. |
| **Kịch bản chính** | 1. Truy cập chức năng "Ăn uống & mua sắm".<br>2. Thêm mới cơ sở (nhập tên, địa chỉ, loại hình, thực đơn/mặt hàng).<br>3. Kiểm tra thông tin và Lưu lại. |
| **Kịch bản phụ** | Hình ảnh tải lên vượt quá dung lượng: Báo lỗi và yêu cầu tải ảnh khác. |
| **Các yêu cầu, ràng buộc** | Hệ thống đảm bảo kết nối internet. Tọa độ (Lat/Long) phải hợp lệ để hiển thị trên bản đồ. |

### 3.7 Quản lý điểm đến

| | |
| :--- | :--- |
| **Tên Use case** | **Quản lý điểm đến** |
| **Mô tả** | Quản trị viên quản lý danh mục các điểm tham quan, di tích, danh lam thắng cảnh. |
| **Tác nhân** | Quản trị viên hệ thống |
| **Độ phức tạp** | 🔲 Đơn giản <br> ☑️ Trung bình <br> 🔲 Phức tạp |
| **Điều kiện bắt đầu** | Tài khoản Quản trị viên đăng nhập thành công. |
| **Điều kiện kết thúc** | Điểm đến mới được tạo hoặc cập nhật thành công. |
| **Kịch bản chính** | 1. Chọn module "Điểm đến".<br>2. Thêm thông tin (Tên điểm đến, phân loại, mô tả, giá vé, hình ảnh 360/Video).<br>3. Lưu thông tin vào CSDL. |
| **Kịch bản phụ** | Hủy bỏ thao tác: Hệ thống xác nhận và quay về trang danh sách không lưu dữ liệu. |
| **Các yêu cầu, ràng buộc** | Hệ thống đảm bảo kết nối internet. Có hỗ trợ tích hợp bản đồ số (GIS). |

### 3.8 Quản lý lễ hội và sự kiện

| | |
| :--- | :--- |
| **Tên Use case** | **Quản lý lễ hội và sự kiện** |
| **Mô tả** | Quản lý lịch trình, thời gian, địa điểm tổ chức các sự kiện văn hóa, lễ hội du lịch sắp và đang diễn ra. |
| **Tác nhân** | Quản trị viên, Chuyên viên sở DL |
| **Độ phức tạp** | ☑️ Đơn giản <br> 🔲 Trung bình <br> 🔲 Phức tạp |
| **Điều kiện bắt đầu** | Người dùng có quyền thêm/sửa/xóa bài viết sự kiện. |
| **Điều kiện kết thúc** | Thông tin sự kiện được công bố/cập nhật thành công. |
| **Kịch bản chính** | 1. Chọn "Lễ hội & Sự kiện".<br>2. Nhập thông tin sự kiện (Tên, thời gian bắt đầu/kết thúc, địa điểm, nội dung).<br>3. Đặt trạng thái "Sắp diễn ra" hoặc "Đang diễn ra" và Lưu. |
| **Kịch bản phụ** | Ngày kết thúc nhỏ hơn ngày bắt đầu: Hệ thống báo lỗi bắt buộc nhập lại ngày hợp lệ. |
| **Các yêu cầu, ràng buộc** | Hệ thống đảm bảo kết nối internet. Sự kiện phải thuộc một địa bàn quản lý xác định. |

### 3.9 Quản lý phản hồi

| | |
| :--- | :--- |
| **Tên Use case** | **Quản lý phản hồi / Đánh giá** |
| **Mô tả** | Quản trị viên và Doanh nghiệp tiếp nhận, quản lý và phản hồi lại các đánh giá, khiếu nại từ du khách (3.9.1 cho QTV, 3.9.2 cho Doanh nghiệp). |
| **Tác nhân** | Quản trị viên, Doanh nghiệp |
| **Độ phức tạp** | 🔲 Đơn giản <br> ☑️ Trung bình <br> 🔲 Phức tạp |
| **Điều kiện bắt đầu** | Có dữ liệu đánh giá/phản hồi từ người dùng (du khách) gửi về hệ thống. |
| **Điều kiện kết thúc** | Trạng thái phản hồi được cập nhật thành "Đã xử lý" / "Đã phản hồi". |
| **Kịch bản chính** | 1. Xem danh sách đánh giá/phản hồi mới.<br>2. Lọc theo số sao hoặc trạng thái (chưa xử lý).<br>3. Chọn một phản hồi để đọc chi tiết.<br>4. Viết nội dung trả lời và nhấn Gửi. |
| **Kịch bản phụ** | Phát hiện bình luận spam/từ ngữ phản cảm: Quản trị viên sử dụng chức năng Ẩn/Xóa đánh giá. |
| **Các yêu cầu, ràng buộc** | Hệ thống đảm bảo kết nối internet. Quản trị viên có quyền xem toàn bộ phản hồi, Doanh nghiệp chỉ xem phản hồi thuộc cơ sở của mình. |

### 3.10 Tìm kiếm thông tin du lịch

| | |
| :--- | :--- |
| **Tên Use case** | **Tìm kiếm thông tin du lịch** |
| **Mô tả** | Du khách hoặc người dùng tìm kiếm nhanh các điểm đến, cơ sở lưu trú, nhà hàng, dịch vụ theo từ khóa hoặc bộ lọc. |
| **Tác nhân** | Du khách, Thành viên hệ thống |
| **Độ phức tạp** | ☑️ Đơn giản <br> 🔲 Trung bình <br> 🔲 Phức tạp |
| **Điều kiện bắt đầu** | Hệ thống đang hoạt động ổn định. (Không bắt buộc đăng nhập) |
| **Điều kiện kết thúc** | Hiển thị danh sách kết quả phù hợp với từ khóa tìm kiếm. |
| **Kịch bản chính** | 1. Người dùng nhập từ khóa vào thanh tìm kiếm.<br>2. Áp dụng bộ lọc (giá cả, đánh giá, loại hình).<br>3. Hệ thống trả về danh sách kết quả tương ứng. |
| **Kịch bản phụ** | Không tìm thấy kết quả: Hiển thị thông báo "Không tìm thấy dữ liệu phù hợp" và gợi ý các từ khóa khác. |
| **Các yêu cầu, ràng buộc** | Hệ thống đảm bảo kết nối internet. Tốc độ tìm kiếm nhanh (sử dụng cache/index). |

### 3.11 Quản lý API

| | |
| :--- | :--- |
| **Tên Use case** | **Quản lý API kết nối dữ liệu** |
| **Mô tả** | Quản trị hệ thống quản lý các khóa kết nối (API Keys), cung cấp dữ liệu cho ứng dụng di động hoặc các nền tảng bên thứ ba (Ví dụ: Hue-S). |
| **Tác nhân** | Quản trị hệ thống (Super Admin) |
| **Độ phức tạp** | 🔲 Đơn giản <br> 🔲 Trung bình <br> ☑️ Phức tạp |
| **Điều kiện bắt đầu** | Đăng nhập với quyền quản trị hệ thống cao nhất. |
| **Điều kiện kết thúc** | API Key được tạo mới, thu hồi hoặc cấp quyền thành công. |
| **Kịch bản chính** | 1. Truy cập "Quản lý API".<br>2. Xem danh sách các API Key đang hoạt động.<br>3. Chọn tạo mới API Key cho đối tác.<br>4. Lưu và gửi thông tin kết nối cho đối tác. |
| **Kịch bản phụ** | API bị lạm dụng/Gửi request quá mức (Rate limit): Hệ thống tự động khóa tạm thời và gửi cảnh báo. |
| **Các yêu cầu, ràng buộc** | Hệ thống đảm bảo kết nối internet. Tuân thủ nghiêm ngặt chuẩn bảo mật dữ liệu và chuẩn RESTful/GraphQL. |

### 3.12 Báo cáo thống kê

| | |
| :--- | :--- |
| **Tên Use case** | **Báo cáo thống kê (Dashboard)** |
| **Mô tả** | Cung cấp giao diện biểu đồ tổng quan, xuất các báo cáo thống kê về lượng khách, cơ sở lưu trú, doanh thu định kỳ. |
| **Tác nhân** | Lãnh đạo, Quản trị viên, Chuyên viên |
| **Độ phức tạp** | 🔲 Đơn giản <br> 🔲 Trung bình <br> ☑️ Phức tạp |
| **Điều kiện bắt đầu** | Người dùng đăng nhập có quyền xem thống kê. |
| **Điều kiện kết thúc** | Báo cáo được hiển thị hoặc xuất ra file (Excel/PDF) thành công. |
| **Kịch bản chính** | 1. Chọn module "Báo cáo thống kê".<br>2. Chọn loại báo cáo và thời gian (Từ ngày - Đến ngày).<br>3. Hệ thống tổng hợp dữ liệu và vẽ biểu đồ.<br>4. Nhấn "Xuất báo cáo" tải file về máy. |
| **Kịch bản phụ** | Khoảng thời gian quá dài gây quá tải: Hệ thống nhắc nhở giới hạn thời gian truy vấn ngắn lại. |
| **Các yêu cầu, ràng buộc** | Hệ thống đảm bảo kết nối internet. Dữ liệu tính toán đảm bảo độ chính xác theo thời gian thực (hoặc near real-time). |
