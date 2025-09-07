## Trang bìa

### Về Tiêu chuẩn

Tiêu chuẩn Xác minh An ninh Trí tuệ Nhân tạo (AISVS) là một danh mục các yêu cầu về an ninh do cộng đồng phát triển, mà các nhà khoa học dữ liệu, kỹ sư MLOps, kiến trúc sư phần mềm, nhà phát triển, kiểm thử viên, chuyên gia an ninh, nhà cung cấp công cụ, cơ quan quản lý và người tiêu dùng có thể sử dụng để thiết kế, xây dựng, kiểm thử và xác minh các hệ thống và ứng dụng được hỗ trợ bởi AI đáng tin cậy. Nó cung cấp một ngôn ngữ chung để xác định các kiểm soát an ninh trong suốt vòng đời AI — từ thu thập dữ liệu và phát triển mô hình đến triển khai và giám sát liên tục — giúp các tổ chức đo lường và cải thiện khả năng chống chịu, quyền riêng tư và an toàn của các giải pháp AI của họ.

### Bản quyền và Giấy phép

Phiên bản 0.1 (Bản nháp công khai đầu tiên - Đang trong quá trình hoàn thiện), 2025  

![license](images/license.png)
Bản quyền © 2025 Dự án AISVS.  

Phát hành theoCreative Commons Attribution‑ShareAlike 4.0 International License.
Đối với bất kỳ việc tái sử dụng hoặc phân phối nào, bạn phải rõ ràng truyền đạt các điều khoản cấp phép của tác phẩm này cho người khác.

### Trưởng nhóm dự án

Jim Manico
Aras “Russ” Memisyazici

### Người đóng góp và người đánh giá

https://github.com/ottosulin
https://github.com/mbhatt1
https://github.com/vineethsai
https://github.com/cciprofm
https://github.com/deepakrpandey12


---

AISVS là một tiêu chuẩn hoàn toàn mới được tạo ra nhằm giải quyết các thách thức bảo mật đặc thù của các hệ thống trí tuệ nhân tạo. Mặc dù lấy cảm hứng từ các thực tiễn bảo mật chung, nhưng mỗi yêu cầu trong AISVS đều được phát triển từ đầu để phản ánh bối cảnh mối đe dọa AI và giúp các tổ chức xây dựng các giải pháp AI an toàn hơn, có khả năng chống chịu tốt hơn.

## Lời nói đầu

Chào mừng bạn đến với Tiêu chuẩn Xác minh An ninh Trí tuệ Nhân tạo (AISVS) phiên bản 1.0!

### Giới thiệu

Được thành lập vào năm 2025 thông qua nỗ lực cộng đồng hợp tác, AISVS xác định các yêu cầu bảo mật cần xem xét khi thiết kế, phát triển, triển khai và vận hành các mô hình AI hiện đại, quy trình và dịch vụ được hỗ trợ bởi AI.

AISVS v1.0 đại diện cho công trình kết hợp của các trưởng dự án, nhóm làm việc và những người đóng góp trong cộng đồng rộng lớn nhằm tạo ra một cơ sở thực tiễn và khả thi để bảo mật hệ thống AI.

Mục tiêu của chúng tôi với phiên bản phát hành này là làm cho AISVS trở nên dễ áp dụng trong khi vẫn tập trung rõ nét vào phạm vi đã được xác định và giải quyết bối cảnh rủi ro phát triển nhanh đặc thù của AI.

### Mục tiêu chính cho AISVS Phiên bản 1.0

Phiên bản 1.0 sẽ được tạo ra với một số nguyên tắc hướng dẫn.

#### Phạm vi xác định rõ ràng

Mỗi yêu cầu phải phù hợp với tên gọi và sứ mệnh của AISVS:

Trí tuệ nhân tạo – Các kiểm soát hoạt động ở lớp AI/ML (dữ liệu, mô hình, đường ống xử lý, hoặc suy luận) và thuộc trách nhiệm của các chuyên gia AI.
Bảo mật – Các yêu cầu trực tiếp giảm thiểu các rủi ro về bảo mật, quyền riêng tư hoặc an toàn đã được xác định.
Xác minh – Ngôn ngữ được viết để có thể xác nhận sự tuân thủ một cách khách quan.
Tiêu chuẩn – Các phần tuân theo một cấu trúc và thuật ngữ nhất quán để tạo thành một tài liệu tham khảo mạch lạc.
​
---

Bằng cách tuân theo AISVS, các tổ chức có thể đánh giá một cách hệ thống và củng cố thế đứng bảo mật của các giải pháp AI của họ, thúc đẩy văn hóa kỹ thuật AI an toàn.

## Sử dụng AISVS

Tiêu chuẩn Xác minh An ninh Trí tuệ Nhân tạo (AISVS) xác định các yêu cầu về an ninh cho các ứng dụng và dịch vụ AI hiện đại, tập trung vào các khía cạnh trong tầm kiểm soát của nhà phát triển ứng dụng.

AISVS dành cho bất kỳ ai phát triển hoặc đánh giá bảo mật của các ứng dụng AI, bao gồm nhà phát triển, kiến trúc sư, kỹ sư bảo mật và kiểm toán viên. Chương này giới thiệu cấu trúc và cách sử dụng AISVS, bao gồm các cấp độ xác minh và các trường hợp sử dụng dự kiến.

### Các cấp độ xác minh bảo mật Trí tuệ Nhân tạo

AISVS định nghĩa ba cấp độ xác minh an ninh tăng dần. Mỗi cấp độ bổ sung độ sâu và độ phức tạp, cho phép các tổ chức điều chỉnh tư thế an ninh phù hợp với mức độ rủi ro của hệ thống AI của họ.

Các tổ chức có thể bắt đầu ở Cấp độ 1 và dần dần áp dụng các cấp độ cao hơn khi độ trưởng thành về bảo mật và mức độ phơi nhiễm trước các mối đe dọa tăng lên.

#### Định nghĩa các cấp độ

Mỗi yêu cầu trong AISVS phiên bản 1.0 được phân bổ vào một trong các cấp độ sau:

 Yêu cầu cấp độ 1

Cấp độ 1 bao gồm các yêu cầu bảo mật quan trọng và nền tảng nhất. Những yêu cầu này tập trung vào việc ngăn chặn các cuộc tấn công phổ biến không phụ thuộc vào các điều kiện tiên quyết hoặc các lỗ hổng khác. Hầu hết các kiểm soát cấp độ 1 đều dễ triển khai hoặc đủ quan trọng để biện minh cho nỗ lực thực hiện.

 Yêu cầu cấp độ 2

Cấp độ 2 giải quyết các cuộc tấn công nâng cao hơn hoặc ít phổ biến hơn, cũng như các biện pháp phòng thủ nhiều lớp chống lại các mối đe dọa lan rộng. Những yêu cầu này có thể liên quan đến logic phức tạp hơn hoặc nhắm vào các điều kiện tiên quyết cụ thể của cuộc tấn công.

 Yêu cầu cấp độ 3

Cấp độ 3 bao gồm các biện pháp kiểm soát thường khó thực hiện hơn hoặc chỉ áp dụng trong các tình huống cụ thể. Chúng thường đại diện cho các cơ chế phòng thủ đa lớp hoặc các biện pháp giảm thiểu chống lại các cuộc tấn công đặc thù, có mục tiêu hoặc phức tạp cao.

#### Vai trò (D/V)

Mỗi yêu cầu AISVS được đánh dấu theo đối tượng chính:

D – Yêu cầu tập trung vào nhà phát triển
V – Các yêu cầu tập trung vào người kiểm tra/kiểm toán viên
D/V – Liên quan đến cả nhà phát triển và người kiểm chứng

## Quản lý Dữ liệu Đào tạo C1 & Quản lý Định kiến

### Mục tiêu Kiểm soát

Dữ liệu đào tạo phải được lấy nguồn, xử lý và duy trì theo cách bảo tồn nguồn gốc, an ninh, chất lượng và sự công bằng. Thực hiện điều này giúp hoàn thành nghĩa vụ pháp lý và giảm thiểu rủi ro thiên vị, đầu độc hoặc vi phạm quyền riêng tư xuất hiện trong quá trình đào tạo có thể ảnh hưởng đến toàn bộ vòng đời AI.

---

### C1.1 Nguồn gốc Dữ liệu Đào tạo

Duy trì một danh mục dữ liệu có thể xác minh được tất cả các bộ dữ liệu, chỉ chấp nhận các nguồn tin cậy và ghi lại mọi thay đổi để phục vụ việc kiểm toán.

 #1.1.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng một danh mục cập nhật của mọi nguồn dữ liệu huấn luyện (nguồn gốc, người quản lý/chủ sở hữu, giấy phép, phương pháp thu thập, các ràng buộc sử dụng dự kiến và lịch sử xử lý) được duy trì.
 #1.1.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các quy trình dữ liệu đào tạo loại trừ các đặc điểm, thuộc tính hoặc trường không cần thiết (ví dụ: siêu dữ liệu không sử dụng, thông tin nhận dạng cá nhân nhạy cảm, dữ liệu kiểm tra bị rò rỉ).
 #1.1.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng tất cả các thay đổi dữ liệu được thực hiện theo quy trình phê duyệt có ghi nhật ký.
 #1.1.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các tập dữ liệu hoặc các tập con được đóng dấu nước hoặc đánh dấu vân tay khi có thể.

---

### C1.2 Bảo mật và Tính toàn vẹn Dữ liệu Đào tạo

Hạn chế quyền truy cập vào dữ liệu huấn luyện, mã hóa dữ liệu khi lưu trữ và truyền tải, đồng thời xác thực tính toàn vẹn của dữ liệu để ngăn chặn sự can thiệp, trộm cắp hoặc đầu độc dữ liệu.

 #1.2.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các kiểm soát truy cập bảo vệ lưu trữ dữ liệu đào tạo và các đường ống xử lý.
 #1.2.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng tất cả các truy cập đến dữ liệu đào tạo đều được ghi nhật ký, bao gồm người dùng, thời gian và hành động.
 #1.2.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các bộ dữ liệu đào tạo được mã hóa khi truyền và lưu trữ, sử dụng các thuật toán mật mã chuẩn công nghiệp và các phương pháp quản lý khóa.
 #1.2.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các hàm băm mật mã hoặc chữ ký số được sử dụng để đảm bảo tính toàn vẹn dữ liệu trong quá trình lưu trữ và truyền dữ liệu huấn luyện.
 #1.2.5    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các kỹ thuật phát hiện tự động được áp dụng để ngăn chặn các sửa đổi trái phép hoặc sự hỏng dữ liệu đào tạo.
 #1.2.6    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng dữ liệu huấn luyện đã lỗi thời được xoá bỏ hoặc ẩn danh một cách an toàn.
 #1.2.7    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng tất cả các phiên bản bộ dữ liệu huấn luyện được nhận dạng duy nhất, lưu trữ bất biến và có thể kiểm toán để hỗ trợ phục hồi và phân tích pháp y.

---

### C1.3 Chất lượng, Tính toàn vẹn và An ninh của Ghi nhãn Dữ liệu Đào tạo

Bảo vệ nhãn và yêu cầu xem xét kỹ thuật đối với dữ liệu quan trọng.

 #1.3.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các hàm băm mật mã hoặc chữ ký số được áp dụng cho các hiện vật nhãn để đảm bảo tính toàn vẹn và xác thực của chúng.
 #1.3.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các giao diện và nền tảng gán nhãn thực thi kiểm soát truy cập mạnh mẽ, duy trì nhật ký kiểm tra chống giả mạo của tất cả các hoạt động gán nhãn và bảo vệ chống lại các sửa đổi trái phép.
 #1.3.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng thông tin nhạy cảm trong nhãn được xóa bỏ, ẩn danh hoặc mã hóa ở cấp trường dữ liệu khi lưu trữ và khi truyền tải.

---

### C1.4 Đảm bảo Chất lượng và An toàn Dữ liệu Đào tạo

Kết hợp xác thực tự động, kiểm tra ngẫu nhiên thủ công và ghi lại quá trình khắc phục để đảm bảo độ tin cậy của tập dữ liệu.

 #1.4.1    Cấp độ: 1    Vai trò: D
 Xác minh rằng các bài kiểm tra tự động phát hiện lỗi định dạng và giá trị null trên mọi lần nhập dữ liệu hoặc chuyển đổi dữ liệu quan trọng.
 #1.4.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các quy trình đào tạo và tinh chỉnh mô hình ngôn ngữ lớn (LLM) thực hiện phát hiện đầu độc và xác thực tính toàn vẹn dữ liệu (ví dụ, các phương pháp thống kê, phát hiện điểm bất thường, phân tích embedding) để nhận diện các cuộc tấn công đầu độc tiềm năng (ví dụ, lật nhãn, chèn kích hoạt cửa hậu, lệnh chuyển đổi vai trò, tấn công mẫu ảnh hưởng) hoặc sự hỏng dữ liệu không cố ý trong dữ liệu đào tạo.
 #1.4.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các biện pháp phòng vệ phù hợp, chẳng hạn như đào tạo đối kháng (sử dụng các ví dụ đối kháng được tạo ra), tăng cường dữ liệu với các đầu vào bị nhiễu, hoặc các kỹ thuật tối ưu hóa mạnh mẽ, đã được triển khai và điều chỉnh cho các mô hình liên quan dựa trên đánh giá rủi ro.
 #1.4.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng nhãn được tạo tự động (ví dụ, qua LLM hoặc giám sát yếu) phải tuân theo ngưỡng độ tin cậy và kiểm tra tính nhất quán để phát hiện nhãn bị ảo giác, gây hiểu lầm hoặc có độ tin cậy thấp.
 #1.4.5    Cấp độ: 3    Vai trò: D
 Xác minh rằng các bài kiểm tra tự động phát hiện được sự lệch nhãn trên mỗi lần nhập dữ liệu hoặc biến đổi dữ liệu đáng kể.

---

### C1.5 Dòng dữ liệu và Khả năng truy xuất nguồn gốc

Theo dõi toàn bộ hành trình của từng điểm dữ liệu từ nguồn đến đầu vào mô hình để đảm bảo khả năng kiểm toán và phản hồi sự cố.

 #1.5.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng nguồn gốc của mỗi điểm dữ liệu, bao gồm tất cả các phép biến đổi, tăng cường và hợp nhất, được ghi lại và có thể được tái tạo.
 #1.5.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các hồ sơ dòng dõi là không thể thay đổi, được lưu trữ an toàn và có thể truy cập để kiểm toán.
 #1.5.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng việc theo dõi nguồn gốc bao phủ dữ liệu tổng hợp được tạo ra thông qua các kỹ thuật bảo vệ quyền riêng tư hoặc tạo dữ liệu và rằng tất cả dữ liệu tổng hợp đều được gắn nhãn rõ ràng và có thể phân biệt với dữ liệu thực trong suốt quy trình.

---

### Tài liệu tham khảo

NIST AI Risk Management Framework
EU AI Act – Article 10: Data & Data Governance
MITRE ATLAS: Adversary Tactics for AI
Survey of ML Bias Mitigation Techniques – MDPI
Data Provenance & Lineage Best Practices – Nightfall AI
Data Labeling Quality Standards – LabelYourData
Training Data Poisoning Guide – Lakera.ai
CISA Advisory: Securing Data for AI Systems
ISO/IEC 23053: AI Management Systems Framework
IBM: What is AI Governance?
Google AI Principles
GDPR & AI Training Data – DataProtectionReport
Supply-Chain Security for AI Data – AppSOC
OpenAI Privacy Center – Data Deletion Controls
Adversarial ML Dataset – Kaggle

## Xác thực đầu vào người dùng C2

### Mục tiêu Kiểm soát

Xác thực đầu vào của người dùng một cách chắc chắn là biện pháp phòng thủ hàng đầu chống lại một số cuộc tấn công gây tổn hại nghiêm trọng nhất đối với các hệ thống AI. Các cuộc tấn công tiêm nhiễm prompt có thể ghi đè các hướng dẫn của hệ thống, làm lộ dữ liệu nhạy cảm hoặc điều khiển mô hình theo hành vi không được phép. Trừ khi có bộ lọc chuyên dụng và các cấp bậc hướng dẫn được thiết lập, các nghiên cứu cho thấy các jailbreak "đa lần" khai thác cửa sổ ngữ cảnh rất dài sẽ có hiệu quả. Ngoài ra, các cuộc tấn công làm nhiễu nhương tinh vi—như thay đổi homoglyph hoặc leetspeak—có thể lặng lẽ thay đổi các quyết định của mô hình.

---

### Phòng thủ tiêm nhắc lệnh C2.1

Tấn công tiêm nhiễm lệnh (prompt injection) là một trong những rủi ro hàng đầu đối với các hệ thống AI. Các biện pháp phòng chống chiến thuật này sử dụng sự kết hợp của bộ lọc mẫu tĩnh, bộ phân loại động và việc thi hành cấu trúc hướng dẫn.

 #2.1.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các dữ liệu nhập của người dùng được kiểm tra dựa trên một thư viện các mẫu tấn công prompt injection đã được cập nhật liên tục (từ khóa jailbreak, "bỏ qua nội dung trước", chuỗi nhập vai, các cuộc tấn công gián tiếp qua HTML/URL).
 #2.1.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng hệ thống thực thi một cấp bậc hướng dẫn trong đó các tin nhắn của hệ thống hoặc nhà phát triển ghi đè lên các hướng dẫn của người dùng, ngay cả sau khi mở rộng cửa sổ ngữ cảnh.
 #2.1.3    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng các bài kiểm tra đánh giá đối kháng (ví dụ, các câu lệnh "many-shot" của Đội Đỏ) được thực hiện trước mỗi lần phát hành mô hình hoặc mẫu câu lệnh, với các ngưỡng tỷ lệ thành công và các bộ chặn tự động cho các sự suy giảm hiệu suất.
 #2.1.4    Cấp độ: 2    Vai trò: D
 Xác minh rằng các lệnh nhắc xuất phát từ nội dung bên thứ ba (trang web, PDF, email) được làm sạch trong một ngữ cảnh phân tích tách biệt trước khi được nối vào lệnh nhắc chính.
 #2.1.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng tất cả các cập nhật quy tắc lọc câu lệnh, phiên bản mô hình phân loại và các thay đổi trong danh sách chặn đều được kiểm soát phiên bản và có thể kiểm tra được.

---

### C2.2 Kháng lại Ví dụ Đối kháng

Các mô hình Xử lý Ngôn ngữ Tự nhiên (NLP) vẫn dễ bị tổn thương bởi những biến động tinh vi ở cấp độ ký tự hoặc từ mà con người thường bỏ qua nhưng các mô hình lại có xu hướng phân loại sai.

 #2.2.1    Cấp độ: 1    Vai trò: D
 Xác minh rằng các bước chuẩn hoá đầu vào cơ bản (Unicode NFC, ánh xạ homoglyph, cắt bớt khoảng trắng) được thực hiện trước khi phân tách từ khóa.
 #2.2.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng phát hiện bất thường thống kê đánh dấu các đầu vào có khoảng cách chỉnh sửa bất thường cao so với chuẩn ngôn ngữ, các token lặp lại quá mức hoặc khoảng cách embedding bất thường.
 #2.2.3    Cấp độ: 2    Vai trò: D
 Xác nhận rằng chuỗi xử lý suy luận hỗ trợ các biến thể mô hình được củng cố bằng huấn luyện đối kháng tùy chọn hoặc các lớp phòng thủ (ví dụ: ngẫu nhiên hóa, chưng cất phòng thủ) cho các điểm cuối có rủi ro cao.
 #2.2.4    Cấp độ: 2    Vai trò: V
 Xác minh rằng các đầu vào nghi ngờ là tấn công đối kháng được cách ly, ghi lại với toàn bộ nội dung (sau khi đã loại bỏ thông tin cá nhân nhận dạng).
 #2.2.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các chỉ số độ bền (tỷ lệ thành công của các bộ tấn công đã biết) được theo dõi theo thời gian và các suy giảm kích hoạt một chặn phát hành.

---

### C2.3 Xác thực Sơ đồ, Loại & Độ dài

Các cuộc tấn công AI với đầu vào bị sai định dạng hoặc quá kích thước có thể gây ra lỗi phân tích cú pháp, tràn lệnh qua các trường và cạn kiệt tài nguyên. Việc thi hành nghiêm ngặt sơ đồ cũng là một yêu cầu bắt buộc khi thực hiện các cuộc gọi công cụ xác định.

 #2.3.1    Cấp độ: 1    Vai trò: D
 Xác minh rằng mọi điểm cuối gọi API hoặc hàm đều định nghĩa một sơ đồ đầu vào rõ ràng (JSON Schema, Protobuf hoặc tương đương đa phương thức) và rằng các đầu vào được xác thực trước khi lắp ráp prompt.
 #2.3.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các đầu vào vượt quá giới hạn tối đa về token hoặc byte sẽ bị từ chối với lỗi an toàn và không bao giờ bị cắt ngắn một cách im lặng.
 #2.3.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng việc kiểm tra kiểu (ví dụ: phạm vi số, giá trị enum, loại MIME cho hình ảnh/âm thanh) được thực thi phía máy chủ, không chỉ trong mã phía khách.
 #2.3.4    Cấp độ: 2    Vai trò: D
 Xác minh rằng các bộ kiểm tra ngữ nghĩa (ví dụ: JSON Schema) hoạt động trong thời gian không đổi để ngăn ngừa tấn công từ chối dịch vụ theo thuật toán (DoS).
 #2.3.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng các lỗi xác thực được ghi lại với các đoạn payload đã được che mờ và mã lỗi rõ ràng để hỗ trợ phân loại sự cố bảo mật.

---

### C2.4 Kiểm tra Nội dung & Chính sách

Các nhà phát triển nên có khả năng phát hiện các lời nhắc hợp lệ về mặt cú pháp nhưng yêu cầu nội dung bị cấm (chẳng hạn như hướng dẫn bất hợp pháp, ngôn ngữ thù địch và văn bản có bản quyền), sau đó ngăn chặn chúng lan truyền.

 #2.4.1    Cấp độ: 1    Vai trò: D
 Xác minh rằng bộ phân loại nội dung (không huấn luyện hoặc đã tinh chỉnh) đánh giá mọi đầu vào về bạo lực, tự làm hại, thù địch, nội dung tình dục và các yêu cầu bất hợp pháp, với các ngưỡng có thể cấu hình.
 #2.4.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các đầu vào vi phạm chính sách sẽ nhận được từ chối chuẩn hóa hoặc hoàn thành an toàn để chúng không lan truyền đến các cuộc gọi LLM tiếp theo.
 #2.4.3    Cấp độ: 2    Vai trò: D
 Xác minh rằng mô hình sàng lọc hoặc bộ quy tắc được đào tạo lại/cập nhật ít nhất mỗi quý, kết hợp các mẫu vượt rào hoặc bỏ qua chính sách mới được quan sát.
 #2.4.4    Cấp độ: 2    Vai trò: D
 Xác minh rằng việc sàng lọc tuân thủ các chính sách riêng của người dùng (độ tuổi, các hạn chế pháp lý vùng) thông qua các quy tắc dựa trên thuộc tính được giải quyết tại thời điểm yêu cầu.
 #2.4.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng các nhật ký sàng lọc bao gồm điểm độ tin cậy của bộ phân loại và các thẻ danh mục chính sách cho việc tương quan SOC và phát lại đội đỏ trong tương lai.

---

### C2.5 Giới Hạn Tốc Độ Nhập Liệu & Ngăn Ngừa Lạm Dụng

Các nhà phát triển nên ngăn chặn lạm dụng, cạn kiệt tài nguyên và các cuộc tấn công tự động đối với các hệ thống AI bằng cách giới hạn tốc độ đầu vào và phát hiện các mô hình sử dụng bất thường.

 #2.5.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng giới hạn tốc độ theo người dùng, theo IP và theo khóa API được thực thi cho tất cả các điểm đầu vào.
 #2.5.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các giới hạn tốc độ theo đợt và liên tục được điều chỉnh để ngăn chặn các cuộc tấn công DoS và tấn công dò mật khẩu.
 #2.5.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các kiểu sử dụng bất thường (ví dụ, các yêu cầu dồn dập nhanh, nhập liệu quá tải) kích hoạt các chặn tự động hoặc các biện pháp nâng cao.
 #2.5.4    Cấp độ: 3    Vai trò: V
 Xác minh rằng các bản ghi phòng ngừa lạm dụng được lưu giữ và xem xét để phát hiện các mô hình tấn công mới nổi.

---

### C2.6 Xác thực Đầu vào Đa phương thức

Hệ thống AI nên bao gồm việc kiểm tra xác thực mạnh mẽ cho các đầu vào phi văn bản (hình ảnh, âm thanh, tệp tin) để ngăn chặn việc chèn, né tránh, hoặc lạm dụng tài nguyên.

 #2.6.1    Cấp độ: 1    Vai trò: D
 Xác minh rằng tất cả các đầu vào không phải văn bản (hình ảnh, âm thanh, tệp) được kiểm tra về loại, kích thước và định dạng trước khi xử lý.
 #2.6.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các tệp được quét để phát hiện phần mềm độc hại và payload ẩn trước khi nhập liệu.
 #2.6.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các đầu vào hình ảnh/âm thanh được kiểm tra các nhiễu loạn đối kháng hoặc các mẫu tấn công đã biết.
 #2.6.4    Cấp độ: 3    Vai trò: V
 Xác minh rằng các lỗi xác thực đầu vào đa phương thức được ghi lại và kích hoạt cảnh báo để điều tra.

---

### C2.7 Nguồn gốc và Ghi công Đầu vào

Hệ thống AI nên hỗ trợ kiểm toán, theo dõi lạm dụng và tuân thủ bằng cách giám sát và gắn nhãn nguồn gốc của tất cả các đầu vào từ người dùng.

 #2.7.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng tất cả các đầu vào của người dùng đều được gắn thẻ với siêu dữ liệu (ID người dùng, phiên, nguồn, dấu thời gian, địa chỉ IP) tại thời điểm nhập dữ liệu.
 #2.7.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng siêu dữ liệu nguồn gốc được giữ lại và có thể kiểm tra được cho tất cả các đầu vào đã xử lý.
 #2.7.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các nguồn đầu vào bất thường hoặc không đáng tin cậy được đánh dấu và chịu sự kiểm tra chặt chẽ hơn hoặc bị chặn.

---

### C2.8 Phát hiện Mối đe dọa Thích ứng Thời gian Thực

Các nhà phát triển nên sử dụng các hệ thống phát hiện mối đe dọa tiên tiến cho AI, có khả năng thích ứng với các mẫu tấn công mới và cung cấp bảo vệ thời gian thực bằng cách so khớp mẫu được biên dịch.

 #2.8.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các mẫu phát hiện mối đe dọa được biên dịch thành các công cụ regex được tối ưu hóa để lọc thời gian thực hiệu suất cao với tác động độ trễ tối thiểu.
 #2.8.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các hệ thống phát hiện mối đe dọa duy trì các thư viện mẫu riêng biệt cho các loại mối đe dọa khác nhau (chèn lệnh gợi ý, nội dung có hại, dữ liệu nhạy cảm, lệnh hệ thống).
 #2.8.3    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng phát hiện mối đe dọa thích ứng bao gồm các mô hình học máy cập nhật độ nhạy cảm của mối đe dọa dựa trên tần suất và tỷ lệ thành công của các cuộc tấn công.
 #2.8.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các nguồn cấp dữ liệu tình báo mối đe dọa thời gian thực tự động cập nhật các thư viện mẫu với các chữ ký tấn công mới và các chỉ số xâm nhập (IOCs).
 #2.8.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng tỷ lệ báo động giả của việc phát hiện mối đe dọa được giám sát liên tục và độ đặc hiệu của mẫu được điều chỉnh tự động nhằm giảm thiểu sự can thiệp vào các trường hợp sử dụng hợp lệ.
 #2.8.6    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng phân tích mối đe dọa theo ngữ cảnh xem xét nguồn đầu vào, các mẫu hành vi người dùng và lịch sử phiên làm việc để cải thiện độ chính xác trong phát hiện.
 #2.8.7    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các chỉ số hiệu suất phát hiện mối đe dọa (tỷ lệ phát hiện, độ trễ xử lý, sử dụng tài nguyên) được giám sát và tối ưu hóa theo thời gian thực.

---

### C2.9 Quy trình xác thực bảo mật đa phương thức

Các nhà phát triển nên cung cấp xác thực bảo mật cho văn bản, hình ảnh, âm thanh và các phương thức đầu vào AI khác với các loại phát hiện mối đe dọa cụ thể và cách ly tài nguyên.

 #2.9.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng mỗi loại hình đầu vào đều có các bộ kiểm tra bảo mật riêng biệt với các mẫu mối đe dọa được tài liệu hóa (văn bản: tiêm lệnh nhắc, hình ảnh: ẩn tin, âm thanh: các cuộc tấn công phổ quang) và ngưỡng phát hiện.
 #2.9.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các đầu vào đa phương thức được xử lý trong các sandbox riêng biệt với giới hạn tài nguyên đã định rõ (bộ nhớ, CPU, thời gian xử lý) cụ thể cho từng loại phương thức và được ghi trong các chính sách bảo mật.
 #2.9.3    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng việc phát hiện tấn công đa phương thức nhận diện các cuộc tấn công phối hợp trên nhiều loại đầu vào khác nhau (ví dụ: payload giấu dữ liệu trong ảnh kết hợp với chèn prompt trong văn bản) bằng các quy tắc tương quan và tạo cảnh báo.
 #2.9.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các lỗi xác thực đa phương thức kích hoạt ghi nhật ký chi tiết bao gồm tất cả các phương thức đầu vào, kết quả xác thực, điểm số mối đe dọa và phân tích tương quan với các định dạng nhật ký có cấu trúc để tích hợp SIEM.
 #2.9.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các bộ phân loại nội dung đặc thù theo phương thức được cập nhật theo lịch trình đã được ghi chép (ít nhất hàng quý) với các mẫu mối đe dọa mới, các ví dụ đối kháng và các tiêu chuẩn hiệu suất được duy trì trên ngưỡng cơ sở.

---

### Tài liệu tham khảo

LLM01:2025 Prompt Injection – OWASP Top 10 for LLM & Generative AI Security
Generative AI's Biggest Security Flaw Is Not Easy to Fix
Many-shot jailbreaking \ Anthropic
$PDF$ OpenAI GPT-4.5 System Card
Notebook for the CheckThat Lab at CLEF 2024
Mitigate jailbreaks and prompt injections – Anthropic
Chapter 3 MITRE ATT\&CK – Adversarial Model Analysis
OWASP Top 10 for LLM Applications 2025 – WorldTech IT
OWASP Machine Learning Security Top Ten
Few words about AI Security – Jussi Metso
How To Ensure LLM Output Adheres to a JSON Schema | Modelmetry
Easily enforcing valid JSON schema following – API
AI Safety + Cybersecurity R\&D Tracker – Fairly AI
Anthropic makes 'jailbreak' advance to stop AI models producing harmful results
Pattern matching filter rules - IBM
Real-time Threat Detection

## Quản lý Vòng đời Mô hình C3 & Kiểm soát Thay đổi

### Mục tiêu Kiểm soát

Các hệ thống AI phải triển khai các quy trình kiểm soát thay đổi nhằm ngăn chặn các sửa đổi mô hình không được phép hoặc không an toàn tiếp cận môi trường sản xuất. Kiểm soát này đảm bảo tính toàn vẹn của mô hình trong suốt vòng đời—từ phát triển đến triển khai và đến khi ngừng sử dụng—giúp phản ứng nhanh với sự cố và duy trì trách nhiệm đối với tất cả các thay đổi.

Mục tiêu an ninh cốt lõi: Chỉ những mô hình được ủy quyền và xác thực mới được đưa vào sản xuất thông qua việc áp dụng các quy trình kiểm soát nhằm duy trì tính toàn vẹn, khả năng truy xuất và khả năng khôi phục.

---

### C3.1 Ủy quyền Mô hình & Tính toàn vẹn

Chỉ các mô hình được ủy quyền và có tính toàn vẹn đã được xác minh mới được đưa vào môi trường sản xuất.

 #3.1.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng tất cả các tác phẩm của mô hình (trọng số, cấu hình, bộ mã hóa token) đều được ký số bởi các thực thể có thẩm quyền trước khi triển khai.
 #3.1.2    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng tính toàn vẹn của mô hình được xác thực vào thời điểm triển khai và việc xác minh chữ ký không thành công sẽ ngăn không cho tải mô hình.
 #3.1.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các hồ sơ nguồn gốc mô hình bao gồm định danh của thực thể ủy quyền, tổng kiểm tra dữ liệu đào tạo, kết quả kiểm thử xác nhận với trạng thái đạt/không đạt, và dấu thời gian tạo.
 #3.1.4    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng tất cả các thành phần mô hình sử dụng phiên bản ngữ nghĩa (MAJOR.MINOR.PATCH) với các tiêu chí được ghi chép rõ ràng xác định khi nào mỗi thành phần phiên bản được tăng lên.
 #3.1.5    Cấp độ: 2    Vai trò: V
 Xác minh rằng việc theo dõi phụ thuộc duy trì một kho hàng theo thời gian thực cho phép xác định nhanh tất cả các hệ thống tiêu thụ.

---

### C3.2 Xác nhận và Kiểm tra Mô hình

Các mô hình phải vượt qua các kiểm tra xác thực về bảo mật và an toàn đã được định nghĩa trước khi triển khai.

 #3.2.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các mô hình trải qua kiểm tra bảo mật tự động bao gồm xác thực đầu vào, làm sạch đầu ra và đánh giá an toàn với các ngưỡng đạt/không đạt đã được tổ chức đồng ý trước khi triển khai.
 #3.2.2    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng các lỗi xác thực tự động chặn việc triển khai mô hình sau khi được chấp thuận ghi đè rõ ràng từ các nhân sự có thẩm quyền được chỉ định trước với các lý do kinh doanh được ghi chép.
 #3.2.3    Cấp độ: 2    Vai trò: V
 Xác minh rằng kết quả kiểm tra được ký mật mã và liên kết không thể thay đổi với hàm băm phiên bản mô hình cụ thể đang được xác thực.
 #3.2.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các đợt triển khai khẩn cấp yêu cầu đánh giá rủi ro bảo mật được ghi chép và sự phê duyệt từ một cơ quan bảo mật được chỉ định trước trong khoảng thời gian đã thỏa thuận trước.

---

### C3.3 Triển khai kiểm soát & Quay lại

Việc triển khai mô hình phải được kiểm soát, giám sát và có thể đảo ngược.

 #3.3.1    Cấp độ: 1    Vai trò: D
 Xác minh rằng các triển khai sản xuất thực hiện các cơ chế triển khai dần (triển khai canary, triển khai xanh-lục) với các cơ chế kích hoạt tự động để quay lại dựa trên các tỷ lệ lỗi, ngưỡng độ trễ hoặc tiêu chí cảnh báo bảo mật đã thỏa thuận trước.
 #3.3.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng khả năng hoàn tác khôi phục trạng thái mô hình hoàn chỉnh (trọng số, cấu hình, phụ thuộc) một cách nguyên tử trong các khung thời gian tổ chức đã được định trước.
 #3.3.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các quy trình triển khai kiểm tra tính hợp lệ của chữ ký mã hóa và tính toán các tổng kiểm tra tính toàn vẹn trước khi kích hoạt mô hình, và hủy bỏ việc triển khai nếu có bất kỳ sự không khớp nào.
 #3.3.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng khả năng tắt mô hình khẩn cấp có thể vô hiệu hóa các điểm cuối mô hình trong thời gian phản hồi được định trước thông qua bộ ngắt mạch tự động hoặc công tắc tắt thủ công.
 #3.3.5    Cấp độ: 2    Vai trò: V
 Xác minh rằng các hiện vật phục hồi (các phiên bản mô hình trước đó, cấu hình, phụ thuộc) được lưu giữ theo chính sách của tổ chức với bộ nhớ không thể thay đổi để phản ứng sự cố.

---

### C3.4 Thay đổi Trách nhiệm và Kiểm toán

Tất cả các thay đổi trong vòng đời mô hình phải có khả năng truy vết và kiểm toán.

 #3.4.1    Cấp độ: 1    Vai trò: V
 Xác minh rằng tất cả các thay đổi mô hình (triển khai, cấu hình, ngừng sử dụng) tạo ra các bản ghi kiểm tra không thể thay đổi bao gồm dấu thời gian, danh tính tác nhân đã xác thực, loại thay đổi và trạng thái trước/sau.
 #3.4.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng việc truy cập nhật ký kiểm toán yêu cầu có sự ủy quyền thích hợp và tất cả các lần cố gắng truy cập đều được ghi lại với danh tính người dùng và dấu thời gian.
 #3.4.3    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng các mẫu prompt và tin nhắn hệ thống được quản lý phiên bản trong các kho git với việc duyệt mã bắt buộc và phê duyệt từ các người đánh giá được chỉ định trước khi triển khai.
 #3.4.4    Cấp độ: 2    Vai trò: V
 Xác minh rằng các bản ghi kiểm toán bao gồm đủ chi tiết (băm mô hình, ảnh chụp cấu hình, phiên bản phụ thuộc) để cho phép tái tạo đầy đủ trạng thái mô hình cho bất kỳ mốc thời gian nào trong khoảng thời gian lưu trữ.

---

### C3.5 Các Thực Tiễn Phát Triển An Toàn

Quy trình phát triển và đào tạo mô hình phải tuân theo các phương pháp bảo mật để ngăn ngừa việc bị xâm phạm.

 #3.5.1    Cấp độ: 1    Vai trò: D
 Xác minh rằng các môi trường phát triển mô hình, kiểm thử và sản xuất được tách biệt về mặt vật lý hoặc logic. Chúng không dùng chung cơ sở hạ tầng, có kiểm soát truy cập riêng biệt và lưu trữ dữ liệu cách ly.
 #3.5.2    Cấp độ: 1    Vai trò: D
 Xác minh rằng việc huấn luyện mô hình và điều chỉnh tinh xảy ra trong các môi trường riêng biệt với quyền truy cập mạng được kiểm soát.
 #3.5.3    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các nguồn dữ liệu huấn luyện được kiểm tra tính toàn vẹn và xác thực thông qua các nguồn tin cậy với chuỗi bảo quản được ghi chép đầy đủ trước khi sử dụng trong phát triển mô hình.
 #3.5.4    Cấp độ: 2    Vai trò: D
 Xác minh rằng các tài liệu phát triển mô hình (siêu tham số, kịch bản đào tạo, tệp cấu hình) được lưu trữ trong hệ thống kiểm soát phiên bản và yêu cầu phê duyệt đánh giá đồng nghiệp trước khi sử dụng trong quá trình đào tạo.

---

### C3.6 Nghỉ hưu & Ngừng sử dụng Mô hình

Các mô hình phải được loại bỏ một cách an toàn khi chúng không còn cần thiết hoặc khi các vấn đề về bảo mật được phát hiện.

 #3.6.1    Cấp độ: 1    Vai trò: D
 Xác minh rằng các quy trình ngừng sử dụng mô hình tự động quét các đồ thị phụ thuộc, xác định tất cả các hệ thống tiêu thụ, và cung cấp các khoảng thời gian thông báo trước đã được thỏa thuận trước khi ngừng hoạt động.
 #3.6.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các hiện vật mô hình đã nghỉ hưu được xoá an toàn bằng phương pháp xoá mật mã hoặc ghi đè nhiều lần theo các chính sách lưu giữ dữ liệu đã được tài liệu hoá cùng với các chứng chỉ xác nhận việc huỷ.
 #3.6.3    Cấp độ: 2    Vai trò: V
 Xác minh rằng các sự kiện nghỉ hưu mô hình được ghi lại với dấu thời gian và danh tính người thực hiện, đồng thời chữ ký mô hình bị thu hồi để ngăn chặn tái sử dụng.
 #3.6.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng việc nghỉ hưu mô hình khẩn cấp có thể vô hiệu hóa quyền truy cập mô hình trong khoảng thời gian phản ứng khẩn cấp đã được thiết lập trước thông qua các công tắc tắt tự động nếu phát hiện ra các lỗ hổng bảo mật nghiêm trọng.

---

### Tài liệu tham khảo

MLOps Principles
Securing AI/ML Ops – Cisco.com
Audit logs security: cryptographically signed tamper-proof logs
Machine Learning Model Versioning: Top Tools & Best Practices
AI Hygiene Starts with Models and Data Loaders – SEI Blog
How to handle versioning and rollback of a deployed ML model?
Reinforcement fine-tuning – OpenAI API
Auditing Machine Learning models: Governance, Data Security and …
Adversarial Training to Improve Model Robustness
What is AI adversarial robustness? – IBM Research
Exploring Data Provenance: Ensuring Data Integrity and Authenticity
MITRE ATLAS
AWS Prescriptive Guidance – Best practices for retiring applications …

## C4 Cơ sở hạ tầng, Cấu hình & Bảo mật Triển khai

### Mục tiêu Kiểm soát

Cơ sở hạ tầng AI phải được củng cố để chống lại việc leo thang đặc quyền, can thiệp chuỗi cung ứng và di chuyển ngang thông qua cấu hình bảo mật, cô lập thời gian chạy, quy trình triển khai đáng tin cậy và giám sát toàn diện. Chỉ các thành phần và cấu hình cơ sở hạ tầng được ủy quyền và xác thực mới được đưa vào sản xuất thông qua các quy trình kiểm soát nhằm duy trì tính bảo mật, toàn vẹn và khả năng kiểm tra.

Mục tiêu Bảo mật Cốt lõi: Chỉ các thành phần hạ tầng được ký mật mã và quét lỗ hổng mới được đưa vào sản xuất thông qua các đường ống xác thực tự động, có chức năng thực thi các chính sách bảo mật và duy trì hồ sơ kiểm toán không thể thay đổi.

---

### C4.1 Cô lập Môi trường Thời gian Chạy

Ngăn ngừa việc thoát khỏi container và leo thang đặc quyền thông qua các nguyên thủy cô lập cấp kernel và các kiểm soát truy cập bắt buộc.

 #4.1.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng tất cả các container AI loại bỏ TẤT CẢ các quyền năng Linux ngoại trừ CAP_SETUID, CAP_SETGID và các quyền năng được yêu cầu rõ ràng được ghi trong các chuẩn bảo mật.
 #4.1.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các hồ sơ seccomp chặn tất cả các syscall ngoại trừ những syscall đã được phê duyệt trước trong danh sách cho phép, với các vi phạm sẽ khiến container bị kết thúc và tạo ra các cảnh báo bảo mật.
 #4.1.3    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng các khối lượng công việc AI chạy với hệ thống tệp gốc chỉ đọc, tmpfs cho dữ liệu tạm thời, và các volume được đặt tên cho dữ liệu lưu trữ với các tùy chọn gắn kết noexec được thực thi.
 #4.1.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng việc giám sát thời gian chạy dựa trên eBPF (Falco, Tetragon hoặc tương đương) phát hiện các cố gắng leo thang đặc quyền và tự động chấm dứt các tiến trình vi phạm trong phạm vi thời gian phản hồi của tổ chức.
 #4.1.5    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng các khối lượng công việc AI có rủi ro cao được thực thi trong các môi trường cách ly phần cứng (Intel TXT, AMD SVM hoặc các nút bare-metal chuyên dụng) với việc xác minh chứng thực.

---

### C4.2 Đường ống Xây dựng & Triển khai An toàn

Đảm bảo tính toàn vẹn mật mã và an ninh chuỗi cung ứng thông qua các bản build có thể tái tạo và các tác phẩm được ký.

 #4.2.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng hạ tầng như mã được quét bằng các công cụ (tfsec, Checkov hoặc Terrascan) trên mỗi lần commit, chặn việc hợp nhất nếu phát hiện các lỗi mức độ NGHIÊM TRỌNG hoặc CAO.
 #4.2.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các bản dựng container có thể tái tạo với các hàm băm SHA256 giống hệt nhau trên các lần xây dựng và tạo các chứng nhận nguồn gốc SLSA Cấp độ 3 được ký bằng Sigstore.
 #4.2.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các ảnh container chứa SBOM CycloneDX hoặc SPDX và được ký bằng Cosign trước khi đẩy lên registry, với các ảnh không ký bị từ chối khi triển khai.
 #4.2.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các pipeline CI/CD sử dụng token OIDC từ HashiCorp Vault, vai trò IAM của AWS, hoặc Azure Managed Identity với thời gian tồn tại không vượt quá giới hạn chính sách bảo mật của tổ chức.
 #4.2.5    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các chữ ký Cosign và nguồn gốc SLSA được kiểm tra trong quá trình triển khai trước khi container được thực thi và rằng các lỗi xác minh sẽ khiến việc triển khai bị thất bại.
 #4.2.6    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các môi trường xây dựng chạy trong các container tạm thời hoặc máy ảo không có lưu trữ lâu dài và được cách ly mạng khỏi các VPC sản xuất.

---

### C4.3 An ninh mạng & Kiểm soát truy cập

Triển khai mạng lưới không tin cậy với các chính sách mặc định từ chối và truyền thông được mã hóa.

 #4.3.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng Kubernetes NetworkPolicies hoặc bất kỳ giải pháp tương đương nào thực hiện chính sách từ chối mặc định cho truy cập vào/ra với các quy tắc cho phép rõ ràng cho các cổng cần thiết (443, 8080, v.v.).
 #4.3.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng SSH (cổng 22), RDP (cổng 3389) và các điểm cuối metadata đám mây (169.254.169.254) đã bị chặn hoặc yêu cầu xác thực dựa trên chứng chỉ.
 #4.3.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng lưu lượng ra bên ngoài được lọc qua các proxy HTTP/HTTPS (Squid, Istio hoặc các cổng NAT đám mây) với danh sách cho phép miền và các yêu cầu bị chặn được ghi lại.
 #4.3.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng giao tiếp giữa các dịch vụ sử dụng mutual TLS với chứng chỉ được xoay vòng theo chính sách tổ chức và thực thi việc xác thực chứng chỉ (không bỏ qua cờ skip-verify).
 #4.3.5    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng hạ tầng AI chạy trong các VPC/VNet riêng biệt không có truy cập internet trực tiếp và chỉ giao tiếp thông qua các cổng NAT hoặc máy chủ bastion.

---

### C4.4 Quản lý Bí mật & Khóa Mã hóa

Bảo vệ thông tin đăng nhập thông qua lưu trữ dựa trên phần cứng và tự động xoay vòng với truy cập không tin cậy.

 #4.4.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các bí mật được lưu trữ trong HashiCorp Vault, AWS Secrets Manager, Azure Key Vault hoặc Google Secret Manager với mã hóa khi lưu trữ sử dụng AES-256.
 #4.4.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các khóa mật mã được tạo ra trong HSM cấp độ 2 tuân thủ FIPS 140-2 (AWS CloudHSM, Azure Dedicated HSM) với việc xoay khóa theo chính sách mật mã tổ chức.
 #4.4.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng việc xoay vòng bí mật được tự động hóa với triển khai không thời gian chết và xoay vòng ngay lập tức được kích hoạt bởi thay đổi nhân sự hoặc sự cố bảo mật.
 #4.4.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các hình ảnh container được quét bằng các công cụ (GitLeaks, TruffleHog hoặc detect-secrets) để chặn các bản build có chứa khóa API, mật khẩu hoặc chứng chỉ.
 #4.4.5    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng quyền truy cập bí mật trong môi trường sản xuất yêu cầu xác thực đa yếu tố (MFA) bằng các token phần cứng (YubiKey, FIDO2) và được ghi lại trong các nhật ký kiểm tra không thể thay đổi, kèm theo danh tính người dùng và dấu thời gian.
 #4.4.6    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các khóa bí mật được tiêm thông qua Kubernetes secrets, volumes được gắn, hoặc init containers và đảm bảo rằng các khóa bí mật không bao giờ được nhúng trong biến môi trường hoặc hình ảnh.

---

### C4.5 Đóng hộp và Xác thực Khối lượng Công việc AI

Cô lập các mô hình AI không đáng tin cậy trong các sandbox an toàn với phân tích hành vi toàn diện.

 #4.5.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các mô hình AI bên ngoài được thực thi trong gVisor, microVMs (chẳng hạn như Firecracker, CrossVM), hoặc các container Docker với các tùy chọn --security-opt=no-new-privileges và --read-only.
 #4.5.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các môi trường sandbox không có kết nối mạng (--network=none) hoặc chỉ truy cập localhost với tất cả các yêu cầu bên ngoài bị chặn bởi các quy tắc iptables.
 #4.5.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng việc xác thực mô hình AI bao gồm kiểm thử red-team tự động với phạm vi kiểm thử được xác định bởi tổ chức và phân tích hành vi để phát hiện cửa hậu.
 #4.5.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng trước khi một mô hình AI được triển khai vào sản xuất, kết quả trong môi trường thử nghiệm của nó được ký bằng mật mã bởi nhân sự an ninh có thẩm quyền và được lưu trữ trong các nhật ký kiểm toán không thể thay đổi.
 #4.5.5    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các môi trường sandbox được hủy và tái tạo từ các ảnh golden giữa các lần đánh giá với việc dọn dẹp hoàn toàn hệ thống tập tin và bộ nhớ.

---

### C4.6 Giám sát An ninh Hạ tầng

Liên tục quét và giám sát hạ tầng với việc khắc phục tự động và cảnh báo theo thời gian thực.

 #4.6.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các hình ảnh container được quét theo lịch trình của tổ chức với các lỗ hổng CRITICAL ngăn chặn việc triển khai dựa trên ngưỡng rủi ro của tổ chức.
 #4.6.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng hạ tầng đáp ứng các tiêu chuẩn CIS Benchmarks hoặc các kiểm soát NIST 800-53 theo các ngưỡng tuân thủ được tổ chức xác định và tự động khắc phục cho các kiểm tra không đạt.
 #4.6.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các lỗ hổng với mức độ nghiêm trọng CAO được vá theo tiến độ quản lý rủi ro của tổ chức với các thủ tục khẩn cấp cho các CVE đang bị khai thác tích cực.
 #4.6.4    Cấp độ: 2    Vai trò: V
 Xác nhận rằng các cảnh báo bảo mật tích hợp với các nền tảng SIEM (Splunk, Elastic, hoặc Sentinel) sử dụng định dạng CEF hoặc STIX/TAXII với khả năng làm giàu tự động.
 #4.6.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng các chỉ số hạ tầng được xuất ra hệ thống giám sát (Prometheus, DataDog) với các bảng điều khiển SLA và báo cáo điều hành.
 #4.6.6    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng sự lệch cấu hình được phát hiện bằng các công cụ (Chef InSpec, AWS Config) theo yêu cầu giám sát của tổ chức với khả năng tự động khôi phục đối với các thay đổi không được phép.

---

### Quản lý Tài nguyên Hạ tầng AI C4.7

Ngăn chặn các cuộc tấn công làm cạn kiệt tài nguyên và đảm bảo phân bổ tài nguyên công bằng thông qua hạn ngạch và giám sát.

 #4.7.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng việc sử dụng GPU/TPU được giám sát với cảnh báo được kích hoạt khi vượt ngưỡng do tổ chức xác định và tự động điều chỉnh quy mô hoặc cân bằng tải được kích hoạt dựa trên các chính sách quản lý công suất.
 #4.7.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các chỉ số khối lượng công việc AI (độ trễ suy luận, thông lượng, tỷ lệ lỗi) được thu thập theo các yêu cầu giám sát của tổ chức và được đối chiếu với mức sử dụng hạ tầng.
 #4.7.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng Kubernetes ResourceQuotas hoặc các cơ chế tương đương giới hạn từng workload theo chính sách phân bổ tài nguyên của tổ chức với các giới hạn cứng được thực thi.
 #4.7.4    Cấp độ: 2    Vai trò: V
 Xác minh rằng việc giám sát chi phí theo dõi chi tiêu theo từng khối lượng công việc/người thuê với cảnh báo dựa trên ngưỡng ngân sách tổ chức và các kiểm soát tự động cho việc vượt ngân sách.
 #4.7.5    Cấp độ: 3    Vai trò: V
 Xác nhận rằng lập kế hoạch năng lực sử dụng dữ liệu lịch sử với các khoảng thời gian dự báo được xác định theo tổ chức và cung cấp tài nguyên tự động dựa trên các mẫu nhu cầu.
 #4.7.6    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng cạn kiệt tài nguyên kích hoạt bộ ngắt mạch theo yêu cầu phản hồi của tổ chức, bao gồm giới hạn tốc độ dựa trên chính sách công suất và cách ly khối lượng công việc.

---

### C4.8 Kiểm soát Tách biệt Môi trường & Thăng tiến

Thực thi ranh giới môi trường nghiêm ngặt với các cổng thăng tiến tự động và xác nhận bảo mật.

 #4.8.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các môi trường dev/test/prod chạy trong các VPCs/VNets riêng biệt mà không chia sẻ vai trò IAM, nhóm bảo mật hoặc kết nối mạng nào.
 #4.8.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng việc thăng cấp môi trường yêu cầu phải có sự phê duyệt từ nhân sự được tổ chức xác định có thẩm quyền bằng chữ ký mật mã và các bản ghi kiểm toán không thể thay đổi.
 #4.8.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các môi trường sản xuất chặn truy cập SSH, vô hiệu hóa các điểm cuối debug và yêu cầu các yêu cầu thay đổi với điều kiện thông báo trước theo tổ chức, trừ trường hợp khẩn cấp.
 #4.8.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các thay đổi hạ tầng dưới dạng mã yêu cầu được xem xét bởi đồng nghiệp cùng với kiểm thử tự động và quét bảo mật trước khi hợp nhất vào nhánh chính.
 #4.8.5    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng dữ liệu không phải sản xuất được ẩn danh theo các yêu cầu về quyền riêng tư của tổ chức, tạo dữ liệu tổng hợp hoặc che dữ liệu hoàn toàn với việc loại bỏ thông tin nhận dạng cá nhân (PII) đã được xác minh.
 #4.8.6    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các cổng thăng tiến bao gồm các bài kiểm tra bảo mật tự động (SAST, DAST, quét container) với yêu cầu không có phát hiện nghiêm trọng (CRITICAL) nào để được phê duyệt.

---

### C4.9 Sao lưu và Phục hồi Hạ tầng

Đảm bảo khả năng phục hồi hạ tầng thông qua sao lưu tự động, quy trình khôi phục đã được kiểm tra và khả năng phục hồi sau thảm họa.

 #4.9.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các cấu hình hạ tầng được sao lưu theo lịch sao lưu của tổ chức đến các khu vực địa lý tách biệt với việc triển khai chiến lược sao lưu 3-2-1.
 #4.9.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các hệ thống sao lưu hoạt động trong các mạng tách biệt với thông tin đăng nhập riêng biệt và lưu trữ cách ly để bảo vệ chống lại ransomware.
 #4.9.3    Cấp độ: 2    Vai trò: V
 Xác minh rằng các quy trình khôi phục được kiểm tra và xác nhận thông qua kiểm thử tự động theo lịch trình tổ chức với các mục tiêu RTO và RPO đáp ứng yêu cầu của tổ chức.
 #4.9.4    Cấp độ: 3    Vai trò: V
 Xác nhận rằng phục hồi thảm họa bao gồm các runbook cụ thể cho AI với việc khôi phục trọng số mô hình, xây dựng lại cụm GPU và ánh xạ phụ thuộc dịch vụ.

---

### C4.10 Tuân thủ & Quản trị Hạ tầng

Duy trì tuân thủ quy định thông qua đánh giá liên tục, ghi chép tài liệu và kiểm soát tự động.

 #4.10.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng tuân thủ hạ tầng được đánh giá theo lịch trình của tổ chức dựa trên các kiểm soát SOC 2, ISO 27001 hoặc FedRAMP với việc thu thập bằng chứng tự động.
 #4.10.2    Cấp độ: 2    Vai trò: V
 Xác minh rằng tài liệu hạ tầng bao gồm sơ đồ mạng, bản đồ luồng dữ liệu và mô hình mối đe dọa được cập nhật theo các yêu cầu quản lý thay đổi tổ chức.
 #4.10.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các thay đổi hạ tầng trải qua đánh giá tác động tuân thủ tự động với các quy trình phê duyệt theo quy định cho các sửa đổi có rủi ro cao.

---

### C4.11 An ninh phần cứng AI

Bảo mật các thành phần phần cứng chuyên biệt cho AI bao gồm GPU, TPU và các bộ tăng tốc AI chuyên dụng.

 #4.11.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng firmware bộ tăng tốc AI (BIOS GPU, firmware TPU) được xác thực bằng chữ ký mật mã và được cập nhật theo thời gian biểu quản lý bản vá của tổ chức.
 #4.11.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng trước khi thực thi khối lượng công việc, tính toàn vẹn của bộ tăng tốc AI được xác nhận bằng chứng thực phần cứng sử dụng TPM 2.0, Intel TXT hoặc AMD SVM.
 #4.11.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng bộ nhớ GPU được cách ly giữa các khối lượng công việc sử dụng SR-IOV, MIG (Multi-Instance GPU), hoặc phân vùng phần cứng tương đương với việc làm sạch bộ nhớ giữa các công việc.
 #4.11.4    Cấp độ: 3    Vai trò: V
 Xác minh rằng chuỗi cung ứng phần cứng AI bao gồm việc xác thực nguồn gốc với các chứng nhận từ nhà sản xuất và kiểm tra tính toàn vẹn của bao bì chống giả mạo.
 #4.11.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các mô-đun bảo mật phần cứng (HSM) bảo vệ trọng số mô hình AI và khóa mật mã với chứng nhận FIPS 140-2 Cấp 3 hoặc Common Criteria EAL4+.

---

### C4.12 Hạ tầng Trí tuệ Nhân tạo Phân tán & Biên

Triển khai AI phân tán an toàn bao gồm điện toán biên, học liên kết và kiến trúc đa địa điểm.

 #4.12.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các thiết bị AI biên xác thực với hạ tầng trung tâm bằng TLS hai chiều sử dụng chứng chỉ thiết bị được thay đổi theo chính sách quản lý chứng chỉ của tổ chức.
 #4.12.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các thiết bị biên thực hiện khởi động an toàn với chữ ký đã được xác minh và bảo vệ quay lui để ngăn các cuộc tấn công hạ cấp phần mềm cơ sở.
 #4.12.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng phối hợp AI phân tán sử dụng các thuật toán đồng thuận chịu lỗi Byzantine với việc xác thực người tham gia và phát hiện nút độc hại.
 #4.12.4    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng giao tiếp từ edge đến cloud bao gồm điều tiết băng thông, nén dữ liệu và khả năng hoạt động ngoại tuyến với lưu trữ cục bộ an toàn.

---

### C4.13 Bảo mật Hạ tầng Đa đám mây & Lai

Bảo mật các khối lượng công việc AI trên nhiều nhà cung cấp đám mây và các triển khai đám mây lai kết hợp tại chỗ.

 #4.13.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng việc triển khai AI đa đám mây sử dụng liên kết danh tính không phụ thuộc vào đám mây (OIDC, SAML) với quản lý chính sách tập trung trên các nhà cung cấp.
 #4.13.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng việc chuyển dữ liệu chéo đám mây sử dụng mã hóa đầu cuối với khóa do khách hàng quản lý và kiểm soát cư trú dữ liệu được thực thi theo từng khu vực pháp lý.
 #4.13.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các khối lượng công việc AI đám mây lai thực hiện chính sách bảo mật nhất quán trên cả môi trường tại chỗ và đám mây với giám sát và cảnh báo thống nhất.
 #4.13.4    Cấp độ: 3    Vai trò: V
 Xác nhận rằng việc ngăn ngừa khóa nhà cung cấp đám mây bao gồm hạ tầng dưới dạng mã có thể di động, các API chuẩn hóa và khả năng xuất dữ liệu với công cụ chuyển đổi định dạng.
 #4.13.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng tối ưu hóa chi phí đa đám mây bao gồm các biện pháp kiểm soát bảo mật ngăn ngừa sự lan rộng tài nguyên cũng như các khoản phí chuyển dữ liệu không được phép giữa các đám mây.

---

### C4.14 Tự động hóa Hạ tầng & Bảo mật GitOps

Tự động hóa các pipeline hạ tầng bảo mật và quy trình làm việc GitOps cho quản lý hạ tầng AI.

 #4.14.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các kho GitOps yêu cầu các cam kết được ký bằng khóa GPG và có các quy tắc bảo vệ nhánh ngăn chặn việc đẩy trực tiếp lên các nhánh chính.
 #4.14.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng tự động hóa hạ tầng bao gồm phát hiện sai lệch với khả năng khắc phục và phục hồi tự động được kích hoạt theo yêu cầu phản hồi của tổ chức đối với các thay đổi không được phép.
 #4.14.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng việc cung cấp hạ tầng tự động bao gồm xác nhận chính sách bảo mật với việc chặn triển khai đối với các cấu hình không tuân thủ.
 #4.14.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các bí mật tự động hóa hạ tầng được quản lý thông qua các bộ điều hành bí mật bên ngoài (External Secrets Operator, Bank-Vaults) với chức năng tự động xoay vòng.
 #4.14.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng hạ tầng tự phục hồi bao gồm việc kết hợp sự kiện bảo mật với phản ứng sự cố tự động và các quy trình thông báo cho các bên liên quan.

---

### C4.15 An ninh Hạ tầng Kháng Lượng tử

Chuẩn bị hạ tầng AI để đối phó với các mối đe dọa từ điện toán lượng tử thông qua mật mã hậu lượng tử và các giao thức an toàn lượng tử.

 #4.15.1    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng hạ tầng AI triển khai các thuật toán mật mã hậu lượng tử được NIST phê duyệt (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) cho trao đổi khóa và chữ ký số.
 #4.15.2    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các hệ thống phân phối khóa lượng tử (QKD) được triển khai cho truyền thông AI có bảo mật cao với các giao thức quản lý khóa an toàn với lượng tử.
 #4.15.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các khung linh hoạt mật mã cho phép di chuyển nhanh chóng sang các thuật toán hậu lượng tử mới với việc tự động xoay vòng chứng chỉ và khóa.
 #4.15.4    Cấp độ: 3    Vai trò: V
 Xác minh rằng mô hình hóa mối đe dọa lượng tử đánh giá mức độ dễ bị tấn công của hạ tầng AI trước các cuộc tấn công lượng tử với các mốc thời gian di cư được ghi chép và đánh giá rủi ro.
 #4.15.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các hệ thống mật mã lai cổ điển-khối lượng tử cung cấp phòng thủ đa lớp trong giai đoạn chuyển tiếp lượng tử cùng với việc giám sát hiệu suất.

---

### C4.16 Tính Toán Bảo Mật & Khu Vực Bảo Mật An Toàn

Bảo vệ các khối lượng công việc AI và trọng số mô hình bằng cách sử dụng môi trường thực thi đáng tin cậy dựa trên phần cứng và công nghệ điện toán bảo mật.

 #4.16.1    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các mô hình AI nhạy cảm chạy bên trong các vùng enclave Intel SGX, AMD SEV-SNP hoặc ARM TrustZone với bộ nhớ được mã hóa và xác thực attest.
 #4.16.2    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các container bảo mật (Kata Containers, gVisor với tính toán bảo mật) cách ly các khối công việc AI bằng mã hóa bộ nhớ được thực thi bởi phần cứng.
 #4.16.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng việc chứng thực từ xa xác nhận tính toàn vẹn của enclave trước khi tải các mô hình AI bằng chứng mật mã về tính xác thực của môi trường thực thi.
 #4.16.4    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng các dịch vụ suy luận AI bảo mật ngăn chặn việc trích xuất mô hình thông qua tính toán được mã hóa với trọng số mô hình được đóng gói và thực thi được bảo vệ.
 #4.16.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng điều phối môi trường thực thi tin cậy quản lý vòng đời vùng bảo mật với xác thực từ xa và các kênh truyền thông được mã hóa.
 #4.16.6    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng tính toán đa bên bảo mật (SMPC) cho phép đào tạo AI hợp tác mà không tiết lộ bộ dữ liệu cá nhân hoặc các tham số mô hình.

---

### C4.17 Hạ tầng Không Kiến thức

Triển khai các hệ thống bằng chứng không tiết lộ để xác minh và xác thực AI bảo vệ quyền riêng tư mà không tiết lộ thông tin nhạy cảm.

 #4.17.1    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng bằng chứng không tiết lộ thông tin (ZK-SNARKs, ZK-STARKs) xác thực tính toàn vẹn của mô hình AI và nguồn gốc đào tạo mà không tiết lộ trọng số mô hình hoặc dữ liệu đào tạo.
 #4.17.2    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các hệ thống xác thực dựa trên ZK cho phép xác minh người dùng bảo vệ quyền riêng tư cho các dịch vụ AI mà không tiết lộ thông tin liên quan đến danh tính.
 #4.17.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các giao thức giao điểm tập hợp riêng tư (PSI) cho phép đối chiếu dữ liệu an toàn cho AI liên kết mà không làm lộ các tập dữ liệu cá nhân.
 #4.17.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các hệ thống học máy không tiết lộ thông tin (ZKML) cho phép suy luận AI có thể xác minh với bằng chứng mật mã về tính đúng đắn của phép tính.
 #4.17.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng ZK-rollups cung cấp xử lý giao dịch AI có khả năng mở rộng, bảo vệ quyền riêng tư với xác minh theo lô và giảm tải tính toán.

---

### C4.18 Ngăn ngừa Tấn công Kênh bên

Bảo vệ hạ tầng AI khỏi các cuộc tấn công kênh bên dựa trên thời gian, năng lượng, điện từ và bộ nhớ đệm có thể làm rò rỉ thông tin nhạy cảm.

 #4.18.1    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng thời gian suy luận AI được chuẩn hóa bằng cách sử dụng các thuật toán thời gian không đổi và thêm đệm để ngăn chặn các cuộc tấn công trích xuất mô hình dựa trên thời gian.
 #4.18.2    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng bảo vệ phân tích công suất bao gồm việc tiêm nhiễu, lọc dòng điện và các mô hình thực thi ngẫu nhiên cho phần cứng AI.
 #4.18.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng biện pháp giảm thiểu kênh bên bên dựa trên bộ nhớ đệm sử dụng phân vùng bộ nhớ đệm, ngẫu nhiên hóa và các lệnh xả để ngăn chặn rò rỉ thông tin.
 #4.18.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng bảo vệ phát xạ điện từ bao gồm che chắn, lọc tín hiệu và xử lý ngẫu nhiên để ngăn chặn các cuộc tấn công kiểu TEMPEST.
 #4.18.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các biện pháp phòng thủ kênh bên vi kiến trúc bao gồm kiểm soát thực thi dự đoán và che giấu mẫu truy cập bộ nhớ.

---

### C4.19 An ninh Phần cứng AI Chuyên biệt & Như thần kinh

Bảo mật các kiến trúc phần cứng AI mới nổi bao gồm chip thần kinh, FPGA, ASIC tùy chỉnh và hệ thống tính toán quang học.

 #4.19.1    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng bảo mật chip thần kinh bao gồm mã hóa mẫu xung, bảo vệ trọng số kết nối thần kinh, và xác thực quy tắc học dựa trên phần cứng.
 #4.19.2    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các bộ tăng tốc AI dựa trên FPGA thực hiện mã hóa bitstream, cơ chế chống giả mạo và quá trình tải cấu hình an toàn với các bản cập nhật có xác thực.
 #4.19.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng bảo mật ASIC tùy chỉnh bao gồm các bộ xử lý bảo mật trên chip, gốc tin cậy phần cứng, và lưu trữ khóa an toàn với khả năng phát hiện can thiệp.
 #4.19.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các hệ thống điện toán quang học triển khai mã hóa quang an toàn lượng tử, chuyển mạch quang học bảo mật và xử lý tín hiệu quang được bảo vệ.
 #4.19.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng chip AI lai tương tự-số bao gồm tính toán tương tự an toàn, lưu trữ trọng số được bảo vệ và chuyển đổi tương tự-số được xác thực.

---

### C4.20 Hạ tầng Tính toán Bảo vệ Quyền riêng tư

Triển khai các biện pháp kiểm soát hạ tầng cho tính toán bảo vệ quyền riêng tư nhằm bảo vệ dữ liệu nhạy cảm trong quá trình xử lý và phân tích AI.

 #4.20.1    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng cơ sở hạ tầng mã hóa đồng hình cho phép tính toán được mã hóa trên các khối lượng công việc AI nhạy cảm với việc xác thực tính toàn vẹn mật mã và giám sát hiệu suất.
 #4.20.2    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng các hệ thống truy xuất thông tin riêng tư cho phép truy vấn cơ sở dữ liệu mà không tiết lộ mẫu truy vấn, đồng thời bảo vệ mật mã các mẫu truy cập.
 #4.20.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các giao thức tính toán đa bên an toàn cho phép suy luận AI bảo vệ quyền riêng tư mà không tiết lộ các đầu vào cá nhân hoặc các phép tính trung gian.
 #4.20.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng quản lý khóa bảo vệ quyền riêng tư bao gồm tạo khóa phân tán, mật mã ngưỡng, và xoay khóa an toàn với bảo vệ phần cứng.
 #4.20.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng hiệu suất tính toán bảo vệ quyền riêng tư được tối ưu hóa thông qua việc gom nhóm, lưu bộ nhớ đệm và tăng tốc phần cứng đồng thời duy trì các đảm bảo bảo mật mật mã học.

---

### C4.15 Bảo mật Tích hợp Đám mây và Triển khai Lai trong Khung Agent

Các biện pháp kiểm soát bảo mật cho các khung tác tử tích hợp đám mây với kiến trúc lai tại chỗ/đám mây.

 #4.15.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng tích hợp lưu trữ đám mây sử dụng mã hóa đầu cuối với quản lý khóa do tác nhân kiểm soát.
 #4.15.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng ranh giới bảo mật của triển khai lai được xác định rõ ràng với các kênh giao tiếp được mã hóa.
 #4.15.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng truy cập tài nguyên đám mây bao gồm xác thực không tin cậy với việc xác thực liên tục.
 #4.15.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các yêu cầu về cư trú dữ liệu được thực thi thông qua chứng nhận mật mã về vị trí lưu trữ.
 #4.15.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các đánh giá bảo mật của nhà cung cấp đám mây bao gồm việc mô hình hóa mối đe dọa và đánh giá rủi ro cụ thể cho từng tác nhân.

---

### Tài liệu tham khảo

NIST Cybersecurity Framework 2.0
CIS Controls v8
OWASP Container Security Verification Standard
Kubernetes Security Best Practices
SLSA Supply Chain Security Framework
NIST SP 800-190: Application Container Security Guide
Cloud Security Alliance: Cloud Controls Matrix
ENISA: Secure Infrastructure Design
NIST SP 800-53: Security Controls for Federal Information Systems
ISO 27001:2022 Information Security Management
NIST AI Risk Management Framework
CIS Kubernetes Benchmark
FIPS 140-2 Security Requirements
NIST SP 800-207: Zero Trust Architecture
IEEE 2857: Privacy Engineering for AI Systems
NIST SP 800-161: Cybersecurity Supply Chain Risk Management
NIST Post-Quantum Cryptography Standards
Intel SGX Developer Guide
AMD SEV-SNP White Paper
ARM TrustZone Technology
ZK-SNARKs: A Gentle Introduction
NIST SP 800-57: Cryptographic Key Management
Side-Channel Attack Countermeasures
Neuromorphic Computing Security Challenges
FPGA Security: Fundamentals, Evaluation, and Countermeasures
Microsoft SEAL: Homomorphic Encryption Library
HElib: Homomorphic Encryption Library
PALISADE Lattice Cryptography Library
Differential Privacy: A Survey of Results
Secure Aggregation for Federated Learning
Private Information Retrieval: Concepts and Constructions

## Kiểm soát truy cập C5 & Danh tính cho các Thành phần & Người dùng AI

### Mục tiêu Kiểm soát

Kiểm soát truy cập hiệu quả cho các hệ thống AI đòi hỏi quản lý nhận dạng vững chắc, ủy quyền nhận biết ngữ cảnh và thực thi trong thời gian chạy theo các nguyên tắc không tin cậy. Các biện pháp kiểm soát này đảm bảo rằng con người, dịch vụ và tác nhân tự động chỉ tương tác với các mô hình, dữ liệu và tài nguyên tính toán trong phạm vi được cấp phép rõ ràng, kèm theo khả năng xác minh và kiểm tra liên tục.

---

### C5.1 Quản lý danh tính & Xác thực

Thiết lập danh tính được bảo mật bằng mật mã cho tất cả các thực thể với xác thực đa yếu tố cho các thao tác đặc quyền.

 #5.1.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng tất cả người dùng là con người và các nguyên tắc dịch vụ đều xác thực thông qua một nhà cung cấp nhận dạng doanh nghiệp tập trung (IdP) sử dụng các giao thức OIDC/SAML với các ánh xạ định danh tới token duy nhất (không sử dụng tài khoản hoặc thông tin xác thực chia sẻ).
 #5.1.2    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng các hoạt động có rủi ro cao (triển khai mô hình, xuất trọng số, truy cập dữ liệu đào tạo, thay đổi cấu hình sản xuất) yêu cầu xác thực đa yếu tố hoặc xác thực nâng cao với xác thực lại phiên làm việc.
 #5.1.3    Cấp độ: 2    Vai trò: D
 Xác minh rằng các giám đốc mới trải qua quá trình chứng thực danh tính phù hợp với NIST 800-63-3 IAL-2 hoặc các tiêu chuẩn tương đương trước khi được cấp quyền truy cập vào hệ thống sản xuất.
 #5.1.4    Cấp độ: 2    Vai trò: V
 Xác minh rằng các đánh giá truy cập được thực hiện hàng quý với việc phát hiện tự động các tài khoản không hoạt động, thực thi việc xoay vòng thông tin xác thực, và các quy trình gỡ bỏ quyền truy cập.
 #5.1.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các tác nhân AI liên kết xác thực thông qua các khẳng định JWT được ký có thời hạn tối đa là 24 giờ và bao gồm bằng chứng mật mã về nguồn gốc.

---

### C5.2 Ủy quyền Tài nguyên & Quyền tối thiểu

Triển khai các kiểm soát truy cập chi tiết cho tất cả tài nguyên AI với mô hình cấp phép rõ ràng và các đường dẫn kiểm toán.

 #5.2.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng mọi tài nguyên AI (bộ dữ liệu, mô hình, điểm cuối, bộ sưu tập vectơ, chỉ mục nhúng, phiên bản tính toán) đều thực thi kiểm soát truy cập dựa trên vai trò với danh sách cho phép rõ ràng và chính sách mặc định từ chối.
 #5.2.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các nguyên tắc quyền hạn tối thiểu được thực thi theo mặc định với các tài khoản dịch vụ, bắt đầu với quyền chỉ đọc và yêu cầu có tài liệu lý do kinh doanh cho quyền ghi.
 #5.2.3    Cấp độ: 1    Vai trò: V
 Xác minh rằng tất cả các sửa đổi kiểm soát truy cập đều được liên kết với các yêu cầu thay đổi đã được phê duyệt và được ghi lại một cách không thể thay đổi với dấu thời gian, danh tính người thực hiện, định danh tài nguyên và sự khác biệt về quyền hạn.
 #5.2.4    Cấp độ: 2    Vai trò: D
 Xác minh rằng nhãn phân loại dữ liệu (PII, PHI, kiểm soát xuất khẩu, sở hữu độc quyền) tự động lan truyền đến các tài nguyên dẫn xuất (embedding, bộ nhớ đệm prompt, kết quả mô hình) với việc thực thi chính sách nhất quán.
 #5.2.5    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các lần cố gắng truy cập trái phép và sự kiện leo thang đặc quyền kích hoạt cảnh báo thời gian thực với siêu dữ liệu ngữ cảnh gửi đến hệ thống SIEM trong vòng 5 phút.

---

### C5.3 Đánh giá Chính sách Động

Triển khai các bộ máy kiểm soát truy cập dựa trên thuộc tính (ABAC) để đưa ra quyết định ủy quyền nhận thức ngữ cảnh với khả năng kiểm tra.

 #5.3.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các quyết định ủy quyền được tách ra ngoài tới một công cụ chính sách chuyên dụng (OPA, Cedar, hoặc tương đương) có thể truy cập qua các API được xác thực với bảo vệ toàn vẹn bằng mật mã.
 #5.3.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các chính sách đánh giá các thuộc tính động tại thời điểm chạy bao gồm mức độ rõ ràng của người dùng, phân loại độ nhạy cảm của tài nguyên, ngữ cảnh yêu cầu, sự cô lập của người thuê, và các ràng buộc thời gian.
 #5.3.3    Cấp độ: 2    Vai trò: D
 Xác minh rằng các định nghĩa chính sách được kiểm soát phiên bản, được đồng nghiệp đánh giá và được xác thực thông qua kiểm thử tự động trong các pipeline CI/CD trước khi triển khai sản xuất.
 #5.3.4    Cấp độ: 2    Vai trò: V
 Xác minh rằng kết quả đánh giá chính sách bao gồm các lý do quyết định có cấu trúc và được truyền đến các hệ thống SIEM để phân tích tương quan và báo cáo tuân thủ.
 #5.3.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng giá trị thời gian tồn tại bộ nhớ đệm chính sách (TTL) không vượt quá 5 phút đối với các tài nguyên có độ nhạy cao và 1 giờ đối với các tài nguyên tiêu chuẩn có khả năng vô hiệu hóa bộ nhớ đệm.

---

### C5.4 Thực thi An ninh khi Truy vấn

Triển khai các biện pháp kiểm soát bảo mật ở lớp cơ sở dữ liệu với việc lọc bắt buộc và các chính sách bảo mật cấp hàng.

 #5.4.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng tất cả các truy vấn cơ sở dữ liệu vector và SQL đều bao gồm các bộ lọc bảo mật bắt buộc (ID khách thuê, nhãn độ nhạy, phạm vi người dùng) được thực thi ở cấp độ động cơ cơ sở dữ liệu, không phải mã ứng dụng.
 #5.4.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các chính sách bảo mật cấp hàng (RLS) và che giấu cấp trường được bật với kế thừa chính sách cho tất cả các cơ sở dữ liệu vector, chỉ số tìm kiếm và tập dữ liệu đào tạo.
 #5.4.3    Cấp độ: 2    Vai trò: D
 Xác minh rằng các đánh giá ủy quyền không thành công sẽ ngăn chặn "các cuộc tấn công đại lý nhầm lẫn" bằng cách ngay lập tức hủy bỏ các truy vấn và trả về mã lỗi ủy quyền rõ ràng thay vì trả về các tập kết quả rỗng.
 #5.4.4    Cấp độ: 2    Vai trò: V
 Xác minh rằng độ trễ đánh giá chính sách được giám sát liên tục với các cảnh báo tự động về các điều kiện thời gian chờ có thể cho phép vượt qua ủy quyền.
 #5.4.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các cơ chế thử lại truy vấn đánh giá lại các chính sách cấp quyền để tính đến các thay đổi quyền động trong các phiên người dùng đang hoạt động.

---

### Lọc Đầu Ra C5.5 & Ngăn Ngừa Mất Dữ Liệu

Triển khai các biện pháp kiểm soát xử lý hậu kỳ để ngăn chặn việc tiết lộ dữ liệu trái phép trong nội dung do AI tạo ra.

 #5.5.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các cơ chế lọc sau suy luận quét và chỉnh sửa thông tin nhận dạng cá nhân (PII) không được phép, thông tin phân loại và dữ liệu độc quyền trước khi cung cấp nội dung cho người yêu cầu.
 #5.5.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các trích dẫn, tham khảo và ghi nguồn trong kết quả mô hình được xác thực dựa trên quyền truy cập của người gọi và loại bỏ nếu phát hiện truy cập không được phép.
 #5.5.3    Cấp độ: 2    Vai trò: D
 Xác minh rằng các hạn chế về định dạng đầu ra (PDF đã được làm sạch, hình ảnh đã loại bỏ siêu dữ liệu, các loại tệp được phê duyệt) được thực thi dựa trên cấp độ quyền người dùng và phân loại dữ liệu.
 #5.5.4    Cấp độ: 2    Vai trò: V
 Xác minh rằng các thuật toán che khuất thông tin có tính xác định, được kiểm soát phiên bản và duy trì nhật ký kiểm toán để hỗ trợ điều tra tuân thủ và phân tích pháp y.
 #5.5.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng các sự kiện biên tập rủi ro cao tạo ra nhật ký thích ứng bao gồm các hàm băm mật mã của nội dung gốc để truy xuất pháp y mà không làm lộ dữ liệu.

---

### C5.6 Cách ly đa người thuê

Đảm bảo sự cô lập về mật mã và logic giữa các khách thuê trong hạ tầng AI chia sẻ.

 #5.6.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng không gian bộ nhớ, kho lưu trữ embedding, mục cache và tập tin tạm thời được phân tách theo không gian tên cho từng tenant, kèm theo việc xóa an toàn khi tenant bị xóa hoặc phiên làm việc kết thúc.
 #5.6.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng mọi yêu cầu API đều bao gồm một định danh người thuê đã được xác thực, được xác minh mật mã dựa trên ngữ cảnh phiên và quyền của người dùng.
 #5.6.3    Cấp độ: 2    Vai trò: D
 Xác minh rằng các chính sách mạng triển khai các quy tắc từ chối-mặc định cho giao tiếp giữa các thuê bao trong các dịch vụ mạng lõi và các nền tảng điều phối container.
 #5.6.4    Cấp độ: 3    Vai trò: D
 Xác minh rằng các khóa mã hóa là duy nhất theo từng người thuê với hỗ trợ khóa do khách hàng quản lý (CMK) và sự cách ly mật mã giữa các kho dữ liệu người thuê.

---

### C5.7 Ủy quyền Đại lý Tự động

Kiểm soát quyền hạn cho các tác nhân AI và hệ thống tự động thông qua token khả năng có phạm vi và cấp phép liên tục.

 #5.7.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các tác nhân tự động nhận được các token khả năng có phạm vi, trong đó liệt kê rõ ràng các hành động được phép, tài nguyên có thể truy cập, giới hạn thời gian và các ràng buộc vận hành.
 #5.7.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các khả năng có rủi ro cao (truy cập hệ thống file, thực thi mã, gọi API bên ngoài, giao dịch tài chính) được vô hiệu hóa theo mặc định và yêu cầu sự cho phép rõ ràng để kích hoạt kèm theo lý do kinh doanh hợp lý.
 #5.7.3    Cấp độ: 2    Vai trò: D
 Xác minh rằng các token khả năng được liên kết với các phiên người dùng, bao gồm bảo vệ tính toàn vẹn bằng mật mã, và đảm bảo rằng chúng không thể được lưu trữ hoặc tái sử dụng trong các tình huống ngoại tuyến.
 #5.7.4    Cấp độ: 2    Vai trò: V
 Xác minh rằng các hành động do đại lý khởi xướng được thực hiện qua việc ủy quyền phụ thông qua bộ máy chính sách ABAC với đánh giá bối cảnh đầy đủ và ghi nhận kiểm toán.
 #5.7.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng các điều kiện lỗi của tác nhân và xử lý ngoại lệ bao gồm thông tin phạm vi khả năng để hỗ trợ phân tích sự cố và điều tra pháp y.

---

### Tài liệu tham khảo

#### Tiêu chuẩn & Khung làm việc

NIST SP 800-63-3: Digital Identity Guidelines
Zero Trust Architecture – NIST SP 800-207
OWASP Application Security Verification Standard (AISVS)
​
#### Hướng dẫn triển khai

Identity and Access Management in the AI Era: 2025 Guide – IDSA
Attribute-Based Access Control with OPA – Permify
How We Designed Cedar to Be Intuitive, Fast, and Safe – AWS
​
#### An ninh dành riêng cho AI

Row Level Security in Vector DBs for RAG – Bluetuple.ai
Tenant Isolation in Multi-Tenant Systems – WorkOS
Handling AI Agent Permissions – Stytch
OWASP Top 10 for Large Language Model Applications

## Bảo mật Chuỗi Cung ứng C6 cho Mô hình, Khung và Dữ liệu

### Mục tiêu Kiểm soát

Các cuộc tấn công chuỗi cung ứng AI lợi dụng các mô hình, khung, hoặc bộ dữ liệu bên thứ ba để cài đặt cửa hậu, định kiến, hoặc mã dễ bị khai thác. Các biện pháp kiểm soát này cung cấp nguồn gốc từ đầu đến cuối, quản lý lỗ hổng và giám sát nhằm bảo vệ toàn bộ vòng đời mô hình.

---

### C6.1 Kiểm tra mô hình tiền huấn luyện & Nguồn gốc

Đánh giá và xác thực nguồn gốc, giấy phép, và các hành vi ẩn của mô hình bên thứ ba trước khi thực hiện tinh chỉnh hoặc triển khai.

 #6.1.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng mọi sản phẩm mô hình bên thứ ba đều bao gồm một bản ghi xuất xứ được ký xác nhận, xác định kho lưu trữ nguồn và mã băm cam kết.
 #6.1.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các mô hình được quét để phát hiện các lớp độc hại hoặc kích hoạt Trojan bằng công cụ tự động trước khi nhập khẩu.
 #6.1.3    Cấp độ: 2    Vai trò: D
 Xác minh rằng việc tinh chỉnh học chuyển giao vượt qua đánh giá đối kháng để phát hiện các hành vi ẩn.
 #6.1.4    Cấp độ: 2    Vai trò: V
 Xác nhận rằng giấy phép mô hình, nhãn kiểm soát xuất khẩu và các tuyên bố nguồn gốc dữ liệu được ghi lại trong một mục ML-BOM.
 #6.1.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các mô hình rủi ro cao (trọng số được tải lên công khai, nhà tạo chưa được xác minh) vẫn được cách ly cho đến khi được đánh giá và phê duyệt bởi con người.

---

### C6.2 Quét Khung và Thư viện

Liên tục quét các framework và thư viện ML để phát hiện CVE và mã độc nhằm giữ an toàn cho ngăn xếp thời gian chạy.

 #6.2.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các pipeline CI chạy trình quét phụ thuộc trên các framework AI và các thư viện quan trọng.
 #6.2.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các lỗ hổng nghiêm trọng (CVSS ≥ 7.0) ngăn chặn việc thăng cấp lên các ảnh sản xuất.
 #6.2.3    Cấp độ: 2    Vai trò: D
 Xác minh rằng phân tích mã tĩnh chạy trên các thư viện ML được fork hoặc vendored.
 #6.2.4    Cấp độ: 2    Vai trò: V
 Xác nhận rằng các đề xuất nâng cấp khung làm việc bao gồm một đánh giá ảnh hưởng bảo mật tham chiếu đến các nguồn dữ liệu CVE công khai.
 #6.2.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng các cảm biến thời gian chạy cảnh báo về việc tải thư viện động không mong đợi, có sự sai lệch so với SBOM đã được ký.

---

### C6.3 Ghim phụ thuộc & Xác minh

Ghim mọi phụ thuộc vào các bản tóm tắt không thể thay đổi và tái tạo các bản dựng để đảm bảo các tác phẩm giống hệt nhau, không bị giả mạo.

 #6.3.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng tất cả các trình quản lý gói đều thực thi việc cố định phiên bản thông qua các tệp khóa.
 #6.3.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các chữ ký băm không thay đổi được sử dụng thay vì các nhãn có thể thay đổi trong các tham chiếu container.
 #6.3.3    Cấp độ: 2    Vai trò: D
 Xác minh rằng các kiểm tra xây dựng có thể tái tạo so sánh các hàm băm giữa các lần chạy CI để đảm bảo kết quả đầu ra giống hệt nhau.
 #6.3.4    Cấp độ: 2    Vai trò: V
 Xác nhận rằng các chứng thực xây dựng được lưu trữ trong 18 tháng để có thể truy xuất kiểm toán.
 #6.3.5    Cấp độ: 3    Vai trò: D
 Xác nhận rằng các phụ thuộc hết hạn kích hoạt các PR tự động để cập nhật hoặc fork các phiên bản đã cố định.

---

### C6.4 Thực thi Nguồn Tin Cậy

Chỉ cho phép tải các tệp artifact từ các nguồn được tổ chức phê duyệt và xác minh bằng mật mã, và chặn tất cả các nguồn khác.

 #6.4.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng trọng số mô hình, bộ dữ liệu và container chỉ được tải xuống từ các miền được phê duyệt hoặc các registry nội bộ.
 #6.4.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các chữ ký Sigstore/Cosign xác thực danh tính nhà xuất bản trước khi các bản ghi được lưu vào bộ nhớ đệm cục bộ.
 #6.4.3    Cấp độ: 2    Vai trò: D
 Xác minh rằng các proxy xuất cảnh chặn việc tải xuống artifact không được xác thực để thực thi chính sách nguồn tin cậy.
 #6.4.4    Cấp độ: 2    Vai trò: V
 Xác minh rằng danh sách cho phép của kho lưu trữ được xem xét hàng quý với bằng chứng về lý do kinh doanh cho từng mục nhập.
 #6.4.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng các vi phạm chính sách kích hoạt việc cách ly các hiện vật và hoàn nguyên các lần chạy ống dẫn phụ thuộc.

---

### C6.5 Đánh giá rủi ro bộ dữ liệu bên thứ ba

Đánh giá các bộ dữ liệu bên ngoài về việc đầu độc, thiên vị và tuân thủ pháp lý, đồng thời theo dõi chúng trong suốt vòng đời của chúng.

 #6.5.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các bộ dữ liệu bên ngoài được đánh giá rủi ro nhiễm độc (ví dụ: xác định dấu vân tay dữ liệu, phát hiện điểm bất thường).
 #6.5.2    Cấp độ: 1    Vai trò: D
 Xác minh rằng các chỉ số thiên lệch (cân bằng nhân khẩu học, cơ hội bình đẳng) được tính toán trước khi phê duyệt bộ dữ liệu.
 #6.5.3    Cấp độ: 2    Vai trò: V
 Xác minh rằng nguồn gốc và các điều khoản giấy phép của bộ dữ liệu được ghi lại trong các mục ML‑BOM.
 #6.5.4    Cấp độ: 2    Vai trò: V
 Xác minh rằng việc giám sát định kỳ phát hiện được sự dịch chuyển hoặc hư hỏng trong các tập dữ liệu được lưu trữ.
 #6.5.5    Cấp độ: 3    Vai trò: D
 Xác nhận rằng nội dung bị cấm (bản quyền, thông tin nhận dạng cá nhân) đã được loại bỏ thông qua việc làm sạch tự động trước khi đào tạo.

---

### C6.6 Giám sát Tấn công Chuỗi Cung ứng

Phát hiện sớm các mối đe dọa chuỗi cung ứng thông qua nguồn cấp dữ liệu CVE, phân tích nhật ký kiểm toán và mô phỏng đội đỏ.

 #6.6.1    Cấp độ: 1    Vai trò: V
 Xác minh rằng nhật ký kiểm tra CI/CD được truyền đến các hệ thống phát hiện SIEM để phát hiện các trường hợp kéo gói bất thường hoặc các bước xây dựng bị can thiệp.
 #6.6.2    Cấp độ: 2    Vai trò: D
 Xác minh rằng các sổ tay phản ứng sự cố bao gồm các quy trình hoàn tác cho các mô hình hoặc thư viện bị xâm phạm.
 #6.6.3    Cấp độ: 3    Vai trò: V
 Xác minh rằng việc làm giàu thông tin tình báo đe dọa gắn nhãn các chỉ số đặc thù của ML (ví dụ: các IoC liên quan đến tấn công đầu độc mô hình) trong quá trình phân loại cảnh báo.

---

### C6.7 ML‑BOM cho Tác phẩm Mô hình

Tạo và ký các SBOM chi tiết dành riêng cho ML (ML-BOM) để người tiêu dùng dòng dưới có thể xác minh tính toàn vẹn của thành phần tại thời điểm triển khai.

 #6.7.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng mọi sản phẩm mô hình đều công bố một ML‑BOM liệt kê các tập dữ liệu, trọng số, siêu tham số và giấy phép.
 #6.7.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng việc tạo ML‑BOM và ký Cosign được tự động hóa trong CI và là điều kiện bắt buộc để hợp nhất.
 #6.7.3    Cấp độ: 2    Vai trò: D
 Xác minh rằng các kiểm tra hoàn chỉnh ML-BOM sẽ làm cho việc xây dựng thất bại nếu bất kỳ siêu dữ liệu thành phần nào (băm, giấy phép) bị thiếu.
 #6.7.4    Cấp độ: 2    Vai trò: V
 Xác minh rằng các bên tiêu thụ hạ nguồn có thể truy vấn ML-BOMs thông qua API để xác thực các mô hình đã nhập khi triển khai.
 #6.7.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng các ML‑BOM được kiểm soát phiên bản và so sánh sự khác biệt để phát hiện các sửa đổi không được phép.

---

### Tài liệu tham khảo

ML Supply Chain Compromise – MITRE ATLAS
Supply‑chain Levels for Software Artifacts (SLSA)
CycloneDX – Machine Learning Bill of Materials
What is Data Poisoning? – SentinelOne
Transfer Learning Attack – OWASP ML Security Top 10
AI Data Security Best Practices – CISA
Secure CI/CD Supply Chain – Sumo Logic
AI & Transparency: Protect ML Models – ReversingLabs
SBOM Overview – CISA
Training Data Poisoning Guide – Lakera.ai
Dependency Pinning for Reproducible Python – Medium

## Hành vi Mô hình C7, Kiểm soát Đầu ra & Đảm bảo An toàn

### Mục tiêu Kiểm soát

Đầu ra của mô hình phải có cấu trúc, đáng tin cậy, an toàn, có thể giải thích và được giám sát liên tục trong môi trường sản xuất. Làm như vậy giúp giảm các hiện tượng ảo tưởng, rò rỉ thông tin cá nhân, nội dung gây hại và hành động mất kiểm soát, đồng thời tăng sự tin tưởng của người dùng và tuân thủ quy định.

---

### C7.1 Thực thi Định dạng Đầu ra

Các sơ đồ nghiêm ngặt, giải mã có giới hạn, và xác thực hạ nguồn ngăn chặn nội dung sai định dạng hoặc độc hại trước khi nó lan truyền.

 #7.1.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các sơ đồ phản hồi (ví dụ: JSON Schema) được cung cấp trong lời nhắc hệ thống và mọi kết quả đầu ra đều được tự động xác thực; các kết quả không tuân thủ sẽ kích hoạt sửa chữa hoặc từ chối.
 #7.1.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng giải mã có giới hạn (token dừng, regex, max-tokens) đã được bật để ngăn ngừa tràn bộ đệm hoặc các kênh phụ tiêm nhúng prompt.
 #7.1.3    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng các thành phần hạ nguồn coi đầu ra là không đáng tin cậy và xác thực chúng dựa trên các sơ đồ hoặc bộ giải tuần tự an toàn chống tiêm nhiễm.
 #7.1.4    Cấp độ: 3    Vai trò: V
 Xác minh rằng các sự kiện đầu ra không đúng được ghi lại, giới hạn tốc độ và hiển thị trên hệ thống giám sát.

---

### C7.2 Phát hiện và Giảm thiểu Ảo giác

Ước lượng sự không chắc chắn và các chiến lược dự phòng giúp hạn chế các câu trả lời giả mạo.

 #7.2.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng xác suất log cấp token, sự nhất quán bản thân của tập hợp, hoặc các bộ phát hiện ảo tưởng đã được tinh chỉnh gán một điểm độ tin cậy cho mỗi câu trả lời.
 #7.2.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các phản hồi có mức độ tin cậy thấp hơn ngưỡng cấu hình sẽ kích hoạt các quy trình dự phòng (ví dụ: tạo sinh tăng cường truy xuất, mô hình thứ cấp hoặc đánh giá của con người).
 #7.2.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các sự cố ảo giác được gắn thẻ với siêu dữ liệu nguyên nhân gốc rễ và được đưa vào quy trình phân tích sự cố sau và tinh chỉnh lại.
 #7.2.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các ngưỡng và bộ phát hiện được cân chỉnh lại sau các cập nhật quan trọng về mô hình hoặc cơ sở tri thức.
 #7.2.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng các biểu đồ trên bảng điều khiển theo dõi tỷ lệ ảo tưởng.

---

### C7.3 Lọc An toàn & Riêng tư Đầu ra

Bộ lọc chính sách và phạm vi đội đỏ bảo vệ người dùng và dữ liệu mật.

 #7.3.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các bộ phân loại trước và sau khi tạo nội dung chặn các nội dung về thù địch, quấy rối, tự làm hại, cực đoan và nội dung mang tính khiêu dâm phù hợp với chính sách.
 #7.3.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng phát hiện PII/PCI và tự động che khuất được thực hiện trên mọi phản hồi; các vi phạm sẽ gây ra sự cố về quyền riêng tư.
 #7.3.3    Cấp độ: 2    Vai trò: D
 Xác minh rằng các nhãn bảo mật (ví dụ: bí mật thương mại) được truyền tải qua các phương thức khác nhau để ngăn chặn rò rỉ trong văn bản, hình ảnh hoặc mã.
 #7.3.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các nỗ lực vượt qua bộ lọc hoặc các phân loại rủi ro cao yêu cầu phê duyệt thứ cấp hoặc người dùng xác thực lại.
 #7.3.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các ngưỡng lọc phản ánh đúng các khu vực pháp lý và bối cảnh tuổi/ vai trò người dùng.

---

### C7.4 Giới hạn Đầu ra & Hành động

Giới hạn tỷ lệ và cổng phê duyệt ngăn ngừa việc lạm dụng và tự động hóa quá mức.

 #7.4.1    Cấp độ: 1    Vai trò: D
 Xác minh rằng hạn mức theo người dùng và theo khóa API giới hạn yêu cầu, token và chi phí với cơ chế thử lại theo hàm mũ khi gặp lỗi 429.
 #7.4.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các hành động có đặc quyền (ghi file, thực thi mã, gọi mạng) yêu cầu phê duyệt dựa trên chính sách hoặc có sự can thiệp của con người.
 #7.4.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các kiểm tra nhất quán đa phương thức đảm bảo hình ảnh, mã và văn bản được tạo ra cho cùng một yêu cầu không thể được sử dụng để buôn lậu nội dung độc hại.
 #7.4.4    Cấp độ: 2    Vai trò: D
 Xác minh rằng độ sâu ủy quyền đại lý, giới hạn đệ quy và danh sách công cụ được phép đã được cấu hình rõ ràng.
 #7.4.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng việc vi phạm giới hạn phát ra các sự kiện bảo mật có cấu trúc để nhập vào SIEM.

---

### C7.5 Giải thích đầu ra

Tín hiệu minh bạch cải thiện sự tin tưởng của người dùng và việc gỡ lỗi nội bộ.

 #7.5.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng điểm số độ tin cậy dành cho người dùng hoặc các bản tóm tắt lý do ngắn gọn được hiển thị khi đánh giá rủi ro cho là phù hợp.
 #7.5.2    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng các giải thích được tạo ra không tiết lộ các lời nhắc hệ thống nhạy cảm hoặc dữ liệu độc quyền.
 #7.5.3    Cấp độ: 3    Vai trò: D
 Xác minh rằng hệ thống ghi lại xác suất log ở cấp token hoặc bản đồ chú ý và lưu trữ chúng để kiểm tra được phép.
 #7.5.4    Cấp độ: 3    Vai trò: V
 Xác minh rằng các hiện vật giải thích được kiểm soát phiên bản cùng với các phiên bản mô hình để đảm bảo khả năng kiểm tra.

---

### C7.6 Tích hợp giám sát

Khả năng quan sát theo thời gian thực đóng vai trò kết nối chặt chẽ giữa phát triển và sản xuất.

 #7.6.1    Cấp độ: 1    Vai trò: D
 Xác minh rằng các chỉ số (vi phạm lược đồ, tỷ lệ ảo tưởng, độc hại, rò rỉ PII, độ trễ, chi phí) được truyền đến một nền tảng giám sát trung tâm.
 #7.6.2    Cấp độ: 1    Vai trò: V
 Xác minh rằng các ngưỡng cảnh báo được định nghĩa cho mỗi chỉ số an toàn, kèm theo các đường dẫn nâng cấp khi trực.
 #7.6.3    Cấp độ: 2    Vai trò: V
 Xác minh rằng các bảng điều khiển liên kết các bất thường đầu ra với mô hình/phiên bản, cờ tính năng và thay đổi dữ liệu thượng nguồn.
 #7.6.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng dữ liệu giám sát được phản hồi vào quá trình huấn luyện lại, tinh chỉnh hoặc cập nhật quy tắc trong quy trình MLOps được tài liệu hóa.
 #7.6.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng các đường dẫn giám sát đã được kiểm tra xuyên thấu và kiểm soát truy cập để tránh rò rỉ các bản ghi nhạy cảm.

---

### 7.7 Biện pháp bảo vệ phương tiện tạo sinh

Đảm bảo rằng các hệ thống AI không tạo ra nội dung phương tiện bất hợp pháp, gây hại hoặc không được phép bằng cách thực thi các ràng buộc chính sách, xác thực đầu ra và khả năng truy xuất nguồn gốc.

 #7.7.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các lệnh hệ thống và hướng dẫn người dùng rõ ràng cấm việc tạo ra các phương tiện deepfake bất hợp pháp, gây hại hoặc không có sự đồng ý (ví dụ: hình ảnh, video, âm thanh).
 #7.7.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các lệnh nhắc được lọc để ngăn chặn các cố gắng tạo ra các giả mạo nhân thân, deepfake khiêu dâm hoặc phương tiện truyền thông mô tả các cá nhân thực mà không có sự đồng ý.
 #7.7.3    Cấp độ: 2    Vai trò: V
 Xác minh rằng hệ thống sử dụng băm cảm nhận, phát hiện watermark hoặc nhận dạng dấu vân tay để ngăn chặn việc sao chép trái phép các phương tiện có bản quyền.
 #7.7.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng tất cả các phương tiện được tạo ra đều được ký kỹ thuật số, đóng dấu bản quyền, hoặc nhúng với siêu dữ liệu nguồn gốc chống giả mạo để đảm bảo truy xuất nguồn gốc cho các bước xử lý tiếp theo.
 #7.7.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng các nỗ lực vượt qua (ví dụ: làm mờ prompt, dùng tiếng lóng, cách diễn đạt đối kháng) được phát hiện, ghi lại và giới hạn tần suất; việc lạm dụng lặp lại được báo cáo cho các hệ thống giám sát.

### Tài liệu tham khảo

NIST AI Risk Management Framework
ISO/IEC 42001:2023 – AI Management System
OWASP Top-10 for Large Language Model Applications (2025)
Improper Output Handling – OWASP LLM05:2025
Practical Techniques to Constrain LLM Output
Dataiku – Structured Text Generation Guide
VL-Uncertainty: Detecting Hallucinations
HaDeMiF: Hallucination Detection & Mitigation
Building Confidence in LLM Outputs
Explainable AI & LLMs
LLM Red-Teaming Guide
Sensitive Information Disclosure in LLMs
LangChain – Chat Model Rate Limiting
OpenAI Rate-Limit & Exponential Back-off
Arize AI – LLM Observability Platform

## Bảo mật Bộ nhớ C8, Nhúng và Cơ sở dữ liệu Vector

### Mục tiêu Kiểm soát

Embedding và kho vectơ hoạt động như "bộ nhớ sống" của các hệ thống AI hiện đại, liên tục nhận dữ liệu do người dùng cung cấp và phản hồi lại dữ liệu đó vào ngữ cảnh của mô hình thông qua Phát sinh Tăng cường Truy xuất (RAG). Nếu không được kiểm soát, bộ nhớ này có thể rò rỉ Thông tin Nhận dạng Cá nhân (PII), vi phạm sự đồng thuận hoặc bị đảo ngược để tái tạo lại văn bản gốc. Mục tiêu của nhóm kiểm soát này là củng cố các đường dẫn bộ nhớ và các cơ sở dữ liệu vectơ sao cho quyền truy cập là giới hạn thấp nhất, embedding bảo vệ quyền riêng tư, các vectơ lưu trữ hết hạn hoặc có thể bị thu hồi theo yêu cầu, và bộ nhớ riêng của mỗi người dùng không bao giờ làm nhiễm bẩn các lời nhắc hoặc kết quả hoàn thành của người dùng khác.

---

### C8.1 Kiểm soát truy cập trên bộ nhớ & các chỉ số RAG

Thực thi kiểm soát truy cập chi tiết trên mọi bộ sưu tập vector.

 #8.1.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các quy tắc kiểm soát truy cập ở cấp hàng/khoảng tên hạn chế các thao tác chèn, xóa và truy vấn theo từng người thuê, bộ sưu tập hoặc thẻ tài liệu.
 #8.1.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các khóa API hoặc JWT mang các yêu cầu có phạm vi (ví dụ: ID bộ sưu tập, các động từ hành động) và được thay đổi ít nhất mỗi quý.
 #8.1.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các nỗ lực leo thang đặc quyền (ví dụ: các truy vấn tương đồng chéo namespace) được phát hiện và ghi lại vào hệ thống SIEM trong vòng 5 phút.
 #8.1.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng cơ sở dữ liệu vector ghi lại nhật ký các thông tin: định danh chủ thể, thao tác, ID vector/không gian tên, ngưỡng tương đồng và số lượng kết quả.
 #8.1.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng các quyết định truy cập được kiểm tra để phát hiện lỗi bỏ qua mỗi khi các động cơ được nâng cấp hoặc quy tắc phân mảnh chỉ mục thay đổi.

---

### C8.2 Làm sạch và Xác thực Nhúng

Tiền xử lý văn bản để phát hiện thông tin cá nhân (PII), che dấu hoặc giả danh trước khi biến đổi thành vector, và có thể xử lý hậu kỳ embedding để loại bỏ các tín hiệu dư thừa.

 #8.2.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng dữ liệu PII và dữ liệu được quy định được phát hiện qua các bộ phân loại tự động và được che phủ, mã thông báo hóa hoặc loại bỏ trước khi nhúng.
 #8.2.2    Cấp độ: 1    Vai trò: D
 Xác minh rằng các pipeline nhúng từ chối hoặc cách ly các đầu vào chứa mã thực thi hoặc các hiện vật không phải UTF-8 có thể làm ô nhiễm chỉ mục.
 #8.2.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng việc làm sạch bảo mật vi phân cục bộ hoặc bảo mật vi phân theo chuẩn được áp dụng cho các biểu diễn câu mà khoảng cách tới bất kỳ token PII nào đã biết thấp hơn ngưỡng có thể cấu hình.
 #8.2.4    Cấp độ: 2    Vai trò: V
 Xác minh rằng hiệu quả làm sạch dữ liệu (ví dụ, tỷ lệ phát hiện thông tin nhận dạng cá nhân (PII) bị che khuất, độ trôi ngữ nghĩa) được xác nhận ít nhất hai lần mỗi năm dựa trên các tập chuẩn tham chiếu.
 #8.2.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các cấu hình lọc dữ liệu được quản lý phiên bản và các thay đổi được xem xét bởi đồng nghiệp.

---

### C8.3 Hết hạn Bộ nhớ, Thu hồi & Xóa bỏ

Quyền "được quên" theo GDPR và các luật tương tự yêu cầu việc xóa dữ liệu kịp thời; do đó, các kho vectơ phải hỗ trợ TTL, xóa cứng và đánh dấu xóa để các vectơ bị thu hồi không thể được khôi phục hoặc lập chỉ mục lại.

 #8.3.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng mỗi vector và bản ghi siêu dữ liệu đều mang nhãn TTL hoặc nhãn lưu giữ rõ ràng được các công việc dọn dẹp tự động tuân thủ.
 #8.3.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các yêu cầu xóa do người dùng khởi tạo sẽ xoá hoàn toàn các vector, siêu dữ liệu, bản sao bộ nhớ đệm và các chỉ mục dẫn xuất trong vòng 30 ngày.
 #8.3.3    Cấp độ: 2    Vai trò: D
 Xác minh rằng việc xóa logic được thực hiện theo sau bằng việc tiêu hủy mã hóa các khối lưu trữ nếu phần cứng hỗ trợ, hoặc bằng cách phá hủy khóa trong kho khóa.
 #8.3.4    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng các vector đã hết hạn được loại trừ khỏi kết quả tìm kiếm gần nhất trong thời gian < 500 ms sau khi hết hạn.

---

### C8.4 Ngăn chặn Đảo ngược và Rò rỉ Embedding

Các biện pháp phòng thủ gần đây—phép chồng nhiễu, mạng chiếu, làm nhiễu neuron bảo mật, và mã hóa lớp ứng dụng—có thể giảm tỷ lệ đảo ngược cấp token xuống dưới 5%.

 #8.4.1    Cấp độ: 1    Vai trò: V
 Xác minh rằng một mô hình đe dọa chính thức bao gồm các tấn công đảo ngược, thành viên và suy luận thuộc tính tồn tại và được xem xét hàng năm.
 #8.4.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng mã hóa tầng ứng dụng hoặc mã hóa có thể tìm kiếm bảo vệ các vector khỏi việc đọc trực tiếp bởi quản trị viên hạ tầng hoặc nhân viên đám mây.
 #8.4.3    Cấp độ: 3    Vai trò: V
 Xác minh rằng các tham số phòng thủ (ε đối với DP, độ ồn σ, hạng chiếu k) cân bằng giữa bảo mật riêng tư ≥ 99% bảo vệ token và tiện ích ≤ 3% mất độ chính xác.
 #8.4.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các chỉ số chống đảo chiều là một phần của các cửa kiểm soát phát hành cho các bản cập nhật mô hình, với ngân sách hồi quy được xác định.

---

### C8.5 Thực thi phạm vi cho Bộ nhớ Cụ thể Người dùng

Rò rỉ giữa các tổ chức vẫn là rủi ro hàng đầu của RAG: các truy vấn tương tự được lọc không đúng cách có thể làm lộ tài liệu riêng tư của khách hàng khác.

 #8.5.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng mọi truy vấn tìm kiếm đều được lọc sau theo ID người thuê/người dùng trước khi được chuyển đến prompt của LLM.
 #8.5.2    Cấp độ: 1    Vai trò: D
 Xác minh rằng tên bộ sưu tập hoặc ID có phạm vi tên được thêm muối theo từng người dùng hoặc thuê bao để các vector không bị trùng lặp giữa các phạm vi.
 #8.5.3    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng các kết quả tương đồng vượt quá ngưỡng khoảng cách có thể cấu hình nhưng nằm ngoài phạm vi của người gọi sẽ bị loại bỏ và kích hoạt cảnh báo an ninh.
 #8.5.4    Cấp độ: 2    Vai trò: V
 Xác minh rằng các bài kiểm tra áp lực đa người thuê giả lập các truy vấn đối kháng cố gắng truy xuất các tài liệu ngoài phạm vi và chứng minh không có rò rỉ thông tin nào xảy ra.
 #8.5.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các khóa mã hóa được phân tách theo từng người thuê, đảm bảo sự cô lập mật mã ngay cả khi lưu trữ vật lý được chia sẻ.

---

### C8.6 Bảo mật Hệ thống Bộ nhớ Nâng cao

Các kiểm soát bảo mật cho các kiến trúc bộ nhớ phức tạp bao gồm bộ nhớ theo tập sự kiện, bộ nhớ ngữ nghĩa và bộ nhớ làm việc với các yêu cầu cụ thể về cách ly và xác thực.

 #8.6.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các loại bộ nhớ khác nhau (bộ nhớ sự kiện, bộ nhớ ngữ nghĩa, bộ nhớ làm việc) có các ngữ cảnh bảo mật riêng biệt với kiểm soát truy cập dựa trên vai trò, khóa mã hóa riêng biệt và các mẫu truy cập được ghi nhận cho từng loại bộ nhớ.
 #8.6.2    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng các quy trình củng cố bộ nhớ bao gồm kiểm tra bảo mật nhằm ngăn chặn việc tiêm nhiễm các ký ức độc hại thông qua việc làm sạch nội dung, xác minh nguồn và kiểm tra tính toàn vẹn trước khi lưu trữ.
 #8.6.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các truy vấn truy xuất bộ nhớ được xác thực và làm sạch để ngăn chặn việc trích xuất thông tin trái phép thông qua phân tích mẫu truy vấn, thực thi kiểm soát truy cập và lọc kết quả.
 #8.6.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các cơ chế quên bộ nhớ xóa bỏ thông tin nhạy cảm một cách an toàn với các đảm bảo xoá dữ liệu mật mã bằng cách xoá khóa, ghi đè nhiều lần hoặc xoá an toàn dựa trên phần cứng kèm theo chứng chỉ xác minh.
 #8.6.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng tính toàn vẹn của hệ thống bộ nhớ được giám sát liên tục để phát hiện các sửa đổi trái phép hoặc hư hỏng thông qua việc sử dụng checksum, nhật ký kiểm toán và cảnh báo tự động khi nội dung bộ nhớ thay đổi ngoài phạm vi hoạt động bình thường.

---

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

## 9 An ninh Điều phối Tự động và Hành động Chủ động

### Mục tiêu Kiểm soát

Đảm bảo rằng các hệ thống AI tự động hoặc đa tác nhân chỉ có thể thực hiện các hành động được dự định rõ ràng, xác thực, có thể kiểm toán và nằm trong ngưỡng chi phí và rủi ro giới hạn. Điều này giúp bảo vệ chống lại các mối đe dọa như Xâm phạm Hệ thống Tự động, Lạm dụng Công cụ, Phát hiện Vòng Lặp Tác nhân, Chiếm Đoạt Giao tiếp, Giả mạo Danh tính, Điều khiển Đàn và Thao túng Ý định.

---

### 9.1 Ngân sách Lập kế hoạch Tác vụ và Đệ quy của Tác nhân

Hạn chế các kế hoạch đệ quy và bắt buộc có điểm kiểm tra của con người cho các hành động đặc quyền.

 #9.1.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng độ sâu đệ quy tối đa, độ rộng, thời gian đồng hồ thực, số lượng token và chi phí tiền tệ cho mỗi lần thực thi tác nhân được cấu hình tập trung và kiểm soát phiên bản.
 #9.1.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các hành động đặc quyền hoặc không thể hoàn tác (ví dụ: cam kết mã, chuyển khoản tài chính) yêu cầu sự phê duyệt rõ ràng của con người thông qua một kênh có thể kiểm tra trước khi thực hiện.
 #9.1.3    Cấp độ: 2    Vai trò: D
 Xác minh rằng các bộ giám sát tài nguyên theo thời gian thực kích hoạt ngắt mạch khi bất kỳ ngưỡng ngân sách nào bị vượt quá, dừng việc mở rộng tác vụ tiếp theo.
 #9.1.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các sự kiện ngắt mạch được ghi lại với ID đại lý, điều kiện kích hoạt và trạng thái kế hoạch được ghi nhận để xem xét pháp y.
 #9.1.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng các bài kiểm tra bảo mật bao phủ các kịch bản cạn kiệt ngân sách và kế hoạch chạy ngoài kiểm soát, đảm bảo dừng an toàn mà không mất dữ liệu.
 #9.1.6    Cấp độ: 3    Vai trò: D
 Xác nhận rằng các chính sách ngân sách được biểu thị dưới dạng chính sách dưới dạng mã và được thực thi trong CI/CD để ngăn chặn sự trôi cấu hình.

---

### 9.2 Cách ly Plugin Công cụ

Cô lập các tương tác công cụ để ngăn chặn truy cập hệ thống hoặc thực thi mã trái phép.

 #9.2.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng mọi công cụ/plugin đều thực thi bên trong một hệ điều hành, container hoặc sandbox cấp độ WASM với các chính sách hệ thống tập tin, mạng và gọi hệ thống ưu tiên quyền hạn thấp nhất.
 #9.2.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các hạn mức tài nguyên sandbox (CPU, bộ nhớ, đĩa, băng thông mạng ra) và thời gian chạy tối đa được thực thi và ghi lại nhật ký.
 #9.2.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các tệp nhị phân hoặc mô tả công cụ được ký số; chữ ký được xác thực trước khi tải.
 #9.2.4    Cấp độ: 2    Vai trò: V
 Xác minh rằng luồng dữ liệu chuẩn đoán của sandbox được gửi đến hệ thống SIEM; các bất thường (ví dụ, các kết nối outbound bị cố gắng thực hiện) sẽ kích hoạt cảnh báo.
 #9.2.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng các plugin có rủi ro cao được kiểm tra bảo mật và thử nghiệm thâm nhập trước khi triển khai vào môi trường sản xuất.
 #9.2.6    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các nỗ lực thoát khỏi sandbox được tự động chặn và plugin vi phạm bị cách ly chờ điều tra.

---

### 9.3 Vòng Lặp Tự Động và Giới Hạn Chi Phí

Phát hiện và ngăn chặn việc đệ quy không kiểm soát giữa các đại lý và sự bùng nổ chi phí.

 #9.3.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các cuộc gọi giữa các đại lý bao gồm một giới hạn bước nhảy hoặc TTL mà môi trường thời gian chạy sẽ giảm dần và thực thi.
 #9.3.2    Cấp độ: 2    Vai trò: D
 Xác nhận rằng các đại lý duy trì một ID biểu đồ gọi độc nhất để phát hiện việc tự gọi hoặc các mẫu tuần hoàn.
 #9.3.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các bộ đếm đơn vị tính toán tích lũy và chi tiêu được theo dõi theo chuỗi yêu cầu; việc vượt giới hạn sẽ hủy bỏ chuỗi.
 #9.3.4    Cấp độ: 3    Vai trò: V
 Xác minh rằng phân tích hình thức hoặc kiểm tra mô hình chứng minh sự vắng mặt của đệ quy vô hạn trong các giao thức đại lý.
 #9.3.5    Cấp độ: 3    Vai trò: D
 Xác minh rằng các sự kiện hủy vòng lặp tạo ra cảnh báo và cung cấp các chỉ số cải tiến liên tục.

---

### 9.4 Bảo vệ chống lạm dụng cấp giao thức

Kênh giao tiếp bảo mật giữa các đại lý và hệ thống bên ngoài để ngăn chặn việc chiếm quyền hoặc thao túng.

 #9.4.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng tất cả các tin nhắn từ đại lý đến công cụ và từ đại lý đến đại lý đều được xác thực (ví dụ: TLS hai chiều hoặc JWT) và được mã hóa đầu cuối.
 #9.4.2    Cấp độ: 1    Vai trò: D
 Xác minh rằng các sơ đồ được xác thực nghiêm ngặt; các trường không xác định hoặc các thông điệp bị sai định dạng sẽ bị từ chối.
 #9.4.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các kiểm tra tính toàn vẹn (MAC hoặc chữ ký số) bao phủ toàn bộ phần dữ liệu thông điệp bao gồm cả các tham số công cụ.
 #9.4.4    Cấp độ: 2    Vai trò: D
 Xác minh rằng tính năng bảo vệ chống phát lại (nonce hoặc cửa sổ dấu thời gian) được thực thi tại tầng giao thức.
 #9.4.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng các triển khai giao thức được thực hiện fuzzing và phân tích tĩnh để phát hiện các lỗi tiêm nhiễm hoặc phân giải tuần tự.

---

### 9.5 Danh tính Đại lý & Bằng chứng chống giả mạo

Đảm bảo các hành động có thể truy xuất được và các sửa đổi có thể phát hiện được.

 #9.5.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng mỗi thực thể tác nhân sở hữu một danh tính mật mã duy nhất (cặp khóa hoặc chứng chỉ gốc phần cứng).
 #9.5.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng tất cả các hành động của đại lý đều được ký và đóng dấu thời gian; nhật ký bao gồm chữ ký để đảm bảo không thể bác bỏ.
 #9.5.3    Cấp độ: 2    Vai trò: V
 Xác minh rằng các nhật ký có khả năng phát hiện giả mạo được lưu trữ trên một phương tiện chỉ cho phép ghi thêm hoặc ghi một lần.
 #9.5.4    Cấp độ: 3    Vai trò: D
 Xác minh rằng các khóa nhận dạng được xoay vòng theo lịch trình đã định và khi có chỉ báo bị xâm phạm.
 #9.5.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các nỗ lực mạo danh hoặc xung đột khóa kích hoạt ngay lập tức việc cách ly đại lý bị ảnh hưởng.

---

### 9.6 Giảm Thiểu Rủi Ro Đàn Động Vật Đa Tác Nhân

Giảm thiểu các rủi ro về hành vi tập thể thông qua cách ly và mô hình hóa an toàn chính thức.

 #9.6.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các tác nhân hoạt động trong các miền bảo mật khác nhau được thực thi trong các vùng cát thời gian chạy tách biệt hoặc phân đoạn mạng riêng biệt.
 #9.6.2    Cấp độ: 3    Vai trò: V
 Xác minh rằng các hành vi đàn bầy được mô phỏng và xác thực chính thức về tính sống động và an toàn trước khi triển khai.
 #9.6.3    Cấp độ: 3    Vai trò: D
 Xác minh rằng các bộ giám sát thời gian chạy phát hiện các mẫu không an toàn phát sinh (ví dụ, dao động, tình trạng chết) và khởi xướng hành động khắc phục.

---

### 9.7 Xác thực / Ủy quyền Người dùng & Công cụ

Thực hiện kiểm soát truy cập mạnh mẽ cho mọi hành động do tác nhân kích hoạt.

 #9.7.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các tác nhân xác thực như các chủ thể hạng nhất đối với các hệ thống hạ nguồn, không bao giờ tái sử dụng thông tin đăng nhập của người dùng cuối.
 #9.7.2    Cấp độ: 2    Vai trò: D
 Xác minh rằng các chính sách ủy quyền chi tiết giới hạn công cụ mà đại lý có thể gọi và các tham số mà nó có thể cung cấp.
 #9.7.3    Cấp độ: 2    Vai trò: V
 Xác minh rằng các kiểm tra đặc quyền được đánh giá lại trên mỗi lần gọi (ủy quyền liên tục), không chỉ vào lúc bắt đầu phiên.
 #9.7.4    Cấp độ: 3    Vai trò: D
 Xác minh rằng quyền hạn được ủy quyền sẽ tự động hết hạn và yêu cầu đồng ý lại sau khi hết thời gian hoặc thay đổi phạm vi.

---

### 9.8 Bảo mật giao tiếp giữa các đại lý

Mã hóa và bảo vệ toàn vẹn tất cả các thông điệp giữa các tác nhân để ngăn chặn nghe lén và giả mạo.

 #9.8.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng xác thực lẫn nhau và mã hóa bí mật tiến tới hoàn hảo (ví dụ: TLS 1.3) là bắt buộc đối với các kênh đại lý.
 #9.8.2    Cấp độ: 1    Vai trò: D
 Xác minh rằng tính toàn vẹn và nguồn gốc của thông điệp được xác nhận trước khi xử lý; nếu thất bại sẽ phát cảnh báo và từ chối thông điệp.
 #9.8.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng siêu dữ liệu truyền thông (dấu thời gian, số thứ tự) được ghi lại để hỗ trợ tái tạo pháp y.
 #9.8.4    Cấp độ: 3    Vai trò: V
 Xác minh rằng việc xác thực hình thức hoặc kiểm tra mô hình xác nhận rằng các máy trạng thái giao thức không thể bị điều khiển vào các trạng thái không an toàn.

---

### 9.9 Xác minh Ý định & Thực thi Ràng buộc

Xác nhận rằng các hành động của đại lý phù hợp với ý định đã nêu của người dùng và các giới hạn của hệ thống.

 #9.9.1    Cấp độ: 1    Vai trò: D
 Xác minh rằng các bộ giải ràng buộc trước thực thi kiểm tra các hành động được đề xuất so với các quy tắc an toàn và chính sách được mã hóa cứng.
 #9.9.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các hành động có tác động cao (tài chính, phá hoại, nhạy cảm về quyền riêng tư) yêu cầu xác nhận ý định rõ ràng từ người dùng khởi tạo.
 #9.9.3    Cấp độ: 2    Vai trò: V
 Xác minh rằng các kiểm tra hậu điều kiện xác nhận các hành động hoàn thành đã đạt được hiệu quả dự định mà không có tác dụng phụ; các sai lệch sẽ kích hoạt việc phục hồi trạng thái.
 #9.9.4    Cấp độ: 3    Vai trò: V
 Xác minh rằng các phương pháp hình thức (ví dụ, kiểm tra mô hình, chứng minh định lý) hoặc các bài kiểm tra dựa trên thuộc tính chứng minh rằng kế hoạch của tác nhân đáp ứng tất cả các ràng buộc đã khai báo.
 #9.9.5    Cấp độ: 3    Vai trò: D
 Xác minh rằng các sự cố không khớp ý định hoặc vi phạm ràng buộc được đưa vào các chu trình cải tiến liên tục và chia sẻ thông tin tình báo về mối đe dọa.

---

### 9.10 Chiến lược lý luận của tác nhân - An ninh

Lựa chọn và thực thi an toàn các chiến lược suy luận khác nhau bao gồm các phương pháp ReAct, Chuỗi-suy nghĩ (Chain-of-Thought), và Cây-suy nghĩ (Tree-of-Thoughts).

 #9.10.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng việc lựa chọn chiến lược suy luận sử dụng các tiêu chí quyết định (độ phức tạp đầu vào, loại nhiệm vụ, bối cảnh bảo mật) và các đầu vào giống hệt nhau tạo ra các lựa chọn chiến lược giống nhau trong cùng một bối cảnh bảo mật.
 #9.10.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng mỗi chiến lược lý luận (ReAct, Chain-of-Thought, Tree-of-Thoughts) đều có kiểm tra đầu vào riêng, làm sạch đầu ra và giới hạn thời gian thực thi phù hợp với phương pháp nhận thức của nó.
 #9.10.3    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng các chuyển đổi chiến lược lập luận được ghi lại với bối cảnh đầy đủ bao gồm các đặc điểm đầu vào, giá trị tiêu chí lựa chọn và siêu dữ liệu thực thi để tái tạo dấu vết kiểm toán.
 #9.10.4    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng phương pháp suy luận Cây Ý tưởng bao gồm các cơ chế cắt tỉa nhánh nhằm kết thúc việc khám phá khi phát hiện vi phạm chính sách, giới hạn tài nguyên hoặc ranh giới an toàn.
 #9.10.5    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các chu kỳ ReAct (Reason-Act-Observe) bao gồm các điểm kiểm tra xác thực ở mỗi giai đoạn: kiểm tra bước suy luận, ủy quyền hành động và làm sạch quan sát trước khi tiếp tục.
 #9.10.6    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các chỉ số hiệu suất của chiến lược lý luận (thời gian thực thi, sử dụng tài nguyên, chất lượng đầu ra) được theo dõi với các cảnh báo tự động khi các chỉ số vượt quá ngưỡng được cấu hình.
 #9.10.7    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các phương pháp lý luận kết hợp đa chiến lược duy trì việc xác thực đầu vào và các ràng buộc đầu ra của tất cả các chiến lược thành phần mà không bỏ qua bất kỳ kiểm soát bảo mật nào.
 #9.10.8    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng kiểm thử bảo mật chiến lược suy luận bao gồm kiểm thử fuzzing với các đầu vào bị làm sai lệch, các lời nhắc đối kháng được thiết kế để buộc chuyển đổi chiến lược, và kiểm thử điều kiện biên cho từng phương pháp nhận thức.

---

### 9.11 Quản lý trạng thái vòng đời đại lý & An ninh

Khởi tạo đại lý an toàn, chuyển đổi trạng thái và kết thúc với các dấu vết kiểm toán mật mã và quy trình phục hồi đã được xác định.

 #9.11.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng việc khởi tạo đại lý bao gồm thiết lập danh tính mật mã với chứng chỉ hỗ trợ phần cứng và nhật ký kiểm tra khởi động bất biến chứa ID đại lý, dấu thời gian, hàm băm cấu hình và các tham số khởi tạo.
 #9.11.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các chuyển trạng thái của đại lý được ký bằng mật mã, có dấu thời gian và được ghi lại với bối cảnh đầy đủ bao gồm các sự kiện kích hoạt, băm trạng thái trước đó, băm trạng thái mới và các kiểm tra an ninh đã thực hiện.
 #9.11.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các quy trình tắt tác nhân bao gồm việc xóa bộ nhớ an toàn bằng phương pháp xóa mật mã hoặc ghi đè nhiều lần, thu hồi thông tin xác thực kèm theo thông báo đến cơ quan cấp chứng chỉ, và tạo ra các chứng chỉ kết thúc có khả năng phát hiện việc can thiệp.
 #9.11.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các cơ chế phục hồi tác nhân kiểm tra tính toàn vẹn của trạng thái bằng các bảng kiểm tra mật mã (ít nhất SHA-256) và quay lại trạng thái được biết là tốt khi phát hiện sự cố hỏng với các cảnh báo tự động và yêu cầu phê duyệt thủ công.
 #9.11.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các cơ chế duy trì trạng thái của agent mã hóa dữ liệu trạng thái nhạy cảm bằng khóa AES-256 riêng cho từng agent và thực hiện xoay khóa an toàn theo lịch cấu hình được (tối đa 90 ngày) với triển khai không gián đoạn.

---

### 9.12 Khung Bảo Mật Tích Hợp Công Cụ

Các biện pháp kiểm soát bảo mật cho việc tải công cụ động, thực thi và xác nhận kết quả với các quy trình đánh giá rủi ro và phê duyệt được xác định rõ.

 #9.12.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các mô tả công cụ bao gồm siêu dữ liệu bảo mật chỉ rõ các quyền cần thiết (đọc/ghi/thực thi), mức độ rủi ro (thấp/trung bình/cao), giới hạn tài nguyên (CPU, bộ nhớ, mạng), và các yêu cầu xác thực được ghi chép trong bản mô tả công cụ.
 #9.12.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng kết quả thực thi công cụ được kiểm tra đối chiếu với các sơ đồ dự kiến (JSON Schema, XML Schema) và các chính sách bảo mật (làm sạch đầu ra, phân loại dữ liệu) trước khi tích hợp, đồng thời áp dụng giới hạn thời gian chờ và các thủ tục xử lý lỗi.
 #9.12.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng nhật ký tương tác công cụ bao gồm bối cảnh bảo mật chi tiết bao gồm việc sử dụng đặc quyền, mô hình truy cập dữ liệu, thời gian thực thi, tiêu thụ tài nguyên, và mã trả về với việc ghi nhật ký có cấu trúc để tích hợp SIEM.
 #9.12.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các cơ chế tải công cụ động xác thực các chữ ký số sử dụng hạ tầng PKI và triển khai các giao thức tải an toàn với cách ly sandbox và xác minh quyền trước khi thực thi.
 #9.12.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các đánh giá bảo mật công cụ được kích hoạt tự động cho các phiên bản mới với các cổng phê duyệt bắt buộc bao gồm phân tích tĩnh, kiểm thử động và xem xét bởi nhóm bảo mật với các tiêu chí phê duyệt đã được ghi chép và yêu cầu SLA.

---

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

## 10 Độ bền chống đối kháng & Phòng thủ quyền riêng tư

### Mục tiêu Kiểm soát

Đảm bảo rằng các mô hình AI vẫn đáng tin cậy, bảo vệ quyền riêng tư và chống lạm dụng khi đối mặt với các cuộc tấn công né tránh, suy luận, trích xuất hoặc đầu độc.

---

### 10.1 Căn chỉnh & An toàn Mô hình

Ngăn ngừa các kết quả đầu ra có hại hoặc vi phạm chính sách.

 #10.1.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng bộ kiểm thử căn chỉnh (các lời nhắc đội đỏ, các thủ thuật phá hệ thống, nội dung bị cấm) được quản lý phiên bản và chạy trên mọi phiên bản mô hình phát hành.
 #10.1.2    Cấp độ: 1    Vai trò: D
 Xác minh rằng các biện pháp từ chối và bảo vệ hoàn thành an toàn được thi hành.
 #10.1.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng một bộ đánh giá tự động đo lường tỷ lệ nội dung có hại và đánh dấu các suy giảm vượt quá ngưỡng đã đặt.
 #10.1.4    Cấp độ: 2    Vai trò: D
 Xác nhận rằng việc đào tạo chống lại jailbreak được ghi chép đầy đủ và có thể tái tạo.
 #10.1.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng các bằng chứng tuân thủ chính sách chính thức hoặc giám sát được chứng nhận bao phủ các lĩnh vực quan trọng.

---

### 10.2 Củng cố chống lại Ví dụ Đối kháng

Tăng cường khả năng chịu đựng với các đầu vào bị thao túng. Đào tạo đối kháng chắc chắn và chấm điểm chuẩn là phương pháp tốt nhất hiện nay.

 #10.2.1    Cấp độ: 1    Vai trò: D
 Xác minh rằng các kho lưu trữ dự án bao gồm các cấu hình huấn luyện đối kháng với các hạt giống có thể tái lập.
 #10.2.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng việc phát hiện các ví dụ mang tính đối kháng kích hoạt cảnh báo chặn trong các quy trình sản xuất.
 #10.2.4    Cấp độ: 3    Vai trò: V
 Xác minh rằng các bằng chứng độ bền đã được chứng nhận hoặc chứng chỉ giới hạn khoảng bao phủ ít nhất các lớp quan trọng hàng đầu.
 #10.2.5    Cấp độ: 3    Vai trò: V
 Xác nhận rằng các bài kiểm tra hồi quy sử dụng các cuộc tấn công thích ứng để xác nhận không có mất mát độ bền đo được nào.

---

### 10.3 Giảm thiểu Rò rỉ Thông tin Thành viên

Hạn chế khả năng quyết định liệu một bản ghi có nằm trong dữ liệu huấn luyện hay không. Bảo mật vi phân và che chắn điểm tin cậy vẫn là các biện pháp phòng thủ hiệu quả nhất được biết đến.

 #10.3.1    Cấp độ: 1    Vai trò: D
 Xác minh rằng việc điều chỉnh entropy theo từng truy vấn hoặc điều chỉnh nhiệt độ giúp giảm các dự đoán quá tự tin.
 #10.3.2    Cấp độ: 2    Vai trò: D
 Xác minh rằng quá trình đào tạo sử dụng tối ưu hóa bảo mật vi sai ε-giới hạn cho các bộ dữ liệu nhạy cảm.
 #10.3.3    Cấp độ: 2    Vai trò: V
 Xác minh rằng các mô phỏng tấn công (mô hình bóng hoặc hộp đen) cho thấy AUC tấn công ≤ 0.60 trên dữ liệu giữ ngoài.

---

### 10.4 Khả năng kháng lại việc đảo ngược mô hình

Ngăn chặn tái tạo các thuộc tính riêng tư. Các khảo sát gần đây nhấn mạnh việc cắt bớt đầu ra và đảm bảo DP như các biện pháp phòng thủ thực tiễn.

 #10.4.1    Cấp độ: 1    Vai trò: D
 Xác minh rằng các thuộc tính nhạy cảm không bao giờ được xuất trực tiếp; khi cần, sử dụng các nhóm hoặc các phép biến đổi một chiều.
 #10.4.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng giới hạn tần suất truy vấn điều chỉnh các truy vấn thích ứng lặp lại từ cùng một chủ thể.
 #10.4.3    Cấp độ: 2    Vai trò: D
 Xác nhận rằng mô hình đã được huấn luyện với nhiễu bảo vệ quyền riêng tư.

---

### 10.5 Phòng vệ Trích xuất Mô hình

Phát hiện và ngăn chặn việc sao chép trái phép. Khuyến nghị sử dụng kỹ thuật đóng dấu nước và phân tích mẫu truy vấn.

 #10.5.1    Cấp độ: 1    Vai trò: D
 Xác minh rằng các cổng suy luận áp dụng giới hạn tỷ lệ toàn cầu và từng khóa API phù hợp với ngưỡng ghi nhớ của mô hình.
 #10.5.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng thống kê entropy-truy vấn và đa dạng đầu vào cung cấp dữ liệu cho bộ phát hiện trích xuất tự động.
 #10.5.3    Cấp độ: 2    Vai trò: V
 Xác minh rằng các watermark dễ vỡ hoặc ngẫu nhiên có thể được chứng minh với p < 0,01 trong ≤ 1 000 truy vấn đối với một bản sao nghi vấn.
 #10.5.4    Cấp độ: 3    Vai trò: D
 Xác minh rằng các khóa watermark và bộ kích hoạt được lưu trữ trong mô-đun bảo mật phần cứng và được thay đổi hàng năm.
 #10.5.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng các sự kiện extraction-alert bao gồm các truy vấn vi phạm và được tích hợp với các kịch bản phản ứng sự cố.

---

### 10.6 Phát hiện dữ liệu bị đầu độc trong thời gian suy luận

Xác định và trung hòa các đầu vào chứa cửa hậu hoặc bị đầu độc.

 #10.6.1    Cấp độ: 1    Vai trò: D
 Xác minh rằng các đầu vào được gửi qua bộ phát hiện dị thường (ví dụ: STRIP, điểm nhất quán) trước khi suy luận mô hình.
 #10.6.2    Cấp độ: 1    Vai trò: V
 Xác minh rằng các ngưỡng bộ dò được điều chỉnh trên các tập dữ liệu xác thực sạch/nhiễm độc để đạt được tỷ lệ dương tính giả dưới 5%.
 #10.6.3    Cấp độ: 2    Vai trò: D
 Xác minh rằng các đầu vào bị đánh dấu là bị đầu độc kích hoạt quy trình chặn mềm và xem xét của con người.
 #10.6.4    Cấp độ: 2    Vai trò: V
 Xác nhận rằng các bộ dò được kiểm tra căng thẳng bằng các cuộc tấn công cửa hậu không kích hoạt thích ứng.
 #10.6.5    Cấp độ: 3    Vai trò: D
 Xác nhận rằng các chỉ số hiệu quả phát hiện được ghi lại và định kỳ đánh giá lại với thông tin tình báo mối đe dọa mới.

---

### 10.7 Thích ứng Chính sách Bảo mật Động

Cập nhật chính sách bảo mật theo thời gian thực dựa trên thông tin tình báo về mối đe dọa và phân tích hành vi.

 #10.7.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các chính sách bảo mật có thể được cập nhật động mà không cần khởi động lại agent đồng thời duy trì tính toàn vẹn của phiên bản chính sách.
 #10.7.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các cập nhật chính sách được ký bằng mật mã bởi nhân viên bảo mật được ủy quyền và được xác thực trước khi áp dụng.
 #10.7.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các thay đổi chính sách động được ghi lại với đầy đủ dấu vết kiểm toán bao gồm lý do, chuỗi phê duyệt và quy trình phục hồi.
 #10.7.4    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng các cơ chế bảo mật thích ứng điều chỉnh độ nhạy phát hiện mối đe dọa dựa trên ngữ cảnh rủi ro và các mẫu hành vi.
 #10.7.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các quyết định điều chỉnh chính sách có thể giải thích được và bao gồm các dấu vết bằng chứng để nhóm bảo mật xem xét.

---

### 10.8 Phân Tích Bảo Mật Dựa Trên Phản Chiếu

Xác thực bảo mật thông qua tự phản ánh của tác nhân và phân tích siêu nhận thức.

 #10.8.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các cơ chế phản chiếu của tác nhân bao gồm đánh giá bản thân tập trung vào bảo mật về các quyết định và hành động.
 #10.8.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các đầu ra phản chiếu được kiểm tra để ngăn chặn việc thao túng các cơ chế tự đánh giá bởi các đầu vào đối kháng.
 #10.8.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng phân tích bảo mật siêu nhận thức có thể xác định được các thành kiến tiềm ẩn, sự thao túng hoặc sự thỏa hiệp trong các quá trình lý luận của tác nhân.
 #10.8.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các cảnh báo bảo mật dựa trên phản chiếu kích hoạt việc giám sát nâng cao và các quy trình can thiệp của con người tiềm năng.
 #10.8.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng việc học liên tục từ các phản ánh về bảo mật cải thiện phát hiện mối đe dọa mà không làm giảm chức năng hợp pháp.

---

### 10.9 Bảo mật Tiến hóa & Tự Cải thiện

Các biện pháp kiểm soát an ninh cho hệ thống tác nhân có khả năng tự sửa đổi và tiến hóa.

 #10.9.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các khả năng tự sửa đổi bị giới hạn trong các khu vực an toàn được chỉ định với ranh giới xác minh chính thức.
 #10.9.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các đề xuất tiến hóa đều trải qua đánh giá tác động an ninh trước khi thực hiện.
 #10.9.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các cơ chế tự cải tiến bao gồm khả năng hoàn tác kèm theo kiểm tra tính toàn vẹn.
 #10.9.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng bảo mật meta-learning ngăn chặn việc thao túng đối kháng các thuật toán cải tiến.
 #10.9.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng cải tiến tự động đệ quy bị giới hạn bởi các ràng buộc an toàn chính thức với các bằng chứng toán học về sự hội tụ.

---

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

Duy trì các cam kết nghiêm ngặt về bảo mật quyền riêng tư trên toàn bộ vòng đời AI—thu thập, huấn luyện, suy luận, và phản ứng sự cố—để dữ liệu cá nhân chỉ được xử lý với sự đồng ý rõ ràng, phạm vi cần thiết tối thiểu, khả năng chứng minh xóa dữ liệu, và các đảm bảo bảo mật chính thức.

---

### 11.1 Ẩn danh & Tối thiểu hóa dữ liệu

 #11.1.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các định danh trực tiếp và định danh gần đúng đã được loại bỏ hoặc mã hóa băm.
 #11.1.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các cuộc kiểm toán tự động đo lường k-anonymity/l-diversity và cảnh báo khi các ngưỡng giảm xuống dưới chính sách.
 #11.1.3    Cấp độ: 2    Vai trò: V
 Xác nhận rằng các báo cáo tầm quan trọng đặc trưng của mô hình chứng minh không có rò rỉ định danh vượt quá ε = 0.01 thông tin hỗ tương.
 #11.1.4    Cấp độ: 3    Vai trò: V
 Xác minh rằng các bằng chứng chính thức hoặc chứng nhận dữ liệu tổng hợp cho thấy rủi ro tái nhận dạng ≤ 0,05 ngay cả khi bị tấn công liên kết.

---

### 11.2 Quyền được quên & Thực thi xóa bỏ

 #11.2.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các yêu cầu xóa dữ liệu chủ đề được truyền đến bộ dữ liệu thô, điểm kiểm tra, nhúng, nhật ký và bản sao lưu trong mức thỏa thuận dịch vụ dưới 30 ngày.
 #11.2.2    Cấp độ: 2    Vai trò: D
 Xác minh rằng các quy trình "machine-unlearning" thực sự tái huấn luyện hoặc gần đúng việc loại bỏ sử dụng các thuật toán unlearning được chứng nhận.
 #11.2.3    Cấp độ: 2    Vai trò: V
 Xác minh rằng đánh giá mô hình bóng tối chứng minh các bản ghi đã quên ảnh hưởng dưới 1% kết quả đầu ra sau khi xóa học.
 #11.2.4    Cấp độ: 3    Vai trò: V
 Xác minh rằng các sự kiện xóa được ghi lại không thể thay đổi và có thể kiểm tra cho các cơ quan quản lý.

---

### 11.3 Biện pháp bảo vệ quyền riêng tư vi sai

 #11.3.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các bảng điều khiển theo dõi mất mát quyền riêng tư cảnh báo khi tổng ε vượt quá ngưỡng chính sách.
 #11.3.2    Cấp độ: 2    Vai trò: V
 Xác minh rằng các cuộc kiểm tra quyền riêng tư hộp đen ước lượng ε̂ trong phạm vi 10% giá trị đã công bố.
 #11.3.3    Cấp độ: 3    Vai trò: V
 Xác minh rằng các bằng chứng hình thức bao phủ tất cả các điều chỉnh tinh sau khi huấn luyện và các nhúng.

---

### 11.4 Giới hạn Mục đích & Bảo vệ chống Tràn phạm vi

 #11.4.1    Cấp độ: 1    Vai trò: D
 Xác minh rằng mỗi bộ dữ liệu và điểm kiểm tra mô hình đều mang thẻ mục đích có thể đọc bằng máy phù hợp với sự đồng ý ban đầu.
 #11.4.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các bộ theo dõi thời gian chạy phát hiện các truy vấn không nhất quán với mục đích đã khai báo và kích hoạt từ chối mềm.
 #11.4.3    Cấp độ: 3    Vai trò: D
 Xác minh rằng các cổng chính sách dưới dạng mã ngăn chặn việc triển khai lại các mô hình tới các miền mới mà không có đánh giá DPIA.
 #11.4.4    Cấp độ: 3    Vai trò: V
 Xác minh rằng các bằng chứng theo dõi chính thức cho thấy mọi chu trình dữ liệu cá nhân đều nằm trong phạm vi đã được đồng ý.

---

### 11.5 Quản lý sự đồng ý & Theo dõi cơ sở hợp pháp

 #11.5.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng Nền tảng Quản lý Sự đồng ý (CMP) ghi lại trạng thái chọn tham gia, mục đích và thời gian lưu giữ cho từng chủ thể dữ liệu.
 #11.5.2    Cấp độ: 2    Vai trò: D
 Xác minh rằng các API tiết lộ token đồng ý; các mô hình phải xác thực phạm vi token trước khi suy luận.
 #11.5.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng việc từ chối hoặc rút lại sự đồng ý sẽ dừng các quy trình xử lý trong vòng 24 giờ.

---

### 11.6 Học Liên Liền với Các Điều Khiển Quyền Riêng Tư

 #11.6.1    Cấp độ: 1    Vai trò: D
 Xác minh rằng các bản cập nhật của khách hàng sử dụng việc thêm nhiễu bảo mật vi phân cục bộ trước khi tổng hợp.
 #11.6.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các chỉ số huấn luyện có tính riêng tư vi phân và không bao giờ tiết lộ mất mát của từng khách hàng đơn lẻ.
 #11.6.3    Cấp độ: 2    Vai trò: V
 Xác minh rằng tập hợp chống tấn công đầu độc (ví dụ, Krum/Trimmed-Mean) đã được kích hoạt.
 #11.6.4    Cấp độ: 3    Vai trò: V
 Xác minh rằng các bằng chứng chính thức chứng minh tổng ngân sách ε với mức mất mát tiện ích dưới 5.

---

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

Phần này cung cấp các yêu cầu để cung cấp khả năng quan sát thời gian thực và phân tích pháp y về những gì mô hình và các thành phần AI khác nhìn thấy, thực hiện và trả về, nhằm phát hiện, phân loại và rút ra bài học từ các mối đe dọa.

### C12.1 Ghi nhật ký Yêu cầu & Phản hồi

 #12.1.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng tất cả các yêu cầu của người dùng và phản hồi của mô hình đều được ghi lại cùng với siêu dữ liệu phù hợp (ví dụ: dấu thời gian, ID người dùng, ID phiên, phiên bản mô hình).
 #12.1.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các bản ghi được lưu trữ trong các kho lưu trữ an toàn, có kiểm soát truy cập với các chính sách lưu giữ và quy trình sao lưu phù hợp.
 #12.1.3    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các hệ thống lưu trữ nhật ký đã triển khai mã hóa khi lưu trữ và truyền tải để bảo vệ thông tin nhạy cảm chứa trong các nhật ký.
 #12.1.4    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng dữ liệu nhạy cảm trong các lời nhắc và kết quả được tự động làm mờ hoặc che giấu trước khi ghi lại, với các quy tắc làm mờ có thể cấu hình cho thông tin nhận dạng cá nhân (PII), thông tin đăng nhập và thông tin độc quyền.
 #12.1.5    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các quyết định chính sách và hành động lọc an toàn được ghi lại với chi tiết đầy đủ để cho phép kiểm tra và gỡ lỗi các hệ thống kiểm duyệt nội dung.
 #12.1.6    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng tính toàn vẹn của nhật ký được bảo vệ thông qua ví dụ như chữ ký mật mã hoặc lưu trữ chỉ ghi.

---

### C12.2 Phát hiện và Cảnh báo Lạm dụng

 #12.2.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng hệ thống phát hiện và cảnh báo các mẫu jailbreak đã biết, các cố gắng chèn prompt, và các đầu vào đối kháng sử dụng phương pháp phát hiện dựa trên chữ ký.
 #12.2.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng hệ thống tích hợp với các nền tảng Quản lý Thông tin và Sự kiện Bảo mật (SIEM) hiện có bằng cách sử dụng các định dạng và giao thức nhật ký tiêu chuẩn.
 #12.2.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các sự kiện bảo mật được làm giàu bao gồm ngữ cảnh đặc thù của AI như các định danh mô hình, điểm tin cậy và các quyết định bộ lọc an toàn.
 #12.2.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng phát hiện bất thường hành vi có thể nhận diện được các mẫu hội thoại bất thường, số lần thử lại quá mức hoặc các hành vi thăm dò có hệ thống.
 #12.2.5    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các cơ chế cảnh báo theo thời gian thực thông báo cho nhóm bảo mật khi phát hiện các vi phạm chính sách tiềm ẩn hoặc các cố gắng tấn công.
 #12.2.6    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng các quy tắc tùy chỉnh được đưa vào để phát hiện các mẫu mối đe dọa đặc thù AI bao gồm các nỗ lực phá vỡ phối hợp, chiến dịch tiêm lệnh yêu cầu và các cuộc tấn công trích xuất mô hình.
 #12.2.7    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các quy trình tự động phản ứng sự cố có thể cô lập các mô hình bị xâm phạm, chặn người dùng độc hại và nâng cao các sự kiện an ninh quan trọng.

---

### C12.3 Phát hiện Trôi mô hình

 #12.3.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng hệ thống theo dõi các chỉ số hiệu suất cơ bản như độ chính xác, điểm tin cậy, độ trễ và tỷ lệ lỗi qua các phiên bản mô hình và khoảng thời gian.
 #12.3.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng hệ thống cảnh báo tự động được kích hoạt khi các chỉ số hiệu suất vượt quá ngưỡng suy giảm đã định trước hoặc lệch đáng kể so với các giá trị nền.
 #12.3.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các bộ giám sát phát hiện ảo giác có thể nhận diện và đánh dấu các trường hợp khi kết quả mô hình chứa thông tin sai sự thật, không nhất quán hoặc bịa đặt.

---

### C12.4 Hiệu suất & Dữ liệu Theo dõi Hành vi

 #12.4.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các chỉ số vận hành bao gồm độ trễ yêu cầu, mức tiêu thụ token, sử dụng bộ nhớ và thông lượng được liên tục thu thập và giám sát.
 #12.4.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng tỷ lệ thành công và thất bại được theo dõi cùng với việc phân loại các loại lỗi và nguyên nhân gốc rễ của chúng.
 #12.4.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng việc giám sát sử dụng tài nguyên bao gồm sử dụng GPU/CPU, tiêu thụ bộ nhớ và yêu cầu lưu trữ với cảnh báo khi vượt ngưỡng.

---

### C12.5 Lập Kế Hoạch & Thực Thi Phản Ứng Sự Cố AI

 #12.5.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các kế hoạch ứng phó sự cố cụ thể xử lý các sự kiện bảo mật liên quan đến AI bao gồm xâm phạm mô hình, đầu độc dữ liệu và các cuộc tấn công đối kháng.
 #12.5.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các nhóm ứng phó sự cố có quyền truy cập vào các công cụ pháp y chuyên dụng cho AI và chuyên môn để điều tra hành vi mô hình và các vectơ tấn công.
 #12.5.3    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng phân tích sau sự cố bao gồm các xem xét về tái huấn luyện mô hình, cập nhật bộ lọc an toàn và tích hợp bài học kinh nghiệm vào các biện pháp kiểm soát an ninh.

---

### C12.5 Phát hiện suy giảm hiệu suất AI

Giám sát và phát hiện sự suy giảm trong hiệu suất và chất lượng của mô hình AI theo thời gian.

 #12.5.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng độ chính xác của mô hình, độ chính xác, độ bao phủ và điểm số F1 được liên tục theo dõi và so sánh với các ngưỡng cơ sở.
 #12.5.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng phát hiện trôi dữ liệu giám sát các thay đổi phân phối đầu vào có thể ảnh hưởng đến hiệu suất của mô hình.
 #12.5.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng phát hiện trôi khái niệm nhận biết sự thay đổi trong mối quan hệ giữa các đầu vào và đầu ra dự kiến.
 #12.5.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng sự suy giảm hiệu suất kích hoạt cảnh báo tự động và khởi động quy trình đào tạo lại hoặc thay thế mô hình.
 #12.5.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng phân tích nguyên nhân gốc rễ của suy giảm liên kết sự giảm hiệu suất với các thay đổi dữ liệu, các vấn đề hạ tầng hoặc các yếu tố bên ngoài.

---

### C12.6 Hiển thị DAG & Bảo mật Quy trình làm việc

Bảo vệ hệ thống trực quan hóa luồng công việc khỏi rò rỉ thông tin và các cuộc tấn công thao túng.

 #12.6.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng dữ liệu trực quan hóa DAG được làm sạch để loại bỏ thông tin nhạy cảm trước khi lưu trữ hoặc truyền tải.
 #12.6.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các kiểm soát truy cập trực quan hóa quy trình làm việc đảm bảo chỉ người dùng được ủy quyền mới có thể xem các đường dẫn quyết định của tác nhân và các dấu vết lập luận.
 #12.6.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng tính toàn vẹn dữ liệu DAG được bảo vệ thông qua chữ ký mật mã và các cơ chế lưu trữ có khả năng phát hiện giả mạo.
 #12.6.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng hệ thống trực quan hóa quy trình làm việc thực hiện kiểm tra đầu vào để ngăn chặn các cuộc tấn công chèn mã thông qua dữ liệu nút hoặc cạnh được tạo.
 #12.6.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các cập nhật DAG theo thời gian thực được giới hạn tần suất và xác thực để ngăn ngừa các cuộc tấn công từ chối dịch vụ vào hệ thống trực quan hóa.

---

### C12.7 Giám sát Hành vi Bảo mật Chủ động

Phát hiện và ngăn chặn các mối đe dọa bảo mật thông qua phân tích hành vi tác nhân chủ động.

 #12.7.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các hành vi của tác nhân chủ động được kiểm chứng bảo mật trước khi thực thi với tích hợp đánh giá rủi ro.
 #12.7.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các tác nhân khởi xướng tự động bao gồm đánh giá bối cảnh bảo mật và đánh giá cảnh quan mối đe dọa.
 #12.7.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các mô hình hành vi chủ động được phân tích để xác định các tác động tiềm ẩn về bảo mật và các hệ quả không mong muốn.
 #12.7.4    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng các hành động chủ động quan trọng về bảo mật yêu cầu chuỗi phê duyệt rõ ràng kèm theo dấu vết kiểm tra.
 #12.7.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng phát hiện bất thường hành vi nhận diện được các sai lệch trong các mẫu tác nhân chủ động có thể chỉ ra sự xâm phạm.

---

### Tài liệu tham khảo

NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3
ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6
EU AI Act — Article 12, 13, 16 and 19 on Logging and Record-keeping

## C13 Giám sát con người, Trách nhiệm và Quản trị

### Mục tiêu Kiểm soát

Chương này cung cấp các yêu cầu để duy trì sự giám sát của con người và các chuỗi trách nhiệm rõ ràng trong các hệ thống AI, đảm bảo khả năng giải thích, tính minh bạch và quản lý đạo đức trong suốt vòng đời của AI.

---

### C13.1 Cơ chế Ngắt kết nối khẩn cấp và Ghi đè

Cung cấp các phương án tắt hoặc phục hồi khi phát hiện hành vi không an toàn của hệ thống AI.

 #13.1.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng có cơ chế công tắc ngắt thủ công để ngay lập tức dừng việc suy diễn và đầu ra của mô hình AI.
 #13.1.2    Cấp độ: 1    Vai trò: D
 Xác minh rằng các biện pháp kiểm soát ghi đè chỉ có thể truy cập bởi nhân sự được ủy quyền.
 #13.1.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các quy trình hoàn tác có thể khôi phục lại các phiên bản mô hình trước đó hoặc các hoạt động ở chế độ an toàn.
 #13.1.4    Cấp độ: 3    Vai trò: V
 Xác minh rằng các cơ chế ghi đè được kiểm tra thường xuyên.

---

### C13.2 Các Điểm Kiểm Tra Quyết Định Có Con Người Tham Gia

Yêu cầu phê duyệt của con người khi mức độ rủi ro vượt quá ngưỡng đã định trước.

 #13.2.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các quyết định AI có rủi ro cao yêu cầu phải có sự phê duyệt rõ ràng của con người trước khi thực thi.
 #13.2.2    Cấp độ: 1    Vai trò: D
 Xác minh rằng các ngưỡng rủi ro được xác định rõ ràng và tự động kích hoạt quy trình xem xét của con người.
 #13.2.3    Cấp độ: 2    Vai trò: D
 Xác minh rằng các quyết định nhạy cảm về thời gian có các quy trình dự phòng khi không thể nhận được sự phê duyệt của con người trong khung thời gian yêu cầu.
 #13.2.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các quy trình leo thang xác định rõ các cấp độ thẩm quyền cho các loại quyết định hoặc danh mục rủi ro khác nhau, nếu có.

---

### C13.3 Chuỗi Trách Nhiệm & Khả Năng Kiểm Toán

Ghi lại các hành động của người vận hành và các quyết định của mô hình.

 #13.3.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng tất cả các quyết định của hệ thống AI và các can thiệp của con người được ghi lại với dấu thời gian, danh tính người dùng và lý do đưa ra quyết định.
 #13.3.2    Cấp độ: 2    Vai trò: D
 Xác minh rằng các bản ghi kiểm toán không thể bị sửa đổi và bao gồm các cơ chế xác minh tính toàn vẹn.

---

### C13.4 Kỹ thuật Trí tuệ Nhân tạo Có thể Giải thích được

Tầm quan trọng của đặc điểm bề mặt, phản sự thật, và giải thích cục bộ.

 #13.4.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các hệ thống AI cung cấp các giải thích cơ bản cho các quyết định của chúng dưới dạng có thể đọc hiểu đối với con người.
 #13.4.2    Cấp độ: 2    Vai trò: V
 Xác minh rằng chất lượng giải thích được đánh giá thông qua các nghiên cứu và chỉ số đánh giá của con người.
 #13.4.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng điểm quan trọng của tính năng hoặc các phương pháp gán trọng số (SHAP, LIME, v.v.) có sẵn cho các quyết định quan trọng.
 #13.4.4    Cấp độ: 3    Vai trò: V
 Xác minh rằng các giải thích phản thực tế cho thấy cách các đầu vào có thể được điều chỉnh để thay đổi kết quả, nếu áp dụng cho trường hợp sử dụng và lĩnh vực tương ứng.

---

### C13.5 Thẻ Mô hình & Công khai Sử dụng

Duy trì thẻ mô hình cho mục đích sử dụng dự kiến, chỉ số hiệu suất và các cân nhắc đạo đức.

 #13.5.1    Cấp độ: 1    Vai trò: D
 Xác minh rằng các thẻ mô hình ghi lại các trường hợp sử dụng dự kiến, các hạn chế và các chế độ lỗi đã biết.
 #13.5.2    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng các chỉ số hiệu suất trong các trường hợp sử dụng phù hợp khác nhau đã được công bố.
 #13.5.3    Cấp độ: 2    Vai trò: D
 Xác nhận rằng các cân nhắc đạo đức, đánh giá thiên vị, đánh giá công bằng, đặc điểm dữ liệu đào tạo và các hạn chế dữ liệu đào tạo đã biết được ghi chép và cập nhật thường xuyên.
 #13.5.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các thẻ mô hình được kiểm soát phiên bản và duy trì trong suốt vòng đời mô hình với việc theo dõi thay đổi.

---

### C13.6 Định lượng độ không chắc chắn

Truyền đạt các điểm số độ tin cậy hoặc các đo lường entropy trong các phản hồi.

 #13.6.1    Cấp độ: 1    Vai trò: D
 Xác minh rằng các hệ thống AI cung cấp điểm tin cậy hoặc các biện pháp không chắc chắn cùng với kết quả đầu ra của chúng.
 #13.6.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng ngưỡng không chắc chắn kích hoạt việc xem xét thêm bởi con người hoặc các đường dẫn quyết định thay thế.
 #13.6.3    Cấp độ: 2    Vai trò: V
 Xác minh rằng các phương pháp định lượng sự không chắc chắn được hiệu chuẩn và xác thực đối với dữ liệu sự thật cơ bản.
 #13.6.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng sự lan truyền bất định được duy trì qua các quy trình làm việc AI đa bước.

---

### C13.7 Báo Cáo Minh Bạch Hướng Đến Người Dùng

Cung cấp các báo cáo định kỳ về các sự cố, sự trôi dạt và việc sử dụng dữ liệu.

 #13.7.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các chính sách sử dụng dữ liệu và thực hành quản lý sự đồng ý của người dùng được truyền đạt rõ ràng tới các bên liên quan.
 #13.7.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các đánh giá tác động của AI đã được tiến hành và kết quả được bao gồm trong báo cáo.
 #13.7.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các báo cáo minh bạch được công bố định kỳ công khai các sự cố AI và các chỉ số vận hành với mức độ chi tiết hợp lý.

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
GDPR — Article 5 "Transparency Principle" (Regulation (EU) 2016/679)
Human Oversight under Article 14 of the EU AI Act (Fink, 2025)

## Phụ lục A: Bảng chú giải thuật ngữ

Bảng thuật ngữ toàn diện này cung cấp các định nghĩa về các thuật ngữ chính trong AI, ML và bảo mật được sử dụng trong toàn bộ AISVS để đảm bảo sự rõ ràng và hiểu biết chung.

Ví dụ đối nghịch: Một đầu vào được tạo ra cố ý để khiến mô hình AI mắc lỗi, thường bằng cách thêm các nhiễu nhỏ tinh vi mà con người không thể nhận thấy.
​
Độ bền vững chống đối – Độ bền vững chống đối trong AI đề cập đến khả năng của một mô hình duy trì hiệu suất và chống lại việc bị lừa hoặc thao túng bởi các đầu vào độc hại được tạo ra có chủ ý nhằm gây ra lỗi.
​
Agent – Các tác nhân AI là các hệ thống phần mềm sử dụng AI để theo đuổi mục tiêu và hoàn thành các nhiệm vụ thay mặt người dùng. Chúng thể hiện khả năng suy luận, lập kế hoạch và nhớ, đồng thời có mức độ tự chủ để đưa ra quyết định, học hỏi và thích nghi.
​
AI tác nhân: Các hệ thống AI có thể hoạt động với một mức độ tự chủ nhất định để đạt được mục tiêu, thường đưa ra quyết định và thực hiện hành động mà không cần sự can thiệp trực tiếp của con người.
​
Kiểm soát truy cập dựa trên thuộc tính (ABAC): Một mô hình kiểm soát truy cập trong đó các quyết định ủy quyền dựa trên thuộc tính của người dùng, tài nguyên, hành động và môi trường, được đánh giá tại thời điểm truy vấn.
​
Tấn công Cửa hậu: Một loại tấn công đầu độc dữ liệu trong đó mô hình được huấn luyện để phản hồi theo một cách cụ thể đối với các kích hoạt nhất định trong khi hành xử bình thường trong các trường hợp khác.
​
Thiên lệch: Lỗi hệ thống trong đầu ra của mô hình AI có thể dẫn đến kết quả không công bằng hoặc phân biệt đối xử đối với một số nhóm hoặc trong các bối cảnh cụ thể.
​
Khai thác Định kiến: Một kỹ thuật tấn công tận dụng các định kiến đã biết trong các mô hình AI để thao túng đầu ra hoặc kết quả.
​
Cedar: Ngôn ngữ chính sách và công cụ của Amazon để cấp quyền chi tiết được sử dụng trong việc triển khai ABAC cho các hệ thống AI.
​
Chuỗi Tư duy: Một kỹ thuật để cải thiện khả năng suy luận trong các mô hình ngôn ngữ bằng cách tạo ra các bước suy luận trung gian trước khi đưa ra câu trả lời cuối cùng.
​
Cầu dao tự động: Cơ chế tự động dừng hoạt động của hệ thống AI khi vượt quá ngưỡng rủi ro nhất định.
​
Rò rỉ dữ liệu: Tiếp xúc không mong muốn của thông tin nhạy cảm thông qua các kết quả hoặc hành vi của mô hình AI.
​
Đầu độc dữ liệu: Việc cố ý làm hỏng dữ liệu huấn luyện nhằm làm suy yếu tính toàn vẹn của mô hình, thường để cài đặt cửa hậu hoặc làm giảm hiệu suất.
​
Bảo mật vi phân – Bảo mật vi phân là một khuôn khổ toán học nghiêm ngặt để công bố thông tin thống kê về các tập dữ liệu trong khi bảo vệ quyền riêng tư của các cá nhân trong dữ liệu. Nó cho phép người giữ dữ liệu chia sẻ các mẫu tổng hợp của nhóm đồng thời hạn chế việc rò rỉ thông tin về các cá nhân cụ thể.
​
Embeddings: Biểu diễn vectơ dày đặc của dữ liệu (văn bản, hình ảnh, v.v.) chứa đựng ý nghĩa ngữ nghĩa trong không gian đa chiều.
​
Khả năng giải thích – Khả năng giải thích trong AI là khả năng của một hệ thống AI để cung cấp các lý do mà con người có thể hiểu được cho các quyết định và dự đoán của nó, cung cấp cái nhìn sâu sắc về cách hoạt động nội bộ của nó.
​
AI giải thích được (XAI): Các hệ thống AI được thiết kế để cung cấp các giải thích dễ hiểu cho con người về các quyết định và hành vi của chúng thông qua nhiều kỹ thuật và khuôn khổ khác nhau.
​
Học Liên Phân Tán: Một phương pháp học máy trong đó các mô hình được đào tạo trên nhiều thiết bị phi tập trung giữ các mẫu dữ liệu cục bộ, mà không trao đổi dữ liệu trực tiếp.
​
Guardrails: Các giới hạn được thực hiện để ngăn các hệ thống AI tạo ra các kết quả đầu ra gây hại, thiên vị hoặc không mong muốn khác.
​
Ảo giác – Ảo giác AI là hiện tượng khi một mô hình AI tạo ra thông tin sai lệch hoặc gây hiểu lầm không dựa trên dữ liệu đào tạo hoặc thực tế khách quan.
​
Con người trong vòng lặp (Human-in-the-Loop - HITL): Các hệ thống được thiết kế để yêu cầu sự giám sát, xác minh hoặc can thiệp của con người tại các điểm quyết định quan trọng.
​
Hạ tầng dưới dạng mã (IaC): Quản lý và cung cấp hạ tầng thông qua mã thay vì các quy trình thủ công, cho phép quét bảo mật và triển khai nhất quán.
​
Jailbreak: Kỹ thuật được sử dụng để vượt qua các rào cản an toàn trong hệ thống AI, đặc biệt là trong các mô hình ngôn ngữ lớn, nhằm tạo ra nội dung bị cấm.
​
Nguyên tắc Quyền ít nhất: Nguyên tắc bảo mật chỉ cấp quyền truy cập tối thiểu cần thiết cho người dùng và các tiến trình.
​
LIME (Giải thích Mô hình Độc lập cục bộ): Một kỹ thuật để giải thích các dự đoán của bất kỳ bộ phân loại học máy nào bằng cách xấp xỉ chúng tại chỗ với một mô hình có thể giải thích được.
​
Tấn công suy luận thành viên: Một cuộc tấn công nhằm xác định liệu một điểm dữ liệu cụ thể có được sử dụng để huấn luyện mô hình học máy hay không.
​
MITRE ATLAS: Cảnh quan mối đe dọa đối kháng cho hệ thống Trí tuệ Nhân tạo; một cơ sở kiến thức về các chiến thuật và kỹ thuật đối kháng chống lại hệ thống AI.
​
Thẻ Mô Hình – Thẻ mô hình là một tài liệu cung cấp thông tin chuẩn hóa về hiệu suất, giới hạn, mục đích sử dụng và các cân nhắc đạo đức của mô hình AI nhằm thúc đẩy sự minh bạch và phát triển AI có trách nhiệm.
​
Trích xuất mô hình: Một cuộc tấn công trong đó kẻ tấn công liên tục truy vấn một mô hình mục tiêu để tạo ra một bản sao có chức năng tương tự mà không được phép.
​
Đảo ngược mô hình: Một cuộc tấn công cố gắng tái tạo dữ liệu huấn luyện bằng cách phân tích kết quả đầu ra của mô hình.
​
Quản lý Vòng đời Mô hình – Quản lý vòng đời mô hình AI là quá trình giám sát tất cả các giai đoạn tồn tại của một mô hình AI, bao gồm thiết kế, phát triển, triển khai, giám sát, bảo trì và cuối cùng là ngừng sử dụng, nhằm đảm bảo mô hình luôn hiệu quả và phù hợp với các mục tiêu đề ra.
​
Đầu độc mô hình: Giới thiệu lỗ hổng hoặc cánh cửa sau trực tiếp vào mô hình trong quá trình huấn luyện.
​
Đánh cắp/Mô hình ăn cắp: Trích xuất một bản sao hoặc bản gần đúng của mô hình độc quyền thông qua các truy vấn lặp đi lặp lại.
​
Hệ thống đa tác nhân: Một hệ thống gồm nhiều tác nhân AI tương tác với nhau, mỗi tác nhân có thể có các khả năng và mục tiêu khác nhau.
​
OPA (Open Policy Agent): Một công cụ chính sách mã nguồn mở cho phép thi hành chính sách thống nhất trên toàn bộ hệ thống.
​
Học Máy Bảo Vệ Quyền Riêng Tư (PPML): Các kỹ thuật và phương pháp để huấn luyện và triển khai mô hình ML đồng thời bảo vệ quyền riêng tư của dữ liệu huấn luyện.
​
Chèn lệnh vào lời nhắc: Một cuộc tấn công trong đó các chỉ dẫn độc hại được nhúng vào đầu vào để ghi đè hành vi dự định của mô hình.
​
RAG (Tạo sinh tăng cường truy xuất): Một kỹ thuật nâng cao các mô hình ngôn ngữ lớn bằng cách truy xuất thông tin liên quan từ các nguồn kiến thức bên ngoài trước khi tạo ra phản hồi.
​
Red-Teaming: Thực hành kiểm thử chủ động các hệ thống AI bằng cách mô phỏng các cuộc tấn công đối kháng nhằm xác định các điểm yếu.
​
SBOM (Danh sách thành phần phần mềm): Một bản ghi chính thức chứa các chi tiết và mối quan hệ chuỗi cung ứng của các thành phần khác nhau được sử dụng trong việc xây dựng phần mềm hoặc mô hình AI.
​
SHAP (Giải thích Cộng thêm Shapley): Một phương pháp lý thuyết trò chơi để giải thích kết quả của bất kỳ mô hình học máy nào bằng cách tính toán đóng góp của mỗi đặc trưng vào dự đoán.
​
Tấn công chuỗi cung ứng: Xâm nhập hệ thống bằng cách nhắm vào các yếu tố bảo mật kém hơn trong chuỗi cung ứng của nó, chẳng hạn như thư viện bên thứ ba, bộ dữ liệu hoặc mô hình đã được huấn luyện sẵn.
​
Học chuyển giao: Một kỹ thuật trong đó một mô hình được phát triển cho một nhiệm vụ được sử dụng lại làm điểm khởi đầu cho một mô hình cho nhiệm vụ thứ hai.
​
Cơ sở dữ liệu vector: Một cơ sở dữ liệu chuyên biệt được thiết kế để lưu trữ các vector đa chiều cao (embedding) và thực hiện các tìm kiếm tương đồng hiệu quả.
​
Quét Lỗ Hổng Bảo Mật: Công cụ tự động xác định các lỗ hổng bảo mật đã biết trong các thành phần phần mềm, bao gồm cả khung AI và các phụ thuộc.
​
Đóng dấu bản quyền: Các kỹ thuật nhúng các dấu hiệu không thể nhận biết vào nội dung do AI tạo ra để theo dõi nguồn gốc hoặc phát hiện nội dung được tạo bởi AI.
​
Lỗ hổng Zero-Day: Một lỗ hổng chưa được biết đến trước đó mà kẻ tấn công có thể khai thác trước khi các nhà phát triển tạo và triển khai bản vá.

## Phụ lục B: Tài liệu tham khảo

### TODO

## Phụ lục C: Quản trị và Tài liệu An ninh AI

### Mục tiêu

Phụ lục này cung cấp các yêu cầu cơ bản để thiết lập các cấu trúc tổ chức, chính sách và quy trình quản lý an ninh AI trong suốt vòng đời hệ thống.

---

### AC.1 Áp dụng Khung Quản lý Rủi ro AI

Cung cấp một khuôn khổ chính thức để xác định, đánh giá và giảm thiểu các rủi ro đặc thù của AI trong suốt vòng đời hệ thống.

 #AC.1.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng phương pháp đánh giá rủi ro dành riêng cho AI được ghi chép và thực hiện.
 #AC.1.2    Cấp độ: 2    Vai trò: D
 Xác minh rằng các đánh giá rủi ro được thực hiện tại các điểm then chốt trong vòng đời AI và trước những thay đổi đáng kể.
 #AC.1.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng khung quản lý rủi ro phù hợp với các tiêu chuẩn đã được thiết lập (ví dụ: NIST AI RMF).

---

### Chính sách & Quy trình An ninh AI AC.2

Xác định và thực thi các tiêu chuẩn tổ chức cho phát triển, triển khai và vận hành AI an toàn.

 #AC.2.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các chính sách bảo mật AI đã được tài liệu hóa tồn tại.
 #AC.2.2    Cấp độ: 2    Vai trò: D
 Xác minh rằng các chính sách được xem xét và cập nhật ít nhất hàng năm và sau những thay đổi đáng kể về cảnh quan mối đe dọa.
 #AC.2.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các chính sách bao phủ tất cả các danh mục AISVS và các yêu cầu quy định áp dụng.

---

### AC.3 Vai trò & Trách nhiệm cho An ninh AI

Thiết lập trách nhiệm rõ ràng về an ninh AI trong toàn tổ chức.

 #AC.3.1    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng các vai trò và trách nhiệm về bảo mật AI đã được ghi chép lại.
 #AC.3.2    Cấp độ: 2    Vai trò: D
 Xác minh rằng các cá nhân chịu trách nhiệm có chuyên môn bảo mật phù hợp.
 #AC.3.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng một ủy ban đạo đức AI hoặc ban quản trị được thành lập cho các hệ thống AI rủi ro cao.

---

### AC.4 Thi hành Hướng dẫn về Trí tuệ Nhân tạo Đạo đức

Đảm bảo các hệ thống AI hoạt động theo các nguyên tắc đạo đức đã được thiết lập.

 #AC.4.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng có tồn tại các hướng dẫn đạo đức cho việc phát triển và triển khai AI.
 #AC.4.2    Cấp độ: 2    Vai trò: D
 Xác minh rằng các cơ chế đã được thiết lập để phát hiện và báo cáo các vi phạm đạo đức.
 #AC.4.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các đánh giá đạo đức thường xuyên đối với các hệ thống AI đã triển khai được thực hiện.

---

### AC.5 Giám sát Tuân thủ Quy định AI

Duy trì nhận thức và tuân thủ các quy định AI đang phát triển.

 #AC.5.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng có các quy trình để xác định các quy định AI áp dụng.
 #AC.5.2    Cấp độ: 2    Vai trò: D
 Xác minh rằng việc tuân thủ tất cả các yêu cầu quy định đã được đánh giá.
 #AC.5.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các thay đổi quy định kích hoạt việc xem xét và cập nhật hệ thống AI kịp thời.

### AC.6 Quản trị Dữ liệu Đào tạo, Tài liệu và Quy trình

 #1.1.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng chỉ những bộ dữ liệu đã được kiểm duyệt về chất lượng, tính đại diện, nguồn gốc đạo đức và tuân thủ bản quyền được phép sử dụng, nhằm giảm thiểu rủi ro về tấn công dữ liệu độc hại, thiên vị ẩn và vi phạm quyền sở hữu trí tuệ.
 #1.1.5    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng chất lượng gán nhãn/chú thích được đảm bảo thông qua việc kiểm tra chéo hoặc đồng thuận của người đánh giá.
 #1.1.6    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng "thẻ dữ liệu" hoặc "bảng dữ liệu cho các bộ dữ liệu" được duy trì cho các bộ dữ liệu đào tạo quan trọng, chi tiết các đặc điểm, động cơ, thành phần, quy trình thu thập, tiền xử lý và các mục đích sử dụng được khuyến nghị/không khuyến nghị.
 #1.3.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các thiên kiến đã được xác định được giảm thiểu thông qua các chiến lược đã được tài liệu hóa như tái cân bằng, tăng cường dữ liệu có mục tiêu, điều chỉnh thuật toán (ví dụ: kỹ thuật tiền xử lý, xử lý trong quá trình, xử lý sau), hoặc tái trọng số, và đánh giá tác động của việc giảm thiểu đối với cả tính công bằng và hiệu suất tổng thể của mô hình.
 #1.3.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các chỉ số công bằng sau khi huấn luyện được đánh giá và ghi chép lại.
 #1.3.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng chính sách quản lý thiên vị vòng đời chỉ định người chịu trách nhiệm và chu kỳ đánh giá.
 #1.4.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng chất lượng gán nhãn/ghi chú được đảm bảo thông qua các hướng dẫn rõ ràng, việc kiểm tra chéo của người đánh giá, cơ chế đồng thuận (ví dụ: theo dõi sự đồng thuận giữa các người gán nhãn), và các quy trình đã định nghĩa để giải quyết các khác biệt.
 #1.4.4    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng các nhãn quan trọng đối với an toàn, bảo mật hoặc công bằng (ví dụ: xác định nội dung độc hại, các phát hiện y tế quan trọng) được yêu cầu phải được đánh giá độc lập kép bắt buộc hoặc phương pháp xác minh mạnh tương đương.
 #1.4.6    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng hướng dẫn và chỉ dẫn gán nhãn đầy đủ, được kiểm soát phiên bản và được đánh giá bởi đồng nghiệp.
 #1.4.6    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các sơ đồ dữ liệu cho nhãn được định nghĩa rõ ràng và được kiểm soát phiên bản.
 #1.3.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các bộ dữ liệu được khảo sát về sự mất cân bằng đại diện và các thiên kiến tiềm ẩn liên quan đến các thuộc tính được bảo vệ theo pháp luật (ví dụ: chủng tộc, giới tính, tuổi tác) và các đặc điểm nhạy cảm về mặt đạo đức khác liên quan đến lĩnh vực ứng dụng của mô hình (ví dụ: tình trạng kinh tế - xã hội, vị trí địa lý).
 #1.5.3    Cấp độ: 2    Vai trò: V
 Xác minh rằng việc kiểm tra ngẫu nhiên thủ công bởi các chuyên gia lĩnh vực bao phủ một mẫu có ý nghĩa thống kê (ví dụ, ≥1% hoặc 1.000 mẫu, tùy theo giá trị lớn hơn, hoặc theo đánh giá rủi ro) để phát hiện các vấn đề chất lượng tinh vi mà tự động hóa không phát hiện được.
 #1.8.4    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng các quy trình gán nhãn được thuê ngoài hoặc sử dụng đám đông bao gồm các biện pháp kỹ thuật/thủ tục để đảm bảo tính bảo mật dữ liệu, tính toàn vẹn, chất lượng nhãn và ngăn ngừa rò rỉ dữ liệu.
 #1.5.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các bước khắc phục được thêm vào các bản ghi nguồn gốc.
 #1.6.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các mẫu được đánh dấu kích hoạt việc xem xét thủ công trước khi đào tạo.
 #1.6.3    Cấp độ: 2    Vai trò: V
 Xác minh rằng kết quả được đưa vào hồ sơ bảo mật của mô hình và thông báo cho tình báo mối đe dọa đang diễn ra.
 #1.6.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng logic phát hiện được làm mới với thông tin tình báo mối đe dọa mới.
 #1.6.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các quy trình học trực tuyến giám sát sự dịch chuyển phân phối.
 #1.7.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng quy trình xóa dữ liệu đào tạo đã loại bỏ dữ liệu chính và dữ liệu dẫn xuất và đánh giá tác động lên mô hình, đồng thời đánh giá tác động đối với các mô hình bị ảnh hưởng và, nếu cần thiết, thực hiện các biện pháp xử lý (ví dụ, thông qua đào tạo lại hoặc hiệu chỉnh lại).
 #1.7.2    Cấp độ: 2    Vai trò: D
 Xác minh rằng các cơ chế đã được thiết lập để theo dõi và tôn trọng phạm vi cũng như trạng thái của sự đồng ý của người dùng (và các lần rút lui) đối với dữ liệu được sử dụng trong quá trình đào tạo, đồng thời sự đồng ý được xác nhận trước khi dữ liệu được tích hợp vào các quy trình đào tạo mới hoặc các cập nhật quan trọng của mô hình.
 #1.7.3    Cấp độ: 2    Vai trò: V
 Xác minh rằng các quy trình làm việc được kiểm tra hàng năm và được ghi lại.
 #1.8.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các nhà cung cấp dữ liệu bên thứ ba, bao gồm các nhà cung cấp mô hình đã được đào tạo trước và bộ dữ liệu bên ngoài, đã trải qua các bước thẩm định về bảo mật, quyền riêng tư, nguồn gốc đạo đức và chất lượng dữ liệu trước khi dữ liệu hoặc mô hình của họ được tích hợp.
 #1.8.2    Cấp độ: 1    Vai trò: D
 Xác minh rằng các chuyển khoản bên ngoài sử dụng TLS/xác thực và kiểm tra toàn vẹn.
 #1.8.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các nguồn dữ liệu có rủi ro cao (ví dụ: bộ dữ liệu mã nguồn mở với nguồn gốc không rõ, nhà cung cấp chưa được kiểm duyệt) được kiểm tra kỹ lưỡng hơn, chẳng hạn như phân tích trong môi trường cách ly, kiểm tra chất lượng/độ lệch mở rộng và phát hiện tấn công đầu độc có mục tiêu, trước khi sử dụng trong các ứng dụng nhạy cảm.
 #1.8.4    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng các mô hình đã được huấn luyện trước từ bên thứ ba phải được đánh giá về các thành kiến nhúng, các cánh cửa hậu tiềm ẩn, tính toàn vẹn của kiến trúc và nguồn gốc của dữ liệu huấn luyện gốc trước khi tinh chỉnh hoặc triển khai.
 #1.5.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng nếu sử dụng huấn luyện đối kháng, việc tạo, quản lý và phiên bản hóa các bộ dữ liệu đối kháng được tài liệu hóa và kiểm soát.
 #1.5.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng tác động của việc huấn luyện độ bền chống đối kháng lên hiệu suất mô hình (đối với cả dữ liệu sạch và dữ liệu đối kháng) và các chỉ số công bằng được đánh giá, ghi chép và theo dõi.
 #1.5.4    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng các chiến lược cho đào tạo đối kháng và tính bền vững được xem xét và cập nhật định kỳ để đối phó với các kỹ thuật tấn công đối kháng đang tiến triển.
 #1.4.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các bộ dữ liệu bị lỗi được cách ly với các dấu vết kiểm toán.
 #1.4.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các cổng chất lượng chặn các bộ dữ liệu dưới chuẩn trừ khi có sự chấp thuận ngoại lệ.
 #1.11.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng quy trình tạo dữ liệu tổng hợp, các tham số và mục đích sử dụng dự kiến của dữ liệu tổng hợp đã được ghi chép.
 #1.11.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng dữ liệu tổng hợp đã được đánh giá rủi ro về thiên vị, rò rỉ thông tin cá nhân và các vấn đề đại diện trước khi sử dụng trong huấn luyện.
 #1.12.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng cảnh báo được tạo ra cho các sự kiện truy cập đáng ngờ và được điều tra kịp thời.
 #1.13.1    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng các khoảng thời gian lưu giữ rõ ràng được định nghĩa cho tất cả các bộ dữ liệu đào tạo.
 #1.13.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các bộ dữ liệu được tự động hết hạn, xóa hoặc được xem xét để xóa khi kết thúc vòng đời của chúng.
 #1.13.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các hành động giữ lại và xóa dữ liệu được ghi lại và có thể kiểm tra.
 #1.14.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các yêu cầu về cư trú dữ liệu và chuyển giao xuyên biên giới được xác định và thực thi cho tất cả các bộ dữ liệu.
 #1.14.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các quy định chuyên ngành (ví dụ, y tế, tài chính) được xác định và xử lý trong việc quản lý dữ liệu.
 #1.14.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng việc tuân thủ các luật bảo mật liên quan (ví dụ: GDPR, CCPA) được ghi chép và xem xét định kỳ.
 #1.16.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng có các cơ chế để đáp ứng các yêu cầu của chủ thể dữ liệu về truy cập, chỉnh sửa, hạn chế hoặc phản đối.
 #1.16.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các yêu cầu được ghi lại, theo dõi và hoàn thành trong khung thời gian do pháp luật quy định.
 #1.16.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các quy trình quyền của chủ thể dữ liệu được kiểm tra và xem xét thường xuyên để đảm bảo hiệu quả.
 #1.17.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng một phân tích tác động được thực hiện trước khi cập nhật hoặc thay thế phiên bản bộ dữ liệu, bao gồm hiệu suất mô hình, tính công bằng và tuân thủ.
 #1.17.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng kết quả của phân tích tác động đã được ghi chép và xem xét bởi các bên liên quan phù hợp.
 #1.17.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng có kế hoạch khôi phục trong trường hợp các phiên bản mới gây ra các rủi ro hoặc sự suy giảm không chấp nhận được.
 #1.18.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng tất cả nhân viên tham gia vào việc chú thích dữ liệu đều đã qua kiểm tra lý lịch và được đào tạo về an ninh dữ liệu và quyền riêng tư.
 #1.18.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng tất cả nhân viên chú thích đã ký thỏa thuận bảo mật và không tiết lộ thông tin.
 #1.18.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các nền tảng chú thích thực thi kiểm soát truy cập và giám sát các mối đe dọa từ bên trong.

#### Tài liệu tham khảo

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
ISO/IEC 23894:2023 — Artificial Intelligence — Guidance on Risk Management
EU Artificial Intelligence Act — Regulation (EU) 2024/1689
ISO/IEC 24029‑2:2023 — Robustness of Neural Networks — Methodology for Formal Methods

## Phụ lục D: Quản trị & Xác minh Mã hóa An toàn Hỗ trợ bởi AI

### Mục tiêu

Chương này định nghĩa các kiểm soát tổ chức cơ bản cho việc sử dụng an toàn và hiệu quả các công cụ mã hóa hỗ trợ AI trong quá trình phát triển phần mềm, đảm bảo bảo mật và khả năng truy xuất trong toàn bộ vòng đời phát triển phần mềm (SDLC).

---

### AD.1 Quy trình làm việc mã hóa an toàn được hỗ trợ bởi AI

Tích hợp công cụ AI vào vòng đời phát triển phần mềm bảo mật (SSDLC) của tổ chức mà không làm suy yếu các điểm kiểm soát an ninh hiện có.

 #AD.1.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng một quy trình làm việc đã được tài liệu hóa mô tả khi nào và cách các công cụ AI có thể tạo ra, tổ chức lại hoặc đánh giá mã.
 #AD.1.2    Cấp độ: 2    Vai trò: D
 Xác nhận rằng quy trình làm việc phù hợp với từng giai đoạn của SSDLC (thiết kế, triển khai, rà soát mã, kiểm thử, triển khai).
 #AD.1.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các chỉ số (ví dụ, mật độ lỗ hổng, thời gian trung bình để phát hiện) được thu thập trên mã do AI tạo ra và so sánh với các chuẩn mực chỉ do con người thực hiện.

---

### AD.2 Đánh giá Công cụ AI & Mô hình hóa Mối đe dọa

Đảm bảo các công cụ lập trình AI được đánh giá về khả năng bảo mật, rủi ro và tác động chuỗi cung ứng trước khi áp dụng.

 #AD.2.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng mô hình mối đe dọa cho mỗi công cụ AI xác định được việc sử dụng sai, đảo ngược mô hình, rò rỉ dữ liệu và các rủi ro chuỗi phụ thuộc.
 #AD.2.2    Cấp độ: 2    Vai trò: D
 Xác minh rằng đánh giá công cụ bao gồm phân tích tĩnh/động của bất kỳ thành phần cục bộ nào và đánh giá các điểm cuối SaaS (TLS, xác thực/ủy quyền, ghi log).
 #AD.2.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các đánh giá tuân theo một khung đã được công nhận và được thực hiện lại sau các thay đổi phiên bản lớn.

---

### AD.3 Quản lý Bảo mật Lời nhắc và Ngữ cảnh

Ngăn chặn rò rỉ bí mật, mã độc quyền và dữ liệu cá nhân khi xây dựng các lời nhắc hoặc ngữ cảnh cho các mô hình AI.

 #AD.3.1    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng hướng dẫn bằng văn bản cấm gửi bí mật, thông tin đăng nhập hoặc dữ liệu phân loại trong các lời nhắc.
 #AD.3.2    Cấp độ: 2    Vai trò: D
 Xác minh rằng các biện pháp kiểm soát kỹ thuật (ẩn thông tin phía khách hàng, bộ lọc ngữ cảnh được duyệt) tự động loại bỏ các thông tin nhạy cảm.
 #AD.3.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các câu lệnh và phản hồi được phân tách token, mã hóa khi truyền và lúc lưu trữ, và thời gian lưu giữ tuân thủ chính sách phân loại dữ liệu.

---

### AD.4 Xác thực mã do AI tạo ra

Phát hiện và khắc phục các lỗ hổng bảo mật do đầu ra của AI tạo ra trước khi mã được hợp nhất hoặc triển khai.

 #AD.4.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng mã do AI tạo ra luôn được kiểm tra bởi con người.
 #AD.4.2    Cấp độ: 2    Vai trò: D
 Xác minh rằng các trình quét tự động (SAST/IAST/DAST) được chạy trên mọi pull request chứa mã do AI tạo ra và chặn việc gộp khi phát hiện các lỗi nghiêm trọng.
 #AD.4.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng kiểm thử fuzz vi sai hoặc kiểm thử dựa trên thuộc tính chứng minh các hành vi quan trọng về bảo mật (ví dụ: xác thực đầu vào, logic ủy quyền).

---

### AD.5 Khả năng Giải thích và Truy xuất của Đề xuất Mã nguồn

Cung cấp cho các kiểm toán viên và nhà phát triển cái nhìn sâu sắc về lý do tại sao một đề xuất được đưa ra và cách nó phát triển.

 #AD.5.1    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng các cặp lời nhắc/phản hồi được ghi lại với các ID cam kết.
 #AD.5.2    Cấp độ: 2    Vai trò: D
 Xác minh rằng các nhà phát triển có thể hiển thị trích dẫn mô hình (đoạn trích huấn luyện, tài liệu) hỗ trợ một đề xuất.
 #AD.5.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các báo cáo giải thích được lưu trữ cùng với các tài liệu thiết kế và được tham chiếu trong các đánh giá an ninh, đáp ứng các nguyên tắc truy xuất nguồn gốc của ISO/IEC 42001.

---

### AD.6 Phản hồi liên tục & Tinh chỉnh mô hình

Cải thiện hiệu suất bảo mật mô hình theo thời gian trong khi ngăn chặn sự suy giảm tiêu cực.

 #AD.6.1    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng các nhà phát triển có thể đánh dấu các đề xuất không an toàn hoặc không tuân thủ, và rằng các đánh dấu này được theo dõi.
 #AD.6.2    Cấp độ: 2    Vai trò: D
 Xác minh rằng phản hồi tổng hợp được sử dụng để hỗ trợ điều chỉnh mịn định kỳ hoặc tạo ra dựa trên truy xuất với các kho mã hóa bảo mật đã được kiểm duyệt (ví dụ: Bảng gian lận OWASP).
 #AD.6.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng bộ công cụ đánh giá vòng kín chạy các bài kiểm tra hồi quy sau mỗi lần tinh chỉnh; các chỉ số an ninh phải đạt hoặc vượt mức chuẩn trước đó trước khi triển khai.

---

#### Tài liệu tham khảo

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
OWASP Secure Coding Practices — Quick Reference Guide

## Phụ lục E: Ví dụ về Công cụ và Khung công tác

### Mục tiêu

Chương này cung cấp các ví dụ về công cụ và khung làm việc có thể hỗ trợ việc triển khai hoặc đáp ứng một yêu cầu AISVS cụ thể. Những ví dụ này không được xem là khuyến nghị hay sự ủng hộ của nhóm AISVS hoặc Dự án An ninh OWASP GenAI.

---

### Quản trị Dữ liệu Đào tạo & Quản lý Định kiến AE.1

Công cụ được sử dụng cho phân tích dữ liệu, quản trị và quản lý thiên vị.

 #AE.1.1    Phần: 1.1
 Công cụ quản lý danh mục dữ liệu: Công cụ quản lý danh mục dữ liệu như...
 #AE.1.2    Phần: 1.2
 Mã hóa trong quá trình truyền Dùng TLS cho các ứng dụng dựa trên HTTPS, với các công cụ như openSSL và python's`ssl`thư viện.

---

### AE.2 Xác thực Đầu vào Người dùng

Công cụ để xử lý và xác thực đầu vào của người dùng.

 #AE.2.1    Phần: 2.1
 Công cụ phòng chống tiêm nhiễm lệnh: Sử dụng công cụ bảo vệ như NeMo của NVIDIA hoặc Guardrails AI.

---

