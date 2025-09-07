# 10 Độ bền chống đối kháng & Phòng thủ quyền riêng tư

## Mục tiêu Kiểm soát

Đảm bảo rằng các mô hình AI vẫn đáng tin cậy, bảo vệ quyền riêng tư và chống lạm dụng khi đối mặt với các cuộc tấn công né tránh, suy luận, trích xuất hoặc đầu độc.

---

## 10.1 Căn chỉnh & An toàn Mô hình

Ngăn ngừa các kết quả đầu ra có hại hoặc vi phạm chính sách.

|   #    | Mô tả                                                                                                                                                                       | Cấp độ | Vai trò |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 10.1.1 | Xác minh rằng bộ kiểm thử căn chỉnh (các lời nhắc đội đỏ, các thủ thuật phá hệ thống, nội dung bị cấm) được quản lý phiên bản và chạy trên mọi phiên bản mô hình phát hành. |   1    |   D/V   |
| 10.1.2 | Xác minh rằng các biện pháp từ chối và bảo vệ hoàn thành an toàn được thi hành.                                                                                             |   1    |    D    |
| 10.1.3 | Xác minh rằng một bộ đánh giá tự động đo lường tỷ lệ nội dung có hại và đánh dấu các suy giảm vượt quá ngưỡng đã đặt.                                                       |   2    |   D/V   |
| 10.1.4 | Xác nhận rằng việc đào tạo chống lại jailbreak được ghi chép đầy đủ và có thể tái tạo.                                                                                      |   2    |    D    |
| 10.1.5 | Xác minh rằng các bằng chứng tuân thủ chính sách chính thức hoặc giám sát được chứng nhận bao phủ các lĩnh vực quan trọng.                                                  |   3    |    V    |

---

## 10.2 Củng cố chống lại Ví dụ Đối kháng

Tăng cường khả năng chịu đựng với các đầu vào bị thao túng. Đào tạo đối kháng chắc chắn và chấm điểm chuẩn là phương pháp tốt nhất hiện nay.

|   #    | Mô tả                                                                                                                              | Cấp độ | Vai trò |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 10.2.1 | Xác minh rằng các kho lưu trữ dự án bao gồm các cấu hình huấn luyện đối kháng với các hạt giống có thể tái lập.                    |   1    |    D    |
| 10.2.2 | Xác minh rằng việc phát hiện các ví dụ mang tính đối kháng kích hoạt cảnh báo chặn trong các quy trình sản xuất.                   |   2    |   D/V   |
| 10.2.4 | Xác minh rằng các bằng chứng độ bền đã được chứng nhận hoặc chứng chỉ giới hạn khoảng bao phủ ít nhất các lớp quan trọng hàng đầu. |   3    |    V    |
| 10.2.5 | Xác nhận rằng các bài kiểm tra hồi quy sử dụng các cuộc tấn công thích ứng để xác nhận không có mất mát độ bền đo được nào.        |   3    |    V    |

---

## 10.3 Giảm thiểu Rò rỉ Thông tin Thành viên

Hạn chế khả năng quyết định liệu một bản ghi có nằm trong dữ liệu huấn luyện hay không. Bảo mật vi phân và che chắn điểm tin cậy vẫn là các biện pháp phòng thủ hiệu quả nhất được biết đến.

|   #    | Mô tả                                                                                                                | Cấp độ | Vai trò |
| :----: | -------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 10.3.1 | Xác minh rằng việc điều chỉnh entropy theo từng truy vấn hoặc điều chỉnh nhiệt độ giúp giảm các dự đoán quá tự tin.  |   1    |    D    |
| 10.3.2 | Xác minh rằng quá trình đào tạo sử dụng tối ưu hóa bảo mật vi sai ε-giới hạn cho các bộ dữ liệu nhạy cảm.            |   2    |    D    |
| 10.3.3 | Xác minh rằng các mô phỏng tấn công (mô hình bóng hoặc hộp đen) cho thấy AUC tấn công ≤ 0.60 trên dữ liệu giữ ngoài. |   2    |    V    |

---

## 10.4 Khả năng kháng lại việc đảo ngược mô hình

Ngăn chặn tái tạo các thuộc tính riêng tư. Các khảo sát gần đây nhấn mạnh việc cắt bớt đầu ra và đảm bảo DP như các biện pháp phòng thủ thực tiễn.

|   #    | Mô tả                                                                                                                                | Cấp độ | Vai trò |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 10.4.1 | Xác minh rằng các thuộc tính nhạy cảm không bao giờ được xuất trực tiếp; khi cần, sử dụng các nhóm hoặc các phép biến đổi một chiều. |   1    |    D    |
| 10.4.2 | Xác minh rằng giới hạn tần suất truy vấn điều chỉnh các truy vấn thích ứng lặp lại từ cùng một chủ thể.                              |   1    |   D/V   |
| 10.4.3 | Xác nhận rằng mô hình đã được huấn luyện với nhiễu bảo vệ quyền riêng tư.                                                            |   2    |    D    |

---

## 10.5 Phòng vệ Trích xuất Mô hình

Phát hiện và ngăn chặn việc sao chép trái phép. Khuyến nghị sử dụng kỹ thuật đóng dấu nước và phân tích mẫu truy vấn.

|   #    | Mô tả                                                                                                                                      | Cấp độ | Vai trò |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 10.5.1 | Xác minh rằng các cổng suy luận áp dụng giới hạn tỷ lệ toàn cầu và từng khóa API phù hợp với ngưỡng ghi nhớ của mô hình.                   |   1    |    D    |
| 10.5.2 | Xác minh rằng thống kê entropy-truy vấn và đa dạng đầu vào cung cấp dữ liệu cho bộ phát hiện trích xuất tự động.                           |   2    |   D/V   |
| 10.5.3 | Xác minh rằng các watermark dễ vỡ hoặc ngẫu nhiên có thể được chứng minh với p < 0,01 trong ≤ 1 000 truy vấn đối với một bản sao nghi vấn. |   2    |    V    |
| 10.5.4 | Xác minh rằng các khóa watermark và bộ kích hoạt được lưu trữ trong mô-đun bảo mật phần cứng và được thay đổi hàng năm.                    |   3    |    D    |
| 10.5.5 | Xác minh rằng các sự kiện extraction-alert bao gồm các truy vấn vi phạm và được tích hợp với các kịch bản phản ứng sự cố.                  |   3    |    V    |

---

## 10.6 Phát hiện dữ liệu bị đầu độc trong thời gian suy luận

Xác định và trung hòa các đầu vào chứa cửa hậu hoặc bị đầu độc.

|   #    | Mô tả                                                                                                                                 | Cấp độ | Vai trò |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 10.6.1 | Xác minh rằng các đầu vào được gửi qua bộ phát hiện dị thường (ví dụ: STRIP, điểm nhất quán) trước khi suy luận mô hình.              |   1    |    D    |
| 10.6.2 | Xác minh rằng các ngưỡng bộ dò được điều chỉnh trên các tập dữ liệu xác thực sạch/nhiễm độc để đạt được tỷ lệ dương tính giả dưới 5%. |   1    |    V    |
| 10.6.3 | Xác minh rằng các đầu vào bị đánh dấu là bị đầu độc kích hoạt quy trình chặn mềm và xem xét của con người.                            |   2    |    D    |
| 10.6.4 | Xác nhận rằng các bộ dò được kiểm tra căng thẳng bằng các cuộc tấn công cửa hậu không kích hoạt thích ứng.                            |   2    |    V    |
| 10.6.5 | Xác nhận rằng các chỉ số hiệu quả phát hiện được ghi lại và định kỳ đánh giá lại với thông tin tình báo mối đe dọa mới.               |   3    |    D    |

---

## 10.7 Thích ứng Chính sách Bảo mật Động

Cập nhật chính sách bảo mật theo thời gian thực dựa trên thông tin tình báo về mối đe dọa và phân tích hành vi.

|   #    | Mô tả                                                                                                                                                     | Cấp độ | Vai trò |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 10.7.1 | Xác minh rằng các chính sách bảo mật có thể được cập nhật động mà không cần khởi động lại agent đồng thời duy trì tính toàn vẹn của phiên bản chính sách. |   1    |   D/V   |
| 10.7.2 | Xác minh rằng các cập nhật chính sách được ký bằng mật mã bởi nhân viên bảo mật được ủy quyền và được xác thực trước khi áp dụng.                         |   2    |   D/V   |
| 10.7.3 | Xác minh rằng các thay đổi chính sách động được ghi lại với đầy đủ dấu vết kiểm toán bao gồm lý do, chuỗi phê duyệt và quy trình phục hồi.                |   2    |   D/V   |
| 10.7.4 | Xác nhận rằng các cơ chế bảo mật thích ứng điều chỉnh độ nhạy phát hiện mối đe dọa dựa trên ngữ cảnh rủi ro và các mẫu hành vi.                           |   3    |   D/V   |
| 10.7.5 | Xác minh rằng các quyết định điều chỉnh chính sách có thể giải thích được và bao gồm các dấu vết bằng chứng để nhóm bảo mật xem xét.                      |   3    |   D/V   |

---

## 10.8 Phân Tích Bảo Mật Dựa Trên Phản Chiếu

Xác thực bảo mật thông qua tự phản ánh của tác nhân và phân tích siêu nhận thức.

|   #    | Mô tả                                                                                                                                                                | Cấp độ | Vai trò |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 10.8.1 | Xác minh rằng các cơ chế phản chiếu của tác nhân bao gồm đánh giá bản thân tập trung vào bảo mật về các quyết định và hành động.                                     |   1    |   D/V   |
| 10.8.2 | Xác minh rằng các đầu ra phản chiếu được kiểm tra để ngăn chặn việc thao túng các cơ chế tự đánh giá bởi các đầu vào đối kháng.                                      |   2    |   D/V   |
| 10.8.3 | Xác minh rằng phân tích bảo mật siêu nhận thức có thể xác định được các thành kiến tiềm ẩn, sự thao túng hoặc sự thỏa hiệp trong các quá trình lý luận của tác nhân. |   2    |   D/V   |
| 10.8.4 | Xác minh rằng các cảnh báo bảo mật dựa trên phản chiếu kích hoạt việc giám sát nâng cao và các quy trình can thiệp của con người tiềm năng.                          |   3    |   D/V   |
| 10.8.5 | Xác minh rằng việc học liên tục từ các phản ánh về bảo mật cải thiện phát hiện mối đe dọa mà không làm giảm chức năng hợp pháp.                                      |   3    |   D/V   |

---

## 10.9 Bảo mật Tiến hóa & Tự Cải thiện

Các biện pháp kiểm soát an ninh cho hệ thống tác nhân có khả năng tự sửa đổi và tiến hóa.

|   #    | Mô tả                                                                                                                            | Cấp độ | Vai trò |
| :----: | -------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 10.9.1 | Xác minh rằng các khả năng tự sửa đổi bị giới hạn trong các khu vực an toàn được chỉ định với ranh giới xác minh chính thức.     |   1    |   D/V   |
| 10.9.2 | Xác minh rằng các đề xuất tiến hóa đều trải qua đánh giá tác động an ninh trước khi thực hiện.                                   |   2    |   D/V   |
| 10.9.3 | Xác minh rằng các cơ chế tự cải tiến bao gồm khả năng hoàn tác kèm theo kiểm tra tính toàn vẹn.                                  |   2    |   D/V   |
| 10.9.4 | Xác minh rằng bảo mật meta-learning ngăn chặn việc thao túng đối kháng các thuật toán cải tiến.                                  |   3    |   D/V   |
| 10.9.5 | Xác minh rằng cải tiến tự động đệ quy bị giới hạn bởi các ràng buộc an toàn chính thức với các bằng chứng toán học về sự hội tụ. |   3    |   D/V   |

---

### Tài liệu tham khảo

* [MITRE ATLAS adversary tactics for ML](https://atlas.mitre.org/)
* [NIST AI Risk Management Framework 1.0, 2023](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [OWASP Top 10 for LLM Applications, 2025](https://owasp.org/www-project-top-10-for-large-language-model-applications/)
* [Adversarial Training: A Survey — Zhao et al., 2024](https://arxiv.org/abs/2410.15042)
* [RobustBench adversarial-robustness benchmark](https://robustbench.github.io/)
* [Membership-Inference & Model-Inversion Risk Survey, 2025](https://www.sciencedirect.com/science/article/abs/pii/S0950705125003867)
* [PURIFIER: Confidence-Score Defense against MI Attacks — AAAI 2023](https://ojs.aaai.org/index.php/AAAI/article/view/26289)
* [Model-Inversion Attacks & Defenses Survey — AI Review, 2025](https://link.springer.com/article/10.1007/s10462-025-11248-0)
* [Comprehensive Defense Framework Against Model Extraction — IEEE TDSC 2024](https://doi.org/10.1109/TDSC.2023.3261327)
* [Fragile Model Watermarking Survey — 2025](https://www.sciencedirect.com/science/article/abs/pii/S0165168425002026)
* [Data Poisoning in Deep Learning: A Survey — Zhao et al., 2025](https://arxiv.org/abs/2503.22759)
* [BDetCLIP: Multimodal Prompting Backdoor Detection — Niu et al., 2024](https://arxiv.org/abs/2405.15269)

