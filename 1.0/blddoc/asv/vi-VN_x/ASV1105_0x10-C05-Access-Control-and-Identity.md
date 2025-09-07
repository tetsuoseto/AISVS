# Kiểm soát truy cập C5 & Danh tính cho các Thành phần & Người dùng AI

## Mục tiêu Kiểm soát

Kiểm soát truy cập hiệu quả cho các hệ thống AI đòi hỏi quản lý nhận dạng vững chắc, ủy quyền nhận biết ngữ cảnh và thực thi trong thời gian chạy theo các nguyên tắc không tin cậy. Các biện pháp kiểm soát này đảm bảo rằng con người, dịch vụ và tác nhân tự động chỉ tương tác với các mô hình, dữ liệu và tài nguyên tính toán trong phạm vi được cấp phép rõ ràng, kèm theo khả năng xác minh và kiểm tra liên tục.

---

## C5.1 Quản lý danh tính & Xác thực

Thiết lập danh tính được bảo mật bằng mật mã cho tất cả các thực thể với xác thực đa yếu tố cho các thao tác đặc quyền.

|   #   | Mô tả                                                                                                                                                                                                                                                                                        | Cấp độ | Vai trò |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 5.1.1 | Xác minh rằng tất cả người dùng là con người và các nguyên tắc dịch vụ đều xác thực thông qua một nhà cung cấp nhận dạng doanh nghiệp tập trung (IdP) sử dụng các giao thức OIDC/SAML với các ánh xạ định danh tới token duy nhất (không sử dụng tài khoản hoặc thông tin xác thực chia sẻ). |   1    |   D/V   |
| 5.1.2 | Xác nhận rằng các hoạt động có rủi ro cao (triển khai mô hình, xuất trọng số, truy cập dữ liệu đào tạo, thay đổi cấu hình sản xuất) yêu cầu xác thực đa yếu tố hoặc xác thực nâng cao với xác thực lại phiên làm việc.                                                                       |   1    |   D/V   |
| 5.1.3 | Xác minh rằng các giám đốc mới trải qua quá trình chứng thực danh tính phù hợp với NIST 800-63-3 IAL-2 hoặc các tiêu chuẩn tương đương trước khi được cấp quyền truy cập vào hệ thống sản xuất.                                                                                              |   2    |    D    |
| 5.1.4 | Xác minh rằng các đánh giá truy cập được thực hiện hàng quý với việc phát hiện tự động các tài khoản không hoạt động, thực thi việc xoay vòng thông tin xác thực, và các quy trình gỡ bỏ quyền truy cập.                                                                                     |   2    |    V    |
| 5.1.5 | Xác minh rằng các tác nhân AI liên kết xác thực thông qua các khẳng định JWT được ký có thời hạn tối đa là 24 giờ và bao gồm bằng chứng mật mã về nguồn gốc.                                                                                                                                 |   3    |   D/V   |

---

## C5.2 Ủy quyền Tài nguyên & Quyền tối thiểu

Triển khai các kiểm soát truy cập chi tiết cho tất cả tài nguyên AI với mô hình cấp phép rõ ràng và các đường dẫn kiểm toán.

|   #   | Mô tả                                                                                                                                                                                                                                                         | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 5.2.1 | Xác minh rằng mọi tài nguyên AI (bộ dữ liệu, mô hình, điểm cuối, bộ sưu tập vectơ, chỉ mục nhúng, phiên bản tính toán) đều thực thi kiểm soát truy cập dựa trên vai trò với danh sách cho phép rõ ràng và chính sách mặc định từ chối.                        |   1    |   D/V   |
| 5.2.2 | Xác minh rằng các nguyên tắc quyền hạn tối thiểu được thực thi theo mặc định với các tài khoản dịch vụ, bắt đầu với quyền chỉ đọc và yêu cầu có tài liệu lý do kinh doanh cho quyền ghi.                                                                      |   1    |   D/V   |
| 5.2.3 | Xác minh rằng tất cả các sửa đổi kiểm soát truy cập đều được liên kết với các yêu cầu thay đổi đã được phê duyệt và được ghi lại một cách không thể thay đổi với dấu thời gian, danh tính người thực hiện, định danh tài nguyên và sự khác biệt về quyền hạn. |   1    |    V    |
| 5.2.4 | Xác minh rằng nhãn phân loại dữ liệu (PII, PHI, kiểm soát xuất khẩu, sở hữu độc quyền) tự động lan truyền đến các tài nguyên dẫn xuất (embedding, bộ nhớ đệm prompt, kết quả mô hình) với việc thực thi chính sách nhất quán.                                 |   2    |    D    |
| 5.2.5 | Xác minh rằng các lần cố gắng truy cập trái phép và sự kiện leo thang đặc quyền kích hoạt cảnh báo thời gian thực với siêu dữ liệu ngữ cảnh gửi đến hệ thống SIEM trong vòng 5 phút.                                                                          |   2    |   D/V   |

---

## C5.3 Đánh giá Chính sách Động

Triển khai các bộ máy kiểm soát truy cập dựa trên thuộc tính (ABAC) để đưa ra quyết định ủy quyền nhận thức ngữ cảnh với khả năng kiểm tra.

|   #   | Mô tả                                                                                                                                                                                                                             | Cấp độ | Vai trò |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 5.3.1 | Xác minh rằng các quyết định ủy quyền được tách ra ngoài tới một công cụ chính sách chuyên dụng (OPA, Cedar, hoặc tương đương) có thể truy cập qua các API được xác thực với bảo vệ toàn vẹn bằng mật mã.                         |   1    |   D/V   |
| 5.3.2 | Xác minh rằng các chính sách đánh giá các thuộc tính động tại thời điểm chạy bao gồm mức độ rõ ràng của người dùng, phân loại độ nhạy cảm của tài nguyên, ngữ cảnh yêu cầu, sự cô lập của người thuê, và các ràng buộc thời gian. |   1    |   D/V   |
| 5.3.3 | Xác minh rằng các định nghĩa chính sách được kiểm soát phiên bản, được đồng nghiệp đánh giá và được xác thực thông qua kiểm thử tự động trong các pipeline CI/CD trước khi triển khai sản xuất.                                   |   2    |    D    |
| 5.3.4 | Xác minh rằng kết quả đánh giá chính sách bao gồm các lý do quyết định có cấu trúc và được truyền đến các hệ thống SIEM để phân tích tương quan và báo cáo tuân thủ.                                                              |   2    |    V    |
| 5.3.5 | Xác minh rằng giá trị thời gian tồn tại bộ nhớ đệm chính sách (TTL) không vượt quá 5 phút đối với các tài nguyên có độ nhạy cao và 1 giờ đối với các tài nguyên tiêu chuẩn có khả năng vô hiệu hóa bộ nhớ đệm.                    |   3    |   D/V   |

---

## C5.4 Thực thi An ninh khi Truy vấn

Triển khai các biện pháp kiểm soát bảo mật ở lớp cơ sở dữ liệu với việc lọc bắt buộc và các chính sách bảo mật cấp hàng.

|   #   | Mô tả                                                                                                                                                                                                                         | Cấp độ | Vai trò |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 5.4.1 | Xác minh rằng tất cả các truy vấn cơ sở dữ liệu vector và SQL đều bao gồm các bộ lọc bảo mật bắt buộc (ID khách thuê, nhãn độ nhạy, phạm vi người dùng) được thực thi ở cấp độ động cơ cơ sở dữ liệu, không phải mã ứng dụng. |   1    |   D/V   |
| 5.4.2 | Xác minh rằng các chính sách bảo mật cấp hàng (RLS) và che giấu cấp trường được bật với kế thừa chính sách cho tất cả các cơ sở dữ liệu vector, chỉ số tìm kiếm và tập dữ liệu đào tạo.                                       |   1    |   D/V   |
| 5.4.3 | Xác minh rằng các đánh giá ủy quyền không thành công sẽ ngăn chặn "các cuộc tấn công đại lý nhầm lẫn" bằng cách ngay lập tức hủy bỏ các truy vấn và trả về mã lỗi ủy quyền rõ ràng thay vì trả về các tập kết quả rỗng.       |   2    |    D    |
| 5.4.4 | Xác minh rằng độ trễ đánh giá chính sách được giám sát liên tục với các cảnh báo tự động về các điều kiện thời gian chờ có thể cho phép vượt qua ủy quyền.                                                                    |   2    |    V    |
| 5.4.5 | Xác minh rằng các cơ chế thử lại truy vấn đánh giá lại các chính sách cấp quyền để tính đến các thay đổi quyền động trong các phiên người dùng đang hoạt động.                                                                |   3    |   D/V   |

---

## Lọc Đầu Ra C5.5 & Ngăn Ngừa Mất Dữ Liệu

Triển khai các biện pháp kiểm soát xử lý hậu kỳ để ngăn chặn việc tiết lộ dữ liệu trái phép trong nội dung do AI tạo ra.

|   #   | Mô tả                                                                                                                                                                                                    | Cấp độ | Vai trò |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 5.5.1 | Xác minh rằng các cơ chế lọc sau suy luận quét và chỉnh sửa thông tin nhận dạng cá nhân (PII) không được phép, thông tin phân loại và dữ liệu độc quyền trước khi cung cấp nội dung cho người yêu cầu.   |   1    |   D/V   |
| 5.5.2 | Xác minh rằng các trích dẫn, tham khảo và ghi nguồn trong kết quả mô hình được xác thực dựa trên quyền truy cập của người gọi và loại bỏ nếu phát hiện truy cập không được phép.                         |   1    |   D/V   |
| 5.5.3 | Xác minh rằng các hạn chế về định dạng đầu ra (PDF đã được làm sạch, hình ảnh đã loại bỏ siêu dữ liệu, các loại tệp được phê duyệt) được thực thi dựa trên cấp độ quyền người dùng và phân loại dữ liệu. |   2    |    D    |
| 5.5.4 | Xác minh rằng các thuật toán che khuất thông tin có tính xác định, được kiểm soát phiên bản và duy trì nhật ký kiểm toán để hỗ trợ điều tra tuân thủ và phân tích pháp y.                                |   2    |    V    |
| 5.5.5 | Xác minh rằng các sự kiện biên tập rủi ro cao tạo ra nhật ký thích ứng bao gồm các hàm băm mật mã của nội dung gốc để truy xuất pháp y mà không làm lộ dữ liệu.                                          |   3    |    V    |

---

## C5.6 Cách ly đa người thuê

Đảm bảo sự cô lập về mật mã và logic giữa các khách thuê trong hạ tầng AI chia sẻ.

|   #   | Mô tả                                                                                                                                                                                                               | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 5.6.1 | Xác minh rằng không gian bộ nhớ, kho lưu trữ embedding, mục cache và tập tin tạm thời được phân tách theo không gian tên cho từng tenant, kèm theo việc xóa an toàn khi tenant bị xóa hoặc phiên làm việc kết thúc. |   1    |   D/V   |
| 5.6.2 | Xác minh rằng mọi yêu cầu API đều bao gồm một định danh người thuê đã được xác thực, được xác minh mật mã dựa trên ngữ cảnh phiên và quyền của người dùng.                                                          |   1    |   D/V   |
| 5.6.3 | Xác minh rằng các chính sách mạng triển khai các quy tắc từ chối-mặc định cho giao tiếp giữa các thuê bao trong các dịch vụ mạng lõi và các nền tảng điều phối container.                                           |   2    |    D    |
| 5.6.4 | Xác minh rằng các khóa mã hóa là duy nhất theo từng người thuê với hỗ trợ khóa do khách hàng quản lý (CMK) và sự cách ly mật mã giữa các kho dữ liệu người thuê.                                                    |   3    |    D    |

---

## C5.7 Ủy quyền Đại lý Tự động

Kiểm soát quyền hạn cho các tác nhân AI và hệ thống tự động thông qua token khả năng có phạm vi và cấp phép liên tục.

|   #   | Mô tả                                                                                                                                                                                                                               | Cấp độ | Vai trò |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 5.7.1 | Xác minh rằng các tác nhân tự động nhận được các token khả năng có phạm vi, trong đó liệt kê rõ ràng các hành động được phép, tài nguyên có thể truy cập, giới hạn thời gian và các ràng buộc vận hành.                             |   1    |   D/V   |
| 5.7.2 | Xác minh rằng các khả năng có rủi ro cao (truy cập hệ thống file, thực thi mã, gọi API bên ngoài, giao dịch tài chính) được vô hiệu hóa theo mặc định và yêu cầu sự cho phép rõ ràng để kích hoạt kèm theo lý do kinh doanh hợp lý. |   1    |   D/V   |
| 5.7.3 | Xác minh rằng các token khả năng được liên kết với các phiên người dùng, bao gồm bảo vệ tính toàn vẹn bằng mật mã, và đảm bảo rằng chúng không thể được lưu trữ hoặc tái sử dụng trong các tình huống ngoại tuyến.                  |   2    |    D    |
| 5.7.4 | Xác minh rằng các hành động do đại lý khởi xướng được thực hiện qua việc ủy quyền phụ thông qua bộ máy chính sách ABAC với đánh giá bối cảnh đầy đủ và ghi nhận kiểm toán.                                                          |   2    |    V    |
| 5.7.5 | Xác minh rằng các điều kiện lỗi của tác nhân và xử lý ngoại lệ bao gồm thông tin phạm vi khả năng để hỗ trợ phân tích sự cố và điều tra pháp y.                                                                                     |   3    |    V    |

---

## Tài liệu tham khảo

### Tiêu chuẩn & Khung làm việc

* [NIST SP 800-63-3: Digital Identity Guidelines](https://pages.nist.gov/800-63-3/)
* [Zero Trust Architecture – NIST SP 800-207](https://nvlpubs.nist.gov/nistpubs/specialpublications/NIST.SP.800-207.pdf)
* [OWASP Application Security Verification Standard (AISVS)](https://owasp.org/www-project-application-security-verification-standard/)
  ​
### Hướng dẫn triển khai

* [Identity and Access Management in the AI Era: 2025 Guide – IDSA](https://www.idsalliance.org/blog/identity-and-access-management-in-the-ai-era-2025-guide/)
* [Attribute-Based Access Control with OPA – Permify](https://medium.com/permify-tech-blog/attribute-based-access-control-abac-implementation-with-open-policy-agent-opa-b47052248f29)
* [How We Designed Cedar to Be Intuitive, Fast, and Safe – AWS](https://aws.amazon.com/blogs/security/how-we-designed-cedar-to-be-intuitive-to-use-fast-and-safe/)
  ​
### An ninh dành riêng cho AI

* [Row Level Security in Vector DBs for RAG – Bluetuple.ai](https://medium.com/bluetuple-ai/implementing-row-level-security-in-vector-dbs-for-rag-applications-fdbccb63d464)
* [Tenant Isolation in Multi-Tenant Systems – WorkOS](https://workos.com/blog/tenant-isolation-in-multi-tenant-systems)
* [Handling AI Agent Permissions – Stytch](https://stytch.com/blog/handling-ai-agent-permissions/)
* [OWASP Top 10 for Large Language Model Applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/)

