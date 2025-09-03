# Quản lý vòng đời mô hình C3 và Kiểm soát thay đổi

## Mục tiêu kiểm soát

Hệ thống AI phải triển khai các quy trình kiểm soát thay đổi nhằm ngăn chặn các chỉnh sửa mô hình trái phép hoặc không an toàn được đưa vào sản xuất. Quy trình kiểm soát này đảm bảo tính toàn vẹn của mô hình trong suốt vòng đời--từ phát triển đến triển khai và ngừng sử dụng--giúp phản ứng nhanh với sự cố và duy trì trách nhiệm giải trình cho mọi thay đổi.

Mục tiêu an ninh cốt lõi: Chỉ các mô hình được cấp phép và xác thực mới được đưa vào sản xuất bằng cách áp dụng các quy trình có kiểm soát nhằm duy trì tính toàn vẹn, khả năng truy vết và khả năng khôi phục.

---

## C3.1 Ủy quyền và Tính toàn vẹn của Mô hình

Chỉ các mô hình được ủy quyền và có tính toàn vẹn đã được xác thực mới được đưa vào môi trường sản xuất.

|   #   | Mô tả                                                                                                                                                                                                   | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 3.1.1 | Xác minh rằng tất cả các tài sản mô hình (trọng số, cấu hình, tokenizer) được ký số bằng chữ ký số bởi các thực thể có thẩm quyền trước khi triển khai.                                                 |   1    |   D/V   |
| 3.1.2 | Xác minh tính toàn vẹn của mô hình được thực hiện tại thời điểm triển khai và các lỗi xác thực chữ ký ngăn chặn việc tải mô hình.                                                                       |   1    |   D/V   |
| 3.1.3 | Xác minh rằng các bản ghi nguồn gốc của mô hình bao gồm nhận diện của thực thể ủy quyền, các giá trị băm của dữ liệu đào tạo, kết quả kiểm thử xác thực với trạng thái đạt/không đạt, và thời điểm tạo. |   2    |   D/V   |
| 3.1.4 | Xác minh rằng tất cả các artefact của mô hình tuân thủ semantic versioning (MAJOR.MINOR.PATCH) với các tiêu chí được ghi nhận chỉ rõ khi nào mỗi thành phần phiên bản được tăng.                        |   2    |   D/V   |
| 3.1.5 | Xác nhận rằng việc theo dõi phụ thuộc duy trì một danh mục tồn kho theo thời gian thực, cho phép nhận diện nhanh chóng tất cả các hệ thống tiêu thụ.                                                    |   2    |    V    |

---

## C3.2 Xác nhận và kiểm thử mô hình

Các mô hình phải vượt qua các kiểm tra bảo mật và an toàn được định nghĩa trước khi triển khai.

|   #   | Mô tả                                                                                                                                                                                                                    | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 3.2.1 | Đảm bảo rằng các mô hình trải qua kiểm tra bảo mật tự động bao gồm xác thực đầu vào, làm sạch đầu ra và đánh giá an toàn với các ngưỡng đạt/không đạt đã được thỏa thuận trước bởi tổ chức, trước khi triển khai.        |   1    |   D/V   |
| 3.2.2 | Xác nhận rằng các thất bại trong thẩm định tự động chặn việc triển khai mô hình sau khi có sự phê duyệt ngoại lệ rõ ràng từ các nhân sự được ủy quyền trước được chỉ định, kèm theo các căn cứ kinh doanh được ghi nhận. |   1    |   D/V   |
| 3.2.3 | Xác minh rằng kết quả thử nghiệm được ký bằng chữ ký số và liên kết bất biến với hash của phiên bản mô hình cụ thể đang được xác thực.                                                                                   |   2    |    V    |
| 3.2.4 | Xác nhận rằng các triển khai khẩn cấp đòi hỏi đánh giá rủi ro an ninh được ghi nhận bằng văn bản và phê duyệt từ một cơ quan an ninh được chỉ định trước trong khung thời gian đã thỏa thuận.                            |   2    |   D/V   |

---

## C3.3 Triển khai có kiểm soát và phục hồi

Việc triển khai mô hình phải được kiểm soát, được giám sát và có thể đảo ngược.

|   #   | Mô tả                                                                                                                                                                                                                                                           | Cấp độ | Vai trò |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 3.3.1 | Xác minh rằng các triển khai ở môi trường sản xuất đã áp dụng các cơ chế triển khai dần (triển khai canary, triển khai xanh-đỏ) và có các kích hoạt tự động quay lại dựa trên các tỉ lệ lỗi đã thỏa thuận trước, ngưỡng độ trễ, hoặc tiêu chí cảnh báo bảo mật. |   1    |    D    |
| 3.3.2 | Xác nhận rằng khả năng rollback sẽ khôi phục đầy đủ trạng thái của mô hình (các trọng số, các cấu hình, các phụ thuộc) một cách nguyên tử trong các khung thời gian do tổ chức xác định trước.                                                                  |   1    |   D/V   |
| 3.3.3 | Xác minh rằng các quy trình triển khai xác thực chữ ký mật mã và tính toán chuỗi kiểm tra tính toàn vẹn trước khi kích hoạt mô hình, và từ chối triển khai khi phát hiện bất kỳ sự không khớp nào.                                                              |   2    |   D/V   |
| 3.3.4 | Xác minh rằng khả năng tắt mô hình khẩn cấp có thể vô hiệu hóa các điểm cuối của mô hình trong thời gian đáp ứng được xác định trước, thông qua các cầu dao ngắt mạch tự động hoặc công tắc tắt khẩn cấp bằng tay.                                              |   2    |   D/V   |
| 3.3.5 | Xác minh rằng các tài sản rollback (các phiên bản mô hình trước đây, các cấu hình, các phụ thuộc) được lưu giữ theo chính sách của tổ chức với lưu trữ bất biến để ứng phó sự cố.                                                                               |   2    |    V    |

---

## C3.4 Trách nhiệm giải trình và Kiểm toán thay đổi

Tất cả các thay đổi trong vòng đời của mô hình phải được truy vết và có thể kiểm toán.

|   #   | Mô tả                                                                                                                                                                                                                                              | Cấp độ | Vai trò |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 3.4.1 | Đảm bảo rằng mọi thay đổi đối với mô hình (triển khai, cấu hình, ngừng sử dụng) đều tạo ra các bản ghi kiểm toán bất biến, bao gồm dấu thời gian, danh tính tác nhân được xác thực, loại thay đổi và trạng thái trước/sau.                         |   1    |    V    |
| 3.4.2 | Xác minh rằng việc truy cập nhật ký kiểm toán đòi hỏi ủy quyền phù hợp và mọi lần truy cập đều được ghi lại với danh tính người dùng và một dấu thời gian.                                                                                         |   2    |   D/V   |
| 3.4.3 | Xác minh rằng các mẫu prompt và thông điệp hệ thống được kiểm soát phiên bản trong các kho git với việc rà soát mã nguồn bắt buộc và phê duyệt từ các người rà soát được chỉ định trước khi triển khai.                                            |   2    |   D/V   |
| 3.4.4 | Xác minh rằng các bản ghi kiểm toán có đủ chi tiết (các giá trị băm của mô hình, các bản sao cấu hình, phiên bản của các phụ thuộc) để cho phép tái tạo đầy đủ trạng thái của mô hình cho bất kỳ dấu thời gian nào trong khoảng thời gian lưu giữ. |   2    |    V    |

---

## C3.5 Các thực hành Phát triển Bảo mật

Quá trình phát triển và huấn luyện mô hình phải tuân thủ các thực hành bảo mật để ngăn ngừa sự xâm phạm.

|   #   | Mô tả                                                                                                                                                                                                                             | Cấp độ | Vai trò |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 3.5.1 | Xác nhận rằng các môi trường phát triển mô hình, thử nghiệm và sản xuất được phân tách về mặt vật lý hoặc logic. Chúng không có cơ sở hạ tầng chung, có các kiểm soát truy cập riêng biệt và các kho dữ liệu được cô lập.         |   1    |    D    |
| 3.5.2 | Xác minh rằng quá trình huấn luyện và tinh chỉnh mô hình diễn ra trong các môi trường cô lập với quyền truy cập mạng được kiểm soát.                                                                                              |   1    |    D    |
| 3.5.3 | Xác nhận rằng các nguồn dữ liệu đào tạo được xác thực thông qua các kiểm tra tính toàn vẹn và được chứng thực từ các nguồn đáng tin cậy với chuỗi lưu giữ được ghi nhận trước khi sử dụng trong phát triển mô hình.               |   1    |   D/V   |
| 3.5.4 | Đảm bảo rằng các tài sản phát triển mô hình (siêu tham số, các script huấn luyện, các tệp cấu hình) được lưu trữ trong hệ thống kiểm soát phiên bản và yêu cầu phê duyệt của đồng nghiệp trước khi được sử dụng trong huấn luyện. |   2    |    D    |

---

## C3.6 Kết thúc vòng đời mô hình & khai tử

Các mô hình phải được ngừng sử dụng một cách an toàn khi chúng không còn cần thiết hoặc khi phát hiện các vấn đề về bảo mật.

|   #   | Mô tả                                                                                                                                                                                                                                                     | Cấp độ | Vai trò |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 3.6.1 | Xác minh rằng các quy trình ngừng sử dụng mô hình tự động quét đồ thị phụ thuộc, xác định tất cả các hệ thống đang sử dụng và cung cấp các khoảng thời gian thông báo trước đã được thỏa thuận trước khi ngừng vận hành.                                  |   1    |    D    |
| 3.6.2 | Xác minh rằng các artefact của mô hình đã ngừng sử dụng được xóa an toàn bằng xóa bằng mã hóa bảo mật hoặc ghi đè nhiều lần theo các chính sách lưu giữ dữ liệu được ghi nhận kèm theo các chứng chỉ tiêu hủy được xác nhận.                              |   1    |   D/V   |
| 3.6.3 | Xác minh rằng các sự kiện ngừng sử dụng mô hình được ghi lại với dấu thời gian và danh tính của người thực hiện, và chữ ký số của mô hình được thu hồi để ngăn chặn việc tái sử dụng.                                                                     |   2    |    V    |
| 3.6.4 | Xác minh rằng việc ngừng hoạt động mô hình khẩn cấp có thể vô hiệu hóa quyền truy cập vào mô hình trong khung thời gian ứng phó khẩn cấp đã được thiết lập trước thông qua các công tắc ngắt khẩn cấp tự động nếu phát hiện lỗ hổng bảo mật nghiêm trọng. |   2    |   D/V   |

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

