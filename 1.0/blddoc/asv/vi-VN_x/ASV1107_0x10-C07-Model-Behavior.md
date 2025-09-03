# C7 Hành vi của Mô hình, Kiểm soát Đầu ra và Đảm bảo An toàn

## Mục tiêu kiểm soát

Đầu ra của mô hình phải được cấu trúc hóa, đáng tin cậy, an toàn, có thể giải thích, và được giám sát liên tục trong môi trường sản xuất. Việc này giảm các hiện tượng ảo giác, rò rỉ dữ liệu cá nhân, nội dung độc hại và hành động ngoài tầm kiểm soát, đồng thời tăng niềm tin của người dùng và tuân thủ các quy định pháp lý.

---

## C7.1 Thực thi Định dạng Đầu ra

Các lược đồ nghiêm ngặt, giải mã có ràng buộc và xác thực ở các bước xử lý phía sau ngăn nội dung bị định dạng sai hoặc có hại trước khi nó lan truyền.

|   #   | Mô tả                                                                                                                                                                                            | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 7.1.1 | Xác nhận rằng các khuôn mẫu phản hồi (ví dụ: JSON Schema) được cung cấp trong lời nhắc hệ thống và mọi đầu ra đều được xác thực tự động; các đầu ra không phù hợp sẽ được sửa chữa hoặc từ chối. |   1    |   D/V   |
| 7.1.2 | Đảm bảo rằng giải mã có ràng buộc (token dừng, biểu thức chính quy, max-tokens) được bật để ngăn ngừa tràn dữ liệu hoặc các kênh phụ tiêm prompt.                                                |   1    |   D/V   |
| 7.1.3 | Xác minh rằng các thành phần ở phía sau coi đầu ra là không đáng tin cậy và xác thực chúng theo các sơ đồ hoặc các bộ giải tuần tự an toàn trước các cuộc tấn công injection.                    |   2    |   D/V   |
| 7.1.4 | Xác minh rằng các sự kiện đầu ra không hợp lệ được ghi lại, được giới hạn theo tần suất, và được đưa lên hệ thống giám sát.                                                                      |   3    |    V    |

---

## C7.2 Phát hiện và Giảm thiểu ảo giác

Việc ước lượng sự bất định và các chiến lược dự phòng giúp kiềm chế các câu trả lời bị bịa đặt.

|   #   | Mô tả                                                                                                                                                                                                    | Cấp độ | Vai trò |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 7.2.1 | Xác minh rằng các xác suất log ở cấp token, tính tự nhất quán của ensemble, hoặc các bộ phát hiện ảo giác được tinh chỉnh gán một điểm tin cậy cho mỗi câu trả lời.                                      |   1    |   D/V   |
| 7.2.2 | Xác nhận rằng các phản hồi có độ tin cậy dưới ngưỡng có thể cấu hình sẽ kích hoạt các quy trình xử lý dự phòng (ví dụ: tạo sinh được tăng cường bằng truy xuất, mô hình phụ hoặc xem xét bởi con người). |   1    |   D/V   |
| 7.2.3 | Xác nhận rằng các sự cố ảo giác được gắn nhãn bằng siêu dữ liệu nguyên nhân gốc và được đưa vào các pipeline phân tích sau sự cố và tinh chỉnh.                                                          |   2    |   D/V   |
| 7.2.4 | Xác minh rằng các ngưỡng và bộ phát hiện được hiệu chuẩn lại sau các cập nhật lớn của mô hình hoặc cơ sở tri thức.                                                                                       |   3    |   D/V   |
| 7.2.5 | Xác minh rằng các biểu đồ trực quan trên bảng điều khiển theo dõi tỷ lệ ảo giác.                                                                                                                         |   3    |    V    |

---

## C7.3 Lọc An toàn và Riêng tư cho Đầu ra

Các bộ lọc chính sách và phạm vi của đội đỏ bảo vệ người dùng và dữ liệu bí mật.

|   #   | Mô tả                                                                                                                                                                                               | Cấp độ | Vai trò |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 7.3.1 | Xác minh rằng các bộ phân loại trước và sau khi sinh chặn nội dung liên quan đến thù ghét, quấy rối, tự làm hại bản thân, cực đoan và nội dung mang tính khiêu dâm rõ ràng, phù hợp với chính sách. |   1    |   D/V   |
| 7.3.2 | Xác nhận rằng việc phát hiện PII/PCI và tự động ẩn thông tin được thực thi trên mọi phản hồi; mọi vi phạm sẽ gây ra sự cố quyền riêng tư.                                                           |   1    |   D/V   |
| 7.3.3 | Xác nhận rằng nhãn bảo mật (ví dụ: bí mật thương mại) được lan truyền qua các chế độ để ngăn ngừa rò rỉ trong văn bản, hình ảnh hoặc mã.                                                            |   2    |    D    |
| 7.3.4 | Xác minh rằng các nỗ lực vượt qua bộ lọc hoặc các phân loại rủi ro cao yêu cầu phê duyệt thứ cấp hoặc xác thực lại người dùng.                                                                      |   3    |   D/V   |
| 7.3.5 | Xác minh rằng các ngưỡng lọc phản ánh các khu vực pháp lý và ngữ cảnh về tuổi và vai trò của người dùng.                                                                                            |   3    |   D/V   |

---

## C7.4 Đầu ra và Giới hạn hành động

Giới hạn lưu lượng và cổng phê duyệt ngăn chặn lạm dụng và sự tự chủ quá mức.

|   #   | Mô tả                                                                                                                                                                    | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 7.4.1 | Xác minh rằng các hạn ngạch theo người dùng và theo khóa API giới hạn số lượt yêu cầu, token và chi phí, và áp dụng back-off lũy thừa khi gặp lỗi 429.                   |   1    |    D    |
| 7.4.2 | Xác minh rằng các hành động đặc quyền (viết tệp, thực thi mã, gọi mạng) yêu cầu phê duyệt dựa trên chính sách hoặc có sự tham gia của con người vào vòng lặp.            |   1    |   D/V   |
| 7.4.3 | Xác nhận rằng các kiểm tra nhất quán đa phương thức đảm bảo hình ảnh, mã và văn bản được tạo ra cho cùng một yêu cầu không thể bị lợi dụng để che giấu nội dung độc hại. |   2    |   D/V   |
| 7.4.4 | Xác minh rằng độ sâu ủy quyền của tác nhân, giới hạn đệ quy và danh sách công cụ được phép đã được cấu hình rõ ràng.                                                     |   2    |    D    |
| 7.4.5 | Xác minh rằng khi giới hạn bị vi phạm, các sự kiện bảo mật có cấu trúc được phát ra để nhập vào SIEM.                                                                    |   3    |    V    |

---

## C7.5 Khả năng giải thích đầu ra

Các tín hiệu minh bạch giúp tăng niềm tin của người dùng và hỗ trợ gỡ lỗi nội bộ.

|   #   | Mô tả                                                                                                                                        | Cấp độ | Vai trò |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 7.5.1 | Xác minh rằng các điểm tự tin mà người dùng có thể xem hoặc các bản tóm tắt lý giải ngắn gọn được tiết lộ khi đánh giá rủi ro cho phù hợp.   |   2    |   D/V   |
| 7.5.2 | Xác minh rằng các lời giải thích được tạo ra không tiết lộ các lời nhắc hệ thống nhạy cảm hoặc dữ liệu độc quyền.                            |   2    |   D/V   |
| 7.5.3 | Xác minh rằng hệ thống ghi nhận xác suất log ở cấp độ token hoặc bản đồ attention và lưu trữ chúng để được kiểm tra bởi người có thẩm quyền. |   3    |    D    |
| 7.5.4 | Xác minh rằng các artefacts giải thích được kiểm soát phiên bản cùng với các bản phát hành mô hình để đảm bảo khả năng kiểm toán.            |   3    |    V    |

---

## C7.6 Tích hợp Giám sát

Khả năng quan sát thời gian thực đóng vòng giữa phát triển và vận hành.

|   #   | Mô tả                                                                                                                                                            | Cấp độ | Vai trò |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 7.6.1 | Xác minh rằng các chỉ số (vi phạm lược đồ, tỷ lệ ảo giác, mức độ độc hại, rò rỉ PII, độ trễ, chi phí) được truyền tới một nền tảng giám sát trung tâm.           |   1    |    D    |
| 7.6.2 | Xác nhận rằng ngưỡng cảnh báo được định nghĩa cho từng chỉ số an toàn, kèm theo quy trình tăng cấp khi trực.                                                     |   1    |    V    |
| 7.6.3 | Xác minh rằng các bảng điều khiển thể hiện sự tương quan giữa các bất thường đầu ra với mô hình hoặc phiên bản, cờ tính năng và các thay đổi dữ liệu upstream.   |   2    |    V    |
| 7.6.4 | Xác minh rằng dữ liệu giám sát được phản hồi vào quá trình tái huấn luyện, tinh chỉnh mô hình hoặc cập nhật quy tắc trong một quy trình MLOps được tài liệu hóa. |   2    |   D/V   |
| 7.6.5 | Xác minh rằng các pipeline giám sát được kiểm thử xâm nhập và được kiểm soát truy cập để tránh rò rỉ nhật ký nhạy cảm.                                           |   3    |    V    |

---

## 7.7 Các biện pháp bảo vệ cho nội dung do AI tạo ra

Đảm bảo các hệ thống AI không sinh ra nội dung đa phương tiện bất hợp pháp, gây hại hoặc không được ủy quyền bằng cách thực thi các ràng buộc về chính sách, xác thực đầu ra và tính truy vết.

|   #   | Mô tả                                                                                                                                                                                                                 | Cấp độ | Vai trò |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 7.7.1 | Xác nhận rằng lời nhắc hệ thống và hướng dẫn của người dùng đã cấm rõ ràng việc tạo ra nội dung deepfake bất hợp pháp, gây hại hoặc không có sự đồng ý (ví dụ: hình ảnh, video, âm thanh).                            |   1    |   D/V   |
| 7.7.2 | Xác minh rằng các lời nhắc được lọc để ngăn chặn các cố gắng giả mạo danh tính, deepfake khiêu dâm, hoặc các phương tiện mô tả người thật mà không có sự đồng ý.                                                      |   2    |   D/V   |
| 7.7.3 | Xác nhận rằng hệ thống đang sử dụng băm cảm nhận, phát hiện dấu nước hoặc nhận diện dấu vân tay để ngăn chặn sao chép trái phép các tác phẩm có bản quyền.                                                            |   2    |    V    |
| 7.7.4 | Xác nhận rằng tất cả tài nguyên đa phương tiện được tạo ra được ký bằng mật mã, được gắn watermark, hoặc được nhúng siêu dữ liệu nguồn gốc chống sửa đổi để đảm bảo khả năng truy vết ở các bước sau.                 |   3    |   D/V   |
| 7.7.5 | Xác minh rằng các nỗ lực vượt qua biện pháp (ví dụ: làm rối prompt, tiếng lóng, diễn đạt mang tính thù địch) được phát hiện, ghi lại và giới hạn theo tần suất; việc lạm dụng lặp lại được đưa lên hệ thống giám sát. |   3    |    V    |

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

