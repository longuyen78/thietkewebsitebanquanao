# NHẬT KÝ SỬ DỤNG CÔNG CỤ AI CHI TIẾT — long2hand (AI_LOG · FIT4014)

## 1. Thông tin chung
- **Tên đề tài:** Trang web bán đồ 2hand tối giản **long2hand**[cite: 28]
- **Sinh viên thực hiện:** Nguyễn Bá Long · **Mã SV:** 2071020215 · **Lớp:** CNTT 20-02
- **Học phần:** FIT4014 · Thiết kế web và triển khai hệ thống phần mềm · **Trường:** Đại học Đại Nam[cite: 3, 13]
- **Giảng viên hướng dẫn:** ThS. Lê Thái Bảo (`baolt@dainam.edu.vn`)[cite: 3, 13]
- **Môi trường phát triển:** Visual Studio Code trên Windows, quản lý mã nguồn bằng Git và xuất bản qua GitHub Pages[cite: 1, 18, 24]
- **Phân bổ công sức thực hiện:**
  - **Tự thực hiện (~70%):** Lên ý tưởng cửa hàng đồ 2hand `long2hand`, dựng khung cấu trúc trang, chia danh mục (áo thun, áo khoác, quần đùi, quần dài, giày), chuẩn bị ảnh trong `image/ảnh web/`, thiết lập quy tắc đồ 2hand mỗi món 1 chiếc với size riêng của từng món, biên soạn nội dung và kiểm tra tổng thể bài làm[cite: 24, 28].
  - **Hỗ trợ từ AI (~30%):** Hỗ trợ rà soát và sửa các lỗi thiết kế giao diện, điều chỉnh bảng màu dịu mắt, căn chỉnh lưới responsive và hoàn thiện bố cục hiển thị bill/đánh giá[cite: 29].

---

## 2. Phần việc tự làm (70% — Dựng khung & ý tưởng)
1. **Định hình ý tưởng và tên thương hiệu (`long2hand`):** Xác định rõ mô hình bán đồ 2hand tối giản, gọn nhẹ, phù hợp phạm vi bài tập lớn tĩnh HTML5/CSS3/JS[cite: 18, 28].
2. **Thiết kế khung nội dung và luồng sử dụng:** Chia trang thành các khu vực rõ ràng gồm phần giới thiệu (`#top`), khu vực danh mục riêng (`#danh-muc`), danh sách sản phẩm (`#san-pham`), khu vực mua hàng & xuất bill (`#mua-hang`) và khu vực đánh giá (`#danh-gia`)[cite: 28].
3. **Xây dựng nghiệp vụ đặc thù đồ 2hand:** Quy định mỗi sản phẩm chỉ có số lượng `1 chiếc`, gán 1 size riêng cho từng món và khi bấm vào sản phẩm sẽ chuyển xuống khu vực đặt mua[cite: 28].
4. **Chuẩn bị tài nguyên và thông tin liên hệ:** Sắp xếp hình ảnh sản phẩm trong `image/ảnh web/`[cite: 28], cập nhật SĐT `0971037740`, Gmail `nguyenbalong070820007@gmail.com` và Facebook `https://www.facebook.com/nguyen.long.486500/`.

---

## 3. Nhật ký chi tiết dùng AI sửa lỗi thiết kế giao diện (~30%)

### Phiên 1: Khắc phục bảng màu chói mắt khi xem lâu
- **Vấn đề giao diện ban đầu:** Nền sáng gắt và các điểm nhấn màu đậm khiến giao diện dễ gây chói mắt khi đọc nội dung dài.
- **Cách AI hỗ trợ sửa:** Đề xuất bảng biến màu trung tính trong `css/style.css` gồm nền kem nhạt `#FAF9F6`, thẻ trắng ngà `#FFFFFF`, khối phụ be xám `#F1EFEA`, chữ xám than `#2D3330` và điểm nhấn xanh rêu trầm `#5C7065`[cite: 29].
- **Kiểm tra sau khi sửa:** Mở trang trên trình duyệt, kiểm tra độ dễ đọc của tiêu đề, đoạn mô tả, nút bấm và viền thẻ; màu sắc hài hòa, dịu mắt, không bị chói.

### Phiên 2: Sửa lỗi lệch chiều cao thẻ và tràn bố cục trên màn hình hẹp
- **Vấn đề giao diện ban đầu:** Các thẻ sản phẩm và thẻ đánh giá có độ dài nội dung khác nhau nên khi xếp lưới dễ bị lệch hoặc chật chội trên màn hình nhỏ.
- **Cách AI hỗ trợ sửa:** Sử dụng CSS Grid (`repeat(3, minmax(0, 1fr))` cho màn hình rộng, chuyển 2 cột ở `max-width: 860px` và 1 cột ở `max-width: 560px`) kết hợp `flex: 1` cho phần mô tả `.desc` để chân thẻ thẳng hàng[cite: 29].
- **Kiểm tra sau khi sửa:** Dùng DevTools (`Ctrl + Shift + I`) kiểm tra ở cả màn hình rộng và màn hình hẹp; các thẻ xếp đều, ảnh giữ tỷ lệ `4 / 3` bằng `object-fit: cover` và không bị vỡ khung[cite: 29].

### Phiên 3: Hoàn thiện tương tác chọn sản phẩm sang mua hàng & hiển thị size riêng từng món
- **Vấn đề giao diện ban đầu:** Cần đồng bộ giữa việc bấm chọn 1 món đồ 2hand ở danh sách sản phẩm với phần tóm tắt, ô chọn món và thông tin size của món đó ở khu vực mua hàng[cite: 28].
- **Cách AI hỗ trợ sửa:** Bổ sung hàm đồng bộ sản phẩm đang chọn, gắn size riêng cho từng món (quần áo `S`–`XL`, giày `38`–`42`), khóa số lượng ở mức `1 chiếc` và cuộn mượt tới `#mua-hang` khi người dùng bấm vào thẻ sản phẩm[cite: 28].
- **Kiểm tra sau khi sửa:** Bấm thử vào nhiều thẻ sản phẩm thuộc các danh mục khác nhau; tên món, giá, size món đó tự cập nhật đúng và cuộn tới khu vực mua hàng.

### Phiên 4: Hoàn thiện khung bill sau khi xác nhận đặt mua & khu vực đánh giá
- **Vấn đề giao diện ban đầu:** Sau khi nhấn xác nhận đặt mua, thông tin đơn hàng cần hiển thị thành phiếu bill rõ ràng, dễ nhìn và có nút in/lưu bill; phần đánh giá cần hiển thị 7 khách với số sao 3–5 sao tập trung vào không gian quán và chất lượng sản phẩm[cite: 28].
- **Cách AI hỗ trợ sửa:** Thiết kế khối `.bill-box` hiển thị mã bill, thời gian, thông tin người nhận, bảng chi tiết sản phẩm/size/số lượng/thành tiền cùng kiểu `@media print` cho nút in bill, đồng thời dựng lưới đánh giá 7 khách không có nút đổi sao ngẫu nhiên[cite: 28, 29].
- **Kiểm tra sau khi sửa:** Điền thử thông tin đặt mua và nhấn **Xác nhận đặt mua**, kiểm tra bill hiển thị đầy đủ dữ liệu và kiểm tra 7 thẻ đánh giá hiển thị đúng số sao 3–5 sao.

---

## 4. Cam kết minh bạch và trách nhiệm (TC7)
- Toàn bộ nội dung nhật ký phản ánh quá trình dựng khung 70% của cá nhân và việc sử dụng AI hỗ trợ sửa lỗi thiết kế giao diện.
- Mọi thay đổi đều được kiểm tra thực tế trên mã nguồn trong thư mục `thietkewebsitebanquanao` trước khi đưa vào báo cáo và đẩy lên repository `longuyen78/thietkewebsitebanquanao`[cite: 24, 25].