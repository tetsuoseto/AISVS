# 9 Điều phối tự trị và Hành động mang tính tác nhân Bảo mật

## Mục tiêu kiểm soát

Đảm bảo rằng hệ thống AI tự trị hoặc AI đa tác nhân chỉ có thể thực thi các hành động được định trước một cách rõ ràng, có xác thực, có thể kiểm toán và nằm trong ngưỡng chi phí cũng như rủi ro có giới hạn. Điều này bảo vệ chống lại các mối đe dọa như Xâm phạm hệ thống tự trị, Lạm dụng công cụ, Phát hiện vòng lặp tác nhân, Chiếm quyền kiểm soát liên lạc, Đánh lừa danh tính, Thao túng đàn tác nhân, và Thao túng ý định.

---

## 9.1 Lập kế hoạch tác vụ của tác nhân và ngân sách đệ quy

Kìm hãm các kế hoạch đệ quy và bắt buộc có điểm kiểm tra của con người đối với các hành động có đặc quyền.

|   #   | Mô tả                                                                                                                                                                                                             | Cấp độ | Vai trò |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 9.1.1 | Xác minh rằng độ sâu đệ quy tối đa, độ rộng tìm kiếm, thời gian đồng hồ, token, và chi phí tiền tệ cho mỗi lần thực thi của tác nhân được cấu hình tập trung và được kiểm soát phiên bản.                         |   1    |   D/V   |
| 9.1.2 | Xác minh rằng các hành động đặc quyền hoặc không thể đảo ngược (ví dụ: cam kết mã nguồn, chuyển tiền) yêu cầu sự phê duyệt của con người một cách rõ ràng thông qua một kênh có thể kiểm toán trước khi thực thi. |   1    |   D/V   |
| 9.1.3 | Xác nhận rằng các bộ giám sát tài nguyên thời gian thực kích hoạt sự ngắt mạch khi bất kỳ ngưỡng ngân sách nào bị vượt quá, đồng thời tạm dừng việc mở rộng thêm các tác vụ.                                      |   2    |    D    |
| 9.1.4 | Xác minh rằng các sự kiện circuit-breaker được ghi lại cùng với ID tác nhân, điều kiện kích hoạt và trạng thái kế hoạch được ghi nhận cho việc xem xét pháp y.                                                    |   2    |   D/V   |
| 9.1.5 | Xác minh rằng các bài kiểm tra bảo mật bao phủ các kịch bản budget-exhaustion và runaway-plan, đồng thời xác nhận việc dừng an toàn mà không làm mất dữ liệu.                                                     |   3    |    V    |
| 9.1.6 | Xác minh rằng các chính sách ngân sách được thể hiện dưới dạng policy-as-code và được thực thi trong CI/CD để ngăn chặn sự lệch cấu hình.                                                                         |   3    |    D    |

---

## 9.2 Cô lập Sandbox cho Plugin Công cụ

Cô lập các tương tác với công cụ để ngăn chặn truy cập trái phép vào hệ thống hoặc thực thi mã.

|   #   | Mô tả                                                                                                                                                                       | Cấp độ | Vai trò |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 9.2.1 | Đảm bảo mọi công cụ plugin đều được thực thi trong một sandbox ở cấp độ OS, container hoặc WASM, với các chính sách tối thiểu quyền cho hệ thống tệp, mạng và gọi hệ thống. |   1    |   D/V   |
| 9.2.2 | Xác minh rằng các hạn mức tài nguyên sandbox (CPU, bộ nhớ, đĩa, lưu lượng mạng ra) và thời gian chờ thực thi được áp dụng và ghi lại.                                       |   1    |   D/V   |
| 9.2.3 | Xác minh rằng các nhị phân của công cụ hoặc các descriptor được ký số; chữ ký được xác thực trước khi tải.                                                                  |   2    |   D/V   |
| 9.2.4 | Xác minh rằng dữ liệu telemetry từ sandbox được truyền tới SIEM; các bất thường (ví dụ: cố gắng thiết lập kết nối ra ngoài) sẽ kích hoạt cảnh báo.                          |   2    |    V    |
| 9.2.5 | Xác nhận rằng các plugin rủi ro cao được đánh giá bảo mật và thử nghiệm xâm nhập trước khi triển khai lên môi trường sản xuất.                                              |   3    |    V    |
| 9.2.6 | Xác nhận rằng các nỗ lực thoát khỏi sandbox được tự động chặn và plugin vi phạm bị cách ly cho đến khi điều tra hoàn tất.                                                   |   3    |   D/V   |

---

## 9.3 Vòng lặp tự chủ & Giới hạn chi phí

Phát hiện và ngăn chặn đệ quy giữa các tác nhân không kiểm soát được và sự tăng chi phí quá mức.

|   #   | Mô tả                                                                                                                                            | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 9.3.1 | Xác minh rằng các cuộc gọi giữa các tác nhân bao gồm một giới hạn hop hoặc TTL, mà thời gian chạy sẽ giảm giá trị và thực thi giới hạn đó.       |   1    |   D/V   |
| 9.3.2 | Xác minh rằng các tác nhân duy trì một mã nhận diện đồ thị lời gọi duy nhất để phát hiện tự gọi hoặc các mẫu tuần hoàn.                          |   2    |    D    |
| 9.3.3 | Xác minh rằng các bộ đếm tích lũy cho đơn vị tính toán và chi phí được theo dõi theo từng chuỗi yêu cầu; vi phạm giới hạn sẽ khiến chuỗi bị hủy. |   2    |   D/V   |
| 9.3.4 | Xác minh rằng phân tích hình thức hoặc kiểm tra mô hình cho thấy sự vắng mặt của đệ quy vô hạn trong các giao thức của tác nhân.                 |   3    |    V    |
| 9.3.5 | Xác minh rằng các sự kiện vòng lặp bị hủy bỏ tạo cảnh báo và cung cấp các chỉ số cải tiến liên tục.                                              |   3    |    D    |

---

## 9.4 Bảo vệ chống lạm dụng ở mức giao thức

Đảm bảo kênh giao tiếp được bảo mật giữa các tác nhân và các hệ thống bên ngoài để ngăn chặn việc chiếm quyền kiểm soát hoặc thao túng.

|   #   | Mô tả                                                                                                                                                                         | Cấp độ | Vai trò |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 9.4.1 | Xác minh rằng tất cả các tin nhắn từ tác nhân đến công cụ và tin nhắn từ tác nhân sang tác nhân được xác thực (ví dụ: TLS hai chiều hoặc JWT) và được mã hóa từ đầu đến cuối. |   1    |   D/V   |
| 9.4.2 | Đảm bảo các lược đồ được xác thực nghiêm ngặt; các trường không xác định hoặc tin nhắn bị định dạng sai sẽ bị từ chối.                                                        |   1    |    D    |
| 9.4.3 | Xác minh rằng các kiểm tra tính toàn vẹn (MAC hoặc chữ ký số) bao phủ toàn bộ payload của thông điệp, bao gồm tham số công cụ.                                                |   2    |   D/V   |
| 9.4.4 | Xác minh rằng bảo vệ chống phát lại (nonce hoặc cửa sổ dấu thời gian) được thực thi ở lớp giao thức.                                                                          |   2    |    D    |
| 9.4.5 | Xác minh rằng các triển khai giao thức đã trải qua fuzzing và phân tích tĩnh để phát hiện các lỗ hổng tiêm hoặc giải tuần tự dữ liệu.                                         |   3    |    V    |

---

## 9.5 Danh tính tác nhân và Chứng cứ can thiệp

Đảm bảo các hành động có thể được truy nguồn gốc và các sửa đổi có thể bị phát hiện.

|   #   | Mô tả                                                                                                                            | Cấp độ | Vai trò |
| :---: | -------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 9.5.1 | Xác minh rằng mỗi thể hiện của tác nhân có một danh tính mật mã duy nhất (cặp khóa hoặc chứng chỉ gốc từ phần cứng).             |   1    |   D/V   |
| 9.5.2 | Xác minh rằng toàn bộ hành động của tác nhân được ký và gắn dấu thời gian; nhật ký có chữ ký để đảm bảo tính không thể phủ nhận. |   2    |   D/V   |
| 9.5.3 | Xác minh rằng nhật ký chống giả mạo được lưu trên một phương tiện chỉ cho phép ghi thêm hoặc ghi một lần.                        |   2    |    V    |
| 9.5.4 | Xác nhận rằng các khóa nhận diện được xoay vòng theo lịch trình xác định và khi có các dấu hiệu bị xâm phạm.                     |   3    |    D    |
| 9.5.5 | Xác minh rằng các nỗ lực giả mạo hoặc cố gắng gây xung đột khóa sẽ kích hoạt cách ly ngay lập tức đối với tác nhân bị ảnh hưởng. |   3    |   D/V   |

---

## 9.6 Giảm thiểu rủi ro của bầy đàn đa tác nhân

Giảm thiểu các mối nguy hiểm do hành vi tập thể thông qua cô lập và mô hình hóa an toàn mang tính hình thức.

|   #   | Mô tả                                                                                                                                                                   | Cấp độ | Vai trò |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 9.6.1 | Xác minh rằng các tác nhân hoạt động ở các miền bảo mật khác nhau được thực thi trong các sandbox thời gian chạy được cô lập hoặc trong các phân đoạn mạng được cô lập. |   1    |   D/V   |
| 9.6.2 | Xác nhận rằng các hành vi của bầy robot swarm được mô hình hóa và được xác minh hình thức cho tính khả sống và tính an toàn trước khi triển khai.                       |   3    |    V    |
| 9.6.3 | Hãy xác nhận rằng các trình giám sát thời gian chạy có thể phát hiện các mẫu không an toàn nảy sinh (ví dụ: dao động, điểm chết) và khởi xướng biện pháp khắc phục.     |   3    |    D    |

---

## 9.7 Xác thực / Ủy quyền Người dùng & Công cụ

Triển khai các biện pháp kiểm soát truy cập mạnh mẽ cho mọi hành động do tác nhân kích hoạt.

|   #   | Mô tả                                                                                                                                                                    | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 9.7.1 | Xác minh rằng các tác nhân xác thực với tư cách là chủ thể cấp nhất đối với các hệ thống downstream và không bao giờ tái sử dụng thông tin xác thực của người dùng cuối. |   1    |   D/V   |
| 9.7.2 | Xác nhận rằng các chính sách ủy quyền ở mức chi tiết giới hạn những công cụ mà một tác nhân có thể gọi và các tham số mà nó có thể cung cấp.                             |   2    |    D    |
| 9.7.3 | Xác minh rằng các kiểm tra quyền được đánh giá lại ở mỗi lần gọi (ủy quyền liên tục), chứ không chỉ ở lúc bắt đầu phiên.                                                 |   2    |    V    |
| 9.7.4 | Xác minh rằng quyền được ủy quyền tự động hết hạn và yêu cầu tái đồng ý sau khi hết thời gian hoặc thay đổi phạm vi.                                                     |   3    |    D    |

---

## 9.8 Bảo mật giao tiếp giữa các tác nhân

Mã hóa và bảo vệ tính toàn vẹn cho tất cả các thông điệp giữa các tác nhân để ngăn chặn nghe lén và sửa đổi.

|   #   | Mô tả                                                                                                                                                               | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 9.8.1 | Xác thực lẫn nhau và mã hóa có tính bí mật phiên hoàn hảo (ví dụ TLS 1.3) là bắt buộc đối với các kênh của tác nhân.                                                |   1    |   D/V   |
| 9.8.2 | Xác minh tính toàn vẹn của thông điệp và nguồn gốc trước khi xử lý; nếu xác thực thất bại, hãy kích hoạt cảnh báo và loại bỏ thông điệp.                            |   1    |    D    |
| 9.8.3 | Xác minh rằng siêu dữ liệu giao tiếp (dấu thời gian, số thứ tự) được ghi lại để hỗ trợ tái dựng pháp y.                                                             |   2    |   D/V   |
| 9.8.4 | Hãy xác minh rằng xác minh hình thức hoặc kiểm tra mô hình có thể xác nhận rằng các máy trạng thái của giao thức không thể bị đưa vào các trạng thái không an toàn. |   3    |    V    |

---

## 9.9 Xác minh ý định & Thực thi ràng buộc

Xác nhận rằng các hành động của tác nhân phù hợp với ý định được người dùng nêu ra và các ràng buộc của hệ thống.

|   #   | Mô tả                                                                                                                                                                                                 | Cấp độ | Vai trò |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 9.9.1 | Xác nhận rằng các trình giải ràng buộc tiền thực thi kiểm tra các hành động được đề xuất so với các quy tắc an toàn và chính sách được nhúng sẵn.                                                     |   1    |    D    |
| 9.9.2 | Xác minh rằng các hành động có tác động cao (tài chính, phá hủy, nhạy cảm với quyền riêng tư) yêu cầu xác nhận ý định rõ ràng từ người dùng khởi xướng.                                               |   2    |   D/V   |
| 9.9.3 | Xác nhận rằng các kiểm tra hậu điều kiện xác thực các hành động đã hoàn tất, đạt được các tác động mong đợi và không gây tác dụng phụ; những sai lệch sẽ kích hoạt rollback.                          |   2    |    V    |
| 9.9.4 | Xác minh rằng các phương pháp hình thức (ví dụ: kiểm tra mô hình, chứng minh định lý) hoặc kiểm tra dựa trên đặc tính cho thấy các kế hoạch của tác nhân thỏa mãn tất cả các ràng buộc được khai báo. |   3    |    V    |
| 9.9.5 | Xác nhận rằng các sự cố lệch ý định hoặc vi phạm ràng buộc đóng góp vào chu trình cải tiến liên tục và chia sẻ thông tin tình báo về các mối đe dọa.                                                  |   3    |    D    |

---

## 9.10 Chiến lược Suy luận của Tác nhân cho Bảo mật

Lựa chọn và thực thi an toàn các chiến lược suy luận khác nhau, bao gồm ReAct, Chain-of-Thought và Tree-of-Thoughts.

|   #    | Mô tả                                                                                                                                                                                                                                          | Cấp độ | Vai trò |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 9.10.1 | Xác minh rằng việc lựa chọn chiến lược suy luận sử dụng các tiêu chí xác định (độ phức tạp của đầu vào, loại tác vụ, ngữ cảnh bảo mật) và các đầu vào giống nhau sẽ tạo ra các lựa chọn chiến lược giống hệt nhau trong cùng ngữ cảnh bảo mật. |   1    |   D/V   |
| 9.10.2 | Xác minh rằng mỗi chiến lược suy luận (ReAct, Chain-of-Thought, Tree-of-Thoughts) có xác thực đầu vào riêng biệt, làm sạch đầu ra và giới hạn thời gian thực thi tương ứng với phương pháp nhận thức của nó.                                   |   1    |   D/V   |
| 9.10.3 | Xác minh rằng các chuyển tiếp của chiến lược suy luận được ghi lại với đầy đủ ngữ cảnh, bao gồm đặc tính đầu vào, giá trị của các tiêu chí lựa chọn và siêu dữ liệu thực thi để tái tạo dấu vết kiểm toán.                                     |   2    |   D/V   |
| 9.10.4 | Xác nhận rằng lý luận Tree-of-Thoughts bao gồm các cơ chế cắt nhánh để kết thúc quá trình khám phá khi phát hiện vi phạm chính sách, giới hạn tài nguyên hoặc ranh giới an toàn.                                                               |   2    |   D/V   |
| 9.10.5 | Xác minh rằng chu trình ReAct (Reason-Act-Observe) bao gồm các điểm xác thực ở mỗi giai đoạn: xác minh bước suy luận, phê duyệt hành động và chuẩn hóa quan sát trước khi tiến hành.                                                           |   2    |   D/V   |
| 9.10.6 | Xác nhận rằng các chỉ số hiệu suất của chiến lược suy luận (thời gian thực thi, mức sử dụng tài nguyên, chất lượng đầu ra) được giám sát bằng các cảnh báo tự động khi các chỉ số vượt ngưỡng đã được cấu hình.                                |   3    |   D/V   |
| 9.10.7 | Xác minh rằng các phương pháp suy luận lai kết hợp nhiều chiến lược duy trì xác thực đầu vào và ràng buộc đầu ra của tất cả các chiến lược thành phần mà không bỏ qua bất kỳ biện pháp kiểm soát bảo mật nào.                                  |   3    |   D/V   |
| 9.10.8 | Xác minh rằng kiểm thử bảo mật cho chiến lược suy luận bao gồm fuzzing với đầu vào bị sai định dạng, các lời nhắc thù địch được thiết kế để ép buộc chuyển đổi chiến lược, và kiểm thử điều kiện biên cho từng cách tiếp cận nhận thức.        |   3    |   D/V   |

---

## 9.11 Quản lý trạng thái vòng đời của tác nhân và bảo mật

Khởi tạo tác nhân an toàn, chuyển đổi trạng thái và kết thúc với dấu vết kiểm toán mật mã và các thủ tục khôi phục được định nghĩa.

|   #    | Mô tả                                                                                                                                                                                                                                                              | Cấp độ | Vai trò |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 9.11.1 | Xác nhận rằng quá trình khởi tạo tác nhân bao gồm thiết lập danh tính bằng mật mã với chứng thực dựa trên phần cứng và nhật ký kiểm toán khởi động bất biến chứa ID tác nhân, dấu thời gian, băm cấu hình và các tham số khởi tạo.                                 |   1    |   D/V   |
| 9.11.2 | Xác minh rằng các chuyển đổi trạng thái của tác nhân được ký số, gắn dấu thời gian và được ghi lại với đầy đủ bối cảnh bao gồm các sự kiện kích hoạt, giá trị băm của trạng thái trước, giá trị băm của trạng thái mới, và các xác thực bảo mật đã được thực hiện. |   2    |   D/V   |
| 9.11.3 | Xác minh rằng quy trình tắt tác nhân bao gồm xóa sạch bộ nhớ bằng mã hóa (cryptographic erasure) hoặc ghi đè nhiều lượt, thu hồi thông tin xác thực kèm thông báo cho cơ quan cấp chứng chỉ, và tạo chứng chỉ kết thúc có khả năng phát hiện sự can thiệp.         |   2    |   D/V   |
| 9.11.4 | Xác minh rằng các cơ chế phục hồi của tác nhân xác thực tính toàn vẹn của trạng thái bằng cách sử dụng các chuỗi băm mật mã (tối thiểu SHA-256) và quay về trạng thái được biết là hợp lệ khi phát hiện sự cố, với cảnh báo tự động và yêu cầu phê duyệt thủ công. |   3    |   D/V   |
| 9.11.5 | Xác minh rằng các cơ chế lưu trữ trạng thái của tác nhân mã hóa dữ liệu trạng thái nhạy cảm bằng khóa AES-256 cho từng tác nhân và triển khai quay vòng khóa an toàn theo lịch trình có thể cấu hình (tối đa 90 ngày) với triển khai không gián đoạn.              |   3    |   D/V   |

---

## 9.12 Khung bảo mật tích hợp công cụ

Các biện pháp kiểm soát an ninh cho việc tải công cụ động, thực thi và xác thực kết quả với các quy trình đánh giá rủi ro và phê duyệt được định nghĩa.

|   #    | Mô tả                                                                                                                                                                                                                                                     | Cấp độ | Vai trò |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 9.12.1 | Xác minh rằng các mô tả công cụ bao gồm siêu dữ liệu bảo mật chỉ định quyền được yêu cầu (đọc/ghi/thực thi), mức độ rủi ro (thấp/trung bình/cao), giới hạn tài nguyên (CPU, bộ nhớ, mạng), và các yêu cầu xác thực được ghi trong manifest của công cụ.   |   1    |   D/V   |
| 9.12.2 | Xác minh rằng kết quả thực thi công cụ được xác thực theo các schema mong đợi (JSON Schema, XML Schema) và các chính sách bảo mật (làm sạch đầu ra, phân loại dữ liệu) trước khi tích hợp với các giới hạn thời gian chờ và các thủ tục xử lý lỗi.        |   1    |   D/V   |
| 9.12.3 | Xác minh rằng nhật ký tương tác của công cụ chứa bối cảnh bảo mật chi tiết, bao gồm việc sử dụng đặc quyền, các mẫu truy cập dữ liệu, thời gian thực thi, mức tiêu thụ tài nguyên và mã trả về, được ghi nhật ký có cấu trúc để tích hợp với SIEM.        |   2    |   D/V   |
| 9.12.4 | Xác minh rằng các cơ chế nạp công cụ động xác thực chữ ký số bằng hạ tầng PKI và triển khai các giao thức nạp an toàn với cô lập sandbox và xác thực quyền trước khi thực thi.                                                                            |   2    |   D/V   |
| 9.12.5 | Xác minh rằng các đánh giá bảo mật công cụ được tự động kích hoạt cho các phiên bản mới với các cổng phê duyệt bắt buộc bao gồm phân tích tĩnh, kiểm thử động và xem xét của đội ngũ bảo mật, với các tiêu chí phê duyệt được ghi lại và các yêu cầu SLA. |   3    |   D/V   |

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

