# Bảo mật Bộ nhớ C8, Nhúng và Cơ sở dữ liệu Vector

## Mục tiêu Kiểm soát

Embedding và kho vectơ hoạt động như "bộ nhớ sống" của các hệ thống AI hiện đại, liên tục nhận dữ liệu do người dùng cung cấp và phản hồi lại dữ liệu đó vào ngữ cảnh của mô hình thông qua Phát sinh Tăng cường Truy xuất (RAG). Nếu không được kiểm soát, bộ nhớ này có thể rò rỉ Thông tin Nhận dạng Cá nhân (PII), vi phạm sự đồng thuận hoặc bị đảo ngược để tái tạo lại văn bản gốc. Mục tiêu của nhóm kiểm soát này là củng cố các đường dẫn bộ nhớ và các cơ sở dữ liệu vectơ sao cho quyền truy cập là giới hạn thấp nhất, embedding bảo vệ quyền riêng tư, các vectơ lưu trữ hết hạn hoặc có thể bị thu hồi theo yêu cầu, và bộ nhớ riêng của mỗi người dùng không bao giờ làm nhiễm bẩn các lời nhắc hoặc kết quả hoàn thành của người dùng khác.

---

## C8.1 Kiểm soát truy cập trên bộ nhớ & các chỉ số RAG

Thực thi kiểm soát truy cập chi tiết trên mọi bộ sưu tập vector.

|   #   | Mô tả                                                                                                                                                             | Cấp độ | Vai trò |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 8.1.1 | Xác minh rằng các quy tắc kiểm soát truy cập ở cấp hàng/khoảng tên hạn chế các thao tác chèn, xóa và truy vấn theo từng người thuê, bộ sưu tập hoặc thẻ tài liệu. |   1    |   D/V   |
| 8.1.2 | Xác minh rằng các khóa API hoặc JWT mang các yêu cầu có phạm vi (ví dụ: ID bộ sưu tập, các động từ hành động) và được thay đổi ít nhất mỗi quý.                   |   1    |   D/V   |
| 8.1.3 | Xác minh rằng các nỗ lực leo thang đặc quyền (ví dụ: các truy vấn tương đồng chéo namespace) được phát hiện và ghi lại vào hệ thống SIEM trong vòng 5 phút.       |   2    |   D/V   |
| 8.1.4 | Xác minh rằng cơ sở dữ liệu vector ghi lại nhật ký các thông tin: định danh chủ thể, thao tác, ID vector/không gian tên, ngưỡng tương đồng và số lượng kết quả.   |   2    |   D/V   |
| 8.1.5 | Xác minh rằng các quyết định truy cập được kiểm tra để phát hiện lỗi bỏ qua mỗi khi các động cơ được nâng cấp hoặc quy tắc phân mảnh chỉ mục thay đổi.            |   3    |    V    |

---

## C8.2 Làm sạch và Xác thực Nhúng

Tiền xử lý văn bản để phát hiện thông tin cá nhân (PII), che dấu hoặc giả danh trước khi biến đổi thành vector, và có thể xử lý hậu kỳ embedding để loại bỏ các tín hiệu dư thừa.

|   #   | Mô tả                                                                                                                                                                                                       | Cấp độ | Vai trò |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 8.2.1 | Xác minh rằng dữ liệu PII và dữ liệu được quy định được phát hiện qua các bộ phân loại tự động và được che phủ, mã thông báo hóa hoặc loại bỏ trước khi nhúng.                                              |   1    |   D/V   |
| 8.2.2 | Xác minh rằng các pipeline nhúng từ chối hoặc cách ly các đầu vào chứa mã thực thi hoặc các hiện vật không phải UTF-8 có thể làm ô nhiễm chỉ mục.                                                           |   1    |    D    |
| 8.2.3 | Xác minh rằng việc làm sạch bảo mật vi phân cục bộ hoặc bảo mật vi phân theo chuẩn được áp dụng cho các biểu diễn câu mà khoảng cách tới bất kỳ token PII nào đã biết thấp hơn ngưỡng có thể cấu hình.      |   2    |   D/V   |
| 8.2.4 | Xác minh rằng hiệu quả làm sạch dữ liệu (ví dụ, tỷ lệ phát hiện thông tin nhận dạng cá nhân (PII) bị che khuất, độ trôi ngữ nghĩa) được xác nhận ít nhất hai lần mỗi năm dựa trên các tập chuẩn tham chiếu. |   2    |    V    |
| 8.2.5 | Xác minh rằng các cấu hình lọc dữ liệu được quản lý phiên bản và các thay đổi được xem xét bởi đồng nghiệp.                                                                                                 |   3    |   D/V   |

---

## C8.3 Hết hạn Bộ nhớ, Thu hồi & Xóa bỏ

Quyền "được quên" theo GDPR và các luật tương tự yêu cầu việc xóa dữ liệu kịp thời; do đó, các kho vectơ phải hỗ trợ TTL, xóa cứng và đánh dấu xóa để các vectơ bị thu hồi không thể được khôi phục hoặc lập chỉ mục lại.

|   #   | Mô tả                                                                                                                                                             | Cấp độ | Vai trò |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 8.3.1 | Xác minh rằng mỗi vector và bản ghi siêu dữ liệu đều mang nhãn TTL hoặc nhãn lưu giữ rõ ràng được các công việc dọn dẹp tự động tuân thủ.                         |   1    |   D/V   |
| 8.3.2 | Xác minh rằng các yêu cầu xóa do người dùng khởi tạo sẽ xoá hoàn toàn các vector, siêu dữ liệu, bản sao bộ nhớ đệm và các chỉ mục dẫn xuất trong vòng 30 ngày.    |   1    |   D/V   |
| 8.3.3 | Xác minh rằng việc xóa logic được thực hiện theo sau bằng việc tiêu hủy mã hóa các khối lưu trữ nếu phần cứng hỗ trợ, hoặc bằng cách phá hủy khóa trong kho khóa. |   2    |    D    |
| 8.3.4 | Xác nhận rằng các vector đã hết hạn được loại trừ khỏi kết quả tìm kiếm gần nhất trong thời gian < 500 ms sau khi hết hạn.                                        |   3    |   D/V   |

---

## C8.4 Ngăn chặn Đảo ngược và Rò rỉ Embedding

Các biện pháp phòng thủ gần đây—phép chồng nhiễu, mạng chiếu, làm nhiễu neuron bảo mật, và mã hóa lớp ứng dụng—có thể giảm tỷ lệ đảo ngược cấp token xuống dưới 5%.

|   #   | Mô tả                                                                                                                                                          | Cấp độ | Vai trò |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 8.4.1 | Xác minh rằng một mô hình đe dọa chính thức bao gồm các tấn công đảo ngược, thành viên và suy luận thuộc tính tồn tại và được xem xét hàng năm.                |   1    |    V    |
| 8.4.2 | Xác minh rằng mã hóa tầng ứng dụng hoặc mã hóa có thể tìm kiếm bảo vệ các vector khỏi việc đọc trực tiếp bởi quản trị viên hạ tầng hoặc nhân viên đám mây.     |   2    |   D/V   |
| 8.4.3 | Xác minh rằng các tham số phòng thủ (ε đối với DP, độ ồn σ, hạng chiếu k) cân bằng giữa bảo mật riêng tư ≥ 99% bảo vệ token và tiện ích ≤ 3% mất độ chính xác. |   3    |    V    |
| 8.4.4 | Xác minh rằng các chỉ số chống đảo chiều là một phần của các cửa kiểm soát phát hành cho các bản cập nhật mô hình, với ngân sách hồi quy được xác định.        |   3    |   D/V   |

---

## C8.5 Thực thi phạm vi cho Bộ nhớ Cụ thể Người dùng

Rò rỉ giữa các tổ chức vẫn là rủi ro hàng đầu của RAG: các truy vấn tương tự được lọc không đúng cách có thể làm lộ tài liệu riêng tư của khách hàng khác.

|   #   | Mô tả                                                                                                                                                                              | Cấp độ | Vai trò |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 8.5.1 | Xác minh rằng mọi truy vấn tìm kiếm đều được lọc sau theo ID người thuê/người dùng trước khi được chuyển đến prompt của LLM.                                                       |   1    |   D/V   |
| 8.5.2 | Xác minh rằng tên bộ sưu tập hoặc ID có phạm vi tên được thêm muối theo từng người dùng hoặc thuê bao để các vector không bị trùng lặp giữa các phạm vi.                           |   1    |    D    |
| 8.5.3 | Xác nhận rằng các kết quả tương đồng vượt quá ngưỡng khoảng cách có thể cấu hình nhưng nằm ngoài phạm vi của người gọi sẽ bị loại bỏ và kích hoạt cảnh báo an ninh.                |   2    |   D/V   |
| 8.5.4 | Xác minh rằng các bài kiểm tra áp lực đa người thuê giả lập các truy vấn đối kháng cố gắng truy xuất các tài liệu ngoài phạm vi và chứng minh không có rò rỉ thông tin nào xảy ra. |   2    |    V    |
| 8.5.5 | Xác minh rằng các khóa mã hóa được phân tách theo từng người thuê, đảm bảo sự cô lập mật mã ngay cả khi lưu trữ vật lý được chia sẻ.                                               |   3    |   D/V   |

---

## C8.6 Bảo mật Hệ thống Bộ nhớ Nâng cao

Các kiểm soát bảo mật cho các kiến trúc bộ nhớ phức tạp bao gồm bộ nhớ theo tập sự kiện, bộ nhớ ngữ nghĩa và bộ nhớ làm việc với các yêu cầu cụ thể về cách ly và xác thực.

|   #   | Mô tả                                                                                                                                                                                                                                                           | Cấp độ | Vai trò |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 8.6.1 | Xác minh rằng các loại bộ nhớ khác nhau (bộ nhớ sự kiện, bộ nhớ ngữ nghĩa, bộ nhớ làm việc) có các ngữ cảnh bảo mật riêng biệt với kiểm soát truy cập dựa trên vai trò, khóa mã hóa riêng biệt và các mẫu truy cập được ghi nhận cho từng loại bộ nhớ.          |   1    |   D/V   |
| 8.6.2 | Xác nhận rằng các quy trình củng cố bộ nhớ bao gồm kiểm tra bảo mật nhằm ngăn chặn việc tiêm nhiễm các ký ức độc hại thông qua việc làm sạch nội dung, xác minh nguồn và kiểm tra tính toàn vẹn trước khi lưu trữ.                                              |   2    |   D/V   |
| 8.6.3 | Xác minh rằng các truy vấn truy xuất bộ nhớ được xác thực và làm sạch để ngăn chặn việc trích xuất thông tin trái phép thông qua phân tích mẫu truy vấn, thực thi kiểm soát truy cập và lọc kết quả.                                                            |   2    |   D/V   |
| 8.6.4 | Xác minh rằng các cơ chế quên bộ nhớ xóa bỏ thông tin nhạy cảm một cách an toàn với các đảm bảo xoá dữ liệu mật mã bằng cách xoá khóa, ghi đè nhiều lần hoặc xoá an toàn dựa trên phần cứng kèm theo chứng chỉ xác minh.                                        |   3    |   D/V   |
| 8.6.5 | Xác minh rằng tính toàn vẹn của hệ thống bộ nhớ được giám sát liên tục để phát hiện các sửa đổi trái phép hoặc hư hỏng thông qua việc sử dụng checksum, nhật ký kiểm toán và cảnh báo tự động khi nội dung bộ nhớ thay đổi ngoài phạm vi hoạt động bình thường. |   3    |   D/V   |

---

## Tài liệu tham khảo

* [Vector database security: Pinecone – IronCore Labs](https://ironcorelabs.com/vectordbs/pinecone-security/)
* [Securing the Backbone of AI: Safeguarding Vector Databases and Embeddings – Privacera](https://privacera.com/blog/securing-the-backbone-of-ai-safeguarding-vector-databases-and-embeddings/)
* [Enhancing Data Security with RBAC of Qdrant Vector Database – AI Advances](https://ai.gopubby.com/enhancing-data-security-with-role-based-access-control-of-qdrant-vector-database-3878769bec83)
* [Mitigating Privacy Risks in LLM Embeddings from Embedding Inversion – arXiv](https://arxiv.org/html/2411.05034v1)
* [DPPN: Detecting and Perturbing Privacy-Sensitive Neurons – OpenReview](https://openreview.net/forum?id=DF5TVzpTW0)
* [Art. 17 GDPR – Right to Erasure](https://gdpr-info.eu/art-17-gdpr/)
* [Sensitive Data in Text Embeddings Is Recoverable – Tonic.ai](https://www.tonic.ai/blog/sensitive-data-in-text-embeddings-is-recoverable)
* [PII Identification and Removal – NVIDIA NeMo Docs](https://docs.nvidia.com/nemo-framework/user-guide/latest/datacuration/personalidentifiableinformationidentificationandremoval.html)
* [De-identifying Sensitive Data – Google Cloud DLP](https://cloud.google.com/sensitive-data-protection/docs/deidentify-sensitive-data)
* [Remove PII from Conversations Using Sensitive Information Filters – AWS Bedrock Guardrails](https://docs.aws.amazon.com/bedrock/latest/userguide/guardrails-sensitive-filters.html)
* [Think Your RAG Is Secure? Think Again – Medium](https://medium.com/%40vijay.poudel1/think-your-rag-is-secure-think-again-heres-how-to-actually-lock-it-down-c4c30e3864e7)
* [Design a Secure Multitenant RAG Inferencing Solution – Microsoft Learn](https://learn.microsoft.com/en-us/azure/architecture/ai-ml/guide/secure-multitenant-rag)
* [Best Practices for Multi-Tenancy RAG with Milvus – Milvus Blog](https://milvus.io/blog/build-multi-tenancy-rag-with-milvus-best-practices-part-one.md)

