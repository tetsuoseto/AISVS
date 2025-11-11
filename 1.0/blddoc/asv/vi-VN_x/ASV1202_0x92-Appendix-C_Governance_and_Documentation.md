# Phụ lục C: Quản trị và Tài liệu An ninh AI (Tổ chức lại)

## Mục tiêu

Phụ lục này cung cấp các yêu cầu cơ bản để thiết lập cấu trúc tổ chức, chính sách, tài liệu và quy trình nhằm quản lý an ninh AI trong suốt vòng đời của hệ thống.

---

## AC.1 Khung Quản lý Rủi ro AI được Áp dụng

|   #    | Mô tả                                                                                                                              | Cấp độ | Vai trò |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| AC.1.1 | Xác nhận rằng một phương pháp đánh giá rủi ro đặc thù cho AI đã được tài liệu hóa và triển khai.                                   |   1    |   D/V   |
| AC.1.2 | Xác minh rằng các đánh giá rủi ro được tiến hành tại các điểm then chốt trong vòng đời AI và trước khi có các thay đổi quan trọng. |   2    |    D    |
| AC.1.3 | Xác minh rằng khung quản lý rủi ro phù hợp với các tiêu chuẩn đã được thiết lập (ví dụ: NIST AI RMF).                              |   3    |   D/V   |

---

## AC.2 Chính sách & Quy trình An ninh AI

|   #    | Mô tả                                                                                                                           | Cấp độ | Vai trò |
| :----: | ------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| AC.2.1 | Xác minh rằng các chính sách bảo mật AI đã được tài liệu hóa tồn tại.                                                           |   1    |   D/V   |
| AC.2.2 | Xác minh rằng các chính sách được xem xét và cập nhật ít nhất hàng năm và sau những thay đổi đáng kể trong bối cảnh mối đe dọa. |   2    |    D    |
| AC.2.3 | Xác minh rằng các chính sách bao quát tất cả các danh mục AISVS và các yêu cầu quy định áp dụng.                                |   3    |   D/V   |

---

## AC.3 Vai Trò & Trách Nhiệm cho An Ninh AI

|   #    | Mô tả                                                                                                   | Cấp độ | Vai trò |
| :----: | ------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| AC.3.1 | Xác nhận rằng các vai trò và trách nhiệm về bảo mật AI đã được ghi lại.                                 |   1    |   D/V   |
| AC.3.2 | Xác minh rằng các cá nhân chịu trách nhiệm có chuyên môn về an ninh phù hợp.                            |   2    |    D    |
| AC.3.3 | Xác minh rằng một ủy ban đạo đức AI hoặc ban quản trị được thành lập cho các hệ thống AI có rủi ro cao. |   3    |   D/V   |

---

## AC.4 Thực thi Hướng dẫn Đạo đức AI

|   #    | Mô tả                                                                                            | Cấp độ | Vai trò |
| :----: | ------------------------------------------------------------------------------------------------ | :----: | :-----: |
| AC.4.1 | Xác minh rằng các hướng dẫn đạo đức cho phát triển và triển khai AI đã tồn tại.                  |   1    |   D/V   |
| AC.4.2 | Xác minh rằng các cơ chế đã được thiết lập để phát hiện và báo cáo các vi phạm đạo đức.          |   2    |    D    |
| AC.4.3 | Xác minh rằng các đánh giá đạo đức định kỳ đối với các hệ thống AI đã triển khai được thực hiện. |   3    |   D/V   |

---

## Giám sát Tuân thủ Quy định AI AC.5

|   #    | Mô tả                                                                                        | Cấp độ | Vai trò |
| :----: | -------------------------------------------------------------------------------------------- | :----: | :-----: |
| AC.5.1 | Xác minh rằng có các quy trình để xác định các quy định AI áp dụng.                          |   1    |   D/V   |
| AC.5.2 | Xác minh rằng việc tuân thủ tất cả các yêu cầu quy định đã được đánh giá.                    |   2    |    D    |
| AC.5.3 | Xác minh rằng các thay đổi quy định kích hoạt các đánh giá và cập nhật hệ thống AI kịp thời. |   3    |   D/V   |

---

## AC.6 Quản trị Dữ liệu Đào tạo, Tài liệu & Quy trình

### AC.6.1 Nguồn dữ liệu & Thẩm định kỹ lưỡng

|    #     | Mô tả                                                                                                                                                                                                                                                                                                                                       | Cấp độ | Vai trò |
| :------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| AC.6.1.1 | Xác minh rằng chỉ các tập dữ liệu đã được kiểm duyệt về chất lượng, tính đại diện, nguồn gốc đạo đức và tuân thủ giấy phép được phép sử dụng, nhằm giảm thiểu rủi ro về đầu độc dữ liệu, thiên vị ẩn và vi phạm sở hữu trí tuệ.                                                                                                             |   1    |   D/V   |
| AC.6.1.2 | Xác minh rằng các nhà cung cấp dữ liệu bên thứ ba, bao gồm các nhà cung cấp mô hình đã được huấn luyện trước và bộ dữ liệu bên ngoài, đều trải qua quá trình thẩm định về bảo mật, quyền riêng tư, nguồn gốc đạo đức và chất lượng dữ liệu trước khi dữ liệu hoặc mô hình của họ được tích hợp.                                             |   2    |   D/V   |
| AC.6.1.3 | Xác minh rằng các chuyển khoản ngoài sử dụng TLS/xác thực và kiểm tra toàn vẹn.                                                                                                                                                                                                                                                             |   1    |    D    |
| AC.6.1.4 | Xác minh rằng các nguồn dữ liệu có rủi ro cao (ví dụ: bộ dữ liệu mã nguồn mở có nguồn gốc không rõ, nhà cung cấp chưa được kiểm duyệt) được kiểm tra kỹ lưỡng hơn, chẳng hạn như phân tích trong môi trường cách ly, kiểm tra chất lượng/thiên vị kỹ lưỡng và phát hiện đầu độc có mục tiêu, trước khi sử dụng trong các ứng dụng nhạy cảm. |   2    |   D/V   |
| AC.6.1.5 | Xác minh rằng các mô hình đã được đào tạo sẵn lấy từ bên thứ ba được đánh giá về các thiên vị nhúng, khả năng có cửa hậu, tính toàn vẹn của kiến trúc và nguồn gốc của dữ liệu đào tạo gốc trước khi tinh chỉnh hoặc triển khai.                                                                                                            |   3    |   D/V   |

### AC.6.2 Quản lý Độ thiên vị & Công bằng

|    #     | Mô tả                                                                                                                                                                                                                                                                                                                                                                        | Cấp độ | Vai trò |
| :------: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| AC.6.2.1 | Xác minh rằng các tập dữ liệu đã được phân tích về sự mất cân đối đại diện và các thiên kiến tiềm ẩn trên các thuộc tính được bảo vệ theo pháp luật (ví dụ, chủng tộc, giới tính, tuổi tác) và các đặc điểm nhạy cảm về mặt đạo đức khác liên quan đến lĩnh vực ứng dụng của mô hình (ví dụ, tình trạng kinh tế-xã hội, vị trí địa lý).                                      |   1    |   D/V   |
| AC.6.2.2 | Xác minh rằng các thiên vị được xác định đã được giảm thiểu thông qua các chiến lược được ghi chép như cân bằng lại, tăng cường dữ liệu có mục tiêu, điều chỉnh thuật toán (ví dụ: các kỹ thuật tiền xử lý, xử lý trong quá trình, xử lý sau) hoặc tái phân bổ trọng số, và đánh giá tác động của việc giảm thiểu đối với cả độ công bằng và hiệu suất tổng thể của mô hình. |   2    |   D/V   |
| AC.6.2.3 | Xác minh rằng các chỉ số công bằng sau đào tạo được đánh giá và ghi chép lại.                                                                                                                                                                                                                                                                                                |   2    |   D/V   |
| AC.6.2.4 | Xác minh rằng chính sách quản lý thiên vị trong vòng đời gán quyền sở hữu và tần suất xem xét.                                                                                                                                                                                                                                                                               |   3    |   D/V   |

### AC.6.3 Quản trị Gán nhãn & Ghi chú

|     #     | Mô tả                                                                                                                                                                                                                                                                          | Cấp độ | Vai trò |
| :-------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| AC.6.3.1  | Xác minh rằng chất lượng gán nhãn/chú thích được đảm bảo thông qua việc kiểm tra chéo hoặc sự đồng thuận của người đánh giá.                                                                                                                                                   |   2    |   D/V   |
| AC.6.3.2  | Xác minh rằng các thẻ dữ liệu được duy trì cho các tập dữ liệu đào tạo quan trọng, chi tiết các đặc điểm, động cơ, thành phần, quy trình thu thập, tiền xử lý, giấy phép và các mục đích sử dụng được khuyến nghị/không khuyến nghị.                                           |   2    |   D/V   |
| AC.6.3.3  | Xác minh rằng các thẻ dữ liệu ghi chép các rủi ro thiên vị, lệch lạc dân số học và các cân nhắc đạo đức liên quan đến bộ dữ liệu.                                                                                                                                              |   2    |   D/V   |
| AC.6.3.4  | Xác minh rằng các thẻ dữ liệu được phân phiên bản cùng với các tập dữ liệu và được cập nhật mỗi khi tập dữ liệu bị sửa đổi.                                                                                                                                                    |   2    |   D/V   |
| AC.6.3.5  | Xác minh rằng các thẻ dữ liệu đã được xem xét và phê duyệt bởi cả các bên liên quan kỹ thuật và phi kỹ thuật (ví dụ: bộ phận tuân thủ, đạo đức, chuyên gia lĩnh vực).                                                                                                          |   2    |   D/V   |
| AC.6.3.6  | Xác minh rằng chất lượng gán nhãn/chú thích được đảm bảo thông qua các hướng dẫn rõ ràng, việc kiểm tra chéo giữa các người đánh giá, các cơ chế đồng thuận (ví dụ, theo dõi sự đồng thuận giữa các người chú thích), và các quy trình xác định để giải quyết những khác biệt. |   2    |   D/V   |
| AC.6.3.7  | Xác minh rằng các nhãn quan trọng đối với an toàn, bảo mật hoặc công bằng (ví dụ: xác định nội dung độc hại, phát hiện y tế quan trọng) phải được xem xét lại bắt buộc bởi hai bên độc lập hoặc có phương pháp xác minh mạnh mẽ tương đương.                                   |   3    |   D/V   |
| AC.6.3.8  | Xác minh rằng các hướng dẫn và chỉ dẫn dán nhãn đầy đủ, được kiểm soát phiên bản và được đồng nghiệp đánh giá.                                                                                                                                                                 |   2    |   D/V   |
| AC.6.3.9  | Xác minh rằng các sơ đồ dữ liệu cho nhãn được định nghĩa rõ ràng và được kiểm soát phiên bản.                                                                                                                                                                                  |   2    |   D/V   |
| AC.6.3.10 | Xác minh rằng các quy trình làm việc gán nhãn thuê ngoài hoặc dùng đám đông bao gồm các biện pháp kỹ thuật/thuật procedural để đảm bảo tính bảo mật dữ liệu, tính toàn vẹn, chất lượng nhãn và ngăn ngừa rò rỉ dữ liệu.                                                        |   2    |   D/V   |
| AC.6.3.11 | Xác minh rằng tất cả nhân sự tham gia chú thích dữ liệu đều được kiểm tra lý lịch và đào tạo về an ninh dữ liệu và quyền riêng tư.                                                                                                                                             |   2    |   D/V   |
| AC.6.3.12 | Xác nhận rằng tất cả nhân viên chú thích đã ký các thỏa thuận bảo mật và không tiết lộ thông tin.                                                                                                                                                                              |   2    |   D/V   |
| AC.6.3.13 | Xác minh rằng các nền tảng chú thích thực thi kiểm soát truy cập và theo dõi các mối đe dọa nội bộ.                                                                                                                                                                            |   2    |   D/V   |

### AC.6.4 Cổng chất lượng bộ dữ liệu & Cách ly

|    #     | Mô tả                                                                                                                                                                                                                                                                                          | Cấp độ | Vai trò |
| :------: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| AC.6.4.1 | Xác minh rằng các bộ dữ liệu thất bại được cách ly với dấu vết kiểm toán.                                                                                                                                                                                                                      |   2    |   D/V   |
| AC.6.4.2 | Xác nhận rằng các cổng chất lượng sẽ chặn các tập dữ liệu kém chất lượng trừ khi có sự chấp thuận ngoại lệ.                                                                                                                                                                                    |   2    |   D/V   |
| AC.6.4.3 | Xác minh rằng việc kiểm tra ngẫu nhiên thủ công bởi các chuyên gia trong lĩnh vực bao phủ một mẫu thống kê có ý nghĩa (ví dụ, ≥1% hoặc 1.000 mẫu, tùy theo giá trị lớn hơn, hoặc theo kết quả đánh giá rủi ro) để phát hiện các vấn đề chất lượng tinh vi mà tự động hóa không phát hiện được. |   2    |    V    |

### AC.6.5 Phát hiện Mối đe dọa/Tấn công Độc hại & Trôi dữ liệu

|    #     | Mô tả                                                                                                            | Cấp độ | Vai trò |
| :------: | ---------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| AC.6.5.1 | Xác minh rằng các mẫu bị đánh dấu kích hoạt xem xét thủ công trước khi đào tạo.                                  |   2    |   D/V   |
| AC.6.5.2 | Xác minh rằng kết quả được cung cấp cho hồ sơ bảo mật của mô hình và thông báo cho tình báo mối đe dọa liên tục. |   2    |    V    |
| AC.6.5.3 | Xác nhận rằng logic phát hiện được làm mới với thông tin tình báo mối đe dọa mới.                                |   3    |   D/V   |
| AC.6.5.4 | Xác minh rằng các pipeline học trực tuyến giám sát sự dịch chuyển phân phối dữ liệu.                             |   3    |   D/V   |

### AC.6.6 Xóa bỏ, Đồng ý, Quyền, Lưu trữ & Tuân thủ

|     #     | Mô tả                                                                                                                                                                                                                                                                                                                                   | Cấp độ | Vai trò |
| :-------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| AC.6.6.1  | Xác minh rằng quy trình xóa dữ liệu đào tạo đã xóa sạch dữ liệu gốc và dữ liệu dẫn xuất, đồng thời đánh giá ảnh hưởng lên mô hình, và rằng ảnh hưởng đối với các mô hình bị ảnh hưởng được đánh giá và, nếu cần thiết, được giải quyết (ví dụ, thông qua việc đào tạo lại hoặc hiệu chỉnh lại).                                         |   1    |   D/V   |
| AC.6.6.2  | Xác minh rằng các cơ chế đã được thiết lập để theo dõi và tôn trọng phạm vi cũng như trạng thái của sự đồng ý của người dùng (và các rút lui) đối với dữ liệu sử dụng trong việc huấn luyện, và rằng sự đồng ý được xác thực trước khi dữ liệu được tích hợp vào các quy trình huấn luyện mới hoặc các cập nhật quan trọng của mô hình. |   2    |    D    |
| AC.6.6.3  | Xác minh rằng các quy trình làm việc được kiểm tra hàng năm và ghi lại.                                                                                                                                                                                                                                                                 |   2    |    V    |
| AC.6.6.4  | Xác minh rằng các khoảng thời gian lưu giữ rõ ràng đã được xác định cho tất cả các tập dữ liệu đào tạo.                                                                                                                                                                                                                                 |   1    |   D/V   |
| AC.6.6.5  | Xác minh rằng các bộ dữ liệu tự động hết hạn, bị xóa hoặc được xem xét để xóa khi kết thúc vòng đời của chúng.                                                                                                                                                                                                                          |   2    |   D/V   |
| AC.6.6.6  | Xác minh rằng các hành động giữ lại và xóa dữ liệu được ghi lại và có thể kiểm tra.                                                                                                                                                                                                                                                     |   2    |   D/V   |
| AC.6.6.7  | Xác minh rằng các yêu cầu về cư trú dữ liệu và chuyển giao xuyên biên giới được xác định và thực thi cho tất cả các bộ dữ liệu.                                                                                                                                                                                                         |   2    |   D/V   |
| AC.6.6.8  | Xác minh rằng các quy định đặc thù theo ngành (ví dụ: chăm sóc sức khỏe, tài chính) đã được xác định và xử lý trong việc quản lý dữ liệu.                                                                                                                                                                                               |   2    |   D/V   |
| AC.6.6.9  | Xác nhận rằng việc tuân thủ các luật về quyền riêng tư liên quan (ví dụ, GDPR, CCPA) được ghi chép và xem xét thường xuyên.                                                                                                                                                                                                             |   2    |   D/V   |
| AC.6.6.10 | Xác minh rằng có các cơ chế để phản hồi các yêu cầu của chủ thể dữ liệu về quyền truy cập, chỉnh sửa, hạn chế hoặc phản đối.                                                                                                                                                                                                            |   2    |   D/V   |
| AC.6.6.11 | Xác minh rằng các yêu cầu được ghi lại, theo dõi và hoàn thành trong khoảng thời gian được quy định bởi pháp luật.                                                                                                                                                                                                                      |   2    |   D/V   |
| AC.6.6.12 | Xác nhận rằng các quy trình quyền của chủ thể dữ liệu được kiểm tra và xem xét định kỳ để đảm bảo hiệu quả.                                                                                                                                                                                                                             |   2    |   D/V   |

### AC.6.7 Quản lý Phiên bản & Thay đổi

|    #     | Mô tả                                                                                                                                                              | Cấp độ | Vai trò |
| :------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| AC.6.7.1 | Xác minh rằng một phân tích tác động được thực hiện trước khi cập nhật hoặc thay thế phiên bản tập dữ liệu, bao gồm hiệu suất mô hình, tính công bằng và tuân thủ. |   2    |   D/V   |
| AC.6.7.2 | Xác nhận rằng kết quả của phân tích tác động đã được ghi chép và xem xét bởi các bên liên quan phù hợp.                                                            |   2    |   D/V   |
| AC.6.7.3 | Xác nhận rằng kế hoạch khôi phục tồn tại trong trường hợp các phiên bản mới gây ra các rủi ro hoặc suy giảm không chấp nhận được.                                  |   2    |   D/V   |

### Quản trị Dữ liệu Tổng hợp AC.6.8

|    #     | Mô tả                                                                                                                                               | Cấp độ | Vai trò |
| :------: | --------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| AC.6.8.1 | Xác minh rằng quy trình tạo dữ liệu tổng hợp, các tham số và mục đích sử dụng dự kiến của dữ liệu tổng hợp được ghi chép đầy đủ.                    |   2    |   D/V   |
| AC.6.8.2 | Xác minh rằng dữ liệu tổng hợp đã được đánh giá rủi ro về thiên vị, rò rỉ quyền riêng tư và các vấn đề đại diện trước khi sử dụng trong huấn luyện. |   2    |   D/V   |

### AC.6.9 Giám sát truy cập

|    #     | Mô tả                                                                                                                                                        | Cấp độ | Vai trò |
| :------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| AC.6.9.1 | Xác minh rằng các nhật ký truy cập được xem xét thường xuyên để phát hiện các mẫu bất thường, chẳng hạn như xuất khẩu lớn hoặc truy cập từ các địa điểm mới. |   2    |   D/V   |
| AC.6.9.2 | Xác minh rằng các cảnh báo được tạo ra cho các sự kiện truy cập đáng ngờ và được điều tra kịp thời.                                                          |   2    |   D/V   |

### AC.6.10 Quản lý Đào tạo Đối kháng

|     #     | Mô tả                                                                                                                                                                                                           | Cấp độ | Vai trò |
| :-------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| AC.6.10.1 | Xác minh rằng nếu sử dụng huấn luyện đối kháng, việc tạo ra, quản lý và phiên bản hóa các bộ dữ liệu đối kháng được ghi chép và kiểm soát.                                                                      |   2    |   D/V   |
| AC.6.10.2 | Xác minh rằng tác động của việc huấn luyện độ bền chống đối kháng lên hiệu suất mô hình (đối với cả đầu vào sạch và đầu vào chống đối kháng) cũng như các chỉ số công bằng được đánh giá, ghi chép và theo dõi. |   3    |   D/V   |
| AC.6.10.3 | Xác minh rằng các chiến lược đào tạo đối kháng và độ bền vững được xem xét và cập nhật định kỳ để đối phó với các kỹ thuật tấn công đối kháng ngày càng phát triển.                                             |   3    |   D/V   |

---

## AC.7 Quản lý Vòng đời Mô hình & Tài liệu

|   #    | Mô tả                                                                                                                                                                                               | Cấp độ | Vai trò |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| AC.7.1 | Xác minh rằng tất cả các artifact mô hình sử dụng phiên bản ngữ nghĩa (MAJOR.MINOR.PATCH) với các tiêu chí được ghi chép rõ ràng xác định khi nào mỗi thành phần phiên bản được tăng lên.           |   2    |   D/V   |
| AC.7.2 | Xác minh rằng các triển khai khẩn cấp yêu cầu có đánh giá rủi ro bảo mật được ghi chép và được sự phê duyệt từ cơ quan bảo mật được chỉ định trước trong khoảng thời gian đã được thỏa thuận trước. |   2    |   D/V   |
| AC.7.3 | Xác minh rằng các bản ghi khôi phục (phiên bản mô hình trước đó, cấu hình, phụ thuộc) được giữ lại theo chính sách của tổ chức.                                                                     |   2    |    V    |
| AC.7.4 | Xác minh rằng việc truy cập nhật ký kiểm toán yêu cầu sự ủy quyền phù hợp và tất cả các lần cố gắng truy cập đều được ghi lại với danh tính người dùng và dấu thời gian.                            |   2    |   D/V   |
| AC.7.5 | Xác minh rằng các bản mẫu mô hình đã nghỉ hưu được giữ lại theo chính sách lưu trữ dữ liệu.                                                                                                         |   1    |   D/V   |

---

## Quản trị An toàn Lời nhắc, Đầu vào và Đầu ra AC.8

### AC.8.1 Phòng chống tiêm nhiễm lệnh (Prompt Injection Defense)

|    #     | Mô tả                                                                                                                                                                                                                                        | Cấp độ | Vai trò |
| :------: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| AC.8.1.1 | Xác minh rằng các bài kiểm tra đánh giá đối kháng (ví dụ: các lời nhắc "many-shot" của Đội Đỏ) được thực hiện trước mỗi lần phát hành mô hình hoặc mẫu lời nhắc, với các ngưỡng tỷ lệ thành công và các bộ chặn tự động đối với các hồi quy. |   2    |   D/V   |
| AC.8.1.2 | Xác minh rằng tất cả các cập nhật quy tắc lọc lời nhắc, phiên bản mô hình phân loại và thay đổi danh sách chặn đều được kiểm soát phiên bản và có thể kiểm tra.                                                                              |   3    |   D/V   |

### AC.8.2 Kháng lại Ví dụ Đối kháng

|    #     | Mô tả                                                                                                                                                                    | Cấp độ | Vai trò |
| :------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| AC.8.2.1 | Xác minh rằng các chỉ số độ bền (tỷ lệ thành công của các bộ tấn công đã biết) được theo dõi theo thời gian thông qua tự động hóa và các lỗi hồi quy kích hoạt cảnh báo. |   3    |   D/V   |

### AC.8.3 Kiểm tra Nội dung & Chính sách

|    #     | Mô tả                                                                                                                                                               | Cấp độ | Vai trò |
| :------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| AC.8.3.1 | Xác minh rằng mô hình sàng lọc hoặc bộ quy tắc được đào tạo lại/cập nhật ít nhất mỗi quý, bao gồm các mẫu phá vỡ giới hạn hoặc bỏ qua chính sách mới được quan sát. |   2    |    D    |

### AC.8.4 Giới hạn tốc độ đầu vào & Ngăn chặn lạm dụng

|    #     | Mô tả                                                                                                              | Cấp độ | Vai trò |
| :------: | ------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| AC.8.4.1 | Xác minh rằng các bản ghi phòng ngừa lạm dụng được giữ lại và xem xét để phát hiện các mẫu tấn công mới xuất hiện. |   3    |    V    |

### AC.8.5 Nguồn gốc và Ghi nhận Đầu vào

|    #     | Mô tả                                                                                                                                                     | Cấp độ | Vai trò |
| :------: | --------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| AC.8.5.1 | Xác nhận rằng tất cả các đầu vào của người dùng đều được gắn thẻ với siêu dữ liệu (ID người dùng, phiên, nguồn, dấu thời gian, địa chỉ IP) khi nhập liệu. |   1    |   D/V   |
| AC.8.5.2 | Xác minh rằng siêu dữ liệu nguồn gốc được giữ lại và có thể kiểm tra được cho tất cả các đầu vào đã xử lý.                                                |   2    |   D/V   |
| AC.8.5.3 | Xác minh rằng các nguồn đầu vào bất thường hoặc không đáng tin cậy được đánh dấu và bị xem xét kỹ lưỡng hoặc chặn lại.                                    |   2    |   D/V   |

---

## AC.9 Xác thực đa phương thức, MLOps & Quản trị Hạ tầng

### AC.9.1 Quy trình xác thực bảo mật đa phương thức

|    #     | Mô tả                                                                                                                                                                                                                                          | Cấp độ | Vai trò |
| :------: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| AC.9.1.1 | Xác minh rằng các bộ phân loại nội dung theo từng phương thức được cập nhật theo lịch trình đã được ghi chép (tối thiểu hàng quý) với các mẫu mối đe dọa mới, ví dụ đối kháng, và các tiêu chuẩn hiệu suất được duy trì trên mức ngưỡng cơ sở. |   3    |   D/V   |

### AC.9.2 Bảo mật CI/CD và xây dựng

|    #     | Mô tả                                                                                                                                                     | Cấp độ | Vai trò |
| :------: | --------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| AC.9.2.1 | Xác nhận rằng mã hạ tầng như mã được quét trên mỗi lần commit, và các lần hợp nhất bị chặn khi có các phát hiện với mức độ nghiêm trọng cao hoặc rất cao. |   1    |   D/V   |
| AC.9.2.2 | Xác minh rằng các pipeline CI/CD sử dụng các danh tính có thời gian tồn tại ngắn và phạm vi hạn chế để truy cập vào bí mật và cơ sở hạ tầng.              |   2    |   D/V   |
| AC.9.2.3 | Xác minh rằng các môi trường xây dựng được cách ly với mạng lưới và dữ liệu sản xuất.                                                                     |   2    |   D/V   |

### AC.9.3 An ninh Container & Hình ảnh

|    #     | Mô tả                                                                                                                                                        | Cấp độ | Vai trò |
| :------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| AC.9.3.1 | Xác minh rằng các hình ảnh container được quét để chặn các bí mật mã cứng (ví dụ: khóa API, thông tin xác thực, chứng chỉ).                                  |   2    |   D/V   |
| AC.9.3.2 | Xác minh rằng các hình ảnh container được quét theo lịch trình của tổ chức với các lỗ hổng CRITICAL chặn việc triển khai dựa trên ngưỡng rủi ro của tổ chức. |   1    |   D/V   |

### AC.9.4 Giám sát, Cảnh báo & SIEM

|    #     | Mô tả                                                                                                                                                              | Cấp độ | Vai trò |
| :------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| AC.9.4.1 | Xác nhận rằng các cảnh báo bảo mật tích hợp với các nền tảng SIEM (Splunk, Elastic hoặc Sentinel) sử dụng định dạng CEF hoặc STIX/TAXII với việc làm giàu tự động. |   2    |    V    |

### AC.9.5 Quản lý Lỗ hổng Bảo mật

|    #     | Mô tả                                                                                                                                                                        | Cấp độ | Vai trò |
| :------: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| AC.9.5.1 | Xác minh rằng các lỗ hổng nghiêm trọng cao được vá theo các mốc thời gian quản lý rủi ro của tổ chức với các quy trình khẩn cấp dành cho các CVE đang bị khai thác tích cực. |   2    |   D/V   |

### AC.9.6 Cấu hình & Kiểm soát Trôi Drift

|    #     | Mô tả                                                                                                                                                                                              | Cấp độ | Vai trò |
| :------: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| AC.9.6.1 | Xác minh rằng hiện tượng lệch cấu hình được phát hiện bằng các công cụ (Chef InSpec, AWS Config) theo yêu cầu giám sát của tổ chức với khả năng tự động phục hồi cho các thay đổi không được phép. |   2    |   D/V   |

### AC.9.7 Tăng cường bảo mật Môi trường Sản xuất

|    #     | Mô tả                                                                                                                                                                                      | Cấp độ | Vai trò |
| :------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| AC.9.7.1 | Xác minh rằng các môi trường sản xuất chặn truy cập SSH, vô hiệu hóa các điểm cuối debug và yêu cầu các yêu cầu thay đổi với các yêu cầu thông báo trước tổ chức, trừ trường hợp khẩn cấp. |   2    |   D/V   |

### Cổng Kiểm Soát Quảng Bá Phiên Bản AC.9.8

|    #     | Mô tả                                                                                                                                                              | Cấp độ | Vai trò |
| :------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| AC.9.8.1 | Xác minh rằng các cổng thăng tiến bao gồm các bài kiểm tra bảo mật tự động (SAST, DAST, quét container) với yêu cầu không có phát hiện CRITICAL để được phê duyệt. |   2    |   D/V   |

### AC.9.9 Giám sát Khối lượng công việc, Công suất và Chi phí

|    #     | Mô tả                                                                                                                                                                                                                    | Cấp độ | Vai trò |
| :------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| AC.9.9.1 | Xác minh rằng việc sử dụng GPU/TPU được giám sát với cảnh báo được kích hoạt khi vượt ngưỡng do tổ chức định nghĩa và tự động mở rộng quy mô hoặc cân bằng tải được kích hoạt dựa trên các chính sách quản lý công suất. |   1    |   D/V   |
| AC.9.9.2 | Xác minh rằng các chỉ số tải công việc AI (độ trễ suy luận, thông lượng, tỷ lệ lỗi) được thu thập theo yêu cầu giám sát tổ chức và được đối chiếu với mức sử dụng hạ tầng.                                               |   1    |   D/V   |
| AC.9.9.3 | Xác nhận rằng việc giám sát chi phí theo dõi chi tiêu theo từng khối lượng công việc/người thuê với các cảnh báo dựa trên ngưỡng ngân sách tổ chức và các kiểm soát tự động cho các trường hợp vượt ngân sách.           |   2    |    V    |
| AC.9.9.4 | Xác nhận rằng lập kế hoạch năng lực sử dụng dữ liệu lịch sử với các khoảng thời gian dự báo được định nghĩa bởi tổ chức và cung cấp tài nguyên tự động dựa trên các mẫu nhu cầu.                                         |   3    |    V    |

### AC.9.10 Phê duyệt & Dấu vết kiểm toán

|     #     | Mô tả                                                                                                                                                                          | Cấp độ | Vai trò |
| :-------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| AC.9.10.1 | Xác minh rằng việc thăng cấp môi trường yêu cầu sự phê duyệt từ nhân sự được tổ chức xác định có thẩm quyền, kèm theo chữ ký mật mã và các hồ sơ kiểm toán không thể thay đổi. |   1    |   D/V   |

### AC.9.11 Quản trị IaC

|     #     | Mô tả                                                                                                                                             | Cấp độ | Vai trò |
| :-------: | ------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| AC.9.11.1 | Xác minh rằng các thay đổi hạ tầng như mã nguồn yêu cầu xem xét đồng cấp kèm theo kiểm tra tự động và quét bảo mật trước khi gộp vào nhánh chính. |   2    |   D/V   |

### AC.9.12 Xử lý Dữ liệu trong Môi trường Phi Sản xuất

|     #     | Mô tả                                                                                                                                                                                                                                       | Cấp độ | Vai trò |
| :-------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| AC.9.12.1 | Xác minh rằng dữ liệu không phục vụ sản xuất đã được ẩn danh theo các yêu cầu về quyền riêng tư của tổ chức, việc tạo dữ liệu tổng hợp hoặc che giấu dữ liệu hoàn toàn với việc loại bỏ thông tin nhận dạng cá nhân (PII) đã được xác minh. |   2    |   D/V   |

### AC.9.13 Sao lưu & Phục hồi sau thảm họa

|     #     | Mô tả                                                                                                                                                                          | Cấp độ | Vai trò |
| :-------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| AC.9.13.1 | Xác minh rằng các cấu hình hạ tầng được sao lưu theo lịch sao lưu của tổ chức tới các vùng địa lý tách biệt với việc triển khai chiến lược sao lưu 3-2-1.                      |   1    |   D/V   |
| AC.9.13.2 | Xác minh rằng các quy trình phục hồi được kiểm tra và xác thực thông qua kiểm thử tự động theo lịch trình của tổ chức với các mục tiêu RTO và RPO đáp ứng yêu cầu của tổ chức. |   2    |    V    |
| AC.9.13.3 | Xác nhận rằng kế hoạch phục hồi thảm họa bao gồm các sổ tay chạy riêng cho AI với việc khôi phục trọng số mô hình, xây dựng lại cụm GPU và lập bản đồ phụ thuộc dịch vụ.       |   3    |    V    |

### Tuân thủ & Tài liệu AC.9.14

|     #     | Mô tả                                                                                                                                                                              | Cấp độ | Vai trò |
| :-------: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| AC.9.14.1 | Xác minh rằng việc đánh giá tuân thủ hạ tầng được thực hiện theo lịch trình của tổ chức dựa trên các kiểm soát SOC 2, ISO 27001 hoặc FedRAMP với việc thu thập bằng chứng tự động. |   2    |   D/V   |
| AC.9.14.2 | Xác minh rằng tài liệu hạ tầng bao gồm sơ đồ mạng, bản đồ luồng dữ liệu và mô hình đe dọa được cập nhật theo yêu cầu quản lý thay đổi tổ chức.                                     |   2    |    V    |
| AC.9.14.3 | Xác minh rằng các thay đổi cơ sở hạ tầng trải qua đánh giá tác động tuân thủ tự động với quy trình phê duyệt theo quy định cho các sửa đổi có rủi ro cao.                          |   3    |   D/V   |

### AC.9.15 Phần cứng & Chuỗi cung ứng

|     #     | Mô tả                                                                                                                                                                   | Cấp độ | Vai trò |
| :-------: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| AC.9.15.1 | Xác nhận rằng firmware của bộ tăng tốc AI (BIOS GPU, firmware TPU) được xác minh bằng chữ ký mật mã và được cập nhật theo các mốc thời gian quản lý bản vá của tổ chức. |   2    |   D/V   |
| AC.9.15.2 | Xác minh rằng chuỗi cung ứng phần cứng AI bao gồm việc kiểm tra nguồn gốc với giấy chứng nhận của nhà sản xuất và xác nhận bao bì chống giả mạo.                        |   3    |    V    |

### AC.9.16 Chiến lược Điện toán đám mây & Khả năng di động

|     #     | Mô tả                                                                                                                                                                                            | Cấp độ | Vai trò |
| :-------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| AC.9.16.1 | Xác minh rằng việc ngăn ngừa khóa nhà cung cấp đám mây bao gồm cơ sở hạ tầng dưới dạng mã có thể di động, các API tiêu chuẩn hóa, và khả năng xuất dữ liệu với các công cụ chuyển đổi định dạng. |   3    |    V    |
| AC.9.16.2 | Xác minh rằng tối ưu hóa chi phí đa đám mây bao gồm các kiểm soát bảo mật ngăn chặn sự lan tràn tài nguyên cũng như các khoản phí chuyển dữ liệu không được phép giữa các đám mây.               |   3    |    V    |

### AC.9.17 GitOps & Tự phục hồi

|     #     | Mô tả                                                                                                                                                        | Cấp độ | Vai trò |
| :-------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| AC.9.17.1 | Xác minh rằng các kho GitOps yêu cầu các cam kết được ký bằng khóa GPG và các quy tắc bảo vệ nhánh ngăn chặn việc đẩy trực tiếp lên các nhánh chính.         |   2    |   D/V   |
| AC.9.17.2 | Xác minh rằng cơ sở hạ tầng tự phục hồi bao gồm việc tương quan sự kiện bảo mật với phản hồi sự cố tự động và các quy trình thông báo cho các bên liên quan. |   3    |    V    |

### AC.9.18 Zero-Trust, Đại lý, Cấp phát & Xác nhận Cư trú

|     #     | Mô tả                                                                                                                                                            | Cấp độ | Vai trò |
| :-------: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| AC.9.18.1 | Xác minh rằng truy cập tài nguyên đám mây bao gồm xác thực không-trust với xác thực liên tục.                                                                    |   2    |   D/V   |
| AC.9.18.2 | Xác minh rằng việc cung cấp hạ tầng tự động bao gồm việc kiểm tra chính sách bảo mật với việc chặn triển khai đối với các cấu hình không tuân thủ.               |   2    |   D/V   |
| AC.9.18.3 | Xác minh rằng việc cung cấp hạ tầng tự động kiểm tra các chính sách bảo mật trong quá trình CI/CD, với các cấu hình không tuân thủ bị chặn khỏi việc triển khai. |   2    |   D/V   |
| AC.9.18.4 | Xác nhận rằng các yêu cầu về cư trú dữ liệu được thực thi thông qua việc chứng thực mã hóa vị trí lưu trữ.                                                       |   3    |   D/V   |
| AC.9.18.5 | Xác minh rằng các đánh giá bảo mật của nhà cung cấp đám mây bao gồm mô hình hóa mối đe dọa và đánh giá rủi ro cụ thể cho từng tác nhân.                          |   3    |   D/V   |

### AC.9.19 Kiểm soát truy cập & Danh tính

|   #   | Mô tả                                                                                                                                                                                             | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 5.1.3 | Xác minh rằng các cán bộ mới trải qua quy trình chứng thực danh tính phù hợp với tiêu chuẩn NIST 800-63-3 IAL-2 hoặc tiêu chuẩn tương đương trước khi được cấp quyền truy cập hệ thống sản xuất.  |   2    |    D    |
| 5.1.4 | Xác minh rằng các đánh giá truy cập được thực hiện hàng quý với việc phát hiện tự động các tài khoản không hoạt động, thực thi xoay vòng chứng chỉ và các quy trình gỡ bỏ quyền truy cập.         |   2    |    V    |
| 5.2.2 | Xác nhận rằng các nguyên tắc quyền hạn tối thiểu được áp dụng mặc định với các tài khoản dịch vụ bắt đầu từ quyền chỉ đọc và yêu cầu có lý do kinh doanh được ghi chép rõ ràng để được quyền ghi. |   1    |   D/V   |
| 5.3.3 | Xác nhận rằng các định nghĩa chính sách được kiểm soát phiên bản, được đồng nghiệp xem xét, và được xác thực thông qua kiểm thử tự động trong các pipeline CI/CD trước khi triển khai sản xuất.   |   2    |    D    |
| 5.3.4 | Xác minh rằng kết quả đánh giá chính sách bao gồm các lý do quyết định và được truyền tới hệ thống SIEM để phân tích tương quan và báo cáo tuân thủ.                                              |   2    |    V    |
| 5.4.4 | Xác nhận rằng độ trễ đánh giá chính sách được theo dõi liên tục với các cảnh báo tự động cho các điều kiện hết thời gian có thể cho phép vượt qua xác thực.                                       |   2    |    V    |
| 5.5.4 | Xác minh rằng các thuật toán che giấu thông tin là xác định, được kiểm soát phiên bản và duy trì nhật ký kiểm toán để hỗ trợ điều tra tuân thủ và phân tích pháp y.                               |   2    |    V    |
| 5.5.5 | Xác minh rằng các sự kiện ẩn dữ liệu có rủi ro cao tạo ra nhật ký thích ứng bao gồm các hàm băm mật mã của nội dung gốc để truy xuất pháp y mà không làm lộ dữ liệu.                              |   3    |    V    |
| 5.7.5 | Xác minh rằng các điều kiện lỗi của tác nhân và xử lý ngoại lệ bao gồm thông tin phạm vi khả năng để hỗ trợ phân tích sự cố và điều tra pháp y.                                                   |   3    |    V    |
| 5.4.2 | Xác minh rằng các trích dẫn, tham chiếu và nguồn gốc trong kết quả của mô hình được kiểm tra theo quyền hạn của người gọi và loại bỏ nếu phát hiện truy cập trái phép.                            |   1    |   D/V   |

### Các Mục Mới cần được Tích Hợp Phía Trên

|   #   | Mô tả                                                                                                                    | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 2.3.3 | Xác minh rằng tập hợp ký tự được phép được xem xét và cập nhật định kỳ để đảm bảo nó vẫn phù hợp với yêu cầu kinh doanh. |   2    |   D/V   |

