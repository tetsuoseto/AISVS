# C5 Kiểm soát truy cập và danh tính cho các thành phần AI và người dùng

## Mục tiêu kiểm soát

Việc thiết lập kiểm soát truy cập hiệu quả cho các hệ thống AI đòi hỏi quản lý danh tính mạnh mẽ, ủy quyền nhận thức ngữ cảnh và thực thi tại thời điểm chạy theo nguyên tắc zero-trust. Các biện pháp này đảm bảo rằng con người, dịch vụ và các tác nhân tự động chỉ tương tác với mô hình, dữ liệu và tài nguyên tính toán trong phạm vi được cấp phép rõ ràng, với khả năng xác minh và kiểm toán liên tục.

---

## C5.1 Quản lý danh tính và Xác thực

Thiết lập danh tính dựa trên mật mã cho mọi thực thể và áp dụng xác thực đa yếu tố cho các thao tác đặc quyền.

|   #   | Mô tả                                                                                                                                                                                                                                                              | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 5.1.1 | Xác minh rằng tất cả người dùng và đối tượng dịch vụ xác thực thông qua một nhà cung cấp danh tính doanh nghiệp tập trung (IdP) bằng các giao thức OIDC/SAML với các ánh xạ danh tính sang token duy nhất (không có tài khoản hoặc thông tin xác thực dùng chung). |   1    |   D/V   |
| 5.1.2 | Xác nhận rằng các thao tác rủi ro cao (triển khai mô hình, xuất trọng số, truy cập dữ liệu huấn luyện, thay đổi cấu hình sản xuất) yêu cầu xác thực nhiều yếu tố hoặc xác thực cấp cao hơn với xác thực lại phiên làm việc.                                        |   1    |   D/V   |
| 5.1.3 | Đảm bảo rằng các đối tượng nhận diện mới trải qua quá trình xác minh danh tính phù hợp với NIST 800-63-3 IAL-2 hoặc các tiêu chuẩn tương đương trước khi được cấp quyền truy cập hệ thống sản xuất.                                                                |   2    |    D    |
| 5.1.4 | Xác nhận rằng các đánh giá quyền truy cập được thực hiện mỗi quý với việc phát hiện tự động các tài khoản không hoạt động, thực thi việc thay đổi thông tin xác thực theo chu kỳ, và quy trình thu hồi quyền truy cập.                                             |   2    |    V    |
| 5.1.5 | Xác minh rằng các tác nhân AI liên kết xác thực thông qua các khẳng định JWT được ký có thời hạn tối đa 24 giờ và bao gồm bằng chứng nguồn gốc bằng mật mã.                                                                                                        |   3    |   D/V   |

---

## C5.2 Phân quyền tài nguyên & Nguyên tắc tối thiểu

Triển khai kiểm soát truy cập chi tiết cho tất cả các tài nguyên AI với các mô hình cấp phép rõ ràng và nhật ký kiểm toán.

|   #   | Mô tả                                                                                                                                                                                                                                                | Cấp độ | Vai trò |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 5.2.1 | Xác minh rằng mọi nguồn tài nguyên AI (tập dữ liệu, mô hình, điểm cuối API, bộ sưu tập vectơ, chỉ mục nhúng, các instance tính toán) đều thực thi kiểm soát truy cập dựa trên vai trò với danh sách cho phép rõ ràng và chính sách từ chối mặc định. |   1    |   D/V   |
| 5.2.2 | Xác nhận rằng nguyên tắc tối thiểu đặc quyền được thực thi mặc định với các tài khoản dịch vụ bắt đầu từ quyền read-only và yêu cầu lý do kinh doanh được ghi nhận cho quyền ghi.                                                                    |   1    |   D/V   |
| 5.2.3 | Xác minh rằng mọi sửa đổi kiểm soát truy cập đều được liên kết với các yêu cầu thay đổi đã được phê duyệt và được ghi lại một cách bất biến với các dấu thời gian, danh tính tác nhân, định danh tài nguyên và sự thay đổi quyền.                    |   1    |    V    |
| 5.2.4 | Xác nhận rằng các nhãn phân loại dữ liệu (PII, PHI, export-controlled, proprietary) tự động lan truyền đến các tài nguyên phát sinh (các nhúng, bộ đệm prompt, đầu ra của mô hình) với việc thực thi chính sách nhất quán.                           |   2    |    D    |
| 5.2.5 | Xác nhận rằng các lần cố gắng truy cập trái phép và các sự kiện leo thang đặc quyền sẽ kích hoạt cảnh báo thời gian thực kèm siêu dữ liệu ngữ cảnh gửi tới các hệ thống SIEM trong vòng 5 phút.                                                      |   2    |   D/V   |

---

## C5.3 Đánh giá Chính sách Động

Triển khai các động cơ ABAC (kiểm soát truy cập dựa trên thuộc tính) để đưa ra các quyết định cấp quyền dựa trên ngữ cảnh, đồng thời có khả năng kiểm toán.

|   #   | Mô tả                                                                                                                                                                                                                                | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 5.3.1 | Xác nhận các quyết định ủy quyền được đưa ra ngoài sang một động cơ chính sách riêng biệt (OPA, Cedar hoặc tương đương), có thể truy cập thông qua các API được xác thực và được bảo toàn tính toàn vẹn bằng các biện pháp mã hóa.   |   1    |   D/V   |
| 5.3.2 | Xác minh rằng các chính sách đánh giá các thuộc tính động tại thời gian chạy, bao gồm mức độ cấp phép của người dùng, phân loại độ nhạy của tài nguyên, ngữ cảnh của yêu cầu, sự cách ly giữa các tenant và các ràng buộc thời gian. |   1    |   D/V   |
| 5.3.3 | Xác minh rằng các định nghĩa chính sách được kiểm soát phiên bản, được thẩm định bởi các đồng nghiệp, và được xác thực thông qua kiểm thử tự động trong các pipeline CI/CD trước khi triển khai lên môi trường sản xuất.             |   2    |    D    |
| 5.3.4 | Xác nhận rằng kết quả đánh giá chính sách bao gồm các lý do quyết định có cấu trúc và được truyền đến các hệ thống SIEM để phân tích tương quan và báo cáo tuân thủ.                                                                 |   2    |    V    |
| 5.3.5 | Xác nhận rằng giá trị TTL của bộ nhớ đệm chính sách không vượt quá 5 phút đối với các tài nguyên có độ nhạy cao và 1 giờ đối với các tài nguyên chuẩn có khả năng làm mất hiệu lực bộ nhớ đệm.                                       |   3    |   D/V   |

---

## C5.4 Thực thi bảo mật tại thời điểm truy vấn

Triển khai các biện pháp kiểm soát bảo mật ở lớp cơ sở dữ liệu với lọc bắt buộc và row-level security policies.

|   #   | Mô tả                                                                                                                                                                                                                                | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 5.4.1 | Xác minh rằng tất cả các truy vấn tới cơ sở dữ liệu vectơ và SQL đều có các bộ lọc bảo mật bắt buộc (ID khách thuê, nhãn độ nhạy, phạm vi người dùng) được thực thi tại cấp động cơ của cơ sở dữ liệu, chứ không phải ở mã ứng dụng. |   1    |   D/V   |
| 5.4.2 | Xác minh rằng các chính sách bảo mật theo hàng (RLS) và ẩn theo trường được bật với kế thừa chính sách cho tất cả các cơ sở dữ liệu vector, các chỉ mục tìm kiếm và các tập dữ liệu huấn luyện.                                      |   1    |   D/V   |
| 5.4.3 | Xác minh rằng các đánh giá ủy quyền thất bại sẽ ngăn chặn các cuộc tấn công 'confused deputy' bằng cách ngay lập tức hủy bỏ truy vấn và trả về các mã lỗi ủy quyền rõ ràng thay vì trả về các tập kết quả rỗng.                      |   2    |    D    |
| 5.4.4 | Xác nhận rằng độ trễ trong quá trình đánh giá chính sách được giám sát liên tục với các cảnh báo tự động cho các điều kiện hết thời gian có thể cho phép bỏ qua phân quyền.                                                          |   2    |    V    |
| 5.4.5 | Xác nhận rằng các cơ chế thử lại truy vấn sẽ tái đánh giá các chính sách ủy quyền nhằm phản ánh các thay đổi quyền theo thời gian thực trong các phiên người dùng đang hoạt động.                                                    |   3    |   D/V   |

---

## C5.5 Lọc đầu ra & Phòng ngừa mất dữ liệu

Triển khai các biện pháp hậu xử lý để ngăn ngừa rò rỉ dữ liệu trái phép trong nội dung do AI tạo ra.

|   #   | Mô tả                                                                                                                                                                                                               | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 5.5.1 | Xác minh rằng các cơ chế lọc sau suy luận sẽ quét và che khuất PII trái phép, thông tin được phân loại và dữ liệu sở hữu trước khi cung cấp nội dung cho người yêu cầu.                                             |   1    |   D/V   |
| 5.5.2 | Xác minh rằng các trích dẫn, tham khảo và nguồn được gắn trong đầu ra của mô hình đã được xác thực với quyền truy cập được cấp cho người gọi và bị loại bỏ nếu phát hiện truy cập trái phép.                        |   1    |   D/V   |
| 5.5.3 | Xác minh rằng các giới hạn về định dạng đầu ra (PDF được làm sạch, hình ảnh đã loại bỏ siêu dữ liệu, các định dạng tệp được phê duyệt) được thực thi dựa trên mức độ cấp quyền của người dùng và phân loại dữ liệu. |   2    |    D    |
| 5.5.4 | Xác minh rằng các thuật toán tẩy xóa có tính xác định, được kiểm soát phiên bản, và duy trì nhật ký kiểm toán để hỗ trợ các cuộc điều tra tuân thủ và phân tích pháp y.                                             |   2    |    V    |
| 5.5.5 | Xác minh rằng các sự kiện ẩn nội dung có rủi ro cao tạo ra các nhật ký thích ứng chứa các giá trị băm mã hóa của nội dung gốc để phục vụ cho điều tra pháp y mà không để lộ dữ liệu.                                |   3    |    V    |

---

## C5.6 Cách ly đa người thuê

Đảm bảo sự cô lập dựa trên mã hóa và logic giữa các khách thuê trong hạ tầng AI dùng chung.

|   #   | Mô tả                                                                                                                                                                                                                     | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 5.6.1 | Xác minh rằng các không gian nhớ, kho lưu trữ nhúng, các mục trong bộ nhớ đệm và tệp tin tạm được phân tách theo không gian tên cho từng khách thuê với việc xóa an toàn khi xóa khách thuê hoặc kết thúc phiên làm việc. |   1    |   D/V   |
| 5.6.2 | Xác nhận mọi yêu cầu API đều chứa một định danh khách thuê được xác thực, và định danh này được xác thực bằng mã hóa so với ngữ cảnh phiên và quyền được cấp cho người dùng.                                              |   1    |   D/V   |
| 5.6.3 | Xác nhận rằng các chính sách mạng triển khai quy tắc từ chối mặc định cho giao tiếp chéo giữa các khách thuê trong service mesh và nền tảng điều phối container.                                                          |   2    |    D    |
| 5.6.4 | Xác minh rằng khóa mã hóa là duy nhất cho từng khách thuê, với hỗ trợ khóa do khách hàng quản lý (CMK) và sự cô lập bằng mật mã giữa các kho dữ liệu của khách thuê.                                                      |   3    |    D    |

---

## C5.7 Ủy quyền cho tác nhân tự trị

Kiểm soát quyền truy cập của các tác nhân AI và hệ thống tự động thông qua các token khả năng có phạm vi được giới hạn và ủy quyền liên tục.

|   #   | Mô tả                                                                                                                                                                                                                                 | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 5.7.1 | Xác minh rằng các tác nhân tự trị nhận được các token quyền năng có phạm vi, trong đó liệt kê rõ ràng các hành động được phép, các tài nguyên có thể truy cập, ranh giới thời gian và các giới hạn vận hành.                          |   1    |   D/V   |
| 5.7.2 | Đảm bảo rằng các khả năng có rủi ro cao (truy cập hệ thống tập tin, thực thi mã, gọi API bên ngoài, giao dịch tài chính) bị vô hiệu hóa theo mặc định và chỉ được kích hoạt khi có sự cho phép rõ ràng kèm theo các lý do kinh doanh. |   1    |   D/V   |
| 5.7.3 | Xác nhận rằng các token cấp quyền được gắn với các phiên người dùng, bao gồm bảo vệ tính toàn vẹn bằng mật mã, và đảm bảo chúng không thể được lưu trữ hoặc tái sử dụng trong các trường hợp ngoại tuyến.                             |   2    |    D    |
| 5.7.4 | Xác minh rằng các hành động do tác nhân khởi tạo trải qua ủy quyền cấp thứ cấp thông qua máy xử lý chính sách ABAC, với đánh giá ngữ cảnh đầy đủ và ghi nhật ký kiểm toán.                                                            |   2    |    V    |
| 5.7.5 | Xác minh rằng các điều kiện lỗi của tác nhân và xử lý ngoại lệ bao gồm thông tin phạm vi năng lực để hỗ trợ phân tích sự cố và điều tra pháp y.                                                                                       |   3    |    V    |

---

## Tài liệu tham khảo

### Tiêu chuẩn và Khung

* [NIST SP 800-63-3: Digital Identity Guidelines](https://pages.nist.gov/800-63-3/)
* [Zero Trust Architecture – NIST SP 800-207](https://nvlpubs.nist.gov/nistpubs/specialpublications/NIST.SP.800-207.pdf)
* [OWASP Application Security Verification Standard (AISVS)](https://owasp.org/www-project-application-security-verification-standard/)
  ​
### Hướng dẫn triển khai

* [Identity and Access Management in the AI Era: 2025 Guide – IDSA](https://www.idsalliance.org/blog/identity-and-access-management-in-the-ai-era-2025-guide/)
* [Attribute-Based Access Control with OPA – Permify](https://medium.com/permify-tech-blog/attribute-based-access-control-abac-implementation-with-open-policy-agent-opa-b47052248f29)
* [How We Designed Cedar to Be Intuitive, Fast, and Safe – AWS](https://aws.amazon.com/blogs/security/how-we-designed-cedar-to-be-intuitive-to-use-fast-and-safe/)
  ​
### Bảo mật dành riêng cho AI

* [Row Level Security in Vector DBs for RAG – Bluetuple.ai](https://medium.com/bluetuple-ai/implementing-row-level-security-in-vector-dbs-for-rag-applications-fdbccb63d464)
* [Tenant Isolation in Multi-Tenant Systems – WorkOS](https://workos.com/blog/tenant-isolation-in-multi-tenant-systems)
* [Handling AI Agent Permissions – Stytch](https://stytch.com/blog/handling-ai-agent-permissions/)
* [OWASP Top 10 for Large Language Model Applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/)

