# Quản lý Vòng đời Mô hình C3 & Kiểm soát Thay đổi

## Mục tiêu Kiểm soát

Hệ thống AI phải thực hiện các quy trình kiểm soát thay đổi nhằm ngăn chặn các sửa đổi mô hình trái phép hoặc không an toàn được đưa vào sản xuất. Kiểm soát này đảm bảo tính toàn vẹn của mô hình trong suốt vòng đời - từ phát triển đến triển khai và ngừng sử dụng - giúp phản ứng nhanh với sự cố và duy trì trách nhiệm cho tất cả các thay đổi.

Mục tiêu bảo mật cốt lõi: Chỉ những mô hình được ủy quyền và xác thực mới được đưa vào sản xuất thông qua các quy trình kiểm soát nhằm duy trì tính toàn vẹn, khả năng truy xuất và khả năng phục hồi.

---

## C3.1 Ủy quyền Mô hình & Toàn vẹn

Chỉ những mô hình được ủy quyền với tính toàn vẹn đã được xác minh mới được đưa vào môi trường sản xuất.

|   #   | Mô tả                                                                                                                                                                                  | Cấp độ | Vai trò |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 3.1.1 | Xác minh rằng tất cả các tác phẩm mô hình (trọng số, cấu hình, bộ mã hóa) đều được ký mật mã bởi các thực thể được ủy quyền trước khi triển khai.                                      |   1    |   D/V   |
| 3.1.2 | Xác minh rằng việc theo dõi phụ thuộc duy trì một kho hàng thời gian thực cho phép nhận diện tất cả các hệ thống sử dụng.                                                              |   2    |    V    |
| 3.1.3 | Xác minh rằng hồ sơ nguồn gốc mô hình bao gồm danh tính của thực thể ủy quyền, checksum dữ liệu đào tạo, kết quả kiểm tra xác nhận với trạng thái đạt/không đạt, và dấu thời gian tạo. |   3    |   D/V   |

---

## C3.2 Xác thực & Kiểm thử Mô hình

Các mô hình phải vượt qua các kiểm tra xác thực bảo mật và an toàn đã được định nghĩa trước khi triển khai.

|   #   | Mô tả                                                                                                                                                                                                                                 | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 3.2.1 | Xác nhận rằng các mô hình trải qua kiểm thử bảo mật tự động bao gồm xác thực đầu vào, làm sạch đầu ra, và đánh giá an toàn với các ngưỡng đạt/không đạt đã được tổ chức đồng thuận trước khi triển khai.                              |   1    |   D/V   |
| 3.2.2 | Xác minh rằng tất cả các thay đổi của mô hình (triển khai, cấu hình, ngừng sử dụng) đều tạo ra các bản ghi kiểm toán không thể thay đổi bao gồm dấu thời gian, danh tính tác nhân đã xác thực, loại thay đổi và trạng thái trước/sau. |   1    |    V    |
| 3.2.3 | Xác minh rằng các lỗi xác thực sẽ tự động chặn việc triển khai mô hình sau khi có sự phê duyệt ghi đè rõ ràng từ nhân sự được ủy quyền trước với các lý do kinh doanh được tài liệu hóa.                                              |   2    |   D/V   |

---

## C3.3 Triển khai có kiểm soát & Quay lại

Các triển khai mô hình phải được kiểm soát, giám sát và có khả năng đảo ngược.

|   #   | Mô tả                                                                                                                                                                                                                                                    | Cấp độ | Vai trò |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 3.3.1 | Xác minh rằng các quy trình triển khai xác thực chữ ký mật mã và tính toán các hàm kiểm tra tính toàn vẹn trước khi kích hoạt mô hình, đồng thời thất bại triển khai nếu có bất kỳ sự không khớp nào.                                                    |   1    |   D/V   |
| 3.3.2 | Xác minh rằng các triển khai sản xuất thực hiện các cơ chế triển khai dần dần (triển khai canary, triển khai xanh-xanh) với các kích hoạt hoàn tác tự động dựa trên các tỷ lệ lỗi đã thỏa thuận trước, ngưỡng độ trễ hoặc các tiêu chí cảnh báo bảo mật. |   1    |    D    |
| 3.3.3 | Xác minh rằng khả năng khôi phục lại trạng thái hoàn chỉnh của mô hình (trọng số, cấu hình, phụ thuộc) được thực hiện một cách nguyên tử.                                                                                                                |   2    |   D/V   |
| 3.3.4 | Xác minh rằng khả năng tắt mô hình khẩn cấp có thể vô hiệu hóa các điểm cuối của mô hình trong phạm vi phản hồi đã được xác định trước.                                                                                                                  |   3    |   D/V   |

---

## C3.4 Thực hành phát triển an toàn

Quy trình phát triển và đào tạo mô hình phải tuân theo các biện pháp bảo mật để ngăn ngừa việc bị xâm phạm.

|   #   | Mô tả                                                                                                                                                                                                                                            | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 3.4.1 | Xác minh rằng các môi trường phát triển, kiểm thử và sản xuất mô hình được tách biệt về mặt vật lý hoặc logic. Chúng không dùng chung hạ tầng, có kiểm soát truy cập riêng biệt và lưu trữ dữ liệu độc lập.                                      |   1    |   D/V   |
| 3.4.2 | Xác minh rằng các tác phẩm phát triển mô hình (siêu tham số, kịch bản đào tạo, tệp cấu hình, mẫu lệnh nhắc, v.v.) được lưu trữ trong hệ thống kiểm soát phiên bản và yêu cầu phê duyệt từ đồng nghiệp trước khi sử dụng trong quá trình đào tạo. |   1    |    D    |
| 3.4.3 | Xác minh rằng việc đào tạo và điều chỉnh mô hình diễn ra trong các môi trường cách ly với quyền truy cập mạng được kiểm soát.                                                                                                                    |   2    |   D/V   |
| 3.4.4 | Xác nhận rằng các nguồn dữ liệu đào tạo được xác thực thông qua các kiểm tra tính toàn vẹn và được xác thực qua các nguồn đáng tin cậy với chuỗi quản lý tài liệu trước khi sử dụng trong phát triển mô hình.                                    |   2    |    D    |

---

## Ngừng sử dụng và Triệt phá Mô hình C3.5

Các mô hình phải được ngừng sử dụng một cách an toàn khi chúng không còn cần thiết hoặc khi các vấn đề về bảo mật được xác định.

|   #   | Mô tả                                                                                                                                                            | Cấp độ | Vai trò |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 3.5.1 | Xác minh rằng các tệp mô hình đã nghỉ hưu được xóa an toàn bằng cách sử dụng xóa mật mã an toàn.                                                                 |   1    |   D/V   |
| 3.5.2 | Xác minh rằng các sự kiện nghỉ hưu mô hình được ghi lại với dấu thời gian và nhận dạng người thực hiện, đồng thời chữ ký mô hình bị thu hồi để ngăn tái sử dụng. |   2    |    V    |

---

## Tài liệu tham khảo

* [MITRE ATLAS](https://atlas.mitre.org/)
* [MLOps Principles](https://ml-ops.org/content/mlops-principles)
* [Reinforcement fine-tuning](https://platform.openai.com/docs/guides/reinforcement-fine-tuning)
* [What is AI adversarial robustness? – IBM Research](https://research.ibm.com/blog/securing-ai-workflows-with-adversarial-robustness)

