# Hành vi Mô hình C7, Kiểm soát Đầu ra & Đảm bảo An toàn

## Mục tiêu Kiểm soát

Đầu ra của mô hình phải có cấu trúc, đáng tin cậy, an toàn, có thể giải thích và được giám sát liên tục trong môi trường sản xuất. Làm như vậy giúp giảm các hiện tượng ảo tưởng, rò rỉ thông tin cá nhân, nội dung gây hại và hành động mất kiểm soát, đồng thời tăng sự tin tưởng của người dùng và tuân thủ quy định.

---

## C7.1 Thực thi Định dạng Đầu ra

Các sơ đồ nghiêm ngặt, giải mã có giới hạn, và xác thực hạ nguồn ngăn chặn nội dung sai định dạng hoặc độc hại trước khi nó lan truyền.

|   #   | Mô tả                                                                                                                                                                                                       | Cấp độ | Vai trò |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 7.1.1 | Xác minh rằng các sơ đồ phản hồi (ví dụ: JSON Schema) được cung cấp trong lời nhắc hệ thống và mọi kết quả đầu ra đều được tự động xác thực; các kết quả không tuân thủ sẽ kích hoạt sửa chữa hoặc từ chối. |   1    |   D/V   |
| 7.1.2 | Xác minh rằng giải mã có giới hạn (token dừng, regex, max-tokens) đã được bật để ngăn ngừa tràn bộ đệm hoặc các kênh phụ tiêm nhúng prompt.                                                                 |   1    |   D/V   |
| 7.1.3 | Xác nhận rằng các thành phần hạ nguồn coi đầu ra là không đáng tin cậy và xác thực chúng dựa trên các sơ đồ hoặc bộ giải tuần tự an toàn chống tiêm nhiễm.                                                  |   2    |   D/V   |
| 7.1.4 | Xác minh rằng các sự kiện đầu ra không đúng được ghi lại, giới hạn tốc độ và hiển thị trên hệ thống giám sát.                                                                                               |   3    |    V    |

---

## C7.2 Phát hiện và Giảm thiểu Ảo giác

Ước lượng sự không chắc chắn và các chiến lược dự phòng giúp hạn chế các câu trả lời giả mạo.

|   #   | Mô tả                                                                                                                                                                                          | Cấp độ | Vai trò |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 7.2.1 | Xác minh rằng xác suất log cấp token, sự nhất quán bản thân của tập hợp, hoặc các bộ phát hiện ảo tưởng đã được tinh chỉnh gán một điểm độ tin cậy cho mỗi câu trả lời.                        |   1    |   D/V   |
| 7.2.2 | Xác minh rằng các phản hồi có mức độ tin cậy thấp hơn ngưỡng cấu hình sẽ kích hoạt các quy trình dự phòng (ví dụ: tạo sinh tăng cường truy xuất, mô hình thứ cấp hoặc đánh giá của con người). |   1    |   D/V   |
| 7.2.3 | Xác minh rằng các sự cố ảo giác được gắn thẻ với siêu dữ liệu nguyên nhân gốc rễ và được đưa vào quy trình phân tích sự cố sau và tinh chỉnh lại.                                              |   2    |   D/V   |
| 7.2.4 | Xác minh rằng các ngưỡng và bộ phát hiện được cân chỉnh lại sau các cập nhật quan trọng về mô hình hoặc cơ sở tri thức.                                                                        |   3    |   D/V   |
| 7.2.5 | Xác minh rằng các biểu đồ trên bảng điều khiển theo dõi tỷ lệ ảo tưởng.                                                                                                                        |   3    |    V    |

---

## C7.3 Lọc An toàn & Riêng tư Đầu ra

Bộ lọc chính sách và phạm vi đội đỏ bảo vệ người dùng và dữ liệu mật.

|   #   | Mô tả                                                                                                                                                                              | Cấp độ | Vai trò |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 7.3.1 | Xác minh rằng các bộ phân loại trước và sau khi tạo nội dung chặn các nội dung về thù địch, quấy rối, tự làm hại, cực đoan và nội dung mang tính khiêu dâm phù hợp với chính sách. |   1    |   D/V   |
| 7.3.2 | Xác minh rằng phát hiện PII/PCI và tự động che khuất được thực hiện trên mọi phản hồi; các vi phạm sẽ gây ra sự cố về quyền riêng tư.                                              |   1    |   D/V   |
| 7.3.3 | Xác minh rằng các nhãn bảo mật (ví dụ: bí mật thương mại) được truyền tải qua các phương thức khác nhau để ngăn chặn rò rỉ trong văn bản, hình ảnh hoặc mã.                        |   2    |    D    |
| 7.3.4 | Xác minh rằng các nỗ lực vượt qua bộ lọc hoặc các phân loại rủi ro cao yêu cầu phê duyệt thứ cấp hoặc người dùng xác thực lại.                                                     |   3    |   D/V   |
| 7.3.5 | Xác minh rằng các ngưỡng lọc phản ánh đúng các khu vực pháp lý và bối cảnh tuổi/ vai trò người dùng.                                                                               |   3    |   D/V   |

---

## C7.4 Giới hạn Đầu ra & Hành động

Giới hạn tỷ lệ và cổng phê duyệt ngăn ngừa việc lạm dụng và tự động hóa quá mức.

|   #   | Mô tả                                                                                                                                                                     | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 7.4.1 | Xác minh rằng hạn mức theo người dùng và theo khóa API giới hạn yêu cầu, token và chi phí với cơ chế thử lại theo hàm mũ khi gặp lỗi 429.                                 |   1    |    D    |
| 7.4.2 | Xác minh rằng các hành động có đặc quyền (ghi file, thực thi mã, gọi mạng) yêu cầu phê duyệt dựa trên chính sách hoặc có sự can thiệp của con người.                      |   1    |   D/V   |
| 7.4.3 | Xác minh rằng các kiểm tra nhất quán đa phương thức đảm bảo hình ảnh, mã và văn bản được tạo ra cho cùng một yêu cầu không thể được sử dụng để buôn lậu nội dung độc hại. |   2    |   D/V   |
| 7.4.4 | Xác minh rằng độ sâu ủy quyền đại lý, giới hạn đệ quy và danh sách công cụ được phép đã được cấu hình rõ ràng.                                                            |   2    |    D    |
| 7.4.5 | Xác minh rằng việc vi phạm giới hạn phát ra các sự kiện bảo mật có cấu trúc để nhập vào SIEM.                                                                             |   3    |    V    |

---

## C7.5 Giải thích đầu ra

Tín hiệu minh bạch cải thiện sự tin tưởng của người dùng và việc gỡ lỗi nội bộ.

|   #   | Mô tả                                                                                                                                      | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 7.5.1 | Xác minh rằng điểm số độ tin cậy dành cho người dùng hoặc các bản tóm tắt lý do ngắn gọn được hiển thị khi đánh giá rủi ro cho là phù hợp. |   2    |   D/V   |
| 7.5.2 | Xác nhận rằng các giải thích được tạo ra không tiết lộ các lời nhắc hệ thống nhạy cảm hoặc dữ liệu độc quyền.                              |   2    |   D/V   |
| 7.5.3 | Xác minh rằng hệ thống ghi lại xác suất log ở cấp token hoặc bản đồ chú ý và lưu trữ chúng để kiểm tra được phép.                          |   3    |    D    |
| 7.5.4 | Xác minh rằng các hiện vật giải thích được kiểm soát phiên bản cùng với các phiên bản mô hình để đảm bảo khả năng kiểm tra.                |   3    |    V    |

---

## C7.6 Tích hợp giám sát

Khả năng quan sát theo thời gian thực đóng vai trò kết nối chặt chẽ giữa phát triển và sản xuất.

|   #   | Mô tả                                                                                                                                                | Cấp độ | Vai trò |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 7.6.1 | Xác minh rằng các chỉ số (vi phạm lược đồ, tỷ lệ ảo tưởng, độc hại, rò rỉ PII, độ trễ, chi phí) được truyền đến một nền tảng giám sát trung tâm.     |   1    |    D    |
| 7.6.2 | Xác minh rằng các ngưỡng cảnh báo được định nghĩa cho mỗi chỉ số an toàn, kèm theo các đường dẫn nâng cấp khi trực.                                  |   1    |    V    |
| 7.6.3 | Xác minh rằng các bảng điều khiển liên kết các bất thường đầu ra với mô hình/phiên bản, cờ tính năng và thay đổi dữ liệu thượng nguồn.               |   2    |    V    |
| 7.6.4 | Xác minh rằng dữ liệu giám sát được phản hồi vào quá trình huấn luyện lại, tinh chỉnh hoặc cập nhật quy tắc trong quy trình MLOps được tài liệu hóa. |   2    |   D/V   |
| 7.6.5 | Xác minh rằng các đường dẫn giám sát đã được kiểm tra xuyên thấu và kiểm soát truy cập để tránh rò rỉ các bản ghi nhạy cảm.                          |   3    |    V    |

---

## 7.7 Biện pháp bảo vệ phương tiện tạo sinh

Đảm bảo rằng các hệ thống AI không tạo ra nội dung phương tiện bất hợp pháp, gây hại hoặc không được phép bằng cách thực thi các ràng buộc chính sách, xác thực đầu ra và khả năng truy xuất nguồn gốc.

|   #   | Mô tả                                                                                                                                                                                                          | Cấp độ | Vai trò |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 7.7.1 | Xác minh rằng các lệnh hệ thống và hướng dẫn người dùng rõ ràng cấm việc tạo ra các phương tiện deepfake bất hợp pháp, gây hại hoặc không có sự đồng ý (ví dụ: hình ảnh, video, âm thanh).                     |   1    |   D/V   |
| 7.7.2 | Xác minh rằng các lệnh nhắc được lọc để ngăn chặn các cố gắng tạo ra các giả mạo nhân thân, deepfake khiêu dâm hoặc phương tiện truyền thông mô tả các cá nhân thực mà không có sự đồng ý.                     |   2    |   D/V   |
| 7.7.3 | Xác minh rằng hệ thống sử dụng băm cảm nhận, phát hiện watermark hoặc nhận dạng dấu vân tay để ngăn chặn việc sao chép trái phép các phương tiện có bản quyền.                                                 |   2    |    V    |
| 7.7.4 | Xác minh rằng tất cả các phương tiện được tạo ra đều được ký kỹ thuật số, đóng dấu bản quyền, hoặc nhúng với siêu dữ liệu nguồn gốc chống giả mạo để đảm bảo truy xuất nguồn gốc cho các bước xử lý tiếp theo. |   3    |   D/V   |
| 7.7.5 | Xác minh rằng các nỗ lực vượt qua (ví dụ: làm mờ prompt, dùng tiếng lóng, cách diễn đạt đối kháng) được phát hiện, ghi lại và giới hạn tần suất; việc lạm dụng lặp lại được báo cáo cho các hệ thống giám sát. |   3    |    V    |

## Tài liệu tham khảo

* [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
* [ISO/IEC 42001:2023 – AI Management System](https://www.iso.org/obp/ui/en/)
* [OWASP Top-10 for Large Language Model Applications (2025)](https://owasp.org/www-project-top-10-for-large-language-model-applications/)
* [Improper Output Handling – OWASP LLM05:2025](https://genai.owasp.org/llmrisk/llm052025-improper-output-handling/)
* [Practical Techniques to Constrain LLM Output](https://mychen76.medium.com/practical-techniques-to-constraint-llm-output-in-json-format-e3e72396c670)
* [Dataiku – Structured Text Generation Guide](https://blog.dataiku.com/your-guide-to-structured-text-generation)
* [VL-Uncertainty: Detecting Hallucinations](https://arxiv.org/abs/2411.11919)
* [HaDeMiF: Hallucination Detection & Mitigation](https://openreview.net/forum?id=VwOYxPScxB)
* [Building Confidence in LLM Outputs](https://www.alkymi.io/data-science-room/building-confidence-in-llm-outputs)
* [Explainable AI & LLMs](https://duncsand.medium.com/explainable-ai-140912d31b3b)
* [LLM Red-Teaming Guide](https://www.confident-ai.com/blog/red-teaming-llms-a-step-by-step-guide)
* [Sensitive Information Disclosure in LLMs](https://virtualcyberlabs.com/llm-sensitive-information-disclosure/)
* [LangChain – Chat Model Rate Limiting](https://python.langchain.com/docs/how_to/chat_model_rate_limiting/)
* [OpenAI Rate-Limit & Exponential Back-off](https://hackernoon.com/openais-rate-limit-a-guide-to-exponential-backoff-for-llm-evaluation)
* [Arize AI – LLM Observability Platform](https://arize.com/)

