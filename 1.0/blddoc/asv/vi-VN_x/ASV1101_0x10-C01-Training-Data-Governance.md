# Quản trị Dữ liệu Đào tạo C1 & Quản lý Thiên lệch

## Mục tiêu Kiểm soát

Dữ liệu đào tạo phải được lấy nguồn, xử lý và duy trì theo cách bảo toàn nguồn gốc, bảo mật, chất lượng và tính công bằng. Việc làm này đáp ứng các nghĩa vụ pháp lý và giảm thiểu rủi ro về thiên lệch, đầu độc dữ liệu hoặc vi phạm quyền riêng tư xuất hiện trong quá trình đào tạo, có thể ảnh hưởng đến toàn bộ vòng đời của AI.

---

## C1.1 Nguồn gốc Dữ liệu Đào tạo

Duy trì một danh mục có thể kiểm chứng của tất cả các bộ dữ liệu, chỉ chấp nhận các nguồn tin cậy và ghi lại mọi thay đổi để có thể kiểm tra.

|   #   | Mô tả                                                                                                                                                                                                               | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 1.1.1 | Xác minh rằng tồn kho cập nhật của mọi nguồn dữ liệu đào tạo (nguồn gốc, người quản lý/chủ sở hữu, giấy phép, phương pháp thu thập, các hạn chế sử dụng dự kiến và lịch sử xử lý) được duy trì.                     |   1    |   D/V   |
| 1.1.2 | Xác minh rằng các quy trình dữ liệu huấn luyện loại trừ các đặc trưng, thuộc tính hoặc trường không cần thiết (ví dụ: siêu dữ liệu không sử dụng, thông tin nhận dạng cá nhân nhạy cảm, dữ liệu kiểm tra bị rò rỉ). |   1    |   D/V   |
| 1.1.3 | Xác minh rằng tất cả các thay đổi dữ liệu đều phải tuân theo quy trình phê duyệt có ghi lại.                                                                                                                        |   2    |   D/V   |
| 1.1.4 | Xác minh rằng các bộ dữ liệu hoặc các tập con đã được đóng dấu nước hoặc ghi dấu vân tay khi có thể thực hiện được.                                                                                                 |   3    |   D/V   |

---

## C1.2 An ninh và tính toàn vẹn của dữ liệu huấn luyện

Hạn chế truy cập vào dữ liệu đào tạo, mã hóa nó khi lưu trữ và truyền tải, đồng thời xác thực tính toàn vẹn của dữ liệu để ngăn chặn việc làm giả, đánh cắp hoặc đầu độc dữ liệu.

|   #   | Mô tả                                                                                                                                                                              | Cấp độ | Vai trò |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 1.2.1 | Xác minh rằng các kiểm soát truy cập bảo vệ việc lưu trữ dữ liệu đào tạo và các đường dẫn xử lý dữ liệu.                                                                           |   1    |   D/V   |
| 1.2.2 | Xác minh rằng tất cả các truy cập vào dữ liệu đào tạo đều được ghi lại, bao gồm người dùng, thời gian và hành động.                                                                |   2    |   D/V   |
| 1.2.3 | Xác minh rằng các bộ dữ liệu huấn luyện được mã hóa khi truyền và lưu trữ, sử dụng các thuật toán mã hóa tiêu chuẩn ngành và các phương pháp quản lý khóa.                         |   2    |   D/V   |
| 1.2.4 | Xác minh rằng các hàm băm mật mã hoặc chữ ký số được sử dụng để đảm bảo tính toàn vẹn dữ liệu trong quá trình lưu trữ và truyền tải dữ liệu huấn luyện.                            |   2    |   D/V   |
| 1.2.5 | Xác minh rằng các kỹ thuật phát hiện tự động được áp dụng để ngăn chặn các sửa đổi trái phép hoặc hư hỏng dữ liệu đào tạo.                                                         |   2    |   D/V   |
| 1.2.6 | Xác nhận rằng dữ liệu huấn luyện lỗi thời đã được xóa một cách an toàn hoặc được ẩn danh.                                                                                          |   2    |   D/V   |
| 1.2.7 | Xác minh rằng tất cả các phiên bản tập dữ liệu huấn luyện đều được nhận dạng duy nhất, lưu trữ không thể thay đổi và có thể kiểm toán để hỗ trợ việc phục hồi và phân tích pháp y. |   3    |   D/V   |

---

## C1.3 Chất lượng, Tính toàn vẹn và An ninh của Việc Gán nhãn Dữ liệu Đào tạo

Bảo vệ nhãn và yêu cầu xem xét kỹ thuật đối với dữ liệu quan trọng.

|   #   | Mô tả                                                                                                                                                                                                           | Cấp độ | Vai trò |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 1.3.1 | Xác minh rằng các băm mật mã hoặc chữ ký số được áp dụng cho các hiện vật nhãn để đảm bảo tính toàn vẹn và tính xác thực của chúng.                                                                             |   2    |   D/V   |
| 1.3.2 | Xác minh rằng các giao diện và nền tảng gán nhãn thực thi các kiểm soát truy cập mạnh mẽ, duy trì nhật ký kiểm toán chống giả mạo cho tất cả các hoạt động gán nhãn, và bảo vệ chống lại các sửa đổi trái phép. |   2    |   D/V   |
| 1.3.3 | Xác minh rằng thông tin nhạy cảm trong nhãn được xóa hoặc làm ẩn danh hoặc mã hóa ở cấp trường dữ liệu khi lưu trữ và trong quá trình truyền.                                                                   |   3    |   D/V   |

---

## C1.4 Đảm bảo Chất lượng và An ninh Dữ liệu Đào tạo

Kết hợp xác thực tự động, kiểm tra ngẫu nhiên thủ công và ghi lại quá trình khắc phục để đảm bảo độ tin cậy của tập dữ liệu.

|   #   | Mô tả                                                                                                                                                                                                                                                                                                                                                                                                             | Cấp độ | Vai trò |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 1.4.1 | Xác minh rằng các bài kiểm tra tự động phát hiện lỗi định dạng và giá trị null ở mỗi lần nhập dữ liệu hoặc chuyển đổi dữ liệu quan trọng.                                                                                                                                                                                                                                                                         |   1    |    D    |
| 1.4.2 | Xác minh rằng các quy trình huấn luyện và tinh chỉnh LLM thực hiện phát hiện đầu độc và kiểm tra tính toàn vẹn dữ liệu (ví dụ: các phương pháp thống kê, phát hiện ngoại lệ, phân tích embedding) để nhận diện các cuộc tấn công đầu độc tiềm ẩn (ví dụ: đảo nhãn, chèn kích hoạt backdoor, lệnh đổi vai trò, tấn công các trường hợp có ảnh hưởng) hoặc sự cố vô tình làm hỏng dữ liệu trong dữ liệu huấn luyện. |   2    |   D/V   |
| 1.4.3 | Xác minh rằng các nhãn được tạo tự động (ví dụ, thông qua các LLM hoặc giám sát yếu) phải tuân theo ngưỡng độ tin cậy và các kiểm tra nhất quán để phát hiện các nhãn ảo tưởng, gây hiểu lầm hoặc có độ tin cậy thấp.                                                                                                                                                                                             |   2    |   D/V   |
| 1.4.4 | Xác minh rằng các biện pháp phòng thủ phù hợp, chẳng hạn như huấn luyện chống đối kháng (sử dụng các ví dụ đối kháng được tạo ra), tăng cường dữ liệu với các đầu vào bị nhiễu, hoặc các kỹ thuật tối ưu hóa bền vững, được triển khai và điều chỉnh cho các mô hình liên quan dựa trên đánh giá rủi ro.                                                                                                          |   3    |   D/V   |
| 1.4.5 | Xác nhận rằng các bài kiểm tra tự động phát hiện được sự lệch nhãn trên mọi lần nhập dữ liệu hoặc biến đổi dữ liệu quan trọng.                                                                                                                                                                                                                                                                                    |   3    |    D    |

---

## C1.5 Dòng dữ liệu và khả năng truy xuất nguồn gốc

Theo dõi toàn bộ hành trình của từng điểm dữ liệu từ nguồn đến đầu vào mô hình để đảm bảo khả năng kiểm toán và phản ứng sự cố.

|   #   | Mô tả                                                                                                                                                                                                                                                       | Cấp độ | Vai trò |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 1.5.1 | Xác minh rằng nguồn gốc của mỗi điểm dữ liệu, bao gồm tất cả các phép biến đổi, tăng cường và kết hợp, được ghi lại và có thể tái tạo lại.                                                                                                                  |   2    |   D/V   |
| 1.5.2 | Xác minh rằng các bản ghi nguồn gốc là bất biến, được lưu trữ an toàn và có thể truy cập để kiểm toán.                                                                                                                                                      |   2    |   D/V   |
| 1.5.3 | Xác minh rằng việc theo dõi nguồn gốc bao gồm dữ liệu tổng hợp được tạo ra thông qua các kỹ thuật bảo vệ quyền riêng tư hoặc tạo dữ liệu và tất cả dữ liệu tổng hợp đều được dán nhãn rõ ràng và có thể phân biệt với dữ liệu thực trong toàn bộ quy trình. |   2    |   D/V   |

---

## Tài liệu tham khảo

* [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
* [EU AI Act – Article 10: Data & Data Governance](https://artificialintelligenceact.eu/article/10/)
* [CISA Advisory: Securing Data for AI Systems](https://www.cisa.gov/news-events/cybersecurity-advisories/aa25-142a)
* [OpenAI Privacy Center – Data Deletion Controls](https://privacy.openai.com/policies?modal=take-control)

