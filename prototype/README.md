# Prototype T3 — Bay cùng nhau

Mở trực tiếp [index.html](index.html) bằng trình duyệt. File chạy cục bộ, không cần cài đặt, đăng nhập, API key, backend hoặc AI thật. Chuyến bay, hành khách, hãng Bay Mẫu và mọi kết quả là dữ liệu dựng.

## Ba ca và ba mức

Chọn **S03**, **S07** hoặc **S04** ở đầu trang. Mức **2 · Khách xác nhận** là lựa chọn chính thức của nhóm và mặc định. Mức 1 và 3 chỉ dùng so sánh; chuyển ca hoặc mức đặt lại phiên và thông báo trạng thái cũ đã xóa.

- **Mức 1:** AI chỉ gợi ý; không giữ chỗ, đổi chuyến hay gửi hoàn. Khách cần tự xử lý hoặc nhờ nhân viên.
- **Mức 2:** AI được giữ chỗ ở S03 sau khi khách chọn rõ chuyến đủ chỗ; việc đổi vé chờ khách xác nhận. Ở S07, gửi hoàn bị khóa vì thiếu thông tin. Ở S04, trợ lý không tự xử lý trẻ bay một mình.
- **Mức 3:** phương án bị loại. Màn hình trình bày hậu quả giả định của việc tự đổi hoặc tự gửi hoàn; không thực hiện giao dịch. S04 vẫn không tự đổi riêng vé trẻ ở bất kỳ mức nào.

## Bấm demo

1. **S03:** đọc lý do một chỗ không đủ cho hai người → chọn BM 201 hoặc BM 205 cho cả hai → thấy đã giữ 20 phút nhưng chưa đổi → bấm xem lại → kiểm tra chuyến, hai hành khách và hậu quả → tích xác nhận rồi bấm đổi. Có thể hủy giữ hoặc sửa lựa chọn; chuyển sang chuyến khác cần xác nhận nhả chỗ cũ. Hết hạn thì chọn lại.
2. **S07:** bấm xem trước hoàn → thấy số tiền, nơi nhận và thời gian chưa xác minh, cảnh báo không rút được và nút gửi bị khóa → bấm gặp nhân viên để gửi hồ sơ mô phỏng. Chưa gửi yêu cầu hoàn.
3. **S04:** đọc giới hạn trẻ 5 tuổi bay một mình → bấm gặp nhân viên → thấy trạng thái đang gửi và hệ thống hỗ trợ mô phỏng đã nhận. S04 là ca lạ **để luyện tập**; ca lạ trong buổi demo do người xem đưa và có thể khác.

Ô **Hiện chú thích HAX/PAIR** bật hoặc tắt cả số trên giao diện và bảng giải thích. Khi bật, bảng chỉ hiện số của trạng thái đang xem. Ảnh minh họa: [S03 xác nhận](01-s03-xac-nhan.png), [S07 hoàn vé](02-s07-hoan-ve.png).

Bảng công cụ giữ tên đầy đủ; trên màn hình hẹp, đưa focus vào bảng bằng phím Tab rồi dùng phím mũi tên để cuộn ngang. Đổi ca hoặc mức vẫn đặt lại phiên ngay và thông báo trạng thái cũ đã xóa.

## Phạm vi kiểm tra

Đã kiểm tra bằng Edge/Playwright ở 360, 390, 768, 860, 1024 và 1440 px sau chỉnh UI: S03 giữ chỗ, khóa duyệt trước khi tích và đổi sau xác nhận; S07 khóa gửi; S04 không có nút đổi riêng trẻ ở ba mức; chuyển hỗ trợ; giữ chỗ hết hạn mô phỏng; chuyển ca/mức; ẩn/hiện chú thích và cuộn bảng bằng bàn phím; focus trở về vùng hội thoại khi chuyển trạng thái. Không phát hiện tràn ngang toàn trang hoặc lỗi JavaScript trong các lượt này. Bảng cuộn ngang cục bộ khi không đủ chỗ. Kết quả cũ của phiên bản trước không được sử dụng.

Kiểm tra bổ sung ở 390 và 1440 px: chuyển đủ ba mức trong từng ca S03/S07/S04; hai mức so sánh không hiển thị nút thực hiện giao dịch.

Giới hạn: đây là kịch bản cố định, không nhận câu hỏi tự do; không mô phỏng S08/S09, thay đổi chỗ thực tế, lỗi gửi hồ sơ hoặc timeout. Chưa demo với TA, chưa kiểm chứng sản phẩm thật; không có dữ liệu hoàn đầy đủ để thực hiện gửi hoàn thành công.
