# Sử dụng AISVS

Tiêu chuẩn Xác minh An ninh Trí tuệ Nhân tạo (AISVS) xác định các yêu cầu về an ninh cho các ứng dụng và dịch vụ AI hiện đại, tập trung vào các khía cạnh trong tầm kiểm soát của nhà phát triển ứng dụng.

AISVS dành cho bất kỳ ai phát triển hoặc đánh giá bảo mật của các ứng dụng AI, bao gồm nhà phát triển, kiến trúc sư, kỹ sư bảo mật và kiểm toán viên. Chương này giới thiệu cấu trúc và cách sử dụng AISVS, bao gồm các cấp độ xác minh và các trường hợp sử dụng dự kiến.

## Các cấp độ xác minh bảo mật Trí tuệ Nhân tạo

AISVS định nghĩa ba cấp độ xác minh an ninh tăng dần. Mỗi cấp độ bổ sung độ sâu và độ phức tạp, cho phép các tổ chức điều chỉnh tư thế an ninh phù hợp với mức độ rủi ro của hệ thống AI của họ.

Các tổ chức có thể bắt đầu ở Cấp độ 1 và dần dần áp dụng các cấp độ cao hơn khi độ trưởng thành về bảo mật và mức độ phơi nhiễm trước các mối đe dọa tăng lên.

### Định nghĩa các cấp độ

Mỗi yêu cầu trong AISVS phiên bản 1.0 được phân bổ vào một trong các cấp độ sau:

#### Yêu cầu cấp độ 1

Cấp độ 1 bao gồm các yêu cầu bảo mật quan trọng và nền tảng nhất. Những yêu cầu này tập trung vào việc ngăn chặn các cuộc tấn công phổ biến không phụ thuộc vào các điều kiện tiên quyết hoặc các lỗ hổng khác. Hầu hết các kiểm soát cấp độ 1 đều dễ triển khai hoặc đủ quan trọng để biện minh cho nỗ lực thực hiện.

#### Yêu cầu cấp độ 2

Cấp độ 2 giải quyết các cuộc tấn công nâng cao hơn hoặc ít phổ biến hơn, cũng như các biện pháp phòng thủ nhiều lớp chống lại các mối đe dọa lan rộng. Những yêu cầu này có thể liên quan đến logic phức tạp hơn hoặc nhắm vào các điều kiện tiên quyết cụ thể của cuộc tấn công.

#### Yêu cầu cấp độ 3

Cấp độ 3 bao gồm các biện pháp kiểm soát thường khó thực hiện hơn hoặc chỉ áp dụng trong các tình huống cụ thể. Chúng thường đại diện cho các cơ chế phòng thủ đa lớp hoặc các biện pháp giảm thiểu chống lại các cuộc tấn công đặc thù, có mục tiêu hoặc phức tạp cao.

### Vai trò (D/V)

Mỗi yêu cầu AISVS được đánh dấu theo đối tượng chính:

* D – Yêu cầu tập trung vào nhà phát triển
* V – Các yêu cầu tập trung vào người kiểm tra/kiểm toán viên
* D/V – Liên quan đến cả nhà phát triển và người kiểm chứng

