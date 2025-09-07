# Quản lý Dữ liệu Đào tạo C1 & Quản lý Định kiến

## Mục tiêu Kiểm soát

Dữ liệu đào tạo phải được lấy nguồn, xử lý và duy trì theo cách bảo tồn nguồn gốc, an ninh, chất lượng và sự công bằng. Thực hiện điều này giúp hoàn thành nghĩa vụ pháp lý và giảm thiểu rủi ro thiên vị, đầu độc hoặc vi phạm quyền riêng tư xuất hiện trong quá trình đào tạo có thể ảnh hưởng đến toàn bộ vòng đời AI.

---

## C1.1 Nguồn gốc Dữ liệu Đào tạo

Duy trì một danh mục dữ liệu có thể xác minh được tất cả các bộ dữ liệu, chỉ chấp nhận các nguồn tin cậy và ghi lại mọi thay đổi để phục vụ việc kiểm toán.

|   #   | Mô tả                                                                                                                                                                                                           | Cấp độ | Vai trò |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 1.1.1 | Xác minh rằng một danh mục cập nhật của mọi nguồn dữ liệu huấn luyện (nguồn gốc, người quản lý/chủ sở hữu, giấy phép, phương pháp thu thập, các ràng buộc sử dụng dự kiến và lịch sử xử lý) được duy trì.       |   1    |   D/V   |
| 1.1.2 | Xác minh rằng các quy trình dữ liệu đào tạo loại trừ các đặc điểm, thuộc tính hoặc trường không cần thiết (ví dụ: siêu dữ liệu không sử dụng, thông tin nhận dạng cá nhân nhạy cảm, dữ liệu kiểm tra bị rò rỉ). |   1    |   D/V   |
| 1.1.3 | Xác minh rằng tất cả các thay đổi dữ liệu được thực hiện theo quy trình phê duyệt có ghi nhật ký.                                                                                                               |   2    |   D/V   |
| 1.1.4 | Xác minh rằng các tập dữ liệu hoặc các tập con được đóng dấu nước hoặc đánh dấu vân tay khi có thể.                                                                                                             |   3    |   D/V   |

---

## C1.2 Bảo mật và Tính toàn vẹn Dữ liệu Đào tạo

Hạn chế quyền truy cập vào dữ liệu huấn luyện, mã hóa dữ liệu khi lưu trữ và truyền tải, đồng thời xác thực tính toàn vẹn của dữ liệu để ngăn chặn sự can thiệp, trộm cắp hoặc đầu độc dữ liệu.

|   #   | Mô tả                                                                                                                                                          | Cấp độ | Vai trò |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 1.2.1 | Xác minh rằng các kiểm soát truy cập bảo vệ lưu trữ dữ liệu đào tạo và các đường ống xử lý.                                                                    |   1    |   D/V   |
| 1.2.2 | Xác minh rằng tất cả các truy cập đến dữ liệu đào tạo đều được ghi nhật ký, bao gồm người dùng, thời gian và hành động.                                        |   2    |   D/V   |
| 1.2.3 | Xác minh rằng các bộ dữ liệu đào tạo được mã hóa khi truyền và lưu trữ, sử dụng các thuật toán mật mã chuẩn công nghiệp và các phương pháp quản lý khóa.       |   2    |   D/V   |
| 1.2.4 | Xác minh rằng các hàm băm mật mã hoặc chữ ký số được sử dụng để đảm bảo tính toàn vẹn dữ liệu trong quá trình lưu trữ và truyền dữ liệu huấn luyện.            |   2    |   D/V   |
| 1.2.5 | Xác minh rằng các kỹ thuật phát hiện tự động được áp dụng để ngăn chặn các sửa đổi trái phép hoặc sự hỏng dữ liệu đào tạo.                                     |   2    |   D/V   |
| 1.2.6 | Xác minh rằng dữ liệu huấn luyện đã lỗi thời được xoá bỏ hoặc ẩn danh một cách an toàn.                                                                        |   2    |   D/V   |
| 1.2.7 | Xác minh rằng tất cả các phiên bản bộ dữ liệu huấn luyện được nhận dạng duy nhất, lưu trữ bất biến và có thể kiểm toán để hỗ trợ phục hồi và phân tích pháp y. |   3    |   D/V   |

---

## C1.3 Chất lượng, Tính toàn vẹn và An ninh của Ghi nhãn Dữ liệu Đào tạo

Bảo vệ nhãn và yêu cầu xem xét kỹ thuật đối với dữ liệu quan trọng.

|   #   | Mô tả                                                                                                                                                                                                     | Cấp độ | Vai trò |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 1.3.1 | Xác minh rằng các hàm băm mật mã hoặc chữ ký số được áp dụng cho các hiện vật nhãn để đảm bảo tính toàn vẹn và xác thực của chúng.                                                                        |   2    |   D/V   |
| 1.3.2 | Xác minh rằng các giao diện và nền tảng gán nhãn thực thi kiểm soát truy cập mạnh mẽ, duy trì nhật ký kiểm tra chống giả mạo của tất cả các hoạt động gán nhãn và bảo vệ chống lại các sửa đổi trái phép. |   2    |   D/V   |
| 1.3.3 | Xác minh rằng thông tin nhạy cảm trong nhãn được xóa bỏ, ẩn danh hoặc mã hóa ở cấp trường dữ liệu khi lưu trữ và khi truyền tải.                                                                          |   3    |   D/V   |

---

## C1.4 Đảm bảo Chất lượng và An toàn Dữ liệu Đào tạo

Kết hợp xác thực tự động, kiểm tra ngẫu nhiên thủ công và ghi lại quá trình khắc phục để đảm bảo độ tin cậy của tập dữ liệu.

|   #   | Mô tả                                                                                                                                                                                                                                                                                                                                                                                                                           | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 1.4.1 | Xác minh rằng các bài kiểm tra tự động phát hiện lỗi định dạng và giá trị null trên mọi lần nhập dữ liệu hoặc chuyển đổi dữ liệu quan trọng.                                                                                                                                                                                                                                                                                    |   1    |    D    |
| 1.4.2 | Xác minh rằng các quy trình đào tạo và tinh chỉnh mô hình ngôn ngữ lớn (LLM) thực hiện phát hiện đầu độc và xác thực tính toàn vẹn dữ liệu (ví dụ, các phương pháp thống kê, phát hiện điểm bất thường, phân tích embedding) để nhận diện các cuộc tấn công đầu độc tiềm năng (ví dụ, lật nhãn, chèn kích hoạt cửa hậu, lệnh chuyển đổi vai trò, tấn công mẫu ảnh hưởng) hoặc sự hỏng dữ liệu không cố ý trong dữ liệu đào tạo. |   2    |   D/V   |
| 1.4.3 | Xác minh rằng các biện pháp phòng vệ phù hợp, chẳng hạn như đào tạo đối kháng (sử dụng các ví dụ đối kháng được tạo ra), tăng cường dữ liệu với các đầu vào bị nhiễu, hoặc các kỹ thuật tối ưu hóa mạnh mẽ, đã được triển khai và điều chỉnh cho các mô hình liên quan dựa trên đánh giá rủi ro.                                                                                                                                |   3    |   D/V   |
| 1.4.4 | Xác minh rằng nhãn được tạo tự động (ví dụ, qua LLM hoặc giám sát yếu) phải tuân theo ngưỡng độ tin cậy và kiểm tra tính nhất quán để phát hiện nhãn bị ảo giác, gây hiểu lầm hoặc có độ tin cậy thấp.                                                                                                                                                                                                                          |   2    |   D/V   |
| 1.4.5 | Xác minh rằng các bài kiểm tra tự động phát hiện được sự lệch nhãn trên mỗi lần nhập dữ liệu hoặc biến đổi dữ liệu đáng kể.                                                                                                                                                                                                                                                                                                     |   3    |    D    |

---

## C1.5 Dòng dữ liệu và Khả năng truy xuất nguồn gốc

Theo dõi toàn bộ hành trình của từng điểm dữ liệu từ nguồn đến đầu vào mô hình để đảm bảo khả năng kiểm toán và phản hồi sự cố.

|   #   | Mô tả                                                                                                                                                                                                                                                         | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 1.5.1 | Xác minh rằng nguồn gốc của mỗi điểm dữ liệu, bao gồm tất cả các phép biến đổi, tăng cường và hợp nhất, được ghi lại và có thể được tái tạo.                                                                                                                  |   2    |   D/V   |
| 1.5.2 | Xác minh rằng các hồ sơ dòng dõi là không thể thay đổi, được lưu trữ an toàn và có thể truy cập để kiểm toán.                                                                                                                                                 |   2    |   D/V   |
| 1.5.3 | Xác minh rằng việc theo dõi nguồn gốc bao phủ dữ liệu tổng hợp được tạo ra thông qua các kỹ thuật bảo vệ quyền riêng tư hoặc tạo dữ liệu và rằng tất cả dữ liệu tổng hợp đều được gắn nhãn rõ ràng và có thể phân biệt với dữ liệu thực trong suốt quy trình. |   2    |   D/V   |

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

