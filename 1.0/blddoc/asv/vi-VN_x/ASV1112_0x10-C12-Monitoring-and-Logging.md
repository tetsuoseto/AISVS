# C12 Giám sát, Ghi nhật ký & Phát hiện Dị thường

## Mục tiêu Kiểm soát

Phần này cung cấp các yêu cầu để cung cấp khả năng quan sát thời gian thực và phân tích pháp y về những gì mô hình và các thành phần AI khác nhìn thấy, thực hiện và trả về, nhằm phát hiện, phân loại và rút kinh nghiệm từ các mối đe dọa.

## C12.1 Ghi lại Yêu cầu & Phản hồi

|   #    | Mô tả                                                                                                                                                                                                                            | Cấp độ | Vai trò |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 12.1.1 | Xác minh rằng tất cả các lời nhắc của người dùng và phản hồi của mô hình đều được ghi lại cùng với siêu dữ liệu thích hợp (ví dụ: dấu thời gian, ID người dùng, ID phiên, phiên bản mô hình).                                    |   1    |   D/V   |
| 12.1.2 | Xác minh rằng các bản ghi được lưu trữ trong các kho lưu trữ an toàn, có kiểm soát truy cập với các chính sách giữ lại và quy trình sao lưu phù hợp.                                                                             |   1    |   D/V   |
| 12.1.3 | Xác minh rằng các hệ thống lưu trữ nhật ký thực hiện mã hóa khi dữ liệu được nghỉ lưu và khi truyền tải để bảo vệ thông tin nhạy cảm chứa trong các nhật ký.                                                                     |   1    |   D/V   |
| 12.1.4 | Xác nhận rằng dữ liệu nhạy cảm trong các lời nhắc và kết quả đầu ra được tự động ẩn hoặc che giấu trước khi ghi lại, với các quy tắc ẩn có thể cấu hình cho thông tin cá nhân (PII), thông tin đăng nhập và thông tin độc quyền. |   1    |   D/V   |
| 12.1.5 | Xác minh rằng các quyết định chính sách và các hành động lọc an toàn được ghi lại với chi tiết đủ để cho phép kiểm toán và gỡ lỗi các hệ thống kiểm duyệt nội dung.                                                              |   2    |   D/V   |
| 12.1.6 | Xác minh rằng tính toàn vẹn của nhật ký được bảo vệ thông qua ví dụ như chữ ký mật mã hoặc lưu trữ chỉ ghi.                                                                                                                      |   2    |   D/V   |

---

## C12.2 Phát hiện và cảnh báo lạm dụng

|   #    | Mô tả                                                                                                                                                                                               | Cấp độ | Vai trò |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 12.2.1 | Xác minh rằng hệ thống phát hiện và cảnh báo các mẫu jailbreak đã biết, các cố gắng chèn prompt, và các đầu vào đối kháng sử dụng phương pháp phát hiện dựa trên chữ ký.                            |   1    |   D/V   |
| 12.2.2 | Xác minh rằng hệ thống tích hợp với các nền tảng Quản lý Thông tin và Sự kiện Bảo mật (SIEM) hiện có bằng cách sử dụng các định dạng và giao thức nhật ký tiêu chuẩn.                               |   1    |   D/V   |
| 12.2.3 | Xác minh rằng các sự kiện bảo mật được làm phong phú bao gồm ngữ cảnh đặc thù của AI như định danh mô hình, điểm tin cậy và các quyết định của bộ lọc an toàn.                                      |   2    |   D/V   |
| 12.2.4 | Xác minh rằng phát hiện bất thường hành vi nhận diện các mẫu hội thoại bất thường, số lần thử lại quá nhiều hoặc các hành vi thăm dò có hệ thống.                                                   |   2    |   D/V   |
| 12.2.5 | Xác minh rằng các cơ chế cảnh báo thời gian thực thông báo cho các đội an ninh khi phát hiện các vi phạm chính sách tiềm năng hoặc các cố gắng tấn công.                                            |   2    |   D/V   |
| 12.2.6 | Xác minh rằng các quy tắc tùy chỉnh được bao gồm để phát hiện các mẫu mối đe dọa đặc thù AI bao gồm các nỗ lực phá rào phối hợp, chiến dịch tiêm lệnh nhắc và các cuộc tấn công trích xuất mô hình. |   2    |   D/V   |
| 12.2.7 | Xác minh rằng quy trình phản hồi sự cố tự động có thể cô lập các mô hình bị xâm phạm, chặn người dùng độc hại và nâng cao các sự kiện bảo mật quan trọng.                                           |   3    |   D/V   |

---

## C12.3 Phát hiện Trôi mô hình

|   #    | Mô tả                                                                                                                                                                                                    | Cấp độ | Vai trò |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 12.3.1 | Xác minh rằng hệ thống theo dõi các chỉ số hiệu suất cơ bản như độ chính xác, điểm tin cậy, độ trễ và tỷ lệ lỗi qua các phiên bản mô hình và các khoảng thời gian.                                       |   1    |   D/V   |
| 12.3.2 | Xác minh rằng cảnh báo tự động kích hoạt khi các chỉ số hiệu suất vượt quá ngưỡng suy giảm đã định trước hoặc lệch đáng kể so với các giá trị cơ sở.                                                     |   2    |   D/V   |
| 12.3.3 | Xác minh rằng các bộ theo dõi phát hiện ảo giác có thể nhận diện và đánh dấu các trường hợp khi kết quả mô hình chứa thông tin không chính xác về mặt thực tế, không nhất quán hoặc được tạo ra giả mạo. |   2    |   D/V   |

---

## C12.4 Hiệu suất & Thu thập dữ liệu hành vi

|   #    | Mô tả                                                                                                                                       | Cấp độ | Vai trò |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 12.4.1 | Xác minh rằng các chỉ số vận hành bao gồm độ trễ yêu cầu, tiêu thụ token, sử dụng bộ nhớ và thông lượng được thu thập và giám sát liên tục. |   1    |   D/V   |
| 12.4.2 | Xác minh rằng tỷ lệ thành công và thất bại được theo dõi kèm phân loại các loại lỗi và nguyên nhân gốc rễ của chúng.                        |   1    |   D/V   |
| 12.4.3 | Xác minh rằng việc giám sát sử dụng tài nguyên bao gồm sử dụng GPU/CPU, tiêu thụ bộ nhớ và yêu cầu lưu trữ với cảnh báo khi vượt ngưỡng.    |   2    |   D/V   |

---

## C12.5 Lập kế hoạch và Thực thi Phản ứng Sự cố AI

|   #    | Mô tả                                                                                                                                                                                   | Cấp độ | Vai trò |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 12.5.1 | Xác minh rằng các kế hoạch ứng phó sự cố cụ thể đề cập đến các sự kiện bảo mật liên quan đến AI bao gồm việc xâm phạm mô hình, nhiễm độc dữ liệu và các cuộc tấn công đối kháng.        |   1    |   D/V   |
| 12.5.2 | Xác minh rằng các nhóm ứng phó sự cố có quyền truy cập vào các công cụ pháp y chuyên biệt cho AI và chuyên môn để điều tra hành vi mô hình cũng như các vectơ tấn công.                 |   2    |   D/V   |
| 12.5.3 | Xác minh rằng phân tích sau sự cố bao gồm các cân nhắc về việc huấn luyện lại mô hình, cập nhật bộ lọc an toàn và tích hợp các bài học kinh nghiệm vào các biện pháp kiểm soát bảo mật. |   3    |   D/V   |

---

## C12.6 Phát hiện suy giảm hiệu suất AI

Giám sát và phát hiện sự suy giảm trong hiệu suất và chất lượng của mô hình AI theo thời gian.

|   #    | Mô tả                                                                                                                                                  | Cấp độ | Vai trò |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 12.6.1 | Xác minh rằng độ chính xác mô hình, độ chính xác (precision), độ thu hồi (recall), và điểm F1 được theo dõi liên tục và so sánh với các ngưỡng cơ sở.  |   1    |   D/V   |
| 12.6.2 | Xác minh rằng việc phát hiện trôi dữ liệu giám sát các thay đổi trong phân phối dữ liệu đầu vào có thể ảnh hưởng đến hiệu suất của mô hình.            |   1    |   D/V   |
| 12.6.3 | Xác minh rằng việc phát hiện trôi khái niệm nhận diện được các thay đổi trong mối quan hệ giữa đầu vào và đầu ra dự kiến.                              |   2    |   D/V   |
| 12.6.4 | Xác minh rằng sự suy giảm hiệu suất kích hoạt các cảnh báo tự động và bắt đầu các quy trình làm việc tái huấn luyện hoặc thay thế mô hình.             |   2    |   D/V   |
| 12.6.5 | Xác minh rằng phân tích nguyên nhân gốc rễ suy giảm liên kết các mức giảm hiệu suất với các thay đổi dữ liệu, sự cố hạ tầng hoặc các yếu tố bên ngoài. |   3    |    V    |

---

## C12.7 Hình ảnh hóa DAG & Bảo mật Quy trình làm việc

Bảo vệ hệ thống trực quan hóa quy trình làm việc khỏi rò rỉ thông tin và các cuộc tấn công thao túng.

|   #    | Mô tả                                                                                                                                                                                    | Cấp độ | Vai trò |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 12.7.1 | Xác minh rằng dữ liệu trực quan hóa DAG được làm sạch để loại bỏ thông tin nhạy cảm trước khi lưu trữ hoặc truyền tải.                                                                   |   1    |   D/V   |
| 12.7.2 | Xác minh rằng các điều khiển truy cập trực quan hóa quy trình làm việc đảm bảo chỉ người dùng được ủy quyền mới có thể xem các đường dẫn quyết định của tác nhân và các dấu vết lý giải. |   1    |   D/V   |
| 12.7.3 | Xác minh rằng tính toàn vẹn của dữ liệu DAG được bảo vệ thông qua chữ ký mật mã và cơ chế lưu trữ chống giả mạo.                                                                         |   2    |   D/V   |
| 12.7.4 | Xác minh rằng các hệ thống trực quan hóa quy trình làm việc thực hiện xác thực đầu vào để ngăn chặn các cuộc tấn công chèn mã thông qua dữ liệu nút hoặc cạnh được tạo thủ công.         |   2    |   D/V   |
| 12.7.5 | Xác minh rằng các cập nhật DAG theo thời gian thực được giới hạn tần suất và kiểm tra hợp lệ để ngăn chặn các cuộc tấn công từ chối dịch vụ trên hệ thống trực quan hóa.                 |   3    |   D/V   |

---

## C12.8 Giám sát Hành vi An ninh Chủ động

Phát hiện và ngăn chặn các mối đe dọa an ninh thông qua phân tích hành vi đại lý một cách chủ động.

|   #    | Mô tả                                                                                                                               | Cấp độ | Vai trò |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 12.8.1 | Xác minh rằng các hành vi của đại lý chủ động được xác thực về bảo mật trước khi thực hiện với tích hợp đánh giá rủi ro.            |   1    |   D/V   |
| 12.8.2 | Xác minh rằng các bước khởi xướng tự động bao gồm đánh giá bối cảnh bảo mật và đánh giá cảnh quan mối đe dọa.                       |   2    |   D/V   |
| 12.8.3 | Xác minh rằng các mẫu hành vi chủ động được phân tích để đánh giá các tác động tiềm năng về bảo mật và các hậu quả không mong muốn. |   2    |   D/V   |
| 12.8.4 | Xác minh rằng các hành động chủ động có tính bảo mật quan trọng yêu cầu chuỗi phê duyệt rõ ràng kèm theo dấu vết kiểm toán.         |   3    |   D/V   |
| 12.8.5 | Xác minh rằng việc phát hiện bất thường hành vi nhận dạng những sai lệch trong các mẫu tác nhân chủ động có thể chỉ ra sự xâm phạm. |   3    |   D/V   |

---

## Tài liệu tham khảo

* [NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6](https://www.iso.org/standard/81230.html)

