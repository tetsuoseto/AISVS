# Sử dụng AISVS

Tiêu chuẩn Xác minh Bảo mật Trí tuệ nhân tạo (AISVS) định nghĩa các yêu cầu bảo mật cho các ứng dụng và dịch vụ AI hiện đại, tập trung vào các khía cạnh nằm trong phạm vi kiểm soát của các nhà phát triển ứng dụng.

AISVS được thiết kế cho bất kỳ ai đang phát triển hoặc đánh giá bảo mật của các ứng dụng AI, bao gồm các nhà phát triển, kiến trúc sư, kỹ sư bảo mật và kiểm toán viên. Chương này giới thiệu cấu trúc và cách sử dụng AISVS, bao gồm các cấp xác thực và các trường hợp sử dụng được định sẵn.

## Các mức xác thực bảo mật của Trí tuệ nhân tạo

AISVS định nghĩa ba cấp độ xác thực bảo mật tăng dần. Mỗi cấp độ tăng thêm độ sâu và độ phức tạp, cho phép các tổ chức điều chỉnh tư thế bảo mật của họ cho phù hợp với mức rủi ro của các hệ thống AI của họ.

Các tổ chức có thể bắt đầu ở cấp độ 1 và dần áp dụng các cấp độ cao hơn khi mức độ trưởng thành bảo mật và mức phơi nhiễm mối đe dọa tăng lên.

### Định nghĩa các cấp độ

Mỗi yêu cầu trong AISVS v1.0 được gán cho một trong các mức sau đây:

#### Yêu cầu cấp độ 1

Cấp độ 1 bao gồm các yêu cầu bảo mật quan trọng nhất và nền tảng nhất. Chúng tập trung vào việc ngăn chặn các cuộc tấn công phổ biến mà không dựa vào các điều kiện tiên quyết hoặc lỗ hổng khác. Hầu hết các biện pháp kiểm soát cấp 1 đều dễ triển khai hoặc đủ cần thiết để biện minh cho nỗ lực.

#### Yêu cầu cấp độ 2

Cấp độ 2 giải quyết các cuộc tấn công tiên tiến hoặc ít gặp hơn, đồng thời triển khai các biện pháp phòng thủ nhiều lớp nhằm đối phó với các mối đe dọa lan rộng.

#### Yêu cầu cấp độ 3

Cấp độ 3 bao gồm các biện pháp kiểm soát thường khó triển khai hơn hoặc có tính áp dụng tùy hoàn cảnh. Những biện pháp này thường đại diện cho các cơ chế phòng thủ nhiều lớp hoặc các biện pháp giảm thiểu nhằm chống lại những cuộc tấn công đặc thù, được nhắm mục tiêu hoặc có độ phức tạp cao.

### Vai trò (D/V)

Mỗi yêu cầu AISVS được đánh dấu theo đối tượng người dùng chính:

* D – Yêu cầu dành cho nhà phát triển
* V – Yêu cầu dành cho người xác thực/ kiểm toán viên
* D/V – Liên quan đến cả nhà phát triển và người kiểm tra

