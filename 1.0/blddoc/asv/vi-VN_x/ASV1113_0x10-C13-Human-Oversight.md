# C13 Giám sát con người, Trách nhiệm và Quản trị

## Mục tiêu Kiểm soát

Chương này cung cấp các yêu cầu để duy trì sự giám sát của con người và các chuỗi trách nhiệm rõ ràng trong các hệ thống AI, đảm bảo khả năng giải thích, tính minh bạch và quản lý đạo đức trong suốt vòng đời của AI.

---

## C13.1 Cơ chế Ngắt kết nối khẩn cấp và Ghi đè

Cung cấp các phương án tắt hoặc phục hồi khi phát hiện hành vi không an toàn của hệ thống AI.

|   #    | Mô tả                                                                                                                         | Cấp độ | Vai trò |
| :----: | ----------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 13.1.1 | Xác minh rằng có cơ chế công tắc ngắt thủ công để ngay lập tức dừng việc suy diễn và đầu ra của mô hình AI.                   |   1    |   D/V   |
| 13.1.2 | Xác minh rằng các biện pháp kiểm soát ghi đè chỉ có thể truy cập bởi nhân sự được ủy quyền.                                   |   1    |    D    |
| 13.1.3 | Xác minh rằng các quy trình hoàn tác có thể khôi phục lại các phiên bản mô hình trước đó hoặc các hoạt động ở chế độ an toàn. |   3    |   D/V   |
| 13.1.4 | Xác minh rằng các cơ chế ghi đè được kiểm tra thường xuyên.                                                                   |   3    |    V    |

---

## C13.2 Các Điểm Kiểm Tra Quyết Định Có Con Người Tham Gia

Yêu cầu phê duyệt của con người khi mức độ rủi ro vượt quá ngưỡng đã định trước.

|   #    | Mô tả                                                                                                                                                          | Cấp độ | Vai trò |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 13.2.1 | Xác minh rằng các quyết định AI có rủi ro cao yêu cầu phải có sự phê duyệt rõ ràng của con người trước khi thực thi.                                           |   1    |   D/V   |
| 13.2.2 | Xác minh rằng các ngưỡng rủi ro được xác định rõ ràng và tự động kích hoạt quy trình xem xét của con người.                                                    |   1    |    D    |
| 13.2.3 | Xác minh rằng các quyết định nhạy cảm về thời gian có các quy trình dự phòng khi không thể nhận được sự phê duyệt của con người trong khung thời gian yêu cầu. |   2    |    D    |
| 13.2.4 | Xác minh rằng các quy trình leo thang xác định rõ các cấp độ thẩm quyền cho các loại quyết định hoặc danh mục rủi ro khác nhau, nếu có.                        |   3    |   D/V   |

---

## C13.3 Chuỗi Trách Nhiệm & Khả Năng Kiểm Toán

Ghi lại các hành động của người vận hành và các quyết định của mô hình.

|   #    | Mô tả                                                                                                                                                               | Cấp độ | Vai trò |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 13.3.1 | Xác minh rằng tất cả các quyết định của hệ thống AI và các can thiệp của con người được ghi lại với dấu thời gian, danh tính người dùng và lý do đưa ra quyết định. |   1    |   D/V   |
| 13.3.2 | Xác minh rằng các bản ghi kiểm toán không thể bị sửa đổi và bao gồm các cơ chế xác minh tính toàn vẹn.                                                              |   2    |    D    |

---

## C13.4 Kỹ thuật Trí tuệ Nhân tạo Có thể Giải thích được

Tầm quan trọng của đặc điểm bề mặt, phản sự thật, và giải thích cục bộ.

|   #    | Mô tả                                                                                                                                                                     | Cấp độ | Vai trò |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 13.4.1 | Xác minh rằng các hệ thống AI cung cấp các giải thích cơ bản cho các quyết định của chúng dưới dạng có thể đọc hiểu đối với con người.                                    |   1    |   D/V   |
| 13.4.2 | Xác minh rằng chất lượng giải thích được đánh giá thông qua các nghiên cứu và chỉ số đánh giá của con người.                                                              |   2    |    V    |
| 13.4.3 | Xác minh rằng điểm quan trọng của tính năng hoặc các phương pháp gán trọng số (SHAP, LIME, v.v.) có sẵn cho các quyết định quan trọng.                                    |   3    |   D/V   |
| 13.4.4 | Xác minh rằng các giải thích phản thực tế cho thấy cách các đầu vào có thể được điều chỉnh để thay đổi kết quả, nếu áp dụng cho trường hợp sử dụng và lĩnh vực tương ứng. |   3    |    V    |

---

## C13.5 Thẻ Mô hình & Công khai Sử dụng

Duy trì thẻ mô hình cho mục đích sử dụng dự kiến, chỉ số hiệu suất và các cân nhắc đạo đức.

|   #    | Mô tả                                                                                                                                                                              | Cấp độ | Vai trò |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 13.5.1 | Xác minh rằng các thẻ mô hình ghi lại các trường hợp sử dụng dự kiến, các hạn chế và các chế độ lỗi đã biết.                                                                       |   1    |    D    |
| 13.5.2 | Xác nhận rằng các chỉ số hiệu suất trong các trường hợp sử dụng phù hợp khác nhau đã được công bố.                                                                                 |   1    |   D/V   |
| 13.5.3 | Xác nhận rằng các cân nhắc đạo đức, đánh giá thiên vị, đánh giá công bằng, đặc điểm dữ liệu đào tạo và các hạn chế dữ liệu đào tạo đã biết được ghi chép và cập nhật thường xuyên. |   2    |    D    |
| 13.5.4 | Xác minh rằng các thẻ mô hình được kiểm soát phiên bản và duy trì trong suốt vòng đời mô hình với việc theo dõi thay đổi.                                                          |   2    |   D/V   |

---

## C13.6 Định lượng độ không chắc chắn

Truyền đạt các điểm số độ tin cậy hoặc các đo lường entropy trong các phản hồi.

|   #    | Mô tả                                                                                                                     | Cấp độ | Vai trò |
| :----: | ------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 13.6.1 | Xác minh rằng các hệ thống AI cung cấp điểm tin cậy hoặc các biện pháp không chắc chắn cùng với kết quả đầu ra của chúng. |   1    |    D    |
| 13.6.2 | Xác minh rằng ngưỡng không chắc chắn kích hoạt việc xem xét thêm bởi con người hoặc các đường dẫn quyết định thay thế.    |   2    |   D/V   |
| 13.6.3 | Xác minh rằng các phương pháp định lượng sự không chắc chắn được hiệu chuẩn và xác thực đối với dữ liệu sự thật cơ bản.   |   2    |    V    |
| 13.6.4 | Xác minh rằng sự lan truyền bất định được duy trì qua các quy trình làm việc AI đa bước.                                  |   3    |   D/V   |

---

## C13.7 Báo Cáo Minh Bạch Hướng Đến Người Dùng

Cung cấp các báo cáo định kỳ về các sự cố, sự trôi dạt và việc sử dụng dữ liệu.

|   #    | Mô tả                                                                                                                                     | Cấp độ | Vai trò |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 13.7.1 | Xác minh rằng các chính sách sử dụng dữ liệu và thực hành quản lý sự đồng ý của người dùng được truyền đạt rõ ràng tới các bên liên quan. |   1    |   D/V   |
| 13.7.2 | Xác minh rằng các đánh giá tác động của AI đã được tiến hành và kết quả được bao gồm trong báo cáo.                                       |   2    |   D/V   |
| 13.7.3 | Xác minh rằng các báo cáo minh bạch được công bố định kỳ công khai các sự cố AI và các chỉ số vận hành với mức độ chi tiết hợp lý.        |   2    |   D/V   |

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

