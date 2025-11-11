# 11 Bảo vệ quyền riêng tư & Quản lý dữ liệu cá nhân

## Mục tiêu Kiểm soát

Duy trì các cam kết bảo mật nghiêm ngặt trong toàn bộ vòng đời AI—thu thập, huấn luyện, suy luận và phản ứng sự cố—để dữ liệu cá nhân chỉ được xử lý với sự đồng ý rõ ràng, phạm vi tối thiểu cần thiết, xóa dữ liệu có thể chứng minh và các đảm bảo bảo mật chính thức.

---

## 11.1 Ẩn danh & Tối thiểu hóa dữ liệu

|   #    | Mô tả                                                                                                                                                  | Cấp độ | Vai trò |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 11.1.1 | Xác minh rằng các định danh trực tiếp và bán định danh đã được loại bỏ hoặc băm.                                                                       |   1    |   D/V   |
| 11.1.2 | Xác minh rằng các cuộc kiểm tra tự động đo lường k-anonymity/l-diversity và cảnh báo khi các ngưỡng giảm dưới mức chính sách.                          |   2    |   D/V   |
| 11.1.3 | Xác minh rằng các báo cáo tầm quan trọng đặc trưng của mô hình chứng minh không có rò rỉ định danh vượt quá ε = 0.01 thông tin tương hỗ.               |   2    |    V    |
| 11.1.4 | Xác minh rằng các chứng minh hình thức hoặc chứng nhận dữ liệu tổng hợp cho thấy nguy cơ tái nhận dạng ≤ 0.05 ngay cả dưới các cuộc tấn công liên kết. |   3    |    V    |

---

## 11.2 Quyền được quên & Thực thi xóa dữ liệu

|   #    | Mô tả                                                                                                                                                                         | Cấp độ | Vai trò |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 11.2.1 | Xác nhận rằng các yêu cầu xóa dữ liệu cá nhân được truyền đến các bộ dữ liệu thô, điểm kiểm tra, nhúng, nhật ký và sao lưu trong phạm vi thỏa thuận mức dịch vụ dưới 30 ngày. |   1    |   D/V   |
| 11.2.2 | Xác minh rằng các quy trình "machine-unlearning" thực sự đào tạo lại hoặc xóa bỏ gần đúng bằng cách sử dụng các thuật toán xóa học được chứng nhận.                           |   2    |    D    |
| 11.2.3 | Xác minh rằng đánh giá mô hình bóng tối chứng minh các bản ghi đã bị quên ảnh hưởng dưới 1% kết quả sau khi loại bỏ kiến thức.                                                |   2    |    V    |
| 11.2.4 | Xác minh rằng các sự kiện xóa được ghi lại một cách không thể thay đổi và có thể kiểm tra cho các cơ quan quản lý.                                                            |   3    |    V    |

---

## 11.3 Các biện pháp bảo vệ quyền riêng tư vi phân

|   #    | Mô tả                                                                                                         | Cấp độ | Vai trò |
| :----: | ------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 11.3.1 | Xác minh rằng các bảng điều khiển theo dõi thiệt hại riêng tư cảnh báo khi tổng ε vượt quá ngưỡng chính sách. |   2    |   D/V   |
| 11.3.2 | Xác minh rằng các cuộc kiểm toán quyền riêng tư hộp đen ước tính ε̂ trong phạm vi 10% giá trị đã khai báo.    |   2    |    V    |
| 11.3.3 | Xác minh rằng các bằng chứng hình thức bao phủ tất cả các tinh chỉnh sau khi đào tạo và các nhúng.            |   3    |    V    |

---

## 11.4 Hạn chế mục đích & Bảo vệ chống tràn phạm vi

|   #    | Mô tả                                                                                                                                  | Cấp độ | Vai trò |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 11.4.1 | Xác minh rằng mỗi bộ dữ liệu và điểm kiểm tra mô hình đều mang thẻ mục đích có thể đọc bằng máy và phù hợp với sự đồng thuận ban đầu.  |   1    |    D    |
| 11.4.2 | Xác minh rằng các bộ theo dõi thời gian chạy phát hiện các truy vấn không nhất quán với mục đích đã khai báo và kích hoạt từ chối mềm. |   1    |   D/V   |
| 11.4.3 | Xác minh rằng các cổng policy-as-code ngăn chặn việc triển khai lại các mô hình sang các miền mới mà không qua đánh giá DPIA.          |   3    |    D    |
| 11.4.4 | Xác minh rằng các bằng chứng truy xuất chính thức cho thấy mọi vòng đời dữ liệu cá nhân vẫn nằm trong phạm vi đã được đồng ý.          |   3    |    V    |

---

## 11.5 Quản lý sự đồng ý & Theo dõi cơ sở pháp lý

|   #    | Mô tả                                                                                                                                | Cấp độ | Vai trò |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 11.5.1 | Xác minh rằng Nền tảng Quản lý Đồng thuận (CMP) ghi lại trạng thái đồng ý, mục đích và thời gian lưu giữ cho từng đối tượng dữ liệu. |   1    |   D/V   |
| 11.5.2 | Xác minh rằng các API tiết lộ mã thông báo đồng ý; các mô hình phải xác thực phạm vi mã thông báo trước khi suy luận.                |   2    |    D    |
| 11.5.3 | Xác minh rằng việc từ chối hoặc rút lại sự đồng ý sẽ ngăn chặn các quy trình xử lý trong vòng 24 giờ.                                |   2    |   D/V   |

---

## 11.6 Học Liên Liền với Kiểm Soát Quyền Riêng Tư

|   #    | Mô tả                                                                                                                        | Cấp độ | Vai trò |
| :----: | ---------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 11.6.1 | Xác minh rằng các bản cập nhật của khách hàng sử dụng phép thêm nhiễu bảo mật vi phân cục bộ trước khi tổng hợp.             |   1    |    D    |
| 11.6.2 | Xác minh rằng các chỉ số huấn luyện có tính riêng tư vi phân và không bao giờ tiết lộ tổn thất của từng khách hàng riêng lẻ. |   2    |   D/V   |
| 11.6.3 | Xác minh rằng việc tổng hợp chống đầu độc (ví dụ: Krum/Trimmed-Mean) đã được bật.                                            |   2    |    V    |
| 11.6.4 | Xác minh rằng các bằng chứng chính thức chứng minh tổng ngân sách ε với mất mát tiện ích dưới 5.                             |   3    |    V    |

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

