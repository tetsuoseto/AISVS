# Sử dụng AISVS

Tiêu chuẩn Xác minh An ninh Trí tuệ Nhân tạo (AISVS) định nghĩa các yêu cầu về an ninh cho các ứng dụng và dịch vụ AI hiện đại, tập trung vào các khía cạnh nằm trong tầm kiểm soát của các nhà phát triển ứng dụng.

AISVS dành cho bất kỳ ai phát triển hoặc đánh giá bảo mật của các ứng dụng AI, bao gồm nhà phát triển, kiến trúc sư, kỹ sư bảo mật và kiểm toán viên. Chương này giới thiệu cấu trúc và cách sử dụng AISVS, bao gồm các cấp độ xác minh và các trường hợp sử dụng dự kiến.

## Các cấp độ xác minh an ninh Trí tuệ Nhân tạo

AISVS định nghĩa ba cấp độ xác minh bảo mật tăng dần. Mỗi cấp độ tăng thêm độ sâu và sự phức tạp, cho phép các tổ chức điều chỉnh vị thế bảo mật của họ phù hợp với mức độ rủi ro của các hệ thống AI.

Các tổ chức có thể bắt đầu ở Cấp độ 1 và dần dần áp dụng các cấp độ cao hơn khi độ trưởng thành về bảo mật và mức độ tiếp xúc với mối đe dọa tăng lên.

### Định nghĩa các cấp độ

Mỗi yêu cầu trong AISVS v1.0 được phân công vào một trong các cấp độ sau:

#### Yêu cầu cấp độ 1

Cấp độ 1 bao gồm các yêu cầu bảo mật quan trọng và cơ bản nhất. Những yêu cầu này tập trung vào việc ngăn chặn các cuộc tấn công phổ biến không phụ thuộc vào các điều kiện tiên quyết hay lỗ hổng khác. Hầu hết các biện pháp kiểm soát ở Cấp độ 1 đều dễ thực hiện hoặc quan trọng đến mức đáng để bỏ công sức thực hiện.

#### Yêu cầu cấp độ 2

Cấp 2 xử lý các cuộc tấn công nâng cao hơn hoặc ít phổ biến hơn, cũng như các biện pháp phòng thủ nhiều lớp chống lại các mối đe dọa rộng rãi. Các yêu cầu này có thể liên quan đến logic phức tạp hơn hoặc nhắm vào các điều kiện tiên quyết cụ thể của cuộc tấn công.

#### Yêu cầu cấp độ 3

Cấp độ 3 bao gồm các kiểm soát thường khó thực hiện hơn hoặc chỉ phù hợp trong các tình huống nhất định. Chúng thường đại diện cho các cơ chế phòng thủ sâu hoặc các biện pháp giảm thiểu đối với các cuộc tấn công đặc thù, có mục tiêu hoặc có độ phức tạp cao.

### Vai trò (D/V)

Mỗi yêu cầu AISVS được đánh dấu theo đối tượng chính:

* D – Yêu cầu tập trung vào nhà phát triển
* V – Các yêu cầu tập trung vào người kiểm tra/đánh giá
* D/V – Liên quan đến cả nhà phát triển và người kiểm tra

