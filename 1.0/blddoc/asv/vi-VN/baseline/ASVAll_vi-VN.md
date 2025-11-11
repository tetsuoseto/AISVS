## Trang đầu sách

### Về Tiêu chuẩn

Tiêu chuẩn Xác minh An ninh Trí tuệ Nhân tạo (AISVS) là một danh mục các yêu cầu an ninh do cộng đồng phát triển, mà các nhà khoa học dữ liệu, kỹ sư MLOps, kiến trúc sư phần mềm, nhà phát triển, kiểm thử viên, chuyên gia an ninh, nhà cung cấp công cụ, cơ quan quản lý và người tiêu dùng có thể sử dụng để thiết kế, xây dựng, kiểm thử và xác minh các hệ thống và ứng dụng được hỗ trợ bởi AI đáng tin cậy. Nó cung cấp một ngôn ngữ chung để chỉ định các biện pháp kiểm soát an ninh trong suốt vòng đời AI — từ thu thập dữ liệu và phát triển mô hình đến triển khai và giám sát liên tục — để các tổ chức có thể đo lường và cải thiện khả năng phục hồi, tính riêng tư và an toàn của các giải pháp AI của họ.

### Bản quyền và Giấy phép

Phiên bản 0.1 (Bản Dự Thảo Công Khai Đầu Tiên - Đang Trong Quá Trình Hoàn Thiện), 2025  

![license](images/license.png)
Bản quyền © 2025 Dự án AISVS.  

Phát hành theo Creative Commons Attribution‑ShareAlike 4.0 International License.
Đối với bất kỳ việc tái sử dụng hoặc phân phối nào, bạn phải truyền đạt rõ ràng các điều khoản giấy phép của tác phẩm này đến người khác.

### Trưởng nhóm dự án

Jim Manico
Aras “Russ” Memisyazici

### Người đóng góp và người đánh giá

https://github.com/ottosulin
https://github.com/mbhatt1
https://github.com/vineethsai
https://github.com/cciprofm
https://github.com/deepakrpandey12


────────────────────────────────────────

AISVS là một tiêu chuẩn hoàn toàn mới được tạo ra đặc biệt để giải quyết các thách thức bảo mật riêng biệt của hệ thống trí tuệ nhân tạo. Mặc dù nó lấy cảm hứng từ các thực tiễn bảo mật tốt hơn nói chung, mọi yêu cầu trong AISVS đều được phát triển từ đầu để phản ánh bối cảnh nguy cơ của AI và giúp các tổ chức xây dựng các giải pháp AI an toàn hơn, bền vững hơn.

## Lời nói đầu

Chào mừng bạn đến với Tiêu chuẩn Xác minh An ninh Trí tuệ Nhân tạo (AISVS) phiên bản 1.0!

### Giới thiệu

Được thành lập vào năm 2025 thông qua một nỗ lực cộng đồng hợp tác, AISVS xác định các yêu cầu về bảo mật cần xem xét khi thiết kế, phát triển, triển khai và vận hành các mô hình AI hiện đại, các quy trình và dịch vụ được hỗ trợ bởi AI.

AISVS phiên bản 1.0 là kết quả công việc kết hợp của các trưởng dự án, nhóm làm việc và các cộng tác viên trong cộng đồng rộng lớn hơn nhằm tạo ra một chuẩn mực cơ bản thực tiễn và có thể kiểm tra được cho việc bảo mật các hệ thống AI.

Mục tiêu của chúng tôi với phiên bản này là làm cho AISVS dễ dàng áp dụng trong khi vẫn tập trung cao độ vào phạm vi đã định và giải quyết bối cảnh rủi ro thay đổi nhanh chóng đặc thù của AI.

### Mục tiêu chính cho AISVS Phiên bản 1.0

Phiên bản 1.0 sẽ được tạo ra với một số nguyên tắc hướng dẫn.

#### Phạm vi xác định rõ ràng

Mỗi yêu cầu phải phù hợp với tên và sứ mệnh của AISVS:

Trí tuệ nhân tạo – Các biện pháp kiểm soát hoạt động ở lớp AI/ML (dữ liệu, mô hình, đường ống, hoặc suy luận) và là trách nhiệm của các chuyên gia AI.
Bảo mật – Yêu cầu trực tiếp giảm thiểu các rủi ro về bảo mật, quyền riêng tư hoặc an toàn đã được xác định.
Xác minh – Ngôn ngữ được viết sao cho việc tuân thủ có thể được xác nhận một cách khách quan.
Tiêu chuẩn – Các phần tuân theo cấu trúc và thuật ngữ nhất quán để tạo thành một tài liệu tham khảo mạch lạc.
​
────────────────────────────────────────

Bằng cách tuân theo AISVS, các tổ chức có thể đánh giá một cách có hệ thống và củng cố vị thế bảo mật của các giải pháp AI của họ, thúc đẩy văn hóa kỹ thuật AI an toàn.

## Sử dụng AISVS

Tiêu chuẩn Xác minh An ninh Trí tuệ Nhân tạo (AISVS) định nghĩa các yêu cầu về an ninh cho các ứng dụng và dịch vụ AI hiện đại, tập trung vào các khía cạnh nằm trong tầm kiểm soát của các nhà phát triển ứng dụng.

AISVS dành cho bất kỳ ai phát triển hoặc đánh giá bảo mật của các ứng dụng AI, bao gồm nhà phát triển, kiến trúc sư, kỹ sư bảo mật và kiểm toán viên. Chương này giới thiệu cấu trúc và cách sử dụng AISVS, bao gồm các cấp độ xác minh và các trường hợp sử dụng dự kiến.

### Các cấp độ xác minh an ninh Trí tuệ Nhân tạo

AISVS định nghĩa ba cấp độ xác minh bảo mật tăng dần. Mỗi cấp độ tăng thêm độ sâu và sự phức tạp, cho phép các tổ chức điều chỉnh vị thế bảo mật của họ phù hợp với mức độ rủi ro của các hệ thống AI.

Các tổ chức có thể bắt đầu ở Cấp độ 1 và dần dần áp dụng các cấp độ cao hơn khi độ trưởng thành về bảo mật và mức độ tiếp xúc với mối đe dọa tăng lên.

#### Định nghĩa các cấp độ

Mỗi yêu cầu trong AISVS v1.0 được phân công vào một trong các cấp độ sau:

 Yêu cầu cấp độ 1

Cấp độ 1 bao gồm các yêu cầu bảo mật quan trọng và cơ bản nhất. Những yêu cầu này tập trung vào việc ngăn chặn các cuộc tấn công phổ biến không phụ thuộc vào các điều kiện tiên quyết hay lỗ hổng khác. Hầu hết các biện pháp kiểm soát ở Cấp độ 1 đều dễ thực hiện hoặc quan trọng đến mức đáng để bỏ công sức thực hiện.

 Yêu cầu cấp độ 2

Cấp 2 xử lý các cuộc tấn công nâng cao hơn hoặc ít phổ biến hơn, cũng như các biện pháp phòng thủ nhiều lớp chống lại các mối đe dọa rộng rãi. Các yêu cầu này có thể liên quan đến logic phức tạp hơn hoặc nhắm vào các điều kiện tiên quyết cụ thể của cuộc tấn công.

 Yêu cầu cấp độ 3

Cấp độ 3 bao gồm các kiểm soát thường khó thực hiện hơn hoặc chỉ phù hợp trong các tình huống nhất định. Chúng thường đại diện cho các cơ chế phòng thủ sâu hoặc các biện pháp giảm thiểu đối với các cuộc tấn công đặc thù, có mục tiêu hoặc có độ phức tạp cao.

#### Vai trò (D/V)

Mỗi yêu cầu AISVS được đánh dấu theo đối tượng chính:

D – Yêu cầu tập trung vào nhà phát triển
V – Các yêu cầu tập trung vào người kiểm tra/đánh giá
D/V – Liên quan đến cả nhà phát triển và người kiểm tra

## Quản trị Dữ liệu Đào tạo C1 & Quản lý Thiên lệch

### Mục tiêu Kiểm soát

Dữ liệu đào tạo phải được lấy nguồn, xử lý và duy trì theo cách bảo toàn nguồn gốc, bảo mật, chất lượng và tính công bằng. Việc làm này đáp ứng các nghĩa vụ pháp lý và giảm thiểu rủi ro về thiên lệch, đầu độc dữ liệu hoặc vi phạm quyền riêng tư xuất hiện trong quá trình đào tạo, có thể ảnh hưởng đến toàn bộ vòng đời của AI.

────────────────────────────────────────

### C1.1 Nguồn gốc Dữ liệu Đào tạo

Duy trì một danh mục có thể kiểm chứng của tất cả các bộ dữ liệu, chỉ chấp nhận các nguồn tin cậy và ghi lại mọi thay đổi để có thể kiểm tra.

 #1.1.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng tồn kho cập nhật của mọi nguồn dữ liệu đào tạo (nguồn gốc, người quản lý/chủ sở hữu, giấy phép, phương pháp thu thập, các hạn chế sử dụng dự kiến và lịch sử xử lý) được duy trì.
 #1.1.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các quy trình dữ liệu huấn luyện loại trừ các đặc trưng, thuộc tính hoặc trường không cần thiết (ví dụ: siêu dữ liệu không sử dụng, thông tin nhận dạng cá nhân nhạy cảm, dữ liệu kiểm tra bị rò rỉ).
 #1.1.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng tất cả các thay đổi dữ liệu đều phải tuân theo quy trình phê duyệt có ghi lại.
 #1.1.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các bộ dữ liệu hoặc các tập con đã được đóng dấu nước hoặc ghi dấu vân tay khi có thể thực hiện được.

────────────────────────────────────────

### C1.2 An ninh và tính toàn vẹn của dữ liệu huấn luyện

Hạn chế truy cập vào dữ liệu đào tạo, mã hóa nó khi lưu trữ và truyền tải, đồng thời xác thực tính toàn vẹn của dữ liệu để ngăn chặn việc làm giả, đánh cắp hoặc đầu độc dữ liệu.

 #1.2.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các kiểm soát truy cập bảo vệ việc lưu trữ dữ liệu đào tạo và các đường dẫn xử lý dữ liệu.
 #1.2.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng tất cả các truy cập vào dữ liệu đào tạo đều được ghi lại, bao gồm người dùng, thời gian và hành động.
 #1.2.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các bộ dữ liệu huấn luyện được mã hóa khi truyền và lưu trữ, sử dụng các thuật toán mã hóa tiêu chuẩn ngành và các phương pháp quản lý khóa.
 #1.2.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các hàm băm mật mã hoặc chữ ký số được sử dụng để đảm bảo tính toàn vẹn dữ liệu trong quá trình lưu trữ và truyền tải dữ liệu huấn luyện.
 #1.2.5    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các kỹ thuật phát hiện tự động được áp dụng để ngăn chặn các sửa đổi trái phép hoặc hư hỏng dữ liệu đào tạo.
 #1.2.6    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng dữ liệu huấn luyện lỗi thời đã được xóa một cách an toàn hoặc được ẩn danh.
 #1.2.7    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng tất cả các phiên bản tập dữ liệu huấn luyện đều được nhận dạng duy nhất, lưu trữ không thể thay đổi và có thể kiểm toán để hỗ trợ việc phục hồi và phân tích pháp y.

────────────────────────────────────────

### C1.3 Chất lượng, Tính toàn vẹn và An ninh của Việc Gán nhãn Dữ liệu Đào tạo

Bảo vệ nhãn và yêu cầu xem xét kỹ thuật đối với dữ liệu quan trọng.

 #1.3.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các băm mật mã hoặc chữ ký số được áp dụng cho các hiện vật nhãn để đảm bảo tính toàn vẹn và tính xác thực của chúng.
 #1.3.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các giao diện và nền tảng gán nhãn thực thi các kiểm soát truy cập mạnh mẽ, duy trì nhật ký kiểm toán chống giả mạo cho tất cả các hoạt động gán nhãn, và bảo vệ chống lại các sửa đổi trái phép.
 #1.3.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng thông tin nhạy cảm trong nhãn được xóa hoặc làm ẩn danh hoặc mã hóa ở cấp trường dữ liệu khi lưu trữ và trong quá trình truyền.

────────────────────────────────────────

### C1.4 Đảm bảo Chất lượng và An ninh Dữ liệu Đào tạo

Kết hợp xác thực tự động, kiểm tra ngẫu nhiên thủ công và ghi lại quá trình khắc phục để đảm bảo độ tin cậy của tập dữ liệu.

 #1.4.1    Cấp độ: 1    Vai trò: D
 Xác minh rằng các bài kiểm tra tự động phát hiện lỗi định dạng và giá trị null ở mỗi lần nhập dữ liệu hoặc chuyển đổi dữ liệu quan trọng.
 #1.4.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các quy trình huấn luyện và tinh chỉnh LLM thực hiện phát hiện đầu độc và kiểm tra tính toàn vẹn dữ liệu (ví dụ: các phương pháp thống kê, phát hiện ngoại lệ, phân tích embedding) để nhận diện các cuộc tấn công đầu độc tiềm ẩn (ví dụ: đảo nhãn, chèn kích hoạt backdoor, lệnh đổi vai trò, tấn công các trường hợp có ảnh hưởng) hoặc sự cố vô tình làm hỏng dữ liệu trong dữ liệu huấn luyện.
 #1.4.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các nhãn được tạo tự động (ví dụ, thông qua các LLM hoặc giám sát yếu) phải tuân theo ngưỡng độ tin cậy và các kiểm tra nhất quán để phát hiện các nhãn ảo tưởng, gây hiểu lầm hoặc có độ tin cậy thấp.
 #1.4.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các biện pháp phòng thủ phù hợp, chẳng hạn như huấn luyện chống đối kháng (sử dụng các ví dụ đối kháng được tạo ra), tăng cường dữ liệu với các đầu vào bị nhiễu, hoặc các kỹ thuật tối ưu hóa bền vững, được triển khai và điều chỉnh cho các mô hình liên quan dựa trên đánh giá rủi ro.
 #1.4.5    Cấp độ: 3    Vai trò: D
 Xác nhận rằng các bài kiểm tra tự động phát hiện được sự lệch nhãn trên mọi lần nhập dữ liệu hoặc biến đổi dữ liệu quan trọng.

────────────────────────────────────────

### C1.5 Dòng dữ liệu và khả năng truy xuất nguồn gốc

Theo dõi toàn bộ hành trình của từng điểm dữ liệu từ nguồn đến đầu vào mô hình để đảm bảo khả năng kiểm toán và phản ứng sự cố.

 #1.5.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng nguồn gốc của mỗi điểm dữ liệu, bao gồm tất cả các phép biến đổi, tăng cường và kết hợp, được ghi lại và có thể tái tạo lại.
 #1.5.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các bản ghi nguồn gốc là bất biến, được lưu trữ an toàn và có thể truy cập để kiểm toán.
 #1.5.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng việc theo dõi nguồn gốc bao gồm dữ liệu tổng hợp được tạo ra thông qua các kỹ thuật bảo vệ quyền riêng tư hoặc tạo dữ liệu và tất cả dữ liệu tổng hợp đều được dán nhãn rõ ràng và có thể phân biệt với dữ liệu thực trong toàn bộ quy trình.

────────────────────────────────────────

### Tài liệu tham khảo

NIST AI Risk Management Framework
EU AI Act – Article 10: Data & Data Governance
CISA Advisory: Securing Data for AI Systems
OpenAI Privacy Center – Data Deletion Controls

## Xác thực đầu vào người dùng C2

### Mục tiêu Kiểm soát

Việc xác thực đầu vào của người dùng một cách chặt chẽ là hàng phòng thủ đầu tiên chống lại một số cuộc tấn công gây hại nhất đối với các hệ thống AI. Các cuộc tấn công chèn lệnh (prompt injection) có thể ghi đè các hướng dẫn của hệ thống, làm rò rỉ dữ liệu nhạy cảm hoặc điều hướng mô hình theo hành vi không được phép. Trừ khi có bộ lọc chuyên biệt và các biện pháp xác thực khác được thiết lập, các nghiên cứu cho thấy các cách vượt rào sử dụng khai thác cửa sổ ngữ cảnh vẫn sẽ tiếp tục hiệu quả.

────────────────────────────────────────

### C2.1 Phòng chống Tiêm nhiễm Lệnh Đầu vào

Tiêm nhiễm lệnh đầu vào là một trong những rủi ro hàng đầu đối với các hệ thống AI. Các biện pháp phòng thủ chống lại chiến thuật này sử dụng sự kết hợp của bộ lọc mẫu, bộ phân loại dữ liệu và việc thực thi thứ bậc các hướng dẫn.

 #2.1.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng bất kỳ đầu vào bên ngoài hoặc được dẫn xuất nào có thể điều khiển hành vi, bao gồm các lời nhắc của người dùng, kết quả RAG, đầu ra của plugin hoặc MCP, tin nhắn giữa các agent, phản hồi API hoặc webhook, tệp cấu hình hoặc chính sách, đọc và ghi bộ nhớ, đều được coi là không tin cậy, được làm vô hiệu hóa bằng cách trích dẫn hoặc gắn thẻ và loại bỏ nội dung kích hoạt, đồng thời được sàng lọc bởi bộ quy tắc hoặc dịch vụ phát hiện chèn lời nhắc được duy trì trước khi nối vào lời nhắc hoặc thực thi các hành động.
 #2.1.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng hệ thống thực thi một thứ bậc chỉ dẫn trong đó các tin nhắn của hệ thống và nhà phát triển ghi đè lên các chỉ dẫn của người dùng và các đầu vào không đáng tin cậy khác, ngay cả sau khi xử lý các chỉ dẫn của người dùng.
 #2.1.4    Cấp độ: 2    Vai trò: D
 Xác minh rằng các câu lệnh xuất phát từ nội dung của bên thứ ba (trang web, PDF, email) được làm sạch riêng biệt (ví dụ, loại bỏ các chỉ dẫn dạng hướng dẫn và làm trung hòa nội dung HTML, Markdown, và script) trước khi được ghép nối vào câu lệnh chính.

────────────────────────────────────────

### C2.2 Khả năng chống lại ví dụ đối kháng

Các mô hình Xử lý Ngôn ngữ Tự nhiên (NLP) vẫn còn dễ bị tổn thương bởi những biến động nhỏ ở cấp độ ký tự hoặc từ mà con người thường bỏ qua nhưng các mô hình lại có xu hướng phân loại sai.

 #2.2.1    Cấp độ: 1    Vai trò: D
 Xác minh rằng các bước chuẩn hóa đầu vào cơ bản (Unicode NFC, ánh xạ homoglyph, cắt bớt khoảng trắng, loại bỏ các ký tự điều khiển và Unicode vô hình) được thực hiện trước khi phân tách từ hoặc nhúng và trước khi phân tích cú pháp thành các tham số công cụ hoặc MCP.
 #2.2.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng phát hiện bất thường thống kê đánh dấu các đầu vào có khoảng cách chỉnh sửa cao bất thường so với chuẩn ngôn ngữ hoặc khoảng cách nhúng bất thường và rằng các đầu vào bị đánh dấu này được kiểm soát trước khi nối vào câu lệnh hoặc thực thi các hành động.
 #2.2.3    Cấp độ: 2    Vai trò: D
 Xác minh rằng quy trình suy luận hỗ trợ các biến thể mô hình được củng cố bằng đào tạo chống đối kháng hoặc các lớp phòng thủ (ví dụ: ngẫu nhiên hóa, chiết suất phòng thủ, kiểm tra căn chỉnh) cho các điểm cuối có rủi ro cao.
 #2.2.4    Cấp độ: 2    Vai trò: V
 Xác minh rằng các đầu vào nghi ngờ là tấn công đối kháng được cách ly, đồng thời được ghi lại đầy đủ với toàn bộ nội dung và siêu dữ liệu truy vết (nguồn, công cụ hoặc máy chủ MCP, ID tác nhân, phiên làm việc).
 #2.2.5    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng việc buôn lậu mã hóa và biểu diễn trong cả đầu vào và đầu ra (ví dụ: các ký tự Unicode/điều khiển vô hình, thay thế homoglyph, hoặc văn bản hướng hỗn hợp) được phát hiện và giảm thiểu. Các biện pháp giảm thiểu được phê duyệt bao gồm chuẩn hóa, xác thực lược đồ nghiêm ngặt, từ chối dựa trên chính sách, hoặc đánh dấu rõ ràng.

────────────────────────────────────────

### C2.3 Bộ Ký Tự Lệnh Prompt

Hạn chế bộ ký tự của dữ liệu đầu vào của người dùng chỉ cho phép các ký tự cần thiết cho yêu cầu kinh doanh có thể giúp ngăn chặn nhiều loại cuộc tấn công khác nhau.

 #2.3.1    Cấp độ: 1    Vai trò: D
 Xác minh rằng hệ thống thực hiện giới hạn bộ ký tự cho dữ liệu đầu vào của người dùng, chỉ cho phép các ký tự được yêu cầu rõ ràng cho mục đích kinh doanh.
 #2.3.2    Cấp độ: 1    Vai trò: D
 Xác minh rằng phương pháp danh sách cho phép được sử dụng để định nghĩa tập ký tự được phép.
 #2.3.3    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các đầu vào chứa ký tự nằm ngoài tập hợp cho phép bị từ chối và được ghi lại cùng với siêu dữ liệu theo dõi (nguồn, công cụ hoặc máy chủ MCP, ID đại lý, phiên).

────────────────────────────────────────

### C2.4 Xác thực Lược đồ, Kiểu dữ liệu & Độ dài

Các cuộc tấn công AI với đầu vào bị sai định dạng hoặc quá lớn có thể gây ra lỗi phân tích cú pháp, tràn prompt qua các trường khác nhau và cạn kiệt tài nguyên. Việc thực thi nghiêm ngặt schema cũng là điều kiện tiên quyết khi thực hiện các cuộc gọi công cụ định danh.

 #2.4.1    Cấp độ: 1    Vai trò: D
 Xác minh rằng mọi API, công cụ hoặc điểm cuối MCP đều định nghĩa một sơ đồ đầu vào rõ ràng (JSON Schema, Protobuf hoặc tương đương đa phương thức), từ chối các trường thừa hoặc không xác định và ép kiểu ngầm định, đồng thời xác thực đầu vào phía máy chủ trước khi xây dựng prompt hoặc thực thi công cụ.
 #2.4.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các đầu vào vượt quá giới hạn tối đa về token hoặc byte bị từ chối với lỗi an toàn và không bao giờ bị cắt ngầm.
 #2.4.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các kiểm tra kiểu (ví dụ, phạm vi số, giá trị enum, loại MIME cho hình ảnh/âm thanh) được thực thi phía máy chủ bao gồm cả đối số cho công cụ hoặc MCP.
 #2.4.4    Cấp độ: 2    Vai trò: D
 Xác minh rằng các bộ xác thực ngữ nghĩa, hiểu đầu vào NLP, hoạt động trong thời gian không đổi và tránh các cuộc gọi mạng bên ngoài để ngăn chặn tấn công từ chối dịch vụ (DoS) theo thuật toán.
 #2.4.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng các lỗi xác thực được ghi lại với các đoạn tải trọng đã được che khuất và mã lỗi rõ ràng, đồng thời bao gồm siêu dữ liệu theo dõi (nguồn, công cụ hoặc máy chủ MCP, ID đại lý, phiên làm việc) để hỗ trợ phân tích bảo mật.

────────────────────────────────────────

### C2.5 Sàng lọc Nội dung & Chính sách

Các nhà phát triển nên có khả năng phát hiện các câu lệnh hợp ngữ pháp hợp lệ yêu cầu nội dung bị cấm (chẳng hạn như hướng dẫn bất hợp pháp, ngôn ngữ thù địch và/hoặc văn bản có bản quyền) rồi ngăn chặn chúng lan rộng.

 #2.5.1    Cấp độ: 1    Vai trò: D
 Xác minh rằng một bộ phân loại nội dung (zero shot hoặc tinh chỉnh) đánh giá từng đầu vào và đầu ra về bạo lực, tự làm hại, thù địch, nội dung tình dục và các yêu cầu bất hợp pháp, với các ngưỡng có thể cấu hình.
 #2.5.2    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng các đầu vào vi phạm chính sách sẽ bị từ chối để chúng không được truyền tiếp sang các cuộc gọi LLM hoặc công cụ/MCP phía dưới.
 #2.5.3    Cấp độ: 2    Vai trò: D
 Xác minh rằng việc kiểm duyệt tuân thủ các chính sách cụ thể của người dùng (tuổi tác, các ràng buộc pháp lý khu vực) thông qua các quy tắc dựa trên thuộc tính được giải quyết tại thời điểm yêu cầu, bao gồm các thuộc tính vai trò đại lý.
 #2.5.4    Cấp độ: 3    Vai trò: V
 Xác minh rằng các bản ghi sàng lọc bao gồm điểm tin cậy của bộ phân loại và thẻ danh mục chính sách với giai đoạn áp dụng (trước lời nhắc hoặc sau phản hồi) cùng siêu dữ liệu truy vết (nguồn, công cụ hoặc máy chủ MCP, ID tác nhân, phiên) để tương quan SOC và phát lại red-team trong tương lai.

────────────────────────────────────────

### C2.6 Giới hạn Tốc độ Đầu vào & Ngăn chặn Lạm dụng

Các nhà phát triển nên ngăn chặn việc lạm dụng, cạn kiệt tài nguyên và các cuộc tấn công tự động chống lại các hệ thống AI bằng cách giới hạn tốc độ đầu vào và phát hiện các mẫu sử dụng bất thường.

 #2.6.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng giới hạn tốc độ theo người dùng, theo IP, theo khóa API, theo tác nhân và theo phiên/nhiệm vụ được thực thi cho tất cả các điểm cuối đầu vào và công cụ/MCP.
 #2.6.2    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng giới hạn tốc độ đột biến và duy trì được điều chỉnh để ngăn chặn các cuộc tấn công DoS và tấn công dò tìm mật khẩu, đồng thời các ngân sách theo từng tác vụ (ví dụ như token, cuộc gọi công cụ/MCP, và chi phí) được thực thi cho các vòng lập kế hoạch của agent.
 #2.6.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các mẫu sử dụng bất thường (ví dụ: các yêu cầu liên tiếp nhanh, tràn ngập đầu vào, các cuộc gọi công cụ/MCP thất bại lặp lại hoặc vòng lặp tác nhân đệ quy) kích hoạt các khối tự động hoặc sự leo thang.
 #2.6.4    Cấp độ: 3    Vai trò: V
 Xác minh rằng các bản ghi phòng chống lạm dụng được lưu giữ và xem xét để phát hiện các mẫu tấn công mới nổi, cùng với siêu dữ liệu truy vết (nguồn, công cụ hoặc máy chủ MCP, ID đại lý, phiên).

────────────────────────────────────────

### C2.7 Xác thực đầu vào đa phương thức

Hệ thống AI nên bao gồm việc xác thực mạnh mẽ cho các đầu vào phi văn bản (hình ảnh, âm thanh, tệp tin) để ngăn chặn việc tiêm nhiễm, né tránh hoặc lạm dụng tài nguyên.

 #2.7.1    Cấp độ: 1    Vai trò: D
 Xác minh rằng tất cả các đầu vào không phải văn bản (hình ảnh, âm thanh, tệp tin) đều được kiểm tra hợp lệ về loại, kích thước và định dạng trước khi xử lý, và bất kỳ văn bản được trích xuất nào (từ hình ảnh sang văn bản hoặc giọng nói sang văn bản) cũng như bất kỳ hướng dẫn ẩn hoặc nhúng nào (siêu dữ liệu, các lớp, văn bản thay thế, bình luận) đều được xử lý như nguồn không đáng tin cậy theo mục 2.1.1.
 #2.7.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các tệp được quét để phát hiện phần mềm độc hại và payload ẩn trong ảnh trước khi nhập dữ liệu, và mọi nội dung hoạt động (như script hoặc macro) được loại bỏ hoặc tệp được cách ly quarantine.
 #2.7.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng đầu vào hình ảnh/âm thanh được kiểm tra các nhiễu loạn đối kháng hoặc các mẫu tấn công đã biết, và các phát hiện này kích hoạt cơ chế kiểm soát (chặn hoặc giảm khả năng) trước khi sử dụng mô hình.
 #2.7.4    Cấp độ: 3    Vai trò: V
 Xác nhận rằng các lỗi xác thực đầu vào đa phương thức được ghi lại và kích hoạt cảnh báo để điều tra, kèm theo siêu dữ liệu truy vết (nguồn, công cụ hoặc máy chủ MCP, ID đại lý, phiên).
 #2.7.5    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng phát hiện tấn công đa phương thức nhận diện các cuộc tấn công phối hợp bao gồm nhiều loại dữ liệu đầu vào khác nhau (ví dụ, payload ẩn trong ảnh kết hợp với chèn lệnh trong văn bản) thông qua các quy tắc tương quan và tạo cảnh báo, và các phát hiện được xác nhận sẽ bị chặn hoặc yêu cầu sự phê duyệt của con người tham gia (HITL).
 #2.7.6    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các lỗi xác thực đa phương thức kích hoạt ghi nhật ký chi tiết bao gồm tất cả các phương thức đầu vào, kết quả xác thực và điểm mối đe dọa, cũng như siêu dữ liệu truy vết (nguồn, công cụ hoặc máy chủ MCP, ID đại lý, phiên làm việc).
────────────────────────────────────────

### C2.8 Phát hiện mối đe dọa thích ứng theo thời gian thực

Các nhà phát triển nên sử dụng các hệ thống phát hiện mối đe dọa tiên tiến cho AI, có khả năng thích nghi với các mẫu tấn công mới và cung cấp bảo vệ thời gian thực bằng cách sử dụng kỹ thuật so khớp mẫu biên dịch.

 #2.8.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng việc so khớp mẫu (ví dụ: regex đã biên dịch) hoạt động trên tất cả các đầu vào và đầu ra (bao gồm cả bề mặt công cụ/MCP) với tác động độ trễ tối thiểu.
 #2.8.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các mô hình phát hiện thích ứng điều chỉnh độ nhạy dựa trên hoạt động tấn công gần đây và được cập nhật với các mẫu mới trong thời gian thực, đồng thời kích hoạt các phản ứng điều chỉnh rủi ro (ví dụ như vô hiệu hóa công cụ, thu nhỏ ngữ cảnh hoặc yêu cầu phê duyệt HITL).
 #2.8.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng độ chính xác của việc phát hiện được cải thiện thông qua phân tích ngữ cảnh của lịch sử người dùng, nguồn và hành vi phiên, bao gồm siêu dữ liệu dấu vết (nguồn, công cụ hoặc máy chủ MCP, ID đại lý, phiên).
 #2.8.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các chỉ số hiệu suất phát hiện (tỷ lệ phát hiện, tỷ lệ dương tính giả, độ trễ xử lý) được giám sát và tối ưu hóa liên tục, bao gồm thời gian để chặn và giai đoạn (trước lời nhắc/sau phản hồi).

### Tài liệu tham khảo

OWASP LLM01:2025 Prompt Injection
LLM Prompt Injection Prevention Cheat Sheet
MITRE ATLAS : Adversarial Input Detection
Mitigate jailbreaks and prompt injections

## Quản lý Vòng đời Mô hình C3 & Kiểm soát Thay đổi

### Mục tiêu Kiểm soát

Hệ thống AI phải thực hiện các quy trình kiểm soát thay đổi nhằm ngăn chặn các sửa đổi mô hình trái phép hoặc không an toàn được đưa vào sản xuất. Kiểm soát này đảm bảo tính toàn vẹn của mô hình trong suốt vòng đời - từ phát triển đến triển khai và ngừng sử dụng - giúp phản ứng nhanh với sự cố và duy trì trách nhiệm cho tất cả các thay đổi.

Mục tiêu bảo mật cốt lõi: Chỉ những mô hình được ủy quyền và xác thực mới được đưa vào sản xuất thông qua các quy trình kiểm soát nhằm duy trì tính toàn vẹn, khả năng truy xuất và khả năng phục hồi.

────────────────────────────────────────

### C3.1 Ủy quyền Mô hình & Toàn vẹn

Chỉ những mô hình được ủy quyền với tính toàn vẹn đã được xác minh mới được đưa vào môi trường sản xuất.

 #3.1.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng tất cả các tác phẩm mô hình (trọng số, cấu hình, bộ mã hóa) đều được ký mật mã bởi các thực thể được ủy quyền trước khi triển khai.
 #3.1.2    Cấp độ: 2    Vai trò: V
 Xác minh rằng việc theo dõi phụ thuộc duy trì một kho hàng thời gian thực cho phép nhận diện tất cả các hệ thống sử dụng.
 #3.1.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng hồ sơ nguồn gốc mô hình bao gồm danh tính của thực thể ủy quyền, checksum dữ liệu đào tạo, kết quả kiểm tra xác nhận với trạng thái đạt/không đạt, và dấu thời gian tạo.

────────────────────────────────────────

### C3.2 Xác thực & Kiểm thử Mô hình

Các mô hình phải vượt qua các kiểm tra xác thực bảo mật và an toàn đã được định nghĩa trước khi triển khai.

 #3.2.1    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng các mô hình trải qua kiểm thử bảo mật tự động bao gồm xác thực đầu vào, làm sạch đầu ra, và đánh giá an toàn với các ngưỡng đạt/không đạt đã được tổ chức đồng thuận trước khi triển khai.
 #3.2.2    Cấp độ: 1    Vai trò: V
 Xác minh rằng tất cả các thay đổi của mô hình (triển khai, cấu hình, ngừng sử dụng) đều tạo ra các bản ghi kiểm toán không thể thay đổi bao gồm dấu thời gian, danh tính tác nhân đã xác thực, loại thay đổi và trạng thái trước/sau.
 #3.2.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các lỗi xác thực sẽ tự động chặn việc triển khai mô hình sau khi có sự phê duyệt ghi đè rõ ràng từ nhân sự được ủy quyền trước với các lý do kinh doanh được tài liệu hóa.

────────────────────────────────────────

### C3.3 Triển khai có kiểm soát & Quay lại

Các triển khai mô hình phải được kiểm soát, giám sát và có khả năng đảo ngược.

 #3.3.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các quy trình triển khai xác thực chữ ký mật mã và tính toán các hàm kiểm tra tính toàn vẹn trước khi kích hoạt mô hình, đồng thời thất bại triển khai nếu có bất kỳ sự không khớp nào.
 #3.3.2    Cấp độ: 1    Vai trò: D
 Xác minh rằng các triển khai sản xuất thực hiện các cơ chế triển khai dần dần (triển khai canary, triển khai xanh-xanh) với các kích hoạt hoàn tác tự động dựa trên các tỷ lệ lỗi đã thỏa thuận trước, ngưỡng độ trễ hoặc các tiêu chí cảnh báo bảo mật.
 #3.3.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng khả năng khôi phục lại trạng thái hoàn chỉnh của mô hình (trọng số, cấu hình, phụ thuộc) được thực hiện một cách nguyên tử.
 #3.3.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng khả năng tắt mô hình khẩn cấp có thể vô hiệu hóa các điểm cuối của mô hình trong phạm vi phản hồi đã được xác định trước.

────────────────────────────────────────

### C3.4 Thực hành phát triển an toàn

Quy trình phát triển và đào tạo mô hình phải tuân theo các biện pháp bảo mật để ngăn ngừa việc bị xâm phạm.

 #3.4.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các môi trường phát triển, kiểm thử và sản xuất mô hình được tách biệt về mặt vật lý hoặc logic. Chúng không dùng chung hạ tầng, có kiểm soát truy cập riêng biệt và lưu trữ dữ liệu độc lập.
 #3.4.2    Cấp độ: 1    Vai trò: D
 Xác minh rằng các tác phẩm phát triển mô hình (siêu tham số, kịch bản đào tạo, tệp cấu hình, mẫu lệnh nhắc, v.v.) được lưu trữ trong hệ thống kiểm soát phiên bản và yêu cầu phê duyệt từ đồng nghiệp trước khi sử dụng trong quá trình đào tạo.
 #3.4.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng việc đào tạo và điều chỉnh mô hình diễn ra trong các môi trường cách ly với quyền truy cập mạng được kiểm soát.
 #3.4.4    Cấp độ: 2    Vai trò: D
 Xác nhận rằng các nguồn dữ liệu đào tạo được xác thực thông qua các kiểm tra tính toàn vẹn và được xác thực qua các nguồn đáng tin cậy với chuỗi quản lý tài liệu trước khi sử dụng trong phát triển mô hình.

────────────────────────────────────────

### Ngừng sử dụng và Triệt phá Mô hình C3.5

Các mô hình phải được ngừng sử dụng một cách an toàn khi chúng không còn cần thiết hoặc khi các vấn đề về bảo mật được xác định.

 #3.5.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các tệp mô hình đã nghỉ hưu được xóa an toàn bằng cách sử dụng xóa mật mã an toàn.
 #3.5.2    Cấp độ: 2    Vai trò: V
 Xác minh rằng các sự kiện nghỉ hưu mô hình được ghi lại với dấu thời gian và nhận dạng người thực hiện, đồng thời chữ ký mô hình bị thu hồi để ngăn tái sử dụng.

────────────────────────────────────────

### Tài liệu tham khảo

MITRE ATLAS
MLOps Principles
Reinforcement fine-tuning
What is AI adversarial robustness? – IBM Research

## Bảo mật Hạ tầng, Cấu hình & Triển khai C4

### Mục tiêu Kiểm soát

Cơ sở hạ tầng AI phải được củng cố chống lại việc leo thang đặc quyền, can thiệp chuỗi cung ứng và di chuyển ngang thông qua cấu hình bảo mật, cô lập khi chạy, các quy trình triển khai đáng tin cậy và giám sát toàn diện. Chỉ các thành phần cơ sở hạ tầng đã được xác thực và ủy quyền mới được đưa vào sản xuất thông qua các quy trình kiểm soát nhằm đảm bảo bảo mật, tính toàn vẹn và khả năng kiểm toán.

Mục tiêu Bảo mật Cốt lõi: Chỉ những thành phần hạ tầng được ký kết mật mã và quét lỗ hổng mới được đưa vào sản xuất thông qua các pipeline xác thực tự động, đảm bảo thực thi các chính sách bảo mật và duy trì các hồ sơ kiểm toán bất biến.

────────────────────────────────────────

### C4.1 Cô lập môi trường chạy thời gian

Ngăn chặn thoát container và leo thang đặc quyền thông qua các nguyên thủy cô lập ở cấp độ hệ điều hành.

 #4.1.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng tất cả các khối lượng công việc AI chạy với quyền tối thiểu cần thiết trên hệ điều hành, ví dụ như loại bỏ các khả năng Linux không cần thiết trong trường hợp sử dụng container.
 #4.1.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các khối lượng công việc được bảo vệ bằng các công nghệ giới hạn khai thác như sandboxing, hồ sơ seccomp, AppArmor, SELinux hoặc tương tự, và cấu hình phù hợp.
 #4.1.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các khối lượng công việc chạy với hệ thống tệp gốc chỉ đọc, và bất kỳ điểm gắn kết có thể ghi đều được định nghĩa rõ ràng và được tăng cường bảo mật với các tùy chọn hạn chế (ví dụ: noexec, nosuid, nodev).
 #4.1.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng giám sát thời gian chạy phát hiện các hành vi leo thang đặc quyền và thoát container và tự động chấm dứt các tiến trình vi phạm.
 #4.1.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các khối lượng công việc AI có rủi ro cao chỉ chạy trong các môi trường cách ly phần cứng (ví dụ: TEEs, trình giám sát đáng tin cậy, hoặc các nút bare-metal) sau khi thực hiện thành công việc xác thực từ xa.

────────────────────────────────────────

### C4.2 Dây chuyền Xây dựng & Triển khai An toàn

Đảm bảo tính toàn vẹn mật mã và an ninh chuỗi cung ứng thông qua việc xây dựng có thể tái tạo và các hiện vật đã được ký.

 #4.2.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các bản build có thể tái tạo và tạo ra siêu dữ liệu nguồn gốc đã được ký phù hợp với các sản phẩm build, để có thể kiểm chứng độc lập.
 #4.2.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các bản dựng tạo ra bảng kê nguyên liệu phần mềm (SBOM) và được ký trước khi được chấp nhận để triển khai.
 #4.2.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng chữ ký của thành phẩm xây dựng (ví dụ: hình ảnh container) và siêu dữ liệu nguồn gốc được xác thực khi triển khai, và các thành phẩm chưa được xác minh sẽ bị từ chối.

────────────────────────────────────────

### C4.3 Bảo mật mạng & Kiểm soát truy cập

Triển khai mạng lưới không tin cậy với các chính sách mặc định từ chối và giao tiếp được mã hóa.

 #4.3.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các chính sách mạng thực thi việc từ chối mặc định đối với lưu lượng vào và ra, chỉ cho phép rõ ràng các dịch vụ cần thiết.
 #4.3.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các giao thức truy cập quản trị (ví dụ: SSH, RDP) và quyền truy cập vào dịch vụ siêu dữ liệu đám mây đều bị giới hạn và yêu cầu xác thực mạnh.
 #4.3.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng lưu lượng đi ra được giới hạn đến các điểm đến được phê duyệt và tất cả các yêu cầu đều được ghi lại.
 #4.3.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng giao tiếp giữa các dịch vụ sử dụng mutual TLS với việc xác thực chứng chỉ và xoay vòng tự động thường xuyên.
 #4.3.5    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các khối lượng công việc AI và môi trường (phát triển, kiểm thử, sản xuất) chạy trong các phân đoạn mạng tách biệt (VPCs/VNets) không có truy cập trực tiếp internet và không chia sẻ vai trò IAM, nhóm bảo mật hoặc kết nối giữa các môi trường.

### C4.4 Quản lý Bí mật & Khóa Mã hóa

Bảo vệ bí mật và khóa mã hóa bằng lưu trữ an toàn, tự động xoay vòng, và kiểm soát truy cập mạnh mẽ.

 #4.4.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các bí mật được lưu trữ trong một hệ thống quản lý bí mật chuyên dụng với mã hóa khi lưu trữ và được tách biệt khỏi các khối lượng công việc ứng dụng.
 #4.4.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các khóa mật mã được tạo và lưu trữ trong các mô-đun có hỗ trợ phần cứng (ví dụ, HSM, KMS đám mây).
 #4.4.3    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng việc truy cập vào các bí mật sản xuất yêu cầu xác thực mạnh.
 #4.4.4    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các bí mật được triển khai đến các ứng dụng tại thời điểm runtime thông qua một hệ thống quản lý bí mật chuyên dụng. Bí mật không được phép nhúng trong mã nguồn, tập tin cấu hình, sản phẩm xây dựng, hình ảnh container, hoặc biến môi trường.
 #4.4.5    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng việc xoay vòng bí mật được tự động hóa.

────────────────────────────────────────

### C4.5 Phân vùng và Xác thực Khối lượng công việc AI

Cô lập các mô hình AI không đáng tin cậy trong các sandbox an toàn và bảo vệ các khối công việc AI nhạy cảm bằng cách sử dụng các môi trường thực thi đáng tin cậy (TEE) và công nghệ điện toán bảo mật.

 #4.5.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các mô hình AI bên ngoài hoặc không đáng tin cậy được thực thi trong các sandbox tách biệt.
 #4.5.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các workload trong sandbox mặc định không có kết nối mạng ra ngoài, với bất kỳ quyền truy cập cần thiết nào được định nghĩa rõ ràng.
 #4.5.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng việc xác nhận khối lượng công việc được thực hiện trước khi tải mô hình hoặc khối lượng công việc, đảm bảo bằng chứng mật mã của môi trường thực thi tin cậy.
 #4.5.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các khối công việc bảo mật được thực thi trong môi trường thực thi tin cậy (TEE) cung cấp sự cô lập được thực thi bằng phần cứng, mã hóa bộ nhớ và bảo vệ tính toàn vẹn.
 #4.5.5    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng các dịch vụ suy luận bảo mật ngăn chặn việc trích xuất mô hình thông qua tính toán được mã hóa với trọng số mô hình đóng kín và thực thi được bảo vệ.
 #4.5.6    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng việc điều phối môi trường thực thi tin cậy bao gồm quản lý vòng đời, xác thực từ xa và các kênh truyền thông được mã hóa.
 #4.5.7    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng tính toán đa bên bảo mật (SMPC) cho phép đào tạo AI hợp tác mà không làm lộ bộ dữ liệu cá nhân hoặc các tham số mô hình.

────────────────────────────────────────

### C4.6 Quản lý Tài nguyên Hạ tầng AI, Sao lưu và Khôi phục

Ngăn chặn các cuộc tấn công làm cạn kiệt tài nguyên và đảm bảo phân bổ tài nguyên công bằng thông qua hạn mức và giám sát. Duy trì khả năng chống chịu của hạ tầng bằng các bản sao lưu an toàn, quy trình khôi phục đã được kiểm tra và khả năng phục hồi sau thảm họa.

 #4.6.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng mức tiêu thụ tài nguyên của workload được giới hạn một cách phù hợp bằng cách sử dụng ví dụ như Kubernetes ResourceQuotas hoặc các phương pháp tương tự để giảm thiểu các cuộc tấn công Từ chối Dịch vụ (Denial of Service).
 #4.6.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng việc cạn kiệt tài nguyên kích hoạt các biện pháp bảo vệ tự động (ví dụ: giới hạn tốc độ hoặc cô lập khối lượng công việc) khi vượt quá các ngưỡng đã định về CPU, bộ nhớ hoặc yêu cầu.
 #4.6.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các hệ thống sao lưu hoạt động trong các mạng riêng biệt với thông tin đăng nhập riêng biệt, và hệ thống lưu trữ được vận hành trong mạng tách biệt hoàn toàn (air-gapped) hoặc triển khai bảo vệ WORM (ghi một lần, đọc nhiều lần) để ngăn chặn việc sửa đổi trái phép.

────────────────────────────────────────

### C4.7 An ninh Phần cứng AI

Bảo mật các thành phần phần cứng chuyên dụng cho AI bao gồm GPU, TPU và các bộ tăng tốc AI chuyên biệt.

 #4.7.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng trước khi thực hiện khối lượng công việc, tính toàn vẹn của bộ tăng tốc AI được kiểm tra bằng các cơ chế xác thực dựa trên phần cứng (ví dụ: TPM, DRTM hoặc tương đương).
 #4.7.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng bộ nhớ của bộ tăng tốc (GPU) được cách ly giữa các khối lượng công việc thông qua các cơ chế phân vùng với việc làm sạch bộ nhớ giữa các công việc.
 #4.7.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các mô-đun bảo mật phần cứng (HSM) bảo vệ trọng số mô hình AI và khóa mật mã với chứng nhận FIPS 140-3 Cấp 3 hoặc Common Criteria EAL4+.
 #4.7.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng firmware bộ tăng tốc (GPU/TPU/NPUs) được gắn cố định phiên bản, ký và xác thực khi khởi động; firmware chưa ký hoặc debug bị chặn.
 #4.7.5    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng VRAM và bộ nhớ trên gói được xóa sạch giữa các công việc/người thuê và chính sách đặt lại thiết bị ngăn chặn hiện tượng dữ liệu còn sót lại giữa các người thuê.
 #4.7.6    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các tính năng phân vùng/cô lập (ví dụ, phân vùng MIG/VM) được thực thi đối với từng người thuê riêng và ngăn chặn truy cập bộ nhớ từ đối tác này sang đối tác khác qua các phân vùng.
 #4.7.7    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các kết nối liên kết bộ tăng tốc (NVLink/PCIe/InfiniBand/RDMA/NCCL) bị giới hạn trong các kiến trúc được phê duyệt và các đầu cuối được xác thực; các liên kết văn bản thuần giữa các người thuê chéo không được phép.
 #4.7.8    Cấp độ: 3    Vai trò: D
 Xác minh rằng dữ liệu telemetri bộ tăng tốc (công suất, nhiệt độ, ECC, bộ đếm hiệu suất) được xuất ra SIEM/OTel và có cảnh báo khi phát hiện các bất thường cho thấy kênh bên hoặc kênh che dấu.

────────────────────────────────────────

### C4.8 An ninh AI Biên và Phân tán

Triển khai AI phân tán an toàn bao gồm điện toán biên, học liên kết, và kiến trúc đa địa điểm.

 #4.8.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các thiết bị AI biên xác thực với hạ tầng trung tâm bằng cách sử dụng TLS tương hỗ.
 #4.8.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các thiết bị đầu cuối thực hiện khởi động an toàn với chữ ký được xác minh và bảo vệ chống hạ cấp để ngăn chặn các cuộc tấn công giảm cấp phần mềm.
 #4.8.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng việc phối hợp AI phân tán sử dụng các cơ chế đồng thuận chịu lỗi Byzantine với việc xác thực người tham gia và phát hiện nút độc hại.
 #4.8.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng giao tiếp từ edge đến cloud hỗ trợ điều tiết băng thông, nén dữ liệu và hoạt động ngoại tuyến an toàn với lưu trữ cục bộ được mã hóa.

────────────────────────────────────────

### Tài liệu tham khảo

NIST Cybersecurity Framework 2.0
CIS Controls v8
Kubernetes Security Best Practices
Cloud Security Alliance: Cloud Controls Matrix
ENISA: Secure Infrastructure Design
ISO 27001:2022 Information Security Management
NIST AI Risk Management Framework

## Kiểm soát truy cập C5 & Định danh cho các thành phần và người dùng AI

### Mục tiêu Kiểm soát

Kiểm soát truy cập hiệu quả cho các hệ thống AI yêu cầu quản lý danh tính vững chắc, ủy quyền dựa trên bối cảnh, và thực thi khi chạy theo các nguyên tắc không tin cậy. Các kiểm soát này đảm bảo rằng con người, dịch vụ và tác nhân tự động chỉ tương tác với các mô hình, dữ liệu và tài nguyên tính toán trong phạm vi đã được cấp phép rõ ràng, với khả năng xác minh và kiểm tra liên tục.

────────────────────────────────────────

### C5.1 Quản lý Danh tính & Xác thực

Thiết lập danh tính được hỗ trợ mật mã cho tất cả các thực thể với xác thực đa yếu tố.

 #5.1.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng tất cả người dùng là con người và các nguyên tắc dịch vụ xác thực thông qua một nhà cung cấp danh tính doanh nghiệp tập trung (IdP) sử dụng các giao thức OIDC và/hoặc SAML.
 #5.1.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các hoạt động có rủi ro cao (triển khai mô hình, xuất trọng số, truy cập dữ liệu đào tạo, thay đổi cấu hình sản xuất) yêu cầu xác thực đa yếu tố hoặc xác thực nâng cao kèm theo tái xác nhận phiên làm việc.
 #5.1.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các tác nhân AI liên kết xác thực thông qua các khẳng định JWT được ký có thời gian sống tối đa là 24 giờ và bao gồm bằng chứng mật mã về nguồn gốc.

────────────────────────────────────────

### C5.2 Ủy quyền & Chính sách

Triển khai kiểm soát truy cập cho tất cả nguồn lực AI với các mô hình phân quyền rõ ràng và nhật ký kiểm tra.

 #5.2.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng mọi tài nguyên AI (bộ dữ liệu, mô hình, điểm cuối, bộ sưu tập vector, chỉ mục nhúng, phiên bản tính toán) đều thực thi kiểm soát truy cập dựa trên vai trò với danh sách cho phép rõ ràng và chính sách mặc định là từ chối.
 #5.2.2    Cấp độ: 1    Vai trò: V
 Xác minh rằng tất cả các sửa đổi kiểm soát truy cập đều được ghi lại vĩnh viễn với dấu thời gian, danh tính người thực hiện, định danh tài nguyên và các thay đổi quyền hạn.
 #5.2.3    Cấp độ: 2    Vai trò: D
 Xác minh rằng nhãn phân loại dữ liệu (PII, PHI, thuộc quyền sở hữu, v.v.) tự động lan truyền đến các tài nguyên dẫn xuất (embedding, bộ nhớ đệm prompt, đầu ra mô hình).
 #5.2.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các cố gắng truy cập trái phép và các sự kiện leo thang quyền hạn kích hoạt cảnh báo thời gian thực kèm theo siêu dữ liệu ngữ cảnh.
 #5.2.5    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các quyết định ủy quyền được tách ra bên ngoài thành một cơ chế chính sách chuyên dụng (OPA, Cedar hoặc tương đương).
 #5.2.6    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các chính sách đánh giá các thuộc tính động tại thời gian chạy bao gồm vai trò hoặc nhóm người dùng, phân loại tài nguyên, ngữ cảnh yêu cầu, cô lập người thuê và các hạn chế về thời gian.
 #5.2.7    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng giá trị thời gian tồn tại trong bộ nhớ đệm chính sách (TTL) không vượt quá 5 phút đối với tài nguyên có độ nhạy cao và 1 giờ đối với tài nguyên tiêu chuẩn có khả năng hủy bộ nhớ đệm.

────────────────────────────────────────

### C5.3 Thực thi Bảo mật vào Thời gian Truy vấn

Thực hiện các biện pháp kiểm soát bảo mật tầng cơ sở dữ liệu với lọc bắt buộc và chính sách bảo mật cấp hàng.

 #5.3.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng tất cả các truy vấn cơ sở dữ liệu vector và SQL bao gồm các bộ lọc bảo mật bắt buộc (ID người thuê, nhãn độ nhạy, phạm vi người dùng) được thực thi ở cấp động cơ cơ sở dữ liệu.
 #5.3.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các chính sách bảo mật cấp dòng và che mặt trường được bật với kế thừa chính sách cho tất cả cơ sở dữ liệu vector, chỉ mục tìm kiếm và bộ dữ liệu huấn luyện.
 #5.3.3    Cấp độ: 2    Vai trò: D
 Xác minh rằng các đánh giá ủy quyền không thành công sẽ ngay lập tức hủy bỏ các truy vấn và trả về mã lỗi ủy quyền rõ ràng.
 #5.3.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các cơ chế thử lại truy vấn đánh giá lại các chính sách ủy quyền để tính đến các thay đổi quyền động trong các phiên người dùng đang hoạt động.

────────────────────────────────────────

### C5.4 Lọc Đầu Ra & Ngăn Ngừa Mất Dữ Liệu

Triển khai các biện pháp kiểm soát hậu xử lý để ngăn chặn việc tiết lộ dữ liệu trái phép trong nội dung do AI tạo ra.

 #5.4.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các cơ chế lọc sau suy luận quét và chỉnh sửa các thông tin nhận dạng cá nhân (PII), thông tin phân loại và dữ liệu sở hữu không được phép trước khi chuyển nội dung đến người yêu cầu.
 #5.4.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các trích dẫn, tài liệu tham khảo và nguồn gốc trong kết quả mô hình được kiểm tra dựa trên quyền truy cập của người gọi và loại bỏ nếu phát hiện truy cập không được phép.
 #5.4.3    Cấp độ: 2    Vai trò: D
 Xác minh rằng các hạn chế định dạng đầu ra (PDF đã được làm sạch, hình ảnh đã được loại bỏ siêu dữ liệu, loại tệp được phê duyệt) được thực thi dựa trên cấp độ quyền người dùng và phân loại dữ liệu.

────────────────────────────────────────

### C5.5 Cách ly đa thuê bao

Đảm bảo sự cô lập về mật mã và logic giữa các khách thuê trong hạ tầng AI dùng chung.

 #5.5.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các không gian bộ nhớ, kho nhúng, mục lưu trong bộ nhớ đệm và tệp tạm thời được phân tách theo không gian tên cho từng khách thuê với việc xóa sạch an toàn khi xóa khách thuê hoặc kết thúc phiên.
 #5.5.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng mỗi yêu cầu API bao gồm một định danh thuê bao đã được xác thực và được xác minh bằng mật mã dựa trên ngữ cảnh phiên và quyền hạn của người dùng.
 #5.5.3    Cấp độ: 2    Vai trò: D
 Xác minh rằng các chính sách mạng thực thi các quy tắc từ chối mặc định đối với giao tiếp giữa các tenant trong các service mesh và nền tảng điều phối container.
 #5.5.4    Cấp độ: 3    Vai trò: D
 Xác minh rằng các khóa mã hóa là duy nhất cho từng thuê bao với hỗ trợ khóa do khách hàng quản lý (CMK) và sự cô lập mật mã giữa các kho dữ liệu của thuê bao.

────────────────────────────────────────

### C5.6 Ủy quyền Đại lý Tự động

Kiểm soát quyền hạn cho các đại lý AI và hệ thống tự động thông qua token khả năng theo phạm vi và ủy quyền liên tục.

 #5.6.1    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng các tác nhân tự động nhận được token khả năng có phạm vi, trong đó liệt kê rõ ràng các hành động được phép thực hiện, các tài nguyên có thể truy cập, giới hạn thời gian và các ràng buộc hoạt động.
 #5.6.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các khả năng rủi ro cao (truy cập hệ thống tệp, thực thi mã, gọi API bên ngoài, giao dịch tài chính) bị vô hiệu hóa theo mặc định và cần có sự cho phép rõ ràng.
 #5.6.3    Cấp độ: 2    Vai trò: D
 Xác minh rằng các token khả năng được liên kết với phiên người dùng, bao gồm bảo vệ tính toàn vẹn bằng mật mã, và đảm bảo rằng chúng không thể được lưu trữ hoặc sử dụng lại trong các tình huống ngoại tuyến.
 #5.6.4    Cấp độ: 2    Vai trò: V
 Xác minh rằng các hành động do tác nhân khởi tạo được trải qua việc ủy quyền thông qua bộ máy chính sách ABAC.

────────────────────────────────────────

### Tài liệu tham khảo

NIST SP 800-162: Guide to Attribute Based Access Control (ABAC)
NIST SP 800-207: Zero Trust Architecture
NIST SP 800-63-3: Digital Identity Guidelines
NIST IR 8360: Machine Learning for Access Control Policy Verification

## An ninh Chuỗi Cung ứng C6 cho Mô hình, Khung công tác & Dữ liệu

### Mục tiêu Kiểm soát

Các cuộc tấn công chuỗi cung ứng AI lợi dụng các mô hình, khung làm việc hoặc bộ dữ liệu bên thứ ba để chèn cửa hậu, thiên vị hoặc mã có thể bị khai thác. Các biện pháp kiểm soát này cung cấp nguồn gốc từ đầu đến cuối, quản lý lỗ hổng và giám sát để bảo vệ toàn bộ vòng đời của mô hình.

────────────────────────────────────────

### C6.1 Kiểm tra mô hình học trước và nguồn gốc

Đánh giá và xác thực nguồn gốc, giấy phép và hành vi ẩn của mô hình bên thứ ba trước bất kỳ quá trình tinh chỉnh hoặc triển khai nào.

 #6.1.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng mọi sản phẩm mô hình bên thứ ba đều bao gồm một bản ghi xuất xứ có chữ ký xác nhận kho lưu trữ nguồn và mã băm cam kết.
 #6.1.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các mô hình được quét để phát hiện các lớp độc hại hoặc kích hoạt Trojan bằng công cụ tự động trước khi nhập.
 #6.1.3    Cấp độ: 2    Vai trò: D
 Xác minh rằng việc tinh chỉnh học chuyển giao vượt qua đánh giá đối kháng để phát hiện các hành vi ẩn.
 #6.1.4    Cấp độ: 2    Vai trò: V
 Xác minh rằng giấy phép mô hình, thẻ kiểm soát xuất khẩu và tuyên bố nguồn gốc dữ liệu được ghi lại trong mục ML‑BOM.
 #6.1.5    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng các mô hình có rủi ro cao (trọng số được tải lên công khai, người tạo chưa được xác minh) vẫn được cách ly cho đến khi được con người xem xét và phê duyệt.

────────────────────────────────────────

### C6.2 Quét Khung và Thư viện

Liên tục quét các framework và thư viện ML để phát hiện CVE và mã độc nhằm giữ cho ngăn xếp runtime an toàn.

 #6.2.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các pipeline CI thực thi trình quét phụ thuộc trên các framework AI và thư viện quan trọng.
 #6.2.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các lỗ hổng nghiêm trọng (CVSS ≥ 7.0) chặn việc thăng cấp lên các ảnh sản xuất.
 #6.2.3    Cấp độ: 2    Vai trò: D
 Xác nhận rằng phân tích mã tĩnh chạy trên các thư viện ML được phân nhánh hoặc cung cấp dưới dạng bản sao bên ngoài.
 #6.2.4    Cấp độ: 2    Vai trò: V
 Xác minh rằng các đề xuất nâng cấp framework bao gồm đánh giá tác động bảo mật có tham chiếu đến nguồn dữ liệu CVE công khai.
 #6.2.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng các cảm biến thời gian chạy cảnh báo về việc tải thư viện động bất thường khi không tuân theo SBOM đã ký.

────────────────────────────────────────

### C6.3 Ghim và Xác minh Phụ thuộc

Ghim mọi phụ thuộc vào các bản tổng hợp không thể thay đổi và tái tạo các bản dựng để đảm bảo các tác phẩm là giống hệt và không bị giả mạo.

 #6.3.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng tất cả các trình quản lý gói đều thi hành việc khoá phiên bản thông qua các file khóa.
 #6.3.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các digest bất biến được sử dụng thay vì các tag có thể thay đổi trong các tham chiếu container.
 #6.3.3    Cấp độ: 2    Vai trò: D
 Xác minh rằng các kiểm tra xây dựng có thể tái tạo so sánh các giá trị băm trong các lần chạy CI để đảm bảo đầu ra giống hệt nhau.
 #6.3.4    Cấp độ: 2    Vai trò: V
 Xác minh rằng các bản khai nhận xây dựng được lưu trữ trong 18 tháng để phục vụ việc theo dõi kiểm toán.
 #6.3.5    Cấp độ: 3    Vai trò: D
 Xác minh rằng các thư viện phụ thuộc hết hạn sẽ kích hoạt các PR tự động để cập nhật hoặc nhân bản các phiên bản đã được cố định.

────────────────────────────────────────

### C6.4 Thực thi Nguồn Tin cậy

Chỉ cho phép tải xuống các hiện vật từ các nguồn được tổ chức phê duyệt và xác minh mật mã, và chặn tất cả các nguồn khác.

 #6.4.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng trọng số mô hình, bộ dữ liệu và container chỉ được tải xuống từ các miền được phê duyệt hoặc các kho nội bộ.
 #6.4.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các chữ ký Sigstore/Cosign xác thực danh tính nhà phát hành trước khi các hiện vật được lưu vào bộ nhớ đệm cục bộ.
 #6.4.3    Cấp độ: 2    Vai trò: D
 Xác minh rằng các proxy egress chặn việc tải xuống artifact không xác thực để thực thi chính sách nguồn tin cậy.
 #6.4.4    Cấp độ: 2    Vai trò: V
 Xác minh rằng danh sách cho phép của kho lưu trữ được xem xét hàng quý kèm theo bằng chứng về lý do kinh doanh cho mỗi mục.
 #6.4.5    Cấp độ: 3    Vai trò: V
 Xác nhận rằng các vi phạm chính sách kích hoạt việc cách ly các artifact và hoàn nguyên các lần chạy pipeline phụ thuộc.

────────────────────────────────────────

### C6.5 Đánh giá Rủi ro Bộ dữ liệu Bên thứ ba

Đánh giá các bộ dữ liệu bên ngoài về việc đầu độc, thiên vị và tuân thủ pháp lý, đồng thời theo dõi chúng trong suốt vòng đời của chúng.

 #6.5.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các bộ dữ liệu bên ngoài phải trải qua đánh giá rủi ro nhiễm độc (ví dụ: định danh dữ liệu, phát hiện điểm ngoại lai).
 #6.5.2    Cấp độ: 1    Vai trò: D
 Xác minh rằng các chỉ số sai lệch (cân bằng nhân khẩu học, cơ hội bình đẳng) được tính toán trước khi phê duyệt bộ dữ liệu.
 #6.5.3    Cấp độ: 2    Vai trò: V
 Xác minh rằng nguồn gốc và các điều khoản cấp phép cho bộ dữ liệu được ghi lại trong các mục ML‑BOM.
 #6.5.4    Cấp độ: 2    Vai trò: V
 Xác minh rằng việc giám sát định kỳ phát hiện sự dịch chuyển hoặc hỏng hóc trong các bộ dữ liệu được lưu trữ.
 #6.5.5    Cấp độ: 3    Vai trò: D
 Xác minh rằng nội dung bị cấm (bản quyền, thông tin cá nhân nhạy cảm) đã được loại bỏ thông qua việc làm sạch tự động trước khi đào tạo.

────────────────────────────────────────

### C6.6 Giám sát Tấn công Chuỗi Cung ứng

Phát hiện sớm các mối đe dọa chuỗi cung ứng thông qua nguồn cấp CVE, phân tích nhật ký kiểm toán và mô phỏng nhóm tấn công.

 #6.6.1    Cấp độ: 1    Vai trò: V
 Xác minh rằng các nhật ký kiểm toán CI/CD được truyền đến SIEM để phát hiện các hành vi bất thường trong việc lấy gói hoặc các bước xây dựng bị can thiệp.
 #6.6.2    Cấp độ: 2    Vai trò: D
 Xác minh rằng các kịch bản ứng phó sự cố bao gồm các thủ tục khôi phục cho các mô hình hoặc thư viện bị xâm phạm.
 #6.6.3    Cấp độ: 3    Vai trò: V
 Xác minh rằng việc làm giàu thông tin tình báo mối đe dọa gắn thẻ các chỉ báo đặc thù cho ML (ví dụ: các IoC tấn công đầu độc mô hình) trong quá trình phân loại cảnh báo.

────────────────────────────────────────

### C6.7 ML‑BOM cho Các Tác phẩm Mô hình

Tạo và ký các SBOM chi tiết dành riêng cho ML (ML-BOM) để người tiêu dùng ở hạ nguồn có thể xác minh tính toàn vẹn của các thành phần khi triển khai.

 #6.7.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng mỗi hiện vật mô hình đều xuất bản một ML-BOM liệt kê các bộ dữ liệu, trọng số, siêu tham số và giấy phép.
 #6.7.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng việc tạo ML‑BOM và ký Cosign được tự động hóa trong CI và là yêu cầu bắt buộc để hợp nhất.
 #6.7.3    Cấp độ: 2    Vai trò: D
 Xác minh rằng các kiểm tra độ hoàn chỉnh của ML‑BOM sẽ làm cho việc xây dựng thất bại nếu bất kỳ siêu dữ liệu thành phần nào (hash, giấy phép) bị thiếu.
 #6.7.4    Cấp độ: 2    Vai trò: V
 Xác minh rằng người tiêu dùng hạ nguồn có thể truy vấn ML-BOMs thông qua API để xác thực các mô hình đã nhập khi triển khai.
 #6.7.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng các ML‑BOM được kiểm soát phiên bản và so sánh để phát hiện các sửa đổi trái phép.

────────────────────────────────────────

### Tài liệu tham khảo

OWASP LLM03:2025 Supply Chain
MITRE ATLAS : Supply Chain Compromise
SBOM Overview – CISA
CycloneDX – Machine Learning Bill of Materials

## Hành vi mô hình C7, Kiểm soát đầu ra và Đảm bảo an toàn

### Mục tiêu Kiểm soát

Các kết quả mô hình phải được cấu trúc, đáng tin cậy, an toàn, có thể giải thích và liên tục được giám sát trong môi trường sản xuất. Thực hiện như vậy sẽ giảm thiểu các hiện tượng ảo tưởng, rò rỉ thông tin riêng tư, nội dung gây hại và các hành động không kiểm soát được, đồng thời tăng cường sự tin tưởng của người dùng và tuân thủ quy định.

────────────────────────────────────────

### C7.1 Thực thi Định dạng Đầu ra

Các sơ đồ nghiêm ngặt, giải mã có giới hạn và xác thực hạ nguồn ngăn chặn nội dung bị biến dạng hoặc độc hại trước khi nó lan truyền.

 #7.1.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các sơ đồ phản hồi (ví dụ: JSON Schema) được cung cấp trong lời nhắc hệ thống và mọi đầu ra đều được tự động xác thực; các đầu ra không phù hợp sẽ kích hoạt sửa chữa hoặc từ chối.
 #7.1.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng việc giải mã có giới hạn (token dừng, regex, max-tokens) đã được bật để ngăn ngừa tình trạng tràn bộ đệm hoặc các kênh bên ngoài tấn công qua prompt.
 #7.1.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các thành phần hạ nguồn coi đầu ra là không đáng tin cậy và xác thực chúng theo các lược đồ hoặc trình giải tuần tự hóa an toàn chống chèn.
 #7.1.4    Cấp độ: 3    Vai trò: V
 Xác minh rằng các sự kiện lỗi đầu ra không đúng được ghi lại, giới hạn tốc độ và hiển thị lên hệ thống giám sát.

────────────────────────────────────────

### C7.2 Phát hiện và Giảm thiểu Ảo tưởng

Ước lượng sự không chắc chắn và các chiến lược dự phòng ngăn chặn các câu trả lời bịa đặt.

 #7.2.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng xác suất log cấp token, tính nhất quán tự nhóm, hoặc bộ phát hiện ảo hóa được tinh chỉnh đều gán điểm độ tin cậy cho từng câu trả lời.
 #7.2.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các phản hồi dưới ngưỡng độ chắc chắn có thể cấu hình kích hoạt các quy trình thay thế (ví dụ: tạo sinh tăng cường truy xuất, mô hình phụ, hoặc xem xét bởi con người).
 #7.2.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các sự cố ảo giác được gắn thẻ bằng siêu dữ liệu nguyên nhân gốc rễ và được đưa vào quy trình phân tích sau sự cố và tinh chỉnh.
 #7.2.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các ngưỡng và bộ dò được hiệu chỉnh lại sau các cập nhật lớn về mô hình hoặc cơ sở tri thức.
 #7.2.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng các biểu đồ điều khiển theo dõi tỷ lệ ảo tưởng.

────────────────────────────────────────

### C7.3 Lọc An toàn & Bảo mật Đầu ra

Các bộ lọc chính sách và phạm vi bảo vệ của nhóm kiểm tra đỏ bảo vệ người dùng và dữ liệu bảo mật.

 #7.3.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các bộ phân loại trước và sau khi tạo nội dung chặn các nội dung về thù hận, quấy rối, tự làm hại, cực đoan và nội dung khiêu dâm phù hợp với chính sách.
 #7.3.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng việc phát hiện PII/PCI và tự động ẩn thông tin được thực hiện trên mọi phản hồi; các vi phạm sẽ gây ra sự cố về quyền riêng tư.
 #7.3.3    Cấp độ: 2    Vai trò: D
 Xác minh rằng các thẻ bảo mật (ví dụ, bí mật thương mại) được truyền qua các phương thức để ngăn ngừa rò rỉ trong văn bản, hình ảnh hoặc mã.
 #7.3.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các cố gắng vượt qua bộ lọc hoặc phân loại có rủi ro cao yêu cầu phê duyệt phụ hoặc xác thực lại người dùng.
 #7.3.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng ngưỡng lọc phản ánh đúng khu vực pháp lý và ngữ cảnh về độ tuổi/vai trò của người dùng.

────────────────────────────────────────

### C7.4 Giới hạn Đầu ra & Hành động

Giới hạn tốc độ và cổng phê duyệt ngăn chặn lạm dụng và tự động hóa quá mức.

 #7.4.1    Cấp độ: 1    Vai trò: D
 Xác minh rằng hạn mức mỗi người dùng và mỗi khóa API giới hạn yêu cầu, token và chi phí với cơ chế lùi lại theo cấp số nhân khi gặp lỗi 429.
 #7.4.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các hành động đặc quyền (ghi file, thực thi mã, gọi mạng) yêu cầu phê duyệt dựa trên chính sách hoặc có người kiểm soát.
 #7.4.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các kiểm tra nhất quán đa phương thức đảm bảo hình ảnh, mã và văn bản được tạo ra cho cùng một yêu cầu không thể bị sử dụng để giấu nội dung độc hại.
 #7.4.4    Cấp độ: 2    Vai trò: D
 Xác minh rằng độ sâu đại diện của đại lý, giới hạn đệ quy và danh sách công cụ được phép được cấu hình rõ ràng.
 #7.4.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng việc vi phạm giới hạn phát ra các sự kiện bảo mật có cấu trúc để nhập vào SIEM.

────────────────────────────────────────

### C7.5 Giải thích khả năng xuất đầu ra

Tín hiệu minh bạch cải thiện sự tin tưởng của người dùng và việc gỡ lỗi nội bộ.

 #7.5.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các điểm số độ tin cậy hướng đến người dùng hoặc tóm tắt lý do ngắn gọn được hiển thị khi đánh giá rủi ro cho là phù hợp.
 #7.5.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các giải thích được tạo ra không tiết lộ các lời nhắc hệ thống nhạy cảm hoặc dữ liệu sở hữu độc quyền.
 #7.5.3    Cấp độ: 3    Vai trò: D
 Xác minh rằng hệ thống ghi lại xác suất log cấp token hoặc bản đồ chú ý và lưu trữ chúng để kiểm tra có phép.
 #7.5.4    Cấp độ: 3    Vai trò: V
 Xác minh rằng các hiện vật giải thích được quản lý phiên bản cùng với các bản phát hành mô hình để đảm bảo khả năng kiểm toán.

────────────────────────────────────────

### C7.6 Tích hợp giám sát

Khả năng quan sát thời gian thực khép kín vòng lặp giữa phát triển và sản xuất.

 #7.6.1    Cấp độ: 1    Vai trò: D
 Xác minh rằng các chỉ số (vi phạm lược đồ, tỉ lệ ảo tưởng, độ độc hại, rò rỉ PII, độ trễ, chi phí) được truyền đến một nền tảng giám sát trung tâm.
 #7.6.2    Cấp độ: 1    Vai trò: V
 Xác minh rằng các ngưỡng cảnh báo được định nghĩa cho từng chỉ số an toàn, kèm theo các đường dẫn leo thang trực tiếp khi cần.
 #7.6.3    Cấp độ: 2    Vai trò: V
 Xác minh rằng các bảng điều khiển liên kết các bất thường đầu ra với mô hình/phiên bản, cờ tính năng và các thay đổi dữ liệu thượng nguồn.
 #7.6.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng dữ liệu giám sát được phản hồi lại vào việc đào tạo lại, tinh chỉnh hoặc cập nhật quy tắc trong quy trình làm việc MLOps đã được ghi chép.
 #7.6.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng các pipeline giám sát đã được kiểm tra xâm nhập và kiểm soát truy cập để tránh rò rỉ các bản ghi nhạy cảm.

────────────────────────────────────────

### 7.7 Các Biện Pháp An Toàn cho Nội Dung Tạo Sinh

Đảm bảo rằng các hệ thống AI không tạo ra nội dung truyền thông bất hợp pháp, có hại hoặc không được phép bằng cách thực thi các ràng buộc chính sách, xác thực đầu ra và khả năng truy xuất.

 #7.7.1    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng các lời nhắc hệ thống và hướng dẫn người dùng rõ ràng cấm việc tạo ra các phương tiện deepfake bất hợp pháp, có hại hoặc không có sự đồng thuận (ví dụ: hình ảnh, video, âm thanh).
 #7.7.2    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng các lời nhắc được lọc để ngăn chặn các cố gắng tạo ra các bản giả mạo, các nội dung khiêu dâm sâu, hoặc các phương tiện truyền thông mô tả những cá nhân thực mà không có sự đồng ý.
 #7.7.3    Cấp độ: 2    Vai trò: V
 Xác minh rằng hệ thống sử dụng băm nhận thức, phát hiện watermark, hoặc dấu vân tay để ngăn chặn việc tái sản xuất trái phép các phương tiện có bản quyền.
 #7.7.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng tất cả phương tiện được tạo ra đều được ký mật mã, đóng dấu bản quyền hoặc nhúng với siêu dữ liệu nguồn gốc chống giả mạo để có thể truy xuất nguồn gốc khi xử lý tiếp theo.
 #7.7.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng các cố gắng vượt qua (ví dụ: che giấu prompt, ngôn ngữ lóng, cách diễn đạt mang tính đối kháng) được phát hiện, ghi lại và giới hạn tần suất; những hành vi lạm dụng lặp lại được báo cáo lên hệ thống giám sát.

### Tài liệu tham khảo

NIST AI Risk Management Framework
ISO/IEC 42001:2023 – AI Management System
OWASP Top-10 for Large Language Model Applications (2025)
Practical Techniques to Constrain LLM Output
Dataiku – Structured Text Generation Guide
VL-Uncertainty: Detecting Hallucinations
HaDeMiF: Hallucination Detection & Mitigation
Building Confidence in LLM Outputs
Explainable AI & LLMs
Sensitive Information Disclosure in LLMs
OpenAI Rate-Limit & Exponential Back-off
Arize AI – LLM Observability Platform

## Bộ nhớ C8, Chèn nhúng & Bảo mật cơ sở dữ liệu véc-tơ

### Mục tiêu Kiểm soát

Embedding và kho vector hoạt động như "bộ nhớ sống" của các hệ thống AI hiện đại, liên tục tiếp nhận dữ liệu do người dùng cung cấp và phản hồi nó vào các ngữ cảnh mô hình thông qua Retrieval-Augmented Generation (RAG). Nếu không được quản lý, bộ nhớ này có thể làm rò rỉ thông tin cá nhân (PII), vi phạm sự đồng ý, hoặc bị đảo ngược để tái tạo lại văn bản gốc. Mục tiêu của nhóm kiểm soát này là củng cố các đường dẫn bộ nhớ và cơ sở dữ liệu vector sao cho quyền truy cập được giới hạn tối thiểu, embedding giữ được sự riêng tư, các vector lưu trữ có thể hết hạn hoặc bị thu hồi theo yêu cầu, và bộ nhớ theo người dùng không bao giờ làm ảnh hưởng đến các lệnh nhắc hoặc kết quả của người dùng khác.

────────────────────────────────────────

### C8.1 Kiểm soát truy cập trên bộ nhớ & chỉ số RAG

Áp dụng các biện pháp kiểm soát truy cập chi tiết cho mọi bộ sưu tập vectơ.

 #8.1.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các quy tắc kiểm soát truy cập cấp hàng/namespace giới hạn các thao tác chèn, xóa và truy vấn theo từng tenant, bộ sưu tập hoặc thẻ tài liệu.
 #8.1.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các khóa API hoặc JWT mang các quyền truy cập có phạm vi (ví dụ: ID bộ sưu tập, động từ hành động) và được thay đổi ít nhất mỗi quý.
 #8.1.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các nỗ lực leo thang đặc quyền (ví dụ: truy vấn tương đồng chéo namespace) được phát hiện và ghi nhật ký vào SIEM trong vòng 5 phút.
 #8.1.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng cơ sở dữ liệu vector ghi lại nhật ký các mục sau: định danh chủ thể, thao tác, ID vector/không gian tên, ngưỡng tương đồng, và số lượng kết quả.
 #8.1.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng các quyết định truy cập được kiểm tra lỗi vượt qua mỗi khi các engine được nâng cấp hoặc quy tắc phân mảnh chỉ mục thay đổi.

────────────────────────────────────────

### C8.2 Sàng lọc và Xác thực Nhúng

Tiền xử lý văn bản để loại bỏ thông tin nhận dạng cá nhân (PII), che giấu hoặc thay thế bằng bí danh trước khi chuyển đổi thành vector, và tùy chọn xử lý hậu kỳ embeddings để loại bỏ các tín hiệu còn sót lại.

 #8.2.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng dữ liệu PII và dữ liệu được quy định được phát hiện thông qua bộ phân loại tự động và được che mặt, mã token hoặc loại bỏ trước khi nhúng.
 #8.2.2    Cấp độ: 1    Vai trò: D
 Xác minh rằng các quy trình nhúng từ chối hoặc cách ly các đầu vào chứa mã thực thi hoặc các ký tự không phải UTF-8 có thể làm nhiễm độc chỉ mục.
 #8.2.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng việc xử lý làm sạch bảo mật vi phân cục bộ hoặc bảo mật vi phân metric được áp dụng cho các biểu diễn câu mà khoảng cách đến bất kỳ token PII (Thông tin nhận dạng cá nhân) đã biết nào thấp hơn một ngưỡng có thể cấu hình.
 #8.2.4    Cấp độ: 2    Vai trò: V
 Xác minh rằng hiệu quả làm sạch dữ liệu (ví dụ, độ nhạy trong việc ẩn thông tin cá nhân nhận dạng được - PII, sự sai lệch ngữ nghĩa) được kiểm tra ít nhất hai lần một năm dựa trên các bộ dữ liệu chuẩn.
 #8.2.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các cấu hình xử lý dữ liệu đầu vào được kiểm soát phiên bản và mọi thay đổi đều được đồng nghiệp xem xét.

────────────────────────────────────────

### C8.3 Hết hạn bộ nhớ, Thu hồi & Xóa dữ liệu

Quyền "được quên" theo GDPR và các luật tương tự yêu cầu việc xóa bỏ kịp thời; do đó, kho vectơ phải hỗ trợ TTL, xóa cứng và ghi dấu "tomb-stoning" để các vectơ bị thu hồi không thể được khôi phục hoặc lập chỉ mục lại.

 #8.3.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng mỗi vector và bản ghi siêu dữ liệu đều có TTL hoặc nhãn giữ liệu rõ ràng được tôn trọng bởi các công việc dọn dẹp tự động.
 #8.3.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các yêu cầu xóa do người dùng khởi xướng sẽ xóa hoàn toàn các vector, siêu dữ liệu, bản sao bộ nhớ đệm và các chỉ mục phái sinh trong vòng 30 ngày.
 #8.3.3    Cấp độ: 2    Vai trò: D
 Xác minh rằng việc xóa logic được theo sau bởi việc phá hủy dữ liệu mã hóa các khối lưu trữ nếu phần cứng hỗ trợ, hoặc bằng cách hủy khóa trong kho khóa.
 #8.3.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các vector hết hạn được loại trừ khỏi kết quả tìm kiếm láng giềng gần nhất trong vòng < 500 ms sau khi hết hạn.

────────────────────────────────────────

### C8.4 Ngăn ngừa Đảo ngược và Rò rỉ Embedding

Các biện pháp phòng thủ gần đây—chồng nhiễu, mạng chiếu, làm nhiễu neuron bảo mật và mã hóa tầng ứng dụng—có thể giảm tỷ lệ đảo ngược ở cấp token xuống dưới 5%.

 #8.4.1    Cấp độ: 1    Vai trò: V
 Xác minh rằng một mô hình mối đe dọa chính thức bao gồm các cuộc tấn công đảo ngược, thành viên và suy luận thuộc tính tồn tại và được xem xét hàng năm.
 #8.4.2    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng mã hóa tầng ứng dụng hoặc mã hóa có thể tìm kiếm bảo vệ các vector khỏi việc bị đọc trực tiếp bởi quản trị viên hạ tầng hoặc nhân viên đám mây.
 #8.4.3    Cấp độ: 3    Vai trò: V
 Xác minh rằng các tham số phòng thủ (ε cho DP, nhiễu σ, hạng chiếu k) cân bằng giữa quyền riêng tư ≥ 99% bảo vệ token và tiện ích ≤ 3% mất độ chính xác.
 #8.4.4    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng các chỉ số kháng đảo chiều là một phần của các cửa kiểm soát phát hành cho các bản cập nhật mô hình, với các ngân sách hồi quy được xác định.

────────────────────────────────────────

### C8.5 Thực thi phạm vi cho bộ nhớ dành cho người dùng cụ thể

Rò rỉ giữa các khách thuê vẫn là rủi ro hàng đầu của RAG: các truy vấn tương đồng được lọc không đúng cách có thể làm lộ tài liệu riêng tư của khách hàng khác.

 #8.5.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng mọi truy vấn truy xuất đều được lọc sau bởi ID thuê bao/người dùng trước khi được chuyển đến lệnh nhắc của LLM.
 #8.5.2    Cấp độ: 1    Vai trò: D
 Xác minh rằng tên bộ sưu tập hoặc ID có phạm vi tên được muối theo từng người dùng hoặc thuê bao để các vector không thể trùng nhau giữa các phạm vi.
 #8.5.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các kết quả tương đồng vượt quá ngưỡng khoảng cách có thể cấu hình nhưng nằm ngoài phạm vi của người gọi sẽ bị loại bỏ và kích hoạt cảnh báo bảo mật.
 #8.5.4    Cấp độ: 2    Vai trò: V
 Xác minh rằng các bài kiểm tra căng thẳng đa thuê simulates các truy vấn đối nghịch cố gắng truy xuất tài liệu ngoài phạm vi và chứng minh không rò rỉ dữ liệu.
 #8.5.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các khóa mã hóa được phân tách theo từng người thuê, đảm bảo sự cô lập mật mã ngay cả khi lưu trữ vật lý được chia sẻ.

────────────────────────────────────────

### C8.6 Bảo mật Hệ thống Bộ nhớ Nâng cao

Các biện pháp kiểm soát bảo mật cho các kiến trúc bộ nhớ phức tạp bao gồm bộ nhớ theo tập sự kiện (episodic), bộ nhớ ngữ nghĩa (semantic) và bộ nhớ làm việc (working memory) với các yêu cầu cụ thể về phân lập và xác thực.

 #8.6.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các loại bộ nhớ khác nhau (bộ nhớ theo tập, bộ nhớ ngữ nghĩa, bộ nhớ làm việc) có các ngữ cảnh bảo mật tách biệt với kiểm soát truy cập dựa trên vai trò, khóa mã hóa riêng biệt và các mẫu truy cập được tài liệu hóa cho từng loại bộ nhớ.
 #8.6.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các quy trình củng cố bộ nhớ bao gồm xác thực bảo mật để ngăn chặn việc chèn các ký ức độc hại thông qua việc làm sạch nội dung, xác minh nguồn và kiểm tra tính toàn vẹn trước khi lưu trữ.
 #8.6.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các truy vấn truy xuất bộ nhớ được xác thực và làm sạch để ngăn chặn việc trích xuất thông tin không được phép thông qua phân tích mẫu truy vấn, thực thi kiểm soát truy cập và lọc kết quả.
 #8.6.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các cơ chế quên bộ nhớ xoá bỏ thông tin nhạy cảm một cách an toàn với các đảm bảo xoá dữ liệu mật mã bằng cách xóa khóa, ghi đè nhiều lần hoặc xoá an toàn dựa trên phần cứng kèm theo chứng nhận xác minh.
 #8.6.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng tính toàn vẹn của hệ thống bộ nhớ được giám sát liên tục để phát hiện các thay đổi trái phép hoặc hỏng hóc thông qua các tổng kiểm tra (checksum), nhật ký kiểm tra (audit logs) và cảnh báo tự động khi nội dung bộ nhớ thay đổi ngoài phạm vi hoạt động bình thường.

────────────────────────────────────────

### Tài liệu tham khảo

Vector database security: Pinecone – IronCore Labs
Securing the Backbone of AI: Safeguarding Vector Databases and Embeddings – Privacera
Enhancing Data Security with RBAC of Qdrant Vector Database – AI Advances
Mitigating Privacy Risks in LLM Embeddings from Embedding Inversion – arXiv
DPPN: Detecting and Perturbing Privacy-Sensitive Neurons – OpenReview
Art. 17 GDPR – Right to Erasure
Sensitive Data in Text Embeddings Is Recoverable – Tonic.ai
PII Identification and Removal – NVIDIA NeMo Docs
De-identifying Sensitive Data – Google Cloud DLP
Remove PII from Conversations Using Sensitive Information Filters – AWS Bedrock Guardrails
Think Your RAG Is Secure? Think Again – Medium
Design a Secure Multitenant RAG Inferencing Solution – Microsoft Learn
Best Practices for Multi-Tenancy RAG with Milvus – Milvus Blog

## 9 Điều phối tự động và An ninh Hành động Tác nhân

### Mục tiêu Kiểm soát

Đảm bảo rằng các hệ thống AI tự động hoặc đa tác nhân chỉ có thể thực hiện các hành động được xác định rõ ràng, được xác thực, có thể kiểm tra và nằm trong giới hạn chi phí và rủi ro cho phép. Điều này giúp bảo vệ chống lại các mối đe dọa như Xâm phạm Hệ thống Tự động, Sử dụng Sai Công cụ, Phát hiện Vòng lặp Tác nhân, Chiếm quyền Giao tiếp, Giả mạo Danh tính, Điều khiển Đám đông và Điều khiển Ý định.

────────────────────────────────────────

### 9.1 Ngân sách Lập kế hoạch Nhiệm vụ Đại lý & Đệ quy

Giảm tốc độ các kế hoạch đệ quy và bắt buộc điểm kiểm tra con người cho các hành động đặc quyền.

 #9.1.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng độ sâu đệ quy tối đa, độ rộng, thời gian đồng hồ thực, số lượng token và chi phí tiền tệ cho mỗi lần thực thi tác tử được cấu hình tập trung và kiểm soát phiên bản.
 #9.1.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các hành động đặc quyền hoặc không thể đảo ngược (ví dụ: cam kết mã, chuyển tiền tài chính) yêu cầu sự phê duyệt rõ ràng của con người thông qua một kênh có thể kiểm toán trước khi thực hiện.
 #9.1.3    Cấp độ: 2    Vai trò: D
 Xác minh rằng các công cụ giám sát tài nguyên theo thời gian thực kích hoạt ngắt mạch ngắt khi bất kỳ ngưỡng ngân sách nào bị vượt quá, dừng việc mở rộng tác vụ tiếp theo.
 #9.1.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các sự kiện ngắt mạch được ghi lại với ID đại lý, điều kiện kích hoạt và trạng thái kế hoạch được ghi nhận để phục vụ xem xét pháp y.
 #9.1.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng các bài kiểm tra bảo mật bao phủ các kịch bản cạn kiệt ngân sách và kế hoạch chạy trốn, đảm bảo dừng an toàn mà không mất dữ liệu.
 #9.1.6    Cấp độ: 3    Vai trò: D
 Xác nhận rằng các chính sách ngân sách được thể hiện dưới dạng mã chính sách và được thực thi trong CI/CD để ngăn chặn sự sai lệch cấu hình.

────────────────────────────────────────

### 9.2 Vùng cát Plugin Công cụ

Cô lập các tương tác công cụ để ngăn chặn truy cập hệ thống hoặc thực thi mã không được phép.

 #9.2.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng mỗi công cụ/plugin chạy bên trong hệ điều hành, container hoặc sandbox ở cấp độ WASM với các chính sách quyền hạn thấp nhất về hệ thống tệp, mạng và gọi hệ thống.
 #9.2.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các hạn ngạch tài nguyên sandbox (CPU, bộ nhớ, đĩa, xuất mạng) và thời gian chờ thực thi được thực thi và ghi log.
 #9.2.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các nhị phân công cụ hoặc mô tả được ký kỹ thuật số; các chữ ký được xác thực trước khi tải.
 #9.2.4    Cấp độ: 2    Vai trò: V
 Xác minh rằng dữ liệu đo lường từ sandbox được truyền đến SIEM; các bất thường (ví dụ: các kết nối ra ngoài bị cố gắng thực hiện) sẽ kích hoạt cảnh báo.
 #9.2.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng các plugin có nguy cơ cao được kiểm tra bảo mật và thử nghiệm xâm nhập trước khi triển khai ra môi trường sản xuất.
 #9.2.6    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các nỗ lực thoát khỏi sandbox được tự động chặn và plugin vi phạm bị cách ly chờ điều tra.

────────────────────────────────────────

### 9.3 Vòng lập trình Tự động & Giới hạn Chi phí

Phát hiện và ngăn chặn đệ quy không kiểm soát giữa các tác nhân và sự bùng nổ chi phí.

 #9.3.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các cuộc gọi giữa các tác nhân bao gồm giới hạn số lần chuyển tiếp hoặc TTL mà runtime sẽ giảm và thực thi.
 #9.3.2    Cấp độ: 2    Vai trò: D
 Xác minh rằng các tác nhân duy trì một ID đồ thị gọi độc nhất để phát hiện sự tự gọi hoặc các mẫu tuần hoàn.
 #9.3.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng bộ đếm đơn vị tính toán tích lũy và chi tiêu được theo dõi theo chuỗi yêu cầu; vượt quá giới hạn sẽ hủy bỏ chuỗi.
 #9.3.4    Cấp độ: 3    Vai trò: V
 Xác minh rằng phân tích hình thức hoặc kiểm tra mô hình chứng minh sự vắng mặt của đệ quy không giới hạn trong các giao thức đại lý.
 #9.3.5    Cấp độ: 3    Vai trò: D
 Xác minh rằng các sự kiện dừng vòng lặp tạo ra cảnh báo và cung cấp các chỉ số cải tiến liên tục.

────────────────────────────────────────

### 9.4 Bảo vệ chống lạm dụng cấp giao thức

Kênh truyền thông an toàn giữa các tác nhân và hệ thống bên ngoài để ngăn chặn chiếm quyền hoặc thao túng.

 #9.4.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng tất cả các tin nhắn giữa đại lý với công cụ và đại lý với đại lý đều được xác thực (ví dụ: mutual TLS hoặc JWT) và được mã hóa đầu cuối.
 #9.4.2    Cấp độ: 1    Vai trò: D
 Xác minh rằng các schema được xác thực một cách nghiêm ngặt; các trường không xác định hoặc các thông điệp bị sai định dạng sẽ bị từ chối.
 #9.4.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các kiểm tra tính toàn vẹn (MAC hoặc chữ ký số) bao phủ toàn bộ phần tải tin nhắn bao gồm cả các tham số công cụ.
 #9.4.4    Cấp độ: 2    Vai trò: D
 Xác minh rằng việc bảo vệ chống phát lại (nonce hoặc cửa sổ dấu thời gian) được thực thi ở tầng giao thức.
 #9.4.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng các triển khai giao thức được thực hiện kiểm thử fuzzing và phân tích tĩnh để phát hiện các lỗi tiêm nhiễm hoặc giải tuần tự.

────────────────────────────────────────

### 9.5 Thông Tin Định Danh Đại Lý & Bằng Chứng Chống Thay Đổi

Đảm bảo các hành động có thể được truy nguyên và các sửa đổi có thể phát hiện được.

 #9.5.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng mỗi thực thể đại lý sở hữu một danh tính mật mã duy nhất (cặp khóa hoặc chứng nhận gốc phần cứng).
 #9.5.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng tất cả các hành động của đại lý đều được ký và ghi dấu thời gian; các bản ghi bao gồm chữ ký để đảm bảo không thể chối bỏ.
 #9.5.3    Cấp độ: 2    Vai trò: V
 Xác minh rằng các nhật ký có khả năng phát hiện giả mạo được lưu trữ trên một phương tiện chỉ cho phép thêm dữ liệu hoặc ghi một lần.
 #9.5.4    Cấp độ: 3    Vai trò: D
 Xác minh rằng các khóa định danh được thay đổi theo lịch trình định trước và khi có dấu hiệu bị xâm phạm.
 #9.5.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các cố gắng giả mạo hoặc xung đột khóa sẽ kích hoạt việc cách ly ngay lập tức đối với tác nhân bị ảnh hưởng.

────────────────────────────────────────

### 9.6 Giảm Thiểu Rủi Ro Đàn Động Tác Tác Động Đa Tác Nhân

Giảm thiểu các nguy cơ hành vi tập thể thông qua cách ly và mô hình hóa an toàn chính thức.

 #9.6.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các tác nhân hoạt động trong các miền bảo mật khác nhau thực thi trong các môi trường chạy tách biệt hoặc các phân đoạn mạng riêng biệt.
 #9.6.2    Cấp độ: 3    Vai trò: V
 Xác minh rằng các hành vi bầy đàn được mô hình hóa và xác minh chính thức về tính sống động và an toàn trước khi triển khai.
 #9.6.3    Cấp độ: 3    Vai trò: D
 Xác minh rằng các bộ giám sát thời gian chạy phát hiện các mẫu không an toàn mới phát sinh (ví dụ: dao động, tình trạng treo) và thực hiện hành động khắc phục.

────────────────────────────────────────

### 9.7 Xác thực / Ủy quyền người dùng và công cụ

Triển khai kiểm soát truy cập chặt chẽ cho mọi hành động do đại lý kích hoạt.

 #9.7.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các đại lý xác thực như các chủ thể hạng nhất đối với các hệ thống hạ nguồn, không bao giờ sử dụng lại thông tin đăng nhập của người dùng cuối.
 #9.7.2    Cấp độ: 2    Vai trò: D
 Xác minh rằng các chính sách ủy quyền chi tiết giới hạn công cụ mà tác nhân có thể gọi và các tham số mà nó có thể cung cấp.
 #9.7.3    Cấp độ: 2    Vai trò: V
 Xác minh rằng các kiểm tra đặc quyền được đánh giá lại ở mỗi lần gọi (ủy quyền liên tục), không chỉ tại lúc bắt đầu phiên đăng nhập.
 #9.7.4    Cấp độ: 3    Vai trò: D
 Xác minh rằng các đặc quyền được ủy quyền tự động hết hạn và yêu cầu đồng ý lại sau khi hết thời gian hoặc thay đổi phạm vi.

────────────────────────────────────────

### 9.8 Bảo mật Giao tiếp Động tác viên-động tác viên

Mã hóa và bảo vệ tính toàn vẹn cho tất cả các thông điệp giữa các tác nhân để ngăn chặn việc nghe trộm và giả mạo.

 #9.8.1    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng xác thực hai chiều và mã hóa bảo mật hoàn hảo về phía trước (ví dụ: TLS 1.3) là bắt buộc cho các kênh đại lý.
 #9.8.2    Cấp độ: 1    Vai trò: D
 Xác minh rằng tính toàn vẹn và nguồn gốc của thông điệp được xác thực trước khi xử lý; các lỗi sẽ kích hoạt cảnh báo và loại bỏ thông điệp.
 #9.8.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng siêu dữ liệu giao tiếp (dấu thời gian, số thứ tự) được ghi lại để hỗ trợ việc tái tạo pháp y.
 #9.8.4    Cấp độ: 3    Vai trò: V
 Xác minh rằng việc xác minh hình thức hoặc kiểm tra mô hình xác nhận rằng các máy trạng thái giao thức không thể bị dẫn đến các trạng thái không an toàn.

────────────────────────────────────────

### 9.9 Xác minh ý định & Thực thi ràng buộc

Xác nhận rằng các hành động của đại lý phù hợp với ý định đã được người dùng nêu ra và các ràng buộc của hệ thống.

 #9.9.1    Cấp độ: 1    Vai trò: D
 Xác minh rằng các bộ giải ràng buộc trước khi thực thi kiểm tra các hành động được đề xuất dựa trên các quy tắc an toàn và chính sách được mã hóa cứng.
 #9.9.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các hành động có tác động lớn (tài chính, phá hoại, nhạy cảm về quyền riêng tư) yêu cầu xác nhận mục đích rõ ràng từ người dùng khởi xướng.
 #9.9.3    Cấp độ: 2    Vai trò: V
 Xác minh rằng các kiểm tra điều kiện hậu xác nhận các hành động đã hoàn thành đạt được hiệu quả dự định mà không có tác dụng phụ; các sai lệch sẽ kích hoạt việc hoàn tác.
 #9.9.4    Cấp độ: 3    Vai trò: V
 Xác minh rằng các phương pháp hình thức (ví dụ, kiểm tra mô hình, chứng minh định lý) hoặc kiểm thử dựa trên thuộc tính chứng minh rằng các kế hoạch của đại lý đáp ứng tất cả các ràng buộc đã khai báo.
 #9.9.5    Cấp độ: 3    Vai trò: D
 Xác nhận rằng các sự cố không khớp ý định hoặc vi phạm ràng buộc được đưa vào chu trình cải tiến liên tục và chia sẻ thông tin tình báo về mối đe dọa.

────────────────────────────────────────

### 9.10 Chiến lược Lập luận Đại lý An ninh

Lựa chọn và thực thi an toàn các chiến lược suy luận khác nhau bao gồm các phương pháp ReAct, Chuỗi suy nghĩ (Chain-of-Thought) và Cây suy nghĩ (Tree-of-Thoughts).

 #9.10.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng việc lựa chọn chiến lược suy luận sử dụng các tiêu chí quyết định (độ phức tạp đầu vào, loại nhiệm vụ, ngữ cảnh bảo mật) và các đầu vào giống hệt nhau tạo ra các lựa chọn chiến lược giống nhau trong cùng một ngữ cảnh bảo mật.
 #9.10.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng mỗi chiến lược tư duy (ReAct, Chuỗi suy nghĩ, Cây suy nghĩ) có kiểm tra đầu vào riêng biệt, làm sạch đầu ra, và giới hạn thời gian thực thi phù hợp với phương pháp nhận thức của nó.
 #9.10.3    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng các chuyển đổi chiến lược suy luận được ghi lại với bối cảnh đầy đủ bao gồm đặc điểm đầu vào, giá trị tiêu chí lựa chọn và siêu dữ liệu thực thi để tái tạo dấu vết kiểm tra.
 #9.10.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng phương pháp suy luận Tree-of-Thoughts bao gồm các cơ chế cắt tỉa nhánh để chấm dứt việc khám phá khi phát hiện vi phạm chính sách, giới hạn tài nguyên hoặc ranh giới an toàn.
 #9.10.5    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng chu kỳ ReAct (Lý luận-Hành động-Quan sát) bao gồm các điểm kiểm tra xác thực ở mỗi giai đoạn: xác minh bước lý luận, phê duyệt hành động, và làm sạch quan sát trước khi tiếp tục.
 #9.10.6    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các chỉ số hiệu suất chiến lược lý luận (thời gian thực thi, sử dụng tài nguyên, chất lượng đầu ra) được theo dõi với các cảnh báo tự động khi các chỉ số vượt quá ngưỡng cấu hình.
 #9.10.7    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các phương pháp suy luận kết hợp nhiều chiến lược duy trì việc xác thực đầu vào và các giới hạn đầu ra của tất cả các chiến lược thành phần mà không vượt qua bất kỳ kiểm soát bảo mật nào.
 #9.10.8    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng kiểm thử bảo mật chiến lược lý luận bao gồm việc thử nghiệm fuzzing với các đầu vào bị lỗi, các lời nhắc đối kháng được thiết kế để buộc chuyển đổi chiến lược, và kiểm thử điều kiện biên cho từng phương pháp nhận thức.

────────────────────────────────────────

### 9.11 Quản lý trạng thái vòng đời đại lý & Bảo mật

Khởi tạo đại lý an toàn, chuyển đổi trạng thái và kết thúc với các dấu vết kiểm toán mật mã và quy trình phục hồi được xác định rõ.

 #9.11.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng việc khởi tạo tác nhân bao gồm thiết lập danh tính mật mã với chứng chỉ được bảo vệ bởi phần cứng và các nhật ký kiểm toán khởi động không thể thay đổi chứa ID tác nhân, dấu thời gian, hàm băm cấu hình và các tham số khởi tạo.
 #9.11.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các chuyển đổi trạng thái của đại lý được ký thuật toán mã hóa, đóng dấu thời gian và ghi lại cùng với ngữ cảnh đầy đủ bao gồm các sự kiện kích hoạt, băm trạng thái trước đó, băm trạng thái mới và các xác thực bảo mật đã được thực hiện.
 #9.11.3    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng các quy trình tắt agent bao gồm việc xóa bộ nhớ an toàn bằng phương pháp xóa mật mã hoặc ghi đè nhiều lần, thu hồi thông tin đăng nhập kèm theo thông báo tới cơ quan cấp chứng chỉ, và tạo ra các chứng chỉ chấm dứt có khả năng phát hiện giả mạo.
 #9.11.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các cơ chế phục hồi tác nhân xác thực tính toàn vẹn của trạng thái bằng cách sử dụng các bảng kiểm tra mật mã (ít nhất là SHA-256) và khôi phục lại các trạng thái đã biết là tốt khi phát hiện hỏng hóc, kèm theo cảnh báo tự động và yêu cầu phê duyệt thủ công.
 #9.11.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các cơ chế lưu trữ trạng thái của tác nhân mã hóa dữ liệu trạng thái nhạy cảm bằng khóa AES-256 riêng cho từng tác nhân và triển khai việc xoay khóa an toàn theo lịch trình có thể cấu hình (tối đa 90 ngày) với việc triển khai không gián đoạn.

────────────────────────────────────────

### 9.12 Khung An ninh Tích hợp Công cụ

Các biện pháp kiểm soát bảo mật cho việc tải công cụ động, thực thi và xác thực kết quả với các quy trình đánh giá rủi ro và phê duyệt đã được xác định.

 #9.12.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các mô tả công cụ bao gồm siêu dữ liệu bảo mật chỉ định các đặc quyền cần thiết (đọc/ghi/thực thi), mức độ rủi ro (thấp/trung bình/cao), giới hạn tài nguyên (CPU, bộ nhớ, mạng), và các yêu cầu xác thực được ghi chép trong các bản mô tả công cụ.
 #9.12.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng kết quả thực thi công cụ được kiểm tra xác thực theo các lược đồ dự kiến (JSON Schema, XML Schema) và các chính sách bảo mật (lọc đầu ra, phân loại dữ liệu) trước khi tích hợp, với các giới hạn thời gian chờ và quy trình xử lý lỗi.
 #9.12.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng nhật ký tương tác công cụ bao gồm ngữ cảnh bảo mật chi tiết bao gồm việc sử dụng đặc quyền, mô hình truy cập dữ liệu, thời gian thực thi, tiêu thụ tài nguyên và mã trả về với ghi nhật ký có cấu trúc để tích hợp SIEM.
 #9.12.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các cơ chế tải công cụ động kiểm tra chữ ký số sử dụng hạ tầng PKI và thực hiện các giao thức tải an toàn với cách ly sandbox cùng xác minh quyền trước khi thực thi.
 #9.12.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các đánh giá bảo mật công cụ được kích hoạt tự động cho các phiên bản mới với các cổng phê duyệt bắt buộc bao gồm phân tích tĩnh, kiểm thử động và đánh giá nhóm bảo mật cùng với các tiêu chí phê duyệt đã được tài liệu hóa và yêu cầu SLA.

────────────────────────────────────────

#### Tài liệu tham khảo

MITRE ATLAS tactics ML09
Circuit-breaker research for AI agents — Zou et al., 2024
Trend Micro analysis of sandbox escapes in AI agents — Park, 2025
Auth0 guidance on human-in-the-loop authorization for agents — Martinez, 2025
Medium deep-dive on MCP & A2A protocol hijacking — ForAISec, 2025
Rapid7 fundamentals on spoofing attack prevention — 2024
Imperial College verification of swarm systems — Lomuscio et al.
NIST AI Risk Management Framework 1.0, 2023
WIRED security briefing on encryption best practices, 2024
OWASP Top 10 for LLM Applications, 2025
Comprehensive Vulnerability Analysis is Necessary for Trustworthy LLM-MAS
[How Is LLM Reasoning Distracted by Irrelevant Context?
An Analysis Using a Controlled Benchmark](https://www.arxiv.org/pdf/2505.18761)
Large Language Model Sentinel: LLM Agent for Adversarial Purification
Securing Agentic AI: A Comprehensive Threat Model and Mitigation Framework for Generative AI Agents

## 10 Độ Bền Đối Kháng & Bảo Vệ Quyền Riêng Tư

### Mục tiêu Kiểm soát

Đảm bảo rằng các mô hình AI vẫn đáng tin cậy, bảo vệ quyền riêng tư và chống lạm dụng khi đối mặt với các cuộc tấn công né tránh, suy diễn, trích xuất hoặc đầu độc.

────────────────────────────────────────

### 10.1 Cân chỉnh và An toàn Mô hình

Bảo vệ chống lại các kết quả đầu ra gây hại hoặc vi phạm chính sách.

 #10.1.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng bộ kiểm tra căn chỉnh (lệnh nhắc đội đỏ, thăm dò phá khóa, nội dung bị cấm) được quản lý phiên bản và chạy trên mọi phiên bản mô hình phát hành.
 #10.1.2    Cấp độ: 1    Vai trò: D
 Xác minh rằng các biện pháp từ chối và bảo vệ hoàn thành an toàn được thực thi.
 #10.1.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng một bộ đánh giá tự động đo lường tỷ lệ nội dung có hại và đánh dấu các bước lùi vượt quá ngưỡng đã đặt.
 #10.1.4    Cấp độ: 2    Vai trò: D
 Xác nhận rằng việc huấn luyện chống jailbreak được ghi chép và có thể tái tạo.
 #10.1.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng các bằng chứng tuân thủ chính sách chính thức hoặc giám sát được chứng nhận bao phủ các lĩnh vực quan trọng.

────────────────────────────────────────

### 10.2 Củng cố chống lại các ví dụ đối kháng

Tăng khả năng chịu đựng trước các đầu vào bị thao túng. Huấn luyện đối kháng chắc chắn và đánh giá chuẩn hiện là phương pháp tốt nhất hiện nay.

 #10.2.1    Cấp độ: 1    Vai trò: D
 Xác minh rằng các kho lưu trữ dự án bao gồm các cấu hình huấn luyện đối kháng với các hạt giống có thể tái lập.
 #10.2.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng việc phát hiện ví dụ đối kháng kích hoạt cảnh báo chặn trong các quy trình sản xuất.
 #10.2.4    Cấp độ: 3    Vai trò: V
 Xác minh rằng các bằng chứng về tính chắc chắn đã được chứng nhận hoặc các chứng nhận giới hạn khoảng bao phủ ít nhất các lớp quan trọng hàng đầu.
 #10.2.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng các bài kiểm tra hồi quy sử dụng các cuộc tấn công thích ứng để xác nhận không có mất mát độ bền đo được nào.

────────────────────────────────────────

### 10.3 Giảm thiểu Rò rỉ Thành viên

Hạn chế khả năng quyết định liệu một bản ghi có nằm trong dữ liệu đào tạo hay không. Bảo mật vi phân và che điểm tin cậy vẫn là những biện pháp phòng thủ hiệu quả nhất đã biết.

 #10.3.1    Cấp độ: 1    Vai trò: D
 Xác minh rằng việc chuẩn hóa entropy theo từng truy vấn hoặc điều chỉnh nhiệt độ giúp giảm các dự đoán quá tự tin.
 #10.3.2    Cấp độ: 2    Vai trò: D
 Xác minh rằng việc đào tạo sử dụng tối ưu hóa riêng tư khác biệt có giới hạn ε cho các bộ dữ liệu nhạy cảm.
 #10.3.3    Cấp độ: 2    Vai trò: V
 Xác nhận rằng các mô phỏng tấn công (mô hình bóng hoặc hộp đen) cho thấy AUC của tấn công ≤ 0,60 trên dữ liệu giữ lại.

────────────────────────────────────────

### 10.4 Kháng lại Đảo ngược Mô hình

Ngăn chặn việc tái tạo các thuộc tính riêng tư. Các khảo sát gần đây nhấn mạnh cắt ngắn đầu ra và đảm bảo DP như các biện pháp phòng thủ thực tiễn.

 #10.4.1    Cấp độ: 1    Vai trò: D
 Xác minh rằng các thuộc tính nhạy cảm không bao giờ được xuất ra trực tiếp; khi cần, sử dụng các nhóm (buckets) hoặc biến đổi một chiều.
 #10.4.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng giới hạn tỷ lệ truy vấn kiểm soát các truy vấn thích ứng lặp lại từ cùng một chủ thể.
 #10.4.3    Cấp độ: 2    Vai trò: D
 Xác nhận rằng mô hình đã được huấn luyện với nhiễu bảo vệ quyền riêng tư.

────────────────────────────────────────

### 10.5 Phòng thủ Trích xuất Mô hình

Phát hiện và ngăn chặn sao chép trái phép. Đề xuất sử dụng kỹ thuật đóng dấu bản quyền và phân tích mẫu truy vấn.

 #10.5.1    Cấp độ: 1    Vai trò: D
 Xác minh rằng các cổng suy luận thực thi giới hạn tỷ lệ toàn cầu và theo từng khóa API được điều chỉnh phù hợp với ngưỡng ghi nhớ của mô hình.
 #10.5.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng thống kê entropy-truy vấn và đa số-đầu vào cung cấp dữ liệu cho bộ phát hiện trích xuất tự động.
 #10.5.3    Cấp độ: 2    Vai trò: V
 Xác minh rằng các watermark dễ vỡ hoặc xác suất có thể được chứng minh với p < 0.01 trong ≤ 1 000 truy vấn đối với một bản sao nghi ngờ.
 #10.5.4    Cấp độ: 3    Vai trò: D
 Xác minh rằng các khóa watermark và bộ kích hoạt được lưu trữ trong mô-đun bảo mật phần cứng và được thay đổi hàng năm.
 #10.5.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng các sự kiện extraction-alert bao gồm các truy vấn vi phạm và được tích hợp với các sách hướng dẫn xử lý sự cố.

────────────────────────────────────────

### 10.6 Phát hiện Dữ liệu Bị Độc tại Thời điểm Suy luận

Xác định và trung hòa các đầu vào bị cài đặt cửa sau hoặc bị đầu độc.

 #10.6.1    Cấp độ: 1    Vai trò: D
 Xác minh rằng các đầu vào được kiểm tra qua bộ phát hiện bất thường (ví dụ: STRIP, chấm điểm nhất quán) trước khi suy luận mô hình.
 #10.6.2    Cấp độ: 1    Vai trò: V
 Xác minh rằng ngưỡng của bộ phát hiện được điều chỉnh trên các tập dữ liệu xác thực sạch/đã bị đầu độc để đạt được tỷ lệ dương tính giả dưới 5%.
 #10.6.3    Cấp độ: 2    Vai trò: D
 Xác minh rằng các đầu vào bị đánh dấu là đầu độc kích hoạt quy trình chặn mềm và xem xét bởi con người.
 #10.6.4    Cấp độ: 2    Vai trò: V
 Xác nhận rằng các bộ cảm biến đã được kiểm tra độ bền bằng các cuộc tấn công cửa hậu thích ứng không cần kích hoạt.
 #10.6.5    Cấp độ: 3    Vai trò: D
 Xác minh rằng các chỉ số hiệu quả phát hiện được ghi lại và định kỳ đánh giá lại với thông tin tình báo mối đe dọa mới.

────────────────────────────────────────

### 10.7 Điều chỉnh Chính sách Bảo mật Động

Cập nhật chính sách bảo mật theo thời gian thực dựa trên thông tin tình báo mối đe dọa và phân tích hành vi.

 #10.7.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các chính sách bảo mật có thể được cập nhật động mà không cần khởi động lại đại lý trong khi vẫn duy trì tính toàn vẹn của phiên bản chính sách.
 #10.7.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các cập nhật chính sách được ký bằng mật mã bởi nhân sự bảo mật có thẩm quyền và được xác nhận trước khi áp dụng.
 #10.7.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các thay đổi chính sách động được ghi lại với đầy đủ các nhật ký kiểm toán bao gồm lý do, chuỗi phê duyệt, và quy trình hoàn tác.
 #10.7.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các cơ chế bảo mật thích ứng điều chỉnh độ nhạy phát hiện mối đe dọa dựa trên ngữ cảnh rủi ro và các mẫu hành vi.
 #10.7.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các quyết định điều chỉnh chính sách có thể giải thích được và bao gồm các bằng chứng theo dõi để nhóm an ninh xem xét.

────────────────────────────────────────

### 10.8 Phân tích Bảo mật Dựa trên Phản chiếu

Xác thực bảo mật thông qua sự tự phản ánh của đại lý và phân tích siêu nhận thức.

 #10.8.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các cơ chế phản chiếu của tác nhân bao gồm đánh giá tự thân tập trung vào bảo mật đối với các quyết định và hành động.
 #10.8.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các kết quả phản chiếu được xác thực để ngăn chặn việc thao túng các cơ chế tự đánh giá bởi các đầu vào đối kháng.
 #10.8.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng phân tích bảo mật siêu nhận thức xác định được các thiên vị tiềm ẩn, sự thao túng hoặc sự xâm phạm trong quy trình lý luận của tác nhân.
 #10.8.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các cảnh báo bảo mật dựa trên phản chiếu kích hoạt việc giám sát nâng cao và các quy trình can thiệp của con người tiềm năng.
 #10.8.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng việc học liên tục từ các phản ánh về bảo mật cải thiện khả năng phát hiện mối đe dọa mà không làm suy giảm chức năng hợp lệ.

────────────────────────────────────────

### 10.9 Bảo mật tiến hóa & tự cải thiện

Các biện pháp kiểm soát an ninh cho hệ thống tác nhân có khả năng tự chỉnh sửa và phát triển.

 #10.9.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các khả năng tự sửa đổi được giới hạn trong các khu vực an toàn được chỉ định với các ranh giới xác minh chính thức.
 #10.9.2    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng các đề xuất tiến hóa phải trải qua đánh giá tác động an ninh trước khi triển khai.
 #10.9.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các cơ chế tự cải tiến bao gồm khả năng khôi phục với việc kiểm tra tính toàn vẹn.
 #10.9.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng bảo mật meta-learning ngăn chặn sự thao túng đối kháng của các thuật toán cải tiến.
 #10.9.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng việc tự cải tiến đệ quy được giới hạn bởi các ràng buộc an toàn chính thức với các bằng chứng toán học về sự hội tụ.

────────────────────────────────────────

#### Tài liệu tham khảo

MITRE ATLAS adversary tactics for ML
NIST AI Risk Management Framework 1.0, 2023
OWASP Top 10 for LLM Applications, 2025
Adversarial Training: A Survey — Zhao et al., 2024
RobustBench adversarial-robustness benchmark
Membership-Inference & Model-Inversion Risk Survey, 2025
PURIFIER: Confidence-Score Defense against MI Attacks — AAAI 2023
Model-Inversion Attacks & Defenses Survey — AI Review, 2025
Comprehensive Defense Framework Against Model Extraction — IEEE TDSC 2024
Fragile Model Watermarking Survey — 2025
Data Poisoning in Deep Learning: A Survey — Zhao et al., 2025
BDetCLIP: Multimodal Prompting Backdoor Detection — Niu et al., 2024

## 11 Bảo vệ quyền riêng tư & Quản lý dữ liệu cá nhân

### Mục tiêu Kiểm soát

Duy trì các cam kết bảo mật nghiêm ngặt trong toàn bộ vòng đời AI—thu thập, huấn luyện, suy luận và phản ứng sự cố—để dữ liệu cá nhân chỉ được xử lý với sự đồng ý rõ ràng, phạm vi tối thiểu cần thiết, xóa dữ liệu có thể chứng minh và các đảm bảo bảo mật chính thức.

────────────────────────────────────────

### 11.1 Ẩn danh & Tối thiểu hóa dữ liệu

 #11.1.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các định danh trực tiếp và bán định danh đã được loại bỏ hoặc băm.
 #11.1.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các cuộc kiểm tra tự động đo lường k-anonymity/l-diversity và cảnh báo khi các ngưỡng giảm dưới mức chính sách.
 #11.1.3    Cấp độ: 2    Vai trò: V
 Xác minh rằng các báo cáo tầm quan trọng đặc trưng của mô hình chứng minh không có rò rỉ định danh vượt quá ε = 0.01 thông tin tương hỗ.
 #11.1.4    Cấp độ: 3    Vai trò: V
 Xác minh rằng các chứng minh hình thức hoặc chứng nhận dữ liệu tổng hợp cho thấy nguy cơ tái nhận dạng ≤ 0.05 ngay cả dưới các cuộc tấn công liên kết.

────────────────────────────────────────

### 11.2 Quyền được quên & Thực thi xóa dữ liệu

 #11.2.1    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng các yêu cầu xóa dữ liệu cá nhân được truyền đến các bộ dữ liệu thô, điểm kiểm tra, nhúng, nhật ký và sao lưu trong phạm vi thỏa thuận mức dịch vụ dưới 30 ngày.
 #11.2.2    Cấp độ: 2    Vai trò: D
 Xác minh rằng các quy trình "machine-unlearning" thực sự đào tạo lại hoặc xóa bỏ gần đúng bằng cách sử dụng các thuật toán xóa học được chứng nhận.
 #11.2.3    Cấp độ: 2    Vai trò: V
 Xác minh rằng đánh giá mô hình bóng tối chứng minh các bản ghi đã bị quên ảnh hưởng dưới 1% kết quả sau khi loại bỏ kiến thức.
 #11.2.4    Cấp độ: 3    Vai trò: V
 Xác minh rằng các sự kiện xóa được ghi lại một cách không thể thay đổi và có thể kiểm tra cho các cơ quan quản lý.

────────────────────────────────────────

### 11.3 Các biện pháp bảo vệ quyền riêng tư vi phân

 #11.3.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các bảng điều khiển theo dõi thiệt hại riêng tư cảnh báo khi tổng ε vượt quá ngưỡng chính sách.
 #11.3.2    Cấp độ: 2    Vai trò: V
 Xác minh rằng các cuộc kiểm toán quyền riêng tư hộp đen ước tính ε̂ trong phạm vi 10% giá trị đã khai báo.
 #11.3.3    Cấp độ: 3    Vai trò: V
 Xác minh rằng các bằng chứng hình thức bao phủ tất cả các tinh chỉnh sau khi đào tạo và các nhúng.

────────────────────────────────────────

### 11.4 Hạn chế mục đích & Bảo vệ chống tràn phạm vi

 #11.4.1    Cấp độ: 1    Vai trò: D
 Xác minh rằng mỗi bộ dữ liệu và điểm kiểm tra mô hình đều mang thẻ mục đích có thể đọc bằng máy và phù hợp với sự đồng thuận ban đầu.
 #11.4.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các bộ theo dõi thời gian chạy phát hiện các truy vấn không nhất quán với mục đích đã khai báo và kích hoạt từ chối mềm.
 #11.4.3    Cấp độ: 3    Vai trò: D
 Xác minh rằng các cổng policy-as-code ngăn chặn việc triển khai lại các mô hình sang các miền mới mà không qua đánh giá DPIA.
 #11.4.4    Cấp độ: 3    Vai trò: V
 Xác minh rằng các bằng chứng truy xuất chính thức cho thấy mọi vòng đời dữ liệu cá nhân vẫn nằm trong phạm vi đã được đồng ý.

────────────────────────────────────────

### 11.5 Quản lý sự đồng ý & Theo dõi cơ sở pháp lý

 #11.5.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng Nền tảng Quản lý Đồng thuận (CMP) ghi lại trạng thái đồng ý, mục đích và thời gian lưu giữ cho từng đối tượng dữ liệu.
 #11.5.2    Cấp độ: 2    Vai trò: D
 Xác minh rằng các API tiết lộ mã thông báo đồng ý; các mô hình phải xác thực phạm vi mã thông báo trước khi suy luận.
 #11.5.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng việc từ chối hoặc rút lại sự đồng ý sẽ ngăn chặn các quy trình xử lý trong vòng 24 giờ.

────────────────────────────────────────

### 11.6 Học Liên Liền với Kiểm Soát Quyền Riêng Tư

 #11.6.1    Cấp độ: 1    Vai trò: D
 Xác minh rằng các bản cập nhật của khách hàng sử dụng phép thêm nhiễu bảo mật vi phân cục bộ trước khi tổng hợp.
 #11.6.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các chỉ số huấn luyện có tính riêng tư vi phân và không bao giờ tiết lộ tổn thất của từng khách hàng riêng lẻ.
 #11.6.3    Cấp độ: 2    Vai trò: V
 Xác minh rằng việc tổng hợp chống đầu độc (ví dụ: Krum/Trimmed-Mean) đã được bật.
 #11.6.4    Cấp độ: 3    Vai trò: V
 Xác minh rằng các bằng chứng chính thức chứng minh tổng ngân sách ε với mất mát tiện ích dưới 5.

────────────────────────────────────────

#### Tài liệu tham khảo

GDPR & AI Compliance Best Practices
EU Parliament Study on GDPR & AI, 2020
ISO 31700-1:2023 — Privacy by Design for Consumer Products
NIST Privacy Framework 1.1 (2025 Draft)
Machine Unlearning: Right-to-Be-Forgotten Techniques
A Survey of Machine Unlearning, 2024
Auditing DP-SGD — ArXiv 2024
DP-SGD Explained — PyTorch Blog
Purpose-Limitation for AI — IJLIT 2025
Data-Protection Considerations for AI — URM Consulting
Top Consent-Management Platforms, 2025
Secure Aggregation in DP Federated Learning — ArXiv 2024

## C12 Giám sát, Ghi nhật ký & Phát hiện Dị thường

### Mục tiêu Kiểm soát

Phần này cung cấp các yêu cầu để cung cấp khả năng quan sát thời gian thực và phân tích pháp y về những gì mô hình và các thành phần AI khác nhìn thấy, thực hiện và trả về, nhằm phát hiện, phân loại và rút kinh nghiệm từ các mối đe dọa.

### C12.1 Ghi lại Yêu cầu & Phản hồi

 #12.1.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng tất cả các lời nhắc của người dùng và phản hồi của mô hình đều được ghi lại cùng với siêu dữ liệu thích hợp (ví dụ: dấu thời gian, ID người dùng, ID phiên, phiên bản mô hình).
 #12.1.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các bản ghi được lưu trữ trong các kho lưu trữ an toàn, có kiểm soát truy cập với các chính sách giữ lại và quy trình sao lưu phù hợp.
 #12.1.3    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các hệ thống lưu trữ nhật ký thực hiện mã hóa khi dữ liệu được nghỉ lưu và khi truyền tải để bảo vệ thông tin nhạy cảm chứa trong các nhật ký.
 #12.1.4    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng dữ liệu nhạy cảm trong các lời nhắc và kết quả đầu ra được tự động ẩn hoặc che giấu trước khi ghi lại, với các quy tắc ẩn có thể cấu hình cho thông tin cá nhân (PII), thông tin đăng nhập và thông tin độc quyền.
 #12.1.5    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các quyết định chính sách và các hành động lọc an toàn được ghi lại với chi tiết đủ để cho phép kiểm toán và gỡ lỗi các hệ thống kiểm duyệt nội dung.
 #12.1.6    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng tính toàn vẹn của nhật ký được bảo vệ thông qua ví dụ như chữ ký mật mã hoặc lưu trữ chỉ ghi.

────────────────────────────────────────

### C12.2 Phát hiện và cảnh báo lạm dụng

 #12.2.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng hệ thống phát hiện và cảnh báo các mẫu jailbreak đã biết, các cố gắng chèn prompt, và các đầu vào đối kháng sử dụng phương pháp phát hiện dựa trên chữ ký.
 #12.2.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng hệ thống tích hợp với các nền tảng Quản lý Thông tin và Sự kiện Bảo mật (SIEM) hiện có bằng cách sử dụng các định dạng và giao thức nhật ký tiêu chuẩn.
 #12.2.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các sự kiện bảo mật được làm phong phú bao gồm ngữ cảnh đặc thù của AI như định danh mô hình, điểm tin cậy và các quyết định của bộ lọc an toàn.
 #12.2.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng phát hiện bất thường hành vi nhận diện các mẫu hội thoại bất thường, số lần thử lại quá nhiều hoặc các hành vi thăm dò có hệ thống.
 #12.2.5    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các cơ chế cảnh báo thời gian thực thông báo cho các đội an ninh khi phát hiện các vi phạm chính sách tiềm năng hoặc các cố gắng tấn công.
 #12.2.6    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các quy tắc tùy chỉnh được bao gồm để phát hiện các mẫu mối đe dọa đặc thù AI bao gồm các nỗ lực phá rào phối hợp, chiến dịch tiêm lệnh nhắc và các cuộc tấn công trích xuất mô hình.
 #12.2.7    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng quy trình phản hồi sự cố tự động có thể cô lập các mô hình bị xâm phạm, chặn người dùng độc hại và nâng cao các sự kiện bảo mật quan trọng.

────────────────────────────────────────

### C12.3 Phát hiện Trôi mô hình

 #12.3.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng hệ thống theo dõi các chỉ số hiệu suất cơ bản như độ chính xác, điểm tin cậy, độ trễ và tỷ lệ lỗi qua các phiên bản mô hình và các khoảng thời gian.
 #12.3.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng cảnh báo tự động kích hoạt khi các chỉ số hiệu suất vượt quá ngưỡng suy giảm đã định trước hoặc lệch đáng kể so với các giá trị cơ sở.
 #12.3.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các bộ theo dõi phát hiện ảo giác có thể nhận diện và đánh dấu các trường hợp khi kết quả mô hình chứa thông tin không chính xác về mặt thực tế, không nhất quán hoặc được tạo ra giả mạo.

────────────────────────────────────────

### C12.4 Hiệu suất & Thu thập dữ liệu hành vi

 #12.4.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các chỉ số vận hành bao gồm độ trễ yêu cầu, tiêu thụ token, sử dụng bộ nhớ và thông lượng được thu thập và giám sát liên tục.
 #12.4.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng tỷ lệ thành công và thất bại được theo dõi kèm phân loại các loại lỗi và nguyên nhân gốc rễ của chúng.
 #12.4.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng việc giám sát sử dụng tài nguyên bao gồm sử dụng GPU/CPU, tiêu thụ bộ nhớ và yêu cầu lưu trữ với cảnh báo khi vượt ngưỡng.

────────────────────────────────────────

### C12.5 Lập kế hoạch và Thực thi Phản ứng Sự cố AI

 #12.5.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các kế hoạch ứng phó sự cố cụ thể đề cập đến các sự kiện bảo mật liên quan đến AI bao gồm việc xâm phạm mô hình, nhiễm độc dữ liệu và các cuộc tấn công đối kháng.
 #12.5.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các nhóm ứng phó sự cố có quyền truy cập vào các công cụ pháp y chuyên biệt cho AI và chuyên môn để điều tra hành vi mô hình cũng như các vectơ tấn công.
 #12.5.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng phân tích sau sự cố bao gồm các cân nhắc về việc huấn luyện lại mô hình, cập nhật bộ lọc an toàn và tích hợp các bài học kinh nghiệm vào các biện pháp kiểm soát bảo mật.

────────────────────────────────────────

### C12.6 Phát hiện suy giảm hiệu suất AI

Giám sát và phát hiện sự suy giảm trong hiệu suất và chất lượng của mô hình AI theo thời gian.

 #12.6.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng độ chính xác mô hình, độ chính xác (precision), độ thu hồi (recall), và điểm F1 được theo dõi liên tục và so sánh với các ngưỡng cơ sở.
 #12.6.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng việc phát hiện trôi dữ liệu giám sát các thay đổi trong phân phối dữ liệu đầu vào có thể ảnh hưởng đến hiệu suất của mô hình.
 #12.6.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng việc phát hiện trôi khái niệm nhận diện được các thay đổi trong mối quan hệ giữa đầu vào và đầu ra dự kiến.
 #12.6.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng sự suy giảm hiệu suất kích hoạt các cảnh báo tự động và bắt đầu các quy trình làm việc tái huấn luyện hoặc thay thế mô hình.
 #12.6.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng phân tích nguyên nhân gốc rễ suy giảm liên kết các mức giảm hiệu suất với các thay đổi dữ liệu, sự cố hạ tầng hoặc các yếu tố bên ngoài.

────────────────────────────────────────

### C12.7 Hình ảnh hóa DAG & Bảo mật Quy trình làm việc

Bảo vệ hệ thống trực quan hóa quy trình làm việc khỏi rò rỉ thông tin và các cuộc tấn công thao túng.

 #12.7.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng dữ liệu trực quan hóa DAG được làm sạch để loại bỏ thông tin nhạy cảm trước khi lưu trữ hoặc truyền tải.
 #12.7.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các điều khiển truy cập trực quan hóa quy trình làm việc đảm bảo chỉ người dùng được ủy quyền mới có thể xem các đường dẫn quyết định của tác nhân và các dấu vết lý giải.
 #12.7.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng tính toàn vẹn của dữ liệu DAG được bảo vệ thông qua chữ ký mật mã và cơ chế lưu trữ chống giả mạo.
 #12.7.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các hệ thống trực quan hóa quy trình làm việc thực hiện xác thực đầu vào để ngăn chặn các cuộc tấn công chèn mã thông qua dữ liệu nút hoặc cạnh được tạo thủ công.
 #12.7.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các cập nhật DAG theo thời gian thực được giới hạn tần suất và kiểm tra hợp lệ để ngăn chặn các cuộc tấn công từ chối dịch vụ trên hệ thống trực quan hóa.

────────────────────────────────────────

### C12.8 Giám sát Hành vi An ninh Chủ động

Phát hiện và ngăn chặn các mối đe dọa an ninh thông qua phân tích hành vi đại lý một cách chủ động.

 #12.8.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các hành vi của đại lý chủ động được xác thực về bảo mật trước khi thực hiện với tích hợp đánh giá rủi ro.
 #12.8.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các bước khởi xướng tự động bao gồm đánh giá bối cảnh bảo mật và đánh giá cảnh quan mối đe dọa.
 #12.8.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các mẫu hành vi chủ động được phân tích để đánh giá các tác động tiềm năng về bảo mật và các hậu quả không mong muốn.
 #12.8.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các hành động chủ động có tính bảo mật quan trọng yêu cầu chuỗi phê duyệt rõ ràng kèm theo dấu vết kiểm toán.
 #12.8.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng việc phát hiện bất thường hành vi nhận dạng những sai lệch trong các mẫu tác nhân chủ động có thể chỉ ra sự xâm phạm.

────────────────────────────────────────

### Tài liệu tham khảo

NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3
ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6

## C13 Giám sát Con người, Trách nhiệm và Quản trị

### Mục tiêu Kiểm soát

Chương này cung cấp các yêu cầu để duy trì sự giám sát của con người và chuỗi trách nhiệm rõ ràng trong các hệ thống AI, đảm bảo khả năng giải thích, minh bạch và quản lý đạo đức xuyên suốt vòng đời của AI.

────────────────────────────────────────

### C13.1 Cơ chế Công tắc Ngắt & Ghi đè

Cung cấp các phương án tắt máy hoặc phục hồi khi phát hiện hành vi không an toàn của hệ thống AI.

 #13.1.1    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng có một cơ chế công tắc ngắt thủ công để ngay lập tức dừng việc suy luận và xuất kết quả của mô hình AI.
 #13.1.2    Cấp độ: 1    Vai trò: D
 Xác minh rằng các kiểm soát ghi đè chỉ có thể truy cập bởi nhân sự được ủy quyền.
 #13.1.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các quy trình hoàn tác có thể quay trở lại các phiên bản mô hình trước đó hoặc các hoạt động ở chế độ an toàn.
 #13.1.4    Cấp độ: 3    Vai trò: V
 Xác minh rằng các cơ chế ghi đè được kiểm tra thường xuyên.

────────────────────────────────────────

### C13.2 Các điểm kiểm tra quyết định có con người tham gia

Yêu cầu sự chấp thuận của con người khi mức độ rủi ro vượt quá ngưỡng đã định trước.

 #13.2.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các quyết định AI có rủi ro cao yêu cầu sự phê duyệt rõ ràng của con người trước khi thực hiện.
 #13.2.2    Cấp độ: 1    Vai trò: D
 Xác nhận rằng các ngưỡng rủi ro được định nghĩa rõ ràng và tự động kích hoạt các quy trình xem xét bởi con người.
 #13.2.3    Cấp độ: 2    Vai trò: D
 Xác minh rằng các quyết định nhạy cảm về thời gian có các thủ tục dự phòng khi không thể có được sự phê duyệt của con người trong khoảng thời gian yêu cầu.
 #13.2.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các quy trình leo thang xác định rõ các cấp độ quyền hạn cho các loại quyết định hoặc danh mục rủi ro khác nhau, nếu có.

────────────────────────────────────────

### C13.3 Chuỗi Trách Nhiệm & Khả Năng Kiểm Toán

Ghi nhật ký các hành động của người vận hành và các quyết định của mô hình.

 #13.3.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng tất cả các quyết định của hệ thống AI và các can thiệp con người đều được ghi lại với dấu thời gian, danh tính người dùng, và lý do đưa ra quyết định.
 #13.3.2    Cấp độ: 2    Vai trò: D
 Xác minh rằng các nhật ký kiểm toán không thể bị làm giả và bao gồm các cơ chế xác minh tính toàn vẹn.

────────────────────────────────────────

### C13.4 Các kỹ thuật AI có thể giải thích được

Tầm quan trọng của đặc điểm bề mặt, các trường hợp phản thực, và giải thích cục bộ.

 #13.4.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các hệ thống AI cung cấp các giải thích cơ bản cho các quyết định của chúng dưới dạng dễ đọc cho con người.
 #13.4.2    Cấp độ: 2    Vai trò: V
 Xác nhận rằng chất lượng giải thích được kiểm định thông qua các nghiên cứu và chỉ số đánh giá bởi con người.
 #13.4.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các điểm số quan trọng của tính năng hoặc phương pháp gán trách nhiệm (SHAP, LIME, v.v.) có sẵn cho các quyết định quan trọng.
 #13.4.4    Cấp độ: 3    Vai trò: V
 Xác minh rằng các giải thích phản thực cho thấy cách các đầu vào có thể được sửa đổi để thay đổi kết quả, nếu áp dụng được cho trường hợp sử dụng và lĩnh vực.

────────────────────────────────────────

### Thẻ Mô Hình C13.5 & Tiết Lộ Cách Sử Dụng

Duy trì các thẻ mô hình cho mục đích sử dụng, chỉ số hiệu suất và các cân nhắc đạo đức.

 #13.5.1    Cấp độ: 1    Vai trò: D
 Xác minh rằng các thẻ mô hình ghi lại các trường hợp sử dụng dự kiến, giới hạn và các chế độ lỗi đã biết.
 #13.5.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các chỉ số hiệu suất cho các trường hợp sử dụng phù hợp khác nhau đã được công bố.
 #13.5.3    Cấp độ: 2    Vai trò: D
 Xác minh rằng các cân nhắc đạo đức, đánh giá thiên lệch, đánh giá công bằng, đặc điểm dữ liệu huấn luyện và giới hạn dữ liệu huấn luyện đã biết được ghi chép và cập nhật thường xuyên.
 #13.5.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng thẻ mô hình được kiểm soát phiên bản và duy trì trong suốt vòng đời mô hình với việc theo dõi thay đổi.

────────────────────────────────────────

### C13.6 Định lượng sự không chắc chắn

Truyền các điểm tin cậy hoặc các phép đo entropy trong các phản hồi.

 #13.6.1    Cấp độ: 1    Vai trò: D
 Xác minh rằng các hệ thống AI cung cấp điểm tin cậy hoặc các phép đo độ không chắc chắn cùng với kết quả của chúng.
 #13.6.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các ngưỡng không chắc chắn kích hoạt việc xem xét bổ sung bởi con người hoặc các con đường ra quyết định thay thế.
 #13.6.3    Cấp độ: 2    Vai trò: V
 Xác minh rằng các phương pháp định lượng độ không chắc chắn được hiệu chuẩn và xác nhận dựa trên dữ liệu sự thật nền.
 #13.6.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng việc truyền tải độ không chắc chắn được duy trì qua các quy trình làm việc AI nhiều bước.

────────────────────────────────────────

### C13.7 Báo cáo Minh bạch Hướng tới Người dùng

Cung cấp các báo cáo định kỳ về các sự cố, sự sai lệch và việc sử dụng dữ liệu.

 #13.7.1    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng các chính sách sử dụng dữ liệu và quy trình quản lý sự đồng ý của người dùng được truyền đạt rõ ràng đến các bên liên quan.
 #13.7.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các đánh giá tác động AI được thực hiện và kết quả được bao gồm trong báo cáo.
 #13.7.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các báo cáo minh bạch được xuất bản thường xuyên công bố các sự cố AI và các chỉ số hoạt động một cách chi tiết hợp lý.

#### Tài liệu tham khảo

EU Artificial Intelligence Act — Regulation (EU) 2024/1689 (Official Journal, 12 July 2024)
ISO/IEC 23894:2023 — Artificial Intelligence — Guidance on Risk Management
ISO/IEC 42001:2023 — AI Management Systems Requirements
NIST AI Risk Management Framework 1.0
NIST SP 800-53 Revision 5 — Security and Privacy Controls
A Unified Approach to Interpreting Model Predictions (SHAP, ICML 2017)
Model Cards for Model Reporting (Mitchell et al., 2018)
Dropout as a Bayesian Approximation: Representing Model Uncertainty in Deep Learning (Gal & Ghahramani, 2016)
ISO/IEC 24029-2:2023 — Robustness of Neural Networks — Methodology for Formal Methods
IEEE 7001-2021 — Transparency of Autonomous Systems
Human Oversight under Article 14 of the EU AI Act (Fink, 2025)

## Phụ lục A: Bảng thuật ngữ

Bảng thuật ngữ toàn diện này cung cấp định nghĩa của các thuật ngữ quan trọng về AI, ML và bảo mật được sử dụng trong toàn bộ AISVS nhằm đảm bảo sự rõ ràng và hiểu biết chung.

Ví dụ đối kháng: Một đầu vào được tạo ra cố ý nhằm khiến mô hình AI mắc lỗi, thường bằng cách thêm các biến đổi tinh vi mà con người không thể nhận thấy.
​
Độ bền đối kháng – Độ bền đối kháng trong AI đề cập đến khả năng của một mô hình duy trì hiệu suất và chống lại việc bị đánh lừa hoặc thao túng bởi các đầu vào có chủ ý, ác ý được thiết kế để gây ra lỗi.
​
Agent – Các đại lý AI là hệ thống phần mềm sử dụng trí tuệ nhân tạo để theo đuổi mục tiêu và hoàn thành nhiệm vụ thay mặt cho người dùng. Chúng thể hiện khả năng suy luận, lập kế hoạch và ghi nhớ, đồng thời có mức độ tự chủ để đưa ra quyết định, học hỏi và thích nghi.
​
Agentic AI: Hệ thống AI có khả năng hoạt động với một mức độ tự chủ nhất định để đạt được các mục tiêu, thường đưa ra quyết định và thực hiện hành động mà không cần sự can thiệp trực tiếp từ con người.
​
Kiểm soát truy cập dựa trên thuộc tính (ABAC): Một mô hình kiểm soát truy cập trong đó các quyết định cấp quyền dựa trên các thuộc tính của người dùng, tài nguyên, hành động và môi trường, được đánh giá tại thời điểm truy vấn.
​
Tấn công Cửa sau: Một loại tấn công đầu độc dữ liệu, trong đó mô hình được huấn luyện để phản ứng theo cách cụ thể với các tín hiệu kích hoạt nhất định trong khi hành xử bình thường trong các trường hợp khác.
​
Thiên kiến: Sai số hệ thống trong kết quả của mô hình AI có thể dẫn đến kết quả không công bằng hoặc phân biệt đối xử đối với các nhóm nhất định hoặc trong các ngữ cảnh cụ thể.
​
Khai thác Thành kiến: Một kỹ thuật tấn công tận dụng các thành kiến đã biết trong các mô hình AI để thao túng kết quả hoặc đầu ra.
​
Cedar: Ngôn ngữ chính sách và công cụ của Amazon để quản lý quyền truy cập chi tiết được sử dụng trong việc triển khai ABAC cho các hệ thống AI.
​
Chuỗi suy luận: Một kỹ thuật để cải thiện khả năng lập luận trong các mô hình ngôn ngữ bằng cách tạo ra các bước suy luận trung gian trước khi đưa ra câu trả lời cuối cùng.
​
Cầu dao ngắt mạch: Cơ chế tự động dừng hoạt động của hệ thống AI khi vượt quá các ngưỡng rủi ro cụ thể.
​
Dịch vụ suy luận bảo mật: Một dịch vụ suy luận chạy các mô hình AI bên trong môi trường thực thi tin cậy (TEE) hoặc cơ chế tính toán bảo mật tương đương, đảm bảo trọng số mô hình và dữ liệu suy luận vẫn được mã hóa, niêm phong và bảo vệ khỏi truy cập hoặc sửa đổi trái phép.
​
Khối lượng công việc bảo mật: Một khối lượng công việc AI (ví dụ, đào tạo, suy luận, tiền xử lý) được thực hiện bên trong môi trường thực thi đáng tin cậy (TEE) với sự cô lập được hỗ trợ bởi phần cứng, mã hóa bộ nhớ, và xác nhận từ xa nhằm bảo vệ mã, dữ liệu và mô hình khỏi truy cập từ máy chủ chủ hoặc khách thuê cùng.
​
Rò rỉ dữ liệu: Tiết lộ không mong muốn thông tin nhạy cảm thông qua kết quả hoặc hành vi của mô hình AI.
​
Đầu độc dữ liệu: Sự làm hỏng có chủ ý dữ liệu huấn luyện nhằm làm suy yếu tính toàn vẹn của mô hình, thường nhằm cài đặt cửa hậu hoặc giảm hiệu suất.
​
Bảo mật vi phân – Bảo mật vi phân là một khuôn khổ chặt chẽ về mặt toán học để công bố thông tin thống kê về các bộ dữ liệu đồng thời bảo vệ sự riêng tư của từng cá nhân trong dữ liệu. Nó cho phép người sở hữu dữ liệu chia sẻ các mẫu tổng hợp của nhóm trong khi hạn chế thông tin bị rò rỉ về các cá nhân cụ thể.
​
Mã nhúng: Các biểu diễn vectơ đậm đặc của dữ liệu (văn bản, hình ảnh, v.v.) nắm bắt ý nghĩa ngữ nghĩa trong không gian nhiều chiều.
​
Giải thích được – Giải thích được trong AI là khả năng của hệ thống AI cung cấp các lý do mà con người có thể hiểu được cho các quyết định và dự đoán của nó, đồng thời mang lại cái nhìn sâu sắc về hoạt động nội bộ của nó.
​
Trí tuệ nhân tạo có thể giải thích (XAI): Hệ thống AI được thiết kế để cung cấp các giải thích dễ hiểu đối với con người về các quyết định và hành vi của chúng thông qua nhiều kỹ thuật và khung phương pháp khác nhau.
​
Học Liên Liên: Một phương pháp học máy trong đó các mô hình được đào tạo trên nhiều thiết bị phân tán giữ các mẫu dữ liệu cục bộ, mà không trao đổi dữ liệu gốc.
​
Công thức: Công thức hoặc phương pháp được sử dụng để tạo ra một vật phẩm hoặc bộ dữ liệu, chẳng hạn như siêu tham số, cấu hình huấn luyện, các bước tiền xử lý hoặc kịch bản xây dựng.
​
Rào chắn: Những giới hạn được thực hiện nhằm ngăn chặn hệ thống AI tạo ra các kết quả có hại, thiên vị hoặc không mong muốn khác.
​
Ảo giác – Ảo giác AI đề cập đến hiện tượng một mô hình AI tạo ra thông tin không chính xác hoặc gây hiểu lầm, không dựa trên dữ liệu đào tạo hoặc thực tế khách quan.
​
Con người trong vòng lặp (HITL): Hệ thống được thiết kế để yêu cầu sự giám sát, xác minh hoặc can thiệp của con người tại các điểm quyết định quan trọng.
​
Cơ sở hạ tầng dưới dạng Mã (IaC): Quản lý và cung cấp cơ sở hạ tầng thông qua mã thay vì các quy trình thủ công, cho phép quét bảo mật và triển khai nhất quán.
​
Jailbreak: Các kỹ thuật được sử dụng để vượt qua các rào cản an toàn trong hệ thống AI, đặc biệt là trong các mô hình ngôn ngữ lớn, nhằm tạo ra nội dung bị cấm.
​
Nguyên tắc Quyền Tối thiểu: Nguyên tắc bảo mật chỉ cấp quyền truy cập cần thiết tối thiểu cho người dùng và các tiến trình.
​
LIME (Giải thích Độc lập Mô hình Cục bộ): Một kỹ thuật để giải thích các dự đoán của bất kỳ bộ phân loại học máy nào bằng cách xấp xỉ cục bộ nó với một mô hình có thể giải thích được.
​
Tấn công suy luận thành viên: Một cuộc tấn công nhằm xác định xem một điểm dữ liệu cụ thể có được sử dụng để huấn luyện mô hình học máy hay không.
​
MITRE ATLAS: Bản đồ mối đe dọa đối kháng cho các hệ thống Trí tuệ Nhân tạo; một cơ sở kiến thức về các chiến thuật và kỹ thuật đối kháng chống lại các hệ thống AI.
​
Thẻ Mô Hình – Thẻ mô hình là một tài liệu cung cấp thông tin tiêu chuẩn về hiệu suất, giới hạn, mục đích sử dụng và các cân nhắc đạo đức của một mô hình AI nhằm thúc đẩy tính minh bạch và phát triển AI có trách nhiệm.
​
Trích xuất mô hình: Một cuộc tấn công mà kẻ thù liên tục truy vấn một mô hình mục tiêu để tạo ra một bản sao có chức năng tương tự mà không được phép.
​
Mô hình Đảo ngược: Một cuộc tấn công nhằm cố gắng tái tạo dữ liệu đào tạo bằng cách phân tích đầu ra của mô hình.
​
Quản lý Vòng đời Mô hình – Quản lý vòng đời mô hình AI là quá trình giám sát tất cả các giai đoạn tồn tại của một mô hình AI, bao gồm thiết kế, phát triển, triển khai, giám sát, bảo trì và cuối cùng là ngừng sử dụng, nhằm đảm bảo mô hình luôn hiệu quả và phù hợp với các mục tiêu.
​
Đầu độc mô hình: Giới thiệu các lỗ hổng hoặc cổng sau trực tiếp vào mô hình trong quá trình huấn luyện.
​
Đánh cắp/Mạo danh Mô hình: Trích xuất một bản sao hoặc bản xấp xỉ của một mô hình độc quyền thông qua các truy vấn lặp đi lặp lại.
​
Hệ thống đa tác nhân: Một hệ thống được tạo thành từ nhiều tác nhân AI tương tác với nhau, mỗi tác nhân có thể có khả năng và mục tiêu khác nhau.
​
OPA (Open Policy Agent): Một công cụ chính sách mã nguồn mở cho phép thực thi chính sách thống nhất trên toàn bộ hệ thống.
​
Nguồn gốc: Dòng dõi và chuỗi bảo quản của một hiện vật hoặc bộ dữ liệu, bao gồm nguồn gốc, người xử lý, đường dẫn chuyển giao và bằng chứng về tính toàn vẹn (ví dụ: mã kiểm tra, chữ ký).
​
Học máy bảo vệ quyền riêng tư (PPML): Các kỹ thuật và phương pháp để huấn luyện và triển khai các mô hình học máy trong khi bảo vệ quyền riêng tư của dữ liệu huấn luyện.
​
Tiêm nhiễm Lệnh nhắc: Một cuộc tấn công nơi các chỉ thị độc hại được chèn vào đầu vào nhằm ghi đè hành vi dự định của mô hình.
​
RAG (Tạo Sinh Tăng Cường Truy Xuất): Một kỹ thuật nâng cao các mô hình ngôn ngữ lớn bằng cách truy xuất thông tin liên quan từ các nguồn kiến thức bên ngoài trước khi tạo ra phản hồi.
​
Red-Teaming: Thực hành kiểm tra hệ thống AI một cách chủ động bằng cách mô phỏng các cuộc tấn công đối nghịch để xác định các điểm yếu.
​
SLSA Provenance: Siêu dữ liệu được định nghĩa bởi khung SLSA để ghi lại nơi, thời gian và cách thức một sản phẩm được tạo ra (ví dụ: kho nguồn, mã hash commit, hệ thống xây dựng và các tham số).
​
SBOM (Danh Mục Vật Liệu Phần Mềm): Một hồ sơ chính thức chứa các chi tiết và quan hệ chuỗi cung ứng của các thành phần khác nhau được sử dụng trong việc xây dựng phần mềm hoặc mô hình AI.
​
SHAP (Giải thích cộng thêm Shapley): Một phương pháp dựa trên lý thuyết trò chơi để giải thích đầu ra của bất kỳ mô hình học máy nào bằng cách tính toán đóng góp của từng đặc trưng vào dự đoán.
​
Xác thực mạnh: Xác thực chống lại việc đánh cắp thông tin đăng nhập và phát lại bằng cách yêu cầu ít nhất hai yếu tố (kiến thức, sở hữu, bản chất) và các cơ chế chống lừa đảo như FIDO2/WebAuthn, xác thực dịch vụ dựa trên chứng chỉ, hoặc token có thời gian sống ngắn.
​
Tấn công chuỗi cung ứng: Xâm nhập vào hệ thống bằng cách nhắm mục tiêu vào các thành phần có bảo mật kém hơn trong chuỗi cung ứng của nó, chẳng hạn như thư viện bên thứ ba, bộ dữ liệu hoặc mô hình đã được huấn luyện trước.
​
Học chuyển giao: Một kỹ thuật trong đó một mô hình được phát triển cho một nhiệm vụ được tái sử dụng làm điểm khởi đầu cho một mô hình trên một nhiệm vụ thứ hai.
​
Cơ sở dữ liệu Vector: Một cơ sở dữ liệu chuyên biệt được thiết kế để lưu trữ các vector đa chiều cao (embedding) và thực hiện tìm kiếm tương tự hiệu quả.
​
Quét lỗ hổng bảo mật: Các công cụ tự động xác định các lỗ hổng bảo mật đã biết trong các thành phần phần mềm, bao gồm cả các khung AI và các phụ thuộc.
​
Đóng dấu bản quyền: Các kỹ thuật nhúng các dấu hiệu không thể nhận biết trong nội dung do AI tạo ra để theo dõi nguồn gốc hoặc phát hiện việc tạo nội dung bằng AI.
​
Lỗ hổng Zero-Day: Một lỗ hổng chưa được biết đến trước đây mà kẻ tấn công có thể khai thác trước khi các nhà phát triển tạo và triển khai bản vá.

## Phụ lục B: Tài liệu tham khảo

### Cần làm

## Phụ lục C: Quản trị và Tài liệu An ninh AI (Tổ chức lại)

### Mục tiêu

Phụ lục này cung cấp các yêu cầu cơ bản để thiết lập cấu trúc tổ chức, chính sách, tài liệu và quy trình nhằm quản lý an ninh AI trong suốt vòng đời của hệ thống.

────────────────────────────────────────

### AC.1 Khung Quản lý Rủi ro AI được Áp dụng

 #AC.1.1    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng một phương pháp đánh giá rủi ro đặc thù cho AI đã được tài liệu hóa và triển khai.
 #AC.1.2    Cấp độ: 2    Vai trò: D
 Xác minh rằng các đánh giá rủi ro được tiến hành tại các điểm then chốt trong vòng đời AI và trước khi có các thay đổi quan trọng.
 #AC.1.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng khung quản lý rủi ro phù hợp với các tiêu chuẩn đã được thiết lập (ví dụ: NIST AI RMF).

────────────────────────────────────────

### AC.2 Chính sách & Quy trình An ninh AI

 #AC.2.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các chính sách bảo mật AI đã được tài liệu hóa tồn tại.
 #AC.2.2    Cấp độ: 2    Vai trò: D
 Xác minh rằng các chính sách được xem xét và cập nhật ít nhất hàng năm và sau những thay đổi đáng kể trong bối cảnh mối đe dọa.
 #AC.2.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các chính sách bao quát tất cả các danh mục AISVS và các yêu cầu quy định áp dụng.

────────────────────────────────────────

### AC.3 Vai Trò & Trách Nhiệm cho An Ninh AI

 #AC.3.1    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng các vai trò và trách nhiệm về bảo mật AI đã được ghi lại.
 #AC.3.2    Cấp độ: 2    Vai trò: D
 Xác minh rằng các cá nhân chịu trách nhiệm có chuyên môn về an ninh phù hợp.
 #AC.3.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng một ủy ban đạo đức AI hoặc ban quản trị được thành lập cho các hệ thống AI có rủi ro cao.

────────────────────────────────────────

### AC.4 Thực thi Hướng dẫn Đạo đức AI

 #AC.4.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các hướng dẫn đạo đức cho phát triển và triển khai AI đã tồn tại.
 #AC.4.2    Cấp độ: 2    Vai trò: D
 Xác minh rằng các cơ chế đã được thiết lập để phát hiện và báo cáo các vi phạm đạo đức.
 #AC.4.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các đánh giá đạo đức định kỳ đối với các hệ thống AI đã triển khai được thực hiện.

────────────────────────────────────────

### Giám sát Tuân thủ Quy định AI AC.5

 #AC.5.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng có các quy trình để xác định các quy định AI áp dụng.
 #AC.5.2    Cấp độ: 2    Vai trò: D
 Xác minh rằng việc tuân thủ tất cả các yêu cầu quy định đã được đánh giá.
 #AC.5.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các thay đổi quy định kích hoạt các đánh giá và cập nhật hệ thống AI kịp thời.

────────────────────────────────────────

### AC.6 Quản trị Dữ liệu Đào tạo, Tài liệu & Quy trình

#### AC.6.1 Nguồn dữ liệu & Thẩm định kỹ lưỡng

 #AC.6.1.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng chỉ các tập dữ liệu đã được kiểm duyệt về chất lượng, tính đại diện, nguồn gốc đạo đức và tuân thủ giấy phép được phép sử dụng, nhằm giảm thiểu rủi ro về đầu độc dữ liệu, thiên vị ẩn và vi phạm sở hữu trí tuệ.
 #AC.6.1.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các nhà cung cấp dữ liệu bên thứ ba, bao gồm các nhà cung cấp mô hình đã được huấn luyện trước và bộ dữ liệu bên ngoài, đều trải qua quá trình thẩm định về bảo mật, quyền riêng tư, nguồn gốc đạo đức và chất lượng dữ liệu trước khi dữ liệu hoặc mô hình của họ được tích hợp.
 #AC.6.1.3    Cấp độ: 1    Vai trò: D
 Xác minh rằng các chuyển khoản ngoài sử dụng TLS/xác thực và kiểm tra toàn vẹn.
 #AC.6.1.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các nguồn dữ liệu có rủi ro cao (ví dụ: bộ dữ liệu mã nguồn mở có nguồn gốc không rõ, nhà cung cấp chưa được kiểm duyệt) được kiểm tra kỹ lưỡng hơn, chẳng hạn như phân tích trong môi trường cách ly, kiểm tra chất lượng/thiên vị kỹ lưỡng và phát hiện đầu độc có mục tiêu, trước khi sử dụng trong các ứng dụng nhạy cảm.
 #AC.6.1.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các mô hình đã được đào tạo sẵn lấy từ bên thứ ba được đánh giá về các thiên vị nhúng, khả năng có cửa hậu, tính toàn vẹn của kiến trúc và nguồn gốc của dữ liệu đào tạo gốc trước khi tinh chỉnh hoặc triển khai.

#### AC.6.2 Quản lý Độ thiên vị & Công bằng

 #AC.6.2.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các tập dữ liệu đã được phân tích về sự mất cân đối đại diện và các thiên kiến tiềm ẩn trên các thuộc tính được bảo vệ theo pháp luật (ví dụ, chủng tộc, giới tính, tuổi tác) và các đặc điểm nhạy cảm về mặt đạo đức khác liên quan đến lĩnh vực ứng dụng của mô hình (ví dụ, tình trạng kinh tế-xã hội, vị trí địa lý).
 #AC.6.2.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các thiên vị được xác định đã được giảm thiểu thông qua các chiến lược được ghi chép như cân bằng lại, tăng cường dữ liệu có mục tiêu, điều chỉnh thuật toán (ví dụ: các kỹ thuật tiền xử lý, xử lý trong quá trình, xử lý sau) hoặc tái phân bổ trọng số, và đánh giá tác động của việc giảm thiểu đối với cả độ công bằng và hiệu suất tổng thể của mô hình.
 #AC.6.2.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các chỉ số công bằng sau đào tạo được đánh giá và ghi chép lại.
 #AC.6.2.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng chính sách quản lý thiên vị trong vòng đời gán quyền sở hữu và tần suất xem xét.

#### AC.6.3 Quản trị Gán nhãn & Ghi chú

 #AC.6.3.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng chất lượng gán nhãn/chú thích được đảm bảo thông qua việc kiểm tra chéo hoặc sự đồng thuận của người đánh giá.
 #AC.6.3.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các thẻ dữ liệu được duy trì cho các tập dữ liệu đào tạo quan trọng, chi tiết các đặc điểm, động cơ, thành phần, quy trình thu thập, tiền xử lý, giấy phép và các mục đích sử dụng được khuyến nghị/không khuyến nghị.
 #AC.6.3.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các thẻ dữ liệu ghi chép các rủi ro thiên vị, lệch lạc dân số học và các cân nhắc đạo đức liên quan đến bộ dữ liệu.
 #AC.6.3.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các thẻ dữ liệu được phân phiên bản cùng với các tập dữ liệu và được cập nhật mỗi khi tập dữ liệu bị sửa đổi.
 #AC.6.3.5    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các thẻ dữ liệu đã được xem xét và phê duyệt bởi cả các bên liên quan kỹ thuật và phi kỹ thuật (ví dụ: bộ phận tuân thủ, đạo đức, chuyên gia lĩnh vực).
 #AC.6.3.6    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng chất lượng gán nhãn/chú thích được đảm bảo thông qua các hướng dẫn rõ ràng, việc kiểm tra chéo giữa các người đánh giá, các cơ chế đồng thuận (ví dụ, theo dõi sự đồng thuận giữa các người chú thích), và các quy trình xác định để giải quyết những khác biệt.
 #AC.6.3.7    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các nhãn quan trọng đối với an toàn, bảo mật hoặc công bằng (ví dụ: xác định nội dung độc hại, phát hiện y tế quan trọng) phải được xem xét lại bắt buộc bởi hai bên độc lập hoặc có phương pháp xác minh mạnh mẽ tương đương.
 #AC.6.3.8    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các hướng dẫn và chỉ dẫn dán nhãn đầy đủ, được kiểm soát phiên bản và được đồng nghiệp đánh giá.
 #AC.6.3.9    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các sơ đồ dữ liệu cho nhãn được định nghĩa rõ ràng và được kiểm soát phiên bản.
 #AC.6.3.10    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các quy trình làm việc gán nhãn thuê ngoài hoặc dùng đám đông bao gồm các biện pháp kỹ thuật/thuật procedural để đảm bảo tính bảo mật dữ liệu, tính toàn vẹn, chất lượng nhãn và ngăn ngừa rò rỉ dữ liệu.
 #AC.6.3.11    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng tất cả nhân sự tham gia chú thích dữ liệu đều được kiểm tra lý lịch và đào tạo về an ninh dữ liệu và quyền riêng tư.
 #AC.6.3.12    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng tất cả nhân viên chú thích đã ký các thỏa thuận bảo mật và không tiết lộ thông tin.
 #AC.6.3.13    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các nền tảng chú thích thực thi kiểm soát truy cập và theo dõi các mối đe dọa nội bộ.

#### AC.6.4 Cổng chất lượng bộ dữ liệu & Cách ly

 #AC.6.4.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các bộ dữ liệu thất bại được cách ly với dấu vết kiểm toán.
 #AC.6.4.2    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng các cổng chất lượng sẽ chặn các tập dữ liệu kém chất lượng trừ khi có sự chấp thuận ngoại lệ.
 #AC.6.4.3    Cấp độ: 2    Vai trò: V
 Xác minh rằng việc kiểm tra ngẫu nhiên thủ công bởi các chuyên gia trong lĩnh vực bao phủ một mẫu thống kê có ý nghĩa (ví dụ, ≥1% hoặc 1.000 mẫu, tùy theo giá trị lớn hơn, hoặc theo kết quả đánh giá rủi ro) để phát hiện các vấn đề chất lượng tinh vi mà tự động hóa không phát hiện được.

#### AC.6.5 Phát hiện Mối đe dọa/Tấn công Độc hại & Trôi dữ liệu

 #AC.6.5.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các mẫu bị đánh dấu kích hoạt xem xét thủ công trước khi đào tạo.
 #AC.6.5.2    Cấp độ: 2    Vai trò: V
 Xác minh rằng kết quả được cung cấp cho hồ sơ bảo mật của mô hình và thông báo cho tình báo mối đe dọa liên tục.
 #AC.6.5.3    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng logic phát hiện được làm mới với thông tin tình báo mối đe dọa mới.
 #AC.6.5.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các pipeline học trực tuyến giám sát sự dịch chuyển phân phối dữ liệu.

#### AC.6.6 Xóa bỏ, Đồng ý, Quyền, Lưu trữ & Tuân thủ

 #AC.6.6.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng quy trình xóa dữ liệu đào tạo đã xóa sạch dữ liệu gốc và dữ liệu dẫn xuất, đồng thời đánh giá ảnh hưởng lên mô hình, và rằng ảnh hưởng đối với các mô hình bị ảnh hưởng được đánh giá và, nếu cần thiết, được giải quyết (ví dụ, thông qua việc đào tạo lại hoặc hiệu chỉnh lại).
 #AC.6.6.2    Cấp độ: 2    Vai trò: D
 Xác minh rằng các cơ chế đã được thiết lập để theo dõi và tôn trọng phạm vi cũng như trạng thái của sự đồng ý của người dùng (và các rút lui) đối với dữ liệu sử dụng trong việc huấn luyện, và rằng sự đồng ý được xác thực trước khi dữ liệu được tích hợp vào các quy trình huấn luyện mới hoặc các cập nhật quan trọng của mô hình.
 #AC.6.6.3    Cấp độ: 2    Vai trò: V
 Xác minh rằng các quy trình làm việc được kiểm tra hàng năm và ghi lại.
 #AC.6.6.4    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các khoảng thời gian lưu giữ rõ ràng đã được xác định cho tất cả các tập dữ liệu đào tạo.
 #AC.6.6.5    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các bộ dữ liệu tự động hết hạn, bị xóa hoặc được xem xét để xóa khi kết thúc vòng đời của chúng.
 #AC.6.6.6    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các hành động giữ lại và xóa dữ liệu được ghi lại và có thể kiểm tra.
 #AC.6.6.7    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các yêu cầu về cư trú dữ liệu và chuyển giao xuyên biên giới được xác định và thực thi cho tất cả các bộ dữ liệu.
 #AC.6.6.8    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các quy định đặc thù theo ngành (ví dụ: chăm sóc sức khỏe, tài chính) đã được xác định và xử lý trong việc quản lý dữ liệu.
 #AC.6.6.9    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng việc tuân thủ các luật về quyền riêng tư liên quan (ví dụ, GDPR, CCPA) được ghi chép và xem xét thường xuyên.
 #AC.6.6.10    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng có các cơ chế để phản hồi các yêu cầu của chủ thể dữ liệu về quyền truy cập, chỉnh sửa, hạn chế hoặc phản đối.
 #AC.6.6.11    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các yêu cầu được ghi lại, theo dõi và hoàn thành trong khoảng thời gian được quy định bởi pháp luật.
 #AC.6.6.12    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng các quy trình quyền của chủ thể dữ liệu được kiểm tra và xem xét định kỳ để đảm bảo hiệu quả.

#### AC.6.7 Quản lý Phiên bản & Thay đổi

 #AC.6.7.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng một phân tích tác động được thực hiện trước khi cập nhật hoặc thay thế phiên bản tập dữ liệu, bao gồm hiệu suất mô hình, tính công bằng và tuân thủ.
 #AC.6.7.2    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng kết quả của phân tích tác động đã được ghi chép và xem xét bởi các bên liên quan phù hợp.
 #AC.6.7.3    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng kế hoạch khôi phục tồn tại trong trường hợp các phiên bản mới gây ra các rủi ro hoặc suy giảm không chấp nhận được.

#### Quản trị Dữ liệu Tổng hợp AC.6.8

 #AC.6.8.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng quy trình tạo dữ liệu tổng hợp, các tham số và mục đích sử dụng dự kiến của dữ liệu tổng hợp được ghi chép đầy đủ.
 #AC.6.8.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng dữ liệu tổng hợp đã được đánh giá rủi ro về thiên vị, rò rỉ quyền riêng tư và các vấn đề đại diện trước khi sử dụng trong huấn luyện.

#### AC.6.9 Giám sát truy cập

 #AC.6.9.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các nhật ký truy cập được xem xét thường xuyên để phát hiện các mẫu bất thường, chẳng hạn như xuất khẩu lớn hoặc truy cập từ các địa điểm mới.
 #AC.6.9.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các cảnh báo được tạo ra cho các sự kiện truy cập đáng ngờ và được điều tra kịp thời.

#### AC.6.10 Quản lý Đào tạo Đối kháng

 #AC.6.10.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng nếu sử dụng huấn luyện đối kháng, việc tạo ra, quản lý và phiên bản hóa các bộ dữ liệu đối kháng được ghi chép và kiểm soát.
 #AC.6.10.2    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng tác động của việc huấn luyện độ bền chống đối kháng lên hiệu suất mô hình (đối với cả đầu vào sạch và đầu vào chống đối kháng) cũng như các chỉ số công bằng được đánh giá, ghi chép và theo dõi.
 #AC.6.10.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các chiến lược đào tạo đối kháng và độ bền vững được xem xét và cập nhật định kỳ để đối phó với các kỹ thuật tấn công đối kháng ngày càng phát triển.

────────────────────────────────────────

### AC.7 Quản lý Vòng đời Mô hình & Tài liệu

 #AC.7.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng tất cả các artifact mô hình sử dụng phiên bản ngữ nghĩa (MAJOR.MINOR.PATCH) với các tiêu chí được ghi chép rõ ràng xác định khi nào mỗi thành phần phiên bản được tăng lên.
 #AC.7.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các triển khai khẩn cấp yêu cầu có đánh giá rủi ro bảo mật được ghi chép và được sự phê duyệt từ cơ quan bảo mật được chỉ định trước trong khoảng thời gian đã được thỏa thuận trước.
 #AC.7.3    Cấp độ: 2    Vai trò: V
 Xác minh rằng các bản ghi khôi phục (phiên bản mô hình trước đó, cấu hình, phụ thuộc) được giữ lại theo chính sách của tổ chức.
 #AC.7.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng việc truy cập nhật ký kiểm toán yêu cầu sự ủy quyền phù hợp và tất cả các lần cố gắng truy cập đều được ghi lại với danh tính người dùng và dấu thời gian.
 #AC.7.5    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các bản mẫu mô hình đã nghỉ hưu được giữ lại theo chính sách lưu trữ dữ liệu.

────────────────────────────────────────

### Quản trị An toàn Lời nhắc, Đầu vào và Đầu ra AC.8

#### AC.8.1 Phòng chống tiêm nhiễm lệnh (Prompt Injection Defense)

 #AC.8.1.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các bài kiểm tra đánh giá đối kháng (ví dụ: các lời nhắc "many-shot" của Đội Đỏ) được thực hiện trước mỗi lần phát hành mô hình hoặc mẫu lời nhắc, với các ngưỡng tỷ lệ thành công và các bộ chặn tự động đối với các hồi quy.
 #AC.8.1.2    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng tất cả các cập nhật quy tắc lọc lời nhắc, phiên bản mô hình phân loại và thay đổi danh sách chặn đều được kiểm soát phiên bản và có thể kiểm tra.

#### AC.8.2 Kháng lại Ví dụ Đối kháng

 #AC.8.2.1    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các chỉ số độ bền (tỷ lệ thành công của các bộ tấn công đã biết) được theo dõi theo thời gian thông qua tự động hóa và các lỗi hồi quy kích hoạt cảnh báo.

#### AC.8.3 Kiểm tra Nội dung & Chính sách

 #AC.8.3.1    Cấp độ: 2    Vai trò: D
 Xác minh rằng mô hình sàng lọc hoặc bộ quy tắc được đào tạo lại/cập nhật ít nhất mỗi quý, bao gồm các mẫu phá vỡ giới hạn hoặc bỏ qua chính sách mới được quan sát.

#### AC.8.4 Giới hạn tốc độ đầu vào & Ngăn chặn lạm dụng

 #AC.8.4.1    Cấp độ: 3    Vai trò: V
 Xác minh rằng các bản ghi phòng ngừa lạm dụng được giữ lại và xem xét để phát hiện các mẫu tấn công mới xuất hiện.

#### AC.8.5 Nguồn gốc và Ghi nhận Đầu vào

 #AC.8.5.1    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng tất cả các đầu vào của người dùng đều được gắn thẻ với siêu dữ liệu (ID người dùng, phiên, nguồn, dấu thời gian, địa chỉ IP) khi nhập liệu.
 #AC.8.5.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng siêu dữ liệu nguồn gốc được giữ lại và có thể kiểm tra được cho tất cả các đầu vào đã xử lý.
 #AC.8.5.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các nguồn đầu vào bất thường hoặc không đáng tin cậy được đánh dấu và bị xem xét kỹ lưỡng hoặc chặn lại.

────────────────────────────────────────

### AC.9 Xác thực đa phương thức, MLOps & Quản trị Hạ tầng

#### AC.9.1 Quy trình xác thực bảo mật đa phương thức

 #AC.9.1.1    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các bộ phân loại nội dung theo từng phương thức được cập nhật theo lịch trình đã được ghi chép (tối thiểu hàng quý) với các mẫu mối đe dọa mới, ví dụ đối kháng, và các tiêu chuẩn hiệu suất được duy trì trên mức ngưỡng cơ sở.

#### AC.9.2 Bảo mật CI/CD và xây dựng

 #AC.9.2.1    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng mã hạ tầng như mã được quét trên mỗi lần commit, và các lần hợp nhất bị chặn khi có các phát hiện với mức độ nghiêm trọng cao hoặc rất cao.
 #AC.9.2.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các pipeline CI/CD sử dụng các danh tính có thời gian tồn tại ngắn và phạm vi hạn chế để truy cập vào bí mật và cơ sở hạ tầng.
 #AC.9.2.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các môi trường xây dựng được cách ly với mạng lưới và dữ liệu sản xuất.

#### AC.9.3 An ninh Container & Hình ảnh

 #AC.9.3.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các hình ảnh container được quét để chặn các bí mật mã cứng (ví dụ: khóa API, thông tin xác thực, chứng chỉ).
 #AC.9.3.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các hình ảnh container được quét theo lịch trình của tổ chức với các lỗ hổng CRITICAL chặn việc triển khai dựa trên ngưỡng rủi ro của tổ chức.

#### AC.9.4 Giám sát, Cảnh báo & SIEM

 #AC.9.4.1    Cấp độ: 2    Vai trò: V
 Xác nhận rằng các cảnh báo bảo mật tích hợp với các nền tảng SIEM (Splunk, Elastic hoặc Sentinel) sử dụng định dạng CEF hoặc STIX/TAXII với việc làm giàu tự động.

#### AC.9.5 Quản lý Lỗ hổng Bảo mật

 #AC.9.5.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các lỗ hổng nghiêm trọng cao được vá theo các mốc thời gian quản lý rủi ro của tổ chức với các quy trình khẩn cấp dành cho các CVE đang bị khai thác tích cực.

#### AC.9.6 Cấu hình & Kiểm soát Trôi Drift

 #AC.9.6.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng hiện tượng lệch cấu hình được phát hiện bằng các công cụ (Chef InSpec, AWS Config) theo yêu cầu giám sát của tổ chức với khả năng tự động phục hồi cho các thay đổi không được phép.

#### AC.9.7 Tăng cường bảo mật Môi trường Sản xuất

 #AC.9.7.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các môi trường sản xuất chặn truy cập SSH, vô hiệu hóa các điểm cuối debug và yêu cầu các yêu cầu thay đổi với các yêu cầu thông báo trước tổ chức, trừ trường hợp khẩn cấp.

#### Cổng Kiểm Soát Quảng Bá Phiên Bản AC.9.8

 #AC.9.8.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các cổng thăng tiến bao gồm các bài kiểm tra bảo mật tự động (SAST, DAST, quét container) với yêu cầu không có phát hiện CRITICAL để được phê duyệt.

#### AC.9.9 Giám sát Khối lượng công việc, Công suất và Chi phí

 #AC.9.9.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng việc sử dụng GPU/TPU được giám sát với cảnh báo được kích hoạt khi vượt ngưỡng do tổ chức định nghĩa và tự động mở rộng quy mô hoặc cân bằng tải được kích hoạt dựa trên các chính sách quản lý công suất.
 #AC.9.9.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các chỉ số tải công việc AI (độ trễ suy luận, thông lượng, tỷ lệ lỗi) được thu thập theo yêu cầu giám sát tổ chức và được đối chiếu với mức sử dụng hạ tầng.
 #AC.9.9.3    Cấp độ: 2    Vai trò: V
 Xác nhận rằng việc giám sát chi phí theo dõi chi tiêu theo từng khối lượng công việc/người thuê với các cảnh báo dựa trên ngưỡng ngân sách tổ chức và các kiểm soát tự động cho các trường hợp vượt ngân sách.
 #AC.9.9.4    Cấp độ: 3    Vai trò: V
 Xác nhận rằng lập kế hoạch năng lực sử dụng dữ liệu lịch sử với các khoảng thời gian dự báo được định nghĩa bởi tổ chức và cung cấp tài nguyên tự động dựa trên các mẫu nhu cầu.

#### AC.9.10 Phê duyệt & Dấu vết kiểm toán

 #AC.9.10.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng việc thăng cấp môi trường yêu cầu sự phê duyệt từ nhân sự được tổ chức xác định có thẩm quyền, kèm theo chữ ký mật mã và các hồ sơ kiểm toán không thể thay đổi.

#### AC.9.11 Quản trị IaC

 #AC.9.11.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các thay đổi hạ tầng như mã nguồn yêu cầu xem xét đồng cấp kèm theo kiểm tra tự động và quét bảo mật trước khi gộp vào nhánh chính.

#### AC.9.12 Xử lý Dữ liệu trong Môi trường Phi Sản xuất

 #AC.9.12.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng dữ liệu không phục vụ sản xuất đã được ẩn danh theo các yêu cầu về quyền riêng tư của tổ chức, việc tạo dữ liệu tổng hợp hoặc che giấu dữ liệu hoàn toàn với việc loại bỏ thông tin nhận dạng cá nhân (PII) đã được xác minh.

#### AC.9.13 Sao lưu & Phục hồi sau thảm họa

 #AC.9.13.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các cấu hình hạ tầng được sao lưu theo lịch sao lưu của tổ chức tới các vùng địa lý tách biệt với việc triển khai chiến lược sao lưu 3-2-1.
 #AC.9.13.2    Cấp độ: 2    Vai trò: V
 Xác minh rằng các quy trình phục hồi được kiểm tra và xác thực thông qua kiểm thử tự động theo lịch trình của tổ chức với các mục tiêu RTO và RPO đáp ứng yêu cầu của tổ chức.
 #AC.9.13.3    Cấp độ: 3    Vai trò: V
 Xác nhận rằng kế hoạch phục hồi thảm họa bao gồm các sổ tay chạy riêng cho AI với việc khôi phục trọng số mô hình, xây dựng lại cụm GPU và lập bản đồ phụ thuộc dịch vụ.

#### Tuân thủ & Tài liệu AC.9.14

 #AC.9.14.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng việc đánh giá tuân thủ hạ tầng được thực hiện theo lịch trình của tổ chức dựa trên các kiểm soát SOC 2, ISO 27001 hoặc FedRAMP với việc thu thập bằng chứng tự động.
 #AC.9.14.2    Cấp độ: 2    Vai trò: V
 Xác minh rằng tài liệu hạ tầng bao gồm sơ đồ mạng, bản đồ luồng dữ liệu và mô hình đe dọa được cập nhật theo yêu cầu quản lý thay đổi tổ chức.
 #AC.9.14.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các thay đổi cơ sở hạ tầng trải qua đánh giá tác động tuân thủ tự động với quy trình phê duyệt theo quy định cho các sửa đổi có rủi ro cao.

#### AC.9.15 Phần cứng & Chuỗi cung ứng

 #AC.9.15.1    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng firmware của bộ tăng tốc AI (BIOS GPU, firmware TPU) được xác minh bằng chữ ký mật mã và được cập nhật theo các mốc thời gian quản lý bản vá của tổ chức.
 #AC.9.15.2    Cấp độ: 3    Vai trò: V
 Xác minh rằng chuỗi cung ứng phần cứng AI bao gồm việc kiểm tra nguồn gốc với giấy chứng nhận của nhà sản xuất và xác nhận bao bì chống giả mạo.

#### AC.9.16 Chiến lược Điện toán đám mây & Khả năng di động

 #AC.9.16.1    Cấp độ: 3    Vai trò: V
 Xác minh rằng việc ngăn ngừa khóa nhà cung cấp đám mây bao gồm cơ sở hạ tầng dưới dạng mã có thể di động, các API tiêu chuẩn hóa, và khả năng xuất dữ liệu với các công cụ chuyển đổi định dạng.
 #AC.9.16.2    Cấp độ: 3    Vai trò: V
 Xác minh rằng tối ưu hóa chi phí đa đám mây bao gồm các kiểm soát bảo mật ngăn chặn sự lan tràn tài nguyên cũng như các khoản phí chuyển dữ liệu không được phép giữa các đám mây.

#### AC.9.17 GitOps & Tự phục hồi

 #AC.9.17.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các kho GitOps yêu cầu các cam kết được ký bằng khóa GPG và các quy tắc bảo vệ nhánh ngăn chặn việc đẩy trực tiếp lên các nhánh chính.
 #AC.9.17.2    Cấp độ: 3    Vai trò: V
 Xác minh rằng cơ sở hạ tầng tự phục hồi bao gồm việc tương quan sự kiện bảo mật với phản hồi sự cố tự động và các quy trình thông báo cho các bên liên quan.

#### AC.9.18 Zero-Trust, Đại lý, Cấp phát & Xác nhận Cư trú

 #AC.9.18.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng truy cập tài nguyên đám mây bao gồm xác thực không-trust với xác thực liên tục.
 #AC.9.18.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng việc cung cấp hạ tầng tự động bao gồm việc kiểm tra chính sách bảo mật với việc chặn triển khai đối với các cấu hình không tuân thủ.
 #AC.9.18.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng việc cung cấp hạ tầng tự động kiểm tra các chính sách bảo mật trong quá trình CI/CD, với các cấu hình không tuân thủ bị chặn khỏi việc triển khai.
 #AC.9.18.4    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng các yêu cầu về cư trú dữ liệu được thực thi thông qua việc chứng thực mã hóa vị trí lưu trữ.
 #AC.9.18.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các đánh giá bảo mật của nhà cung cấp đám mây bao gồm mô hình hóa mối đe dọa và đánh giá rủi ro cụ thể cho từng tác nhân.

#### AC.9.19 Kiểm soát truy cập & Danh tính

 #5.1.3    Cấp độ: 2    Vai trò: D
 Xác minh rằng các cán bộ mới trải qua quy trình chứng thực danh tính phù hợp với tiêu chuẩn NIST 800-63-3 IAL-2 hoặc tiêu chuẩn tương đương trước khi được cấp quyền truy cập hệ thống sản xuất.
 #5.1.4    Cấp độ: 2    Vai trò: V
 Xác minh rằng các đánh giá truy cập được thực hiện hàng quý với việc phát hiện tự động các tài khoản không hoạt động, thực thi xoay vòng chứng chỉ và các quy trình gỡ bỏ quyền truy cập.
 #5.2.2    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng các nguyên tắc quyền hạn tối thiểu được áp dụng mặc định với các tài khoản dịch vụ bắt đầu từ quyền chỉ đọc và yêu cầu có lý do kinh doanh được ghi chép rõ ràng để được quyền ghi.
 #5.3.3    Cấp độ: 2    Vai trò: D
 Xác nhận rằng các định nghĩa chính sách được kiểm soát phiên bản, được đồng nghiệp xem xét, và được xác thực thông qua kiểm thử tự động trong các pipeline CI/CD trước khi triển khai sản xuất.
 #5.3.4    Cấp độ: 2    Vai trò: V
 Xác minh rằng kết quả đánh giá chính sách bao gồm các lý do quyết định và được truyền tới hệ thống SIEM để phân tích tương quan và báo cáo tuân thủ.
 #5.4.4    Cấp độ: 2    Vai trò: V
 Xác nhận rằng độ trễ đánh giá chính sách được theo dõi liên tục với các cảnh báo tự động cho các điều kiện hết thời gian có thể cho phép vượt qua xác thực.
 #5.5.4    Cấp độ: 2    Vai trò: V
 Xác minh rằng các thuật toán che giấu thông tin là xác định, được kiểm soát phiên bản và duy trì nhật ký kiểm toán để hỗ trợ điều tra tuân thủ và phân tích pháp y.
 #5.5.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng các sự kiện ẩn dữ liệu có rủi ro cao tạo ra nhật ký thích ứng bao gồm các hàm băm mật mã của nội dung gốc để truy xuất pháp y mà không làm lộ dữ liệu.
 #5.7.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng các điều kiện lỗi của tác nhân và xử lý ngoại lệ bao gồm thông tin phạm vi khả năng để hỗ trợ phân tích sự cố và điều tra pháp y.
 #5.4.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các trích dẫn, tham chiếu và nguồn gốc trong kết quả của mô hình được kiểm tra theo quyền hạn của người gọi và loại bỏ nếu phát hiện truy cập trái phép.

#### Các Mục Mới cần được Tích Hợp Phía Trên

 #2.3.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng tập hợp ký tự được phép được xem xét và cập nhật định kỳ để đảm bảo nó vẫn phù hợp với yêu cầu kinh doanh.

## Phụ lục D: Quản trị và Kiểm tra Mã hóa An toàn Hỗ trợ bởi AI

### Mục tiêu

Chương này định nghĩa các kiểm soát tổ chức cơ bản cho việc sử dụng an toàn và hiệu quả các công cụ mã hóa hỗ trợ AI trong quá trình phát triển phần mềm, đảm bảo an ninh và khả năng truy xuất trong toàn bộ SDLC.

────────────────────────────────────────

### AD.1 Quy trình làm việc mã hóa an toàn được hỗ trợ bởi AI

Tích hợp công cụ AI vào vòng đời phát triển phần mềm an toàn (SSDLC) của tổ chức mà không làm yếu các điểm kiểm soát an ninh hiện có.

 #AD.1.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng một quy trình làm việc được tài liệu hóa mô tả khi nào và như thế nào các công cụ AI có thể tạo ra, tái cấu trúc hoặc kiểm tra mã.
 #AD.1.2    Cấp độ: 2    Vai trò: D
 Xác minh rằng quy trình làm việc phù hợp với từng giai đoạn của SSDLC (thiết kế, triển khai, xem xét mã, kiểm thử, triển khai).
 #AD.1.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các chỉ số (ví dụ: mật độ lỗ hổng, thời gian trung bình để phát hiện) được thu thập trên mã do AI tạo ra và so sánh với các chuẩn cơ sở chỉ có con người.

────────────────────────────────────────

### AD.2 Đánh giá Công cụ AI & Mô hình hóa Mối đe dọa

Đảm bảo các công cụ lập trình AI được đánh giá về khả năng bảo mật, rủi ro và tác động chuỗi cung ứng trước khi áp dụng.

 #AD.2.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng mô hình đe dọa cho từng công cụ AI nhận diện được việc sử dụng sai mục đích, đảo ngược mô hình, rò rỉ dữ liệu và các rủi ro chuỗi phụ thuộc.
 #AD.2.2    Cấp độ: 2    Vai trò: D
 Xác minh rằng việc đánh giá công cụ bao gồm phân tích tĩnh/động của bất kỳ thành phần cục bộ nào và đánh giá các điểm cuối SaaS (TLS, xác thực/ủy quyền, ghi nhật ký).
 #AD.2.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các đánh giá tuân theo một khuôn khổ được công nhận và được thực hiện lại sau các thay đổi phiên bản lớn.

────────────────────────────────────────

### AD.3 Quản lý Bảo mật Prompt & Ngữ cảnh

Ngăn ngừa rò rỉ bí mật, mã nguồn độc quyền và dữ liệu cá nhân khi xây dựng câu lệnh hoặc ngữ cảnh cho các mô hình AI.

 #AD.3.1    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng hướng dẫn bằng văn bản cấm gửi bí mật, thông tin đăng nhập hoặc dữ liệu mật trong các lời nhắc.
 #AD.3.2    Cấp độ: 2    Vai trò: D
 Xác minh rằng các biện pháp kiểm soát kỹ thuật (lọc phía khách hàng, bộ lọc ngữ cảnh được phê duyệt) tự động loại bỏ các dữ liệu nhạy cảm.
 #AD.3.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các câu lệnh nhắc và phản hồi được phân tích thành token, mã hóa khi truyền và khi lưu trữ, và các khoảng thời gian lưu trữ tuân thủ chính sách phân loại dữ liệu.

────────────────────────────────────────

### AD.4 Xác thực mã do AI tạo ra

Phát hiện và khắc phục các lỗ hổng do đầu ra của AI gây ra trước khi mã được gộp hoặc triển khai.

 #AD.4.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng mã do AI tạo ra luôn được đưa vào quy trình đánh giá mã bởi con người.
 #AD.4.2    Cấp độ: 2    Vai trò: D
 Xác minh rằng các trình quét tự động (SAST/IAST/DAST) được chạy trên mọi yêu cầu kéo chứa mã do AI tạo ra và chặn việc hợp nhất khi phát hiện các vấn đề nghiêm trọng.
 #AD.4.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng kiểm thử fuzz vi phân hoặc kiểm thử dựa trên thuộc tính chứng minh các hành vi quan trọng về bảo mật (ví dụ: xác thực đầu vào, logic ủy quyền).

────────────────────────────────────────

### AD.5 Khả năng Giải thích và Truy xuất nguồn gốc của Gợi ý Mã code

Cung cấp cho các kiểm toán viên và nhà phát triển cái nhìn sâu sắc về lý do tại sao một đề xuất được đưa ra và cách nó phát triển.

 #AD.5.1    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng các cặp lời nhắc/phản hồi được ghi lại kèm theo các ID cam kết.
 #AD.5.2    Cấp độ: 2    Vai trò: D
 Xác minh rằng các nhà phát triển có thể hiển thị trích dẫn mô hình (đoạn trích đào tạo, tài liệu) hỗ trợ một đề xuất.
 #AD.5.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các báo cáo giải thích được lưu trữ cùng với các hiện vật thiết kế và được tham chiếu trong các đánh giá bảo mật, đáp ứng các nguyên tắc truy xuất nguồn gốc của ISO/IEC 42001.

────────────────────────────────────────

### AD.6 Phản hồi liên tục & Tinh chỉnh mô hình

Cải thiện hiệu suất bảo mật mô hình theo thời gian đồng thời ngăn ngừa sự suy giảm tiêu cực.

 #AD.6.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các nhà phát triển có thể đánh dấu các gợi ý không an toàn hoặc không tuân thủ, và các đánh dấu này được theo dõi.
 #AD.6.2    Cấp độ: 2    Vai trò: D
 Xác minh rằng phản hồi tổng hợp được sử dụng để điều chỉnh tinh chỉnh định kỳ hoặc tạo ra kết quả tăng cường truy xuất với các kho dữ liệu mã hóa an toàn đã được kiểm duyệt (ví dụ, OWASP Cheat Sheets).
 #AD.6.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng một hệ thống đánh giá vòng kín thực hiện các bài kiểm tra hồi quy sau mỗi lần tinh chỉnh; các chỉ số bảo mật phải đạt hoặc vượt mức cơ sở trước đó trước khi triển khai.

────────────────────────────────────────

#### Tài liệu tham khảo

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
OWASP Secure Coding Practices — Quick Reference Guide

## Phụ lục E: Ví dụ về Công cụ và Khung làm việc

### Mục tiêu

Chương này cung cấp các ví dụ về công cụ và khung làm việc có thể hỗ trợ việc triển khai hoặc thực hiện một yêu cầu AISVS nhất định. Những ví dụ này không được xem như là khuyến nghị hoặc sự ủng hộ của nhóm AISVS hay Dự án Bảo mật OWASP GenAI.

────────────────────────────────────────

### AE.1 Quản lý Dữ liệu Đào tạo & Quản lý Thiên vị

Công cụ được sử dụng cho phân tích dữ liệu, quản trị và quản lý sự thiên vị.

 #AE.1.1    Phần: 1.1
 Công cụ kiểm kê dữ liệu: Công cụ quản lý kiểm kê dữ liệu như...
 #AE.1.2    Phần: 1.2
 Mã hóa khi truyền Dùng TLS cho các ứng dụng dựa trên HTTPS, với các công cụ như openSSL và python's`ssl` thư viện.

────────────────────────────────────────

### AE.2 Xác thực đầu vào người dùng

Công cụ để xử lý và kiểm tra tính hợp lệ của dữ liệu đầu vào từ người dùng.

 #AE.2.1    Phần: 2.1
 Công cụ phòng chống tấn công tiêm nhiễm Prompt: Sử dụng công cụ rào chắn như NeMo của NVIDIA hoặc Guardrails AI.

────────────────────────────────────────

## Phụ lục B: Kiểm soát chiến lược

### C4.15 An ninh Hạ tầng Chống Lượng tử

Chuẩn bị hạ tầng AI để đối phó với các mối đe dọa từ điện toán lượng tử thông qua mật mã hậu lượng tử và các giao thức an toàn lượng tử.

 #4.15.1    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng hạ tầng AI triển khai các thuật toán mật mã hậu lượng tử được NIST phê duyệt (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) cho trao đổi khóa và chữ ký số.
 #4.15.2    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các hệ thống phân phối khóa lượng tử (QKD) được triển khai cho các giao tiếp AI có độ bảo mật cao với các giao thức quản lý khóa an toàn trước lượng tử.
 #4.15.3    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng các khung công tác linh hoạt về mật mã cho phép di chuyển nhanh chóng sang các thuật toán hậu lượng tử mới với việc tự động quay vòng chứng chỉ và khóa.
 #4.15.4    Cấp độ: 3    Vai trò: V
 Xác minh rằng mô hình hóa rủi ro lượng tử đánh giá mức độ dễ bị tổn thương của hạ tầng AI trước các cuộc tấn công lượng tử với các mốc thời gian di chuyển đã được ghi nhận và các đánh giá rủi ro.
 #4.15.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các hệ thống mật mã lai cổ điển - lượng tử cung cấp phòng thủ đa lớp trong giai đoạn chuyển tiếp lượng tử kèm theo việc giám sát hiệu suất.

────────────────────────────────────────

### C4.17 Hạ tầng Kiến thức Bất Biết

Triển khai các hệ thống chứng minh không kiến thức để xác minh và xác thực AI bảo vệ quyền riêng tư mà không tiết lộ thông tin nhạy cảm.

 #4.17.1    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các bằng chứng không tiết lộ thông tin (ZK-SNARKs, ZK-STARKs) đảm bảo tính toàn vẹn của mô hình AI và nguồn gốc đào tạo mà không tiết lộ trọng số mô hình hoặc dữ liệu đào tạo.
 #4.17.2    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các hệ thống xác thực dựa trên ZK cho phép xác minh người dùng bảo vệ quyền riêng tư cho các dịch vụ AI mà không tiết lộ thông tin liên quan đến danh tính.
 #4.17.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các giao thức giao nhau tập hợp riêng tư (PSI) cho phép khớp dữ liệu an toàn cho AI liên kết mà không làm lộ các tập dữ liệu cá nhân.
 #4.17.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các hệ thống học máy không kiến thức (ZKML) cho phép những suy luận AI có thể kiểm chứng với bằng chứng mật mã về tính toán đúng.
 #4.17.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng ZK-rollups cung cấp quá trình xử lý giao dịch AI có thể mở rộng, bảo vệ quyền riêng tư với xác minh theo lô và giảm tải tính toán.

────────────────────────────────────────

### C4.18 Phòng ngừa tấn công kênh bên

Bảo vệ hạ tầng AI khỏi các cuộc tấn công kênh bên dựa trên thời gian, công suất, điện từ, và bộ nhớ đệm có thể làm rò rỉ thông tin nhạy cảm.

 #4.18.1    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng thời gian suy luận AI được chuẩn hóa bằng cách sử dụng các thuật toán thời gian cố định và đệm để ngăn chặn các cuộc tấn công trích xuất mô hình dựa trên thời gian.
 #4.18.2    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng biện pháp bảo vệ phân tích công suất bao gồm tiêm nhiễu, lọc đường dây điện và các mẫu thực thi ngẫu nhiên cho phần cứng AI.
 #4.18.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng biện pháp giảm thiểu kênh bên dựa trên bộ nhớ đệm sử dụng phân vùng bộ nhớ đệm, ngẫu nhiên hóa và lệnh xả để ngăn chặn rò rỉ thông tin.
 #4.18.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng việc bảo vệ phát xạ điện từ bao gồm chắn sóng, lọc tín hiệu và xử lý ngẫu nhiên để ngăn ngừa các cuộc tấn công kiểu TEMPEST.
 #4.18.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các biện pháp phòng thủ kênh bên vi kiến trúc bao gồm kiểm soát thực thi dự đoán và làm mờ mẫu truy cập bộ nhớ.

────────────────────────────────────────

### C4.19 An ninh phần cứng AI chuyên biệt & dựa trên mô phỏng thần kinh

Bảo mật các kiến trúc phần cứng AI mới nổi bao gồm chip thần kinh, FPGA, ASIC tùy chỉnh và hệ thống tính toán quang học.

 #4.19.1    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng bảo mật chip neuromorphic bao gồm mã hóa mẫu xung, bảo vệ trọng số synapse và xác thực quy tắc học dựa trên phần cứng.
 #4.19.2    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các bộ tăng tốc AI dựa trên FPGA thực hiện mã hóa luồng bit, cơ chế chống giả mạo và tải cấu hình an toàn với các bản cập nhật đã xác thực.
 #4.19.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng bảo mật ASIC tùy chỉnh bao gồm các bộ xử lý bảo mật trên chip, gốc tin cậy phần cứng và lưu trữ khóa an toàn với phát hiện chống giả mạo.
 #4.19.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các hệ thống tính toán quang học thực hiện mã hóa quang học an toàn trước lượng tử, chuyển mạch quang tử bảo mật và xử lý tín hiệu quang học được bảo vệ.
 #4.19.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các chip AI lai tương tự-số bao gồm tính toán tương tự an toàn, lưu trữ trọng số được bảo vệ và chuyển đổi tương tự-số được xác thực.

────────────────────────────────────────

### Hạ tầng tính toán bảo vệ quyền riêng tư C4.20

Triển khai các biện pháp kiểm soát hạ tầng cho tính toán bảo vệ quyền riêng tư nhằm bảo vệ dữ liệu nhạy cảm trong quá trình xử lý và phân tích AI.

 #4.20.1    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng cơ sở hạ tầng mã hóa đồng dạng cho phép tính toán trên dữ liệu được mã hóa cho các khối lượng công việc AI nhạy cảm với việc kiểm tra tính toàn vẹn bằng mật mã và giám sát hiệu suất.
 #4.20.2    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các hệ thống truy xuất thông tin riêng tư cho phép truy vấn cơ sở dữ liệu mà không tiết lộ mẫu truy vấn với sự bảo vệ mật mã đối với mẫu truy cập.
 #4.20.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các giao thức tính toán đa bên an toàn cho phép suy luận AI bảo vệ quyền riêng tư mà không tiết lộ các đầu vào cá nhân hoặc các phép tính trung gian.
 #4.20.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng quản lý khóa bảo vệ quyền riêng tư bao gồm tạo khóa phân tán, mật mã ngưỡng và xoay khóa an toàn với sự bảo vệ dựa trên phần cứng.
 #4.20.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng hiệu suất tính toán bảo vệ quyền riêng tư được tối ưu hóa thông qua việc xử lý theo lô, lưu trong bộ nhớ đệm, và tăng tốc phần cứng trong khi vẫn duy trì các đảm bảo bảo mật mật mã.

 4.9.14.9.2    1: 2    D/V: D/V
 Xác minh rằng triển khai đa đám mây sử dụng các tiêu chuẩn định danh liên minh (ví dụ, OIDC, SAML) với việc thực thi chính sách tập trung trên các nhà cung cấp.
 4.9.14.9.3    1: 2    D/V: D/V
 Xác minh rằng các chuyển dữ liệu giữa các đám mây và dữ liệu lai sử dụng mã hóa đầu cuối với khóa do khách hàng quản lý và thực thi các yêu cầu cư trú dữ liệu theo thẩm quyền.
 4.9.14.9.1    1: 1    D/V: D/V
 Xác minh rằng việc tích hợp lưu trữ đám mây sử dụng mã hóa đầu-cuối với quản lý khóa do tác nhân kiểm soát.
 4.9.14.9.2    1: 2    D/V: D/V
 Xác minh rằng các ranh giới bảo mật triển khai lai được xác định rõ ràng với các kênh truyền thông được mã hóa.

