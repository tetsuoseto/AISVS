# Phụ lục B: Kiểm soát chiến lược

## C4.15 An ninh Hạ tầng Chống Lượng tử

Chuẩn bị hạ tầng AI để đối phó với các mối đe dọa từ điện toán lượng tử thông qua mật mã hậu lượng tử và các giao thức an toàn lượng tử.

|   #    | Mô tả                                                                                                                                                                                               | Cấp độ | Vai trò |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 4.15.1 | Xác minh rằng hạ tầng AI triển khai các thuật toán mật mã hậu lượng tử được NIST phê duyệt (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) cho trao đổi khóa và chữ ký số.                           |   3    |   D/V   |
| 4.15.2 | Xác minh rằng các hệ thống phân phối khóa lượng tử (QKD) được triển khai cho các giao tiếp AI có độ bảo mật cao với các giao thức quản lý khóa an toàn trước lượng tử.                              |   3    |   D/V   |
| 4.15.3 | Xác nhận rằng các khung công tác linh hoạt về mật mã cho phép di chuyển nhanh chóng sang các thuật toán hậu lượng tử mới với việc tự động quay vòng chứng chỉ và khóa.                              |   3    |   D/V   |
| 4.15.4 | Xác minh rằng mô hình hóa rủi ro lượng tử đánh giá mức độ dễ bị tổn thương của hạ tầng AI trước các cuộc tấn công lượng tử với các mốc thời gian di chuyển đã được ghi nhận và các đánh giá rủi ro. |   3    |    V    |
| 4.15.5 | Xác minh rằng các hệ thống mật mã lai cổ điển - lượng tử cung cấp phòng thủ đa lớp trong giai đoạn chuyển tiếp lượng tử kèm theo việc giám sát hiệu suất.                                           |   3    |   D/V   |

---

## C4.17 Hạ tầng Kiến thức Bất Biết

Triển khai các hệ thống chứng minh không kiến thức để xác minh và xác thực AI bảo vệ quyền riêng tư mà không tiết lộ thông tin nhạy cảm.

|   #    | Mô tả                                                                                                                                                                                         | Cấp độ | Vai trò |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 4.17.1 | Xác minh rằng các bằng chứng không tiết lộ thông tin (ZK-SNARKs, ZK-STARKs) đảm bảo tính toàn vẹn của mô hình AI và nguồn gốc đào tạo mà không tiết lộ trọng số mô hình hoặc dữ liệu đào tạo. |   3    |   D/V   |
| 4.17.2 | Xác minh rằng các hệ thống xác thực dựa trên ZK cho phép xác minh người dùng bảo vệ quyền riêng tư cho các dịch vụ AI mà không tiết lộ thông tin liên quan đến danh tính.                     |   3    |   D/V   |
| 4.17.3 | Xác minh rằng các giao thức giao nhau tập hợp riêng tư (PSI) cho phép khớp dữ liệu an toàn cho AI liên kết mà không làm lộ các tập dữ liệu cá nhân.                                           |   3    |   D/V   |
| 4.17.4 | Xác minh rằng các hệ thống học máy không kiến thức (ZKML) cho phép những suy luận AI có thể kiểm chứng với bằng chứng mật mã về tính toán đúng.                                               |   3    |   D/V   |
| 4.17.5 | Xác minh rằng ZK-rollups cung cấp quá trình xử lý giao dịch AI có thể mở rộng, bảo vệ quyền riêng tư với xác minh theo lô và giảm tải tính toán.                                              |   3    |   D/V   |

---

## C4.18 Phòng ngừa tấn công kênh bên

Bảo vệ hạ tầng AI khỏi các cuộc tấn công kênh bên dựa trên thời gian, công suất, điện từ, và bộ nhớ đệm có thể làm rò rỉ thông tin nhạy cảm.

|   #    | Mô tả                                                                                                                                                                              | Cấp độ | Vai trò |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 4.18.1 | Xác minh rằng thời gian suy luận AI được chuẩn hóa bằng cách sử dụng các thuật toán thời gian cố định và đệm để ngăn chặn các cuộc tấn công trích xuất mô hình dựa trên thời gian. |   3    |   D/V   |
| 4.18.2 | Xác minh rằng biện pháp bảo vệ phân tích công suất bao gồm tiêm nhiễu, lọc đường dây điện và các mẫu thực thi ngẫu nhiên cho phần cứng AI.                                         |   3    |   D/V   |
| 4.18.3 | Xác minh rằng biện pháp giảm thiểu kênh bên dựa trên bộ nhớ đệm sử dụng phân vùng bộ nhớ đệm, ngẫu nhiên hóa và lệnh xả để ngăn chặn rò rỉ thông tin.                              |   3    |   D/V   |
| 4.18.4 | Xác minh rằng việc bảo vệ phát xạ điện từ bao gồm chắn sóng, lọc tín hiệu và xử lý ngẫu nhiên để ngăn ngừa các cuộc tấn công kiểu TEMPEST.                                         |   3    |   D/V   |
| 4.18.5 | Xác minh rằng các biện pháp phòng thủ kênh bên vi kiến trúc bao gồm kiểm soát thực thi dự đoán và làm mờ mẫu truy cập bộ nhớ.                                                      |   3    |   D/V   |

---

## C4.19 An ninh phần cứng AI chuyên biệt & dựa trên mô phỏng thần kinh

Bảo mật các kiến trúc phần cứng AI mới nổi bao gồm chip thần kinh, FPGA, ASIC tùy chỉnh và hệ thống tính toán quang học.

|   #    | Mô tả                                                                                                                                                                   | Cấp độ | Vai trò |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 4.19.1 | Xác nhận rằng bảo mật chip neuromorphic bao gồm mã hóa mẫu xung, bảo vệ trọng số synapse và xác thực quy tắc học dựa trên phần cứng.                                    |   3    |   D/V   |
| 4.19.2 | Xác minh rằng các bộ tăng tốc AI dựa trên FPGA thực hiện mã hóa luồng bit, cơ chế chống giả mạo và tải cấu hình an toàn với các bản cập nhật đã xác thực.               |   3    |   D/V   |
| 4.19.3 | Xác minh rằng bảo mật ASIC tùy chỉnh bao gồm các bộ xử lý bảo mật trên chip, gốc tin cậy phần cứng và lưu trữ khóa an toàn với phát hiện chống giả mạo.                 |   3    |   D/V   |
| 4.19.4 | Xác minh rằng các hệ thống tính toán quang học thực hiện mã hóa quang học an toàn trước lượng tử, chuyển mạch quang tử bảo mật và xử lý tín hiệu quang học được bảo vệ. |   3    |   D/V   |
| 4.19.5 | Xác minh rằng các chip AI lai tương tự-số bao gồm tính toán tương tự an toàn, lưu trữ trọng số được bảo vệ và chuyển đổi tương tự-số được xác thực.                     |   3    |   D/V   |

---

## Hạ tầng tính toán bảo vệ quyền riêng tư C4.20

Triển khai các biện pháp kiểm soát hạ tầng cho tính toán bảo vệ quyền riêng tư nhằm bảo vệ dữ liệu nhạy cảm trong quá trình xử lý và phân tích AI.

|   #    | Mô tả                                                                                                                                                                                                | Cấp độ | Vai trò |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 4.20.1 | Xác minh rằng cơ sở hạ tầng mã hóa đồng dạng cho phép tính toán trên dữ liệu được mã hóa cho các khối lượng công việc AI nhạy cảm với việc kiểm tra tính toàn vẹn bằng mật mã và giám sát hiệu suất. |   3    |   D/V   |
| 4.20.2 | Xác minh rằng các hệ thống truy xuất thông tin riêng tư cho phép truy vấn cơ sở dữ liệu mà không tiết lộ mẫu truy vấn với sự bảo vệ mật mã đối với mẫu truy cập.                                     |   3    |   D/V   |
| 4.20.3 | Xác minh rằng các giao thức tính toán đa bên an toàn cho phép suy luận AI bảo vệ quyền riêng tư mà không tiết lộ các đầu vào cá nhân hoặc các phép tính trung gian.                                  |   3    |   D/V   |
| 4.20.4 | Xác minh rằng quản lý khóa bảo vệ quyền riêng tư bao gồm tạo khóa phân tán, mật mã ngưỡng và xoay khóa an toàn với sự bảo vệ dựa trên phần cứng.                                                     |   3    |   D/V   |
| 4.20.5 | Xác minh rằng hiệu suất tính toán bảo vệ quyền riêng tư được tối ưu hóa thông qua việc xử lý theo lô, lưu trong bộ nhớ đệm, và tăng tốc phần cứng trong khi vẫn duy trì các đảm bảo bảo mật mật mã.  |   3    |   D/V   |

| 4.9.1 | Xác minh rằng tất cả các môi trường đám mây đều được tích hợp vào các hệ thống danh tính tập trung để đảm bảo xác thực nhất quán. | 1 | D/V |
| 4.9.2 | Xác minh rằng triển khai đa đám mây sử dụng các tiêu chuẩn định danh liên minh (ví dụ, OIDC, SAML) với việc thực thi chính sách tập trung trên các nhà cung cấp. | 2 | D/V |
| 4.9.3 | Xác minh rằng các chuyển dữ liệu giữa các đám mây và dữ liệu lai sử dụng mã hóa đầu cuối với khóa do khách hàng quản lý và thực thi các yêu cầu cư trú dữ liệu theo thẩm quyền. | 2 | D/V |
| 4.9.1 | Xác minh rằng việc tích hợp lưu trữ đám mây sử dụng mã hóa đầu-cuối với quản lý khóa do tác nhân kiểm soát. | 1 | D/V |
| 4.9.2 | Xác minh rằng các ranh giới bảo mật triển khai lai được xác định rõ ràng với các kênh truyền thông được mã hóa. | 2 | D/V |

