# 10 Độ bền trước tấn công adversarial và Bảo vệ quyền riêng tư

## Mục tiêu kiểm soát

Đảm bảo các mô hình AI luôn đáng tin cậy, được bảo vệ quyền riêng tư và chống bị lạm dụng khi đối mặt với các cuộc tấn công né tránh, suy diễn, rút trích hoặc đầu độc mô hình.

---

## 10.1 Căn chỉnh mô hình và An toàn

Ngăn chặn các đầu ra gây hại hoặc vi phạm chính sách.

|   #    | Mô tả                                                                                                                                                               | Cấp độ | Vai trò |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 10.1.1 | Xác minh rằng alignment test-suite (lời nhắc của đội đỏ, các probe jailbreak, nội dung bị cấm) được kiểm soát phiên bản và chạy trên mỗi bản phát hành của mô hình. |   1    |   D/V   |
| 10.1.2 | Xác minh rằng các hàng rào từ chối và hàng rào đảm bảo hoàn thành an toàn được thực thi.                                                                            |   1    |    D    |
| 10.1.3 | Xác minh rằng một trình đánh giá tự động đo lường tỷ lệ nội dung gây hại và đánh dấu các sự hồi quy vượt quá ngưỡng đã thiết lập.                                   |   2    |   D/V   |
| 10.1.4 | Xác minh rằng đào tạo chống jailbreak được ghi chép đầy đủ và có thể tái tạo.                                                                                       |   2    |    D    |
| 10.1.5 | Xác minh rằng các bằng chứng tuân thủ chính sách mang tính hình thức hoặc giám sát được chứng nhận có bao phủ các miền trọng yếu.                                   |   3    |    V    |

---

## 10.2 Làm cứng ví dụ đối kháng

Tăng khả năng chống chịu trước các đầu vào bị thao túng. Huấn luyện đối kháng mạnh mẽ và chấm điểm chuẩn là thực tiễn tốt nhất hiện nay.

|   #    | Mô tả                                                                                                                                | Cấp độ | Vai trò |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 10.2.1 | Xác minh rằng các kho lưu trữ dự án bao gồm các cấu hình huấn luyện đối kháng với seed có thể tái tạo được.                          |   1    |    D    |
| 10.2.2 | Xác nhận rằng phát hiện ví dụ đối kháng kích hoạt các cảnh báo chặn trong các pipeline sản xuất.                                     |   2    |   D/V   |
| 10.2.4 | Xác nhận rằng các chứng minh độ bền được chứng nhận hoặc chứng chỉ giới hạn theo khoảng bao phủ ít nhất các lớp quan trọng hàng đầu. |   3    |    V    |
| 10.2.5 | Xác nhận rằng các bài kiểm tra hồi quy sử dụng các cuộc tấn công thích ứng để đảm bảo không có sự suy giảm độ bền có thể đo được.    |   3    |    V    |

---

## 10.3 Biện pháp giảm thiểu Membership-Inference

Giới hạn khả năng xác định xem một bản ghi có nằm trong dữ liệu huấn luyện hay không. Riêng tư khác biệt và che giấu điểm tin cậy vẫn là những biện pháp bảo vệ được biết đến có hiệu quả nhất.

|   #    | Mô tả                                                                                                                            | Cấp độ | Vai trò |
| :----: | -------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 10.3.1 | Xác nhận rằng chuẩn hóa entropy theo từng truy vấn hoặc điều chỉnh nhiệt độ làm giảm các dự đoán quá tự tin.                     |   1    |    D    |
| 10.3.2 | Xác nhận rằng quá trình huấn luyện sử dụng tối ưu hóa riêng tư khác biệt có giới hạn ε cho các tập dữ liệu nhạy cảm.             |   2    |    D    |
| 10.3.3 | Xác nhận rằng các mô phỏng tấn công (shadow-model hoặc hộp đen) cho thấy AUC của cuộc tấn công ≤ 0.60 trên dữ liệu được giữ lại. |   2    |    V    |

---

## 10.4 Kháng tấn công đảo ngược mô hình

Ngăn chặn việc tái tạo các thuộc tính riêng tư. Các khảo sát gần đây nhấn mạnh việc rút ngắn đầu ra và các đảm bảo DP như các biện pháp bảo vệ thực tế.

|   #    | Mô tả                                                                                                                         | Cấp độ | Vai trò |
| :----: | ----------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 10.4.1 | Xác minh rằng các thuộc tính nhạy cảm không bao giờ được xuất trực tiếp; khi cần, hãy sử dụng bucket hoặc biến đổi một chiều. |   1    |    D    |
| 10.4.2 | Xác minh rằng giới hạn tần suất truy vấn đang điều tiết các truy vấn thích nghi lặp lại từ cùng chủ thể xác thực.             |   1    |   D/V   |
| 10.4.3 | Xác minh rằng mô hình được huấn luyện với nhiễu bảo vệ quyền riêng tư.                                                        |   2    |    D    |

---

## 10.5 Bảo vệ chống rút trích mô hình

Phát hiện và ngăn chặn sao chép trái phép. Dấu nước và phân tích mẫu truy vấn được khuyến nghị.

|   #    | Mô tả                                                                                                                                                          | Cấp độ | Vai trò |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 10.5.1 | Đảm bảo rằng các cổng suy diễn thực thi các giới hạn lưu lượng toàn cầu và theo từng khóa API, được tinh chỉnh theo ngưỡng ghi nhớ của mô hình.                |   1    |    D    |
| 10.5.2 | Xác nhận rằng entropy của truy vấn và thống kê đa dạng đầu vào cung cấp cho một bộ phát hiện trích xuất tự động.                                               |   2    |   D/V   |
| 10.5.3 | Xác minh rằng các dấu nước mong manh hoặc ngẫu nhiên có thể được chứng minh với p < 0.01 trong ≤ 1 000 lượt truy vấn đối với một bản sao bị nghi ngờ sao chép. |   2    |    V    |
| 10.5.4 | Xác minh rằng các khóa watermark và bộ kích hoạt được lưu trữ trong một thiết bị bảo mật phần cứng (HSM) và được xoay vòng hàng năm.                           |   3    |    D    |
| 10.5.5 | Xác nhận rằng các sự kiện cảnh báo trích xuất bao gồm các truy vấn vi phạm và được tích hợp với các kịch bản ứng phó sự cố.                                    |   3    |    V    |

---

## 10.6 Phát hiện dữ liệu-đầu độc tại thời điểm suy diễn

Nhận diện và vô hiệu hóa các đầu vào bị cài cửa hậu hoặc bị đầu độc.

|   #    | Mô tả                                                                                                                                      | Cấp độ | Vai trò |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 10.6.1 | Xác nhận rằng đầu vào đã được đưa qua một bộ phát hiện bất thường (ví dụ: STRIP, điểm đánh giá tính nhất quán) trước khi mô hình suy diễn. |   1    |    D    |
| 10.6.2 | Xác nhận rằng ngưỡng của bộ phát hiện được điều chỉnh trên các tập xác thực sạch và bị nhiễm độc để đạt được ít hơn 5% dương tính giả.     |   1    |    V    |
| 10.6.3 | Xác minh rằng các đầu vào bị đánh dấu là độc hại kích hoạt chặn mềm và quy trình xem xét bởi con người.                                    |   2    |    D    |
| 10.6.4 | Xác minh rằng các bộ phát hiện được thử nghiệm chịu tải với các cuộc tấn công cửa hậu thích nghi và không kích hoạt.                       |   2    |    V    |
| 10.6.5 | Xác minh rằng các chỉ số hiệu quả phát hiện được ghi lại và được đánh giá lại định kỳ với thông tin tình báo về mối đe dọa mới.            |   3    |    D    |

---

## 10.7 Thích ứng Chính sách Bảo mật Động

Cập nhật chính sách bảo mật theo thời gian thực dựa trên thông tin tình báo về mối đe dọa và phân tích hành vi.

|   #    | Mô tả                                                                                                                                                               | Cấp độ | Vai trò |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 10.7.1 | Xác minh rằng các chính sách bảo mật có thể được cập nhật một cách động mà không cần khởi động lại agent, đồng thời duy trì tính toàn vẹn của phiên bản chính sách. |   1    |   D/V   |
| 10.7.2 | Xác minh rằng các cập nhật chính sách được ký bằng chữ ký số bởi nhân viên bảo mật được ủy quyền và được xác thực trước khi áp dụng.                                |   2    |   D/V   |
| 10.7.3 | Kiểm tra xem các thay đổi chính sách động được ghi lại với đầy đủ dấu vết kiểm toán, bao gồm lý do, chuỗi phê duyệt và thủ tục quay lui.                            |   2    |   D/V   |
| 10.7.4 | Xác minh rằng các cơ chế bảo mật thích ứng điều chỉnh độ nhạy của phát hiện mối đe dọa dựa trên ngữ cảnh rủi ro và mẫu hành vi.                                     |   3    |   D/V   |
| 10.7.5 | Xác nhận rằng các quyết định thích ứng chính sách có thể giải thích được và bao gồm các dấu vết bằng chứng cho việc xem xét bởi nhóm an ninh.                       |   3    |   D/V   |

---

## 10.8 Phân tích bảo mật dựa trên phản chiếu

Xác thực bảo mật thông qua sự tự phản chiếu của tác nhân và phân tích siêu nhận thức.

|   #    | Mô tả                                                                                                                                                   | Cấp độ | Vai trò |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 10.8.1 | Xác nhận rằng các cơ chế phản chiếu của tác nhân bao gồm đánh giá tự thân tập trung vào an ninh đối với các quyết định và hành động.                    |   1    |   D/V   |
| 10.8.2 | Xác nhận rằng các đầu ra của quá trình suy ngẫm được xác thực để ngăn chặn sự thao túng các cơ chế tự đánh giá bởi các đầu vào đối kháng.               |   2    |   D/V   |
| 10.8.3 | Kiểm tra để đảm bảo rằng phân tích an ninh siêu nhận thức có thể xác định thiên lệch, thao túng hoặc bị xâm phạm trong quá trình suy luận của tác nhân. |   2    |   D/V   |
| 10.8.4 | Xác nhận rằng các cảnh báo bảo mật dựa trên phản chiếu sẽ kích hoạt giám sát nâng cao và có thể kích hoạt các luồng làm việc can thiệp của con người.   |   3    |   D/V   |
| 10.8.5 | Xác minh rằng việc học liên tục từ các phản ánh về bảo mật cải thiện khả năng phát hiện mối đe dọa mà không làm suy giảm chức năng hợp lệ.              |   3    |   D/V   |

---

## 10.9 Tiến hóa và Bảo mật Tự cải thiện

Các biện pháp kiểm soát bảo mật cho hệ thống tác nhân có khả năng tự chỉnh sửa và tiến hóa.

|   #    | Mô tả                                                                                                                                       | Cấp độ | Vai trò |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 10.9.1 | Xác minh rằng khả năng tự chỉnh sửa của hệ thống bị giới hạn trong các khu vực an toàn được chỉ định, với các ranh giới xác thực hình thức. |   1    |   D/V   |
| 10.9.2 | Xác minh rằng các đề xuất tiến hóa được đánh giá tác động bảo mật trước khi triển khai.                                                     |   2    |   D/V   |
| 10.9.3 | Xác minh rằng các cơ chế tự cải thiện có khả năng khôi phục về trạng thái trước và có xác thực tính toàn vẹn.                               |   2    |   D/V   |
| 10.9.4 | Xác minh rằng bảo mật của meta-learning ngăn chặn sự thao túng có chủ đích từ phía kẻ tấn công đối với các thuật toán cải thiện.            |   3    |   D/V   |
| 10.9.5 | Xác minh rằng tự cải thiện đệ quy bị giới hạn bởi các ràng buộc an toàn hình thức với các chứng minh toán học về sự hội tụ.                 |   3    |   D/V   |

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

