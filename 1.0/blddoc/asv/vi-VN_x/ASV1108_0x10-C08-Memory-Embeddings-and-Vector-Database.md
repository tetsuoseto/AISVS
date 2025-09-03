# C8 Memory, các vector nhúng và bảo mật cơ sở dữ liệu vector

## Mục tiêu kiểm soát

Nhúng (embeddings) và các kho vector đóng vai trò như 'bộ nhớ thời gian thực' của các hệ thống AI hiện đại, liên tục tiếp nhận dữ liệu do người dùng cung cấp và đưa nó trở lại vào ngữ cảnh của mô hình thông qua Retrieval-Augmented Generation (RAG). Nếu để xảy ra mà không được quản trị, bộ nhớ này có thể rò rỉ PII, vi phạm sự đồng ý của người dùng, hoặc bị đảo ngược để tái tạo văn bản gốc. Mục tiêu của họ kiểm soát này là gia cố các đường ống bộ nhớ và cơ sở dữ liệu vector để truy cập theo nguyên tắc tối thiểu quyền, nhúng được bảo vệ quyền riêng tư, các vector được lưu trữ hết hạn hoặc có thể bị thu hồi theo yêu cầu, và bộ nhớ dành cho từng người dùng không bao giờ làm nhiễm bẩn các prompts hoặc completions của người dùng khác.

---

## C8.1 Kiểm soát truy cập đối với bộ nhớ và chỉ số RAG

Áp dụng kiểm soát truy cập chi tiết cho mọi bộ sưu tập vector.

|   #   | Mô tả                                                                                                                                                                     | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 8.1.1 | Xác minh rằng các quy tắc kiểm soát truy cập ở cấp hàng/namespace giới hạn các thao tác chèn, xóa và truy vấn theo người thuê, bộ sưu tập hoặc nhãn tài liệu.             |   1    |   D/V   |
| 8.1.2 | Xác minh rằng khóa API hoặc JWT mang các khai báo có phạm vi (ví dụ: IDs của bộ sưu tập, các động từ hành động) và được đổi khóa ít nhất mỗi quý.                         |   1    |   D/V   |
| 8.1.3 | Xác minh rằng các nỗ lực leo thang đặc quyền (ví dụ: các truy vấn tương tự giữa các không gian tên) được phát hiện và ghi nhật ký vào SIEM trong vòng 5 phút.             |   2    |   D/V   |
| 8.1.4 | Xác nhận rằng nhật ký kiểm toán vector DB ghi nhận định danh chủ thể, hoạt động, ID vector/không gian tên, ngưỡng tương đồng và số lượng kết quả.                         |   2    |   D/V   |
| 8.1.5 | Xác minh rằng các quyết định truy cập được kiểm tra để phát hiện lỗ hổng bỏ qua quyền truy cập mỗi khi động cơ được nâng cấp hoặc các quy tắc phân mảnh chỉ mục thay đổi. |   3    |    V    |

---

## C8.2 Làm sạch nhúng và xác thực

Tiền sàng lọc văn bản để phát hiện PII, xóa bỏ hoặc ẩn danh trước khi vector hóa, và tùy chọn xử lý sau nhúng để loại bỏ tín hiệu dư thừa.

|   #   | Mô tả                                                                                                                                                                                                                                                 | Cấp độ | Vai trò |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 8.2.1 | Xác minh rằng PII và dữ liệu được quản lý theo quy định được phát hiện thông qua các bộ phân loại tự động và được ẩn, token hóa, hoặc bị loại bỏ trước khi nhúng (pre-embedding).                                                                     |   1    |   D/V   |
| 8.2.2 | Xác minh rằng các pipeline nhúng từ chối hoặc cách ly các đầu vào chứa mã có thể thực thi hoặc các đối tượng không phải UTF-8 có thể làm ô nhiễm chỉ mục.                                                                                             |   1    |    D    |
| 8.2.3 | Xác minh rằng việc làm sạch bằng riêng tư vi phân cục bộ hoặc riêng tư vi phân theo metric được áp dụng cho các nhúng câu có khoảng cách tới bất kỳ token chứa thông tin nhận dạng cá nhân (PII) nào đã được biết nhỏ hơn một ngưỡng có thể cấu hình. |   2    |   D/V   |
| 8.2.4 | Xác nhận hiệu quả làm sạch dữ liệu (ví dụ: độ thu hồi khi che PII, dịch ngữ nghĩa) được xác thực ít nhất hai lần mỗi năm so với các tập dữ liệu tham chiếu.                                                                                           |   2    |    V    |
| 8.2.5 | Xác minh rằng các cấu hình làm sạch dữ liệu được kiểm soát phiên bản và các thay đổi được thẩm định bởi đồng nghiệp.                                                                                                                                  |   3    |   D/V   |

---

## C8.3 Hết hạn bộ nhớ, Thu hồi và Xóa

GDPR "quyền được xóa dữ liệu" và các luật tương tự yêu cầu xóa kịp thời; do đó các kho lưu trữ vector phải hỗ trợ TTL (thời gian sống của dữ liệu), xóa cứng và tomb-stoning để các vector bị thu hồi không thể được phục hồi hoặc tái lập chỉ mục.

|   #   | Mô tả                                                                                                                                                      | Cấp độ | Vai trò |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 8.3.1 | Xác minh rằng mọi vector và bản ghi siêu dữ liệu đều có TTL hoặc nhãn lưu giữ rõ ràng được các tác vụ dọn dẹp tự động tuân thủ.                            |   1    |   D/V   |
| 8.3.2 | Xác nhận rằng các yêu cầu xóa do người dùng khởi xướng sẽ xóa sạch các vector, siêu dữ liệu, bản sao đệm và các chỉ mục dẫn xuất trong vòng 30 ngày.       |   1    |   D/V   |
| 8.3.3 | Xác nhận rằng xóa mềm được theo sau bởi việc xóa dữ liệu bằng mã hóa trên các khối lưu trữ nếu phần cứng hỗ trợ, hoặc bởi sự phá hủy khóa trong Key Vault. |   2    |    D    |
| 8.3.4 | Xác nhận rằng các vector đã hết hạn được loại khỏi kết quả tìm kiếm hàng xóm gần nhất trong vòng dưới 500 ms kể từ khi hết hạn.                            |   3    |   D/V   |

---

## C8.4 Ngăn ngừa đảo ngược nhúng và rò rỉ

Những biện pháp bảo vệ gần đây—chồng nhiễu, mạng chiếu, biến đổi nơ-ron bảo mật riêng tư, và mã hóa ở lớp ứng dụng—có thể làm giảm tỉ lệ đảo ngược theo token xuống dưới 5%.

|   #   | Mô tả                                                                                                                                                                                                                         | Cấp độ | Vai trò |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 8.4.1 | Xác nhận rằng có một mô hình mối đe dọa chính thức bao gồm các tấn công đảo ngược mô hình, tấn công suy luận xem mẫu có thuộc tập huấn luyện hay không và tấn công suy luận thuộc tính, và mô hình này được xem xét hàng năm. |   1    |    V    |
| 8.4.2 | Xác nhận rằng mã hóa ở lớp ứng dụng hoặc mã hóa có thể tìm kiếm bảo vệ các vectơ khỏi đọc trực tiếp bởi các quản trị viên hạ tầng hoặc nhân viên đám mây.                                                                     |   2    |   D/V   |
| 8.4.3 | Xác nhận rằng các tham số phòng thủ (ε cho DP, nhiễu σ, hạng chiếu là k) cân bằng giữa quyền riêng tư ≥ 99 % và bảo vệ token, đồng thời độ hữu ích ≤ 3 % mất độ chính xác.                                                    |   3    |    V    |
| 8.4.4 | Xác nhận rằng các chỉ số kháng đảo ngược là một phần của cổng phát hành cho cập nhật mô hình, với ngân sách hồi quy được xác định.                                                                                            |   3    |   D/V   |

---

## C8.5 Thực thi phạm vi cho bộ nhớ dành riêng cho người dùng

Rò rỉ giữa các tenant vẫn là một rủi ro hàng đầu của RAG: các truy vấn tương đồng được lọc không đúng có thể phơi bày tài liệu riêng tư của khách hàng khác.

|   #   | Mô tả                                                                                                                                                                           | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 8.5.1 | Xác minh rằng mọi truy vấn truy xuất dữ liệu đều được lọc sau theo ID người thuê hoặc người dùng trước khi được đưa vào prompt của Mô hình ngôn ngữ lớn (LLM).                  |   1    |   D/V   |
| 8.5.2 | Xác minh rằng tên bộ sưu tập hoặc ID có không gian tên được muối hóa theo từng người dùng hoặc khách thuê để các vector không thể va chạm giữa các phạm vi.                     |   1    |    D    |
| 8.5.3 | Xác minh rằng các kết quả độ tương đồng vượt quá ngưỡng khoảng cách có thể cấu hình được nhưng nằm ngoài phạm vi của người gọi sẽ bị loại bỏ và kích hoạt các cảnh báo bảo mật. |   2    |   D/V   |
| 8.5.4 | Xác nhận rằng các bài kiểm tra căng thẳng đa thuê mô phỏng các truy vấn ác ý nhằm truy xuất tài liệu ngoài phạm vi và cho thấy không có rò rỉ.                                  |   2    |    V    |
| 8.5.5 | Xác nhận rằng khóa mã hóa được phân tách theo từng khách thuê, nhằm đảm bảo sự cô lập về mặt mã hóa ngay cả khi lưu trữ vật lý được chia sẻ.                                    |   3    |   D/V   |

---

## C8.6 Bảo mật hệ thống bộ nhớ nâng cao

Các biện pháp kiểm soát bảo mật cho các kiến trúc bộ nhớ tinh vi, bao gồm trí nhớ theo sự kiện (episodic), trí nhớ ngữ nghĩa (semantic), và trí nhớ làm việc (working memory) với các yêu cầu cô lập và xác thực cụ thể.

|   #   | Mô tả                                                                                                                                                                                                                                                    | Cấp độ | Vai trò |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 8.6.1 | Xác minh rằng các loại bộ nhớ khác nhau có các ngữ cảnh bảo mật được cô lập với kiểm soát truy cập dựa trên vai trò (RBAC), khóa mã hóa riêng biệt, và các mẫu truy cập được ghi nhận cho mỗi loại bộ nhớ.                                               |   1    |   D/V   |
| 8.6.2 | Xác nhận rằng các quá trình củng cố bộ nhớ bao gồm xác thực bảo mật nhằm ngăn chặn việc tiêm ký ức độc hại thông qua làm sạch nội dung, xác thực nguồn và kiểm tra tính toàn vẹn trước khi lưu trữ.                                                      |   2    |   D/V   |
| 8.6.3 | Xác minh rằng các truy vấn truy xuất bộ nhớ được xác thực và làm sạch nhằm ngăn chặn việc trích xuất thông tin trái phép thông qua phân tích mẫu truy vấn, thực thi kiểm soát truy cập và lọc kết quả.                                                   |   2    |   D/V   |
| 8.6.4 | Xác nhận rằng các cơ chế xóa dữ liệu khỏi bộ nhớ đảm bảo xóa an toàn thông tin nhạy cảm bằng các phương pháp xóa bằng mã hóa, xóa khóa, ghi đè nhiều lần, hoặc xóa an toàn dựa trên phần cứng kèm chứng nhận xác thực.                                   |   3    |   D/V   |
| 8.6.5 | Xác minh rằng tính toàn vẹn của hệ thống bộ nhớ được giám sát liên tục để phát hiện các sửa đổi trái phép hoặc hư hỏng thông qua chuỗi kiểm tra, nhật ký kiểm toán và cảnh báo tự động khi nội dung bộ nhớ thay đổi ngoài phạm vi hoạt động bình thường. |   3    |   D/V   |

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

