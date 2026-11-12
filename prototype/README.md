# Bay cùng nhau — Prototype LAB5 / T3

Mở trực tiếp **[index.html](index.html)** bằng Edge, Chrome hoặc Firefox. HTML chứa toàn bộ CSS, JavaScript và icon SVG; không cần cài thư viện, mạng, tài khoản hay API key.

Đây là mô phỏng xác định theo kịch bản, không có AI hoặc backend thật. Chính sách Bay Mẫu và mọi kết quả thao tác đều là dữ liệu dựng. Thông tin và nhật ký chỉ tồn tại trong phiên; tải lại trang sẽ đặt lại dữ liệu.

## Demo ca chính

1. Chọn `S03 · Hai mẹ con cần bay tối nay`. Chuyến BM 217 chỉ có một chỗ nên không cho đổi hai người hoặc tách hành khách.
2. Chọn `07:00 cho cả hai` hoặc `09:30 cho cả hai`: hành động này chấp nhận ngày 13/11 và giữ hai chỗ trong 20 phút, chưa đổi vé.
3. Bấm `Xem lại để đổi`. Kiểm tra ngày, giờ, tên hai người, phí 0 ₫ và việc dùng lần đổi miễn phí duy nhất.
4. Tự tích ô đồng ý, rồi bấm nút xác nhận ghi rõ chuyến và hai hành khách. Kết quả chỉ xuất hiện sau phản hồi mô phỏng.
5. Dùng `Báo thông tin không đúng` để gửi hồ sơ; có thể bổ sung ghi chú. Không có chức năng tự hoàn tác vé đã đổi.

Trước khi đổi, có thể hủy giữ chỗ hoặc chọn chuyến khác. Khi đổi phương án, phải xác nhận nhả chỗ cũ trước khi giữ chỗ mới; không giữ đồng thời nhiều chuyến.

## Các ca còn lại

| Ca | Cách thử / hành vi cần thấy |
|---|---|
| N01 | Tự giữ BM 201 theo ý định đã rõ, vẫn cần người dùng duyệt đổi. |
| S02 | “Ừ đổi đi” không tự giữ hoặc đổi. Phải chọn chuyến và xem bản duyệt. |
| S07 | Bấm `Xem trước hoàn cho cả hai`. Số tiền, nơi nhận và thời gian chưa xác minh; nút gửi bị khóa. Hồ sơ xác minh được chuyển, yêu cầu hoàn chưa được gửi. |
| S09 | Lỗi cũ được khởi tạo sẵn: chỉ vé Bình đã đổi. Hiện trạng thái từng người, khóa đổi/hoàn mới, chuyển hồ sơ. |
| S08 | Lỗi cũ được khởi tạo sẵn: hoàn đã gửi lúc 15:04. Hiện biên nhận, không có nút rút hoàn hoặc khôi phục vé. |
| S06 | Giữ chỗ, bấm xem lại. Đồng hồ mô phỏng tiến 21 phút, hết hạn và khóa duyệt cũ. Tra cứu lại, chọn và duyệt mới. |
| S05 | Giữ chỗ, xem lại và duyệt. Khi kiểm tra trước thực thi, chuyến đã chọn chỉ còn một chỗ; từ chối cả nhóm, không tiêu quyền đổi. |
| Timeout | Sau duyệt, chưa rõ kết quả và khóa thao tác xung đột. Bấm `Kiểm tra trạng thái thao tác` để đọc lịch sử; không gọi đổi lần nữa. |
| Lỗi tra cứu | Không hiện dữ liệu chưa xác minh; bấm thử tra cứu lại. |
| Lỗi chuyển hồ sơ | Bấm nhờ nhân viên: lần gửi đầu thất bại. Ghi chú được giữ khi thử lại. Không báo đã gửi trước khi có phản hồi. |

Chat hỗ trợ một số câu theo fixture (hỏi giờ bay, bồi thường, trẻ bay một mình, đổi tên, yêu cầu vượt xác nhận). Câu ngoài kịch bản sẽ được hỏi rõ hoặc chuyển hỗ trợ; không tự sinh dữ liệu chuyến bay. Chat không thay nút phê duyệt giao dịch.

`Đặt lại` hoặc thay bộ chọn ca sẽ bắt đầu một phiên mới. Các ca lỗi lịch sử được gắn nhãn riêng; luồng bình thường không tạo lỗi bằng cách bỏ qua rào chắn.

## Ảnh và kiểm chứng

- [Ảnh 1 — chọn phương án, các điểm 1–3](01-chon-phuong-an.png).
- [Ảnh 2 — xác nhận đổi, điểm 4](02-xac-nhan-doi.png). Điểm 5 và 6 được kiểm tra bằng tương tác qua bộ chọn ca và kết quả/hồ sơ hỗ trợ.
- [Ảnh giao diện điện thoại](03-mobile.png).
- [Kết quả 24 kiểm tra trình duyệt](verification.json): Microsoft Edge 157 với Playwright, chạy cả HTTP cục bộ và mở HTML trực tiếp; kiểm tra chiều rộng 1440, 1024, 768, 390 và 360 px.

P1: chặn giao dịch thiếu quyền/duyệt, xử lý cả nhóm và không gửi lặp. P2: trạng thái khớp dữ liệu và phản hồi mô phỏng, phân biệt kết quả chưa rõ. P3: sửa/hủy giữ chỗ, gửi hồ sơ và thử lại đúng khả năng. Các kiểm tra đã chạy đều đạt; chưa demo với TA, chưa kiểm chứng API hay sản phẩm thực tế.

Nếu cần chạy qua HTTP, tại thư mục này dùng `python -m http.server 5173 --bind 127.0.0.1`, rồi mở `http://127.0.0.1:5173`. Mở trực tiếp file vẫn là cách mặc định.
