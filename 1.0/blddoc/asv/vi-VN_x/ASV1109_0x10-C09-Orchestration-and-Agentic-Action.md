# 9 Điều phối tự động và An ninh Hành động Tác nhân

## Mục tiêu Kiểm soát

Đảm bảo rằng các hệ thống AI tự động hoặc đa tác nhân chỉ có thể thực hiện các hành động được xác định rõ ràng, được xác thực, có thể kiểm tra và nằm trong giới hạn chi phí và rủi ro cho phép. Điều này giúp bảo vệ chống lại các mối đe dọa như Xâm phạm Hệ thống Tự động, Sử dụng Sai Công cụ, Phát hiện Vòng lặp Tác nhân, Chiếm quyền Giao tiếp, Giả mạo Danh tính, Điều khiển Đám đông và Điều khiển Ý định.

---

## 9.1 Ngân sách Lập kế hoạch Nhiệm vụ Đại lý & Đệ quy

Giảm tốc độ các kế hoạch đệ quy và bắt buộc điểm kiểm tra con người cho các hành động đặc quyền.

|   #   | Mô tả                                                                                                                                                                                                         | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 9.1.1 | Xác minh rằng độ sâu đệ quy tối đa, độ rộng, thời gian đồng hồ thực, số lượng token và chi phí tiền tệ cho mỗi lần thực thi tác tử được cấu hình tập trung và kiểm soát phiên bản.                            |   1    |   D/V   |
| 9.1.2 | Xác minh rằng các hành động đặc quyền hoặc không thể đảo ngược (ví dụ: cam kết mã, chuyển tiền tài chính) yêu cầu sự phê duyệt rõ ràng của con người thông qua một kênh có thể kiểm toán trước khi thực hiện. |   1    |   D/V   |
| 9.1.3 | Xác minh rằng các công cụ giám sát tài nguyên theo thời gian thực kích hoạt ngắt mạch ngắt khi bất kỳ ngưỡng ngân sách nào bị vượt quá, dừng việc mở rộng tác vụ tiếp theo.                                   |   2    |    D    |
| 9.1.4 | Xác minh rằng các sự kiện ngắt mạch được ghi lại với ID đại lý, điều kiện kích hoạt và trạng thái kế hoạch được ghi nhận để phục vụ xem xét pháp y.                                                           |   2    |   D/V   |
| 9.1.5 | Xác minh rằng các bài kiểm tra bảo mật bao phủ các kịch bản cạn kiệt ngân sách và kế hoạch chạy trốn, đảm bảo dừng an toàn mà không mất dữ liệu.                                                              |   3    |    V    |
| 9.1.6 | Xác nhận rằng các chính sách ngân sách được thể hiện dưới dạng mã chính sách và được thực thi trong CI/CD để ngăn chặn sự sai lệch cấu hình.                                                                  |   3    |    D    |

---

## 9.2 Vùng cát Plugin Công cụ

Cô lập các tương tác công cụ để ngăn chặn truy cập hệ thống hoặc thực thi mã không được phép.

|   #   | Mô tả                                                                                                                                                                            | Cấp độ | Vai trò |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 9.2.1 | Xác minh rằng mỗi công cụ/plugin chạy bên trong hệ điều hành, container hoặc sandbox ở cấp độ WASM với các chính sách quyền hạn thấp nhất về hệ thống tệp, mạng và gọi hệ thống. |   1    |   D/V   |
| 9.2.2 | Xác minh rằng các hạn ngạch tài nguyên sandbox (CPU, bộ nhớ, đĩa, xuất mạng) và thời gian chờ thực thi được thực thi và ghi log.                                                 |   1    |   D/V   |
| 9.2.3 | Xác minh rằng các nhị phân công cụ hoặc mô tả được ký kỹ thuật số; các chữ ký được xác thực trước khi tải.                                                                       |   2    |   D/V   |
| 9.2.4 | Xác minh rằng dữ liệu đo lường từ sandbox được truyền đến SIEM; các bất thường (ví dụ: các kết nối ra ngoài bị cố gắng thực hiện) sẽ kích hoạt cảnh báo.                         |   2    |    V    |
| 9.2.5 | Xác minh rằng các plugin có nguy cơ cao được kiểm tra bảo mật và thử nghiệm xâm nhập trước khi triển khai ra môi trường sản xuất.                                                |   3    |    V    |
| 9.2.6 | Xác minh rằng các nỗ lực thoát khỏi sandbox được tự động chặn và plugin vi phạm bị cách ly chờ điều tra.                                                                         |   3    |   D/V   |

---

## 9.3 Vòng lập trình Tự động & Giới hạn Chi phí

Phát hiện và ngăn chặn đệ quy không kiểm soát giữa các tác nhân và sự bùng nổ chi phí.

|   #   | Mô tả                                                                                                                                | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 9.3.1 | Xác minh rằng các cuộc gọi giữa các tác nhân bao gồm giới hạn số lần chuyển tiếp hoặc TTL mà runtime sẽ giảm và thực thi.            |   1    |   D/V   |
| 9.3.2 | Xác minh rằng các tác nhân duy trì một ID đồ thị gọi độc nhất để phát hiện sự tự gọi hoặc các mẫu tuần hoàn.                         |   2    |    D    |
| 9.3.3 | Xác minh rằng bộ đếm đơn vị tính toán tích lũy và chi tiêu được theo dõi theo chuỗi yêu cầu; vượt quá giới hạn sẽ hủy bỏ chuỗi.      |   2    |   D/V   |
| 9.3.4 | Xác minh rằng phân tích hình thức hoặc kiểm tra mô hình chứng minh sự vắng mặt của đệ quy không giới hạn trong các giao thức đại lý. |   3    |    V    |
| 9.3.5 | Xác minh rằng các sự kiện dừng vòng lặp tạo ra cảnh báo và cung cấp các chỉ số cải tiến liên tục.                                    |   3    |    D    |

---

## 9.4 Bảo vệ chống lạm dụng cấp giao thức

Kênh truyền thông an toàn giữa các tác nhân và hệ thống bên ngoài để ngăn chặn chiếm quyền hoặc thao túng.

|   #   | Mô tả                                                                                                                                                  | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 9.4.1 | Xác minh rằng tất cả các tin nhắn giữa đại lý với công cụ và đại lý với đại lý đều được xác thực (ví dụ: mutual TLS hoặc JWT) và được mã hóa đầu cuối. |   1    |   D/V   |
| 9.4.2 | Xác minh rằng các schema được xác thực một cách nghiêm ngặt; các trường không xác định hoặc các thông điệp bị sai định dạng sẽ bị từ chối.             |   1    |    D    |
| 9.4.3 | Xác minh rằng các kiểm tra tính toàn vẹn (MAC hoặc chữ ký số) bao phủ toàn bộ phần tải tin nhắn bao gồm cả các tham số công cụ.                        |   2    |   D/V   |
| 9.4.4 | Xác minh rằng việc bảo vệ chống phát lại (nonce hoặc cửa sổ dấu thời gian) được thực thi ở tầng giao thức.                                             |   2    |    D    |
| 9.4.5 | Xác minh rằng các triển khai giao thức được thực hiện kiểm thử fuzzing và phân tích tĩnh để phát hiện các lỗi tiêm nhiễm hoặc giải tuần tự.            |   3    |    V    |

---

## 9.5 Thông Tin Định Danh Đại Lý & Bằng Chứng Chống Thay Đổi

Đảm bảo các hành động có thể được truy nguyên và các sửa đổi có thể phát hiện được.

|   #   | Mô tả                                                                                                                                    | Cấp độ | Vai trò |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 9.5.1 | Xác minh rằng mỗi thực thể đại lý sở hữu một danh tính mật mã duy nhất (cặp khóa hoặc chứng nhận gốc phần cứng).                         |   1    |   D/V   |
| 9.5.2 | Xác minh rằng tất cả các hành động của đại lý đều được ký và ghi dấu thời gian; các bản ghi bao gồm chữ ký để đảm bảo không thể chối bỏ. |   2    |   D/V   |
| 9.5.3 | Xác minh rằng các nhật ký có khả năng phát hiện giả mạo được lưu trữ trên một phương tiện chỉ cho phép thêm dữ liệu hoặc ghi một lần.    |   2    |    V    |
| 9.5.4 | Xác minh rằng các khóa định danh được thay đổi theo lịch trình định trước và khi có dấu hiệu bị xâm phạm.                                |   3    |    D    |
| 9.5.5 | Xác minh rằng các cố gắng giả mạo hoặc xung đột khóa sẽ kích hoạt việc cách ly ngay lập tức đối với tác nhân bị ảnh hưởng.               |   3    |   D/V   |

---

## 9.6 Giảm Thiểu Rủi Ro Đàn Động Tác Tác Động Đa Tác Nhân

Giảm thiểu các nguy cơ hành vi tập thể thông qua cách ly và mô hình hóa an toàn chính thức.

|   #   | Mô tả                                                                                                                                                           | Cấp độ | Vai trò |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 9.6.1 | Xác minh rằng các tác nhân hoạt động trong các miền bảo mật khác nhau thực thi trong các môi trường chạy tách biệt hoặc các phân đoạn mạng riêng biệt.          |   1    |   D/V   |
| 9.6.2 | Xác minh rằng các hành vi bầy đàn được mô hình hóa và xác minh chính thức về tính sống động và an toàn trước khi triển khai.                                    |   3    |    V    |
| 9.6.3 | Xác minh rằng các bộ giám sát thời gian chạy phát hiện các mẫu không an toàn mới phát sinh (ví dụ: dao động, tình trạng treo) và thực hiện hành động khắc phục. |   3    |    D    |

---

## 9.7 Xác thực / Ủy quyền người dùng và công cụ

Triển khai kiểm soát truy cập chặt chẽ cho mọi hành động do đại lý kích hoạt.

|   #   | Mô tả                                                                                                                                                         | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 9.7.1 | Xác minh rằng các đại lý xác thực như các chủ thể hạng nhất đối với các hệ thống hạ nguồn, không bao giờ sử dụng lại thông tin đăng nhập của người dùng cuối. |   1    |   D/V   |
| 9.7.2 | Xác minh rằng các chính sách ủy quyền chi tiết giới hạn công cụ mà tác nhân có thể gọi và các tham số mà nó có thể cung cấp.                                  |   2    |    D    |
| 9.7.3 | Xác minh rằng các kiểm tra đặc quyền được đánh giá lại ở mỗi lần gọi (ủy quyền liên tục), không chỉ tại lúc bắt đầu phiên đăng nhập.                          |   2    |    V    |
| 9.7.4 | Xác minh rằng các đặc quyền được ủy quyền tự động hết hạn và yêu cầu đồng ý lại sau khi hết thời gian hoặc thay đổi phạm vi.                                  |   3    |    D    |

---

## 9.8 Bảo mật Giao tiếp Động tác viên-động tác viên

Mã hóa và bảo vệ tính toàn vẹn cho tất cả các thông điệp giữa các tác nhân để ngăn chặn việc nghe trộm và giả mạo.

|   #   | Mô tả                                                                                                                                                     | Cấp độ | Vai trò |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 9.8.1 | Xác nhận rằng xác thực hai chiều và mã hóa bảo mật hoàn hảo về phía trước (ví dụ: TLS 1.3) là bắt buộc cho các kênh đại lý.                               |   1    |   D/V   |
| 9.8.2 | Xác minh rằng tính toàn vẹn và nguồn gốc của thông điệp được xác thực trước khi xử lý; các lỗi sẽ kích hoạt cảnh báo và loại bỏ thông điệp.               |   1    |    D    |
| 9.8.3 | Xác minh rằng siêu dữ liệu giao tiếp (dấu thời gian, số thứ tự) được ghi lại để hỗ trợ việc tái tạo pháp y.                                               |   2    |   D/V   |
| 9.8.4 | Xác minh rằng việc xác minh hình thức hoặc kiểm tra mô hình xác nhận rằng các máy trạng thái giao thức không thể bị dẫn đến các trạng thái không an toàn. |   3    |    V    |

---

## 9.9 Xác minh ý định & Thực thi ràng buộc

Xác nhận rằng các hành động của đại lý phù hợp với ý định đã được người dùng nêu ra và các ràng buộc của hệ thống.

|   #   | Mô tả                                                                                                                                                                                                     | Cấp độ | Vai trò |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 9.9.1 | Xác minh rằng các bộ giải ràng buộc trước khi thực thi kiểm tra các hành động được đề xuất dựa trên các quy tắc an toàn và chính sách được mã hóa cứng.                                                   |   1    |    D    |
| 9.9.2 | Xác minh rằng các hành động có tác động lớn (tài chính, phá hoại, nhạy cảm về quyền riêng tư) yêu cầu xác nhận mục đích rõ ràng từ người dùng khởi xướng.                                                 |   2    |   D/V   |
| 9.9.3 | Xác minh rằng các kiểm tra điều kiện hậu xác nhận các hành động đã hoàn thành đạt được hiệu quả dự định mà không có tác dụng phụ; các sai lệch sẽ kích hoạt việc hoàn tác.                                |   2    |    V    |
| 9.9.4 | Xác minh rằng các phương pháp hình thức (ví dụ, kiểm tra mô hình, chứng minh định lý) hoặc kiểm thử dựa trên thuộc tính chứng minh rằng các kế hoạch của đại lý đáp ứng tất cả các ràng buộc đã khai báo. |   3    |    V    |
| 9.9.5 | Xác nhận rằng các sự cố không khớp ý định hoặc vi phạm ràng buộc được đưa vào chu trình cải tiến liên tục và chia sẻ thông tin tình báo về mối đe dọa.                                                    |   3    |    D    |

---

## 9.10 Chiến lược Lập luận Đại lý An ninh

Lựa chọn và thực thi an toàn các chiến lược suy luận khác nhau bao gồm các phương pháp ReAct, Chuỗi suy nghĩ (Chain-of-Thought) và Cây suy nghĩ (Tree-of-Thoughts).

|   #    | Mô tả                                                                                                                                                                                                                                           | Cấp độ | Vai trò |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 9.10.1 | Xác minh rằng việc lựa chọn chiến lược suy luận sử dụng các tiêu chí quyết định (độ phức tạp đầu vào, loại nhiệm vụ, ngữ cảnh bảo mật) và các đầu vào giống hệt nhau tạo ra các lựa chọn chiến lược giống nhau trong cùng một ngữ cảnh bảo mật. |   1    |   D/V   |
| 9.10.2 | Xác minh rằng mỗi chiến lược tư duy (ReAct, Chuỗi suy nghĩ, Cây suy nghĩ) có kiểm tra đầu vào riêng biệt, làm sạch đầu ra, và giới hạn thời gian thực thi phù hợp với phương pháp nhận thức của nó.                                             |   1    |   D/V   |
| 9.10.3 | Xác nhận rằng các chuyển đổi chiến lược suy luận được ghi lại với bối cảnh đầy đủ bao gồm đặc điểm đầu vào, giá trị tiêu chí lựa chọn và siêu dữ liệu thực thi để tái tạo dấu vết kiểm tra.                                                     |   2    |   D/V   |
| 9.10.4 | Xác minh rằng phương pháp suy luận Tree-of-Thoughts bao gồm các cơ chế cắt tỉa nhánh để chấm dứt việc khám phá khi phát hiện vi phạm chính sách, giới hạn tài nguyên hoặc ranh giới an toàn.                                                    |   2    |   D/V   |
| 9.10.5 | Xác minh rằng chu kỳ ReAct (Lý luận-Hành động-Quan sát) bao gồm các điểm kiểm tra xác thực ở mỗi giai đoạn: xác minh bước lý luận, phê duyệt hành động, và làm sạch quan sát trước khi tiếp tục.                                                |   2    |   D/V   |
| 9.10.6 | Xác minh rằng các chỉ số hiệu suất chiến lược lý luận (thời gian thực thi, sử dụng tài nguyên, chất lượng đầu ra) được theo dõi với các cảnh báo tự động khi các chỉ số vượt quá ngưỡng cấu hình.                                               |   3    |   D/V   |
| 9.10.7 | Xác minh rằng các phương pháp suy luận kết hợp nhiều chiến lược duy trì việc xác thực đầu vào và các giới hạn đầu ra của tất cả các chiến lược thành phần mà không vượt qua bất kỳ kiểm soát bảo mật nào.                                       |   3    |   D/V   |
| 9.10.8 | Xác nhận rằng kiểm thử bảo mật chiến lược lý luận bao gồm việc thử nghiệm fuzzing với các đầu vào bị lỗi, các lời nhắc đối kháng được thiết kế để buộc chuyển đổi chiến lược, và kiểm thử điều kiện biên cho từng phương pháp nhận thức.        |   3    |   D/V   |

---

## 9.11 Quản lý trạng thái vòng đời đại lý & Bảo mật

Khởi tạo đại lý an toàn, chuyển đổi trạng thái và kết thúc với các dấu vết kiểm toán mật mã và quy trình phục hồi được xác định rõ.

|   #    | Mô tả                                                                                                                                                                                                                                                                            | Cấp độ | Vai trò |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 9.11.1 | Xác minh rằng việc khởi tạo tác nhân bao gồm thiết lập danh tính mật mã với chứng chỉ được bảo vệ bởi phần cứng và các nhật ký kiểm toán khởi động không thể thay đổi chứa ID tác nhân, dấu thời gian, hàm băm cấu hình và các tham số khởi tạo.                                 |   1    |   D/V   |
| 9.11.2 | Xác minh rằng các chuyển đổi trạng thái của đại lý được ký thuật toán mã hóa, đóng dấu thời gian và ghi lại cùng với ngữ cảnh đầy đủ bao gồm các sự kiện kích hoạt, băm trạng thái trước đó, băm trạng thái mới và các xác thực bảo mật đã được thực hiện.                       |   2    |   D/V   |
| 9.11.3 | Xác nhận rằng các quy trình tắt agent bao gồm việc xóa bộ nhớ an toàn bằng phương pháp xóa mật mã hoặc ghi đè nhiều lần, thu hồi thông tin đăng nhập kèm theo thông báo tới cơ quan cấp chứng chỉ, và tạo ra các chứng chỉ chấm dứt có khả năng phát hiện giả mạo.               |   2    |   D/V   |
| 9.11.4 | Xác minh rằng các cơ chế phục hồi tác nhân xác thực tính toàn vẹn của trạng thái bằng cách sử dụng các bảng kiểm tra mật mã (ít nhất là SHA-256) và khôi phục lại các trạng thái đã biết là tốt khi phát hiện hỏng hóc, kèm theo cảnh báo tự động và yêu cầu phê duyệt thủ công. |   3    |   D/V   |
| 9.11.5 | Xác minh rằng các cơ chế lưu trữ trạng thái của tác nhân mã hóa dữ liệu trạng thái nhạy cảm bằng khóa AES-256 riêng cho từng tác nhân và triển khai việc xoay khóa an toàn theo lịch trình có thể cấu hình (tối đa 90 ngày) với việc triển khai không gián đoạn.                 |   3    |   D/V   |

---

## 9.12 Khung An ninh Tích hợp Công cụ

Các biện pháp kiểm soát bảo mật cho việc tải công cụ động, thực thi và xác thực kết quả với các quy trình đánh giá rủi ro và phê duyệt đã được xác định.

|   #    | Mô tả                                                                                                                                                                                                                                                              | Cấp độ | Vai trò |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 9.12.1 | Xác minh rằng các mô tả công cụ bao gồm siêu dữ liệu bảo mật chỉ định các đặc quyền cần thiết (đọc/ghi/thực thi), mức độ rủi ro (thấp/trung bình/cao), giới hạn tài nguyên (CPU, bộ nhớ, mạng), và các yêu cầu xác thực được ghi chép trong các bản mô tả công cụ. |   1    |   D/V   |
| 9.12.2 | Xác minh rằng kết quả thực thi công cụ được kiểm tra xác thực theo các lược đồ dự kiến (JSON Schema, XML Schema) và các chính sách bảo mật (lọc đầu ra, phân loại dữ liệu) trước khi tích hợp, với các giới hạn thời gian chờ và quy trình xử lý lỗi.              |   1    |   D/V   |
| 9.12.3 | Xác minh rằng nhật ký tương tác công cụ bao gồm ngữ cảnh bảo mật chi tiết bao gồm việc sử dụng đặc quyền, mô hình truy cập dữ liệu, thời gian thực thi, tiêu thụ tài nguyên và mã trả về với ghi nhật ký có cấu trúc để tích hợp SIEM.                             |   2    |   D/V   |
| 9.12.4 | Xác minh rằng các cơ chế tải công cụ động kiểm tra chữ ký số sử dụng hạ tầng PKI và thực hiện các giao thức tải an toàn với cách ly sandbox cùng xác minh quyền trước khi thực thi.                                                                                |   2    |   D/V   |
| 9.12.5 | Xác minh rằng các đánh giá bảo mật công cụ được kích hoạt tự động cho các phiên bản mới với các cổng phê duyệt bắt buộc bao gồm phân tích tĩnh, kiểm thử động và đánh giá nhóm bảo mật cùng với các tiêu chí phê duyệt đã được tài liệu hóa và yêu cầu SLA.        |   3    |   D/V   |

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

