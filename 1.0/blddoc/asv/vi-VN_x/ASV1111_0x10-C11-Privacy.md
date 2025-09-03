# 11 Bảo vệ quyền riêng tư và Quản lý dữ liệu cá nhân

## Mục tiêu kiểm soát

Giữ vững cam kết quyền riêng tư nghiêm ngặt trên toàn vòng đời AI — từ thu thập, huấn luyện, suy diễn đến ứng phó sự cố — để dữ liệu cá nhân chỉ được xử lý khi có sự đồng thuận rõ ràng, phạm vi tối thiểu cần thiết, xóa dữ liệu có thể được chứng thực, và các đảm bảo quyền riêng tư chính thức.

---

## 11.1 Ẩn danh và Tối thiểu hóa dữ liệu

|   #    | Mô tả                                                                                                                                              | Cấp độ | Vai trò |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 11.1.1 | Xác minh rằng các nhận dạng trực tiếp và nhận dạng bán định danh đã bị loại bỏ và được băm.                                                        |   1    |   D/V   |
| 11.1.2 | Xác minh rằng các kiểm toán tự động đo được k-anonymity/l-diversity và cảnh báo khi các ngưỡng giảm xuống dưới mức được quy định trong chính sách. |   2    |   D/V   |
| 11.1.3 | Xác minh rằng các báo cáo về mức độ quan trọng của đặc trưng trong mô hình không có rò rỉ danh tính vượt quá ε = 0.01 của thông tin tương hỗ.      |   2    |    V    |
| 11.1.4 | Xác minh rằng các chứng minh chính thức hoặc chứng nhận dữ liệu tổng hợp cho thấy nguy cơ nhận dạng lại ≤ 0.05 ngay cả khi bị tấn công liên kết.   |   3    |    V    |

---

## 11.2 Right-to-be-Forgotten & thực thi xóa dữ liệu

|   #    | Mô tả                                                                                                                                                                                         | Cấp độ | Vai trò |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 11.2.1 | Xác nhận rằng các yêu cầu xóa dữ liệu chủ thể được lan truyền tới các tập dữ liệu thô, điểm kiểm tra, nhúng, nhật ký và sao lưu trong khuôn khổ thỏa thuận mức độ dịch vụ (SLA) dưới 30 ngày. |   1    |   D/V   |
| 11.2.2 | Xác minh rằng các quy trình "machine-unlearning" có thể được tái huấn luyện trực tiếp hoặc ước lượng việc xóa bằng cách sử dụng các thuật toán xóa được chứng nhận.                           |   2    |    D    |
| 11.2.3 | Xác nhận rằng đánh giá mô hình bóng cho thấy các bản ghi đã bị quên ảnh hưởng đến dưới 1% đầu ra sau khi thực hiện khử học.                                                                   |   2    |    V    |
| 11.2.4 | Xác minh rằng các sự kiện xóa được ghi lại một cách bất biến và có thể kiểm toán cho cơ quan quản lý.                                                                                         |   3    |    V    |

---

## 11.3 Các biện pháp bảo vệ quyền riêng tư vi phân

|   #    | Mô tả                                                                                                                        | Cấp độ | Vai trò |
| :----: | ---------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 11.3.1 | Xác minh rằng các bảng điều khiển kế toán tổn thất quyền riêng tư sẽ cảnh báo khi ε tích lũy vượt quá ngưỡng của chính sách. |   2    |   D/V   |
| 11.3.2 | Xác minh rằng các kiểm toán quyền riêng tư hộp đen ước lượng ε̂ trong vòng 10% so với giá trị được công bố.                  |   2    |    V    |
| 11.3.3 | Xác nhận rằng các chứng minh chính thức bao phủ tất cả các tinh chỉnh sau đào tạo và các nhúng.                              |   3    |    V    |

---

## 11.4 Mục đích-Giới hạn & Phạm vi-Mở rộng Bảo vệ

|   #    | Mô tả                                                                                                                                    | Cấp độ | Vai trò |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 11.4.1 | Xác nhận rằng mọi tập dữ liệu và điểm kiểm tra mô hình đều mang nhãn mục đích có thể đọc được bằng máy và khớp với sự đồng ý ban đầu.    |   1    |    D    |
| 11.4.2 | Xác minh rằng các bộ giám sát thời gian chạy phát hiện các truy vấn không nhất quán với mục đích được khai báo và kích hoạt từ chối mềm. |   1    |   D/V   |
| 11.4.3 | Xác minh rằng các cổng dựa trên policy-as-code chặn việc tái triển khai các mô hình đến các miền mới mà không được DPIA xem xét.         |   3    |    D    |
| 11.4.4 | Xác minh rằng các bằng chứng truy vết chính thức cho thấy mọi vòng đời dữ liệu cá nhân vẫn nằm trong phạm vi được đồng ý.                |   3    |    V    |

---

## 11.5 Quản lý sự đồng ý và theo dõi dựa trên căn cứ hợp pháp

|   #    | Mô tả                                                                                                                                                     | Cấp độ | Vai trò |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 11.5.1 | Xác nhận rằng một Nền tảng Quản lý Sự đồng ý (CMP) ghi nhận trạng thái đồng ý tham gia, mục đích và thời gian lưu giữ dữ liệu cho từng đối tượng dữ liệu. |   1    |   D/V   |
| 11.5.2 | Xác minh rằng các API tiết lộ token đồng ý; các mô hình phải xác thực phạm vi của token trước khi suy diễn.                                               |   2    |    D    |
| 11.5.3 | Xác minh rằng sự đồng ý bị từ chối hoặc rút lại sẽ khiến các pipeline xử lý dừng hoạt động trong vòng 24 giờ.                                             |   2    |   D/V   |

---

## 11.6 Học liên bang với các biện pháp kiểm soát quyền riêng tư

|   #    | Mô tả                                                                                                                       | Cấp độ | Vai trò |
| :----: | --------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 11.6.1 | Xác minh rằng các cập nhật của máy khách thực hiện thêm nhiễu theo riêng tư vi phân cục bộ trước khi tổng hợp.              |   1    |    D    |
| 11.6.2 | Xác minh rằng các chỉ số huấn luyện được đảm bảo riêng tư vi phân và không bao giờ tiết lộ mất mát của một client duy nhất. |   2    |   D/V   |
| 11.6.3 | Xác minh rằng tổng hợp kháng nhiễm độc dữ liệu (ví dụ: Krum/Trimmed-Mean) đã được bật.                                      |   2    |    V    |
| 11.6.4 | Xác minh rằng các chứng minh hình thức cho thấy tổng ngân sách ε với tổn thất tiện ích dưới 5.                              |   3    |    V    |

---

### Tài liệu tham khảo

* [GDPR & AI Compliance Best Practices](https://www.exabeam.com/explainers/gdpr-compliance/the-intersection-of-gdpr-and-ai-and-6-compliance-best-practices/)
* [EU Parliament Study on GDPR & AI, 2020](https://www.europarl.europa.eu/RegData/etudes/STUD/2020/641530/EPRS_STU%282020%29641530_EN.pdf)
* [ISO 31700-1:2023 — Privacy by Design for Consumer Products](https://www.iso.org/standard/84977.html)
* [NIST Privacy Framework 1.1 (2025 Draft)](https://www.nist.gov/privacy-framework)
* [Machine Unlearning: Right-to-Be-Forgotten Techniques](https://www.kaggle.com/code/tamlhp/machine-unlearning-the-right-to-be-forgotten)
* [A Survey of Machine Unlearning, 2024](https://arxiv.org/html/2209.02299v6)
* [Auditing DP-SGD — ArXiv 2024](https://arxiv.org/html/2405.14106v4)
* [DP-SGD Explained — PyTorch Blog](https://medium.com/pytorch/differential-privacy-series-part-1-dp-sgd-algorithm-explained-12512c3959a3)
* [Purpose-Limitation for AI — IJLIT 2025](https://academic.oup.com/ijlit/article/doi/10.1093/ijlit/eaaf003/8121663)
* [Data-Protection Considerations for AI — URM Consulting](https://www.urmconsulting.com/blog/data-protection-considerations-for-artificial-intelligence-ai)
* [Top Consent-Management Platforms, 2025](https://www.enzuzo.com/blog/best-consent-management-platforms)
* [Secure Aggregation in DP Federated Learning — ArXiv 2024](https://arxiv.org/abs/2407.19286)

