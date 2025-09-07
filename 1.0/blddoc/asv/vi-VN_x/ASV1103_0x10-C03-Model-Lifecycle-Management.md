# Quản lý Vòng đời Mô hình C3 & Kiểm soát Thay đổi

## Mục tiêu Kiểm soát

Các hệ thống AI phải triển khai các quy trình kiểm soát thay đổi nhằm ngăn chặn các sửa đổi mô hình không được phép hoặc không an toàn tiếp cận môi trường sản xuất. Kiểm soát này đảm bảo tính toàn vẹn của mô hình trong suốt vòng đời—từ phát triển đến triển khai và đến khi ngừng sử dụng—giúp phản ứng nhanh với sự cố và duy trì trách nhiệm đối với tất cả các thay đổi.

Mục tiêu an ninh cốt lõi: Chỉ những mô hình được ủy quyền và xác thực mới được đưa vào sản xuất thông qua việc áp dụng các quy trình kiểm soát nhằm duy trì tính toàn vẹn, khả năng truy xuất và khả năng khôi phục.

---

## C3.1 Ủy quyền Mô hình & Tính toàn vẹn

Chỉ các mô hình được ủy quyền và có tính toàn vẹn đã được xác minh mới được đưa vào môi trường sản xuất.

|   #   | Mô tả                                                                                                                                                                                           | Cấp độ | Vai trò |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 3.1.1 | Xác minh rằng tất cả các tác phẩm của mô hình (trọng số, cấu hình, bộ mã hóa token) đều được ký số bởi các thực thể có thẩm quyền trước khi triển khai.                                         |   1    |   D/V   |
| 3.1.2 | Xác nhận rằng tính toàn vẹn của mô hình được xác thực vào thời điểm triển khai và việc xác minh chữ ký không thành công sẽ ngăn không cho tải mô hình.                                          |   1    |   D/V   |
| 3.1.3 | Xác minh rằng các hồ sơ nguồn gốc mô hình bao gồm định danh của thực thể ủy quyền, tổng kiểm tra dữ liệu đào tạo, kết quả kiểm thử xác nhận với trạng thái đạt/không đạt, và dấu thời gian tạo. |   2    |   D/V   |
| 3.1.4 | Xác nhận rằng tất cả các thành phần mô hình sử dụng phiên bản ngữ nghĩa (MAJOR.MINOR.PATCH) với các tiêu chí được ghi chép rõ ràng xác định khi nào mỗi thành phần phiên bản được tăng lên.     |   2    |   D/V   |
| 3.1.5 | Xác minh rằng việc theo dõi phụ thuộc duy trì một kho hàng theo thời gian thực cho phép xác định nhanh tất cả các hệ thống tiêu thụ.                                                            |   2    |    V    |

---

## C3.2 Xác nhận và Kiểm tra Mô hình

Các mô hình phải vượt qua các kiểm tra xác thực về bảo mật và an toàn đã được định nghĩa trước khi triển khai.

|   #   | Mô tả                                                                                                                                                                                               | Cấp độ | Vai trò |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 3.2.1 | Xác minh rằng các mô hình trải qua kiểm tra bảo mật tự động bao gồm xác thực đầu vào, làm sạch đầu ra và đánh giá an toàn với các ngưỡng đạt/không đạt đã được tổ chức đồng ý trước khi triển khai. |   1    |   D/V   |
| 3.2.2 | Xác nhận rằng các lỗi xác thực tự động chặn việc triển khai mô hình sau khi được chấp thuận ghi đè rõ ràng từ các nhân sự có thẩm quyền được chỉ định trước với các lý do kinh doanh được ghi chép. |   1    |   D/V   |
| 3.2.3 | Xác minh rằng kết quả kiểm tra được ký mật mã và liên kết không thể thay đổi với hàm băm phiên bản mô hình cụ thể đang được xác thực.                                                               |   2    |    V    |
| 3.2.4 | Xác minh rằng các đợt triển khai khẩn cấp yêu cầu đánh giá rủi ro bảo mật được ghi chép và sự phê duyệt từ một cơ quan bảo mật được chỉ định trước trong khoảng thời gian đã thỏa thuận trước.      |   2    |   D/V   |

---

## C3.3 Triển khai kiểm soát & Quay lại

Việc triển khai mô hình phải được kiểm soát, giám sát và có thể đảo ngược.

|   #   | Mô tả                                                                                                                                                                                                                                                     | Cấp độ | Vai trò |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 3.3.1 | Xác minh rằng các triển khai sản xuất thực hiện các cơ chế triển khai dần (triển khai canary, triển khai xanh-lục) với các cơ chế kích hoạt tự động để quay lại dựa trên các tỷ lệ lỗi, ngưỡng độ trễ hoặc tiêu chí cảnh báo bảo mật đã thỏa thuận trước. |   1    |    D    |
| 3.3.2 | Xác minh rằng khả năng hoàn tác khôi phục trạng thái mô hình hoàn chỉnh (trọng số, cấu hình, phụ thuộc) một cách nguyên tử trong các khung thời gian tổ chức đã được định trước.                                                                          |   1    |   D/V   |
| 3.3.3 | Xác minh rằng các quy trình triển khai kiểm tra tính hợp lệ của chữ ký mã hóa và tính toán các tổng kiểm tra tính toàn vẹn trước khi kích hoạt mô hình, và hủy bỏ việc triển khai nếu có bất kỳ sự không khớp nào.                                        |   2    |   D/V   |
| 3.3.4 | Xác minh rằng khả năng tắt mô hình khẩn cấp có thể vô hiệu hóa các điểm cuối mô hình trong thời gian phản hồi được định trước thông qua bộ ngắt mạch tự động hoặc công tắc tắt thủ công.                                                                  |   2    |   D/V   |
| 3.3.5 | Xác minh rằng các hiện vật phục hồi (các phiên bản mô hình trước đó, cấu hình, phụ thuộc) được lưu giữ theo chính sách của tổ chức với bộ nhớ không thể thay đổi để phản ứng sự cố.                                                                       |   2    |    V    |

---

## C3.4 Thay đổi Trách nhiệm và Kiểm toán

Tất cả các thay đổi trong vòng đời mô hình phải có khả năng truy vết và kiểm toán.

|   #   | Mô tả                                                                                                                                                                                                                        | Cấp độ | Vai trò |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 3.4.1 | Xác minh rằng tất cả các thay đổi mô hình (triển khai, cấu hình, ngừng sử dụng) tạo ra các bản ghi kiểm tra không thể thay đổi bao gồm dấu thời gian, danh tính tác nhân đã xác thực, loại thay đổi và trạng thái trước/sau. |   1    |    V    |
| 3.4.2 | Xác minh rằng việc truy cập nhật ký kiểm toán yêu cầu có sự ủy quyền thích hợp và tất cả các lần cố gắng truy cập đều được ghi lại với danh tính người dùng và dấu thời gian.                                                |   2    |   D/V   |
| 3.4.3 | Xác nhận rằng các mẫu prompt và tin nhắn hệ thống được quản lý phiên bản trong các kho git với việc duyệt mã bắt buộc và phê duyệt từ các người đánh giá được chỉ định trước khi triển khai.                                 |   2    |   D/V   |
| 3.4.4 | Xác minh rằng các bản ghi kiểm toán bao gồm đủ chi tiết (băm mô hình, ảnh chụp cấu hình, phiên bản phụ thuộc) để cho phép tái tạo đầy đủ trạng thái mô hình cho bất kỳ mốc thời gian nào trong khoảng thời gian lưu trữ.     |   2    |    V    |

---

## C3.5 Các Thực Tiễn Phát Triển An Toàn

Quy trình phát triển và đào tạo mô hình phải tuân theo các phương pháp bảo mật để ngăn ngừa việc bị xâm phạm.

|   #   | Mô tả                                                                                                                                                                                                                             | Cấp độ | Vai trò |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 3.5.1 | Xác minh rằng các môi trường phát triển mô hình, kiểm thử và sản xuất được tách biệt về mặt vật lý hoặc logic. Chúng không dùng chung cơ sở hạ tầng, có kiểm soát truy cập riêng biệt và lưu trữ dữ liệu cách ly.                 |   1    |    D    |
| 3.5.2 | Xác minh rằng việc huấn luyện mô hình và điều chỉnh tinh xảy ra trong các môi trường riêng biệt với quyền truy cập mạng được kiểm soát.                                                                                           |   1    |    D    |
| 3.5.3 | Xác minh rằng các nguồn dữ liệu huấn luyện được kiểm tra tính toàn vẹn và xác thực thông qua các nguồn tin cậy với chuỗi bảo quản được ghi chép đầy đủ trước khi sử dụng trong phát triển mô hình.                                |   1    |   D/V   |
| 3.5.4 | Xác minh rằng các tài liệu phát triển mô hình (siêu tham số, kịch bản đào tạo, tệp cấu hình) được lưu trữ trong hệ thống kiểm soát phiên bản và yêu cầu phê duyệt đánh giá đồng nghiệp trước khi sử dụng trong quá trình đào tạo. |   2    |    D    |

---

## C3.6 Nghỉ hưu & Ngừng sử dụng Mô hình

Các mô hình phải được loại bỏ một cách an toàn khi chúng không còn cần thiết hoặc khi các vấn đề về bảo mật được phát hiện.

|   #   | Mô tả                                                                                                                                                                                                                                         | Cấp độ | Vai trò |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 3.6.1 | Xác minh rằng các quy trình ngừng sử dụng mô hình tự động quét các đồ thị phụ thuộc, xác định tất cả các hệ thống tiêu thụ, và cung cấp các khoảng thời gian thông báo trước đã được thỏa thuận trước khi ngừng hoạt động.                    |   1    |    D    |
| 3.6.2 | Xác minh rằng các hiện vật mô hình đã nghỉ hưu được xoá an toàn bằng phương pháp xoá mật mã hoặc ghi đè nhiều lần theo các chính sách lưu giữ dữ liệu đã được tài liệu hoá cùng với các chứng chỉ xác nhận việc huỷ.                          |   1    |   D/V   |
| 3.6.3 | Xác minh rằng các sự kiện nghỉ hưu mô hình được ghi lại với dấu thời gian và danh tính người thực hiện, đồng thời chữ ký mô hình bị thu hồi để ngăn chặn tái sử dụng.                                                                         |   2    |    V    |
| 3.6.4 | Xác minh rằng việc nghỉ hưu mô hình khẩn cấp có thể vô hiệu hóa quyền truy cập mô hình trong khoảng thời gian phản ứng khẩn cấp đã được thiết lập trước thông qua các công tắc tắt tự động nếu phát hiện ra các lỗ hổng bảo mật nghiêm trọng. |   2    |   D/V   |

---

## Tài liệu tham khảo

* [MLOps Principles](https://ml-ops.org/content/mlops-principles)
* [Securing AI/ML Ops – Cisco.com](https://sec.cloudapps.cisco.com/security/center/resources/SecuringAIMLOps)
* [Audit logs security: cryptographically signed tamper-proof logs](https://www.cossacklabs.com/blog/audit-logs-security/)
* [Machine Learning Model Versioning: Top Tools & Best Practices](https://lakefs.io/blog/model-versioning/)
* [AI Hygiene Starts with Models and Data Loaders – SEI Blog](https://insights.sei.cmu.edu/documents/6190/AI-Hygiene-Starts-with-Models-and-Data-Loaders_1G0KTRh.pdf)
* [How to handle versioning and rollback of a deployed ML model?](https://learn.microsoft.com/en-au/answers/questions/1845378/how-to-handle-versioning-and-rollback-of-a-deploye)
* [Reinforcement fine-tuning – OpenAI API](https://platform.openai.com/docs/guides/reinforcement-fine-tuning)
* [Auditing Machine Learning models: Governance, Data Security and …](https://www.linkedin.com/pulse/auditing-machine-learning-models-governance-data-security-negrete-yn81f)
* [Adversarial Training to Improve Model Robustness](https://medium.com/%40amit25173/adversarial-training-to-improve-model-robustness-5e285b516713)
* [What is AI adversarial robustness? – IBM Research](https://research.ibm.com/blog/securing-ai-workflows-with-adversarial-robustness)
* [Exploring Data Provenance: Ensuring Data Integrity and Authenticity](https://www.astera.com/type/blog/data-provenance/)
* [MITRE ATLAS](https://atlas.mitre.org/)
* [AWS Prescriptive Guidance – Best practices for retiring applications …](https://docs.aws.amazon.com/pdfs/prescriptive-guidance/latest/migration-app-retirement-best-practices/migration-app-retirement-best-practices.pdf)

