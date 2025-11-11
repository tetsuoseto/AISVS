# Hành vi mô hình C7, Kiểm soát đầu ra và Đảm bảo an toàn

## Mục tiêu Kiểm soát

Các kết quả mô hình phải được cấu trúc, đáng tin cậy, an toàn, có thể giải thích và liên tục được giám sát trong môi trường sản xuất. Thực hiện như vậy sẽ giảm thiểu các hiện tượng ảo tưởng, rò rỉ thông tin riêng tư, nội dung gây hại và các hành động không kiểm soát được, đồng thời tăng cường sự tin tưởng của người dùng và tuân thủ quy định.

---

## C7.1 Thực thi Định dạng Đầu ra

Các sơ đồ nghiêm ngặt, giải mã có giới hạn và xác thực hạ nguồn ngăn chặn nội dung bị biến dạng hoặc độc hại trước khi nó lan truyền.

|   #   | Mô tả                                                                                                                                                                                             | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 7.1.1 | Xác minh rằng các sơ đồ phản hồi (ví dụ: JSON Schema) được cung cấp trong lời nhắc hệ thống và mọi đầu ra đều được tự động xác thực; các đầu ra không phù hợp sẽ kích hoạt sửa chữa hoặc từ chối. |   1    |   D/V   |
| 7.1.2 | Xác minh rằng việc giải mã có giới hạn (token dừng, regex, max-tokens) đã được bật để ngăn ngừa tình trạng tràn bộ đệm hoặc các kênh bên ngoài tấn công qua prompt.                               |   1    |   D/V   |
| 7.1.3 | Xác minh rằng các thành phần hạ nguồn coi đầu ra là không đáng tin cậy và xác thực chúng theo các lược đồ hoặc trình giải tuần tự hóa an toàn chống chèn.                                         |   2    |   D/V   |
| 7.1.4 | Xác minh rằng các sự kiện lỗi đầu ra không đúng được ghi lại, giới hạn tốc độ và hiển thị lên hệ thống giám sát.                                                                                  |   3    |    V    |

---

## C7.2 Phát hiện và Giảm thiểu Ảo tưởng

Ước lượng sự không chắc chắn và các chiến lược dự phòng ngăn chặn các câu trả lời bịa đặt.

|   #   | Mô tả                                                                                                                                                                                 | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 7.2.1 | Xác minh rằng xác suất log cấp token, tính nhất quán tự nhóm, hoặc bộ phát hiện ảo hóa được tinh chỉnh đều gán điểm độ tin cậy cho từng câu trả lời.                                  |   1    |   D/V   |
| 7.2.2 | Xác minh rằng các phản hồi dưới ngưỡng độ chắc chắn có thể cấu hình kích hoạt các quy trình thay thế (ví dụ: tạo sinh tăng cường truy xuất, mô hình phụ, hoặc xem xét bởi con người). |   1    |   D/V   |
| 7.2.3 | Xác minh rằng các sự cố ảo giác được gắn thẻ bằng siêu dữ liệu nguyên nhân gốc rễ và được đưa vào quy trình phân tích sau sự cố và tinh chỉnh.                                        |   2    |   D/V   |
| 7.2.4 | Xác minh rằng các ngưỡng và bộ dò được hiệu chỉnh lại sau các cập nhật lớn về mô hình hoặc cơ sở tri thức.                                                                            |   3    |   D/V   |
| 7.2.5 | Xác minh rằng các biểu đồ điều khiển theo dõi tỷ lệ ảo tưởng.                                                                                                                         |   3    |    V    |

---

## C7.3 Lọc An toàn & Bảo mật Đầu ra

Các bộ lọc chính sách và phạm vi bảo vệ của nhóm kiểm tra đỏ bảo vệ người dùng và dữ liệu bảo mật.

|   #   | Mô tả                                                                                                                                                                   | Cấp độ | Vai trò |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 7.3.1 | Xác minh rằng các bộ phân loại trước và sau khi tạo nội dung chặn các nội dung về thù hận, quấy rối, tự làm hại, cực đoan và nội dung khiêu dâm phù hợp với chính sách. |   1    |   D/V   |
| 7.3.2 | Xác minh rằng việc phát hiện PII/PCI và tự động ẩn thông tin được thực hiện trên mọi phản hồi; các vi phạm sẽ gây ra sự cố về quyền riêng tư.                           |   1    |   D/V   |
| 7.3.3 | Xác minh rằng các thẻ bảo mật (ví dụ, bí mật thương mại) được truyền qua các phương thức để ngăn ngừa rò rỉ trong văn bản, hình ảnh hoặc mã.                            |   2    |    D    |
| 7.3.4 | Xác minh rằng các cố gắng vượt qua bộ lọc hoặc phân loại có rủi ro cao yêu cầu phê duyệt phụ hoặc xác thực lại người dùng.                                              |   3    |   D/V   |
| 7.3.5 | Xác minh rằng ngưỡng lọc phản ánh đúng khu vực pháp lý và ngữ cảnh về độ tuổi/vai trò của người dùng.                                                                   |   3    |   D/V   |

---

## C7.4 Giới hạn Đầu ra & Hành động

Giới hạn tốc độ và cổng phê duyệt ngăn chặn lạm dụng và tự động hóa quá mức.

|   #   | Mô tả                                                                                                                                                               | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 7.4.1 | Xác minh rằng hạn mức mỗi người dùng và mỗi khóa API giới hạn yêu cầu, token và chi phí với cơ chế lùi lại theo cấp số nhân khi gặp lỗi 429.                        |   1    |    D    |
| 7.4.2 | Xác minh rằng các hành động đặc quyền (ghi file, thực thi mã, gọi mạng) yêu cầu phê duyệt dựa trên chính sách hoặc có người kiểm soát.                              |   1    |   D/V   |
| 7.4.3 | Xác minh rằng các kiểm tra nhất quán đa phương thức đảm bảo hình ảnh, mã và văn bản được tạo ra cho cùng một yêu cầu không thể bị sử dụng để giấu nội dung độc hại. |   2    |   D/V   |
| 7.4.4 | Xác minh rằng độ sâu đại diện của đại lý, giới hạn đệ quy và danh sách công cụ được phép được cấu hình rõ ràng.                                                     |   2    |    D    |
| 7.4.5 | Xác minh rằng việc vi phạm giới hạn phát ra các sự kiện bảo mật có cấu trúc để nhập vào SIEM.                                                                       |   3    |    V    |

---

## C7.5 Giải thích khả năng xuất đầu ra

Tín hiệu minh bạch cải thiện sự tin tưởng của người dùng và việc gỡ lỗi nội bộ.

|   #   | Mô tả                                                                                                                                   | Cấp độ | Vai trò |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 7.5.1 | Xác minh rằng các điểm số độ tin cậy hướng đến người dùng hoặc tóm tắt lý do ngắn gọn được hiển thị khi đánh giá rủi ro cho là phù hợp. |   2    |   D/V   |
| 7.5.2 | Xác minh rằng các giải thích được tạo ra không tiết lộ các lời nhắc hệ thống nhạy cảm hoặc dữ liệu sở hữu độc quyền.                    |   2    |   D/V   |
| 7.5.3 | Xác minh rằng hệ thống ghi lại xác suất log cấp token hoặc bản đồ chú ý và lưu trữ chúng để kiểm tra có phép.                           |   3    |    D    |
| 7.5.4 | Xác minh rằng các hiện vật giải thích được quản lý phiên bản cùng với các bản phát hành mô hình để đảm bảo khả năng kiểm toán.          |   3    |    V    |

---

## C7.6 Tích hợp giám sát

Khả năng quan sát thời gian thực khép kín vòng lặp giữa phát triển và sản xuất.

|   #   | Mô tả                                                                                                                                                    | Cấp độ | Vai trò |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 7.6.1 | Xác minh rằng các chỉ số (vi phạm lược đồ, tỉ lệ ảo tưởng, độ độc hại, rò rỉ PII, độ trễ, chi phí) được truyền đến một nền tảng giám sát trung tâm.      |   1    |    D    |
| 7.6.2 | Xác minh rằng các ngưỡng cảnh báo được định nghĩa cho từng chỉ số an toàn, kèm theo các đường dẫn leo thang trực tiếp khi cần.                           |   1    |    V    |
| 7.6.3 | Xác minh rằng các bảng điều khiển liên kết các bất thường đầu ra với mô hình/phiên bản, cờ tính năng và các thay đổi dữ liệu thượng nguồn.               |   2    |    V    |
| 7.6.4 | Xác minh rằng dữ liệu giám sát được phản hồi lại vào việc đào tạo lại, tinh chỉnh hoặc cập nhật quy tắc trong quy trình làm việc MLOps đã được ghi chép. |   2    |   D/V   |
| 7.6.5 | Xác minh rằng các pipeline giám sát đã được kiểm tra xâm nhập và kiểm soát truy cập để tránh rò rỉ các bản ghi nhạy cảm.                                 |   3    |    V    |

---

## 7.7 Các Biện Pháp An Toàn cho Nội Dung Tạo Sinh

Đảm bảo rằng các hệ thống AI không tạo ra nội dung truyền thông bất hợp pháp, có hại hoặc không được phép bằng cách thực thi các ràng buộc chính sách, xác thực đầu ra và khả năng truy xuất.

|   #   | Mô tả                                                                                                                                                                                                                          | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 7.7.1 | Xác nhận rằng các lời nhắc hệ thống và hướng dẫn người dùng rõ ràng cấm việc tạo ra các phương tiện deepfake bất hợp pháp, có hại hoặc không có sự đồng thuận (ví dụ: hình ảnh, video, âm thanh).                              |   1    |   D/V   |
| 7.7.2 | Xác nhận rằng các lời nhắc được lọc để ngăn chặn các cố gắng tạo ra các bản giả mạo, các nội dung khiêu dâm sâu, hoặc các phương tiện truyền thông mô tả những cá nhân thực mà không có sự đồng ý.                             |   2    |   D/V   |
| 7.7.3 | Xác minh rằng hệ thống sử dụng băm nhận thức, phát hiện watermark, hoặc dấu vân tay để ngăn chặn việc tái sản xuất trái phép các phương tiện có bản quyền.                                                                     |   2    |    V    |
| 7.7.4 | Xác minh rằng tất cả phương tiện được tạo ra đều được ký mật mã, đóng dấu bản quyền hoặc nhúng với siêu dữ liệu nguồn gốc chống giả mạo để có thể truy xuất nguồn gốc khi xử lý tiếp theo.                                     |   3    |   D/V   |
| 7.7.5 | Xác minh rằng các cố gắng vượt qua (ví dụ: che giấu prompt, ngôn ngữ lóng, cách diễn đạt mang tính đối kháng) được phát hiện, ghi lại và giới hạn tần suất; những hành vi lạm dụng lặp lại được báo cáo lên hệ thống giám sát. |   3    |    V    |

## Tài liệu tham khảo

* [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
* [ISO/IEC 42001:2023 – AI Management System](https://www.iso.org/obp/ui/en/)
* [OWASP Top-10 for Large Language Model Applications (2025)](https://owasp.org/www-project-top-10-for-large-language-model-applications/)
* [Practical Techniques to Constrain LLM Output](https://mychen76.medium.com/practical-techniques-to-constraint-llm-output-in-json-format-e3e72396c670)
* [Dataiku – Structured Text Generation Guide](https://blog.dataiku.com/your-guide-to-structured-text-generation)
* [VL-Uncertainty: Detecting Hallucinations](https://arxiv.org/abs/2411.11919)
* [HaDeMiF: Hallucination Detection & Mitigation](https://openreview.net/forum?id=VwOYxPScxB)
* [Building Confidence in LLM Outputs](https://www.alkymi.io/data-science-room/building-confidence-in-llm-outputs)
* [Explainable AI & LLMs](https://duncsand.medium.com/explainable-ai-140912d31b3b)
* [Sensitive Information Disclosure in LLMs](https://virtualcyberlabs.com/llm-sensitive-information-disclosure/)
* [OpenAI Rate-Limit & Exponential Back-off](https://hackernoon.com/openais-rate-limit-a-guide-to-exponential-backoff-for-llm-evaluation)
* [Arize AI – LLM Observability Platform](https://arize.com/)

