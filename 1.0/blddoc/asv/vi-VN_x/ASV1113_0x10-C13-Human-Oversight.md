# Giám sát của con người, Trách nhiệm giải trình và Quản trị

## Mục tiêu kiểm soát

Chương này đưa ra các yêu cầu về việc duy trì sự giám sát của con người và chuỗi trách nhiệm rõ ràng trong các hệ thống AI, đồng thời đảm bảo khả năng giải thích, tính minh bạch và quản trị đạo đức trong suốt vòng đời của AI.

---

## C13.1 Cơ chế tắt khẩn cấp và ghi đè

Cung cấp các lộ trình tắt nguồn hoặc khôi phục lại trạng thái trước khi hệ thống AI có hành vi không an toàn được phát hiện.

|   #    | Mô tả                                                                                                                     | Cấp độ | Vai trò |
| :----: | ------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 13.1.1 | Xác nhận rằng tồn tại một cơ chế công tắc tắt thủ công để ngay lập tức ngừng quá trình suy diễn và đầu ra của mô hình AI. |   1    |   D/V   |
| 13.1.2 | Đảm bảo rằng các điều khiển ghi đè chỉ có thể được truy cập bởi những nhân sự được ủy quyền.                              |   1    |    D    |
| 13.1.3 | Xác nhận rằng các thủ tục hoàn nguyên có thể quay về các phiên bản mô hình trước đó hoặc các hoạt động ở safe-mode.       |   3    |   D/V   |
| 13.1.4 | Xác minh rằng các cơ chế ghi đè được kiểm tra định kỳ.                                                                    |   3    |    V    |

---

## C13.2 Human-in-the-Loop Điểm kiểm tra quyết định

Yêu cầu phê duyệt của con người khi mức độ rủi ro vượt quá ngưỡng rủi ro được xác định trước.

|   #    | Mô tả                                                                                                                                                               | Cấp độ | Vai trò |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 13.2.1 | Xác minh rằng các quyết định AI có rủi ro cao đòi hỏi sự phê duyệt rõ ràng từ con người trước khi thực thi.                                                         |   1    |   D/V   |
| 13.2.2 | Xác minh rằng ngưỡng rủi ro được định nghĩa rõ ràng và tự động kích hoạt các quy trình xem xét của con người.                                                       |   1    |    D    |
| 13.2.3 | Xác minh rằng các quyết định nhạy cảm về thời gian có các biện pháp dự phòng khi sự phê duyệt của con người không thể được thực hiện trong khung thời gian yêu cầu. |   2    |    D    |
| 13.2.4 | Xác minh rằng quy trình leo thang định rõ mức thẩm quyền cho các loại quyết định khác nhau hoặc các loại rủi ro, nếu áp dụng.                                       |   3    |   D/V   |

---

## C13.3 Chuỗi chịu trách nhiệm và khả năng kiểm toán

Ghi lại hành động của người vận hành và quyết định của mô hình.

|   #    | Mô tả                                                                                                                                                     | Cấp độ | Vai trò |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 13.3.1 | Xác minh rằng mọi quyết định của hệ thống AI và các can thiệp của con người đều được ghi lại với dấu thời gian, danh tính người dùng và lý do quyết định. |   1    |   D/V   |
| 13.3.2 | Xác minh rằng nhật ký kiểm toán không thể bị sửa đổi và bao gồm các cơ chế xác minh tính toàn vẹn.                                                        |   2    |    D    |

---

## C13.4 Các kỹ thuật Explainable-AI

Tầm quan trọng của đặc trưng bề mặt, counterfactuals và giải thích cục bộ.

|   #    | Mô tả                                                                                                                                                            | Cấp độ | Vai trò |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 13.4.1 | Xác nhận rằng các hệ thống AI cung cấp các giải thích cơ bản cho các quyết định của chúng ở định dạng dễ đọc cho con người.                                      |   1    |   D/V   |
| 13.4.2 | Xác nhận chất lượng giải thích thông qua các nghiên cứu đánh giá bởi con người và các thước đo.                                                                  |   2    |    V    |
| 13.4.3 | Xác nhận rằng các điểm tầm quan trọng của đặc trưng hoặc các phương pháp phân bổ đóng góp (SHAP, LIME, v.v.) có sẵn cho các quyết định quan trọng.               |   3    |   D/V   |
| 13.4.4 | Xác nhận rằng các giải thích counterfactual cho thấy cách các đầu vào có thể được chỉnh sửa để thay đổi kết quả, nếu phù hợp với trường hợp sử dụng và lĩnh vực. |   3    |    V    |

---

## C13.5 Thẻ Mô hình và Tiết lộ về Việc Sử Dụng

Duy trì thẻ mô hình cho mục đích sử dụng dự định, các chỉ số hiệu suất và các cân nhắc đạo đức.

|   #    | Mô tả                                                                                                                                                                                           | Cấp độ | Vai trò |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 13.5.1 | Đảm bảo rằng thẻ mô hình ghi lại các trường hợp sử dụng dự định, giới hạn và các chế độ lỗi được biết.                                                                                          |   1    |    D    |
| 13.5.2 | Xác minh rằng các chỉ số hiệu suất cho các trường hợp sử dụng khác nhau đã được công khai.                                                                                                      |   1    |   D/V   |
| 13.5.3 | Đảm bảo rằng các cân nhắc đạo đức, các đánh giá thiên vị, các đánh giá công bằng, đặc điểm dữ liệu huấn luyện và các hạn chế được biết về dữ liệu huấn luyện được ghi nhận và cập nhật định kỳ. |   2    |    D    |
| 13.5.4 | Xác nhận rằng thẻ mô hình được kiểm soát phiên bản và được duy trì xuyên suốt vòng đời của mô hình, với việc theo dõi sự thay đổi.                                                              |   2    |   D/V   |

---

## C13.6 Định lượng bất định

Lan truyền điểm tự tin hoặc các thước đo entropy trong phản hồi.

|   #    | Mô tả                                                                                                        | Cấp độ | Vai trò |
| :----: | ------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 13.6.1 | Xác minh rằng các hệ thống AI cung cấp điểm tự tin hoặc các thước đo bất định kèm theo đầu ra của chúng.     |   1    |    D    |
| 13.6.2 | Xác nhận rằng ngưỡng bất định kích hoạt xem xét bổ sung bởi con người hoặc các đường đi quyết định thay thế. |   2    |   D/V   |
| 13.6.3 | Xác nhận rằng các phương pháp định lượng bất định được hiệu chuẩn và xác thực so với dữ liệu ground truth.   |   2    |    V    |
| 13.6.4 | Xác minh rằng sự lan truyền bất định được duy trì qua các quy trình AI nhiều bước.                           |   3    |   D/V   |

---

## C13.7 Báo cáo minh bạch dành cho người dùng

Cung cấp các thông báo định kỳ về sự cố, độ lệch dữ liệu và việc sử dụng dữ liệu.

|   #    | Mô tả                                                                                                                                             | Cấp độ | Vai trò |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 13.7.1 | Đảm bảo rằng các chính sách sử dụng dữ liệu và thực hành quản lý sự đồng ý của người dùng được truyền đạt một cách rõ ràng tới các bên liên quan. |   1    |   D/V   |
| 13.7.2 | Xác nhận rằng các đánh giá tác động của AI đã được thực hiện và kết quả được đưa vào báo cáo.                                                     |   2    |   D/V   |
| 13.7.3 | Đảm bảo rằng các báo cáo minh bạch được công bố định kỳ tiết lộ các sự cố liên quan đến AI và các chỉ số vận hành ở mức độ hợp lý.                |   2    |   D/V   |

### Tài liệu tham khảo

* [EU Artificial Intelligence Act — Regulation (EU) 2024/1689 (Official Journal, 12 July 2024)](https://eur-lex.europa.eu/eli/reg/2024/1689/oj)
* [ISO/IEC 23894:2023 — Artificial Intelligence — Guidance on Risk Management](https://www.iso.org/standard/77304.html)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements](https://www.iso.org/standard/81230.html)
* [NIST AI Risk Management Framework 1.0](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [NIST SP 800-53 Revision 5 — Security and Privacy Controls](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-53r5.pdf)
* [A Unified Approach to Interpreting Model Predictions (SHAP, ICML 2017)](https://arxiv.org/abs/1705.07874)
* [Model Cards for Model Reporting (Mitchell et al., 2018)](https://arxiv.org/abs/1810.03993)
* [Dropout as a Bayesian Approximation: Representing Model Uncertainty in Deep Learning (Gal & Ghahramani, 2016)](https://arxiv.org/abs/1506.02142)
* [ISO/IEC 24029-2:2023 — Robustness of Neural Networks — Methodology for Formal Methods](https://www.iso.org/standard/79804.html)
* [IEEE 7001-2021 — Transparency of Autonomous Systems](https://standards.ieee.org/ieee/7001/6929/)
* [GDPR — Article 5 "Transparency Principle" (Regulation (EU) 2016/679)](https://eur-lex.europa.eu/legal-content/EN/TXT/PDF/?uri=CELEX%3A32016R0679)
* [Human Oversight under Article 14 of the EU AI Act (Fink, 2025)](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=5147196)

