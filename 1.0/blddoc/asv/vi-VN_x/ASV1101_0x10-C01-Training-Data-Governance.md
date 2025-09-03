# C1 Quản trị dữ liệu huấn luyện và quản lý thiên lệch

## Mục tiêu kiểm soát

Dữ liệu huấn luyện phải được thu thập từ nguồn, xử lý và bảo quản theo cách bảo toàn nguồn gốc, an toàn, chất lượng và công bằng. Việc này đáp ứng các nghĩa vụ pháp lý và giảm thiểu rủi ro về thiên vị, nhiễm độc dữ liệu hoặc vi phạm quyền riêng tư có thể phát sinh trong quá trình huấn luyện và có thể ảnh hưởng đến toàn bộ vòng đời của AI.

---

## C1.1 Nguồn gốc dữ liệu huấn luyện

Duy trì một danh mục kiểm kê có thể xác minh được cho tất cả các tập dữ liệu, chỉ chấp nhận các nguồn đáng tin cậy, và ghi lại mọi thay đổi để đảm bảo khả năng kiểm toán.

|   #   | Mô tả                                                                                                                                                                                                    | Cấp độ | Vai trò |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 1.1.1 | Xác nhận rằng một danh mục cập nhật về mọi nguồn dữ liệu đào tạo (nguồn gốc, người quản lý/chủ sở hữu, giấy phép, phương pháp thu thập, các hạn chế về mục đích sử dụng, và lịch sử xử lý) được duy trì. |   1    |   D/V   |
| 1.1.2 | Xác minh rằng quá trình xử lý dữ liệu đào tạo loại bỏ các đặc trưng, thuộc tính hoặc trường không cần thiết (ví dụ: siêu dữ liệu không sử dụng, PII nhạy cảm, dữ liệu kiểm tra bị rò rỉ).                |   1    |   D/V   |
| 1.1.3 | Xác minh rằng mọi thay đổi đối với bộ dữ liệu đều phải được phê duyệt thông qua một quy trình có ghi nhận log.                                                                                           |   2    |   D/V   |
| 1.1.4 | Xác minh xem bộ dữ liệu hoặc các tập con có được dán watermark hoặc gắn dấu vân tay khi có thể.                                                                                                          |   3    |   D/V   |

---

## C1.2 Bảo mật và tính toàn vẹn của dữ liệu huấn luyện

Hạn chế quyền truy cập vào dữ liệu huấn luyện, mã hóa dữ liệu khi lưu trữ và khi truyền, và xác thực tính toàn vẹn của nó để ngăn chặn việc sửa đổi trái phép, trộm cắp dữ liệu hoặc đầu độc dữ liệu.

|   #   | Mô tả                                                                                                                                                                                                    | Cấp độ | Vai trò |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 1.2.1 | Xác nhận rằng các biện pháp kiểm soát truy cập bảo vệ lưu trữ dữ liệu đào tạo và các pipeline.                                                                                                           |   1    |   D/V   |
| 1.2.2 | Xác minh rằng mọi truy cập vào dữ liệu huấn luyện được ghi lại, bao gồm người dùng, thời gian và hành động.                                                                                              |   2    |   D/V   |
| 1.2.3 | Đảm bảo rằng các tập dữ liệu đào tạo được mã hóa trong quá trình truyền và khi lưu trữ, bằng các thuật toán mật mã tiêu chuẩn của ngành và các thực hành quản trị khóa.                                  |   2    |   D/V   |
| 1.2.4 | Xác minh rằng các hàm băm mật mã hoặc chữ ký số được sử dụng để đảm bảo tính toàn vẹn của dữ liệu trong quá trình lưu trữ và truyền tải dữ liệu huấn luyện.                                              |   2    |   D/V   |
| 1.2.5 | Xác minh rằng các kỹ thuật phát hiện tự động được áp dụng để ngăn chặn các sửa đổi trái phép hoặc làm hỏng dữ liệu huấn luyện.                                                                           |   2    |   D/V   |
| 1.2.6 | Xác minh rằng dữ liệu huấn luyện đã lỗi thời được xóa sạch một cách an toàn hoặc được ẩn danh.                                                                                                           |   2    |   D/V   |
| 1.2.7 | Xác minh rằng mọi phiên bản của tập dữ liệu huấn luyện đều được nhận dạng một cách duy nhất, được lưu trữ một cách bất biến và có thể kiểm toán để hỗ trợ quay lại trạng thái trước và phân tích pháp y. |   3    |   D/V   |

---

## C1.3 Chất lượng gán nhãn dữ liệu đào tạo, tính toàn vẹn và bảo mật

Bảo vệ nhãn và yêu cầu xem xét kỹ thuật cho dữ liệu quan trọng.

|   #   | Mô tả                                                                                                                                                                                                                     | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 1.3.1 | Xác minh rằng các hàm băm mật mã hoặc chữ ký số được áp dụng cho các artefact được gắn nhãn để đảm bảo tính toàn vẹn và xác thực của chúng.                                                                               |   2    |   D/V   |
| 1.3.2 | Xác minh rằng các giao diện và nền tảng gắn nhãn thực thi các biện pháp kiểm soát truy cập mạnh, duy trì nhật ký kiểm tra có khả năng phát hiện giả mạo cho mọi hoạt động gắn nhãn, và bảo vệ khỏi các sửa đổi trái phép. |   2    |   D/V   |
| 1.3.3 | Xác minh rằng thông tin nhạy cảm trong nhãn được che giấu, ẩn danh hoặc mã hóa ở cấp trường dữ liệu khi lưu trữ và khi truyền.                                                                                            |   3    |   D/V   |

---

## C1.4 Chất lượng dữ liệu đào tạo và bảo mật

Kết hợp xác thực tự động, kiểm tra ngẫu nhiên thủ công và biện pháp khắc phục được ghi lại để đảm bảo độ tin cậy của tập dữ liệu.

|   #   | Mô tả                                                                                                                                                                                                                                                                                                                                                                                                      | Cấp độ | Vai trò |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 1.4.1 | Xác nhận rằng các bài kiểm tra tự động bắt được lỗi định dạng và các giá trị null ở mọi lần nhập dữ liệu hoặc biến đổi dữ liệu có ý nghĩa.                                                                                                                                                                                                                                                                 |   1    |    D    |
| 1.4.2 | Xác nhận rằng các pipeline huấn luyện và tinh chỉnh LLM triển khai phát hiện đầu độc dữ liệu và xác thực tính toàn vẹn dữ liệu (ví dụ: phương pháp thống kê, phát hiện ngoại lệ, phân tích nhúng) để nhận diện các cuộc tấn công đầu độc có tiềm năng (ví dụ: tráo nhãn, chèn kích hoạt cửa hậu, lệnh đổi vai trò, các mẫu có ảnh hưởng lớn) hoặc sự cố dữ liệu vô tình làm hỏng trong dữ liệu huấn luyện. |   2    |   D/V   |
| 1.4.3 | Đảm bảo rằng các biện pháp phòng thủ phù hợp, chẳng hạn như huấn luyện đối kháng (sử dụng các ví dụ đối kháng được tạo ra), gia tăng dữ liệu với các đầu vào bị nhiễu, hoặc các kỹ thuật tối ưu hóa mạnh, đã được triển khai và điều chỉnh cho các mô hình liên quan dựa trên đánh giá rủi ro.                                                                                                             |   3    |   D/V   |
| 1.4.4 | Xác minh rằng các nhãn được tự động tạo ra (ví dụ, thông qua Mô hình ngôn ngữ lớn (LLMs) hoặc giám sát yếu) phải tuân thủ ngưỡng tin cậy và các kiểm tra tính nhất quán để phát hiện nhãn ảo, nhãn gây hiểu lầm hoặc nhãn có độ tin cậy thấp.                                                                                                                                                              |   2    |   D/V   |
| 1.4.5 | Xác minh rằng các bài kiểm tra tự động bắt được sự lệch nhãn ở mọi lần nạp dữ liệu hoặc các chuyển đổi dữ liệu quan trọng.                                                                                                                                                                                                                                                                                 |   3    |    D    |

---

## C1.5 Nguồn gốc dữ liệu và khả năng truy vết

Theo dõi toàn bộ hành trình của từng điểm dữ liệu từ nguồn đến đầu vào của mô hình để đảm bảo khả năng kiểm toán và ứng phó sự cố.

|   #   | Mô tả                                                                                                                                                                                                                                                                     | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 1.5.1 | Xác minh rằng dòng dõi của mỗi điểm dữ liệu, bao gồm tất cả biến đổi, gia tăng dữ liệu và hợp nhất, được ghi lại và có thể tái tạo.                                                                                                                                       |   2    |   D/V   |
| 1.5.2 | Xác minh rằng hồ sơ nguồn dữ liệu bất biến, được lưu trữ an toàn và có thể truy cập được để kiểm toán.                                                                                                                                                                    |   2    |   D/V   |
| 1.5.3 | Xác nhận rằng việc theo dõi nguồn gốc dữ liệu bao gồm dữ liệu tổng hợp được tạo ra bằng các kỹ thuật bảo vệ quyền riêng tư hoặc kỹ thuật sinh dữ liệu, và tất cả dữ liệu tổng hợp được gắn nhãn rõ ràng và phân biệt với dữ liệu thực trong suốt toàn bộ quy trình xử lý. |   2    |   D/V   |

---

## Tài liệu tham khảo

* [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
* [EU AI Act – Article 10: Data & Data Governance](https://artificialintelligenceact.eu/article/10/)
* [MITRE ATLAS: Adversary Tactics for AI](https://atlas.mitre.org/)
* [Survey of ML Bias Mitigation Techniques – MDPI](https://www.mdpi.com/2673-6470/4/1/1)
* [Data Provenance & Lineage Best Practices – Nightfall AI](https://www.nightfall.ai/ai-security-101/data-provenance-and-lineage)
* [Data Labeling Quality Standards – LabelYourData](https://labelyourdata.com/articles/data-labeling-quality-and-how-to-measure-it)
* [Training Data Poisoning Guide – Lakera.ai](https://www.lakera.ai/blog/training-data-poisoning)
* [CISA Advisory: Securing Data for AI Systems](https://www.cisa.gov/news-events/cybersecurity-advisories/aa25-142a)
* [ISO/IEC 23053: AI Management Systems Framework](https://www.iso.org/sectors/it-technologies/ai)
* [IBM: What is AI Governance?](https://www.ibm.com/think/topics/ai-governance)
* [Google AI Principles](https://ai.google/principles/)
* [GDPR & AI Training Data – DataProtectionReport](https://www.dataprotectionreport.com/2024/08/recent-regulatory-developments-in-training-artificial-intelligence-ai-models-under-the-gdpr/)
* [Supply-Chain Security for AI Data – AppSOC](https://www.appsoc.com/blog/ai-is-the-new-frontier-of-supply-chain-security)
* [OpenAI Privacy Center – Data Deletion Controls](https://privacy.openai.com/policies?modal=take-control)
* [Adversarial ML Dataset – Kaggle](https://www.kaggle.com/datasets/cnrieiit/adversarial-machine-learning-dataset)

