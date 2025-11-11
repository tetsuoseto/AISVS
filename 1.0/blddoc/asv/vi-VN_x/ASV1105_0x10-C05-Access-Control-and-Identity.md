# Kiểm soát truy cập C5 & Định danh cho các thành phần và người dùng AI

## Mục tiêu Kiểm soát

Kiểm soát truy cập hiệu quả cho các hệ thống AI yêu cầu quản lý danh tính vững chắc, ủy quyền dựa trên bối cảnh, và thực thi khi chạy theo các nguyên tắc không tin cậy. Các kiểm soát này đảm bảo rằng con người, dịch vụ và tác nhân tự động chỉ tương tác với các mô hình, dữ liệu và tài nguyên tính toán trong phạm vi đã được cấp phép rõ ràng, với khả năng xác minh và kiểm tra liên tục.

---

## C5.1 Quản lý Danh tính & Xác thực

Thiết lập danh tính được hỗ trợ mật mã cho tất cả các thực thể với xác thực đa yếu tố.

|   #   | Mô tả                                                                                                                                                                                                                       | Cấp độ | Vai trò |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 5.1.1 | Xác minh rằng tất cả người dùng là con người và các nguyên tắc dịch vụ xác thực thông qua một nhà cung cấp danh tính doanh nghiệp tập trung (IdP) sử dụng các giao thức OIDC và/hoặc SAML.                                  |   1    |   D/V   |
| 5.1.2 | Xác minh rằng các hoạt động có rủi ro cao (triển khai mô hình, xuất trọng số, truy cập dữ liệu đào tạo, thay đổi cấu hình sản xuất) yêu cầu xác thực đa yếu tố hoặc xác thực nâng cao kèm theo tái xác nhận phiên làm việc. |   1    |   D/V   |
| 5.1.3 | Xác minh rằng các tác nhân AI liên kết xác thực thông qua các khẳng định JWT được ký có thời gian sống tối đa là 24 giờ và bao gồm bằng chứng mật mã về nguồn gốc.                                                          |   3    |   D/V   |

---

## C5.2 Ủy quyền & Chính sách

Triển khai kiểm soát truy cập cho tất cả nguồn lực AI với các mô hình phân quyền rõ ràng và nhật ký kiểm tra.

|   #   | Mô tả                                                                                                                                                                                                                                      | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 5.2.1 | Xác minh rằng mọi tài nguyên AI (bộ dữ liệu, mô hình, điểm cuối, bộ sưu tập vector, chỉ mục nhúng, phiên bản tính toán) đều thực thi kiểm soát truy cập dựa trên vai trò với danh sách cho phép rõ ràng và chính sách mặc định là từ chối. |   1    |   D/V   |
| 5.2.2 | Xác minh rằng tất cả các sửa đổi kiểm soát truy cập đều được ghi lại vĩnh viễn với dấu thời gian, danh tính người thực hiện, định danh tài nguyên và các thay đổi quyền hạn.                                                               |   1    |    V    |
| 5.2.3 | Xác minh rằng nhãn phân loại dữ liệu (PII, PHI, thuộc quyền sở hữu, v.v.) tự động lan truyền đến các tài nguyên dẫn xuất (embedding, bộ nhớ đệm prompt, đầu ra mô hình).                                                                   |   2    |    D    |
| 5.2.4 | Xác minh rằng các cố gắng truy cập trái phép và các sự kiện leo thang quyền hạn kích hoạt cảnh báo thời gian thực kèm theo siêu dữ liệu ngữ cảnh.                                                                                          |   2    |   D/V   |
| 5.2.5 | Xác minh rằng các quyết định ủy quyền được tách ra bên ngoài thành một cơ chế chính sách chuyên dụng (OPA, Cedar hoặc tương đương).                                                                                                        |   1    |   D/V   |
| 5.2.6 | Xác minh rằng các chính sách đánh giá các thuộc tính động tại thời gian chạy bao gồm vai trò hoặc nhóm người dùng, phân loại tài nguyên, ngữ cảnh yêu cầu, cô lập người thuê và các hạn chế về thời gian.                                  |   1    |   D/V   |
| 5.2.7 | Xác minh rằng giá trị thời gian tồn tại trong bộ nhớ đệm chính sách (TTL) không vượt quá 5 phút đối với tài nguyên có độ nhạy cao và 1 giờ đối với tài nguyên tiêu chuẩn có khả năng hủy bộ nhớ đệm.                                       |   3    |   D/V   |

---

## C5.3 Thực thi Bảo mật vào Thời gian Truy vấn

Thực hiện các biện pháp kiểm soát bảo mật tầng cơ sở dữ liệu với lọc bắt buộc và chính sách bảo mật cấp hàng.

|   #   | Mô tả                                                                                                                                                                                          | Cấp độ | Vai trò |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 5.3.1 | Xác minh rằng tất cả các truy vấn cơ sở dữ liệu vector và SQL bao gồm các bộ lọc bảo mật bắt buộc (ID người thuê, nhãn độ nhạy, phạm vi người dùng) được thực thi ở cấp động cơ cơ sở dữ liệu. |   1    |   D/V   |
| 5.3.2 | Xác minh rằng các chính sách bảo mật cấp dòng và che mặt trường được bật với kế thừa chính sách cho tất cả cơ sở dữ liệu vector, chỉ mục tìm kiếm và bộ dữ liệu huấn luyện.                    |   1    |   D/V   |
| 5.3.3 | Xác minh rằng các đánh giá ủy quyền không thành công sẽ ngay lập tức hủy bỏ các truy vấn và trả về mã lỗi ủy quyền rõ ràng.                                                                    |   2    |    D    |
| 5.3.4 | Xác minh rằng các cơ chế thử lại truy vấn đánh giá lại các chính sách ủy quyền để tính đến các thay đổi quyền động trong các phiên người dùng đang hoạt động.                                  |   3    |   D/V   |

---

## C5.4 Lọc Đầu Ra & Ngăn Ngừa Mất Dữ Liệu

Triển khai các biện pháp kiểm soát hậu xử lý để ngăn chặn việc tiết lộ dữ liệu trái phép trong nội dung do AI tạo ra.

|   #   | Mô tả                                                                                                                                                                                                  | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 5.4.1 | Xác minh rằng các cơ chế lọc sau suy luận quét và chỉnh sửa các thông tin nhận dạng cá nhân (PII), thông tin phân loại và dữ liệu sở hữu không được phép trước khi chuyển nội dung đến người yêu cầu.  |   1    |   D/V   |
| 5.4.2 | Xác minh rằng các trích dẫn, tài liệu tham khảo và nguồn gốc trong kết quả mô hình được kiểm tra dựa trên quyền truy cập của người gọi và loại bỏ nếu phát hiện truy cập không được phép.              |   1    |   D/V   |
| 5.4.3 | Xác minh rằng các hạn chế định dạng đầu ra (PDF đã được làm sạch, hình ảnh đã được loại bỏ siêu dữ liệu, loại tệp được phê duyệt) được thực thi dựa trên cấp độ quyền người dùng và phân loại dữ liệu. |   2    |    D    |

---

## C5.5 Cách ly đa thuê bao

Đảm bảo sự cô lập về mật mã và logic giữa các khách thuê trong hạ tầng AI dùng chung.

|   #   | Mô tả                                                                                                                                                                                                             | Cấp độ | Vai trò |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 5.5.1 | Xác minh rằng các không gian bộ nhớ, kho nhúng, mục lưu trong bộ nhớ đệm và tệp tạm thời được phân tách theo không gian tên cho từng khách thuê với việc xóa sạch an toàn khi xóa khách thuê hoặc kết thúc phiên. |   1    |   D/V   |
| 5.5.2 | Xác minh rằng mỗi yêu cầu API bao gồm một định danh thuê bao đã được xác thực và được xác minh bằng mật mã dựa trên ngữ cảnh phiên và quyền hạn của người dùng.                                                   |   1    |   D/V   |
| 5.5.3 | Xác minh rằng các chính sách mạng thực thi các quy tắc từ chối mặc định đối với giao tiếp giữa các tenant trong các service mesh và nền tảng điều phối container.                                                 |   2    |    D    |
| 5.5.4 | Xác minh rằng các khóa mã hóa là duy nhất cho từng thuê bao với hỗ trợ khóa do khách hàng quản lý (CMK) và sự cô lập mật mã giữa các kho dữ liệu của thuê bao.                                                    |   3    |    D    |

---

## C5.6 Ủy quyền Đại lý Tự động

Kiểm soát quyền hạn cho các đại lý AI và hệ thống tự động thông qua token khả năng theo phạm vi và ủy quyền liên tục.

|   #   | Mô tả                                                                                                                                                                                                              | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 5.6.1 | Xác nhận rằng các tác nhân tự động nhận được token khả năng có phạm vi, trong đó liệt kê rõ ràng các hành động được phép thực hiện, các tài nguyên có thể truy cập, giới hạn thời gian và các ràng buộc hoạt động. |   1    |   D/V   |
| 5.6.2 | Xác minh rằng các khả năng rủi ro cao (truy cập hệ thống tệp, thực thi mã, gọi API bên ngoài, giao dịch tài chính) bị vô hiệu hóa theo mặc định và cần có sự cho phép rõ ràng.                                     |   1    |   D/V   |
| 5.6.3 | Xác minh rằng các token khả năng được liên kết với phiên người dùng, bao gồm bảo vệ tính toàn vẹn bằng mật mã, và đảm bảo rằng chúng không thể được lưu trữ hoặc sử dụng lại trong các tình huống ngoại tuyến.     |   2    |    D    |
| 5.6.4 | Xác minh rằng các hành động do tác nhân khởi tạo được trải qua việc ủy quyền thông qua bộ máy chính sách ABAC.                                                                                                     |   2    |    V    |

---

## Tài liệu tham khảo

* [NIST SP 800-162: Guide to Attribute Based Access Control (ABAC)](https://csrc.nist.gov/pubs/sp/800/162/final)
* [NIST SP 800-207: Zero Trust Architecture](https://csrc.nist.gov/pubs/sp/800/207/final)
* [NIST SP 800-63-3: Digital Identity Guidelines](https://csrc.nist.gov/pubs/sp/800/63/3/final)
* [NIST IR 8360: Machine Learning for Access Control Policy Verification](https://csrc.nist.gov/pubs/ir/8360/final)

