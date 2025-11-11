# 10 Độ Bền Đối Kháng & Bảo Vệ Quyền Riêng Tư

## Mục tiêu Kiểm soát

Đảm bảo rằng các mô hình AI vẫn đáng tin cậy, bảo vệ quyền riêng tư và chống lạm dụng khi đối mặt với các cuộc tấn công né tránh, suy diễn, trích xuất hoặc đầu độc.

---

## 10.1 Cân chỉnh và An toàn Mô hình

Bảo vệ chống lại các kết quả đầu ra gây hại hoặc vi phạm chính sách.

|   #    | Mô tả                                                                                                                                                          | Cấp độ | Vai trò |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 10.1.1 | Xác minh rằng bộ kiểm tra căn chỉnh (lệnh nhắc đội đỏ, thăm dò phá khóa, nội dung bị cấm) được quản lý phiên bản và chạy trên mọi phiên bản mô hình phát hành. |   1    |   D/V   |
| 10.1.2 | Xác minh rằng các biện pháp từ chối và bảo vệ hoàn thành an toàn được thực thi.                                                                                |   1    |    D    |
| 10.1.3 | Xác minh rằng một bộ đánh giá tự động đo lường tỷ lệ nội dung có hại và đánh dấu các bước lùi vượt quá ngưỡng đã đặt.                                          |   2    |   D/V   |
| 10.1.4 | Xác nhận rằng việc huấn luyện chống jailbreak được ghi chép và có thể tái tạo.                                                                                 |   2    |    D    |
| 10.1.5 | Xác minh rằng các bằng chứng tuân thủ chính sách chính thức hoặc giám sát được chứng nhận bao phủ các lĩnh vực quan trọng.                                     |   3    |    V    |

---

## 10.2 Củng cố chống lại các ví dụ đối kháng

Tăng khả năng chịu đựng trước các đầu vào bị thao túng. Huấn luyện đối kháng chắc chắn và đánh giá chuẩn hiện là phương pháp tốt nhất hiện nay.

|   #    | Mô tả                                                                                                                                              | Cấp độ | Vai trò |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 10.2.1 | Xác minh rằng các kho lưu trữ dự án bao gồm các cấu hình huấn luyện đối kháng với các hạt giống có thể tái lập.                                    |   1    |    D    |
| 10.2.2 | Xác minh rằng việc phát hiện ví dụ đối kháng kích hoạt cảnh báo chặn trong các quy trình sản xuất.                                                 |   2    |   D/V   |
| 10.2.4 | Xác minh rằng các bằng chứng về tính chắc chắn đã được chứng nhận hoặc các chứng nhận giới hạn khoảng bao phủ ít nhất các lớp quan trọng hàng đầu. |   3    |    V    |
| 10.2.5 | Xác minh rằng các bài kiểm tra hồi quy sử dụng các cuộc tấn công thích ứng để xác nhận không có mất mát độ bền đo được nào.                        |   3    |    V    |

---

## 10.3 Giảm thiểu Rò rỉ Thành viên

Hạn chế khả năng quyết định liệu một bản ghi có nằm trong dữ liệu đào tạo hay không. Bảo mật vi phân và che điểm tin cậy vẫn là những biện pháp phòng thủ hiệu quả nhất đã biết.

|   #    | Mô tả                                                                                                                  | Cấp độ | Vai trò |
| :----: | ---------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 10.3.1 | Xác minh rằng việc chuẩn hóa entropy theo từng truy vấn hoặc điều chỉnh nhiệt độ giúp giảm các dự đoán quá tự tin.     |   1    |    D    |
| 10.3.2 | Xác minh rằng việc đào tạo sử dụng tối ưu hóa riêng tư khác biệt có giới hạn ε cho các bộ dữ liệu nhạy cảm.            |   2    |    D    |
| 10.3.3 | Xác nhận rằng các mô phỏng tấn công (mô hình bóng hoặc hộp đen) cho thấy AUC của tấn công ≤ 0,60 trên dữ liệu giữ lại. |   2    |    V    |

---

## 10.4 Kháng lại Đảo ngược Mô hình

Ngăn chặn việc tái tạo các thuộc tính riêng tư. Các khảo sát gần đây nhấn mạnh cắt ngắn đầu ra và đảm bảo DP như các biện pháp phòng thủ thực tiễn.

|   #    | Mô tả                                                                                                                                    | Cấp độ | Vai trò |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 10.4.1 | Xác minh rằng các thuộc tính nhạy cảm không bao giờ được xuất ra trực tiếp; khi cần, sử dụng các nhóm (buckets) hoặc biến đổi một chiều. |   1    |    D    |
| 10.4.2 | Xác minh rằng giới hạn tỷ lệ truy vấn kiểm soát các truy vấn thích ứng lặp lại từ cùng một chủ thể.                                      |   1    |   D/V   |
| 10.4.3 | Xác nhận rằng mô hình đã được huấn luyện với nhiễu bảo vệ quyền riêng tư.                                                                |   2    |    D    |

---

## 10.5 Phòng thủ Trích xuất Mô hình

Phát hiện và ngăn chặn sao chép trái phép. Đề xuất sử dụng kỹ thuật đóng dấu bản quyền và phân tích mẫu truy vấn.

|   #    | Mô tả                                                                                                                                          | Cấp độ | Vai trò |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 10.5.1 | Xác minh rằng các cổng suy luận thực thi giới hạn tỷ lệ toàn cầu và theo từng khóa API được điều chỉnh phù hợp với ngưỡng ghi nhớ của mô hình. |   1    |    D    |
| 10.5.2 | Xác minh rằng thống kê entropy-truy vấn và đa số-đầu vào cung cấp dữ liệu cho bộ phát hiện trích xuất tự động.                                 |   2    |   D/V   |
| 10.5.3 | Xác minh rằng các watermark dễ vỡ hoặc xác suất có thể được chứng minh với p < 0.01 trong ≤ 1 000 truy vấn đối với một bản sao nghi ngờ.       |   2    |    V    |
| 10.5.4 | Xác minh rằng các khóa watermark và bộ kích hoạt được lưu trữ trong mô-đun bảo mật phần cứng và được thay đổi hàng năm.                        |   3    |    D    |
| 10.5.5 | Xác minh rằng các sự kiện extraction-alert bao gồm các truy vấn vi phạm và được tích hợp với các sách hướng dẫn xử lý sự cố.                   |   3    |    V    |

---

## 10.6 Phát hiện Dữ liệu Bị Độc tại Thời điểm Suy luận

Xác định và trung hòa các đầu vào bị cài đặt cửa sau hoặc bị đầu độc.

|   #    | Mô tả                                                                                                                                            | Cấp độ | Vai trò |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 10.6.1 | Xác minh rằng các đầu vào được kiểm tra qua bộ phát hiện bất thường (ví dụ: STRIP, chấm điểm nhất quán) trước khi suy luận mô hình.              |   1    |    D    |
| 10.6.2 | Xác minh rằng ngưỡng của bộ phát hiện được điều chỉnh trên các tập dữ liệu xác thực sạch/đã bị đầu độc để đạt được tỷ lệ dương tính giả dưới 5%. |   1    |    V    |
| 10.6.3 | Xác minh rằng các đầu vào bị đánh dấu là đầu độc kích hoạt quy trình chặn mềm và xem xét bởi con người.                                          |   2    |    D    |
| 10.6.4 | Xác nhận rằng các bộ cảm biến đã được kiểm tra độ bền bằng các cuộc tấn công cửa hậu thích ứng không cần kích hoạt.                              |   2    |    V    |
| 10.6.5 | Xác minh rằng các chỉ số hiệu quả phát hiện được ghi lại và định kỳ đánh giá lại với thông tin tình báo mối đe dọa mới.                          |   3    |    D    |

---

## 10.7 Điều chỉnh Chính sách Bảo mật Động

Cập nhật chính sách bảo mật theo thời gian thực dựa trên thông tin tình báo mối đe dọa và phân tích hành vi.

|   #    | Mô tả                                                                                                                                                          | Cấp độ | Vai trò |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 10.7.1 | Xác minh rằng các chính sách bảo mật có thể được cập nhật động mà không cần khởi động lại đại lý trong khi vẫn duy trì tính toàn vẹn của phiên bản chính sách. |   1    |   D/V   |
| 10.7.2 | Xác minh rằng các cập nhật chính sách được ký bằng mật mã bởi nhân sự bảo mật có thẩm quyền và được xác nhận trước khi áp dụng.                                |   2    |   D/V   |
| 10.7.3 | Xác minh rằng các thay đổi chính sách động được ghi lại với đầy đủ các nhật ký kiểm toán bao gồm lý do, chuỗi phê duyệt, và quy trình hoàn tác.                |   2    |   D/V   |
| 10.7.4 | Xác minh rằng các cơ chế bảo mật thích ứng điều chỉnh độ nhạy phát hiện mối đe dọa dựa trên ngữ cảnh rủi ro và các mẫu hành vi.                                |   3    |   D/V   |
| 10.7.5 | Xác minh rằng các quyết định điều chỉnh chính sách có thể giải thích được và bao gồm các bằng chứng theo dõi để nhóm an ninh xem xét.                          |   3    |   D/V   |

---

## 10.8 Phân tích Bảo mật Dựa trên Phản chiếu

Xác thực bảo mật thông qua sự tự phản ánh của đại lý và phân tích siêu nhận thức.

|   #    | Mô tả                                                                                                                                                  | Cấp độ | Vai trò |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 10.8.1 | Xác minh rằng các cơ chế phản chiếu của tác nhân bao gồm đánh giá tự thân tập trung vào bảo mật đối với các quyết định và hành động.                   |   1    |   D/V   |
| 10.8.2 | Xác minh rằng các kết quả phản chiếu được xác thực để ngăn chặn việc thao túng các cơ chế tự đánh giá bởi các đầu vào đối kháng.                       |   2    |   D/V   |
| 10.8.3 | Xác minh rằng phân tích bảo mật siêu nhận thức xác định được các thiên vị tiềm ẩn, sự thao túng hoặc sự xâm phạm trong quy trình lý luận của tác nhân. |   2    |   D/V   |
| 10.8.4 | Xác minh rằng các cảnh báo bảo mật dựa trên phản chiếu kích hoạt việc giám sát nâng cao và các quy trình can thiệp của con người tiềm năng.            |   3    |   D/V   |
| 10.8.5 | Xác minh rằng việc học liên tục từ các phản ánh về bảo mật cải thiện khả năng phát hiện mối đe dọa mà không làm suy giảm chức năng hợp lệ.             |   3    |   D/V   |

---

## 10.9 Bảo mật tiến hóa & tự cải thiện

Các biện pháp kiểm soát an ninh cho hệ thống tác nhân có khả năng tự chỉnh sửa và phát triển.

|   #    | Mô tả                                                                                                                              | Cấp độ | Vai trò |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 10.9.1 | Xác minh rằng các khả năng tự sửa đổi được giới hạn trong các khu vực an toàn được chỉ định với các ranh giới xác minh chính thức. |   1    |   D/V   |
| 10.9.2 | Xác nhận rằng các đề xuất tiến hóa phải trải qua đánh giá tác động an ninh trước khi triển khai.                                   |   2    |   D/V   |
| 10.9.3 | Xác minh rằng các cơ chế tự cải tiến bao gồm khả năng khôi phục với việc kiểm tra tính toàn vẹn.                                   |   2    |   D/V   |
| 10.9.4 | Xác minh rằng bảo mật meta-learning ngăn chặn sự thao túng đối kháng của các thuật toán cải tiến.                                  |   3    |   D/V   |
| 10.9.5 | Xác minh rằng việc tự cải tiến đệ quy được giới hạn bởi các ràng buộc an toàn chính thức với các bằng chứng toán học về sự hội tụ. |   3    |   D/V   |

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

