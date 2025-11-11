# Bộ nhớ C8, Chèn nhúng & Bảo mật cơ sở dữ liệu véc-tơ

## Mục tiêu Kiểm soát

Embedding và kho vector hoạt động như "bộ nhớ sống" của các hệ thống AI hiện đại, liên tục tiếp nhận dữ liệu do người dùng cung cấp và phản hồi nó vào các ngữ cảnh mô hình thông qua Retrieval-Augmented Generation (RAG). Nếu không được quản lý, bộ nhớ này có thể làm rò rỉ thông tin cá nhân (PII), vi phạm sự đồng ý, hoặc bị đảo ngược để tái tạo lại văn bản gốc. Mục tiêu của nhóm kiểm soát này là củng cố các đường dẫn bộ nhớ và cơ sở dữ liệu vector sao cho quyền truy cập được giới hạn tối thiểu, embedding giữ được sự riêng tư, các vector lưu trữ có thể hết hạn hoặc bị thu hồi theo yêu cầu, và bộ nhớ theo người dùng không bao giờ làm ảnh hưởng đến các lệnh nhắc hoặc kết quả của người dùng khác.

---

## C8.1 Kiểm soát truy cập trên bộ nhớ & chỉ số RAG

Áp dụng các biện pháp kiểm soát truy cập chi tiết cho mọi bộ sưu tập vectơ.

|   #   | Mô tả                                                                                                                                                          | Cấp độ | Vai trò |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 8.1.1 | Xác minh rằng các quy tắc kiểm soát truy cập cấp hàng/namespace giới hạn các thao tác chèn, xóa và truy vấn theo từng tenant, bộ sưu tập hoặc thẻ tài liệu.    |   1    |   D/V   |
| 8.1.2 | Xác minh rằng các khóa API hoặc JWT mang các quyền truy cập có phạm vi (ví dụ: ID bộ sưu tập, động từ hành động) và được thay đổi ít nhất mỗi quý.             |   1    |   D/V   |
| 8.1.3 | Xác minh rằng các nỗ lực leo thang đặc quyền (ví dụ: truy vấn tương đồng chéo namespace) được phát hiện và ghi nhật ký vào SIEM trong vòng 5 phút.             |   2    |   D/V   |
| 8.1.4 | Xác minh rằng cơ sở dữ liệu vector ghi lại nhật ký các mục sau: định danh chủ thể, thao tác, ID vector/không gian tên, ngưỡng tương đồng, và số lượng kết quả. |   2    |   D/V   |
| 8.1.5 | Xác minh rằng các quyết định truy cập được kiểm tra lỗi vượt qua mỗi khi các engine được nâng cấp hoặc quy tắc phân mảnh chỉ mục thay đổi.                     |   3    |    V    |

---

## C8.2 Sàng lọc và Xác thực Nhúng

Tiền xử lý văn bản để loại bỏ thông tin nhận dạng cá nhân (PII), che giấu hoặc thay thế bằng bí danh trước khi chuyển đổi thành vector, và tùy chọn xử lý hậu kỳ embeddings để loại bỏ các tín hiệu còn sót lại.

|   #   | Mô tả                                                                                                                                                                                                                                      | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 8.2.1 | Xác minh rằng dữ liệu PII và dữ liệu được quy định được phát hiện thông qua bộ phân loại tự động và được che mặt, mã token hoặc loại bỏ trước khi nhúng.                                                                                   |   1    |   D/V   |
| 8.2.2 | Xác minh rằng các quy trình nhúng từ chối hoặc cách ly các đầu vào chứa mã thực thi hoặc các ký tự không phải UTF-8 có thể làm nhiễm độc chỉ mục.                                                                                          |   1    |    D    |
| 8.2.3 | Xác minh rằng việc xử lý làm sạch bảo mật vi phân cục bộ hoặc bảo mật vi phân metric được áp dụng cho các biểu diễn câu mà khoảng cách đến bất kỳ token PII (Thông tin nhận dạng cá nhân) đã biết nào thấp hơn một ngưỡng có thể cấu hình. |   2    |   D/V   |
| 8.2.4 | Xác minh rằng hiệu quả làm sạch dữ liệu (ví dụ, độ nhạy trong việc ẩn thông tin cá nhân nhận dạng được - PII, sự sai lệch ngữ nghĩa) được kiểm tra ít nhất hai lần một năm dựa trên các bộ dữ liệu chuẩn.                                  |   2    |    V    |
| 8.2.5 | Xác minh rằng các cấu hình xử lý dữ liệu đầu vào được kiểm soát phiên bản và mọi thay đổi đều được đồng nghiệp xem xét.                                                                                                                    |   3    |   D/V   |

---

## C8.3 Hết hạn bộ nhớ, Thu hồi & Xóa dữ liệu

Quyền "được quên" theo GDPR và các luật tương tự yêu cầu việc xóa bỏ kịp thời; do đó, kho vectơ phải hỗ trợ TTL, xóa cứng và ghi dấu "tomb-stoning" để các vectơ bị thu hồi không thể được khôi phục hoặc lập chỉ mục lại.

|   #   | Mô tả                                                                                                                                                             | Cấp độ | Vai trò |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 8.3.1 | Xác minh rằng mỗi vector và bản ghi siêu dữ liệu đều có TTL hoặc nhãn giữ liệu rõ ràng được tôn trọng bởi các công việc dọn dẹp tự động.                          |   1    |   D/V   |
| 8.3.2 | Xác minh rằng các yêu cầu xóa do người dùng khởi xướng sẽ xóa hoàn toàn các vector, siêu dữ liệu, bản sao bộ nhớ đệm và các chỉ mục phái sinh trong vòng 30 ngày. |   1    |   D/V   |
| 8.3.3 | Xác minh rằng việc xóa logic được theo sau bởi việc phá hủy dữ liệu mã hóa các khối lưu trữ nếu phần cứng hỗ trợ, hoặc bằng cách hủy khóa trong kho khóa.         |   2    |    D    |
| 8.3.4 | Xác minh rằng các vector hết hạn được loại trừ khỏi kết quả tìm kiếm láng giềng gần nhất trong vòng < 500 ms sau khi hết hạn.                                     |   3    |   D/V   |

---

## C8.4 Ngăn ngừa Đảo ngược và Rò rỉ Embedding

Các biện pháp phòng thủ gần đây—chồng nhiễu, mạng chiếu, làm nhiễu neuron bảo mật và mã hóa tầng ứng dụng—có thể giảm tỷ lệ đảo ngược ở cấp token xuống dưới 5%.

|   #   | Mô tả                                                                                                                                                         | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 8.4.1 | Xác minh rằng một mô hình mối đe dọa chính thức bao gồm các cuộc tấn công đảo ngược, thành viên và suy luận thuộc tính tồn tại và được xem xét hàng năm.      |   1    |    V    |
| 8.4.2 | Xác nhận rằng mã hóa tầng ứng dụng hoặc mã hóa có thể tìm kiếm bảo vệ các vector khỏi việc bị đọc trực tiếp bởi quản trị viên hạ tầng hoặc nhân viên đám mây. |   2    |   D/V   |
| 8.4.3 | Xác minh rằng các tham số phòng thủ (ε cho DP, nhiễu σ, hạng chiếu k) cân bằng giữa quyền riêng tư ≥ 99% bảo vệ token và tiện ích ≤ 3% mất độ chính xác.      |   3    |    V    |
| 8.4.4 | Xác nhận rằng các chỉ số kháng đảo chiều là một phần của các cửa kiểm soát phát hành cho các bản cập nhật mô hình, với các ngân sách hồi quy được xác định.   |   3    |   D/V   |

---

## C8.5 Thực thi phạm vi cho bộ nhớ dành cho người dùng cụ thể

Rò rỉ giữa các khách thuê vẫn là rủi ro hàng đầu của RAG: các truy vấn tương đồng được lọc không đúng cách có thể làm lộ tài liệu riêng tư của khách hàng khác.

|   #   | Mô tả                                                                                                                                                               | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 8.5.1 | Xác minh rằng mọi truy vấn truy xuất đều được lọc sau bởi ID thuê bao/người dùng trước khi được chuyển đến lệnh nhắc của LLM.                                       |   1    |   D/V   |
| 8.5.2 | Xác minh rằng tên bộ sưu tập hoặc ID có phạm vi tên được muối theo từng người dùng hoặc thuê bao để các vector không thể trùng nhau giữa các phạm vi.               |   1    |    D    |
| 8.5.3 | Xác minh rằng các kết quả tương đồng vượt quá ngưỡng khoảng cách có thể cấu hình nhưng nằm ngoài phạm vi của người gọi sẽ bị loại bỏ và kích hoạt cảnh báo bảo mật. |   2    |   D/V   |
| 8.5.4 | Xác minh rằng các bài kiểm tra căng thẳng đa thuê simulates các truy vấn đối nghịch cố gắng truy xuất tài liệu ngoài phạm vi và chứng minh không rò rỉ dữ liệu.     |   2    |    V    |
| 8.5.5 | Xác minh rằng các khóa mã hóa được phân tách theo từng người thuê, đảm bảo sự cô lập mật mã ngay cả khi lưu trữ vật lý được chia sẻ.                                |   3    |   D/V   |

---

## C8.6 Bảo mật Hệ thống Bộ nhớ Nâng cao

Các biện pháp kiểm soát bảo mật cho các kiến trúc bộ nhớ phức tạp bao gồm bộ nhớ theo tập sự kiện (episodic), bộ nhớ ngữ nghĩa (semantic) và bộ nhớ làm việc (working memory) với các yêu cầu cụ thể về phân lập và xác thực.

|   #   | Mô tả                                                                                                                                                                                                                                                                                | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 8.6.1 | Xác minh rằng các loại bộ nhớ khác nhau (bộ nhớ theo tập, bộ nhớ ngữ nghĩa, bộ nhớ làm việc) có các ngữ cảnh bảo mật tách biệt với kiểm soát truy cập dựa trên vai trò, khóa mã hóa riêng biệt và các mẫu truy cập được tài liệu hóa cho từng loại bộ nhớ.                           |   1    |   D/V   |
| 8.6.2 | Xác minh rằng các quy trình củng cố bộ nhớ bao gồm xác thực bảo mật để ngăn chặn việc chèn các ký ức độc hại thông qua việc làm sạch nội dung, xác minh nguồn và kiểm tra tính toàn vẹn trước khi lưu trữ.                                                                           |   2    |   D/V   |
| 8.6.3 | Xác minh rằng các truy vấn truy xuất bộ nhớ được xác thực và làm sạch để ngăn chặn việc trích xuất thông tin không được phép thông qua phân tích mẫu truy vấn, thực thi kiểm soát truy cập và lọc kết quả.                                                                           |   2    |   D/V   |
| 8.6.4 | Xác minh rằng các cơ chế quên bộ nhớ xoá bỏ thông tin nhạy cảm một cách an toàn với các đảm bảo xoá dữ liệu mật mã bằng cách xóa khóa, ghi đè nhiều lần hoặc xoá an toàn dựa trên phần cứng kèm theo chứng nhận xác minh.                                                            |   3    |   D/V   |
| 8.6.5 | Xác minh rằng tính toàn vẹn của hệ thống bộ nhớ được giám sát liên tục để phát hiện các thay đổi trái phép hoặc hỏng hóc thông qua các tổng kiểm tra (checksum), nhật ký kiểm tra (audit logs) và cảnh báo tự động khi nội dung bộ nhớ thay đổi ngoài phạm vi hoạt động bình thường. |   3    |   D/V   |

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

