# C12 Giám sát, Ghi nhật ký & Phát hiện Dị thường

## Mục tiêu Kiểm soát

Phần này cung cấp các yêu cầu để cung cấp khả năng quan sát thời gian thực và phân tích pháp y về những gì mô hình và các thành phần AI khác nhìn thấy, thực hiện và trả về, nhằm phát hiện, phân loại và rút ra bài học từ các mối đe dọa.

## C12.1 Ghi nhật ký Yêu cầu & Phản hồi

|   #    | Mô tả                                                                                                                                                                                                                                       | Cấp độ | Vai trò |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 12.1.1 | Xác minh rằng tất cả các yêu cầu của người dùng và phản hồi của mô hình đều được ghi lại cùng với siêu dữ liệu phù hợp (ví dụ: dấu thời gian, ID người dùng, ID phiên, phiên bản mô hình).                                                  |   1    |   D/V   |
| 12.1.2 | Xác minh rằng các bản ghi được lưu trữ trong các kho lưu trữ an toàn, có kiểm soát truy cập với các chính sách lưu giữ và quy trình sao lưu phù hợp.                                                                                        |   1    |   D/V   |
| 12.1.3 | Xác minh rằng các hệ thống lưu trữ nhật ký đã triển khai mã hóa khi lưu trữ và truyền tải để bảo vệ thông tin nhạy cảm chứa trong các nhật ký.                                                                                              |   1    |   D/V   |
| 12.1.4 | Xác minh rằng dữ liệu nhạy cảm trong các lời nhắc và kết quả được tự động làm mờ hoặc che giấu trước khi ghi lại, với các quy tắc làm mờ có thể cấu hình cho thông tin nhận dạng cá nhân (PII), thông tin đăng nhập và thông tin độc quyền. |   1    |   D/V   |
| 12.1.5 | Xác minh rằng các quyết định chính sách và hành động lọc an toàn được ghi lại với chi tiết đầy đủ để cho phép kiểm tra và gỡ lỗi các hệ thống kiểm duyệt nội dung.                                                                          |   2    |   D/V   |
| 12.1.6 | Xác minh rằng tính toàn vẹn của nhật ký được bảo vệ thông qua ví dụ như chữ ký mật mã hoặc lưu trữ chỉ ghi.                                                                                                                                 |   2    |   D/V   |

---

## C12.2 Phát hiện và Cảnh báo Lạm dụng

|   #    | Mô tả                                                                                                                                                                                                 | Cấp độ | Vai trò |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 12.2.1 | Xác minh rằng hệ thống phát hiện và cảnh báo các mẫu jailbreak đã biết, các cố gắng chèn prompt, và các đầu vào đối kháng sử dụng phương pháp phát hiện dựa trên chữ ký.                              |   1    |   D/V   |
| 12.2.2 | Xác minh rằng hệ thống tích hợp với các nền tảng Quản lý Thông tin và Sự kiện Bảo mật (SIEM) hiện có bằng cách sử dụng các định dạng và giao thức nhật ký tiêu chuẩn.                                 |   1    |   D/V   |
| 12.2.3 | Xác minh rằng các sự kiện bảo mật được làm giàu bao gồm ngữ cảnh đặc thù của AI như các định danh mô hình, điểm tin cậy và các quyết định bộ lọc an toàn.                                             |   2    |   D/V   |
| 12.2.4 | Xác minh rằng phát hiện bất thường hành vi có thể nhận diện được các mẫu hội thoại bất thường, số lần thử lại quá mức hoặc các hành vi thăm dò có hệ thống.                                           |   2    |   D/V   |
| 12.2.5 | Xác minh rằng các cơ chế cảnh báo theo thời gian thực thông báo cho nhóm bảo mật khi phát hiện các vi phạm chính sách tiềm ẩn hoặc các cố gắng tấn công.                                              |   2    |   D/V   |
| 12.2.6 | Xác nhận rằng các quy tắc tùy chỉnh được đưa vào để phát hiện các mẫu mối đe dọa đặc thù AI bao gồm các nỗ lực phá vỡ phối hợp, chiến dịch tiêm lệnh yêu cầu và các cuộc tấn công trích xuất mô hình. |   2    |   D/V   |
| 12.2.7 | Xác minh rằng các quy trình tự động phản ứng sự cố có thể cô lập các mô hình bị xâm phạm, chặn người dùng độc hại và nâng cao các sự kiện an ninh quan trọng.                                         |   3    |   D/V   |

---

## C12.3 Phát hiện Trôi mô hình

|   #    | Mô tả                                                                                                                                                                     | Cấp độ | Vai trò |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 12.3.1 | Xác minh rằng hệ thống theo dõi các chỉ số hiệu suất cơ bản như độ chính xác, điểm tin cậy, độ trễ và tỷ lệ lỗi qua các phiên bản mô hình và khoảng thời gian.            |   1    |   D/V   |
| 12.3.2 | Xác minh rằng hệ thống cảnh báo tự động được kích hoạt khi các chỉ số hiệu suất vượt quá ngưỡng suy giảm đã định trước hoặc lệch đáng kể so với các giá trị nền.          |   2    |   D/V   |
| 12.3.3 | Xác minh rằng các bộ giám sát phát hiện ảo giác có thể nhận diện và đánh dấu các trường hợp khi kết quả mô hình chứa thông tin sai sự thật, không nhất quán hoặc bịa đặt. |   2    |   D/V   |

---

## C12.4 Hiệu suất & Dữ liệu Theo dõi Hành vi

|   #    | Mô tả                                                                                                                                           | Cấp độ | Vai trò |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 12.4.1 | Xác minh rằng các chỉ số vận hành bao gồm độ trễ yêu cầu, mức tiêu thụ token, sử dụng bộ nhớ và thông lượng được liên tục thu thập và giám sát. |   1    |   D/V   |
| 12.4.2 | Xác minh rằng tỷ lệ thành công và thất bại được theo dõi cùng với việc phân loại các loại lỗi và nguyên nhân gốc rễ của chúng.                  |   1    |   D/V   |
| 12.4.3 | Xác minh rằng việc giám sát sử dụng tài nguyên bao gồm sử dụng GPU/CPU, tiêu thụ bộ nhớ và yêu cầu lưu trữ với cảnh báo khi vượt ngưỡng.        |   2    |   D/V   |

---

## C12.5 Lập Kế Hoạch & Thực Thi Phản Ứng Sự Cố AI

|   #    | Mô tả                                                                                                                                                                         | Cấp độ | Vai trò |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 12.5.1 | Xác minh rằng các kế hoạch ứng phó sự cố cụ thể xử lý các sự kiện bảo mật liên quan đến AI bao gồm xâm phạm mô hình, đầu độc dữ liệu và các cuộc tấn công đối kháng.          |   1    |   D/V   |
| 12.5.2 | Xác minh rằng các nhóm ứng phó sự cố có quyền truy cập vào các công cụ pháp y chuyên dụng cho AI và chuyên môn để điều tra hành vi mô hình và các vectơ tấn công.             |   2    |   D/V   |
| 12.5.3 | Xác nhận rằng phân tích sau sự cố bao gồm các xem xét về tái huấn luyện mô hình, cập nhật bộ lọc an toàn và tích hợp bài học kinh nghiệm vào các biện pháp kiểm soát an ninh. |   3    |   D/V   |

---

## C12.5 Phát hiện suy giảm hiệu suất AI

Giám sát và phát hiện sự suy giảm trong hiệu suất và chất lượng của mô hình AI theo thời gian.

|   #    | Mô tả                                                                                                                                                      | Cấp độ | Vai trò |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 12.5.1 | Xác minh rằng độ chính xác của mô hình, độ chính xác, độ bao phủ và điểm số F1 được liên tục theo dõi và so sánh với các ngưỡng cơ sở.                     |   1    |   D/V   |
| 12.5.2 | Xác minh rằng phát hiện trôi dữ liệu giám sát các thay đổi phân phối đầu vào có thể ảnh hưởng đến hiệu suất của mô hình.                                   |   1    |   D/V   |
| 12.5.3 | Xác minh rằng phát hiện trôi khái niệm nhận biết sự thay đổi trong mối quan hệ giữa các đầu vào và đầu ra dự kiến.                                         |   2    |   D/V   |
| 12.5.4 | Xác minh rằng sự suy giảm hiệu suất kích hoạt cảnh báo tự động và khởi động quy trình đào tạo lại hoặc thay thế mô hình.                                   |   2    |   D/V   |
| 12.5.5 | Xác minh rằng phân tích nguyên nhân gốc rễ của suy giảm liên kết sự giảm hiệu suất với các thay đổi dữ liệu, các vấn đề hạ tầng hoặc các yếu tố bên ngoài. |   3    |    V    |

---

## C12.6 Hiển thị DAG & Bảo mật Quy trình làm việc

Bảo vệ hệ thống trực quan hóa luồng công việc khỏi rò rỉ thông tin và các cuộc tấn công thao túng.

|   #    | Mô tả                                                                                                                                                                                    | Cấp độ | Vai trò |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 12.6.1 | Xác minh rằng dữ liệu trực quan hóa DAG được làm sạch để loại bỏ thông tin nhạy cảm trước khi lưu trữ hoặc truyền tải.                                                                   |   1    |   D/V   |
| 12.6.2 | Xác minh rằng các kiểm soát truy cập trực quan hóa quy trình làm việc đảm bảo chỉ người dùng được ủy quyền mới có thể xem các đường dẫn quyết định của tác nhân và các dấu vết lập luận. |   1    |   D/V   |
| 12.6.3 | Xác minh rằng tính toàn vẹn dữ liệu DAG được bảo vệ thông qua chữ ký mật mã và các cơ chế lưu trữ có khả năng phát hiện giả mạo.                                                         |   2    |   D/V   |
| 12.6.4 | Xác minh rằng hệ thống trực quan hóa quy trình làm việc thực hiện kiểm tra đầu vào để ngăn chặn các cuộc tấn công chèn mã thông qua dữ liệu nút hoặc cạnh được tạo.                      |   2    |   D/V   |
| 12.6.5 | Xác minh rằng các cập nhật DAG theo thời gian thực được giới hạn tần suất và xác thực để ngăn ngừa các cuộc tấn công từ chối dịch vụ vào hệ thống trực quan hóa.                         |   3    |   D/V   |

---

## C12.7 Giám sát Hành vi Bảo mật Chủ động

Phát hiện và ngăn chặn các mối đe dọa bảo mật thông qua phân tích hành vi tác nhân chủ động.

|   #    | Mô tả                                                                                                                                | Cấp độ | Vai trò |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 12.7.1 | Xác minh rằng các hành vi của tác nhân chủ động được kiểm chứng bảo mật trước khi thực thi với tích hợp đánh giá rủi ro.             |   1    |   D/V   |
| 12.7.2 | Xác minh rằng các tác nhân khởi xướng tự động bao gồm đánh giá bối cảnh bảo mật và đánh giá cảnh quan mối đe dọa.                    |   2    |   D/V   |
| 12.7.3 | Xác minh rằng các mô hình hành vi chủ động được phân tích để xác định các tác động tiềm ẩn về bảo mật và các hệ quả không mong muốn. |   2    |   D/V   |
| 12.7.4 | Xác nhận rằng các hành động chủ động quan trọng về bảo mật yêu cầu chuỗi phê duyệt rõ ràng kèm theo dấu vết kiểm tra.                |   3    |   D/V   |
| 12.7.5 | Xác minh rằng phát hiện bất thường hành vi nhận diện được các sai lệch trong các mẫu tác nhân chủ động có thể chỉ ra sự xâm phạm.    |   3    |   D/V   |

---

## Tài liệu tham khảo

* [NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6](https://www.iso.org/standard/81230.html)
* [EU AI Act — Article 12, 13, 16 and 19 on Logging and Record-keeping](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A32024R1689)

