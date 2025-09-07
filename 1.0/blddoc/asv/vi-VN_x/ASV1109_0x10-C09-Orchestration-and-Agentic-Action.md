# 9 An ninh Điều phối Tự động và Hành động Chủ động

## Mục tiêu Kiểm soát

Đảm bảo rằng các hệ thống AI tự động hoặc đa tác nhân chỉ có thể thực hiện các hành động được dự định rõ ràng, xác thực, có thể kiểm toán và nằm trong ngưỡng chi phí và rủi ro giới hạn. Điều này giúp bảo vệ chống lại các mối đe dọa như Xâm phạm Hệ thống Tự động, Lạm dụng Công cụ, Phát hiện Vòng Lặp Tác nhân, Chiếm Đoạt Giao tiếp, Giả mạo Danh tính, Điều khiển Đàn và Thao túng Ý định.

---

## 9.1 Ngân sách Lập kế hoạch Tác vụ và Đệ quy của Tác nhân

Hạn chế các kế hoạch đệ quy và bắt buộc có điểm kiểm tra của con người cho các hành động đặc quyền.

|   #   | Mô tả                                                                                                                                                                                                        | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 9.1.1 | Xác minh rằng độ sâu đệ quy tối đa, độ rộng, thời gian đồng hồ thực, số lượng token và chi phí tiền tệ cho mỗi lần thực thi tác nhân được cấu hình tập trung và kiểm soát phiên bản.                         |   1    |   D/V   |
| 9.1.2 | Xác minh rằng các hành động đặc quyền hoặc không thể hoàn tác (ví dụ: cam kết mã, chuyển khoản tài chính) yêu cầu sự phê duyệt rõ ràng của con người thông qua một kênh có thể kiểm tra trước khi thực hiện. |   1    |   D/V   |
| 9.1.3 | Xác minh rằng các bộ giám sát tài nguyên theo thời gian thực kích hoạt ngắt mạch khi bất kỳ ngưỡng ngân sách nào bị vượt quá, dừng việc mở rộng tác vụ tiếp theo.                                            |   2    |    D    |
| 9.1.4 | Xác minh rằng các sự kiện ngắt mạch được ghi lại với ID đại lý, điều kiện kích hoạt và trạng thái kế hoạch được ghi nhận để xem xét pháp y.                                                                  |   2    |   D/V   |
| 9.1.5 | Xác minh rằng các bài kiểm tra bảo mật bao phủ các kịch bản cạn kiệt ngân sách và kế hoạch chạy ngoài kiểm soát, đảm bảo dừng an toàn mà không mất dữ liệu.                                                  |   3    |    V    |
| 9.1.6 | Xác nhận rằng các chính sách ngân sách được biểu thị dưới dạng chính sách dưới dạng mã và được thực thi trong CI/CD để ngăn chặn sự trôi cấu hình.                                                           |   3    |    D    |

---

## 9.2 Cách ly Plugin Công cụ

Cô lập các tương tác công cụ để ngăn chặn truy cập hệ thống hoặc thực thi mã trái phép.

|   #   | Mô tả                                                                                                                                                                                               | Cấp độ | Vai trò |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 9.2.1 | Xác minh rằng mọi công cụ/plugin đều thực thi bên trong một hệ điều hành, container hoặc sandbox cấp độ WASM với các chính sách hệ thống tập tin, mạng và gọi hệ thống ưu tiên quyền hạn thấp nhất. |   1    |   D/V   |
| 9.2.2 | Xác minh rằng các hạn mức tài nguyên sandbox (CPU, bộ nhớ, đĩa, băng thông mạng ra) và thời gian chạy tối đa được thực thi và ghi lại nhật ký.                                                      |   1    |   D/V   |
| 9.2.3 | Xác minh rằng các tệp nhị phân hoặc mô tả công cụ được ký số; chữ ký được xác thực trước khi tải.                                                                                                   |   2    |   D/V   |
| 9.2.4 | Xác minh rằng luồng dữ liệu chuẩn đoán của sandbox được gửi đến hệ thống SIEM; các bất thường (ví dụ, các kết nối outbound bị cố gắng thực hiện) sẽ kích hoạt cảnh báo.                             |   2    |    V    |
| 9.2.5 | Xác minh rằng các plugin có rủi ro cao được kiểm tra bảo mật và thử nghiệm thâm nhập trước khi triển khai vào môi trường sản xuất.                                                                  |   3    |    V    |
| 9.2.6 | Xác minh rằng các nỗ lực thoát khỏi sandbox được tự động chặn và plugin vi phạm bị cách ly chờ điều tra.                                                                                            |   3    |   D/V   |

---

## 9.3 Vòng Lặp Tự Động và Giới Hạn Chi Phí

Phát hiện và ngăn chặn việc đệ quy không kiểm soát giữa các đại lý và sự bùng nổ chi phí.

|   #   | Mô tả                                                                                                                                    | Cấp độ | Vai trò |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 9.3.1 | Xác minh rằng các cuộc gọi giữa các đại lý bao gồm một giới hạn bước nhảy hoặc TTL mà môi trường thời gian chạy sẽ giảm dần và thực thi. |   1    |   D/V   |
| 9.3.2 | Xác nhận rằng các đại lý duy trì một ID biểu đồ gọi độc nhất để phát hiện việc tự gọi hoặc các mẫu tuần hoàn.                            |   2    |    D    |
| 9.3.3 | Xác minh rằng các bộ đếm đơn vị tính toán tích lũy và chi tiêu được theo dõi theo chuỗi yêu cầu; việc vượt giới hạn sẽ hủy bỏ chuỗi.     |   2    |   D/V   |
| 9.3.4 | Xác minh rằng phân tích hình thức hoặc kiểm tra mô hình chứng minh sự vắng mặt của đệ quy vô hạn trong các giao thức đại lý.             |   3    |    V    |
| 9.3.5 | Xác minh rằng các sự kiện hủy vòng lặp tạo ra cảnh báo và cung cấp các chỉ số cải tiến liên tục.                                         |   3    |    D    |

---

## 9.4 Bảo vệ chống lạm dụng cấp giao thức

Kênh giao tiếp bảo mật giữa các đại lý và hệ thống bên ngoài để ngăn chặn việc chiếm quyền hoặc thao túng.

|   #   | Mô tả                                                                                                                                                      | Cấp độ | Vai trò |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 9.4.1 | Xác minh rằng tất cả các tin nhắn từ đại lý đến công cụ và từ đại lý đến đại lý đều được xác thực (ví dụ: TLS hai chiều hoặc JWT) và được mã hóa đầu cuối. |   1    |   D/V   |
| 9.4.2 | Xác minh rằng các sơ đồ được xác thực nghiêm ngặt; các trường không xác định hoặc các thông điệp bị sai định dạng sẽ bị từ chối.                           |   1    |    D    |
| 9.4.3 | Xác minh rằng các kiểm tra tính toàn vẹn (MAC hoặc chữ ký số) bao phủ toàn bộ phần dữ liệu thông điệp bao gồm cả các tham số công cụ.                      |   2    |   D/V   |
| 9.4.4 | Xác minh rằng tính năng bảo vệ chống phát lại (nonce hoặc cửa sổ dấu thời gian) được thực thi tại tầng giao thức.                                          |   2    |    D    |
| 9.4.5 | Xác minh rằng các triển khai giao thức được thực hiện fuzzing và phân tích tĩnh để phát hiện các lỗi tiêm nhiễm hoặc phân giải tuần tự.                    |   3    |    V    |

---

## 9.5 Danh tính Đại lý & Bằng chứng chống giả mạo

Đảm bảo các hành động có thể truy xuất được và các sửa đổi có thể phát hiện được.

|   #   | Mô tả                                                                                                                                | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 9.5.1 | Xác minh rằng mỗi thực thể tác nhân sở hữu một danh tính mật mã duy nhất (cặp khóa hoặc chứng chỉ gốc phần cứng).                    |   1    |   D/V   |
| 9.5.2 | Xác minh rằng tất cả các hành động của đại lý đều được ký và đóng dấu thời gian; nhật ký bao gồm chữ ký để đảm bảo không thể bác bỏ. |   2    |   D/V   |
| 9.5.3 | Xác minh rằng các nhật ký có khả năng phát hiện giả mạo được lưu trữ trên một phương tiện chỉ cho phép ghi thêm hoặc ghi một lần.    |   2    |    V    |
| 9.5.4 | Xác minh rằng các khóa nhận dạng được xoay vòng theo lịch trình đã định và khi có chỉ báo bị xâm phạm.                               |   3    |    D    |
| 9.5.5 | Xác minh rằng các nỗ lực mạo danh hoặc xung đột khóa kích hoạt ngay lập tức việc cách ly đại lý bị ảnh hưởng.                        |   3    |   D/V   |

---

## 9.6 Giảm Thiểu Rủi Ro Đàn Động Vật Đa Tác Nhân

Giảm thiểu các rủi ro về hành vi tập thể thông qua cách ly và mô hình hóa an toàn chính thức.

|   #   | Mô tả                                                                                                                                                           | Cấp độ | Vai trò |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 9.6.1 | Xác minh rằng các tác nhân hoạt động trong các miền bảo mật khác nhau được thực thi trong các vùng cát thời gian chạy tách biệt hoặc phân đoạn mạng riêng biệt. |   1    |   D/V   |
| 9.6.2 | Xác minh rằng các hành vi đàn bầy được mô phỏng và xác thực chính thức về tính sống động và an toàn trước khi triển khai.                                       |   3    |    V    |
| 9.6.3 | Xác minh rằng các bộ giám sát thời gian chạy phát hiện các mẫu không an toàn phát sinh (ví dụ, dao động, tình trạng chết) và khởi xướng hành động khắc phục.    |   3    |    D    |

---

## 9.7 Xác thực / Ủy quyền Người dùng & Công cụ

Thực hiện kiểm soát truy cập mạnh mẽ cho mọi hành động do tác nhân kích hoạt.

|   #   | Mô tả                                                                                                                                                           | Cấp độ | Vai trò |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 9.7.1 | Xác minh rằng các tác nhân xác thực như các chủ thể hạng nhất đối với các hệ thống hạ nguồn, không bao giờ tái sử dụng thông tin đăng nhập của người dùng cuối. |   1    |   D/V   |
| 9.7.2 | Xác minh rằng các chính sách ủy quyền chi tiết giới hạn công cụ mà đại lý có thể gọi và các tham số mà nó có thể cung cấp.                                      |   2    |    D    |
| 9.7.3 | Xác minh rằng các kiểm tra đặc quyền được đánh giá lại trên mỗi lần gọi (ủy quyền liên tục), không chỉ vào lúc bắt đầu phiên.                                   |   2    |    V    |
| 9.7.4 | Xác minh rằng quyền hạn được ủy quyền sẽ tự động hết hạn và yêu cầu đồng ý lại sau khi hết thời gian hoặc thay đổi phạm vi.                                     |   3    |    D    |

---

## 9.8 Bảo mật giao tiếp giữa các đại lý

Mã hóa và bảo vệ toàn vẹn tất cả các thông điệp giữa các tác nhân để ngăn chặn nghe lén và giả mạo.

|   #   | Mô tả                                                                                                                                                            | Cấp độ | Vai trò |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 9.8.1 | Xác minh rằng xác thực lẫn nhau và mã hóa bí mật tiến tới hoàn hảo (ví dụ: TLS 1.3) là bắt buộc đối với các kênh đại lý.                                         |   1    |   D/V   |
| 9.8.2 | Xác minh rằng tính toàn vẹn và nguồn gốc của thông điệp được xác nhận trước khi xử lý; nếu thất bại sẽ phát cảnh báo và từ chối thông điệp.                      |   1    |    D    |
| 9.8.3 | Xác minh rằng siêu dữ liệu truyền thông (dấu thời gian, số thứ tự) được ghi lại để hỗ trợ tái tạo pháp y.                                                        |   2    |   D/V   |
| 9.8.4 | Xác minh rằng việc xác thực hình thức hoặc kiểm tra mô hình xác nhận rằng các máy trạng thái giao thức không thể bị điều khiển vào các trạng thái không an toàn. |   3    |    V    |

---

## 9.9 Xác minh Ý định & Thực thi Ràng buộc

Xác nhận rằng các hành động của đại lý phù hợp với ý định đã nêu của người dùng và các giới hạn của hệ thống.

|   #   | Mô tả                                                                                                                                                                                                           | Cấp độ | Vai trò |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 9.9.1 | Xác minh rằng các bộ giải ràng buộc trước thực thi kiểm tra các hành động được đề xuất so với các quy tắc an toàn và chính sách được mã hóa cứng.                                                               |   1    |    D    |
| 9.9.2 | Xác minh rằng các hành động có tác động cao (tài chính, phá hoại, nhạy cảm về quyền riêng tư) yêu cầu xác nhận ý định rõ ràng từ người dùng khởi tạo.                                                           |   2    |   D/V   |
| 9.9.3 | Xác minh rằng các kiểm tra hậu điều kiện xác nhận các hành động hoàn thành đã đạt được hiệu quả dự định mà không có tác dụng phụ; các sai lệch sẽ kích hoạt việc phục hồi trạng thái.                           |   2    |    V    |
| 9.9.4 | Xác minh rằng các phương pháp hình thức (ví dụ, kiểm tra mô hình, chứng minh định lý) hoặc các bài kiểm tra dựa trên thuộc tính chứng minh rằng kế hoạch của tác nhân đáp ứng tất cả các ràng buộc đã khai báo. |   3    |    V    |
| 9.9.5 | Xác minh rằng các sự cố không khớp ý định hoặc vi phạm ràng buộc được đưa vào các chu trình cải tiến liên tục và chia sẻ thông tin tình báo về mối đe dọa.                                                      |   3    |    D    |

---

## 9.10 Chiến lược lý luận của tác nhân - An ninh

Lựa chọn và thực thi an toàn các chiến lược suy luận khác nhau bao gồm các phương pháp ReAct, Chuỗi-suy nghĩ (Chain-of-Thought), và Cây-suy nghĩ (Tree-of-Thoughts).

|   #    | Mô tả                                                                                                                                                                                                                                           | Cấp độ | Vai trò |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 9.10.1 | Xác minh rằng việc lựa chọn chiến lược suy luận sử dụng các tiêu chí quyết định (độ phức tạp đầu vào, loại nhiệm vụ, bối cảnh bảo mật) và các đầu vào giống hệt nhau tạo ra các lựa chọn chiến lược giống nhau trong cùng một bối cảnh bảo mật. |   1    |   D/V   |
| 9.10.2 | Xác minh rằng mỗi chiến lược lý luận (ReAct, Chain-of-Thought, Tree-of-Thoughts) đều có kiểm tra đầu vào riêng, làm sạch đầu ra và giới hạn thời gian thực thi phù hợp với phương pháp nhận thức của nó.                                        |   1    |   D/V   |
| 9.10.3 | Xác nhận rằng các chuyển đổi chiến lược lập luận được ghi lại với bối cảnh đầy đủ bao gồm các đặc điểm đầu vào, giá trị tiêu chí lựa chọn và siêu dữ liệu thực thi để tái tạo dấu vết kiểm toán.                                                |   2    |   D/V   |
| 9.10.4 | Xác nhận rằng phương pháp suy luận Cây Ý tưởng bao gồm các cơ chế cắt tỉa nhánh nhằm kết thúc việc khám phá khi phát hiện vi phạm chính sách, giới hạn tài nguyên hoặc ranh giới an toàn.                                                       |   2    |   D/V   |
| 9.10.5 | Xác minh rằng các chu kỳ ReAct (Reason-Act-Observe) bao gồm các điểm kiểm tra xác thực ở mỗi giai đoạn: kiểm tra bước suy luận, ủy quyền hành động và làm sạch quan sát trước khi tiếp tục.                                                     |   2    |   D/V   |
| 9.10.6 | Xác minh rằng các chỉ số hiệu suất của chiến lược lý luận (thời gian thực thi, sử dụng tài nguyên, chất lượng đầu ra) được theo dõi với các cảnh báo tự động khi các chỉ số vượt quá ngưỡng được cấu hình.                                      |   3    |   D/V   |
| 9.10.7 | Xác minh rằng các phương pháp lý luận kết hợp đa chiến lược duy trì việc xác thực đầu vào và các ràng buộc đầu ra của tất cả các chiến lược thành phần mà không bỏ qua bất kỳ kiểm soát bảo mật nào.                                            |   3    |   D/V   |
| 9.10.8 | Xác minh rằng kiểm thử bảo mật chiến lược suy luận bao gồm kiểm thử fuzzing với các đầu vào bị làm sai lệch, các lời nhắc đối kháng được thiết kế để buộc chuyển đổi chiến lược, và kiểm thử điều kiện biên cho từng phương pháp nhận thức.     |   3    |   D/V   |

---

## 9.11 Quản lý trạng thái vòng đời đại lý & An ninh

Khởi tạo đại lý an toàn, chuyển đổi trạng thái và kết thúc với các dấu vết kiểm toán mật mã và quy trình phục hồi đã được xác định.

|   #    | Mô tả                                                                                                                                                                                                                                                                       | Cấp độ | Vai trò |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 9.11.1 | Xác minh rằng việc khởi tạo đại lý bao gồm thiết lập danh tính mật mã với chứng chỉ hỗ trợ phần cứng và nhật ký kiểm tra khởi động bất biến chứa ID đại lý, dấu thời gian, hàm băm cấu hình và các tham số khởi tạo.                                                        |   1    |   D/V   |
| 9.11.2 | Xác minh rằng các chuyển trạng thái của đại lý được ký bằng mật mã, có dấu thời gian và được ghi lại với bối cảnh đầy đủ bao gồm các sự kiện kích hoạt, băm trạng thái trước đó, băm trạng thái mới và các kiểm tra an ninh đã thực hiện.                                   |   2    |   D/V   |
| 9.11.3 | Xác minh rằng các quy trình tắt tác nhân bao gồm việc xóa bộ nhớ an toàn bằng phương pháp xóa mật mã hoặc ghi đè nhiều lần, thu hồi thông tin xác thực kèm theo thông báo đến cơ quan cấp chứng chỉ, và tạo ra các chứng chỉ kết thúc có khả năng phát hiện việc can thiệp. |   2    |   D/V   |
| 9.11.4 | Xác minh rằng các cơ chế phục hồi tác nhân kiểm tra tính toàn vẹn của trạng thái bằng các bảng kiểm tra mật mã (ít nhất SHA-256) và quay lại trạng thái được biết là tốt khi phát hiện sự cố hỏng với các cảnh báo tự động và yêu cầu phê duyệt thủ công.                   |   3    |   D/V   |
| 9.11.5 | Xác minh rằng các cơ chế duy trì trạng thái của agent mã hóa dữ liệu trạng thái nhạy cảm bằng khóa AES-256 riêng cho từng agent và thực hiện xoay khóa an toàn theo lịch cấu hình được (tối đa 90 ngày) với triển khai không gián đoạn.                                     |   3    |   D/V   |

---

## 9.12 Khung Bảo Mật Tích Hợp Công Cụ

Các biện pháp kiểm soát bảo mật cho việc tải công cụ động, thực thi và xác nhận kết quả với các quy trình đánh giá rủi ro và phê duyệt được xác định rõ.

|   #    | Mô tả                                                                                                                                                                                                                                                                | Cấp độ | Vai trò |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 9.12.1 | Xác minh rằng các mô tả công cụ bao gồm siêu dữ liệu bảo mật chỉ rõ các quyền cần thiết (đọc/ghi/thực thi), mức độ rủi ro (thấp/trung bình/cao), giới hạn tài nguyên (CPU, bộ nhớ, mạng), và các yêu cầu xác thực được ghi chép trong bản mô tả công cụ.             |   1    |   D/V   |
| 9.12.2 | Xác minh rằng kết quả thực thi công cụ được kiểm tra đối chiếu với các sơ đồ dự kiến (JSON Schema, XML Schema) và các chính sách bảo mật (làm sạch đầu ra, phân loại dữ liệu) trước khi tích hợp, đồng thời áp dụng giới hạn thời gian chờ và các thủ tục xử lý lỗi. |   1    |   D/V   |
| 9.12.3 | Xác minh rằng nhật ký tương tác công cụ bao gồm bối cảnh bảo mật chi tiết bao gồm việc sử dụng đặc quyền, mô hình truy cập dữ liệu, thời gian thực thi, tiêu thụ tài nguyên, và mã trả về với việc ghi nhật ký có cấu trúc để tích hợp SIEM.                         |   2    |   D/V   |
| 9.12.4 | Xác minh rằng các cơ chế tải công cụ động xác thực các chữ ký số sử dụng hạ tầng PKI và triển khai các giao thức tải an toàn với cách ly sandbox và xác minh quyền trước khi thực thi.                                                                               |   2    |   D/V   |
| 9.12.5 | Xác minh rằng các đánh giá bảo mật công cụ được kích hoạt tự động cho các phiên bản mới với các cổng phê duyệt bắt buộc bao gồm phân tích tĩnh, kiểm thử động và xem xét bởi nhóm bảo mật với các tiêu chí phê duyệt đã được ghi chép và yêu cầu SLA.                |   3    |   D/V   |

---

### Tài liệu tham khảo

* [MITRE ATLAS tactics ML09](https://atlas.mitre.org/)
* [Circuit-breaker research for AI agents — Zou et al., 2024](https://arxiv.org/abs/2406.04313)
* [Trend Micro analysis of sandbox escapes in AI agents — Park, 2025](https://www.trendmicro.com/vinfo/us/security/news/cybercrime-and-digital-threats/unveiling-ai-agent-vulnerabilities-code-execution)
* [Auth0 guidance on human-in-the-loop authorization for agents — Martinez, 2025](https://auth0.com/blog/secure-human-in-the-loop-interactions-for-ai-agents/)
* [Medium deep-dive on MCP & A2A protocol hijacking — ForAISec, 2025](https://medium.com/%40foraisec/security-analysis-potential-ai-agent-hijacking-via-mcp-and-a2a-protocol-insights-cd1ec5e6045f)
* [Rapid7 fundamentals on spoofing attack prevention — 2024](https://www.rapid7.com/fundamentals/spoofing-attacks/)
* [Imperial College verification of swarm systems — Lomuscio et al.](https://sail.doc.ic.ac.uk/projects/swarms/)
* [NIST AI Risk Management Framework 1.0, 2023](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [WIRED security briefing on encryption best practices, 2024](https://www.wired.com/story/encryption-apps-chinese-telecom-hacking-hydra-russia-exxon)
* [OWASP Top 10 for LLM Applications, 2025](https://owasp.org/www-project-top-10-for-large-language-model-applications/)
* [Comprehensive Vulnerability Analysis is Necessary for Trustworthy LLM-MAS](https://arxiv.org/html/2506.01245v1)
* [How Is LLM Reasoning Distracted by Irrelevant Context?
  An Analysis Using a Controlled Benchmark](https://www.arxiv.org/pdf/2505.18761)
* [Large Language Model Sentinel: LLM Agent for Adversarial Purification](https://arxiv.org/pdf/2405.20770)
* [Securing Agentic AI: A Comprehensive Threat Model and Mitigation Framework for Generative AI Agents](https://arxiv.org/html/2504.19956v2)

