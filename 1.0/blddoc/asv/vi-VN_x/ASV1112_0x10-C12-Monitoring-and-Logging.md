# C12 Giám sát, Ghi nhật ký và Phát hiện bất thường

## Mục tiêu kiểm soát

Phần này cung cấp các yêu cầu để cung cấp khả năng quan sát thời gian thực và tầm nhìn pháp y đối với những gì mô hình và các thành phần AI khác thấy, làm và trả về, nhằm mục đích phát hiện, phân loại và sắp xếp ưu tiên các mối đe dọa và học hỏi từ chúng.

## C12.1 Ghi Nhật ký Yêu cầu và Phản hồi

|   #    | Mô tả                                                                                                                                                                                                                                | Cấp độ | Vai trò |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 12.1.1 | Xác minh rằng tất cả các lời nhắc của người dùng và phản hồi của mô hình được ghi lại với siêu dữ liệu phù hợp (ví dụ: dấu thời gian, ID người dùng, ID phiên, phiên bản mô hình).                                                   |   1    |   D/V   |
| 12.1.2 | Xác minh rằng các nhật ký được lưu trữ trong các kho lưu trữ an toàn và có kiểm soát truy cập, với các chính sách lưu giữ và thủ tục sao lưu phù hợp.                                                                                |   1    |   D/V   |
| 12.1.3 | Xác minh rằng các hệ thống lưu trữ nhật ký triển khai mã hóa khi lưu trữ và mã hóa khi truyền để bảo vệ thông tin nhạy cảm có trong nhật ký.                                                                                         |   1    |   D/V   |
| 12.1.4 | Đảm bảo dữ liệu nhạy cảm trong các lời nhắc và đầu ra được tự động ẩn hoặc che khuất trước khi ghi log, với các quy tắc ẩn dữ liệu có thể cấu hình cho PII (thông tin nhận dạng cá nhân), thông tin xác thực và thông tin độc quyền. |   1    |   D/V   |
| 12.1.5 | Xác nhận rằng các quyết định về chính sách và các hành động lọc an toàn được ghi lại với mức chi tiết đầy đủ để phục vụ cho kiểm toán và gỡ lỗi các hệ thống kiểm duyệt nội dung.                                                    |   2    |   D/V   |
| 12.1.6 | Xác minh rằng tính toàn vẹn của nhật ký được bảo vệ thông qua ví dụ như chữ ký số hoặc lưu trữ chỉ ghi.                                                                                                                              |   2    |   D/V   |

---

## C12.2 Phát hiện và Cảnh báo lạm dụng

|   #    | Mô tả                                                                                                                                                                                                    | Cấp độ | Vai trò |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 12.2.1 | Xác minh rằng hệ thống có khả năng phát hiện và cảnh báo về các mẫu jailbreak đã biết, các nỗ lực chèn prompt và các đầu vào đối kháng bằng cách sử dụng phát hiện dựa trên chữ ký.                      |   1    |   D/V   |
| 12.2.2 | Xác minh rằng hệ thống tích hợp với các nền tảng SIEM hiện có bằng cách sử dụng các định dạng nhật ký và giao thức tiêu chuẩn.                                                                           |   1    |   D/V   |
| 12.2.3 | Xác minh rằng các sự kiện bảo mật được làm phong phú bao gồm ngữ cảnh đặc thù của AI như định danh mô hình, điểm tự tin và quyết định của bộ lọc an toàn.                                                |   2    |   D/V   |
| 12.2.4 | Đảm bảo rằng hệ thống phát hiện bất thường hành vi nhận diện các mẫu trò chuyện bất thường, các nỗ lực thử lại quá mức hoặc các hành vi thăm dò có hệ thống.                                             |   2    |   D/V   |
| 12.2.5 | Xác nhận rằng các cơ chế cảnh báo theo thời gian thực sẽ thông báo cho đội ngũ bảo mật khi phát hiện vi phạm chính sách tiềm ẩn hoặc các nỗ lực tấn công.                                                |   2    |   D/V   |
| 12.2.6 | Xác minh rằng các quy tắc tùy chỉnh được bao gồm để phát hiện các mẫu đe dọa liên quan đến AI, bao gồm các nỗ lực jailbreak có phối hợp, chiến dịch tiêm prompt và các cuộc tấn công trích xuất mô hình. |   2    |   D/V   |
| 12.2.7 | Xác minh rằng các quy trình ứng phó sự cố tự động có thể cô lập các mô hình bị xâm phạm, chặn người dùng độc hại và nâng cao mức ưu tiên cho các sự kiện bảo mật nghiêm trọng.                           |   3    |   D/V   |

---

## C12.3 Phát hiện sự dịch chuyển của mô hình

|   #    | Mô tả                                                                                                                                                                                       | Cấp độ | Vai trò |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 12.3.1 | Xác minh rằng hệ thống theo dõi các chỉ số hiệu suất cơ bản như độ chính xác, điểm tự tin, độ trễ và tỷ lệ lỗi giữa các phiên bản mô hình và theo các khoảng thời gian.                     |   1    |   D/V   |
| 12.3.2 | Xác minh rằng cảnh báo tự động được kích hoạt khi các chỉ số hiệu suất vượt quá ngưỡng suy giảm được xác định trước hoặc lệch đáng kể so với các mức chuẩn tham chiếu.                      |   2    |   D/V   |
| 12.3.3 | Xác minh rằng các công cụ giám sát phát hiện ảo giác nhận diện và đánh dấu các trường hợp khi đầu ra của mô hình chứa thông tin không đúng sự thật, không nhất quán hoặc thông tin giả mạo. |   2    |   D/V   |

---

## C12.4 Hiệu suất và Hành vi Telemetry

|   #    | Mô tả                                                                                                                                                  | Cấp độ | Vai trò |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 12.4.1 | Xác minh rằng các chỉ số vận hành bao gồm độ trễ yêu cầu, lượng token tiêu thụ, mức sử dụng bộ nhớ và thông lượng được thu thập và giám sát liên tục.  |   1    |   D/V   |
| 12.4.2 | Xác minh rằng tỷ lệ thành công và thất bại được theo dõi kèm theo phân loại các loại lỗi và nguyên nhân gốc của chúng.                                 |   1    |   D/V   |
| 12.4.3 | Xác nhận rằng việc giám sát sử dụng tài nguyên bao gồm việc sử dụng GPU/CPU, tiêu thụ bộ nhớ và yêu cầu về lưu trữ, kèm theo cảnh báo khi vượt ngưỡng. |   2    |   D/V   |

---

## C12.5 Lập kế hoạch và thực thi ứng phó sự cố AI

|   #    | Mô tả                                                                                                                                                                         | Cấp độ | Vai trò |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 12.5.1 | Xác nhận rằng các kế hoạch ứng phó sự cố liên quan đến AI được thiết kế để cụ thể xử lý các sự kiện bảo mật, bao gồm xâm phạm mô hình, đầu độc dữ liệu và tấn công đối kháng. |   1    |   D/V   |
| 12.5.2 | Xác nhận rằng các đội phản ứng sự cố có quyền truy cập các công cụ pháp y chuyên dụng cho AI và kiến thức chuyên môn để điều tra hành vi của mô hình và các vector tấn công.  |   2    |   D/V   |
| 12.5.3 | Xác minh rằng phân tích sau sự cố bao gồm các cân nhắc về tái huấn luyện mô hình, cập nhật bộ lọc an toàn và tích hợp các bài học rút ra vào các biện pháp kiểm soát an ninh. |   3    |   D/V   |

---

## C12.5 Phát hiện suy giảm hiệu suất AI

Giám sát và phát hiện sự suy giảm hiệu suất và chất lượng của mô hình AI theo thời gian.

|   #    | Mô tả                                                                                                                                                                | Cấp độ | Vai trò |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 12.5.1 | Xác nhận rằng độ chính xác của mô hình, precision, recall, và điểm F1 được theo dõi liên tục và so sánh với ngưỡng tham chiếu.                                       |   1    |   D/V   |
| 12.5.2 | Xác nhận rằng phát hiện sự lệch dữ liệu đang giám sát sự thay đổi trong phân phối đầu vào có thể ảnh hưởng đến hiệu suất của mô hình.                                |   1    |   D/V   |
| 12.5.3 | Xác nhận rằng việc phát hiện độ lệch khái niệm có thể nhận diện các thay đổi trong mối quan hệ giữa các đầu vào và các đầu ra mong đợi.                              |   2    |   D/V   |
| 12.5.4 | Xác nhận rằng sự suy giảm hiệu suất kích hoạt cảnh báo tự động và khởi động các quy trình tái huấn luyện mô hình hoặc thay thế mô hình.                              |   2    |   D/V   |
| 12.5.5 | Xác nhận rằng phân tích nguyên nhân gốc của sự suy giảm liên quan đến sự sụt giảm hiệu suất với các thay đổi dữ liệu, sự cố cơ sở hạ tầng hoặc các yếu tố bên ngoài. |   3    |    V    |

---

## C12.6 Trực quan hóa DAG và Bảo mật quy trình làm việc

Bảo vệ hệ thống trực quan hóa quy trình làm việc khỏi rò rỉ thông tin và các cuộc tấn công thao túng.

|   #    | Mô tả                                                                                                                                                                                      | Cấp độ | Vai trò |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 12.6.1 | Xác nhận rằng dữ liệu trực quan hóa DAG đã được làm sạch để loại bỏ thông tin nhạy cảm trước khi lưu trữ hoặc truyền.                                                                      |   1    |   D/V   |
| 12.6.2 | Xác nhận rằng các kiểm soát quyền truy cập cho trực quan hóa luồng công việc đảm bảo chỉ người dùng được ủy quyền mới có thể xem đường đi quyết định của tác nhân và các dấu vết suy luận. |   1    |   D/V   |
| 12.6.3 | Xác minh rằng tính toàn vẹn của dữ liệu DAG được bảo vệ thông qua chữ ký số và các cơ chế lưu trữ có khả năng phát hiện sự can thiệp.                                                      |   2    |   D/V   |
| 12.6.4 | Xác nhận rằng các hệ thống trực quan hóa luồng công việc thực hiện xác thực đầu vào để ngăn chặn các cuộc tấn công tiêm thông qua dữ liệu nút hoặc cạnh được thiết kế tinh vi.             |   2    |   D/V   |
| 12.6.5 | Xác minh rằng các cập nhật DAG thời gian thực được giới hạn tốc độ và xác thực để ngăn chặn các cuộc tấn công từ chối dịch vụ nhắm vào hệ thống trực quan hóa.                             |   3    |   D/V   |

---

## C12.7 Giám sát hành vi bảo mật chủ động

Phát hiện và ngăn chặn các mối đe dọa bảo mật thông qua phân tích hành vi của tác nhân chủ động.

|   #    | Mô tả                                                                                                                                     | Cấp độ | Vai trò |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 12.7.1 | Xác minh rằng các hành vi của tác nhân chủ động được xác thực về bảo mật trước khi thực thi, với tích hợp đánh giá rủi ro.                |   1    |   D/V   |
| 12.7.2 | Xác minh rằng các kích hoạt sáng kiến tự động bao gồm đánh giá ngữ cảnh bảo mật và đánh giá bối cảnh mối đe dọa.                          |   2    |   D/V   |
| 12.7.3 | Xác nhận rằng các mẫu hành vi mang tính chủ động được phân tích để đánh giá những tác động bảo mật tiềm ẩn và những hậu quả ngoài ý muốn. |   2    |   D/V   |
| 12.7.4 | Xác minh rằng các hành động chủ động có tính bảo mật cao yêu cầu chuỗi phê duyệt rõ ràng kèm theo nhật ký kiểm toán.                      |   3    |   D/V   |
| 12.7.5 | Xác minh rằng phát hiện bất thường hành vi có thể nhận diện các lệch trong các mẫu của tác nhân chủ động và cho thấy sự xâm nhập.         |   3    |   D/V   |

---

## Tài liệu tham khảo

* [NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6](https://www.iso.org/standard/81230.html)
* [EU AI Act — Article 12, 13, 16 and 19 on Logging and Record-keeping](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A32024R1689)

