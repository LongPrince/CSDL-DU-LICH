# THIẾT KẾ CHI TIẾT CÁC CHỨC NĂNG (BỔ SUNG VÀ CẬP NHẬT)

## 3.9 QUẢN LÝ PHẢN HỒI

### 3.9.1 Quản lý phản hồi quản trị viên

| Tiêu chí | Nội dung chi tiết |
| :--- | :--- |
| **Tên Use case** | **Quản lý phản hồi quản trị viên** |
| **Mô tả** | Quản trị viên hệ thống hoặc chuyên viên thực hiện xem danh sách, tìm kiếm, phân loại và theo dõi trạng thái xử lý các phản hồi, góp ý, báo lỗi hoặc khiếu nại từ du khách và doanh nghiệp gửi lên hệ thống. |
| **Tác nhân** | Quản trị viên hệ thống (Admin), Chuyên viên quản lý nghiệp vụ |
| **Độ phức tạp** | 🔲 Đơn giản  ☑️ Trung bình  🔲 Phức tạp |
| **Điều kiện bắt đầu** | Quản trị viên đăng nhập thành công và truy cập vào phân hệ Quản lý phản hồi của Admin. |
| **Điều kiện kết thúc** | Xem và lọc được danh sách các phản hồi cần xử lý trên toàn hệ thống. |
| **Kịch bản chính** | 1. Chọn menu "Quản lý phản hồi" -> Hệ thống hiển thị danh sách tất cả phản hồi của người dùng.<br>2. Admin sử dụng bộ lọc (Trạng thái, Phân loại) hoặc ô Tìm kiếm để tra cứu phản hồi cụ thể.<br>3. Hệ thống hiển thị danh sách kết quả tương ứng kèm thông tin chi tiết của phản hồi. |
| **Kịch bản phụ** | - *Không có dữ liệu:* Bộ lọc không khớp với phản hồi nào -> Hệ thống hiển thị thông báo "Không có dữ liệu phù hợp". |
| **Các yêu cầu, ràng buộc** | Các phản hồi mới gửi cần được đánh dấu nổi bật (chữ đậm hoặc icon chưa đọc) và xếp lên đầu danh sách. |

#### a. Giao diện danh sách Phản hồi Quản trị viên

| **Màn hình** | **Danh sách phản hồi quản trị viên** |
| :--- | :--- |
| **Mô tả** | Màn hình trung tâm giúp Admin theo dõi toàn bộ ý kiến đóng góp, khiếu nại của du khách và doanh nghiệp gửi về cổng thông tin du lịch. |
| **Màn hình kết nối** | Biểu mẫu Phản hồi Du khách (Khung Pop-up trả lời) |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Tìm kiếm | Textfield – String | Nhập tên người gửi, tiêu đề hoặc nội dung để tìm kiếm nhanh. |
| Loại phản hồi | Combobox – String | Lọc theo loại: Tất cả, Góp ý, Khiếu nại, Báo lỗi hệ thống. |
| Trạng thái xử lý | Combobox – String | Lọc theo: Chưa xử lý, Đang xử lý, Đã xử lý / Đã trả lời. |
| Thời gian gửi | Date Range Picker | Chọn khoảng thời gian nhận phản hồi (Từ ngày - Đến ngày). |
| Bảng danh sách phản hồi | Table | Khung hiển thị danh sách phản hồi tổng hợp. |
| *STT* | Label – Number | Số thứ tự dòng. |
| *Người gửi* | Label – String | Họ tên du khách hoặc Tên doanh nghiệp gửi phản hồi. |
| *Phân loại* | Badge | Loại phản hồi (Màu đỏ: Khiếu nại, Màu xanh: Góp ý, Màu vàng: Báo lỗi). |
| *Tiêu đề / Nội dung* | Text – String | Tiêu đề tóm tắt và một đoạn ngắn nội dung phản hồi. |
| *Ngày gửi* | Label – Date | Thời gian người dùng gửi phản hồi lên hệ thống. |
| *Trạng thái* | Badge | Trạng thái xử lý (Chưa xử lý / Đã xử lý). |
| *Thao tác* | Icon Buttons | Biểu tượng Xem & Phản hồi (Hình hộp thư/Xem), Ẩn/Xóa (Thùng rác). |
| Phân trang | Pagination | Các nút chuyển trang (1, 2, 3...). |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Tìm kiếm & Bộ lọc** | Tra cứu danh sách phản hồi theo tiêu chí chọn. | Bảng dữ liệu cập nhật chính xác các phản hồi thỏa mãn bộ lọc. | Không có dữ liệu phù hợp -> Hiển thị bảng trống. |

---

### 3.9.2 Quản lý phản hồi doanh nghiệp

| Tiêu chí | Nội dung chi tiết |
| :--- | :--- |
| **Tên Use case** | **Quản lý phản hồi doanh nghiệp** |
| **Mô tả** | Đại diện doanh nghiệp (Nhà hàng, khách sạn, lữ hành) thực hiện xem danh sách, theo dõi các đánh giá, bình luận và phản hồi từ khách du lịch trực tiếp đối với cơ sở dịch vụ của mình. |
| **Tác nhân** | Chủ cơ sở / Quản lý Doanh nghiệp dịch vụ |
| **Độ phức tạp** | 🔲 Đơn giản  ☑️ Trung bình  🔲 Phức tạp |
| **Điều kiện bắt đầu** | Tài khoản doanh nghiệp đăng nhập thành công và truy cập module Phản hồi & Đánh giá của cơ sở. |
| **Điều kiện kết thúc** | Xem được danh sách các đánh giá, phản hồi của khách hàng đối với dịch vụ của doanh nghiệp mình. |
| **Kịch bản chính** | 1. Doanh nghiệp chọn menu "Đánh giá & Phản hồi".<br>2. Hệ thống hiển thị danh sách các lượt đánh giá (số sao) và bình luận từ du khách dành cho cơ sở.<br>3. Doanh nghiệp sử dụng bộ lọc theo mức độ đánh giá (số sao) hoặc trạng thái để kiểm tra danh sách. |
| **Kịch bản phụ** | - *Lỗi kết nối:* Không tải được danh sách đánh giá -> Hệ thống hiển thị thông báo thử lại sau. |
| **Các yêu cầu, ràng buộc** | Doanh nghiệp chỉ có quyền xem và phản hồi các đánh giá thuộc về cơ sở của mình, không được xem dữ liệu của doanh nghiệp khác. |

#### a. Giao diện danh sách Phản hồi Doanh nghiệp

| **Màn hình** | **Danh sách phản hồi & Đánh giá của doanh nghiệp** |
| :--- | :--- |
| **Mô tả** | Giao diện dành riêng cho tài khoản doanh nghiệp để theo dõi mức độ hài lòng (số sao) và ý kiến của khách hàng về dịch vụ của mình. |
| **Màn hình kết nối** | Biểu mẫu Phản hồi Du khách (Khung Pop-up trả lời) |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Ô tìm kiếm | Textfield – String | Nhập tên khách hàng hoặc từ khóa trong bình luận để tìm kiếm. |
| Bộ lọc số sao (Đánh giá) | Combobox – String | Lọc theo số sao: Tất cả, 5 Sao, 4 Sao, 3 Sao, 2 Sao, 1 Sao. |
| Trạng thái trả lời | Combobox – String | Lọc theo: Chưa phản hồi, Đã phản hồi khách hàng. |
| Bảng danh sách đánh giá | Table | Khung hiển thị danh sách ý kiến/đánh giá của khách. |
| *STT* | Label – Number | Số thứ tự dòng. |
| *Khách hàng* | Label – String | Tên tài khoản du khách đã thực hiện đánh giá. |
| *Mức độ đánh giá* | Rating Stars | Hiển thị số sao định lượng (Biểu tượng ngôi sao vàng từ 1 đến 5). |
| *Nội dung bình luận* | Text – String | Chi tiết ý kiến đóng góp, nhận xét của du khách về dịch vụ. |
| *Thời gian* | Label – Date/Time | Ngày giờ du khách đăng tải đánh giá. |
| *Trạng thái phản hồi* | Badge | Nhãn hiển thị: Màu xám (Chưa phản hồi), Màu xanh (Đã phản hồi). |
| *Thao tác* | Icon Buttons | Biểu tượng Xem chi tiết / Trả lời bình luận của khách. |
| Phân trang | Pagination | Các nút điều hướng chuyển đổi trang danh sách. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Lọc theo số sao/Trạng thái**| Phân loại nhanh các đánh giá tốt/xấu hoặc các đánh giá chưa được xử lý. | Hệ thống lọc và hiển thị chính xác các dòng dữ liệu tương ứng. | Hiển thị danh sách trống nếu không có bản ghi phù hợp. |

---

### 3.9.3 Phản hồi du khách

| Tiêu chí | Nội dung chi tiết |
| :--- | :--- |
| **Tên Use case** | **Phản hồi du khách (Du khách gửi phản hồi)** |
| **Mô tả** | Du khách sau khi đăng nhập vào ứng dụng di động hoặc cổng thông tin du lịch thực hiện gửi các đánh giá (số sao), bình luận, đóng góp ý kiến hoặc phản ánh khiếu nại về chất lượng của một cơ sở dịch vụ du lịch (lưu trú, ăn uống, điểm đến...) trên địa bàn thành phố. |
| **Tác nhân** | Du khách |
| **Độ phức tạp** | ☑️ Đơn giản  🔲 Trung bình  🔲 Phức tạp |
| **Điều kiện bắt đầu** | Du khách đã đăng nhập tài khoản thành công trên ứng dụng di động/cổng thông tin du lịch và truy cập vào chức năng "Đánh giá & Phản hồi" tại trang chi tiết của một địa điểm/dịch vụ cụ thể. |
| **Điều kiện kết thúc** | Ý kiến phản hồi và số sao đánh giá của du khách được lưu trữ thành công vào cơ sở dữ liệu hệ thống để chuyển tới Admin và doanh nghiệp xử lý. |
| **Kịch bản chính** | 1. Tại trang chi tiết của dịch vụ/điểm đến, du khách nhấn nút "Viết đánh giá" (hoặc biểu tượng Phản hồi).<br>2. Hệ thống hiển thị biểu mẫu Gửi phản hồi bao gồm các thông tin về địa điểm đang chọn.<br>3. **Nhập thông tin:** Du khách thực hiện chọn mức độ hài lòng bằng cách chạm chọn số sao (định lượng từ 1 -> 5 sao); nhập tiêu đề phản hồi; nhập nội dung chi tiết ý kiến và nhấn chọn tải lên các hình ảnh thực tế chứng minh (nếu có).<br>4. Du khách nhấn nút "Gửi phản hồi".<br>5. Hệ thống thực hiện kiểm tra tính hợp lệ của dữ liệu, lưu thông tin vào cơ sở dữ liệu và thông báo cho du khách: *"Gửi phản hồi thành công. Ý kiến của bạn đã được ghi nhận!"*. |
| **Kịch bản phụ** | - **Lỗi bỏ trống thông tin bắt buộc:** Du khách không chọn số sao hoặc để trống nội dung bình luận nhưng bấm "Gửi" -> Hệ thống sẽ hiển thị cảnh báo lỗi màu đỏ tại trường đó và yêu cầu hoàn thiện dữ liệu.<br>- **Lỗi nội dung chứa từ ngữ thô tục/nhạy cảm:** Hệ thống tự động kiểm tra chuỗi văn bản bằng bộ lọc từ khóa cấm, nếu phát hiện nội dung vi phạm tiêu chuẩn cộng đồng -> Hệ thống chặn thao tác gửi và hiển thị thông báo: *"Nội dung phản hồi chứa từ ngữ không phù hợp, vui lòng điều chỉnh lại"*. |
| **Các yêu cầu, ràng buộc** | - Thiết bị di động hoặc máy tính của du khách bắt buộc phải có kết nối mạng internet.<br>- Mỗi tài khoản du khách chỉ được phép gửi đánh giá 1 lần duy nhất cho một dịch vụ/địa điểm trong một khoảng thời gian nhất định (tránh tình trạng spam hoặc seeding đánh giá ảo). |

#### a. Giao diện Biểu mẫu gửi Phản hồi của Du khách

| **Màn hình** | **Biểu mẫu gửi phản hồi của du khách** |
| :--- | :--- |
| **Mô tả** | Giao diện trên thiết bị di động (hoặc cổng thông tin) cho phép khách du lịch thực hiện chấm điểm số sao, viết bình luận nhận xét và đính kèm hình ảnh thực tế về dịch vụ du lịch. |
| **Màn hình kết nối** | Trang chi tiết điểm đến/dịch vụ du lịch |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Đối tượng phản hồi | Label – String | Hiển thị cố định tên địa điểm/dịch vụ du lịch mà khách đang thực hiện phản hồi (VD: "Khách sạn Century Riverside", "Lăng Tự Đức"...). |
| Đánh giá số sao | Rating Stars | Bộ chọn mức độ hài lòng từ 1 -> 5 ngôi sao (Mặc định chưa chọn ngôi sao nào, du khách chạm để kích hoạt số sao mong muốn). |
| Tiêu đề phản hồi | Textfield – String | Ô nhập tóm tắt ngắn gọn lý do hoặc chủ đề phản hồi (tối đa 100 ký tự). |
| Nội dung chi tiết | Text Area – String | Khung nhập văn bản cho phép du khách viết chi tiết ý kiến đóng góp, trải nghiệm tốt/xấu hoặc nội dung khiếu nại (tối đa 1000 ký tự). |
| Đính kèm hình ảnh | Upload Button / Icon | Nút bấm (hình chiếc ghim hoặc máy ảnh) cho phép truy cập vào thư viện ảnh hoặc camera của thiết bị để tải tối đa 3-5 hình ảnh thực tế. |
| Danh sách ảnh đã chọn | Image Grid | Hiển thị các ảnh thu nhỏ (thumbnail) du khách vừa tải lên, có kèm nút icon gạch chéo "X" ở góc ảnh để xóa bớt ảnh nếu chọn nhầm. |
| Nút Hủy bỏ | Button | Quay lại trang chi tiết trước đó, xóa bỏ toàn bộ nội dung vừa nhập trên form. |
| Nút Gửi phản hồi | Button | Nút bấm gửi dữ liệu lên hệ thống để hoàn tất use case. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Tải ảnh đính kèm** | Khách chọn ảnh từ bộ nhớ thiết bị để minh họa cho phản hồi. | Ảnh hiển thị thành công dưới dạng thumbnail trên lưới danh sách ảnh. | Định dạng tệp không phải là ảnh (.jpg, .png) hoặc kích thước file quá lớn (>5MB) -> Hệ thống thông báo từ chối. |
| **Gửi phản hồi** | Hệ thống xử lý dữ liệu biểu mẫu và đóng gói gửi về máy chủ. | Ghi nhận dữ liệu thành công, hiển thị popup thông báo cảm ơn, tự động cập nhật số điểm đánh giá trung bình của địa điểm và đóng màn hình form. | Mất kết nối internet đột ngột, nội dung chứa từ ngữ thô tục vi phạm bộ lọc của hệ thống -> Báo lỗi cụ thể cho du khách và giữ nguyên nội dung trên form để sửa lại. |

---

## PHÂN HỆ QUẢN LÝ TÀI KHOẢN DU KHÁCH

### a. Giao diện Thông tin tài khoản du khách

| **Màn hình** | **Thông tin tài khoản** |
| :--- | :--- |
| **Mô tả** | Giao diện trên ứng dụng di động hiển thị thông tin hồ sơ cá nhân tổng quan của du khách sau khi đăng nhập thành công. |
| **Màn hình kết nối** | Chỉnh sửa thông tin tài khoản |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Tiêu đề màn hình | Nhãn – Static | Hiển thị chữ "Tài khoản" ở phía trên cùng của giao diện. |
| Ảnh đại diện (Avatar) | Image | Hiển thị hình ảnh đại diện cá nhân hiện tại của du khách. |
| Họ và tên | Text – String | Hiển thị họ và tên đầy đủ của chủ tài khoản. |
| Số điện thoại | Text – String | Hiển thị số điện thoại liên kết với tài khoản. |
| Địa chỉ Email | Text – String | Hiển thị hòm thư điện tử cá nhân của du khách. |
| Chỉnh sửa thông tin | Button / Row | Nút bấm (hoặc dòng chọn) có icon mũi tên dẫn sang màn hình cập nhật thông tin cá nhân. |
| Đăng xuất | Button / Row | Nút chức năng nằm ở phía dưới để thoát tài khoản hiện tại ra khỏi ứng dụng. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Chỉnh sửa thông tin** | Du khách nhấn chọn để thay đổi thông tin cá nhân. | Hệ thống chuyển hướng người dùng sang giao diện "Chỉnh sửa thông tin tài khoản". | Lỗi điều hướng màn hình -> Hiển thị thông báo thử lại. |
| **Đăng xuất** | Người dùng thực hiện thoát quyền đăng nhập trên thiết bị. | Hệ thống xóa token phiên làm việc, đăng xuất tài khoản và đưa người dùng về trang Đăng nhập/Trang chủ công cộng. | Mất kết nối internet -> Đăng xuất thất bại và yêu cầu kiểm tra mạng. |

---

### b. Giao diện Chỉnh sửa thông tin tài khoản

| **Màn hình** | **Chỉnh sửa thông tin tài khoản** |
| :--- | :--- |
| **Mô tả** | Biểu mẫu trên ứng dụng di động cho phép du khách thay đổi ảnh đại diện và cập nhật lại các thông tin cá nhân của mình. |
| **Màn hình kết nối** | Thông tin tài khoản |

**Nội dung màn hình:**

| **Item** | **Kiểu dữ liệu** | **Mô tả** |
| :--- | :--- | :--- |
| Tiêu đề màn hình | Nhãn – Static | Hiển thị chữ "Chỉnh sửa thông tin" ở thanh điều hướng phía trên. |
| Nút Quay lại (Back) | Icon Button | Biểu tượng mũi tên quay lại góc trái để hủy thao tác nhanh và trở về màn hình trước. |
| Thay đổi ảnh đại diện | Icon / Button | Nút bấm đè lên vùng ảnh đại diện (thường có hình camera) cho phép kích hoạt tải ảnh mới lên. |
| Họ và tên | Textfield – String | Ô nhập văn bản cho phép du khách chỉnh sửa hoặc nhập lại họ tên mới. |
| Số điện thoại | Textfield – String | Ô nhập cho phép thay đổi số điện thoại liên lạc. |
| Địa chỉ Email | Textfield – String | Ô nhập cho phép thay đổi hoặc cập nhật email cá nhân. |
| Nút Hủy bỏ | Button | Nút nhấn để hủy toàn bộ các thông tin vừa thay đổi và quay lại màn hình hồ sơ tài khoản. |
| Nút Lưu thay đổi | Button | Nút nhấn để xác nhận gửi dữ liệu cập nhật lên máy chủ hệ thống. |

**Các chức năng màn hình:**

| **Tên chức năng** | **Mô tả** | **Thành công** | **Thất bại** |
| :--- | :--- | :--- | :--- |
| **Cập nhật ảnh đại diện**| Người dùng chọn một hình ảnh mới từ thư viện máy hoặc chụp trực tiếp. | Ảnh đại diện mới được hiển thị tạm thời trên khung tròn avatar để chuẩn bị lưu dữ liệu. | Tệp tin chọn không đúng định dạng ảnh hoặc quá dung lượng cho phép -> Hệ thống báo lỗi. |
| **Lưu thay đổi** | Hệ thống kiểm tra dữ liệu đầu vào và tiến hành lưu lại thông tin tài khoản mới. | Dữ liệu cập nhật thành công vào CSDL, hệ thống hiển thị thông báo "Cập nhật thành công" và tự động chuyển về màn hình Thông tin tài khoản. | Trường thông tin bắt buộc bị bỏ trống, hoặc định dạng email/SĐT không hợp lệ -> Hệ thống viền đỏ ô lỗi và hiển thị cảnh báo nhắc nhở chỉnh sửa. |
