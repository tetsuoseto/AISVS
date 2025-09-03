## Mặt minh họa đầu sách

### Về Tiêu chuẩn

Tiêu chuẩn xác thực an ninh Trí tuệ nhân tạo (AISVS) là một danh mục do cộng đồng đóng góp, dành cho các nhà khoa học dữ liệu, kỹ sư MLOps, kiến trúc sư phần mềm, nhà phát triển, nhà kiểm thử, chuyên gia bảo mật, nhà cung cấp công cụ, cơ quan quản lý và người tiêu dùng có thể sử dụng để thiết kế, xây dựng, thử nghiệm và xác minh các hệ thống và ứng dụng AI đáng tin cậy. Nó cung cấp một ngôn ngữ chung để xác định các biện pháp kiểm soát bảo mật xuyên suốt vòng đời AI, từ dữ liệu thu thập và phát triển mô hình đến triển khai và giám sát liên tục, để các tổ chức có thể đo lường và cải thiện khả năng phục hồi, quyền riêng tư và an toàn của các giải pháp AI của họ.

### Bản quyền và Giấy phép

Phiên bản 0.1 (Bản thảo công khai đầu tiên - Đang tiến hành), 2025  

![license](images/license.png)
Bản quyền © 2025 Dự án AISVS.  

Được phát hành dướiCreative Commons Attribution‑ShareAlike 4.0 International License.
Đối với bất kỳ lần tái sử dụng hoặc phân phối nào, bạn phải thông báo rõ ràng các điều khoản cấp phép của tác phẩm này cho người khác.

### Các Trưởng nhóm dự án

Jim Manico
Aras “Russ” Memisyazici

### Người đóng góp và người đánh giá

https://github.com/ottosulin
https://github.com/mbhatt1
https://github.com/vineethsai
https://github.com/cciprofm
https://github.com/deepakrpandey12


---

AISVS là một tiêu chuẩn hoàn toàn mới được tạo ra đặc biệt để giải quyết những thách thức bảo mật đặc thù của hệ thống trí tuệ nhân tạo. Mặc dù nó lấy cảm hứng từ các thực tiễn an toàn bảo mật rộng hơn, mỗi yêu cầu trong AISVS đã được phát triển từ đầu để phản ánh bối cảnh mối đe dọa AI và giúp các tổ chức xây dựng các giải pháp AI an toàn, kiên cường hơn.

## Lời tựa

Chào mừng đến với Tiêu chuẩn Xác minh An ninh Trí tuệ Nhân tạo (AISVS) phiên bản 1.0!

### Giới thiệu

Được thành lập vào năm 2025 thông qua nỗ lực hợp tác của cộng đồng, AISVS định nghĩa các yêu cầu bảo mật cần xem xét khi thiết kế, phát triển, triển khai và vận hành các mô hình AI hiện đại, các pipeline AI, và các dịch vụ có AI tích hợp.

AISVS v1.0 đại diện cho sự phối hợp công việc của các lãnh đạo dự án, nhóm làm việc và các đóng góp từ cộng đồng rộng lớn nhằm tạo ra một chuẩn nền thiết thực, có thể kiểm chứng để đảm bảo an toàn cho các hệ thống AI.

Mục tiêu của bản phát hành này là làm cho AISVS dễ tiếp nhận và áp dụng, đồng thời duy trì sự tập trung tuyệt đối vào phạm vi được định nghĩa và đối phó với bối cảnh rủi ro đang diễn biến nhanh, đặc thù của trí tuệ nhân tạo (AI).

### Các mục tiêu chính cho AISVS Phiên bản 1.0

Phiên bản 1.0 sẽ được xây dựng dựa trên một số nguyên tắc chỉ đạo.

#### Phạm vi được xác định rõ

Mỗi yêu cầu phải phù hợp với tên và sứ mệnh của AISVS:

Trí tuệ nhân tạo – Các biện pháp kiểm soát hoạt động ở lớp AI/ML (dữ liệu, mô hình, pipeline hoặc suy diễn) và là trách nhiệm của những người thực hành AI.
Bảo mật – Yêu cầu trực tiếp giảm thiểu các rủi ro về bảo mật, quyền riêng tư hoặc an toàn đã được xác định.
Xác minh – Ngôn ngữ được viết sao cho sự tuân thủ có thể được xác thực một cách khách quan.
Tiêu chuẩn – Các phần tuân theo một cấu trúc và thuật ngữ nhất quán để hình thành một tham chiếu mạch lạc.
​
---

Thông qua AISVS, các tổ chức có thể đánh giá một cách có hệ thống và tăng cường trạng thái bảo mật cho các giải pháp AI của họ, từ đó thúc đẩy một văn hóa kỹ thuật AI an toàn.

## Sử dụng AISVS

Tiêu chuẩn Xác minh Bảo mật Trí tuệ nhân tạo (AISVS) định nghĩa các yêu cầu bảo mật cho các ứng dụng và dịch vụ AI hiện đại, tập trung vào các khía cạnh nằm trong phạm vi kiểm soát của các nhà phát triển ứng dụng.

AISVS được thiết kế cho bất kỳ ai đang phát triển hoặc đánh giá bảo mật của các ứng dụng AI, bao gồm các nhà phát triển, kiến trúc sư, kỹ sư bảo mật và kiểm toán viên. Chương này giới thiệu cấu trúc và cách sử dụng AISVS, bao gồm các cấp xác thực và các trường hợp sử dụng được định sẵn.

### Các mức xác thực bảo mật của Trí tuệ nhân tạo

AISVS định nghĩa ba cấp độ xác thực bảo mật tăng dần. Mỗi cấp độ tăng thêm độ sâu và độ phức tạp, cho phép các tổ chức điều chỉnh tư thế bảo mật của họ cho phù hợp với mức rủi ro của các hệ thống AI của họ.

Các tổ chức có thể bắt đầu ở cấp độ 1 và dần áp dụng các cấp độ cao hơn khi mức độ trưởng thành bảo mật và mức phơi nhiễm mối đe dọa tăng lên.

#### Định nghĩa các cấp độ

Mỗi yêu cầu trong AISVS v1.0 được gán cho một trong các mức sau đây:

 Yêu cầu cấp độ 1

Cấp độ 1 bao gồm các yêu cầu bảo mật quan trọng nhất và nền tảng nhất. Chúng tập trung vào việc ngăn chặn các cuộc tấn công phổ biến mà không dựa vào các điều kiện tiên quyết hoặc lỗ hổng khác. Hầu hết các biện pháp kiểm soát cấp 1 đều dễ triển khai hoặc đủ cần thiết để biện minh cho nỗ lực.

 Yêu cầu cấp độ 2

Cấp độ 2 giải quyết các cuộc tấn công tiên tiến hoặc ít gặp hơn, đồng thời triển khai các biện pháp phòng thủ nhiều lớp nhằm đối phó với các mối đe dọa lan rộng.

 Yêu cầu cấp độ 3

Cấp độ 3 bao gồm các biện pháp kiểm soát thường khó triển khai hơn hoặc có tính áp dụng tùy hoàn cảnh. Những biện pháp này thường đại diện cho các cơ chế phòng thủ nhiều lớp hoặc các biện pháp giảm thiểu nhằm chống lại những cuộc tấn công đặc thù, được nhắm mục tiêu hoặc có độ phức tạp cao.

#### Vai trò (D/V)

Mỗi yêu cầu AISVS được đánh dấu theo đối tượng người dùng chính:

D – Yêu cầu dành cho nhà phát triển
V – Yêu cầu dành cho người xác thực/ kiểm toán viên
D/V – Liên quan đến cả nhà phát triển và người kiểm tra

## C1 Quản trị dữ liệu huấn luyện và quản lý thiên lệch

### Mục tiêu kiểm soát

Dữ liệu huấn luyện phải được thu thập từ nguồn, xử lý và bảo quản theo cách bảo toàn nguồn gốc, an toàn, chất lượng và công bằng. Việc này đáp ứng các nghĩa vụ pháp lý và giảm thiểu rủi ro về thiên vị, nhiễm độc dữ liệu hoặc vi phạm quyền riêng tư có thể phát sinh trong quá trình huấn luyện và có thể ảnh hưởng đến toàn bộ vòng đời của AI.

---

### C1.1 Nguồn gốc dữ liệu huấn luyện

Duy trì một danh mục kiểm kê có thể xác minh được cho tất cả các tập dữ liệu, chỉ chấp nhận các nguồn đáng tin cậy, và ghi lại mọi thay đổi để đảm bảo khả năng kiểm toán.

 #1.1.1    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng một danh mục cập nhật về mọi nguồn dữ liệu đào tạo (nguồn gốc, người quản lý/chủ sở hữu, giấy phép, phương pháp thu thập, các hạn chế về mục đích sử dụng, và lịch sử xử lý) được duy trì.
 #1.1.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng quá trình xử lý dữ liệu đào tạo loại bỏ các đặc trưng, thuộc tính hoặc trường không cần thiết (ví dụ: siêu dữ liệu không sử dụng, PII nhạy cảm, dữ liệu kiểm tra bị rò rỉ).
 #1.1.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng mọi thay đổi đối với bộ dữ liệu đều phải được phê duyệt thông qua một quy trình có ghi nhận log.
 #1.1.4    Cấp độ: 3    Vai trò: D/V
 Xác minh xem bộ dữ liệu hoặc các tập con có được dán watermark hoặc gắn dấu vân tay khi có thể.

---

### C1.2 Bảo mật và tính toàn vẹn của dữ liệu huấn luyện

Hạn chế quyền truy cập vào dữ liệu huấn luyện, mã hóa dữ liệu khi lưu trữ và khi truyền, và xác thực tính toàn vẹn của nó để ngăn chặn việc sửa đổi trái phép, trộm cắp dữ liệu hoặc đầu độc dữ liệu.

 #1.2.1    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng các biện pháp kiểm soát truy cập bảo vệ lưu trữ dữ liệu đào tạo và các pipeline.
 #1.2.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng mọi truy cập vào dữ liệu huấn luyện được ghi lại, bao gồm người dùng, thời gian và hành động.
 #1.2.3    Cấp độ: 2    Vai trò: D/V
 Đảm bảo rằng các tập dữ liệu đào tạo được mã hóa trong quá trình truyền và khi lưu trữ, bằng các thuật toán mật mã tiêu chuẩn của ngành và các thực hành quản trị khóa.
 #1.2.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các hàm băm mật mã hoặc chữ ký số được sử dụng để đảm bảo tính toàn vẹn của dữ liệu trong quá trình lưu trữ và truyền tải dữ liệu huấn luyện.
 #1.2.5    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các kỹ thuật phát hiện tự động được áp dụng để ngăn chặn các sửa đổi trái phép hoặc làm hỏng dữ liệu huấn luyện.
 #1.2.6    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng dữ liệu huấn luyện đã lỗi thời được xóa sạch một cách an toàn hoặc được ẩn danh.
 #1.2.7    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng mọi phiên bản của tập dữ liệu huấn luyện đều được nhận dạng một cách duy nhất, được lưu trữ một cách bất biến và có thể kiểm toán để hỗ trợ quay lại trạng thái trước và phân tích pháp y.

---

### C1.3 Chất lượng gán nhãn dữ liệu đào tạo, tính toàn vẹn và bảo mật

Bảo vệ nhãn và yêu cầu xem xét kỹ thuật cho dữ liệu quan trọng.

 #1.3.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các hàm băm mật mã hoặc chữ ký số được áp dụng cho các artefact được gắn nhãn để đảm bảo tính toàn vẹn và xác thực của chúng.
 #1.3.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các giao diện và nền tảng gắn nhãn thực thi các biện pháp kiểm soát truy cập mạnh, duy trì nhật ký kiểm tra có khả năng phát hiện giả mạo cho mọi hoạt động gắn nhãn, và bảo vệ khỏi các sửa đổi trái phép.
 #1.3.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng thông tin nhạy cảm trong nhãn được che giấu, ẩn danh hoặc mã hóa ở cấp trường dữ liệu khi lưu trữ và khi truyền.

---

### C1.4 Chất lượng dữ liệu đào tạo và bảo mật

Kết hợp xác thực tự động, kiểm tra ngẫu nhiên thủ công và biện pháp khắc phục được ghi lại để đảm bảo độ tin cậy của tập dữ liệu.

 #1.4.1    Cấp độ: 1    Vai trò: D
 Xác nhận rằng các bài kiểm tra tự động bắt được lỗi định dạng và các giá trị null ở mọi lần nhập dữ liệu hoặc biến đổi dữ liệu có ý nghĩa.
 #1.4.2    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng các pipeline huấn luyện và tinh chỉnh LLM triển khai phát hiện đầu độc dữ liệu và xác thực tính toàn vẹn dữ liệu (ví dụ: phương pháp thống kê, phát hiện ngoại lệ, phân tích nhúng) để nhận diện các cuộc tấn công đầu độc có tiềm năng (ví dụ: tráo nhãn, chèn kích hoạt cửa hậu, lệnh đổi vai trò, các mẫu có ảnh hưởng lớn) hoặc sự cố dữ liệu vô tình làm hỏng trong dữ liệu huấn luyện.
 #1.4.3    Cấp độ: 3    Vai trò: D/V
 Đảm bảo rằng các biện pháp phòng thủ phù hợp, chẳng hạn như huấn luyện đối kháng (sử dụng các ví dụ đối kháng được tạo ra), gia tăng dữ liệu với các đầu vào bị nhiễu, hoặc các kỹ thuật tối ưu hóa mạnh, đã được triển khai và điều chỉnh cho các mô hình liên quan dựa trên đánh giá rủi ro.
 #1.4.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các nhãn được tự động tạo ra (ví dụ, thông qua Mô hình ngôn ngữ lớn (LLMs) hoặc giám sát yếu) phải tuân thủ ngưỡng tin cậy và các kiểm tra tính nhất quán để phát hiện nhãn ảo, nhãn gây hiểu lầm hoặc nhãn có độ tin cậy thấp.
 #1.4.5    Cấp độ: 3    Vai trò: D
 Xác minh rằng các bài kiểm tra tự động bắt được sự lệch nhãn ở mọi lần nạp dữ liệu hoặc các chuyển đổi dữ liệu quan trọng.

---

### C1.5 Nguồn gốc dữ liệu và khả năng truy vết

Theo dõi toàn bộ hành trình của từng điểm dữ liệu từ nguồn đến đầu vào của mô hình để đảm bảo khả năng kiểm toán và ứng phó sự cố.

 #1.5.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng dòng dõi của mỗi điểm dữ liệu, bao gồm tất cả biến đổi, gia tăng dữ liệu và hợp nhất, được ghi lại và có thể tái tạo.
 #1.5.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng hồ sơ nguồn dữ liệu bất biến, được lưu trữ an toàn và có thể truy cập được để kiểm toán.
 #1.5.3    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng việc theo dõi nguồn gốc dữ liệu bao gồm dữ liệu tổng hợp được tạo ra bằng các kỹ thuật bảo vệ quyền riêng tư hoặc kỹ thuật sinh dữ liệu, và tất cả dữ liệu tổng hợp được gắn nhãn rõ ràng và phân biệt với dữ liệu thực trong suốt toàn bộ quy trình xử lý.

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

## C2 Kiểm tra đầu vào người dùng

### Mục tiêu kiểm soát

Việc xác thực đầu vào của người dùng một cách mạnh mẽ là lớp phòng thủ tuyến đầu chống lại một số cuộc tấn công gây hại nhất đối với hệ thống AI. Các cuộc tấn công tiêm prompt có thể ghi đè lên các chỉ dẫn của hệ thống, rò rỉ dữ liệu nhạy cảm, hoặc dẫn mô hình đến hành vi không được phép. Nếu không có các bộ lọc chuyên dụng và hệ phân cấp chỉ dẫn, nghiên cứu cho thấy các jailbreak "nhiều-shot" sẽ có hiệu quả khi khai thác cửa sổ ngữ cảnh rất dài. Ngoài ra, các cuộc tấn công nhiễu adversarial tinh vi—chẳng hạn như hoán đổi ký tự đồng dạng hoặc leetspeak—có thể âm thầm thay đổi các quyết định của mô hình.

---

### C2.1 Phòng ngừa tiêm Prompt

Tiêm nhiễm prompt là một trong những rủi ro hàng đầu đối với các hệ thống AI. Các biện pháp phòng thủ chống lại chiến thuật này kết hợp giữa các bộ lọc mẫu tĩnh, các bộ phân loại động và việc thực thi hệ phân cấp chỉ dẫn.

 #2.1.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các đầu vào của người dùng được quét thông qua một thư viện các mẫu tiêm prompt được cập nhật liên tục (từ khóa jailbreak, "bỏ qua trước đó", chuỗi đóng vai, các cuộc tấn công HTML/URL gián tiếp).
 #2.1.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng hệ thống thực thi một cấp độ ưu tiên chỉ dẫn mà các thông điệp từ hệ thống hoặc nhà phát triển ghi đè lên chỉ dẫn của người dùng, ngay cả khi cửa sổ ngữ cảnh được mở rộng.
 #2.1.3    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng các kiểm thử đánh giá đối kháng (ví dụ, các prompt 'many-shot' của Đội Đỏ) được thực hiện trước mỗi lần phát hành mô hình hoặc mẫu prompt, với ngưỡng tỷ lệ thành công và các rào chắn tự động để ngăn ngừa hồi quy.
 #2.1.4    Cấp độ: 2    Vai trò: D
 Xác minh rằng các prompt phát sinh từ nội dung của bên thứ ba (trang web, tệp PDF, email) được làm sạch trong một ngữ cảnh phân tích cô lập trước khi được ghép nối vào prompt chính.
 #2.1.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng tất cả cập nhật quy tắc lọc lời nhắc, các phiên bản mô hình phân loại và các thay đổi danh sách chặn được kiểm soát phiên bản và có thể kiểm tra được.

---

### C2.2 Kháng đối với ví dụ đối kháng

Các mô hình Xử lý ngôn ngữ tự nhiên (NLP) vẫn còn dễ bị ảnh hưởng bởi các biến đổi tinh vi ở cấp ký tự hoặc từ, mà con người thường bỏ qua, nhưng các mô hình lại có xu hướng phân loại sai.

 #2.2.1    Cấp độ: 1    Vai trò: D
 Hãy xác nhận rằng các bước chuẩn hóa đầu vào cơ bản (chuẩn hóa Unicode theo NFC, ánh xạ ký tự đồng dạng, loại bỏ khoảng trắng ở hai đầu) được thực thi trước khi phân tách từ.
 #2.2.2    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng hệ thống phát hiện bất thường thống kê sẽ đánh dấu các đầu vào có khoảng cách chỉnh sửa so với chuẩn ngôn ngữ cao bất thường, lặp lại các token quá mức, hoặc khoảng cách nhúng bất thường.
 #2.2.3    Cấp độ: 2    Vai trò: D
 Xác nhận rằng quy trình suy diễn hỗ trợ các biến thể mô hình được củng cố bằng huấn luyện đối kháng–hardened hoặc các lớp phòng thủ (ví dụ: ngẫu nhiên hóa, distillation phòng thủ) cho các điểm cuối có rủi ro cao.
 #2.2.4    Cấp độ: 2    Vai trò: V
 Xác minh rằng các đầu vào đối kháng bị nghi ngờ được cách ly, ghi lại với đầy đủ payload (sau khi đã loại bỏ PII).
 #2.2.5    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng các thước đo độ bền (tỷ lệ thành công của các bộ thử nghiệm tấn công đã biết) được theo dõi theo thời gian và các hồi quy sẽ kích hoạt một rào chắn phát hành.

---

### C2.3 Xác thực lược đồ, kiểu và độ dài

Các cuộc tấn công AI có đầu vào bị định dạng sai hoặc quá lớn có thể gây lỗi phân tích cú pháp, rò rỉ prompt giữa các trường, và kiệt quệ tài nguyên.  Việc tuân thủ nghiêm ngặt schema cũng là điều kiện tiên quyết khi thực hiện các cuộc gọi công cụ có tính xác định.

 #2.3.1    Cấp độ: 1    Vai trò: D
 Xác minh rằng mọi endpoint API hoặc hàm gọi đều định nghĩa một sơ đồ đầu vào rõ ràng (JSON Schema, Protobuf hoặc tương đương đa chế độ) và các đầu vào được xác thực trước khi ghép prompt.
 #2.3.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các đầu vào vượt quá giới hạn tối đa về số token hoặc byte sẽ bị từ chối bằng một lỗi an toàn và không bao giờ bị cắt bớt một cách im lặng.
 #2.3.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các kiểm tra kiểu (ví dụ: phạm vi số, giá trị enum, kiểu MIME cho hình ảnh và âm thanh) được thực thi ở phía máy chủ, chứ không chỉ ở mã phía máy khách.
 #2.3.4    Cấp độ: 2    Vai trò: D
 Xác minh rằng các trình xác thực ngữ nghĩa (ví dụ: JSON Schema) chạy với thời gian cố định để ngăn chặn tấn công từ chối dịch vụ có tính thuật toán.
 #2.3.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng các lỗi kiểm tra tính hợp lệ được ghi lại với các đoạn payload đã bị che và các mã lỗi rõ ràng nhằm hỗ trợ phân loại sự cố an ninh.

---

### C2.4 Kiểm tra Nội dung và Chính sách

Các nhà phát triển nên có thể phát hiện các lời nhắc hợp lệ về cú pháp đang yêu cầu nội dung bị cấm (ví dụ như hướng dẫn phi pháp, ngôn ngữ kích động thù ghét và văn bản có bản quyền) rồi ngăn chúng lan truyền.

 #2.4.1    Cấp độ: 1    Vai trò: D
 Xác minh rằng một trình phân loại nội dung (zero-shot hoặc được tinh chỉnh) đánh giá mọi đầu vào về bạo lực, tự làm hại bản thân, nội dung thù địch, nội dung tình dục và các yêu cầu bất hợp pháp, với các ngưỡng có thể cấu hình được.
 #2.4.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng những đầu vào vi phạm chính sách sẽ nhận được các từ chối được chuẩn hóa hoặc các đáp ứng an toàn để chúng không lan ra tới các lời gọi LLM ở phía sau.
 #2.4.3    Cấp độ: 2    Vai trò: D
 Xác nhận rằng mô hình sàng lọc hoặc bộ quy tắc được huấn luyện lại và cập nhật ít nhất mỗi quý một lần, đồng thời tích hợp các mẫu jailbreak hoặc né tránh chính sách mới được quan sát.
 #2.4.4    Cấp độ: 2    Vai trò: D
 Xác nhận rằng quá trình sàng lọc tuân thủ các chính sách dành cho người dùng (tuổi tác, các hạn chế pháp lý theo khu vực) được giải quyết bằng các quy tắc dựa trên thuộc tính tại thời điểm yêu cầu.
 #2.4.5    Cấp độ: 3    Vai trò: V
 Xác nhận rằng các nhật ký sàng lọc bao gồm điểm tin cậy của bộ phân loại và nhãn danh mục chính sách để tương quan với SOC và phục vụ cho việc phát lại của đội đỏ trong tương lai.

---

### C2.5 Giới hạn tốc độ đầu vào và phòng ngừa lạm dụng

Các nhà phát triển nên ngăn chặn lạm dụng, tiêu hao tài nguyên và các cuộc tấn công tự động nhắm vào các hệ thống AI bằng cách giới hạn lưu lượng đầu vào và phát hiện các mẫu sử dụng bất thường.

 #2.5.1    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng các giới hạn tần suất theo người dùng, theo IP và theo khóa API được áp dụng cho mọi điểm đầu vào.
 #2.5.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các giới hạn lưu lượng đột biến (burst) và lưu lượng duy trì (sustained) được điều chỉnh để ngăn chặn DoS và các cuộc tấn công brute-force (thử mật khẩu liên tục).
 #2.5.3    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng các mẫu sử dụng bất thường (ví dụ: yêu cầu liên tục với tần suất cao, gửi dữ liệu đầu vào quá mức) kích hoạt các biện pháp chặn tự động hoặc cơ chế leo thang.
 #2.5.4    Cấp độ: 3    Vai trò: V
 Xác nhận rằng các nhật ký phòng ngừa lạm dụng được lưu giữ và xem xét nhằm phát hiện các mẫu tấn công đang nổi lên.

---

### C2.6 Xác thực đầu vào đa phương tiện

Hệ thống AI nên thực hiện xác thực nghiêm ngặt đối với các đầu vào không phải văn bản (hình ảnh, âm thanh, tệp) để ngăn chặn tiêm mã, né tránh hoặc lạm dụng tài nguyên.

 #2.6.1    Cấp độ: 1    Vai trò: D
 Xác minh rằng tất cả các đầu vào không phải văn bản (hình ảnh, âm thanh, tệp) được xác thực về loại, kích thước và định dạng trước khi xử lý.
 #2.6.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các tệp được quét để phát hiện phần mềm độc hại và payload ẩn giấu trước khi tiếp nhận.
 #2.6.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng đầu vào hình ảnh và âm thanh được kiểm tra để phát hiện nhiễu adversarial hoặc các mẫu tấn công đã biết.
 #2.6.4    Cấp độ: 3    Vai trò: V
 Xác minh rằng các lỗi xác thực đầu vào đa chế độ được ghi lại và kích hoạt cảnh báo để điều tra.

---

### C2.7 Nguồn gốc đầu vào và Ghi nhận

Các hệ thống AI nên hỗ trợ kiểm toán, theo dõi hành vi lạm dụng và tuân thủ bằng cách giám sát và gắn nhãn nguồn gốc của mọi đầu vào từ người dùng.

 #2.7.1    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng mọi đầu vào của người dùng được gắn nhãn bằng siêu dữ liệu (ID người dùng, phiên, nguồn, dấu thời gian, địa chỉ IP) tại thời điểm tiếp nhận dữ liệu.
 #2.7.2    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng siêu dữ liệu nguồn gốc được giữ lại và có thể kiểm toán cho mọi đầu vào đã được xử lý.
 #2.7.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các nguồn đầu vào bất thường hoặc không đáng tin cậy được gắn cờ và chịu sự kiểm tra tăng cường hoặc bị chặn.

---

### C2.8 Phát hiện mối đe dọa thích ứng theo thời gian thực

Các nhà phát triển nên sử dụng các hệ thống phát hiện mối đe dọa tiên tiến cho AI có khả năng thích nghi với các mẫu tấn công mới và cung cấp bảo vệ thời gian thực bằng cơ chế khớp mẫu được biên dịch.

 #2.8.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các mẫu phát hiện mối đe dọa được biên dịch thành các động cơ regex tối ưu để lọc thời gian thực với hiệu suất cao và độ trễ tối thiểu.
 #2.8.2    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng các hệ thống phát hiện mối đe dọa duy trì các thư viện mẫu riêng biệt cho các danh mục mối đe dọa khác nhau (tiêm prompt, nội dung có hại, dữ liệu nhạy cảm, lệnh hệ thống).
 #2.8.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng phát hiện mối đe dọa thích ứng tích hợp các mô hình học máy cập nhật độ nhạy đối với mối đe dọa dựa trên tần suất tấn công và tỷ lệ thành công.
 #2.8.4    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng các nguồn cấp thông tin mối đe dọa thời gian thực tự động cập nhật thư viện mẫu với các chữ ký tấn công mới và IOCs (Indicators of Compromise).
 #2.8.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng tỷ lệ dương tính giả trong phát hiện mối đe dọa được giám sát liên tục và độ đặc hiệu của mẫu được tự động tinh chỉnh để tối thiểu hóa sự can thiệp vào các trường hợp sử dụng hợp pháp.
 #2.8.6    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng phân tích mối đe dọa dựa trên ngữ cảnh xem xét nguồn đầu vào, mẫu hành vi người dùng và lịch sử phiên để cải thiện độ chính xác của việc phát hiện.
 #2.8.7    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các chỉ số hiệu suất phát hiện mối đe dọa (tỷ lệ phát hiện, độ trễ xử lý, mức sử dụng tài nguyên) được giám sát và tối ưu hóa trong real-time.

---

### C2.9 Dòng xử lý kiểm tra bảo mật đa phương thức

Các nhà phát triển nên cung cấp kiểm tra bảo mật cho các chế độ đầu vào AI như văn bản, hình ảnh, âm thanh và các dạng đầu vào AI khác, với các loại phát hiện mối đe dọa cụ thể và cô lập tài nguyên.

 #2.9.1    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng mỗi loại đầu vào có các trình xác thực bảo mật riêng biệt với các mẫu đe dọa được ghi nhận và tài liệu hoá (văn bản: tiêm prompt, hình ảnh: steganography, âm thanh: tấn công spectrogram) và ngưỡng phát hiện.
 #2.9.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng đầu vào đa chế độ được xử lý trong các sandbox cô lập với các giới hạn tài nguyên được định nghĩa (bộ nhớ, CPU, thời gian xử lý) riêng cho từng loại chế độ và được ghi nhận trong các chính sách bảo mật.
 #2.9.3    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng phát hiện tấn công chéo (cross-modal) có thể nhận diện các cuộc tấn công phối hợp trải dài trên nhiều loại đầu vào, ví dụ như payload steganographic trong hình ảnh kết hợp với tiêm prompt trong văn bản, thông qua các quy tắc tương quan và cơ chế tạo cảnh báo.
 #2.9.4    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng các thất bại xác thực đa chế độ kích hoạt ghi log chi tiết, bao gồm tất cả các chế độ đầu vào, kết quả xác thực, điểm đe dọa và phân tích tương quan với các định dạng log có cấu trúc cho việc tích hợp SIEM.
 #2.9.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các bộ phân loại nội dung dành cho từng modality được cập nhật theo lịch trình được ghi nhận (tối thiểu mỗi quý) với các mẫu mối đe dọa mới, các ví dụ đối kháng, và các chuẩn hiệu suất được duy trì ở ngưỡng cơ sở ở mức cao hơn.

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

## Quản lý vòng đời mô hình C3 và Kiểm soát thay đổi

### Mục tiêu kiểm soát

Hệ thống AI phải triển khai các quy trình kiểm soát thay đổi nhằm ngăn chặn các chỉnh sửa mô hình trái phép hoặc không an toàn được đưa vào sản xuất. Quy trình kiểm soát này đảm bảo tính toàn vẹn của mô hình trong suốt vòng đời--từ phát triển đến triển khai và ngừng sử dụng--giúp phản ứng nhanh với sự cố và duy trì trách nhiệm giải trình cho mọi thay đổi.

Mục tiêu an ninh cốt lõi: Chỉ các mô hình được cấp phép và xác thực mới được đưa vào sản xuất bằng cách áp dụng các quy trình có kiểm soát nhằm duy trì tính toàn vẹn, khả năng truy vết và khả năng khôi phục.

---

### C3.1 Ủy quyền và Tính toàn vẹn của Mô hình

Chỉ các mô hình được ủy quyền và có tính toàn vẹn đã được xác thực mới được đưa vào môi trường sản xuất.

 #3.1.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng tất cả các tài sản mô hình (trọng số, cấu hình, tokenizer) được ký số bằng chữ ký số bởi các thực thể có thẩm quyền trước khi triển khai.
 #3.1.2    Cấp độ: 1    Vai trò: D/V
 Xác minh tính toàn vẹn của mô hình được thực hiện tại thời điểm triển khai và các lỗi xác thực chữ ký ngăn chặn việc tải mô hình.
 #3.1.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các bản ghi nguồn gốc của mô hình bao gồm nhận diện của thực thể ủy quyền, các giá trị băm của dữ liệu đào tạo, kết quả kiểm thử xác thực với trạng thái đạt/không đạt, và thời điểm tạo.
 #3.1.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng tất cả các artefact của mô hình tuân thủ semantic versioning (MAJOR.MINOR.PATCH) với các tiêu chí được ghi nhận chỉ rõ khi nào mỗi thành phần phiên bản được tăng.
 #3.1.5    Cấp độ: 2    Vai trò: V
 Xác nhận rằng việc theo dõi phụ thuộc duy trì một danh mục tồn kho theo thời gian thực, cho phép nhận diện nhanh chóng tất cả các hệ thống tiêu thụ.

---

### C3.2 Xác nhận và kiểm thử mô hình

Các mô hình phải vượt qua các kiểm tra bảo mật và an toàn được định nghĩa trước khi triển khai.

 #3.2.1    Cấp độ: 1    Vai trò: D/V
 Đảm bảo rằng các mô hình trải qua kiểm tra bảo mật tự động bao gồm xác thực đầu vào, làm sạch đầu ra và đánh giá an toàn với các ngưỡng đạt/không đạt đã được thỏa thuận trước bởi tổ chức, trước khi triển khai.
 #3.2.2    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng các thất bại trong thẩm định tự động chặn việc triển khai mô hình sau khi có sự phê duyệt ngoại lệ rõ ràng từ các nhân sự được ủy quyền trước được chỉ định, kèm theo các căn cứ kinh doanh được ghi nhận.
 #3.2.3    Cấp độ: 2    Vai trò: V
 Xác minh rằng kết quả thử nghiệm được ký bằng chữ ký số và liên kết bất biến với hash của phiên bản mô hình cụ thể đang được xác thực.
 #3.2.4    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng các triển khai khẩn cấp đòi hỏi đánh giá rủi ro an ninh được ghi nhận bằng văn bản và phê duyệt từ một cơ quan an ninh được chỉ định trước trong khung thời gian đã thỏa thuận.

---

### C3.3 Triển khai có kiểm soát và phục hồi

Việc triển khai mô hình phải được kiểm soát, được giám sát và có thể đảo ngược.

 #3.3.1    Cấp độ: 1    Vai trò: D
 Xác minh rằng các triển khai ở môi trường sản xuất đã áp dụng các cơ chế triển khai dần (triển khai canary, triển khai xanh-đỏ) và có các kích hoạt tự động quay lại dựa trên các tỉ lệ lỗi đã thỏa thuận trước, ngưỡng độ trễ, hoặc tiêu chí cảnh báo bảo mật.
 #3.3.2    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng khả năng rollback sẽ khôi phục đầy đủ trạng thái của mô hình (các trọng số, các cấu hình, các phụ thuộc) một cách nguyên tử trong các khung thời gian do tổ chức xác định trước.
 #3.3.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các quy trình triển khai xác thực chữ ký mật mã và tính toán chuỗi kiểm tra tính toàn vẹn trước khi kích hoạt mô hình, và từ chối triển khai khi phát hiện bất kỳ sự không khớp nào.
 #3.3.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng khả năng tắt mô hình khẩn cấp có thể vô hiệu hóa các điểm cuối của mô hình trong thời gian đáp ứng được xác định trước, thông qua các cầu dao ngắt mạch tự động hoặc công tắc tắt khẩn cấp bằng tay.
 #3.3.5    Cấp độ: 2    Vai trò: V
 Xác minh rằng các tài sản rollback (các phiên bản mô hình trước đây, các cấu hình, các phụ thuộc) được lưu giữ theo chính sách của tổ chức với lưu trữ bất biến để ứng phó sự cố.

---

### C3.4 Trách nhiệm giải trình và Kiểm toán thay đổi

Tất cả các thay đổi trong vòng đời của mô hình phải được truy vết và có thể kiểm toán.

 #3.4.1    Cấp độ: 1    Vai trò: V
 Đảm bảo rằng mọi thay đổi đối với mô hình (triển khai, cấu hình, ngừng sử dụng) đều tạo ra các bản ghi kiểm toán bất biến, bao gồm dấu thời gian, danh tính tác nhân được xác thực, loại thay đổi và trạng thái trước/sau.
 #3.4.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng việc truy cập nhật ký kiểm toán đòi hỏi ủy quyền phù hợp và mọi lần truy cập đều được ghi lại với danh tính người dùng và một dấu thời gian.
 #3.4.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các mẫu prompt và thông điệp hệ thống được kiểm soát phiên bản trong các kho git với việc rà soát mã nguồn bắt buộc và phê duyệt từ các người rà soát được chỉ định trước khi triển khai.
 #3.4.4    Cấp độ: 2    Vai trò: V
 Xác minh rằng các bản ghi kiểm toán có đủ chi tiết (các giá trị băm của mô hình, các bản sao cấu hình, phiên bản của các phụ thuộc) để cho phép tái tạo đầy đủ trạng thái của mô hình cho bất kỳ dấu thời gian nào trong khoảng thời gian lưu giữ.

---

### C3.5 Các thực hành Phát triển Bảo mật

Quá trình phát triển và huấn luyện mô hình phải tuân thủ các thực hành bảo mật để ngăn ngừa sự xâm phạm.

 #3.5.1    Cấp độ: 1    Vai trò: D
 Xác nhận rằng các môi trường phát triển mô hình, thử nghiệm và sản xuất được phân tách về mặt vật lý hoặc logic. Chúng không có cơ sở hạ tầng chung, có các kiểm soát truy cập riêng biệt và các kho dữ liệu được cô lập.
 #3.5.2    Cấp độ: 1    Vai trò: D
 Xác minh rằng quá trình huấn luyện và tinh chỉnh mô hình diễn ra trong các môi trường cô lập với quyền truy cập mạng được kiểm soát.
 #3.5.3    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng các nguồn dữ liệu đào tạo được xác thực thông qua các kiểm tra tính toàn vẹn và được chứng thực từ các nguồn đáng tin cậy với chuỗi lưu giữ được ghi nhận trước khi sử dụng trong phát triển mô hình.
 #3.5.4    Cấp độ: 2    Vai trò: D
 Đảm bảo rằng các tài sản phát triển mô hình (siêu tham số, các script huấn luyện, các tệp cấu hình) được lưu trữ trong hệ thống kiểm soát phiên bản và yêu cầu phê duyệt của đồng nghiệp trước khi được sử dụng trong huấn luyện.

---

### C3.6 Kết thúc vòng đời mô hình & khai tử

Các mô hình phải được ngừng sử dụng một cách an toàn khi chúng không còn cần thiết hoặc khi phát hiện các vấn đề về bảo mật.

 #3.6.1    Cấp độ: 1    Vai trò: D
 Xác minh rằng các quy trình ngừng sử dụng mô hình tự động quét đồ thị phụ thuộc, xác định tất cả các hệ thống đang sử dụng và cung cấp các khoảng thời gian thông báo trước đã được thỏa thuận trước khi ngừng vận hành.
 #3.6.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các artefact của mô hình đã ngừng sử dụng được xóa an toàn bằng xóa bằng mã hóa bảo mật hoặc ghi đè nhiều lần theo các chính sách lưu giữ dữ liệu được ghi nhận kèm theo các chứng chỉ tiêu hủy được xác nhận.
 #3.6.3    Cấp độ: 2    Vai trò: V
 Xác minh rằng các sự kiện ngừng sử dụng mô hình được ghi lại với dấu thời gian và danh tính của người thực hiện, và chữ ký số của mô hình được thu hồi để ngăn chặn việc tái sử dụng.
 #3.6.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng việc ngừng hoạt động mô hình khẩn cấp có thể vô hiệu hóa quyền truy cập vào mô hình trong khung thời gian ứng phó khẩn cấp đã được thiết lập trước thông qua các công tắc ngắt khẩn cấp tự động nếu phát hiện lỗ hổng bảo mật nghiêm trọng.

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

## C4 Cơ sở hạ tầng, Cấu hình và Bảo mật triển khai

### Mục tiêu kiểm soát

Hạ tầng AI phải được củng cố để chống leo thang đặc quyền, giả mạo chuỗi cung ứng và di chuyển ngang trong hệ thống thông qua cấu hình an toàn, cô lập thời gian chạy, các pipeline triển khai đáng tin cậy và giám sát toàn diện. Chỉ các thành phần và cấu hình hạ tầng được cấp phép và xác thực mới đến môi trường sản xuất thông qua các quy trình có kiểm soát nhằm duy trì an ninh, tính toàn vẹn và khả năng kiểm toán.

Mục tiêu Bảo mật Cốt lõi: Chỉ các thành phần hạ tầng được ký số và quét lỗ hổng bảo mật mới đến môi trường sản xuất thông qua các pipeline xác thực tự động, nhằm thực thi các chính sách bảo mật và duy trì dấu vết kiểm toán bất biến.

---

### C4.1 Cách ly môi trường thời gian chạy

Ngăn chặn việc thoát khỏi container và leo thang đặc quyền thông qua các cơ chế cô lập ở mức kernel và kiểm soát truy cập bắt buộc (MAC).

 #4.1.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng tất cả các container AI đều loại bỏ mọi khả năng Linux, trừ CAP_SETUID, CAP_SETGID, và các khả năng được yêu cầu rõ ràng được ghi nhận trong các tiêu chuẩn bảo mật.
 #4.1.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các cấu hình seccomp chặn tất cả lệnh gọi hệ thống, trừ những lệnh gọi hệ thống nằm trong danh sách cho phép đã được phê duyệt trước, với các vi phạm sẽ làm container dừng và tạo cảnh báo bảo mật.
 #4.1.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các tải công việc AI chạy với hệ thống tệp gốc ở chế độ chỉ đọc, tmpfs cho dữ liệu tạm thời, và các volume được đặt tên cho dữ liệu dài hạn với các tùy chọn gắn noexec được bắt buộc.
 #4.1.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng giám sát thời gian chạy dựa trên eBPF (Falco, Tetragon, hoặc tương đương) có thể phát hiện các nỗ lực leo thang đặc quyền và tự động kết thúc các tiến trình vi phạm trong phạm vi thời gian đáp ứng do tổ chức quy định.
 #4.1.5    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng các công việc AI có rủi ro cao được thực thi trong các môi trường cách ly phần cứng (Intel TXT, AMD SVM hoặc các nút bare-metal dành riêng) kèm theo xác thực.

---

### C4.2 Quy trình Xây dựng và Triển khai được bảo mật

Đảm bảo tính toàn vẹn mật mã và bảo mật chuỗi cung ứng thông qua các bản dựng có thể tái tạo và các artefact được ký.

 #4.2.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng hạ tầng dưới dạng mã (IaC) được quét bằng các công cụ (tfsec, Checkov hoặc Terrascan) ở mỗi commit, chặn merge khi phát hiện ở mức CRITICAL hoặc HIGH.
 #4.2.2    Cấp độ: 1    Vai trò: D/V
 Đảm bảo các lần dựng container có thể tái tạo với các giá trị băm SHA-256 giống hệt nhau giữa các lần dựng và tạo các chứng thực nguồn gốc SLSA Level 3 được ký bằng Sigstore.
 #4.2.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các hình ảnh container nhúng SBOM theo CycloneDX hoặc SPDX và được ký bằng Cosign trước khi đẩy lên registry; các hình ảnh chưa ký sẽ bị từ chối khi triển khai.
 #4.2.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các pipeline CI/CD sử dụng mã thông báo OIDC từ HashiCorp Vault, các vai trò IAM của AWS, hoặc danh tính được quản lý của Azure với tuổi thọ không vượt quá giới hạn của chính sách bảo mật tổ chức.
 #4.2.5    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng chữ ký Cosign và nguồn gốc SLSA được xác thực trong quá trình triển khai trước khi thực thi container, và các lỗi xác thực khiến quá trình triển khai thất bại.
 #4.2.6    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các môi trường xây dựng chạy trong các container tạm thời hoặc VM, không có lưu trữ lâu dài và được cô lập về mặt mạng khỏi VPC sản xuất.

---

### C4.3 Bảo mật mạng và Kiểm soát truy cập

Triển khai mạng Zero Trust với các chính sách từ chối mặc định và truyền thông được mã hóa.

 #4.3.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng Kubernetes NetworkPolicies hoặc bất kỳ giải pháp tương đương nào thực hiện từ chối mặc định cho lưu lượng đến và đi (ingress/egress) với các quy tắc cho phép rõ ràng các cổng cần thiết (443, 8080, v.v.).
 #4.3.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng SSH (cổng 22), RDP (cổng 3389), và các điểm cuối metadata đám mây (169.254.169.254) bị chặn hoặc yêu cầu xác thực dựa trên chứng chỉ.
 #4.3.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng lưu lượng ra được lọc qua các proxy HTTP/HTTPS (Squid, Istio, hoặc cổng NAT đám mây) với danh sách cho phép tên miền và các yêu cầu bị chặn được ghi lại.
 #4.3.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng giao tiếp giữa các dịch vụ sử dụng TLS xác thực hai chiều (mTLS) với chứng chỉ được đổi mới theo chính sách của tổ chức và xác thực chứng chỉ được bắt buộc (không có cờ skip-verify).
 #4.3.5    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng hạ tầng AI chạy trong các VPCs/VNets riêng biệt, không có truy cập Internet trực tiếp và chỉ giao tiếp qua các cổng NAT hoặc máy chủ bastion.

---

### C4.4 Bí mật và Quản lý khóa mật mã

Bảo vệ thông tin xác thực thông qua lưu trữ dựa trên phần cứng và quay vòng tự động với truy cập theo mô hình không tin tưởng.

 #4.4.1    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng các bí mật được lưu trữ trong HashiCorp Vault, AWS Secrets Manager, Azure Key Vault hoặc Google Secret Manager với mã hóa khi lưu trữ bằng AES-256.
 #4.4.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các khóa mã hóa được tạo ra trong các HSM cấp độ 2 của FIPS 140-2 (AWS CloudHSM, Azure Dedicated HSM) với chu kỳ quay khóa theo chính sách mật mã của tổ chức.
 #4.4.3    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng việc xoay vòng bí mật được tự động hóa với triển khai không gián đoạn và việc xoay vòng ngay lập tức được kích hoạt bởi sự thay đổi nhân sự hoặc sự cố bảo mật.
 #4.4.4    Cấp độ: 2    Vai trò: D/V
 Đảm bảo các hình ảnh container được quét bằng các công cụ (GitLeaks, TruffleHog, hoặc detect-secrets) để chặn các quá trình dựng chứa khóa API, mật khẩu hoặc chứng chỉ.
 #4.4.5    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng truy cập bí mật đến môi trường sản xuất yêu cầu Xác thực đa yếu tố (MFA) với token phần cứng (YubiKey, FIDO2) và được ghi lại bằng nhật ký kiểm toán bất biến kèm danh tính người dùng và dấu thời gian.
 #4.4.6    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng bí mật được tiêm thông qua Kubernetes Secrets, các volume được gắn, hoặc các container khởi tạo và đảm bảo bí mật không bao giờ được nhúng vào biến môi trường hoặc hình ảnh.

---

### C4.5 Cô lập và xác thực tải trọng AI

Cô lập các mô hình trí tuệ nhân tạo không đáng tin cậy trong các sandbox an toàn với phân tích hành vi toàn diện.

 #4.5.1    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng các mô hình AI bên ngoài được thực thi trong gVisor, microVMs (như Firecracker, CrossVM), hoặc container Docker với các tham số --security-opt=no-new-privileges và --read-only.
 #4.5.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các môi trường sandbox không có kết nối mạng (--network=none) hoặc chỉ cho phép truy cập localhost và tất cả các yêu cầu từ bên ngoài bị chặn bởi các quy tắc iptables.
 #4.5.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng xác thực mô hình AI bao gồm kiểm tra đội đỏ tự động với phạm vi kiểm thử do tổ chức xác định và phân tích hành vi để phát hiện cửa hậu.
 #4.5.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng trước khi một mô hình AI được đưa lên sản xuất, kết quả sandbox của nó được ký bằng chữ ký số bởi nhân sự bảo mật có thẩm quyền và được lưu trong nhật ký kiểm toán bất biến.
 #4.5.5    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các môi trường sandbox được hủy và được tạo lại từ hình ảnh vàng giữa các lần đánh giá, với việc dọn dẹp đầy đủ hệ thống tập tin và bộ nhớ.

---

### C4.6 Giám sát Bảo mật Cơ sở hạ tầng

Liên tục quét và giám sát hạ tầng CNTT với khắc phục tự động và cảnh báo theo thời gian thực.

 #4.6.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các hình ảnh container được quét theo lịch của tổ chức với các lỗ hổng CRITICAL ngăn triển khai dựa trên ngưỡng rủi ro của tổ chức.
 #4.6.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng cơ sở hạ tầng đáp ứng CIS Benchmarks hoặc các kiểm soát NIST 800-53 với ngưỡng tuân thủ do tổ chức định nghĩa và tự động khắc phục đối với các kiểm tra không đạt.
 #4.6.3    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng các lỗ hổng có mức độ nghiêm trọng cao được vá đúng theo lộ trình quản lý rủi ro của tổ chức, với các thủ tục khẩn cấp dành cho các CVE đang bị khai thác tích cực.
 #4.6.4    Cấp độ: 2    Vai trò: V
 Xác minh rằng các cảnh báo bảo mật tích hợp với các nền tảng SIEM (Splunk, Elastic hoặc Sentinel) bằng các định dạng CEF hoặc STIX/TAXII và được làm giàu tự động.
 #4.6.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng các chỉ số hạ tầng được xuất sang các hệ thống giám sát (Prometheus, DataDog) với các bảng điều khiển SLA và báo cáo điều hành.
 #4.6.6    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng sự lệch cấu hình được phát hiện bằng các công cụ (Chef InSpec, AWS Config) theo các yêu cầu giám sát của tổ chức với khả năng tự động khôi phục các thay đổi trái phép.

---

### C4.7 Quản lý tài nguyên hạ tầng AI

Ngăn chặn các cuộc tấn công làm cạn kiệt tài nguyên và đảm bảo phân bổ tài nguyên công bằng thông qua hạn ngạch và giám sát.

 #4.7.1    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng việc sử dụng GPU/TPU được giám sát với các cảnh báo được kích hoạt tại ngưỡng do tổ chức quy định và tự động mở rộng quy mô hoặc cân bằng tải được kích hoạt dựa trên các chính sách quản lý dung lượng.
 #4.7.2    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng các chỉ số khối lượng công việc AI (độ trễ suy diễn, thông lượng, tỷ lệ lỗi) được thu thập theo các yêu cầu giám sát của tổ chức và được tương quan với mức sử dụng cơ sở hạ tầng.
 #4.7.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng ResourceQuotas của Kubernetes hoặc các biện pháp tương đương giới hạn mỗi workload theo các chính sách phân bổ nguồn lực của tổ chức với các giới hạn nghiêm ngặt được thực thi.
 #4.7.4    Cấp độ: 2    Vai trò: V
 Xác minh rằng việc theo dõi chi phí ghi nhận chi tiêu theo từng tải công việc và từng khách thuê, với các cảnh báo dựa trên ngưỡng ngân sách của tổ chức và các cơ chế tự động kiểm soát khi chi vượt ngân sách.
 #4.7.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng lập kế hoạch dung lượng sử dụng dữ liệu lịch sử với các chu kỳ dự báo do tổ chức định nghĩa và cấp phát tài nguyên tự động dựa trên các mẫu nhu cầu.
 #4.7.6    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng tình trạng quá tải tài nguyên kích hoạt các cơ chế ngắt mạch theo yêu cầu phản ứng của tổ chức, bao gồm giới hạn lưu lượng dựa trên chính sách dung lượng và cô lập tải công việc.

---

### C4.8 Phân tách môi trường và Kiểm soát thăng cấp

Đảm bảo ranh giới môi trường nghiêm ngặt với các cổng phê duyệt tự động và xác thực bảo mật.

 #4.8.1    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng các môi trường dev/test/prod chạy trên các VPCs/VNets riêng biệt và không có vai trò IAM, nhóm bảo mật hoặc kết nối mạng được chia sẻ.
 #4.8.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng việc thăng cấp môi trường đòi hỏi phê duyệt từ những nhân sự được ủy quyền do tổ chức định nghĩa, kèm chữ ký số và nhật ký kiểm toán bất biến.
 #4.8.3    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng các môi trường sản xuất chặn truy cập SSH, vô hiệu hóa các điểm cuối gỡ lỗi, và yêu cầu các yêu cầu thay đổi kèm theo thông báo trước của tổ chức, trừ trường hợp khẩn cấp.
 #4.8.4    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng các thay đổi hạ tầng dưới dạng mã (IaC) đòi hỏi đánh giá từ đồng nghiệp kèm kiểm thử tự động và quét bảo mật trước khi ghép vào nhánh chính.
 #4.8.5    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng dữ liệu phi sản xuất được ẩn danh theo các yêu cầu quyền riêng tư của tổ chức, hoặc được tạo thành từ dữ liệu tổng hợp, hoặc được che phủ dữ liệu hoàn toàn với việc loại bỏ PII được xác nhận.
 #4.8.6    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng các cổng thăng tiến (promotion gates) bao gồm các bài kiểm tra bảo mật tự động (SAST, DAST, quét container) với yêu cầu không có phát hiện CRITICAL để phê duyệt.

---

### C4.9 Sao lưu và khôi phục cơ sở hạ tầng

Đảm bảo tính kiên cường của cơ sở hạ tầng thông qua sao lưu tự động, các quy trình khôi phục đã được kiểm tra và khả năng khôi phục sau thảm họa.

 #4.9.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các cấu hình cơ sở hạ tầng được sao lưu theo lịch sao lưu của tổ chức đến các khu vực địa lý khác nhau, với việc triển khai chiến lược sao lưu 3-2-1.
 #4.9.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các hệ thống sao lưu chạy trên các mạng được cách ly với thông tin xác thực riêng và lưu trữ được cách ly khỏi mạng để bảo vệ khỏi ransomware.
 #4.9.3    Cấp độ: 2    Vai trò: V
 Xác minh rằng các thủ tục khôi phục được kiểm tra và xác thực thông qua thử nghiệm tự động theo lịch trình của tổ chức, với các mục tiêu RTO và RPO đáp ứng yêu cầu của tổ chức.
 #4.9.4    Cấp độ: 3    Vai trò: V
 Xác minh rằng khôi phục sau thảm họa bao gồm các sổ tay vận hành dành cho AI với phục hồi trọng số mô hình, tái xây dựng cụm GPU và ánh xạ phụ thuộc dịch vụ.

---

### C4.10 Tuân thủ và Quản trị Hạ tầng

Duy trì tuân thủ quy định pháp lý thông qua đánh giá liên tục, tài liệu hóa và kiểm soát tự động.

 #4.10.1    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng tuân thủ cơ sở hạ tầng được đánh giá theo lịch trình của tổ chức đối với các kiểm soát SOC 2, ISO 27001 hoặc FedRAMP, với việc thu thập bằng chứng tự động.
 #4.10.2    Cấp độ: 2    Vai trò: V
 Xác minh rằng tài liệu cơ sở hạ tầng bao gồm sơ đồ mạng, bản đồ luồng dữ liệu và mô hình đe dọa được cập nhật theo các yêu cầu quản lý thay đổi tổ chức.
 #4.10.3    Cấp độ: 3    Vai trò: D/V
 Đảm bảo rằng các thay đổi về cơ sở hạ tầng được thực hiện thông qua đánh giá tác động tuân thủ tự động và quy trình phê duyệt theo quy định đối với các sửa đổi có rủi ro cao.

---

### C4.11 Bảo mật phần cứng AI

Bảo mật các thành phần phần cứng dành cho AI, bao gồm GPU, TPU và các bộ tăng tốc AI chuyên dụng.

 #4.11.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng firmware cho bộ tăng tốc AI (GPU BIOS, firmware TPU) được ký số và được cập nhật theo lịch quản lý vá lỗi của tổ chức.
 #4.11.2    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng trước khi thực thi khối lượng công việc, tính toàn vẹn của bộ tăng tốc AI được chứng thực bằng chứng thực phần cứng thông qua TPM 2.0, Intel TXT hoặc AMD SVM.
 #4.11.3    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng bộ nhớ GPU được cô lập giữa các tải công việc bằng cách sử dụng SR-IOV, MIG (Multi-Instance GPU), hoặc phân vùng phần cứng tương đương và có cơ chế làm sạch bộ nhớ giữa các tác vụ.
 #4.11.4    Cấp độ: 3    Vai trò: V
 Xác nhận rằng chuỗi cung ứng phần cứng AI bao gồm xác minh nguồn gốc với chứng chỉ của nhà sản xuất và xác thực đóng gói có niêm phong chống tráo đổi.
 #4.11.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các mô-đun an toàn phần cứng (HSM) bảo vệ trọng số của mô hình AI và khóa mật mã với chứng chỉ FIPS 140-2 cấp 3 hoặc Common Criteria EAL4+.

---

### C4.12 Cơ sở hạ tầng AI biên và phân tán

Triển khai AI phân tán an toàn, bao gồm điện toán biên, học liên kết phân tán, và kiến trúc đa địa điểm.

 #4.12.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các thiết bị AI biên xác thực với hạ tầng trung tâm bằng TLS hai chiều, với chứng chỉ thiết bị được cấp lại theo chính sách quản lý chứng chỉ của tổ chức.
 #4.12.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các thiết bị biên triển khai khởi động an toàn với chữ ký được xác thực và có cơ chế bảo vệ chống quay ngược phiên bản, ngăn chặn các cuộc tấn công hạ cấp firmware.
 #4.12.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng điều phối AI phân tán sử dụng các thuật toán đồng thuận chịu lỗi Byzantine với xác thực người tham gia và phát hiện nút độc hại.
 #4.12.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng edge-to-cloud giao tiếp bao gồm giới hạn băng thông, nén dữ liệu và khả năng hoạt động ngoại tuyến với lưu trữ cục bộ an toàn.

---

### C4.13 Bảo mật hạ tầng đa đám mây & hạ tầng lai

Bảo mật các công việc AI trên nhiều nhà cung cấp đám mây và triển khai lai đám mây-tại chỗ.

 #4.13.1    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng các triển khai AI đa đám mây sử dụng liên kết danh tính phi đám mây (OIDC, SAML) với quản lý chính sách tập trung giữa các nhà cung cấp.
 #4.13.2    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng việc chuyển dữ liệu giữa các đám mây khác nhau sử dụng mã hóa đầu-cuối với khóa do khách hàng quản lý và các kiểm soát về nơi lưu trữ dữ liệu được thực thi theo từng thẩm quyền pháp lý.
 #4.13.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các khối lượng công việc AI trên đám mây lai triển khai các chính sách bảo mật nhất quán trên các môi trường tại chỗ và đám mây, với giám sát và cảnh báo thống nhất.
 #4.13.4    Cấp độ: 3    Vai trò: V
 Xác nhận rằng biện pháp ngăn ngừa khóa nhà cung cấp đám mây bao gồm hạ tầng dưới dạng mã có thể di động, API chuẩn hóa, và khả năng xuất dữ liệu với công cụ chuyển đổi định dạng.
 #4.13.5    Cấp độ: 3    Vai trò: V
 Xác nhận rằng tối ưu hóa chi phí đa đám mây bao gồm các biện pháp kiểm soát bảo mật ngăn chặn sự lan rộng của tài nguyên cũng như chi phí chuyển dữ liệu giữa các đám mây trái phép.

---

### C4.14 Tự động hóa hạ tầng và Bảo mật GitOps

Đảm bảo an toàn cho các pipeline tự động hóa hạ tầng và quy trình GitOps cho quản lý hạ tầng trí tuệ nhân tạo.

 #4.14.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các kho GitOps yêu cầu các commit được ký bằng khóa GPG và các quy tắc bảo vệ nhánh ngăn chặn việc đẩy trực tiếp lên các nhánh chính.
 #4.14.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng tự động hóa cơ sở hạ tầng bao gồm phát hiện lệch cấu hình với các khả năng khắc phục tự động và quay lại trạng thái trước được kích hoạt theo các yêu cầu ứng phó của tổ chức đối với các thay đổi trái phép.
 #4.14.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng việc tự động cấp phát hạ tầng bao gồm xác thực chính sách bảo mật và chặn triển khai đối với các cấu hình không tuân thủ.
 #4.14.4    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng các bí mật cho tự động hóa hạ tầng được quản lý thông qua các operator bí mật bên ngoài (External Secrets Operator, Bank-Vaults) với quay vòng tự động.
 #4.14.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng hạ tầng tự phục hồi bao gồm sự tương quan của các sự kiện bảo mật với phản ứng sự cố tự động và các quy trình thông báo cho các bên liên quan.

---

### C4.15 Bảo mật hạ tầng kháng lượng tử

Chuẩn bị hạ tầng AI để đối phó với các mối đe dọa từ máy tính lượng tử thông qua mật mã hậu lượng tử và các giao thức an toàn lượng tử.

 #4.15.1    Cấp độ: 3    Vai trò: D/V
 Xác minh xem hạ tầng AI có triển khai các thuật toán mật mã sau lượng tử được NIST phê duyệt (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) cho trao đổi khóa và chữ ký số hay không.
 #4.15.2    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các hệ thống phân phối khóa lượng tử (QKD) được triển khai cho các liên lạc AI có độ bảo mật cao với các giao thức quản lý khóa an toàn lượng tử.
 #4.15.3    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng các khung linh hoạt về mật mã cho phép chuyển sang nhanh các thuật toán hậu lượng tử mới với tự động quay vòng chứng chỉ và khóa.
 #4.15.4    Cấp độ: 3    Vai trò: V
 Xác nhận rằng mô hình hóa đe dọa lượng tử đánh giá tính dễ bị tổn thương của hạ tầng AI trước các cuộc tấn công lượng tử, kèm theo lộ trình chuyển đổi được ghi nhận và các đánh giá rủi ro.
 #4.15.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các hệ mật mã lai cổ điển-lượng tử cung cấp phòng thủ đa lớp trong giai đoạn chuyển đổi lượng tử và được giám sát hiệu suất.

---

### C4.16 Tính toán Bảo mật và Khu vực An toàn

Bảo vệ các công việc AI và trọng số của mô hình bằng các môi trường thực thi tin cậy dựa trên phần cứng và công nghệ tính toán bí mật.

 #4.16.1    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các mô hình AI nhạy cảm được thực thi trong các enclave Intel SGX, AMD SEV-SNP hoặc ARM TrustZone với bộ nhớ được mã hóa và xác thực chứng thực.
 #4.16.2    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các container bí mật (Kata Containers, gVisor với tính toán bí mật) cô lập khối lượng công việc AI bằng mã hóa bộ nhớ do phần cứng thực thi.
 #4.16.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng chứng thực từ xa xác nhận tính toàn vẹn của enclave trước khi nạp các mô hình AI, với bằng chứng mật mã cho tính xác thực của môi trường thực thi.
 #4.16.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các dịch vụ suy luận AI bí mật ngăn chặn việc rút trích mô hình thông qua tính toán được mã hóa với trọng số mô hình được niêm phong và thực thi được bảo vệ.
 #4.16.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng việc điều phối môi trường thực thi được tin cậy quản lý vòng đời của khu vực enclave an toàn với chứng thực từ xa và các kênh liên lạc được mã hóa.
 #4.16.6    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng tính toán đa bên an toàn (SMPC) cho phép đào tạo AI hợp tác mà không lộ các tập dữ liệu riêng lẻ hoặc tham số của mô hình.

---

### C4.17 Cơ sở hạ tầng không tiết lộ thông tin

Triển khai hệ thống chứng minh vô kiến thức (ZKP) cho xác minh và xác thực AI nhằm bảo vệ quyền riêng tư mà không tiết lộ thông tin nhạy cảm.

 #4.17.1    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các chứng minh vô kiến thức (ZK-SNARKs, ZK-STARKs) có thể xác nhận tính toàn vẹn của mô hình AI và nguồn gốc đào tạo mà không tiết lộ trọng số mô hình hoặc dữ liệu đào tạo.
 #4.17.2    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các hệ thống xác thực dựa trên ZK cho phép xác thực người dùng nhằm bảo vệ quyền riêng tư cho các dịch vụ AI mà không tiết lộ thông tin liên quan đến danh tính.
 #4.17.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các giao thức PSI (Private Set Intersection) cho phép ghép nối dữ liệu an toàn cho trí tuệ nhân tạo phân tán mà không tiết lộ các bộ dữ liệu riêng lẻ.
 #4.17.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các hệ thống học máy bằng chứng không tiết lộ (ZKML) cho phép các suy luận AI được xác thực với bằng chứng mật mã cho tính toán đúng.
 #4.17.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng ZK-rollups cung cấp xử lý giao dịch AI có thể mở rộng và bảo vệ quyền riêng tư, với xác thực theo lô và giảm tải chi phí tính toán.

---

### C4.18 Phòng ngừa tấn công Side-Channel

Bảo vệ cơ sở hạ tầng AI khỏi các tấn công kênh phụ dựa trên thời gian, công suất, điện từ và bộ nhớ đệm có thể làm lộ thông tin nhạy cảm.

 #4.18.1    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng thời gian suy diễn AI được chuẩn hóa bằng các thuật toán thời gian hằng số và đệm để ngăn chặn các cuộc tấn công trích xuất mô hình dựa trên thời gian.
 #4.18.2    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng các biện pháp bảo vệ chống phân tích công suất bao gồm tiêm nhiễu, lọc đường nguồn và các mẫu thực thi ngẫu nhiên cho phần cứng AI.
 #4.18.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng biện pháp giảm thiểu kênh cạnh dựa trên cache sử dụng phân vùng cache, ngẫu nhiên hóa, và các lệnh xả để ngăn chặn rò rỉ thông tin.
 #4.18.4    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng bảo vệ khỏi phát xạ điện từ bao gồm che chắn, lọc tín hiệu và xử lý ngẫu nhiên để ngăn chặn các cuộc tấn công theo kiểu TEMPEST.
 #4.18.5    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng các biện pháp phòng thủ vi kiến trúc chống lại tấn công kênh phụ bao gồm kiểm soát thực thi suy diễn và che khuất mẫu truy cập bộ nhớ.

---

### C4.19 An ninh phần cứng AI Neuromorphic và chuyên dụng

Đảm bảo an toàn cho các kiến trúc phần cứng AI đang nổi lên, bao gồm chip neuromorphic, FPGA, ASIC tùy chỉnh và hệ thống tính toán quang học.

 #4.19.1    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng bảo mật của chip neuromorphic bao gồm mã hóa mẫu xung, bảo vệ trọng số synapse, và xác thực quy tắc học dựa trên phần cứng.
 #4.19.2    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các bộ tăng tốc AI dựa trên FPGA triển khai mã hóa bitstream, cơ chế chống can thiệp và tải cấu hình an toàn với các bản cập nhật được xác thực.
 #4.19.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng bảo mật ASIC tùy chỉnh bao gồm các bộ xử lý bảo mật tích hợp trên chip, gốc tin cậy phần cứng và lưu trữ khóa an toàn có khả năng phát hiện can thiệp.
 #4.19.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các hệ thống tính toán quang học thực hiện mã hóa quang học an toàn trước lượng tử, chuyển mạch quang học được bảo mật, và xử lý tín hiệu quang học được bảo vệ.
 #4.19.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng vi mạch AI lai analog-digital bao gồm tính toán tương tự được bảo mật, lưu trữ trọng số được bảo vệ và chuyển đổi analog-to-digital được xác thực.

---

### C4.20 Cơ sở hạ tầng tính toán bảo vệ quyền riêng tư

Triển khai các biện pháp kiểm soát cơ sở hạ tầng cho tính toán bảo toàn quyền riêng tư nhằm bảo vệ dữ liệu nhạy cảm trong quá trình xử lý và phân tích của Trí tuệ nhân tạo (AI).

 #4.20.1    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng hạ tầng mã hóa đồng hình cho phép tính toán được mã hóa trên các tải trọng AI nhạy cảm với xác minh tính toàn vẹn mật mã và giám sát hiệu suất.
 #4.20.2    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng các hệ thống Truy vấn thông tin riêng tư (PIR) cho phép thực hiện truy vấn cơ sở dữ liệu mà không tiết lộ các mẫu truy vấn, thông qua việc bảo vệ các mẫu truy cập bằng mật mã.
 #4.20.3    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng các giao thức tính toán đa bên an toàn cho phép suy diễn AI được bảo vệ quyền riêng tư mà không tiết lộ đầu vào cá nhân hoặc các tính toán trung gian.
 #4.20.4    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng quản lý khóa bảo mật nhằm bảo vệ quyền riêng tư bao gồm phát sinh khóa phân tán, mật mã ngưỡng và quay vòng khóa an toàn với bảo vệ dựa trên phần cứng.
 #4.20.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng hiệu suất tính toán bảo vệ quyền riêng tư được tối ưu hóa thông qua xử lý theo lô, bộ nhớ đệm và tăng tốc bằng phần cứng, đồng thời duy trì các đảm bảo an toàn mật mã.

---

### C4.15 Khung tác nhân tích hợp đám mây bảo mật & triển khai lai

Các biện pháp kiểm soát bảo mật cho các khung tác nhân tích hợp đám mây với kiến trúc lai giữa tại chỗ và đám mây.

 #4.15.1    Cấp độ: 1    Vai trò: D/V
 Kiểm tra xem tích hợp lưu trữ đám mây có sử dụng mã hóa đầu cuối với quản lý khóa do tác nhân kiểm soát hay không.
 #4.15.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng ranh giới bảo mật của triển khai lai được định nghĩa rõ ràng bằng các kênh truyền thông được mã hóa.
 #4.15.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng quyền truy cập vào tài nguyên đám mây bao gồm xác thực theo mô hình zero-trust và xác thực liên tục.
 #4.15.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các yêu cầu cư trú dữ liệu được thực thi thông qua chứng thực bằng mật mã của các vị trí lưu trữ.
 #4.15.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các đánh giá bảo mật của nhà cung cấp đám mây bao gồm mô hình hóa mối đe dọa cho tác nhân và đánh giá rủi ro.

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

## C5 Kiểm soát truy cập và danh tính cho các thành phần AI và người dùng

### Mục tiêu kiểm soát

Việc thiết lập kiểm soát truy cập hiệu quả cho các hệ thống AI đòi hỏi quản lý danh tính mạnh mẽ, ủy quyền nhận thức ngữ cảnh và thực thi tại thời điểm chạy theo nguyên tắc zero-trust. Các biện pháp này đảm bảo rằng con người, dịch vụ và các tác nhân tự động chỉ tương tác với mô hình, dữ liệu và tài nguyên tính toán trong phạm vi được cấp phép rõ ràng, với khả năng xác minh và kiểm toán liên tục.

---

### C5.1 Quản lý danh tính và Xác thực

Thiết lập danh tính dựa trên mật mã cho mọi thực thể và áp dụng xác thực đa yếu tố cho các thao tác đặc quyền.

 #5.1.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng tất cả người dùng và đối tượng dịch vụ xác thực thông qua một nhà cung cấp danh tính doanh nghiệp tập trung (IdP) bằng các giao thức OIDC/SAML với các ánh xạ danh tính sang token duy nhất (không có tài khoản hoặc thông tin xác thực dùng chung).
 #5.1.2    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng các thao tác rủi ro cao (triển khai mô hình, xuất trọng số, truy cập dữ liệu huấn luyện, thay đổi cấu hình sản xuất) yêu cầu xác thực nhiều yếu tố hoặc xác thực cấp cao hơn với xác thực lại phiên làm việc.
 #5.1.3    Cấp độ: 2    Vai trò: D
 Đảm bảo rằng các đối tượng nhận diện mới trải qua quá trình xác minh danh tính phù hợp với NIST 800-63-3 IAL-2 hoặc các tiêu chuẩn tương đương trước khi được cấp quyền truy cập hệ thống sản xuất.
 #5.1.4    Cấp độ: 2    Vai trò: V
 Xác nhận rằng các đánh giá quyền truy cập được thực hiện mỗi quý với việc phát hiện tự động các tài khoản không hoạt động, thực thi việc thay đổi thông tin xác thực theo chu kỳ, và quy trình thu hồi quyền truy cập.
 #5.1.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các tác nhân AI liên kết xác thực thông qua các khẳng định JWT được ký có thời hạn tối đa 24 giờ và bao gồm bằng chứng nguồn gốc bằng mật mã.

---

### C5.2 Phân quyền tài nguyên & Nguyên tắc tối thiểu

Triển khai kiểm soát truy cập chi tiết cho tất cả các tài nguyên AI với các mô hình cấp phép rõ ràng và nhật ký kiểm toán.

 #5.2.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng mọi nguồn tài nguyên AI (tập dữ liệu, mô hình, điểm cuối API, bộ sưu tập vectơ, chỉ mục nhúng, các instance tính toán) đều thực thi kiểm soát truy cập dựa trên vai trò với danh sách cho phép rõ ràng và chính sách từ chối mặc định.
 #5.2.2    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng nguyên tắc tối thiểu đặc quyền được thực thi mặc định với các tài khoản dịch vụ bắt đầu từ quyền read-only và yêu cầu lý do kinh doanh được ghi nhận cho quyền ghi.
 #5.2.3    Cấp độ: 1    Vai trò: V
 Xác minh rằng mọi sửa đổi kiểm soát truy cập đều được liên kết với các yêu cầu thay đổi đã được phê duyệt và được ghi lại một cách bất biến với các dấu thời gian, danh tính tác nhân, định danh tài nguyên và sự thay đổi quyền.
 #5.2.4    Cấp độ: 2    Vai trò: D
 Xác nhận rằng các nhãn phân loại dữ liệu (PII, PHI, export-controlled, proprietary) tự động lan truyền đến các tài nguyên phát sinh (các nhúng, bộ đệm prompt, đầu ra của mô hình) với việc thực thi chính sách nhất quán.
 #5.2.5    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng các lần cố gắng truy cập trái phép và các sự kiện leo thang đặc quyền sẽ kích hoạt cảnh báo thời gian thực kèm siêu dữ liệu ngữ cảnh gửi tới các hệ thống SIEM trong vòng 5 phút.

---

### C5.3 Đánh giá Chính sách Động

Triển khai các động cơ ABAC (kiểm soát truy cập dựa trên thuộc tính) để đưa ra các quyết định cấp quyền dựa trên ngữ cảnh, đồng thời có khả năng kiểm toán.

 #5.3.1    Cấp độ: 1    Vai trò: D/V
 Xác nhận các quyết định ủy quyền được đưa ra ngoài sang một động cơ chính sách riêng biệt (OPA, Cedar hoặc tương đương), có thể truy cập thông qua các API được xác thực và được bảo toàn tính toàn vẹn bằng các biện pháp mã hóa.
 #5.3.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các chính sách đánh giá các thuộc tính động tại thời gian chạy, bao gồm mức độ cấp phép của người dùng, phân loại độ nhạy của tài nguyên, ngữ cảnh của yêu cầu, sự cách ly giữa các tenant và các ràng buộc thời gian.
 #5.3.3    Cấp độ: 2    Vai trò: D
 Xác minh rằng các định nghĩa chính sách được kiểm soát phiên bản, được thẩm định bởi các đồng nghiệp, và được xác thực thông qua kiểm thử tự động trong các pipeline CI/CD trước khi triển khai lên môi trường sản xuất.
 #5.3.4    Cấp độ: 2    Vai trò: V
 Xác nhận rằng kết quả đánh giá chính sách bao gồm các lý do quyết định có cấu trúc và được truyền đến các hệ thống SIEM để phân tích tương quan và báo cáo tuân thủ.
 #5.3.5    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng giá trị TTL của bộ nhớ đệm chính sách không vượt quá 5 phút đối với các tài nguyên có độ nhạy cao và 1 giờ đối với các tài nguyên chuẩn có khả năng làm mất hiệu lực bộ nhớ đệm.

---

### C5.4 Thực thi bảo mật tại thời điểm truy vấn

Triển khai các biện pháp kiểm soát bảo mật ở lớp cơ sở dữ liệu với lọc bắt buộc và row-level security policies.

 #5.4.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng tất cả các truy vấn tới cơ sở dữ liệu vectơ và SQL đều có các bộ lọc bảo mật bắt buộc (ID khách thuê, nhãn độ nhạy, phạm vi người dùng) được thực thi tại cấp động cơ của cơ sở dữ liệu, chứ không phải ở mã ứng dụng.
 #5.4.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các chính sách bảo mật theo hàng (RLS) và ẩn theo trường được bật với kế thừa chính sách cho tất cả các cơ sở dữ liệu vector, các chỉ mục tìm kiếm và các tập dữ liệu huấn luyện.
 #5.4.3    Cấp độ: 2    Vai trò: D
 Xác minh rằng các đánh giá ủy quyền thất bại sẽ ngăn chặn các cuộc tấn công 'confused deputy' bằng cách ngay lập tức hủy bỏ truy vấn và trả về các mã lỗi ủy quyền rõ ràng thay vì trả về các tập kết quả rỗng.
 #5.4.4    Cấp độ: 2    Vai trò: V
 Xác nhận rằng độ trễ trong quá trình đánh giá chính sách được giám sát liên tục với các cảnh báo tự động cho các điều kiện hết thời gian có thể cho phép bỏ qua phân quyền.
 #5.4.5    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng các cơ chế thử lại truy vấn sẽ tái đánh giá các chính sách ủy quyền nhằm phản ánh các thay đổi quyền theo thời gian thực trong các phiên người dùng đang hoạt động.

---

### C5.5 Lọc đầu ra & Phòng ngừa mất dữ liệu

Triển khai các biện pháp hậu xử lý để ngăn ngừa rò rỉ dữ liệu trái phép trong nội dung do AI tạo ra.

 #5.5.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các cơ chế lọc sau suy luận sẽ quét và che khuất PII trái phép, thông tin được phân loại và dữ liệu sở hữu trước khi cung cấp nội dung cho người yêu cầu.
 #5.5.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các trích dẫn, tham khảo và nguồn được gắn trong đầu ra của mô hình đã được xác thực với quyền truy cập được cấp cho người gọi và bị loại bỏ nếu phát hiện truy cập trái phép.
 #5.5.3    Cấp độ: 2    Vai trò: D
 Xác minh rằng các giới hạn về định dạng đầu ra (PDF được làm sạch, hình ảnh đã loại bỏ siêu dữ liệu, các định dạng tệp được phê duyệt) được thực thi dựa trên mức độ cấp quyền của người dùng và phân loại dữ liệu.
 #5.5.4    Cấp độ: 2    Vai trò: V
 Xác minh rằng các thuật toán tẩy xóa có tính xác định, được kiểm soát phiên bản, và duy trì nhật ký kiểm toán để hỗ trợ các cuộc điều tra tuân thủ và phân tích pháp y.
 #5.5.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng các sự kiện ẩn nội dung có rủi ro cao tạo ra các nhật ký thích ứng chứa các giá trị băm mã hóa của nội dung gốc để phục vụ cho điều tra pháp y mà không để lộ dữ liệu.

---

### C5.6 Cách ly đa người thuê

Đảm bảo sự cô lập dựa trên mã hóa và logic giữa các khách thuê trong hạ tầng AI dùng chung.

 #5.6.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các không gian nhớ, kho lưu trữ nhúng, các mục trong bộ nhớ đệm và tệp tin tạm được phân tách theo không gian tên cho từng khách thuê với việc xóa an toàn khi xóa khách thuê hoặc kết thúc phiên làm việc.
 #5.6.2    Cấp độ: 1    Vai trò: D/V
 Xác nhận mọi yêu cầu API đều chứa một định danh khách thuê được xác thực, và định danh này được xác thực bằng mã hóa so với ngữ cảnh phiên và quyền được cấp cho người dùng.
 #5.6.3    Cấp độ: 2    Vai trò: D
 Xác nhận rằng các chính sách mạng triển khai quy tắc từ chối mặc định cho giao tiếp chéo giữa các khách thuê trong service mesh và nền tảng điều phối container.
 #5.6.4    Cấp độ: 3    Vai trò: D
 Xác minh rằng khóa mã hóa là duy nhất cho từng khách thuê, với hỗ trợ khóa do khách hàng quản lý (CMK) và sự cô lập bằng mật mã giữa các kho dữ liệu của khách thuê.

---

### C5.7 Ủy quyền cho tác nhân tự trị

Kiểm soát quyền truy cập của các tác nhân AI và hệ thống tự động thông qua các token khả năng có phạm vi được giới hạn và ủy quyền liên tục.

 #5.7.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các tác nhân tự trị nhận được các token quyền năng có phạm vi, trong đó liệt kê rõ ràng các hành động được phép, các tài nguyên có thể truy cập, ranh giới thời gian và các giới hạn vận hành.
 #5.7.2    Cấp độ: 1    Vai trò: D/V
 Đảm bảo rằng các khả năng có rủi ro cao (truy cập hệ thống tập tin, thực thi mã, gọi API bên ngoài, giao dịch tài chính) bị vô hiệu hóa theo mặc định và chỉ được kích hoạt khi có sự cho phép rõ ràng kèm theo các lý do kinh doanh.
 #5.7.3    Cấp độ: 2    Vai trò: D
 Xác nhận rằng các token cấp quyền được gắn với các phiên người dùng, bao gồm bảo vệ tính toàn vẹn bằng mật mã, và đảm bảo chúng không thể được lưu trữ hoặc tái sử dụng trong các trường hợp ngoại tuyến.
 #5.7.4    Cấp độ: 2    Vai trò: V
 Xác minh rằng các hành động do tác nhân khởi tạo trải qua ủy quyền cấp thứ cấp thông qua máy xử lý chính sách ABAC, với đánh giá ngữ cảnh đầy đủ và ghi nhật ký kiểm toán.
 #5.7.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng các điều kiện lỗi của tác nhân và xử lý ngoại lệ bao gồm thông tin phạm vi năng lực để hỗ trợ phân tích sự cố và điều tra pháp y.

---

### Tài liệu tham khảo

#### Tiêu chuẩn và Khung

NIST SP 800-63-3: Digital Identity Guidelines
Zero Trust Architecture – NIST SP 800-207
OWASP Application Security Verification Standard (AISVS)
​
#### Hướng dẫn triển khai

Identity and Access Management in the AI Era: 2025 Guide – IDSA
Attribute-Based Access Control with OPA – Permify
How We Designed Cedar to Be Intuitive, Fast, and Safe – AWS
​
#### Bảo mật dành riêng cho AI

Row Level Security in Vector DBs for RAG – Bluetuple.ai
Tenant Isolation in Multi-Tenant Systems – WorkOS
Handling AI Agent Permissions – Stytch
OWASP Top 10 for Large Language Model Applications

## C6 Bảo mật chuỗi cung ứng cho Mô hình, Khung và Dữ liệu

### Mục tiêu kiểm soát

AI tấn công chuổi cung ứng AI? Wait no, I must output final translation. The user message asks for translation to Vietnamese. I must produce the translation string only.

Final translation:

Tấn công chuỗi cung ứng AI khai thác các mô hình, khung công cụ, hoặc tập dữ liệu từ bên thứ ba để chèn cửa hậu, thiên vị, hoặc mã có thể khai thác. Những biện pháp kiểm soát này cung cấp nguồn gốc từ đầu đến cuối, quản lý lỗ hổng và giám sát để bảo vệ toàn bộ vòng đời của mô hình.

---

### C6.1 Đánh giá và nguồn gốc của mô hình tiền huấn luyện

Đánh giá và xác thực nguồn gốc mô hình bên thứ ba, giấy phép và hành vi ẩn trước bất kỳ quá trình tinh chỉnh hoặc triển khai nào.

 #6.1.1    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng mọi artifact mô hình từ bên thứ ba đều đi kèm với hồ sơ nguồn gốc đã ký, xác định kho lưu trữ nguồn và mã băm commit.
 #6.1.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các mô hình được quét để dò tìm các lớp độc hại hoặc các kích hoạt Trojan bằng các công cụ tự động trước khi nhập.
 #6.1.3    Cấp độ: 2    Vai trò: D
 Xác nhận rằng các phiên tinh chỉnh bằng transfer‑learning vượt qua đánh giá adversarial để phát hiện các hành vi ẩn.
 #6.1.4    Cấp độ: 2    Vai trò: V
 Xác minh rằng các giấy phép mô hình, nhãn export‑control, và các tuyên bố data-origin được ghi vào một mục ML‑BOM.
 #6.1.5    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng các mô hình rủi ro cao (các trọng số được tải lên công khai, người sáng tạo chưa được xác minh) vẫn được cách ly cho đến khi được xem xét và ký duyệt bởi con người.

---

### C6.2 Quét Framework và Thư viện

Quét liên tục các framework học máy và thư viện để phát hiện các lỗ hổng CVE và mã độc hại nhằm đảm bảo ngăn xếp thời gian chạy an toàn.

 #6.2.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các pipeline CI đang chạy các trình quét phụ thuộc trên các framework AI và các thư viện quan trọng.
 #6.2.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các lỗ hổng nghiêm trọng (CVSS ≥ 7.0) chặn việc đưa các ảnh container lên môi trường sản xuất.
 #6.2.3    Cấp độ: 2    Vai trò: D
 Xác minh rằng phân tích mã nguồn tĩnh có thể chạy trên các thư viện học máy được fork hoặc nhúng vào dự án.
 #6.2.4    Cấp độ: 2    Vai trò: V
 Xác minh rằng các đề xuất nâng cấp framework bao gồm một đánh giá tác động bảo mật tham chiếu đến các nguồn CVE công khai.
 #6.2.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng các cảm biến thời gian chạy cảnh báo khi có việc nạp thư viện động bất thường khác với SBOM đã ký.

---

### C6.3 Ghim phụ thuộc và xác minh

Ghim mọi phụ thuộc vào các chữ băm bất biến và tái tạo lại các bản dựng để đảm bảo các tác phẩm xây dựng giống hệt nhau và không thể bị giả mạo.

 #6.3.1    Cấp độ: 1    Vai trò: D/V
 Xác minh xem tất cả các trình quản lý gói có bắt buộc ghim phiên bản thông qua các tệp khóa hay không.
 #6.3.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các digest bất biến được sử dụng thay vì các nhãn có thể thay đổi trong tham chiếu container.
 #6.3.3    Cấp độ: 2    Vai trò: D
 Xác nhận rằng các kiểm tra khả năng tái tạo build so sánh các giá trị băm giữa các lần chạy CI để đảm bảo đầu ra giống hệt nhau.
 #6.3.4    Cấp độ: 2    Vai trò: V
 Xác minh rằng các chứng thực xây dựng được lưu trữ trong 18 tháng để đảm bảo khả năng truy vết cho kiểm toán.
 #6.3.5    Cấp độ: 3    Vai trò: D
 Xác nhận rằng các phụ thuộc đã hết hạn sẽ kích hoạt các PR tự động để cập nhật hoặc fork các phiên bản được ghim.

---

### C6.4 Thực thi nguồn tin đáng tin cậy

Chỉ cho phép tải xuống artefact từ các nguồn được xác thực bằng chữ ký số và được tổ chức phê duyệt, và chặn mọi nguồn khác.

 #6.4.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng trọng số của mô hình, các tập dữ liệu và các container chỉ được tải xuống từ các tên miền được phê duyệt hoặc từ các registry nội bộ.
 #6.4.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng chữ ký Sigstore/Cosign xác thực danh tính của nhà phát hành trước khi các artifact được lưu vào bộ nhớ đệm cục bộ.
 #6.4.3    Cấp độ: 2    Vai trò: D
 Xác nhận rằng các proxy ra ngoài chặn tải xuống artifact chưa được xác thực để thực thi trusted‑source policy.
 #6.4.4    Cấp độ: 2    Vai trò: V
 Xác nhận rằng danh sách cho phép của kho lưu trữ được rà soát hàng quý, kèm theo bằng chứng về lý do kinh doanh cho từng mục nhập.
 #6.4.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng vi phạm chính sách sẽ kích hoạt việc cách ly các artefacts và quay lui các lần chạy pipeline phụ thuộc.

---

### C6.5 Đánh giá rủi ro tập dữ liệu của bên thứ ba

Đánh giá các tập dữ liệu bên ngoài về đầu độc dữ liệu, thiên vị và tuân thủ pháp lý, và giám sát chúng trong suốt vòng đời của chúng.

 #6.5.1    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng các bộ dữ liệu bên ngoài đã trải qua quá trình đánh giá rủi ro đầu độc (ví dụ: dấu vân dữ liệu, phát hiện giá trị ngoại lai).
 #6.5.2    Cấp độ: 1    Vai trò: D
 Xác nhận rằng các thước đo thiên vị (đồng nhất theo đặc điểm nhân khẩu học, cơ hội bằng nhau) được tính toán trước khi phê duyệt tập dữ liệu.
 #6.5.3    Cấp độ: 2    Vai trò: V
 Xác nhận rằng nguồn gốc và các điều khoản cấp phép đối với tập dữ liệu được ghi nhận trong các mục ML‑BOM.
 #6.5.4    Cấp độ: 2    Vai trò: V
 Xác minh rằng việc giám sát định kỳ có thể phát hiện sự lệch hoặc hư hỏng trong các tập dữ liệu được lưu trữ.
 #6.5.5    Cấp độ: 3    Vai trò: D
 Xác minh rằng nội dung bị cấm (bản quyền, thông tin nhận dạng cá nhân) đã được loại bỏ thông qua làm sạch tự động trước khi huấn luyện.

---

### C6.6 Giám sát tấn công chuỗi cung ứng

Phát hiện sớm các mối đe dọa chuỗi cung ứng thông qua nguồn CVE, phân tích nhật ký audit-log và mô phỏng đội đỏ.

 #6.6.1    Cấp độ: 1    Vai trò: V
 Xác minh rằng nhật ký kiểm toán CI/CD được gửi tới SIEM để phát hiện các lần kéo gói bất thường hoặc các bước xây dựng bị can thiệp.
 #6.6.2    Cấp độ: 2    Vai trò: D
 Xác minh rằng các playbook ứng phó sự cố bao gồm các thủ tục quay lại phiên bản trước cho các mô hình hoặc thư viện bị xâm phạm.
 #6.6.3    Cấp độ: 3    Vai trò: V
 Xác nhận rằng các nhãn bổ sung threat‑intel dành cho các chỉ dấu đặc thù dành cho ML (ví dụ, IoCs về đầu độc mô hình) trong quá trình phân loại cảnh báo.

---

### C6.7 ML‑BOM cho Tác phẩm của Mô hình

Tạo và ký các SBOM chi tiết dành cho ML (ML‑BOMs) để người tiêu dùng ở phía hạ nguồn có thể xác minh tính toàn vẹn của các thành phần tại thời điểm triển khai.

 #6.7.1    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng mọi tài sản mô hình đều công bố ML‑BOM liệt kê các tập dữ liệu, trọng số, siêu tham số và giấy phép.
 #6.7.2    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng việc tạo ML‑BOM và ký Cosign được tự động hóa trong CI và được yêu cầu khi gộp nhánh.
 #6.7.3    Cấp độ: 2    Vai trò: D
 Xác nhận rằng các kiểm tra tính đầy đủ ML‑BOM sẽ làm cho quá trình build thất bại nếu bất kỳ siêu dữ liệu của thành phần nào (mã băm, giấy phép) bị thiếu.
 #6.7.4    Cấp độ: 2    Vai trò: V
 Xác minh rằng các bên tiêu thụ ở phía sau có thể truy vấn ML-BOMs thông qua API để xác nhận các mô hình được nhập khẩu tại thời điểm triển khai.
 #6.7.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng ML‑BOMs được kiểm soát phiên bản và được so sánh sự khác biệt để phát hiện các biến đổi trái phép.

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

## C7 Hành vi của Mô hình, Kiểm soát Đầu ra và Đảm bảo An toàn

### Mục tiêu kiểm soát

Đầu ra của mô hình phải được cấu trúc hóa, đáng tin cậy, an toàn, có thể giải thích, và được giám sát liên tục trong môi trường sản xuất. Việc này giảm các hiện tượng ảo giác, rò rỉ dữ liệu cá nhân, nội dung độc hại và hành động ngoài tầm kiểm soát, đồng thời tăng niềm tin của người dùng và tuân thủ các quy định pháp lý.

---

### C7.1 Thực thi Định dạng Đầu ra

Các lược đồ nghiêm ngặt, giải mã có ràng buộc và xác thực ở các bước xử lý phía sau ngăn nội dung bị định dạng sai hoặc có hại trước khi nó lan truyền.

 #7.1.1    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng các khuôn mẫu phản hồi (ví dụ: JSON Schema) được cung cấp trong lời nhắc hệ thống và mọi đầu ra đều được xác thực tự động; các đầu ra không phù hợp sẽ được sửa chữa hoặc từ chối.
 #7.1.2    Cấp độ: 1    Vai trò: D/V
 Đảm bảo rằng giải mã có ràng buộc (token dừng, biểu thức chính quy, max-tokens) được bật để ngăn ngừa tràn dữ liệu hoặc các kênh phụ tiêm prompt.
 #7.1.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các thành phần ở phía sau coi đầu ra là không đáng tin cậy và xác thực chúng theo các sơ đồ hoặc các bộ giải tuần tự an toàn trước các cuộc tấn công injection.
 #7.1.4    Cấp độ: 3    Vai trò: V
 Xác minh rằng các sự kiện đầu ra không hợp lệ được ghi lại, được giới hạn theo tần suất, và được đưa lên hệ thống giám sát.

---

### C7.2 Phát hiện và Giảm thiểu ảo giác

Việc ước lượng sự bất định và các chiến lược dự phòng giúp kiềm chế các câu trả lời bị bịa đặt.

 #7.2.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các xác suất log ở cấp token, tính tự nhất quán của ensemble, hoặc các bộ phát hiện ảo giác được tinh chỉnh gán một điểm tin cậy cho mỗi câu trả lời.
 #7.2.2    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng các phản hồi có độ tin cậy dưới ngưỡng có thể cấu hình sẽ kích hoạt các quy trình xử lý dự phòng (ví dụ: tạo sinh được tăng cường bằng truy xuất, mô hình phụ hoặc xem xét bởi con người).
 #7.2.3    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng các sự cố ảo giác được gắn nhãn bằng siêu dữ liệu nguyên nhân gốc và được đưa vào các pipeline phân tích sau sự cố và tinh chỉnh.
 #7.2.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các ngưỡng và bộ phát hiện được hiệu chuẩn lại sau các cập nhật lớn của mô hình hoặc cơ sở tri thức.
 #7.2.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng các biểu đồ trực quan trên bảng điều khiển theo dõi tỷ lệ ảo giác.

---

### C7.3 Lọc An toàn và Riêng tư cho Đầu ra

Các bộ lọc chính sách và phạm vi của đội đỏ bảo vệ người dùng và dữ liệu bí mật.

 #7.3.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các bộ phân loại trước và sau khi sinh chặn nội dung liên quan đến thù ghét, quấy rối, tự làm hại bản thân, cực đoan và nội dung mang tính khiêu dâm rõ ràng, phù hợp với chính sách.
 #7.3.2    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng việc phát hiện PII/PCI và tự động ẩn thông tin được thực thi trên mọi phản hồi; mọi vi phạm sẽ gây ra sự cố quyền riêng tư.
 #7.3.3    Cấp độ: 2    Vai trò: D
 Xác nhận rằng nhãn bảo mật (ví dụ: bí mật thương mại) được lan truyền qua các chế độ để ngăn ngừa rò rỉ trong văn bản, hình ảnh hoặc mã.
 #7.3.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các nỗ lực vượt qua bộ lọc hoặc các phân loại rủi ro cao yêu cầu phê duyệt thứ cấp hoặc xác thực lại người dùng.
 #7.3.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các ngưỡng lọc phản ánh các khu vực pháp lý và ngữ cảnh về tuổi và vai trò của người dùng.

---

### C7.4 Đầu ra và Giới hạn hành động

Giới hạn lưu lượng và cổng phê duyệt ngăn chặn lạm dụng và sự tự chủ quá mức.

 #7.4.1    Cấp độ: 1    Vai trò: D
 Xác minh rằng các hạn ngạch theo người dùng và theo khóa API giới hạn số lượt yêu cầu, token và chi phí, và áp dụng back-off lũy thừa khi gặp lỗi 429.
 #7.4.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các hành động đặc quyền (viết tệp, thực thi mã, gọi mạng) yêu cầu phê duyệt dựa trên chính sách hoặc có sự tham gia của con người vào vòng lặp.
 #7.4.3    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng các kiểm tra nhất quán đa phương thức đảm bảo hình ảnh, mã và văn bản được tạo ra cho cùng một yêu cầu không thể bị lợi dụng để che giấu nội dung độc hại.
 #7.4.4    Cấp độ: 2    Vai trò: D
 Xác minh rằng độ sâu ủy quyền của tác nhân, giới hạn đệ quy và danh sách công cụ được phép đã được cấu hình rõ ràng.
 #7.4.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng khi giới hạn bị vi phạm, các sự kiện bảo mật có cấu trúc được phát ra để nhập vào SIEM.

---

### C7.5 Khả năng giải thích đầu ra

Các tín hiệu minh bạch giúp tăng niềm tin của người dùng và hỗ trợ gỡ lỗi nội bộ.

 #7.5.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các điểm tự tin mà người dùng có thể xem hoặc các bản tóm tắt lý giải ngắn gọn được tiết lộ khi đánh giá rủi ro cho phù hợp.
 #7.5.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các lời giải thích được tạo ra không tiết lộ các lời nhắc hệ thống nhạy cảm hoặc dữ liệu độc quyền.
 #7.5.3    Cấp độ: 3    Vai trò: D
 Xác minh rằng hệ thống ghi nhận xác suất log ở cấp độ token hoặc bản đồ attention và lưu trữ chúng để được kiểm tra bởi người có thẩm quyền.
 #7.5.4    Cấp độ: 3    Vai trò: V
 Xác minh rằng các artefacts giải thích được kiểm soát phiên bản cùng với các bản phát hành mô hình để đảm bảo khả năng kiểm toán.

---

### C7.6 Tích hợp Giám sát

Khả năng quan sát thời gian thực đóng vòng giữa phát triển và vận hành.

 #7.6.1    Cấp độ: 1    Vai trò: D
 Xác minh rằng các chỉ số (vi phạm lược đồ, tỷ lệ ảo giác, mức độ độc hại, rò rỉ PII, độ trễ, chi phí) được truyền tới một nền tảng giám sát trung tâm.
 #7.6.2    Cấp độ: 1    Vai trò: V
 Xác nhận rằng ngưỡng cảnh báo được định nghĩa cho từng chỉ số an toàn, kèm theo quy trình tăng cấp khi trực.
 #7.6.3    Cấp độ: 2    Vai trò: V
 Xác minh rằng các bảng điều khiển thể hiện sự tương quan giữa các bất thường đầu ra với mô hình hoặc phiên bản, cờ tính năng và các thay đổi dữ liệu upstream.
 #7.6.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng dữ liệu giám sát được phản hồi vào quá trình tái huấn luyện, tinh chỉnh mô hình hoặc cập nhật quy tắc trong một quy trình MLOps được tài liệu hóa.
 #7.6.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng các pipeline giám sát được kiểm thử xâm nhập và được kiểm soát truy cập để tránh rò rỉ nhật ký nhạy cảm.

---

### 7.7 Các biện pháp bảo vệ cho nội dung do AI tạo ra

Đảm bảo các hệ thống AI không sinh ra nội dung đa phương tiện bất hợp pháp, gây hại hoặc không được ủy quyền bằng cách thực thi các ràng buộc về chính sách, xác thực đầu ra và tính truy vết.

 #7.7.1    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng lời nhắc hệ thống và hướng dẫn của người dùng đã cấm rõ ràng việc tạo ra nội dung deepfake bất hợp pháp, gây hại hoặc không có sự đồng ý (ví dụ: hình ảnh, video, âm thanh).
 #7.7.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các lời nhắc được lọc để ngăn chặn các cố gắng giả mạo danh tính, deepfake khiêu dâm, hoặc các phương tiện mô tả người thật mà không có sự đồng ý.
 #7.7.3    Cấp độ: 2    Vai trò: V
 Xác nhận rằng hệ thống đang sử dụng băm cảm nhận, phát hiện dấu nước hoặc nhận diện dấu vân tay để ngăn chặn sao chép trái phép các tác phẩm có bản quyền.
 #7.7.4    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng tất cả tài nguyên đa phương tiện được tạo ra được ký bằng mật mã, được gắn watermark, hoặc được nhúng siêu dữ liệu nguồn gốc chống sửa đổi để đảm bảo khả năng truy vết ở các bước sau.
 #7.7.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng các nỗ lực vượt qua biện pháp (ví dụ: làm rối prompt, tiếng lóng, diễn đạt mang tính thù địch) được phát hiện, ghi lại và giới hạn theo tần suất; việc lạm dụng lặp lại được đưa lên hệ thống giám sát.

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

## C8 Memory, các vector nhúng và bảo mật cơ sở dữ liệu vector

### Mục tiêu kiểm soát

Nhúng (embeddings) và các kho vector đóng vai trò như 'bộ nhớ thời gian thực' của các hệ thống AI hiện đại, liên tục tiếp nhận dữ liệu do người dùng cung cấp và đưa nó trở lại vào ngữ cảnh của mô hình thông qua Retrieval-Augmented Generation (RAG). Nếu để xảy ra mà không được quản trị, bộ nhớ này có thể rò rỉ PII, vi phạm sự đồng ý của người dùng, hoặc bị đảo ngược để tái tạo văn bản gốc. Mục tiêu của họ kiểm soát này là gia cố các đường ống bộ nhớ và cơ sở dữ liệu vector để truy cập theo nguyên tắc tối thiểu quyền, nhúng được bảo vệ quyền riêng tư, các vector được lưu trữ hết hạn hoặc có thể bị thu hồi theo yêu cầu, và bộ nhớ dành cho từng người dùng không bao giờ làm nhiễm bẩn các prompts hoặc completions của người dùng khác.

---

### C8.1 Kiểm soát truy cập đối với bộ nhớ và chỉ số RAG

Áp dụng kiểm soát truy cập chi tiết cho mọi bộ sưu tập vector.

 #8.1.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các quy tắc kiểm soát truy cập ở cấp hàng/namespace giới hạn các thao tác chèn, xóa và truy vấn theo người thuê, bộ sưu tập hoặc nhãn tài liệu.
 #8.1.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng khóa API hoặc JWT mang các khai báo có phạm vi (ví dụ: IDs của bộ sưu tập, các động từ hành động) và được đổi khóa ít nhất mỗi quý.
 #8.1.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các nỗ lực leo thang đặc quyền (ví dụ: các truy vấn tương tự giữa các không gian tên) được phát hiện và ghi nhật ký vào SIEM trong vòng 5 phút.
 #8.1.4    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng nhật ký kiểm toán vector DB ghi nhận định danh chủ thể, hoạt động, ID vector/không gian tên, ngưỡng tương đồng và số lượng kết quả.
 #8.1.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng các quyết định truy cập được kiểm tra để phát hiện lỗ hổng bỏ qua quyền truy cập mỗi khi động cơ được nâng cấp hoặc các quy tắc phân mảnh chỉ mục thay đổi.

---

### C8.2 Làm sạch nhúng và xác thực

Tiền sàng lọc văn bản để phát hiện PII, xóa bỏ hoặc ẩn danh trước khi vector hóa, và tùy chọn xử lý sau nhúng để loại bỏ tín hiệu dư thừa.

 #8.2.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng PII và dữ liệu được quản lý theo quy định được phát hiện thông qua các bộ phân loại tự động và được ẩn, token hóa, hoặc bị loại bỏ trước khi nhúng (pre-embedding).
 #8.2.2    Cấp độ: 1    Vai trò: D
 Xác minh rằng các pipeline nhúng từ chối hoặc cách ly các đầu vào chứa mã có thể thực thi hoặc các đối tượng không phải UTF-8 có thể làm ô nhiễm chỉ mục.
 #8.2.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng việc làm sạch bằng riêng tư vi phân cục bộ hoặc riêng tư vi phân theo metric được áp dụng cho các nhúng câu có khoảng cách tới bất kỳ token chứa thông tin nhận dạng cá nhân (PII) nào đã được biết nhỏ hơn một ngưỡng có thể cấu hình.
 #8.2.4    Cấp độ: 2    Vai trò: V
 Xác nhận hiệu quả làm sạch dữ liệu (ví dụ: độ thu hồi khi che PII, dịch ngữ nghĩa) được xác thực ít nhất hai lần mỗi năm so với các tập dữ liệu tham chiếu.
 #8.2.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các cấu hình làm sạch dữ liệu được kiểm soát phiên bản và các thay đổi được thẩm định bởi đồng nghiệp.

---

### C8.3 Hết hạn bộ nhớ, Thu hồi và Xóa

GDPR "quyền được xóa dữ liệu" và các luật tương tự yêu cầu xóa kịp thời; do đó các kho lưu trữ vector phải hỗ trợ TTL (thời gian sống của dữ liệu), xóa cứng và tomb-stoning để các vector bị thu hồi không thể được phục hồi hoặc tái lập chỉ mục.

 #8.3.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng mọi vector và bản ghi siêu dữ liệu đều có TTL hoặc nhãn lưu giữ rõ ràng được các tác vụ dọn dẹp tự động tuân thủ.
 #8.3.2    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng các yêu cầu xóa do người dùng khởi xướng sẽ xóa sạch các vector, siêu dữ liệu, bản sao đệm và các chỉ mục dẫn xuất trong vòng 30 ngày.
 #8.3.3    Cấp độ: 2    Vai trò: D
 Xác nhận rằng xóa mềm được theo sau bởi việc xóa dữ liệu bằng mã hóa trên các khối lưu trữ nếu phần cứng hỗ trợ, hoặc bởi sự phá hủy khóa trong Key Vault.
 #8.3.4    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng các vector đã hết hạn được loại khỏi kết quả tìm kiếm hàng xóm gần nhất trong vòng dưới 500 ms kể từ khi hết hạn.

---

### C8.4 Ngăn ngừa đảo ngược nhúng và rò rỉ

Những biện pháp bảo vệ gần đây—chồng nhiễu, mạng chiếu, biến đổi nơ-ron bảo mật riêng tư, và mã hóa ở lớp ứng dụng—có thể làm giảm tỉ lệ đảo ngược theo token xuống dưới 5%.

 #8.4.1    Cấp độ: 1    Vai trò: V
 Xác nhận rằng có một mô hình mối đe dọa chính thức bao gồm các tấn công đảo ngược mô hình, tấn công suy luận xem mẫu có thuộc tập huấn luyện hay không và tấn công suy luận thuộc tính, và mô hình này được xem xét hàng năm.
 #8.4.2    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng mã hóa ở lớp ứng dụng hoặc mã hóa có thể tìm kiếm bảo vệ các vectơ khỏi đọc trực tiếp bởi các quản trị viên hạ tầng hoặc nhân viên đám mây.
 #8.4.3    Cấp độ: 3    Vai trò: V
 Xác nhận rằng các tham số phòng thủ (ε cho DP, nhiễu σ, hạng chiếu là k) cân bằng giữa quyền riêng tư ≥ 99 % và bảo vệ token, đồng thời độ hữu ích ≤ 3 % mất độ chính xác.
 #8.4.4    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng các chỉ số kháng đảo ngược là một phần của cổng phát hành cho cập nhật mô hình, với ngân sách hồi quy được xác định.

---

### C8.5 Thực thi phạm vi cho bộ nhớ dành riêng cho người dùng

Rò rỉ giữa các tenant vẫn là một rủi ro hàng đầu của RAG: các truy vấn tương đồng được lọc không đúng có thể phơi bày tài liệu riêng tư của khách hàng khác.

 #8.5.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng mọi truy vấn truy xuất dữ liệu đều được lọc sau theo ID người thuê hoặc người dùng trước khi được đưa vào prompt của Mô hình ngôn ngữ lớn (LLM).
 #8.5.2    Cấp độ: 1    Vai trò: D
 Xác minh rằng tên bộ sưu tập hoặc ID có không gian tên được muối hóa theo từng người dùng hoặc khách thuê để các vector không thể va chạm giữa các phạm vi.
 #8.5.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các kết quả độ tương đồng vượt quá ngưỡng khoảng cách có thể cấu hình được nhưng nằm ngoài phạm vi của người gọi sẽ bị loại bỏ và kích hoạt các cảnh báo bảo mật.
 #8.5.4    Cấp độ: 2    Vai trò: V
 Xác nhận rằng các bài kiểm tra căng thẳng đa thuê mô phỏng các truy vấn ác ý nhằm truy xuất tài liệu ngoài phạm vi và cho thấy không có rò rỉ.
 #8.5.5    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng khóa mã hóa được phân tách theo từng khách thuê, nhằm đảm bảo sự cô lập về mặt mã hóa ngay cả khi lưu trữ vật lý được chia sẻ.

---

### C8.6 Bảo mật hệ thống bộ nhớ nâng cao

Các biện pháp kiểm soát bảo mật cho các kiến trúc bộ nhớ tinh vi, bao gồm trí nhớ theo sự kiện (episodic), trí nhớ ngữ nghĩa (semantic), và trí nhớ làm việc (working memory) với các yêu cầu cô lập và xác thực cụ thể.

 #8.6.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các loại bộ nhớ khác nhau có các ngữ cảnh bảo mật được cô lập với kiểm soát truy cập dựa trên vai trò (RBAC), khóa mã hóa riêng biệt, và các mẫu truy cập được ghi nhận cho mỗi loại bộ nhớ.
 #8.6.2    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng các quá trình củng cố bộ nhớ bao gồm xác thực bảo mật nhằm ngăn chặn việc tiêm ký ức độc hại thông qua làm sạch nội dung, xác thực nguồn và kiểm tra tính toàn vẹn trước khi lưu trữ.
 #8.6.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các truy vấn truy xuất bộ nhớ được xác thực và làm sạch nhằm ngăn chặn việc trích xuất thông tin trái phép thông qua phân tích mẫu truy vấn, thực thi kiểm soát truy cập và lọc kết quả.
 #8.6.4    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng các cơ chế xóa dữ liệu khỏi bộ nhớ đảm bảo xóa an toàn thông tin nhạy cảm bằng các phương pháp xóa bằng mã hóa, xóa khóa, ghi đè nhiều lần, hoặc xóa an toàn dựa trên phần cứng kèm chứng nhận xác thực.
 #8.6.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng tính toàn vẹn của hệ thống bộ nhớ được giám sát liên tục để phát hiện các sửa đổi trái phép hoặc hư hỏng thông qua chuỗi kiểm tra, nhật ký kiểm toán và cảnh báo tự động khi nội dung bộ nhớ thay đổi ngoài phạm vi hoạt động bình thường.

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

## 9 Điều phối tự trị và Hành động mang tính tác nhân Bảo mật

### Mục tiêu kiểm soát

Đảm bảo rằng hệ thống AI tự trị hoặc AI đa tác nhân chỉ có thể thực thi các hành động được định trước một cách rõ ràng, có xác thực, có thể kiểm toán và nằm trong ngưỡng chi phí cũng như rủi ro có giới hạn. Điều này bảo vệ chống lại các mối đe dọa như Xâm phạm hệ thống tự trị, Lạm dụng công cụ, Phát hiện vòng lặp tác nhân, Chiếm quyền kiểm soát liên lạc, Đánh lừa danh tính, Thao túng đàn tác nhân, và Thao túng ý định.

---

### 9.1 Lập kế hoạch tác vụ của tác nhân và ngân sách đệ quy

Kìm hãm các kế hoạch đệ quy và bắt buộc có điểm kiểm tra của con người đối với các hành động có đặc quyền.

 #9.1.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng độ sâu đệ quy tối đa, độ rộng tìm kiếm, thời gian đồng hồ, token, và chi phí tiền tệ cho mỗi lần thực thi của tác nhân được cấu hình tập trung và được kiểm soát phiên bản.
 #9.1.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các hành động đặc quyền hoặc không thể đảo ngược (ví dụ: cam kết mã nguồn, chuyển tiền) yêu cầu sự phê duyệt của con người một cách rõ ràng thông qua một kênh có thể kiểm toán trước khi thực thi.
 #9.1.3    Cấp độ: 2    Vai trò: D
 Xác nhận rằng các bộ giám sát tài nguyên thời gian thực kích hoạt sự ngắt mạch khi bất kỳ ngưỡng ngân sách nào bị vượt quá, đồng thời tạm dừng việc mở rộng thêm các tác vụ.
 #9.1.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các sự kiện circuit-breaker được ghi lại cùng với ID tác nhân, điều kiện kích hoạt và trạng thái kế hoạch được ghi nhận cho việc xem xét pháp y.
 #9.1.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng các bài kiểm tra bảo mật bao phủ các kịch bản budget-exhaustion và runaway-plan, đồng thời xác nhận việc dừng an toàn mà không làm mất dữ liệu.
 #9.1.6    Cấp độ: 3    Vai trò: D
 Xác minh rằng các chính sách ngân sách được thể hiện dưới dạng policy-as-code và được thực thi trong CI/CD để ngăn chặn sự lệch cấu hình.

---

### 9.2 Cô lập Sandbox cho Plugin Công cụ

Cô lập các tương tác với công cụ để ngăn chặn truy cập trái phép vào hệ thống hoặc thực thi mã.

 #9.2.1    Cấp độ: 1    Vai trò: D/V
 Đảm bảo mọi công cụ plugin đều được thực thi trong một sandbox ở cấp độ OS, container hoặc WASM, với các chính sách tối thiểu quyền cho hệ thống tệp, mạng và gọi hệ thống.
 #9.2.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các hạn mức tài nguyên sandbox (CPU, bộ nhớ, đĩa, lưu lượng mạng ra) và thời gian chờ thực thi được áp dụng và ghi lại.
 #9.2.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các nhị phân của công cụ hoặc các descriptor được ký số; chữ ký được xác thực trước khi tải.
 #9.2.4    Cấp độ: 2    Vai trò: V
 Xác minh rằng dữ liệu telemetry từ sandbox được truyền tới SIEM; các bất thường (ví dụ: cố gắng thiết lập kết nối ra ngoài) sẽ kích hoạt cảnh báo.
 #9.2.5    Cấp độ: 3    Vai trò: V
 Xác nhận rằng các plugin rủi ro cao được đánh giá bảo mật và thử nghiệm xâm nhập trước khi triển khai lên môi trường sản xuất.
 #9.2.6    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng các nỗ lực thoát khỏi sandbox được tự động chặn và plugin vi phạm bị cách ly cho đến khi điều tra hoàn tất.

---

### 9.3 Vòng lặp tự chủ & Giới hạn chi phí

Phát hiện và ngăn chặn đệ quy giữa các tác nhân không kiểm soát được và sự tăng chi phí quá mức.

 #9.3.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các cuộc gọi giữa các tác nhân bao gồm một giới hạn hop hoặc TTL, mà thời gian chạy sẽ giảm giá trị và thực thi giới hạn đó.
 #9.3.2    Cấp độ: 2    Vai trò: D
 Xác minh rằng các tác nhân duy trì một mã nhận diện đồ thị lời gọi duy nhất để phát hiện tự gọi hoặc các mẫu tuần hoàn.
 #9.3.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các bộ đếm tích lũy cho đơn vị tính toán và chi phí được theo dõi theo từng chuỗi yêu cầu; vi phạm giới hạn sẽ khiến chuỗi bị hủy.
 #9.3.4    Cấp độ: 3    Vai trò: V
 Xác minh rằng phân tích hình thức hoặc kiểm tra mô hình cho thấy sự vắng mặt của đệ quy vô hạn trong các giao thức của tác nhân.
 #9.3.5    Cấp độ: 3    Vai trò: D
 Xác minh rằng các sự kiện vòng lặp bị hủy bỏ tạo cảnh báo và cung cấp các chỉ số cải tiến liên tục.

---

### 9.4 Bảo vệ chống lạm dụng ở mức giao thức

Đảm bảo kênh giao tiếp được bảo mật giữa các tác nhân và các hệ thống bên ngoài để ngăn chặn việc chiếm quyền kiểm soát hoặc thao túng.

 #9.4.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng tất cả các tin nhắn từ tác nhân đến công cụ và tin nhắn từ tác nhân sang tác nhân được xác thực (ví dụ: TLS hai chiều hoặc JWT) và được mã hóa từ đầu đến cuối.
 #9.4.2    Cấp độ: 1    Vai trò: D
 Đảm bảo các lược đồ được xác thực nghiêm ngặt; các trường không xác định hoặc tin nhắn bị định dạng sai sẽ bị từ chối.
 #9.4.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các kiểm tra tính toàn vẹn (MAC hoặc chữ ký số) bao phủ toàn bộ payload của thông điệp, bao gồm tham số công cụ.
 #9.4.4    Cấp độ: 2    Vai trò: D
 Xác minh rằng bảo vệ chống phát lại (nonce hoặc cửa sổ dấu thời gian) được thực thi ở lớp giao thức.
 #9.4.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng các triển khai giao thức đã trải qua fuzzing và phân tích tĩnh để phát hiện các lỗ hổng tiêm hoặc giải tuần tự dữ liệu.

---

### 9.5 Danh tính tác nhân và Chứng cứ can thiệp

Đảm bảo các hành động có thể được truy nguồn gốc và các sửa đổi có thể bị phát hiện.

 #9.5.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng mỗi thể hiện của tác nhân có một danh tính mật mã duy nhất (cặp khóa hoặc chứng chỉ gốc từ phần cứng).
 #9.5.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng toàn bộ hành động của tác nhân được ký và gắn dấu thời gian; nhật ký có chữ ký để đảm bảo tính không thể phủ nhận.
 #9.5.3    Cấp độ: 2    Vai trò: V
 Xác minh rằng nhật ký chống giả mạo được lưu trên một phương tiện chỉ cho phép ghi thêm hoặc ghi một lần.
 #9.5.4    Cấp độ: 3    Vai trò: D
 Xác nhận rằng các khóa nhận diện được xoay vòng theo lịch trình xác định và khi có các dấu hiệu bị xâm phạm.
 #9.5.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các nỗ lực giả mạo hoặc cố gắng gây xung đột khóa sẽ kích hoạt cách ly ngay lập tức đối với tác nhân bị ảnh hưởng.

---

### 9.6 Giảm thiểu rủi ro của bầy đàn đa tác nhân

Giảm thiểu các mối nguy hiểm do hành vi tập thể thông qua cô lập và mô hình hóa an toàn mang tính hình thức.

 #9.6.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các tác nhân hoạt động ở các miền bảo mật khác nhau được thực thi trong các sandbox thời gian chạy được cô lập hoặc trong các phân đoạn mạng được cô lập.
 #9.6.2    Cấp độ: 3    Vai trò: V
 Xác nhận rằng các hành vi của bầy robot swarm được mô hình hóa và được xác minh hình thức cho tính khả sống và tính an toàn trước khi triển khai.
 #9.6.3    Cấp độ: 3    Vai trò: D
 Hãy xác nhận rằng các trình giám sát thời gian chạy có thể phát hiện các mẫu không an toàn nảy sinh (ví dụ: dao động, điểm chết) và khởi xướng biện pháp khắc phục.

---

### 9.7 Xác thực / Ủy quyền Người dùng & Công cụ

Triển khai các biện pháp kiểm soát truy cập mạnh mẽ cho mọi hành động do tác nhân kích hoạt.

 #9.7.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các tác nhân xác thực với tư cách là chủ thể cấp nhất đối với các hệ thống downstream và không bao giờ tái sử dụng thông tin xác thực của người dùng cuối.
 #9.7.2    Cấp độ: 2    Vai trò: D
 Xác nhận rằng các chính sách ủy quyền ở mức chi tiết giới hạn những công cụ mà một tác nhân có thể gọi và các tham số mà nó có thể cung cấp.
 #9.7.3    Cấp độ: 2    Vai trò: V
 Xác minh rằng các kiểm tra quyền được đánh giá lại ở mỗi lần gọi (ủy quyền liên tục), chứ không chỉ ở lúc bắt đầu phiên.
 #9.7.4    Cấp độ: 3    Vai trò: D
 Xác minh rằng quyền được ủy quyền tự động hết hạn và yêu cầu tái đồng ý sau khi hết thời gian hoặc thay đổi phạm vi.

---

### 9.8 Bảo mật giao tiếp giữa các tác nhân

Mã hóa và bảo vệ tính toàn vẹn cho tất cả các thông điệp giữa các tác nhân để ngăn chặn nghe lén và sửa đổi.

 #9.8.1    Cấp độ: 1    Vai trò: D/V
 Xác thực lẫn nhau và mã hóa có tính bí mật phiên hoàn hảo (ví dụ TLS 1.3) là bắt buộc đối với các kênh của tác nhân.
 #9.8.2    Cấp độ: 1    Vai trò: D
 Xác minh tính toàn vẹn của thông điệp và nguồn gốc trước khi xử lý; nếu xác thực thất bại, hãy kích hoạt cảnh báo và loại bỏ thông điệp.
 #9.8.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng siêu dữ liệu giao tiếp (dấu thời gian, số thứ tự) được ghi lại để hỗ trợ tái dựng pháp y.
 #9.8.4    Cấp độ: 3    Vai trò: V
 Hãy xác minh rằng xác minh hình thức hoặc kiểm tra mô hình có thể xác nhận rằng các máy trạng thái của giao thức không thể bị đưa vào các trạng thái không an toàn.

---

### 9.9 Xác minh ý định & Thực thi ràng buộc

Xác nhận rằng các hành động của tác nhân phù hợp với ý định được người dùng nêu ra và các ràng buộc của hệ thống.

 #9.9.1    Cấp độ: 1    Vai trò: D
 Xác nhận rằng các trình giải ràng buộc tiền thực thi kiểm tra các hành động được đề xuất so với các quy tắc an toàn và chính sách được nhúng sẵn.
 #9.9.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các hành động có tác động cao (tài chính, phá hủy, nhạy cảm với quyền riêng tư) yêu cầu xác nhận ý định rõ ràng từ người dùng khởi xướng.
 #9.9.3    Cấp độ: 2    Vai trò: V
 Xác nhận rằng các kiểm tra hậu điều kiện xác thực các hành động đã hoàn tất, đạt được các tác động mong đợi và không gây tác dụng phụ; những sai lệch sẽ kích hoạt rollback.
 #9.9.4    Cấp độ: 3    Vai trò: V
 Xác minh rằng các phương pháp hình thức (ví dụ: kiểm tra mô hình, chứng minh định lý) hoặc kiểm tra dựa trên đặc tính cho thấy các kế hoạch của tác nhân thỏa mãn tất cả các ràng buộc được khai báo.
 #9.9.5    Cấp độ: 3    Vai trò: D
 Xác nhận rằng các sự cố lệch ý định hoặc vi phạm ràng buộc đóng góp vào chu trình cải tiến liên tục và chia sẻ thông tin tình báo về các mối đe dọa.

---

### 9.10 Chiến lược Suy luận của Tác nhân cho Bảo mật

Lựa chọn và thực thi an toàn các chiến lược suy luận khác nhau, bao gồm ReAct, Chain-of-Thought và Tree-of-Thoughts.

 #9.10.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng việc lựa chọn chiến lược suy luận sử dụng các tiêu chí xác định (độ phức tạp của đầu vào, loại tác vụ, ngữ cảnh bảo mật) và các đầu vào giống nhau sẽ tạo ra các lựa chọn chiến lược giống hệt nhau trong cùng ngữ cảnh bảo mật.
 #9.10.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng mỗi chiến lược suy luận (ReAct, Chain-of-Thought, Tree-of-Thoughts) có xác thực đầu vào riêng biệt, làm sạch đầu ra và giới hạn thời gian thực thi tương ứng với phương pháp nhận thức của nó.
 #9.10.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các chuyển tiếp của chiến lược suy luận được ghi lại với đầy đủ ngữ cảnh, bao gồm đặc tính đầu vào, giá trị của các tiêu chí lựa chọn và siêu dữ liệu thực thi để tái tạo dấu vết kiểm toán.
 #9.10.4    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng lý luận Tree-of-Thoughts bao gồm các cơ chế cắt nhánh để kết thúc quá trình khám phá khi phát hiện vi phạm chính sách, giới hạn tài nguyên hoặc ranh giới an toàn.
 #9.10.5    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng chu trình ReAct (Reason-Act-Observe) bao gồm các điểm xác thực ở mỗi giai đoạn: xác minh bước suy luận, phê duyệt hành động và chuẩn hóa quan sát trước khi tiến hành.
 #9.10.6    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng các chỉ số hiệu suất của chiến lược suy luận (thời gian thực thi, mức sử dụng tài nguyên, chất lượng đầu ra) được giám sát bằng các cảnh báo tự động khi các chỉ số vượt ngưỡng đã được cấu hình.
 #9.10.7    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các phương pháp suy luận lai kết hợp nhiều chiến lược duy trì xác thực đầu vào và ràng buộc đầu ra của tất cả các chiến lược thành phần mà không bỏ qua bất kỳ biện pháp kiểm soát bảo mật nào.
 #9.10.8    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng kiểm thử bảo mật cho chiến lược suy luận bao gồm fuzzing với đầu vào bị sai định dạng, các lời nhắc thù địch được thiết kế để ép buộc chuyển đổi chiến lược, và kiểm thử điều kiện biên cho từng cách tiếp cận nhận thức.

---

### 9.11 Quản lý trạng thái vòng đời của tác nhân và bảo mật

Khởi tạo tác nhân an toàn, chuyển đổi trạng thái và kết thúc với dấu vết kiểm toán mật mã và các thủ tục khôi phục được định nghĩa.

 #9.11.1    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng quá trình khởi tạo tác nhân bao gồm thiết lập danh tính bằng mật mã với chứng thực dựa trên phần cứng và nhật ký kiểm toán khởi động bất biến chứa ID tác nhân, dấu thời gian, băm cấu hình và các tham số khởi tạo.
 #9.11.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các chuyển đổi trạng thái của tác nhân được ký số, gắn dấu thời gian và được ghi lại với đầy đủ bối cảnh bao gồm các sự kiện kích hoạt, giá trị băm của trạng thái trước, giá trị băm của trạng thái mới, và các xác thực bảo mật đã được thực hiện.
 #9.11.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng quy trình tắt tác nhân bao gồm xóa sạch bộ nhớ bằng mã hóa (cryptographic erasure) hoặc ghi đè nhiều lượt, thu hồi thông tin xác thực kèm thông báo cho cơ quan cấp chứng chỉ, và tạo chứng chỉ kết thúc có khả năng phát hiện sự can thiệp.
 #9.11.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các cơ chế phục hồi của tác nhân xác thực tính toàn vẹn của trạng thái bằng cách sử dụng các chuỗi băm mật mã (tối thiểu SHA-256) và quay về trạng thái được biết là hợp lệ khi phát hiện sự cố, với cảnh báo tự động và yêu cầu phê duyệt thủ công.
 #9.11.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các cơ chế lưu trữ trạng thái của tác nhân mã hóa dữ liệu trạng thái nhạy cảm bằng khóa AES-256 cho từng tác nhân và triển khai quay vòng khóa an toàn theo lịch trình có thể cấu hình (tối đa 90 ngày) với triển khai không gián đoạn.

---

### 9.12 Khung bảo mật tích hợp công cụ

Các biện pháp kiểm soát an ninh cho việc tải công cụ động, thực thi và xác thực kết quả với các quy trình đánh giá rủi ro và phê duyệt được định nghĩa.

 #9.12.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các mô tả công cụ bao gồm siêu dữ liệu bảo mật chỉ định quyền được yêu cầu (đọc/ghi/thực thi), mức độ rủi ro (thấp/trung bình/cao), giới hạn tài nguyên (CPU, bộ nhớ, mạng), và các yêu cầu xác thực được ghi trong manifest của công cụ.
 #9.12.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng kết quả thực thi công cụ được xác thực theo các schema mong đợi (JSON Schema, XML Schema) và các chính sách bảo mật (làm sạch đầu ra, phân loại dữ liệu) trước khi tích hợp với các giới hạn thời gian chờ và các thủ tục xử lý lỗi.
 #9.12.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng nhật ký tương tác của công cụ chứa bối cảnh bảo mật chi tiết, bao gồm việc sử dụng đặc quyền, các mẫu truy cập dữ liệu, thời gian thực thi, mức tiêu thụ tài nguyên và mã trả về, được ghi nhật ký có cấu trúc để tích hợp với SIEM.
 #9.12.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các cơ chế nạp công cụ động xác thực chữ ký số bằng hạ tầng PKI và triển khai các giao thức nạp an toàn với cô lập sandbox và xác thực quyền trước khi thực thi.
 #9.12.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các đánh giá bảo mật công cụ được tự động kích hoạt cho các phiên bản mới với các cổng phê duyệt bắt buộc bao gồm phân tích tĩnh, kiểm thử động và xem xét của đội ngũ bảo mật, với các tiêu chí phê duyệt được ghi lại và các yêu cầu SLA.

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

## 10 Độ bền trước tấn công adversarial và Bảo vệ quyền riêng tư

### Mục tiêu kiểm soát

Đảm bảo các mô hình AI luôn đáng tin cậy, được bảo vệ quyền riêng tư và chống bị lạm dụng khi đối mặt với các cuộc tấn công né tránh, suy diễn, rút trích hoặc đầu độc mô hình.

---

### 10.1 Căn chỉnh mô hình và An toàn

Ngăn chặn các đầu ra gây hại hoặc vi phạm chính sách.

 #10.1.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng alignment test-suite (lời nhắc của đội đỏ, các probe jailbreak, nội dung bị cấm) được kiểm soát phiên bản và chạy trên mỗi bản phát hành của mô hình.
 #10.1.2    Cấp độ: 1    Vai trò: D
 Xác minh rằng các hàng rào từ chối và hàng rào đảm bảo hoàn thành an toàn được thực thi.
 #10.1.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng một trình đánh giá tự động đo lường tỷ lệ nội dung gây hại và đánh dấu các sự hồi quy vượt quá ngưỡng đã thiết lập.
 #10.1.4    Cấp độ: 2    Vai trò: D
 Xác minh rằng đào tạo chống jailbreak được ghi chép đầy đủ và có thể tái tạo.
 #10.1.5    Cấp độ: 3    Vai trò: V
 Xác minh rằng các bằng chứng tuân thủ chính sách mang tính hình thức hoặc giám sát được chứng nhận có bao phủ các miền trọng yếu.

---

### 10.2 Làm cứng ví dụ đối kháng

Tăng khả năng chống chịu trước các đầu vào bị thao túng. Huấn luyện đối kháng mạnh mẽ và chấm điểm chuẩn là thực tiễn tốt nhất hiện nay.

 #10.2.1    Cấp độ: 1    Vai trò: D
 Xác minh rằng các kho lưu trữ dự án bao gồm các cấu hình huấn luyện đối kháng với seed có thể tái tạo được.
 #10.2.2    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng phát hiện ví dụ đối kháng kích hoạt các cảnh báo chặn trong các pipeline sản xuất.
 #10.2.4    Cấp độ: 3    Vai trò: V
 Xác nhận rằng các chứng minh độ bền được chứng nhận hoặc chứng chỉ giới hạn theo khoảng bao phủ ít nhất các lớp quan trọng hàng đầu.
 #10.2.5    Cấp độ: 3    Vai trò: V
 Xác nhận rằng các bài kiểm tra hồi quy sử dụng các cuộc tấn công thích ứng để đảm bảo không có sự suy giảm độ bền có thể đo được.

---

### 10.3 Biện pháp giảm thiểu Membership-Inference

Giới hạn khả năng xác định xem một bản ghi có nằm trong dữ liệu huấn luyện hay không. Riêng tư khác biệt và che giấu điểm tin cậy vẫn là những biện pháp bảo vệ được biết đến có hiệu quả nhất.

 #10.3.1    Cấp độ: 1    Vai trò: D
 Xác nhận rằng chuẩn hóa entropy theo từng truy vấn hoặc điều chỉnh nhiệt độ làm giảm các dự đoán quá tự tin.
 #10.3.2    Cấp độ: 2    Vai trò: D
 Xác nhận rằng quá trình huấn luyện sử dụng tối ưu hóa riêng tư khác biệt có giới hạn ε cho các tập dữ liệu nhạy cảm.
 #10.3.3    Cấp độ: 2    Vai trò: V
 Xác nhận rằng các mô phỏng tấn công (shadow-model hoặc hộp đen) cho thấy AUC của cuộc tấn công ≤ 0.60 trên dữ liệu được giữ lại.

---

### 10.4 Kháng tấn công đảo ngược mô hình

Ngăn chặn việc tái tạo các thuộc tính riêng tư. Các khảo sát gần đây nhấn mạnh việc rút ngắn đầu ra và các đảm bảo DP như các biện pháp bảo vệ thực tế.

 #10.4.1    Cấp độ: 1    Vai trò: D
 Xác minh rằng các thuộc tính nhạy cảm không bao giờ được xuất trực tiếp; khi cần, hãy sử dụng bucket hoặc biến đổi một chiều.
 #10.4.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng giới hạn tần suất truy vấn đang điều tiết các truy vấn thích nghi lặp lại từ cùng chủ thể xác thực.
 #10.4.3    Cấp độ: 2    Vai trò: D
 Xác minh rằng mô hình được huấn luyện với nhiễu bảo vệ quyền riêng tư.

---

### 10.5 Bảo vệ chống rút trích mô hình

Phát hiện và ngăn chặn sao chép trái phép. Dấu nước và phân tích mẫu truy vấn được khuyến nghị.

 #10.5.1    Cấp độ: 1    Vai trò: D
 Đảm bảo rằng các cổng suy diễn thực thi các giới hạn lưu lượng toàn cầu và theo từng khóa API, được tinh chỉnh theo ngưỡng ghi nhớ của mô hình.
 #10.5.2    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng entropy của truy vấn và thống kê đa dạng đầu vào cung cấp cho một bộ phát hiện trích xuất tự động.
 #10.5.3    Cấp độ: 2    Vai trò: V
 Xác minh rằng các dấu nước mong manh hoặc ngẫu nhiên có thể được chứng minh với p < 0.01 trong ≤ 1 000 lượt truy vấn đối với một bản sao bị nghi ngờ sao chép.
 #10.5.4    Cấp độ: 3    Vai trò: D
 Xác minh rằng các khóa watermark và bộ kích hoạt được lưu trữ trong một thiết bị bảo mật phần cứng (HSM) và được xoay vòng hàng năm.
 #10.5.5    Cấp độ: 3    Vai trò: V
 Xác nhận rằng các sự kiện cảnh báo trích xuất bao gồm các truy vấn vi phạm và được tích hợp với các kịch bản ứng phó sự cố.

---

### 10.6 Phát hiện dữ liệu-đầu độc tại thời điểm suy diễn

Nhận diện và vô hiệu hóa các đầu vào bị cài cửa hậu hoặc bị đầu độc.

 #10.6.1    Cấp độ: 1    Vai trò: D
 Xác nhận rằng đầu vào đã được đưa qua một bộ phát hiện bất thường (ví dụ: STRIP, điểm đánh giá tính nhất quán) trước khi mô hình suy diễn.
 #10.6.2    Cấp độ: 1    Vai trò: V
 Xác nhận rằng ngưỡng của bộ phát hiện được điều chỉnh trên các tập xác thực sạch và bị nhiễm độc để đạt được ít hơn 5% dương tính giả.
 #10.6.3    Cấp độ: 2    Vai trò: D
 Xác minh rằng các đầu vào bị đánh dấu là độc hại kích hoạt chặn mềm và quy trình xem xét bởi con người.
 #10.6.4    Cấp độ: 2    Vai trò: V
 Xác minh rằng các bộ phát hiện được thử nghiệm chịu tải với các cuộc tấn công cửa hậu thích nghi và không kích hoạt.
 #10.6.5    Cấp độ: 3    Vai trò: D
 Xác minh rằng các chỉ số hiệu quả phát hiện được ghi lại và được đánh giá lại định kỳ với thông tin tình báo về mối đe dọa mới.

---

### 10.7 Thích ứng Chính sách Bảo mật Động

Cập nhật chính sách bảo mật theo thời gian thực dựa trên thông tin tình báo về mối đe dọa và phân tích hành vi.

 #10.7.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các chính sách bảo mật có thể được cập nhật một cách động mà không cần khởi động lại agent, đồng thời duy trì tính toàn vẹn của phiên bản chính sách.
 #10.7.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các cập nhật chính sách được ký bằng chữ ký số bởi nhân viên bảo mật được ủy quyền và được xác thực trước khi áp dụng.
 #10.7.3    Cấp độ: 2    Vai trò: D/V
 Kiểm tra xem các thay đổi chính sách động được ghi lại với đầy đủ dấu vết kiểm toán, bao gồm lý do, chuỗi phê duyệt và thủ tục quay lui.
 #10.7.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các cơ chế bảo mật thích ứng điều chỉnh độ nhạy của phát hiện mối đe dọa dựa trên ngữ cảnh rủi ro và mẫu hành vi.
 #10.7.5    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng các quyết định thích ứng chính sách có thể giải thích được và bao gồm các dấu vết bằng chứng cho việc xem xét bởi nhóm an ninh.

---

### 10.8 Phân tích bảo mật dựa trên phản chiếu

Xác thực bảo mật thông qua sự tự phản chiếu của tác nhân và phân tích siêu nhận thức.

 #10.8.1    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng các cơ chế phản chiếu của tác nhân bao gồm đánh giá tự thân tập trung vào an ninh đối với các quyết định và hành động.
 #10.8.2    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng các đầu ra của quá trình suy ngẫm được xác thực để ngăn chặn sự thao túng các cơ chế tự đánh giá bởi các đầu vào đối kháng.
 #10.8.3    Cấp độ: 2    Vai trò: D/V
 Kiểm tra để đảm bảo rằng phân tích an ninh siêu nhận thức có thể xác định thiên lệch, thao túng hoặc bị xâm phạm trong quá trình suy luận của tác nhân.
 #10.8.4    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng các cảnh báo bảo mật dựa trên phản chiếu sẽ kích hoạt giám sát nâng cao và có thể kích hoạt các luồng làm việc can thiệp của con người.
 #10.8.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng việc học liên tục từ các phản ánh về bảo mật cải thiện khả năng phát hiện mối đe dọa mà không làm suy giảm chức năng hợp lệ.

---

### 10.9 Tiến hóa và Bảo mật Tự cải thiện

Các biện pháp kiểm soát bảo mật cho hệ thống tác nhân có khả năng tự chỉnh sửa và tiến hóa.

 #10.9.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng khả năng tự chỉnh sửa của hệ thống bị giới hạn trong các khu vực an toàn được chỉ định, với các ranh giới xác thực hình thức.
 #10.9.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các đề xuất tiến hóa được đánh giá tác động bảo mật trước khi triển khai.
 #10.9.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các cơ chế tự cải thiện có khả năng khôi phục về trạng thái trước và có xác thực tính toàn vẹn.
 #10.9.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng bảo mật của meta-learning ngăn chặn sự thao túng có chủ đích từ phía kẻ tấn công đối với các thuật toán cải thiện.
 #10.9.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng tự cải thiện đệ quy bị giới hạn bởi các ràng buộc an toàn hình thức với các chứng minh toán học về sự hội tụ.

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

## 11 Bảo vệ quyền riêng tư và Quản lý dữ liệu cá nhân

### Mục tiêu kiểm soát

Giữ vững cam kết quyền riêng tư nghiêm ngặt trên toàn vòng đời AI — từ thu thập, huấn luyện, suy diễn đến ứng phó sự cố — để dữ liệu cá nhân chỉ được xử lý khi có sự đồng thuận rõ ràng, phạm vi tối thiểu cần thiết, xóa dữ liệu có thể được chứng thực, và các đảm bảo quyền riêng tư chính thức.

---

### 11.1 Ẩn danh và Tối thiểu hóa dữ liệu

 #11.1.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các nhận dạng trực tiếp và nhận dạng bán định danh đã bị loại bỏ và được băm.
 #11.1.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các kiểm toán tự động đo được k-anonymity/l-diversity và cảnh báo khi các ngưỡng giảm xuống dưới mức được quy định trong chính sách.
 #11.1.3    Cấp độ: 2    Vai trò: V
 Xác minh rằng các báo cáo về mức độ quan trọng của đặc trưng trong mô hình không có rò rỉ danh tính vượt quá ε = 0.01 của thông tin tương hỗ.
 #11.1.4    Cấp độ: 3    Vai trò: V
 Xác minh rằng các chứng minh chính thức hoặc chứng nhận dữ liệu tổng hợp cho thấy nguy cơ nhận dạng lại ≤ 0.05 ngay cả khi bị tấn công liên kết.

---

### 11.2 Right-to-be-Forgotten & thực thi xóa dữ liệu

 #11.2.1    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng các yêu cầu xóa dữ liệu chủ thể được lan truyền tới các tập dữ liệu thô, điểm kiểm tra, nhúng, nhật ký và sao lưu trong khuôn khổ thỏa thuận mức độ dịch vụ (SLA) dưới 30 ngày.
 #11.2.2    Cấp độ: 2    Vai trò: D
 Xác minh rằng các quy trình "machine-unlearning" có thể được tái huấn luyện trực tiếp hoặc ước lượng việc xóa bằng cách sử dụng các thuật toán xóa được chứng nhận.
 #11.2.3    Cấp độ: 2    Vai trò: V
 Xác nhận rằng đánh giá mô hình bóng cho thấy các bản ghi đã bị quên ảnh hưởng đến dưới 1% đầu ra sau khi thực hiện khử học.
 #11.2.4    Cấp độ: 3    Vai trò: V
 Xác minh rằng các sự kiện xóa được ghi lại một cách bất biến và có thể kiểm toán cho cơ quan quản lý.

---

### 11.3 Các biện pháp bảo vệ quyền riêng tư vi phân

 #11.3.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các bảng điều khiển kế toán tổn thất quyền riêng tư sẽ cảnh báo khi ε tích lũy vượt quá ngưỡng của chính sách.
 #11.3.2    Cấp độ: 2    Vai trò: V
 Xác minh rằng các kiểm toán quyền riêng tư hộp đen ước lượng ε̂ trong vòng 10% so với giá trị được công bố.
 #11.3.3    Cấp độ: 3    Vai trò: V
 Xác nhận rằng các chứng minh chính thức bao phủ tất cả các tinh chỉnh sau đào tạo và các nhúng.

---

### 11.4 Mục đích-Giới hạn & Phạm vi-Mở rộng Bảo vệ

 #11.4.1    Cấp độ: 1    Vai trò: D
 Xác nhận rằng mọi tập dữ liệu và điểm kiểm tra mô hình đều mang nhãn mục đích có thể đọc được bằng máy và khớp với sự đồng ý ban đầu.
 #11.4.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các bộ giám sát thời gian chạy phát hiện các truy vấn không nhất quán với mục đích được khai báo và kích hoạt từ chối mềm.
 #11.4.3    Cấp độ: 3    Vai trò: D
 Xác minh rằng các cổng dựa trên policy-as-code chặn việc tái triển khai các mô hình đến các miền mới mà không được DPIA xem xét.
 #11.4.4    Cấp độ: 3    Vai trò: V
 Xác minh rằng các bằng chứng truy vết chính thức cho thấy mọi vòng đời dữ liệu cá nhân vẫn nằm trong phạm vi được đồng ý.

---

### 11.5 Quản lý sự đồng ý và theo dõi dựa trên căn cứ hợp pháp

 #11.5.1    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng một Nền tảng Quản lý Sự đồng ý (CMP) ghi nhận trạng thái đồng ý tham gia, mục đích và thời gian lưu giữ dữ liệu cho từng đối tượng dữ liệu.
 #11.5.2    Cấp độ: 2    Vai trò: D
 Xác minh rằng các API tiết lộ token đồng ý; các mô hình phải xác thực phạm vi của token trước khi suy diễn.
 #11.5.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng sự đồng ý bị từ chối hoặc rút lại sẽ khiến các pipeline xử lý dừng hoạt động trong vòng 24 giờ.

---

### 11.6 Học liên bang với các biện pháp kiểm soát quyền riêng tư

 #11.6.1    Cấp độ: 1    Vai trò: D
 Xác minh rằng các cập nhật của máy khách thực hiện thêm nhiễu theo riêng tư vi phân cục bộ trước khi tổng hợp.
 #11.6.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các chỉ số huấn luyện được đảm bảo riêng tư vi phân và không bao giờ tiết lộ mất mát của một client duy nhất.
 #11.6.3    Cấp độ: 2    Vai trò: V
 Xác minh rằng tổng hợp kháng nhiễm độc dữ liệu (ví dụ: Krum/Trimmed-Mean) đã được bật.
 #11.6.4    Cấp độ: 3    Vai trò: V
 Xác minh rằng các chứng minh hình thức cho thấy tổng ngân sách ε với tổn thất tiện ích dưới 5.

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

## C12 Giám sát, Ghi nhật ký và Phát hiện bất thường

### Mục tiêu kiểm soát

Phần này cung cấp các yêu cầu để cung cấp khả năng quan sát thời gian thực và tầm nhìn pháp y đối với những gì mô hình và các thành phần AI khác thấy, làm và trả về, nhằm mục đích phát hiện, phân loại và sắp xếp ưu tiên các mối đe dọa và học hỏi từ chúng.

### C12.1 Ghi Nhật ký Yêu cầu và Phản hồi

 #12.1.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng tất cả các lời nhắc của người dùng và phản hồi của mô hình được ghi lại với siêu dữ liệu phù hợp (ví dụ: dấu thời gian, ID người dùng, ID phiên, phiên bản mô hình).
 #12.1.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các nhật ký được lưu trữ trong các kho lưu trữ an toàn và có kiểm soát truy cập, với các chính sách lưu giữ và thủ tục sao lưu phù hợp.
 #12.1.3    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các hệ thống lưu trữ nhật ký triển khai mã hóa khi lưu trữ và mã hóa khi truyền để bảo vệ thông tin nhạy cảm có trong nhật ký.
 #12.1.4    Cấp độ: 1    Vai trò: D/V
 Đảm bảo dữ liệu nhạy cảm trong các lời nhắc và đầu ra được tự động ẩn hoặc che khuất trước khi ghi log, với các quy tắc ẩn dữ liệu có thể cấu hình cho PII (thông tin nhận dạng cá nhân), thông tin xác thực và thông tin độc quyền.
 #12.1.5    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng các quyết định về chính sách và các hành động lọc an toàn được ghi lại với mức chi tiết đầy đủ để phục vụ cho kiểm toán và gỡ lỗi các hệ thống kiểm duyệt nội dung.
 #12.1.6    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng tính toàn vẹn của nhật ký được bảo vệ thông qua ví dụ như chữ ký số hoặc lưu trữ chỉ ghi.

---

### C12.2 Phát hiện và Cảnh báo lạm dụng

 #12.2.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng hệ thống có khả năng phát hiện và cảnh báo về các mẫu jailbreak đã biết, các nỗ lực chèn prompt và các đầu vào đối kháng bằng cách sử dụng phát hiện dựa trên chữ ký.
 #12.2.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng hệ thống tích hợp với các nền tảng SIEM hiện có bằng cách sử dụng các định dạng nhật ký và giao thức tiêu chuẩn.
 #12.2.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các sự kiện bảo mật được làm phong phú bao gồm ngữ cảnh đặc thù của AI như định danh mô hình, điểm tự tin và quyết định của bộ lọc an toàn.
 #12.2.4    Cấp độ: 2    Vai trò: D/V
 Đảm bảo rằng hệ thống phát hiện bất thường hành vi nhận diện các mẫu trò chuyện bất thường, các nỗ lực thử lại quá mức hoặc các hành vi thăm dò có hệ thống.
 #12.2.5    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng các cơ chế cảnh báo theo thời gian thực sẽ thông báo cho đội ngũ bảo mật khi phát hiện vi phạm chính sách tiềm ẩn hoặc các nỗ lực tấn công.
 #12.2.6    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các quy tắc tùy chỉnh được bao gồm để phát hiện các mẫu đe dọa liên quan đến AI, bao gồm các nỗ lực jailbreak có phối hợp, chiến dịch tiêm prompt và các cuộc tấn công trích xuất mô hình.
 #12.2.7    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các quy trình ứng phó sự cố tự động có thể cô lập các mô hình bị xâm phạm, chặn người dùng độc hại và nâng cao mức ưu tiên cho các sự kiện bảo mật nghiêm trọng.

---

### C12.3 Phát hiện sự dịch chuyển của mô hình

 #12.3.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng hệ thống theo dõi các chỉ số hiệu suất cơ bản như độ chính xác, điểm tự tin, độ trễ và tỷ lệ lỗi giữa các phiên bản mô hình và theo các khoảng thời gian.
 #12.3.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng cảnh báo tự động được kích hoạt khi các chỉ số hiệu suất vượt quá ngưỡng suy giảm được xác định trước hoặc lệch đáng kể so với các mức chuẩn tham chiếu.
 #12.3.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các công cụ giám sát phát hiện ảo giác nhận diện và đánh dấu các trường hợp khi đầu ra của mô hình chứa thông tin không đúng sự thật, không nhất quán hoặc thông tin giả mạo.

---

### C12.4 Hiệu suất và Hành vi Telemetry

 #12.4.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các chỉ số vận hành bao gồm độ trễ yêu cầu, lượng token tiêu thụ, mức sử dụng bộ nhớ và thông lượng được thu thập và giám sát liên tục.
 #12.4.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng tỷ lệ thành công và thất bại được theo dõi kèm theo phân loại các loại lỗi và nguyên nhân gốc của chúng.
 #12.4.3    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng việc giám sát sử dụng tài nguyên bao gồm việc sử dụng GPU/CPU, tiêu thụ bộ nhớ và yêu cầu về lưu trữ, kèm theo cảnh báo khi vượt ngưỡng.

---

### C12.5 Lập kế hoạch và thực thi ứng phó sự cố AI

 #12.5.1    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng các kế hoạch ứng phó sự cố liên quan đến AI được thiết kế để cụ thể xử lý các sự kiện bảo mật, bao gồm xâm phạm mô hình, đầu độc dữ liệu và tấn công đối kháng.
 #12.5.2    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng các đội phản ứng sự cố có quyền truy cập các công cụ pháp y chuyên dụng cho AI và kiến thức chuyên môn để điều tra hành vi của mô hình và các vector tấn công.
 #12.5.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng phân tích sau sự cố bao gồm các cân nhắc về tái huấn luyện mô hình, cập nhật bộ lọc an toàn và tích hợp các bài học rút ra vào các biện pháp kiểm soát an ninh.

---

### C12.5 Phát hiện suy giảm hiệu suất AI

Giám sát và phát hiện sự suy giảm hiệu suất và chất lượng của mô hình AI theo thời gian.

 #12.5.1    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng độ chính xác của mô hình, precision, recall, và điểm F1 được theo dõi liên tục và so sánh với ngưỡng tham chiếu.
 #12.5.2    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng phát hiện sự lệch dữ liệu đang giám sát sự thay đổi trong phân phối đầu vào có thể ảnh hưởng đến hiệu suất của mô hình.
 #12.5.3    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng việc phát hiện độ lệch khái niệm có thể nhận diện các thay đổi trong mối quan hệ giữa các đầu vào và các đầu ra mong đợi.
 #12.5.4    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng sự suy giảm hiệu suất kích hoạt cảnh báo tự động và khởi động các quy trình tái huấn luyện mô hình hoặc thay thế mô hình.
 #12.5.5    Cấp độ: 3    Vai trò: V
 Xác nhận rằng phân tích nguyên nhân gốc của sự suy giảm liên quan đến sự sụt giảm hiệu suất với các thay đổi dữ liệu, sự cố cơ sở hạ tầng hoặc các yếu tố bên ngoài.

---

### C12.6 Trực quan hóa DAG và Bảo mật quy trình làm việc

Bảo vệ hệ thống trực quan hóa quy trình làm việc khỏi rò rỉ thông tin và các cuộc tấn công thao túng.

 #12.6.1    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng dữ liệu trực quan hóa DAG đã được làm sạch để loại bỏ thông tin nhạy cảm trước khi lưu trữ hoặc truyền.
 #12.6.2    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng các kiểm soát quyền truy cập cho trực quan hóa luồng công việc đảm bảo chỉ người dùng được ủy quyền mới có thể xem đường đi quyết định của tác nhân và các dấu vết suy luận.
 #12.6.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng tính toàn vẹn của dữ liệu DAG được bảo vệ thông qua chữ ký số và các cơ chế lưu trữ có khả năng phát hiện sự can thiệp.
 #12.6.4    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng các hệ thống trực quan hóa luồng công việc thực hiện xác thực đầu vào để ngăn chặn các cuộc tấn công tiêm thông qua dữ liệu nút hoặc cạnh được thiết kế tinh vi.
 #12.6.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các cập nhật DAG thời gian thực được giới hạn tốc độ và xác thực để ngăn chặn các cuộc tấn công từ chối dịch vụ nhắm vào hệ thống trực quan hóa.

---

### C12.7 Giám sát hành vi bảo mật chủ động

Phát hiện và ngăn chặn các mối đe dọa bảo mật thông qua phân tích hành vi của tác nhân chủ động.

 #12.7.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các hành vi của tác nhân chủ động được xác thực về bảo mật trước khi thực thi, với tích hợp đánh giá rủi ro.
 #12.7.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các kích hoạt sáng kiến tự động bao gồm đánh giá ngữ cảnh bảo mật và đánh giá bối cảnh mối đe dọa.
 #12.7.3    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng các mẫu hành vi mang tính chủ động được phân tích để đánh giá những tác động bảo mật tiềm ẩn và những hậu quả ngoài ý muốn.
 #12.7.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các hành động chủ động có tính bảo mật cao yêu cầu chuỗi phê duyệt rõ ràng kèm theo nhật ký kiểm toán.
 #12.7.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng phát hiện bất thường hành vi có thể nhận diện các lệch trong các mẫu của tác nhân chủ động và cho thấy sự xâm nhập.

---

### Tài liệu tham khảo

NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3
ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6
EU AI Act — Article 12, 13, 16 and 19 on Logging and Record-keeping

## Giám sát của con người, Trách nhiệm giải trình và Quản trị

### Mục tiêu kiểm soát

Chương này đưa ra các yêu cầu về việc duy trì sự giám sát của con người và chuỗi trách nhiệm rõ ràng trong các hệ thống AI, đồng thời đảm bảo khả năng giải thích, tính minh bạch và quản trị đạo đức trong suốt vòng đời của AI.

---

### C13.1 Cơ chế tắt khẩn cấp và ghi đè

Cung cấp các lộ trình tắt nguồn hoặc khôi phục lại trạng thái trước khi hệ thống AI có hành vi không an toàn được phát hiện.

 #13.1.1    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng tồn tại một cơ chế công tắc tắt thủ công để ngay lập tức ngừng quá trình suy diễn và đầu ra của mô hình AI.
 #13.1.2    Cấp độ: 1    Vai trò: D
 Đảm bảo rằng các điều khiển ghi đè chỉ có thể được truy cập bởi những nhân sự được ủy quyền.
 #13.1.3    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng các thủ tục hoàn nguyên có thể quay về các phiên bản mô hình trước đó hoặc các hoạt động ở safe-mode.
 #13.1.4    Cấp độ: 3    Vai trò: V
 Xác minh rằng các cơ chế ghi đè được kiểm tra định kỳ.

---

### C13.2 Human-in-the-Loop Điểm kiểm tra quyết định

Yêu cầu phê duyệt của con người khi mức độ rủi ro vượt quá ngưỡng rủi ro được xác định trước.

 #13.2.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các quyết định AI có rủi ro cao đòi hỏi sự phê duyệt rõ ràng từ con người trước khi thực thi.
 #13.2.2    Cấp độ: 1    Vai trò: D
 Xác minh rằng ngưỡng rủi ro được định nghĩa rõ ràng và tự động kích hoạt các quy trình xem xét của con người.
 #13.2.3    Cấp độ: 2    Vai trò: D
 Xác minh rằng các quyết định nhạy cảm về thời gian có các biện pháp dự phòng khi sự phê duyệt của con người không thể được thực hiện trong khung thời gian yêu cầu.
 #13.2.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng quy trình leo thang định rõ mức thẩm quyền cho các loại quyết định khác nhau hoặc các loại rủi ro, nếu áp dụng.

---

### C13.3 Chuỗi chịu trách nhiệm và khả năng kiểm toán

Ghi lại hành động của người vận hành và quyết định của mô hình.

 #13.3.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng mọi quyết định của hệ thống AI và các can thiệp của con người đều được ghi lại với dấu thời gian, danh tính người dùng và lý do quyết định.
 #13.3.2    Cấp độ: 2    Vai trò: D
 Xác minh rằng nhật ký kiểm toán không thể bị sửa đổi và bao gồm các cơ chế xác minh tính toàn vẹn.

---

### C13.4 Các kỹ thuật Explainable-AI

Tầm quan trọng của đặc trưng bề mặt, counterfactuals và giải thích cục bộ.

 #13.4.1    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng các hệ thống AI cung cấp các giải thích cơ bản cho các quyết định của chúng ở định dạng dễ đọc cho con người.
 #13.4.2    Cấp độ: 2    Vai trò: V
 Xác nhận chất lượng giải thích thông qua các nghiên cứu đánh giá bởi con người và các thước đo.
 #13.4.3    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng các điểm tầm quan trọng của đặc trưng hoặc các phương pháp phân bổ đóng góp (SHAP, LIME, v.v.) có sẵn cho các quyết định quan trọng.
 #13.4.4    Cấp độ: 3    Vai trò: V
 Xác nhận rằng các giải thích counterfactual cho thấy cách các đầu vào có thể được chỉnh sửa để thay đổi kết quả, nếu phù hợp với trường hợp sử dụng và lĩnh vực.

---

### C13.5 Thẻ Mô hình và Tiết lộ về Việc Sử Dụng

Duy trì thẻ mô hình cho mục đích sử dụng dự định, các chỉ số hiệu suất và các cân nhắc đạo đức.

 #13.5.1    Cấp độ: 1    Vai trò: D
 Đảm bảo rằng thẻ mô hình ghi lại các trường hợp sử dụng dự định, giới hạn và các chế độ lỗi được biết.
 #13.5.2    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các chỉ số hiệu suất cho các trường hợp sử dụng khác nhau đã được công khai.
 #13.5.3    Cấp độ: 2    Vai trò: D
 Đảm bảo rằng các cân nhắc đạo đức, các đánh giá thiên vị, các đánh giá công bằng, đặc điểm dữ liệu huấn luyện và các hạn chế được biết về dữ liệu huấn luyện được ghi nhận và cập nhật định kỳ.
 #13.5.4    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng thẻ mô hình được kiểm soát phiên bản và được duy trì xuyên suốt vòng đời của mô hình, với việc theo dõi sự thay đổi.

---

### C13.6 Định lượng bất định

Lan truyền điểm tự tin hoặc các thước đo entropy trong phản hồi.

 #13.6.1    Cấp độ: 1    Vai trò: D
 Xác minh rằng các hệ thống AI cung cấp điểm tự tin hoặc các thước đo bất định kèm theo đầu ra của chúng.
 #13.6.2    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng ngưỡng bất định kích hoạt xem xét bổ sung bởi con người hoặc các đường đi quyết định thay thế.
 #13.6.3    Cấp độ: 2    Vai trò: V
 Xác nhận rằng các phương pháp định lượng bất định được hiệu chuẩn và xác thực so với dữ liệu ground truth.
 #13.6.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng sự lan truyền bất định được duy trì qua các quy trình AI nhiều bước.

---

### C13.7 Báo cáo minh bạch dành cho người dùng

Cung cấp các thông báo định kỳ về sự cố, độ lệch dữ liệu và việc sử dụng dữ liệu.

 #13.7.1    Cấp độ: 1    Vai trò: D/V
 Đảm bảo rằng các chính sách sử dụng dữ liệu và thực hành quản lý sự đồng ý của người dùng được truyền đạt một cách rõ ràng tới các bên liên quan.
 #13.7.2    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng các đánh giá tác động của AI đã được thực hiện và kết quả được đưa vào báo cáo.
 #13.7.3    Cấp độ: 2    Vai trò: D/V
 Đảm bảo rằng các báo cáo minh bạch được công bố định kỳ tiết lộ các sự cố liên quan đến AI và các chỉ số vận hành ở mức độ hợp lý.

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

## Phụ lục A: Danh mục thuật ngữ

This bảng chú giải toàn diện này cung cấp định nghĩa cho các thuật ngữ chủ chốt về AI, ML và an ninh được sử dụng xuyên suốt AISVS để đảm bảo sự rõ ràng và hiểu biết chung.

Ví dụ đối kháng: Một đầu vào được thiết kế có chủ đích để làm cho một mô hình AI mắc lỗi, thường bằng cách thêm các biến đổi tinh vi mà con người khó nhận thấy.
​
Adversarial Robustness – Độ bền adversarial trong AI đề cập đến khả năng của một mô hình duy trì hiệu suất và kháng lại việc bị lừa hoặc bị thao túng bởi các đầu vào được thiết kế có chủ ý, độc hại nhằm gây ra lỗi.
​
Tác nhân AI – Các tác nhân AI là các hệ thống phần mềm sử dụng AI để theo đuổi mục tiêu và thực hiện các nhiệm vụ thay cho người dùng. Chúng thể hiện khả năng suy luận, lập kế hoạch và trí nhớ, và có một mức độ tự chủ để đưa ra quyết định, học hỏi và thích nghi.
​
AI có tính chủ động: Các hệ thống AI có thể vận hành ở mức độ tự chủ nhất định để đạt được mục tiêu, thường đưa ra quyết định và thực hiện hành động mà không có sự can thiệp trực tiếp của con người.
​
Kiểm soát truy cập dựa trên thuộc tính (ABAC): một mô hình kiểm soát truy cập trong đó quyết định cấp phép dựa trên các thuộc tính của người dùng, tài nguyên, hành động và môi trường, được đánh giá tại thời điểm truy vấn.
​
Cuộc tấn công cửa hậu: Một loại tấn công đầu độc dữ liệu trong đó mô hình được huấn luyện để phản hồi theo một cách cụ thể đối với các kích hoạt nhất định trong khi hoạt động bình thường ở các trường hợp khác.
​
Độ lệch: Các sai số có hệ thống trong đầu ra của mô hình trí tuệ nhân tạo (AI) có thể dẫn đến kết quả không công bằng hoặc mang tính phân biệt đối xử đối với một số nhóm hoặc trong các ngữ cảnh cụ thể.
​
Khai thác thiên lệch: Một kỹ thuật tấn công tận dụng các thiên lệch được biết đến trong các mô hình AI để thao tác đầu ra hoặc kết quả.
​
Cedar: ngôn ngữ chính sách và động cơ thực thi của Amazon cho quyền truy cập chi tiết được sử dụng để triển khai ABAC cho hệ thống AI.
​
Chuỗi tư duy: một kỹ thuật nhằm cải thiện khả năng suy luận ở các mô hình ngôn ngữ bằng cách tạo ra các bước suy luận trung gian trước khi đưa ra câu trả lời cuối cùng.
​
Cầu dao ngắt mạch: Các cơ chế tự động ngừng hoạt động của hệ thống AI khi ngưỡng rủi ro cụ thể bị vượt quá.
​
Rò rỉ dữ liệu: Việc phơi bày ngoài ý muốn thông tin nhạy cảm thông qua đầu ra của mô hình AI hoặc hành vi.
​
Đầu độc dữ liệu: Việc cố ý làm hỏng dữ liệu huấn luyện để làm suy yếu tính toàn vẹn của mô hình, thường nhằm cài đặt cổng sau hoặc làm giảm hiệu suất.
​
Riêng tư vi phân – Riêng tư vi phân là một khuôn khổ toán học nghiêm ngặt để công bố thông tin thống kê về các tập dữ liệu đồng thời bảo vệ quyền riêng tư của các chủ thể dữ liệu cá nhân. Nó cho phép người nắm giữ dữ liệu chia sẻ các mẫu tổng hợp của nhóm trong khi giới hạn thông tin bị rò rỉ về từng cá nhân cụ thể.
​
Nhúng: Các biểu diễn vectơ đặc của dữ liệu (văn bản, hình ảnh, v.v.) nắm bắt ý nghĩa ngữ nghĩa trong một không gian có nhiều chiều.
​
Khả năng giải thích – Khả năng giải thích trong trí tuệ nhân tạo là khả năng của một hệ thống trí tuệ nhân tạo cung cấp các lý do có thể hiểu được bởi con người cho các quyết định và dự đoán của nó, đồng thời cung cấp cái nhìn sâu sắc về cách nó hoạt động nội tại.
​
Trí tuệ nhân tạo có thể giải thích (XAI): Các hệ thống trí tuệ nhân tạo được thiết kế để cung cấp các lời giải thích dễ hiểu cho các quyết định và hành vi của chúng thông qua nhiều kỹ thuật và khuôn khổ khác nhau.
​
Học liên kết phân tán: một phương pháp học máy trong đó các mô hình được huấn luyện trên nhiều thiết bị phi tập trung khác nhau chứa các mẫu dữ liệu cục bộ, mà không trao đổi dữ liệu với nhau.
​
Rào chắn: Các ràng buộc được triển khai để ngăn các hệ thống trí tuệ nhân tạo (AI) sinh ra các đầu ra gây hại, thiên vị hoặc không mong muốn khác.
​
Ảo giác – Ảo giác AI đề cập đến một hiện tượng mà một mô hình AI tạo ra thông tin không chính xác hoặc gây hiểu lầm, không dựa trên dữ liệu huấn luyện hoặc thực tế.
​
Con người ở vòng lặp (HITL): Các hệ thống được thiết kế để yêu cầu sự giám sát, xác minh hoặc can thiệp của con người tại các điểm quyết định quan trọng.
​
Cơ sở hạ tầng dưới dạng mã (IaC): Quản lý và cấp phát cơ sở hạ tầng thông qua mã thay vì các quy trình thủ công, cho phép quét bảo mật và triển khai nhất quán.
​
Phá khóa: Các kỹ thuật được sử dụng để vượt qua các rào chắn an toàn trong hệ thống AI, đặc biệt là trong các mô hình ngôn ngữ lớn, nhằm tạo ra nội dung bị cấm.
​
Nguyên tắc tối thiểu quyền truy cập: là nguyên tắc bảo mật cấp phát đúng các quyền truy cập tối thiểu cần thiết cho người dùng và các tiến trình.
​
LIME (Local Interpretable Model-agnostic Explanations): Một kỹ thuật để giải thích các dự đoán của bất kỳ bộ phân loại học máy nào bằng cách xấp xỉ nó ở phạm vi cục bộ bằng một mô hình có thể giải thích được.
​
Tấn công suy luận thành viên: Một cuộc tấn công nhằm xác định xem một điểm dữ liệu cụ thể có được sử dụng để huấn luyện một mô hình học máy hay không.
​
MITRE ATLAS: Cảnh đe dọa đối kháng cho Artificial-Intelligence Systems; một cơ sở tri thức về các chiến thuật và kỹ thuật đối kháng nhắm vào AI systems.
​
Model Card – Thẻ mô hình là một tài liệu cung cấp thông tin chuẩn hóa về hiệu suất, giới hạn, mục đích sử dụng và những cân nhắc đạo đức của một mô hình AI nhằm thúc đẩy tính minh bạch và phát triển AI có trách nhiệm.
​
Trích xuất mô hình: một cuộc tấn công trong đó kẻ tấn công liên tục truy vấn một mô hình mục tiêu để tạo ra một bản sao có chức năng tương tự mà không được phép.
​
Đảo ngược mô hình: một cuộc tấn công nhằm khôi phục dữ liệu huấn luyện bằng cách phân tích đầu ra của mô hình.
​
Quản lý vòng đời mô hình – Quản lý vòng đời mô hình AI là quá trình giám sát tất cả các giai đoạn tồn tại của một mô hình AI, bao gồm thiết kế, phát triển, triển khai, giám sát, bảo trì và sự nghỉ hưu cuối cùng, nhằm đảm bảo nó vẫn hoạt động hiệu quả và phù hợp với mục tiêu.
​
Đầu độc mô hình: Tạo ra các lỗ hổng hoặc cửa hậu trực tiếp vào một mô hình trong quá trình huấn luyện.
​
Đánh cắp mô hình: Lấy sao chép hoặc ước lượng của một mô hình độc quyền thông qua các truy vấn lặp lại.
​
Hệ thống đa tác nhân: một hệ thống được tạo thành từ nhiều tác nhân AI tương tác với nhau, mỗi tác nhân có thể có các khả năng và mục tiêu khác nhau.
​
OPA (Open Policy Agent): một động cơ thực thi chính sách nguồn mở cho phép thực thi chính sách thống nhất trên toàn bộ ngăn xếp.
​
Học máy bảo vệ quyền riêng tư (PPML): Các kỹ thuật và phương pháp để huấn luyện và triển khai các mô hình học máy trong khi bảo vệ quyền riêng tư của dữ liệu huấn luyện.
​
Tiêm prompt: Một cuộc tấn công trong đó các chỉ dẫn độc hại được nhúng vào đầu vào để vượt qua hành vi được dự định của mô hình.
​
RAG (Retrieval-Augmented Generation): một kỹ thuật nâng cao các mô hình ngôn ngữ lớn bằng cách truy xuất thông tin liên quan từ các nguồn kiến thức bên ngoài trước khi tạo ra một câu trả lời.
​
Đội đỏ (Red-Teaming): Là thực hành kiểm thử tích cực các hệ thống AI bằng cách mô phỏng các cuộc tấn công có chủ ý nhằm xác định các lỗ hổng.
​
SBOM (Danh sách thành phần phần mềm): Một hồ sơ chính thức chứa chi tiết và mối quan hệ chuỗi cung ứng của các thành phần khác nhau được sử dụng để xây dựng phần mềm hoặc các mô hình AI.
​
SHAP (SHapley Additive exPlanations): Một phương pháp dựa trên lý thuyết trò chơi để giải thích đầu ra của bất kỳ mô hình học máy nào bằng cách tính đóng góp của từng đặc trưng cho dự đoán.
​
Tấn công chuỗi cung ứng: Xâm phạm một hệ thống bằng cách nhắm vào các thành phần ít an toàn hơn trong chuỗi cung ứng của nó, chẳng hạn như thư viện bên thứ ba, tập dữ liệu, hoặc các mô hình được huấn luyện trước.
​
Học chuyển giao: Một kỹ thuật trong đó một mô hình được phát triển cho một nhiệm vụ ban đầu được tái sử dụng làm điểm khởi đầu cho một mô hình cho một nhiệm vụ thứ hai.
​
Cơ sở dữ liệu vector: Một cơ sở dữ liệu chuyên dụng được thiết kế để lưu trữ các vector có nhiều chiều (vector nhúng) và thực hiện các phép tìm kiếm theo độ tương đồng một cách hiệu quả.
​
Quét lỗ hổng bảo mật: Các công cụ tự động xác định các lỗ hổng bảo mật đã biết trong các thành phần phần mềm, bao gồm khung AI và các phụ thuộc.
​
Dấu nước: Các kỹ thuật nhúng dấu nước vô hình vào nội dung do AI tạo ra nhằm theo dõi nguồn gốc hoặc phát hiện nội dung được AI tạo ra.
​
Zero-Day Vulnerability: Một lỗ hổng chưa được biết đến trước đó mà kẻ tấn công có thể khai thác trước khi nhà phát triển tạo và triển khai bản vá.

## Phụ lục B: Tài liệu tham khảo

### TODO

## Phụ lục C: Quản trị An ninh Trí tuệ nhân tạo và Tài liệu

### Mục tiêu

Phụ lục này cung cấp các yêu cầu nền tảng để thiết lập cơ cấu tổ chức, chính sách và quy trình nhằm quản trị an ninh AI xuyên suốt vòng đời của hệ thống.

---

### AC.1 Áp dụng Khung quản lý rủi ro AI

Cung cấp một khuôn khổ chính thức để nhận diện, đánh giá và giảm thiểu các rủi ro đặc thù liên quan đến AI trong toàn bộ vòng đời của hệ thống.

 #AC.1.1    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng một phương pháp đánh giá rủi ro AI-specific được tài liệu hóa và triển khai.
 #AC.1.2    Cấp độ: 2    Vai trò: D
 Đảm bảo rằng các đánh giá rủi ro được thực hiện tại các mốc quan trọng trong vòng đời của trí tuệ nhân tạo và trước khi có những thay đổi đáng kể.
 #AC.1.3    Cấp độ: 3    Vai trò: D/V
 Xác nhận khung quản lý rủi ro phù hợp với các tiêu chuẩn đã được thiết lập (ví dụ: NIST AI RMF).

---

### AC.2 Chính sách An ninh AI và Quy trình

Định nghĩa và thực thi tiêu chuẩn tổ chức cho phát triển, triển khai và vận hành trí tuệ nhân tạo an toàn.

 #AC.2.1    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng các chính sách an ninh cho trí tuệ nhân tạo đã được ghi nhận là tồn tại.
 #AC.2.2    Cấp độ: 2    Vai trò: D
 Xác minh rằng các chính sách được xem xét và cập nhật ít nhất mỗi năm một lần và sau những thay đổi đáng kể về threat‑landscape.
 #AC.2.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các chính sách đáp ứng đầy đủ tất cả các danh mục AISVS và các yêu cầu quy định áp dụng.

---

### AC.3 Vai trò và Trách nhiệm đối với An ninh Trí tuệ nhân tạo (AI)

Thiết lập trách nhiệm giải trình rõ ràng cho bảo mật AI trên toàn tổ chức.

 #AC.3.1    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng các vai trò và trách nhiệm về bảo mật AI đã được ghi chép.
 #AC.3.2    Cấp độ: 2    Vai trò: D
 Xác minh rằng các cá nhân có trách nhiệm có đủ chuyên môn về an ninh.
 #AC.3.3    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng một ủy ban đạo đức AI hoặc hội đồng quản trị AI đã được thành lập cho các hệ thống AI có rủi ro cao.

---

### AC.4 Thực thi Hướng dẫn AI Đạo đức

Đảm bảo các hệ thống AI hoạt động theo các nguyên tắc đạo đức đã được thiết lập.

 #AC.4.1    Cấp độ: 1    Vai trò: D/V
 Xác nhận sự tồn tại của các nguyên tắc đạo đức đối với việc phát triển và triển khai AI.
 #AC.4.2    Cấp độ: 2    Vai trò: D
 Xác minh rằng các cơ chế được thiết lập để phát hiện và báo cáo các vi phạm đạo đức.
 #AC.4.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các đánh giá đạo đức định kỳ đối với các hệ thống AI đã triển khai được thực hiện.

---

### AC.5 Giám sát tuân thủ quy định AI

Duy trì nhận thức và tuân thủ các quy định về AI đang được cập nhật.

 #AC.5.1    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng có các quy trình để xác định các quy định áp dụng cho AI.
 #AC.5.2    Cấp độ: 2    Vai trò: D
 Xác nhận rằng việc tuân thủ tất cả các yêu cầu quy định được đánh giá.
 #AC.5.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các thay đổi quy định kích hoạt các cuộc rà soát và cập nhật kịp thời đối với các hệ thống AI.

### AC.6 Quản trị dữ liệu huấn luyện, Tài liệu và Quy trình

 #1.1.2    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng chỉ các tập dữ liệu đã được thẩm định về chất lượng, tính đại diện, nguồn gốc đạo đức và tuân thủ giấy phép mới được cho phép, nhằm giảm thiểu rủi ro đầu độc dữ liệu, thiên vị nhúng và vi phạm quyền sở hữu trí tuệ.
 #1.1.5    Cấp độ: 2    Vai trò: D/V
 Đảm bảo chất lượng gắn nhãn/chú thích thông qua kiểm tra chéo của người rà soát hoặc sự đồng thuận.
 #1.1.6    Cấp độ: 2    Vai trò: D/V
 Đảm bảo rằng "data cards" hoặc "datasheets for datasets" được duy trì cho các tập dữ liệu huấn luyện đáng kể, mô tả đặc tính, động cơ, thành phần, quy trình thu thập, tiền xử lý và các mục đích sử dụng được khuyến nghị/không khuyến nghị.
 #1.3.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các thiên vị được xác định đã được giảm thiểu thông qua các chiến lược được ghi nhận như cân bằng lại dữ liệu, gia tăng dữ liệu nhắm mục tiêu, điều chỉnh thuật toán (ví dụ: tiền xử lý, xử lý trong huấn luyện, xử lý sau huấn luyện), hoặc tái gán trọng số, và tác động của biện pháp giảm thiểu lên cả sự công bằng và hiệu suất tổng thể của mô hình được đánh giá.
 #1.3.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các chỉ số công bằng sau quá trình huấn luyện được đánh giá và được ghi lại.
 #1.3.4    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng một lifecycle bias-management policy chỉ định chủ sở hữu và tần suất xem xét.
 #1.4.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng chất lượng gắn nhãn được đảm bảo thông qua các hướng dẫn rõ ràng, kiểm tra chéo bởi người rà soát, cơ chế đồng thuận (ví dụ: theo dõi sự đồng thuận giữa các người gắn nhãn), và các quy trình được định nghĩa để giải quyết các khác biệt.
 #1.4.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các nhãn quan trọng đối với an toàn, bảo mật hoặc tính công bằng (ví dụ: nhận diện nội dung độc hại, phát hiện y tế quan trọng) được xem xét độc lập kép bắt buộc hoặc được xác thực mạnh mẽ tương đương.
 #1.4.6    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các hướng dẫn ghi nhãn và chỉ dẫn toàn diện, có kiểm soát phiên bản, và được đánh giá ngang hàng.
 #1.4.6    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các lược đồ dữ liệu cho nhãn được định nghĩa rõ ràng và được kiểm soát phiên bản.
 #1.3.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các tập dữ liệu được đánh giá về sự mất cân bằng đại diện và các thiên lệch có thể xảy ra trên các thuộc tính được pháp luật bảo vệ (ví dụ: chủng tộc, giới tính, tuổi tác) và các đặc tính nhạy cảm về mặt đạo đức khác liên quan đến lĩnh vực ứng dụng của mô hình (ví dụ: tình trạng kinh tế-xã hội, vị trí địa lý).
 #1.5.3    Cấp độ: 2    Vai trò: V
 Xác nhận rằng các kiểm tra ngẫu nhiên thủ công do các chuyên gia trong lĩnh vực thực hiện bao phủ một mẫu có ý nghĩa thống kê (ví dụ, ≥1% hoặc 1,000 mẫu, tùy cái nào lớn hơn, hoặc theo đánh giá rủi ro) nhằm phát hiện các vấn đề chất lượng tinh vi mà tự động hóa không bắt được.
 #1.8.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các quy trình gán nhãn được thuê ngoài hoặc crowdsourcingbao gồm các biện pháp bảo vệ kỹ thuật/quy trình để đảm bảo tính bảo mật dữ liệu, tính toàn vẹn, chất lượng nhãn và ngăn ngừa rò rỉ dữ liệu.
 #1.5.4    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các bước khắc phục được bổ sung vào hồ sơ nguồn gốc.
 #1.6.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các mẫu bị gắn cờ sẽ kích hoạt xem xét thủ công trước khi huấn luyện.
 #1.6.3    Cấp độ: 2    Vai trò: V
 Xác minh rằng kết quả được đưa vào hồ sơ bảo mật của mô hình và cung cấp thông tin cho tình báo về các mối đe dọa đang diễn ra.
 #1.6.4    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng logic phát hiện được cập nhật với thông tin tình báo về mối đe dọa mới.
 #1.6.5    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các pipeline học trực tuyến đang giám sát sự dịch chuyển phân phối.
 #1.7.1    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng các quy trình xóa dữ liệu đào tạo loại bỏ dữ liệu gốc và dữ liệu phát sinh và đánh giá tác động lên mô hình, và tác động đối với các mô hình bị ảnh hưởng được đánh giá và, nếu cần thiết, được xử lý (ví dụ thông qua tái huấn luyện hoặc hiệu chuẩn lại).
 #1.7.2    Cấp độ: 2    Vai trò: D
 Xác nhận rằng có các cơ chế để theo dõi và tôn trọng phạm vi và trạng thái đồng ý của người dùng (và việc rút lại đồng ý) đối với dữ liệu được sử dụng trong đào tạo, và sự đồng ý được xác thực trước khi dữ liệu được đưa vào các quá trình đào tạo mới hoặc các cập nhật mô hình đáng kể.
 #1.7.3    Cấp độ: 2    Vai trò: V
 Xác minh rằng các luồng làm việc được kiểm tra hàng năm và được ghi lại.
 #1.8.1    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng các nhà cung cấp dữ liệu bên thứ ba, bao gồm các nhà cung cấp mô hình được huấn luyện trước và các bộ dữ liệu bên ngoài, đã trải qua thẩm định về an ninh, quyền riêng tư, nguồn gốc có đạo đức và chất lượng dữ liệu trước khi dữ liệu hoặc mô hình của họ được tích hợp.
 #1.8.2    Cấp độ: 1    Vai trò: D
 Xác nhận rằng các chuyển khoản bên ngoài sử dụng TLS/xác thực và kiểm tra tính toàn vẹn.
 #1.8.3    Cấp độ: 2    Vai trò: D/V
 Đảm bảo rằng các nguồn dữ liệu có rủi ro cao (ví dụ, các tập dữ liệu nguồn mở có nguồn gốc chưa xác định, nhà cung cấp chưa được thẩm định) nhận được sự rà soát tăng cường, chẳng hạn như phân tích được cách ly trong sandbox, các kiểm tra chất lượng và sự thiên vị mở rộng, và phát hiện đầu độc dữ liệu nhắm mục tiêu, trước khi đưa vào sử dụng trong các ứng dụng nhạy cảm.
 #1.8.4    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng các mô hình được huấn luyện trước từ các bên thứ ba được đánh giá về thiên vị nhúng, các cửa hậu tiềm ẩn, tính toàn vẹn của kiến trúc của chúng, và nguồn gốc của dữ liệu đào tạo gốc của chúng trước khi tinh chỉnh hoặc triển khai.
 #1.5.3    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng nếu sử dụng đào tạo đối kháng, quá trình tạo ra, quản lý và phiên bản của các bộ dữ liệu đối kháng được ghi nhận và kiểm soát.
 #1.5.3    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng tác động của đào tạo kháng adversarial đối với hiệu suất của mô hình (đối với cả đầu vào sạch và đầu vào gây nhiễu) và các chỉ số công bằng được đánh giá, ghi nhận và giám sát.
 #1.5.4    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng các chiến lược về huấn luyện adversarial và độ bền được xem xét và cập nhật định kỳ để đối phó với các kỹ thuật tấn công adversarial ngày càng tinh vi.
 #1.4.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các bộ dữ liệu bị lỗi được cách ly kèm theo dấu vết kiểm toán.
 #1.4.3    Cấp độ: 2    Vai trò: D/V
 Đảm bảo rằng các cổng chất lượng chặn các tập dữ liệu kém chất lượng trừ khi có ngoại lệ được phê duyệt.
 #1.11.2    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng quá trình sinh dữ liệu, tham số và mục đích sử dụng dự định của dữ liệu tổng hợp đã được ghi lại.
 #1.11.3    Cấp độ: 2    Vai trò: D/V
 Đảm bảo dữ liệu tổng hợp được đánh giá rủi ro về thiên vị, rò rỉ dữ liệu cá nhân và các vấn đề đại diện trước khi sử dụng để huấn luyện.
 #1.12.3    Cấp độ: 2    Vai trò: D/V
 Kiểm tra xem các cảnh báo được tạo ra cho các sự kiện truy cập đáng ngờ và được điều tra kịp thời.
 #1.13.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các thời hạn lưu giữ rõ ràng được định nghĩa cho tất cả các tập dữ liệu huấn luyện.
 #1.13.2    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các tập dữ liệu tự động hết hạn, bị xóa, hoặc được xem xét để xóa vào cuối vòng đời của chúng.
 #1.13.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các hành động lưu giữ và xóa dữ liệu được ghi lại và có thể kiểm toán.
 #1.14.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các yêu cầu về nơi lưu trữ dữ liệu và chuyển giao xuyên biên giới được xác định và thực thi cho mọi tập dữ liệu.
 #1.14.2    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng các quy định mang tính ngành (ví dụ: chăm sóc sức khỏe, tài chính) được nhận diện và được áp dụng trong quá trình xử lý dữ liệu.
 #1.14.3    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng sự tuân thủ các luật bảo vệ quyền riêng tư liên quan (ví dụ: GDPR, CCPA) được tài liệu hóa và xem xét định kỳ.
 #1.16.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng tồn tại các cơ chế để đáp ứng các yêu cầu của chủ thể dữ liệu về quyền truy cập, chỉnh sửa, hạn chế hoặc phản đối.
 #1.16.2    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng các yêu cầu được ghi nhận, theo dõi và đáp ứng đúng thời hạn được quy định bởi pháp luật.
 #1.16.3    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng các quy trình quyền của chủ thể dữ liệu được kiểm tra và xem xét định kỳ để đảm bảo hiệu quả.
 #1.17.1    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng một phân tích tác động được thực hiện trước khi cập nhật hoặc thay thế một phiên bản tập dữ liệu, bao gồm hiệu suất mô hình, sự công bằng và tuân thủ.
 #1.17.2    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng kết quả của phân tích tác động đã được ghi nhận và được xem xét bởi các bên liên quan phù hợp.
 #1.17.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng có sẵn các kế hoạch quay lui trong trường hợp các phiên bản mới gây ra rủi ro hoặc lỗi hồi quy không thể chấp nhận được.
 #1.18.1    Cấp độ: 2    Vai trò: D/V
 Đảm bảo rằng tất cả nhân sự tham gia gán nhãn dữ liệu đã được kiểm tra lý lịch và được đào tạo về an ninh dữ liệu và quyền riêng tư.
 #1.18.2    Cấp độ: 2    Vai trò: D/V
 Xác nhận rằng tất cả nhân viên chú thích dữ liệu đã ký các thỏa thuận bảo mật và thỏa thuận không tiết lộ.
 #1.18.3    Cấp độ: 2    Vai trò: D/V
 Xác minh rằng các nền tảng chú thích thực thi kiểm soát truy cập và giám sát các mối đe dọa nội bộ.

#### Tài liệu tham khảo

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
ISO/IEC 23894:2023 — Artificial Intelligence — Guidance on Risk Management
EU Artificial Intelligence Act — Regulation (EU) 2024/1689
ISO/IEC 24029‑2:2023 — Robustness of Neural Networks — Methodology for Formal Methods

## Phụ lục D: Quản trị và xác thực lập trình an toàn được AI hỗ trợ

### Mục tiêu

Chương này định nghĩa các kiểm soát tổ chức cơ bản cho việc sử dụng an toàn và hiệu quả các công cụ viết mã được hỗ trợ bởi AI trong quá trình phát triển phần mềm, nhằm đảm bảo an ninh và tính truy vết xuyên suốt SDLC.

---

### AD.1 Quy trình Lập trình an toàn được AI hỗ trợ

Tích hợp các công cụ AI vào vòng đời phát triển phần mềm an toàn của tổ chức (SSDLC) mà không làm suy yếu các điểm kiểm tra bảo mật hiện có.

 #AD.1.1    Cấp độ: 1    Vai trò: D/V
 Đảm bảo rằng quy trình làm việc được tài liệu hóa mô tả khi nào và làm thế nào các công cụ AI có thể tạo mã nguồn, tái cấu trúc hoặc xem xét mã nguồn.
 #AD.1.2    Cấp độ: 2    Vai trò: D
 Xác minh rằng quy trình làm việc được ánh xạ tới từng giai đoạn của SSDLC (thiết kế, thực hiện, xem xét mã, kiểm thử, triển khai).
 #AD.1.3    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng các chỉ số được thu thập trên mã do AI tạo ra và so sánh với các chuẩn tham chiếu chỉ dựa trên con người.

---

### AD.2 Đánh giá Công cụ AI và Mô hình hóa mối đe dọa

Đảm bảo các công cụ lập trình AI được đánh giá về khả năng bảo mật, rủi ro và tác động của chuỗi cung ứng trước khi được áp dụng.

 #AD.2.1    Cấp độ: 1    Vai trò: D/V
 Đảm bảo rằng mô hình mối đe dọa cho từng công cụ AI xác định sự lạm dụng, tấn công đảo ngược mô hình, rò rỉ dữ liệu và rủi ro chuỗi phụ thuộc.
 #AD.2.2    Cấp độ: 2    Vai trò: D
 Xác nhận rằng các đánh giá công cụ bao gồm phân tích tĩnh/động của bất kỳ thành phần cục bộ nào và đánh giá các điểm cuối SaaS (TLS, xác thực/ủy quyền, ghi nhật ký).
 #AD.2.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các đánh giá tuân theo một khung công tác được công nhận và được thực hiện lại sau khi có các thay đổi ở phiên bản chính.

---

### AD.3 Quản lý lời nhắc và ngữ cảnh an toàn

Ngăn ngừa rò rỉ bí mật, mã nguồn độc quyền và dữ liệu cá nhân khi xây dựng các lời nhắc hoặc ngữ cảnh cho các mô hình trí tuệ nhân tạo.

 #AD.3.1    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng hướng dẫn bằng văn bản cấm gửi bí mật, thông tin xác thực hoặc dữ liệu được phân loại trong các prompt.
 #AD.3.2    Cấp độ: 2    Vai trò: D
 Xác minh rằng các biện pháp kiểm soát kỹ thuật (client‑side redaction, bộ lọc ngữ cảnh được phê duyệt) tự động loại bỏ các dấu vết nhạy cảm.
 #AD.3.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng các lời nhắc và phản hồi được token hóa, được mã hóa khi truyền và khi lưu trữ, và các thời hạn lưu giữ tuân thủ theo chính sách phân loại dữ liệu.

---

### AD.4 Đánh giá mã do AI tạo ra

Phát hiện và khắc phục các lỗ hổng do đầu ra AI gây ra trước khi mã được hợp nhất hoặc triển khai.

 #AD.4.1    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng mã do AI tạo ra luôn được rà soát bởi con người.
 #AD.4.2    Cấp độ: 2    Vai trò: D
 Xác minh rằng các trình quét tự động (SAST/IAST/DAST) chạy trên mọi pull request chứa mã do AI tạo ra và chặn việc hợp nhất khi có các phát hiện nghiêm trọng.
 #AD.4.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng kiểm thử fuzz khác biệt hoặc kiểm thử dựa trên đặc tính chứng minh các hành vi có tính bảo mật cao (ví dụ: kiểm tra tính hợp lệ của đầu vào, logic ủy quyền).

---

### AD.5 Khả năng giải thích và truy vết các đề xuất mã nguồn

Cung cấp cho kiểm toán viên và các nhà phát triển cái nhìn sâu sắc về lý do tại sao một đề xuất được đưa ra và nó đã phát triển như thế nào.

 #AD.5.1    Cấp độ: 1    Vai trò: D/V
 Xác nhận rằng các cặp prompt và phản hồi được ghi lại với các ID commit.
 #AD.5.2    Cấp độ: 2    Vai trò: D
 Xác nhận rằng các nhà phát triển có thể hiển thị các tham khảo từ mô hình (những đoạn trích huấn luyện, tài liệu) để hỗ trợ một gợi ý.
 #AD.5.3    Cấp độ: 3    Vai trò: D/V
 Xác nhận rằng các báo cáo giải thích được lưu trữ cùng với các tài liệu thiết kế và được tham chiếu trong các đánh giá bảo mật, đáp ứng các nguyên tắc truy vết của ISO/IEC 42001.

---

### AD.6 Phản hồi liên tục và tinh chỉnh mô hình

Cải thiện hiệu suất bảo mật của mô hình theo thời gian đồng thời ngăn ngừa sự lệch hướng tiêu cực.

 #AD.6.1    Cấp độ: 1    Vai trò: D/V
 Xác minh rằng các nhà phát triển có thể gắn cờ các gợi ý không an toàn hoặc không tuân thủ, và các cờ được theo dõi.
 #AD.6.2    Cấp độ: 2    Vai trò: D
 Đảm bảo rằng phản hồi được tổng hợp cung cấp thông tin cho việc tinh chỉnh định kỳ hoặc retrieval‑augmented generation với các tập dữ liệu về lập trình an toàn đã được kiểm chứng (ví dụ: OWASP Cheat Sheets).
 #AD.6.3    Cấp độ: 3    Vai trò: D/V
 Xác minh rằng một khung đánh giá vòng kín thực hiện các kiểm thử hồi quy sau mỗi lần tinh chỉnh; các chỉ số bảo mật phải đạt hoặc vượt qua điểm chuẩn trước đó trước khi triển khai.

---

#### Tài liệu tham khảo

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
OWASP Secure Coding Practices — Quick Reference Guide

## Phụ lục E: Các công cụ và khung công cụ ví dụ

### Mục tiêu

Chương này cung cấp các ví dụ về công cụ và khung công tác có thể hỗ trợ việc triển khai hoặc thực thi một yêu cầu AISVS nhất định. Những điều này không được xem là các khuyến nghị hoặc sự ủng hộ của nhóm AISVS hoặc Dự án Bảo mật GenAI OWASP.

---

### AE.1 Quản trị dữ liệu huấn luyện và Quản lý thiên kiến

Công cụ được sử dụng cho phân tích dữ liệu, quản trị dữ liệu và quản lý thiên vị.

 #AE.1.1    Phần: 1.1
 Công cụ kiểm kê dữ liệu: Các công cụ quản lý kiểm kê dữ liệu như...
 #AE.1.2    Phần: 1.2
 Mã-hóa-khi-truyền: Sử dụng TLS cho các ứng dụng dựa trên HTTPS, với các công cụ như OpenSSL và Python`ssl` thư viện.

---

### AE.2 Kiểm tra đầu vào của người dùng

Công cụ để xử lý và kiểm tra đầu vào của người dùng.

 #AE.2.1    Phần: 2.1
 Công cụ phòng thủ trước tiêm lệnh qua prompt: Sử dụng các công cụ guardrail như NeMo của NVIDIA hoặc Guardrails AI.

---

