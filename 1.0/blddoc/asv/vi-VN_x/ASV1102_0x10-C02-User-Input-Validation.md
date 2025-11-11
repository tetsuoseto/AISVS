# Xác thực đầu vào người dùng C2

## Mục tiêu Kiểm soát

Việc xác thực đầu vào của người dùng một cách chặt chẽ là hàng phòng thủ đầu tiên chống lại một số cuộc tấn công gây hại nhất đối với các hệ thống AI. Các cuộc tấn công chèn lệnh (prompt injection) có thể ghi đè các hướng dẫn của hệ thống, làm rò rỉ dữ liệu nhạy cảm hoặc điều hướng mô hình theo hành vi không được phép. Trừ khi có bộ lọc chuyên biệt và các biện pháp xác thực khác được thiết lập, các nghiên cứu cho thấy các cách vượt rào sử dụng khai thác cửa sổ ngữ cảnh vẫn sẽ tiếp tục hiệu quả.

---

## C2.1 Phòng chống Tiêm nhiễm Lệnh Đầu vào

Tiêm nhiễm lệnh đầu vào là một trong những rủi ro hàng đầu đối với các hệ thống AI. Các biện pháp phòng thủ chống lại chiến thuật này sử dụng sự kết hợp của bộ lọc mẫu, bộ phân loại dữ liệu và việc thực thi thứ bậc các hướng dẫn.

|   #   | Mô tả                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 2.1.1 | Xác minh rằng bất kỳ đầu vào bên ngoài hoặc được dẫn xuất nào có thể điều khiển hành vi, bao gồm các lời nhắc của người dùng, kết quả RAG, đầu ra của plugin hoặc MCP, tin nhắn giữa các agent, phản hồi API hoặc webhook, tệp cấu hình hoặc chính sách, đọc và ghi bộ nhớ, đều được coi là không tin cậy, được làm vô hiệu hóa bằng cách trích dẫn hoặc gắn thẻ và loại bỏ nội dung kích hoạt, đồng thời được sàng lọc bởi bộ quy tắc hoặc dịch vụ phát hiện chèn lời nhắc được duy trì trước khi nối vào lời nhắc hoặc thực thi các hành động. |   1    |   D/V   |
| 2.1.2 | Xác minh rằng hệ thống thực thi một thứ bậc chỉ dẫn trong đó các tin nhắn của hệ thống và nhà phát triển ghi đè lên các chỉ dẫn của người dùng và các đầu vào không đáng tin cậy khác, ngay cả sau khi xử lý các chỉ dẫn của người dùng.                                                                                                                                                                                                                                                                                                         |   1    |   D/V   |
| 2.1.4 | Xác minh rằng các câu lệnh xuất phát từ nội dung của bên thứ ba (trang web, PDF, email) được làm sạch riêng biệt (ví dụ, loại bỏ các chỉ dẫn dạng hướng dẫn và làm trung hòa nội dung HTML, Markdown, và script) trước khi được ghép nối vào câu lệnh chính.                                                                                                                                                                                                                                                                                     |   2    |    D    |

---

## C2.2 Khả năng chống lại ví dụ đối kháng

Các mô hình Xử lý Ngôn ngữ Tự nhiên (NLP) vẫn còn dễ bị tổn thương bởi những biến động nhỏ ở cấp độ ký tự hoặc từ mà con người thường bỏ qua nhưng các mô hình lại có xu hướng phân loại sai.

|   #   | Mô tả                                                                                                                                                                                                                                                                                                                                               | Cấp độ | Vai trò |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 2.2.1 | Xác minh rằng các bước chuẩn hóa đầu vào cơ bản (Unicode NFC, ánh xạ homoglyph, cắt bớt khoảng trắng, loại bỏ các ký tự điều khiển và Unicode vô hình) được thực hiện trước khi phân tách từ hoặc nhúng và trước khi phân tích cú pháp thành các tham số công cụ hoặc MCP.                                                                          |   1    |    D    |
| 2.2.2 | Xác minh rằng phát hiện bất thường thống kê đánh dấu các đầu vào có khoảng cách chỉnh sửa cao bất thường so với chuẩn ngôn ngữ hoặc khoảng cách nhúng bất thường và rằng các đầu vào bị đánh dấu này được kiểm soát trước khi nối vào câu lệnh hoặc thực thi các hành động.                                                                         |   2    |   D/V   |
| 2.2.3 | Xác minh rằng quy trình suy luận hỗ trợ các biến thể mô hình được củng cố bằng đào tạo chống đối kháng hoặc các lớp phòng thủ (ví dụ: ngẫu nhiên hóa, chiết suất phòng thủ, kiểm tra căn chỉnh) cho các điểm cuối có rủi ro cao.                                                                                                                    |   2    |    D    |
| 2.2.4 | Xác minh rằng các đầu vào nghi ngờ là tấn công đối kháng được cách ly, đồng thời được ghi lại đầy đủ với toàn bộ nội dung và siêu dữ liệu truy vết (nguồn, công cụ hoặc máy chủ MCP, ID tác nhân, phiên làm việc).                                                                                                                                  |   2    |    V    |
| 2.2.5 | Xác minh rằng việc buôn lậu mã hóa và biểu diễn trong cả đầu vào và đầu ra (ví dụ: các ký tự Unicode/điều khiển vô hình, thay thế homoglyph, hoặc văn bản hướng hỗn hợp) được phát hiện và giảm thiểu. Các biện pháp giảm thiểu được phê duyệt bao gồm chuẩn hóa, xác thực lược đồ nghiêm ngặt, từ chối dựa trên chính sách, hoặc đánh dấu rõ ràng. |   2    |   D/V   |

---

## C2.3 Bộ Ký Tự Lệnh Prompt

Hạn chế bộ ký tự của dữ liệu đầu vào của người dùng chỉ cho phép các ký tự cần thiết cho yêu cầu kinh doanh có thể giúp ngăn chặn nhiều loại cuộc tấn công khác nhau.

|   #   | Mô tả                                                                                                                                                                          | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 2.3.1 | Xác minh rằng hệ thống thực hiện giới hạn bộ ký tự cho dữ liệu đầu vào của người dùng, chỉ cho phép các ký tự được yêu cầu rõ ràng cho mục đích kinh doanh.                    |   1    |    D    |
| 2.3.2 | Xác minh rằng phương pháp danh sách cho phép được sử dụng để định nghĩa tập ký tự được phép.                                                                                   |   1    |    D    |
| 2.3.3 | Xác minh rằng các đầu vào chứa ký tự nằm ngoài tập hợp cho phép bị từ chối và được ghi lại cùng với siêu dữ liệu theo dõi (nguồn, công cụ hoặc máy chủ MCP, ID đại lý, phiên). |   1    |   D/V   |

---

## C2.4 Xác thực Lược đồ, Kiểu dữ liệu & Độ dài

Các cuộc tấn công AI với đầu vào bị sai định dạng hoặc quá lớn có thể gây ra lỗi phân tích cú pháp, tràn prompt qua các trường khác nhau và cạn kiệt tài nguyên. Việc thực thi nghiêm ngặt schema cũng là điều kiện tiên quyết khi thực hiện các cuộc gọi công cụ định danh.

|   #   | Mô tả                                                                                                                                                                                                                                                                                                          | Cấp độ | Vai trò |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 2.4.1 | Xác minh rằng mọi API, công cụ hoặc điểm cuối MCP đều định nghĩa một sơ đồ đầu vào rõ ràng (JSON Schema, Protobuf hoặc tương đương đa phương thức), từ chối các trường thừa hoặc không xác định và ép kiểu ngầm định, đồng thời xác thực đầu vào phía máy chủ trước khi xây dựng prompt hoặc thực thi công cụ. |   1    |    D    |
| 2.4.2 | Xác minh rằng các đầu vào vượt quá giới hạn tối đa về token hoặc byte bị từ chối với lỗi an toàn và không bao giờ bị cắt ngầm.                                                                                                                                                                                 |   1    |   D/V   |
| 2.4.3 | Xác minh rằng các kiểm tra kiểu (ví dụ, phạm vi số, giá trị enum, loại MIME cho hình ảnh/âm thanh) được thực thi phía máy chủ bao gồm cả đối số cho công cụ hoặc MCP.                                                                                                                                          |   2    |   D/V   |
| 2.4.4 | Xác minh rằng các bộ xác thực ngữ nghĩa, hiểu đầu vào NLP, hoạt động trong thời gian không đổi và tránh các cuộc gọi mạng bên ngoài để ngăn chặn tấn công từ chối dịch vụ (DoS) theo thuật toán.                                                                                                               |   2    |    D    |
| 2.4.5 | Xác minh rằng các lỗi xác thực được ghi lại với các đoạn tải trọng đã được che khuất và mã lỗi rõ ràng, đồng thời bao gồm siêu dữ liệu theo dõi (nguồn, công cụ hoặc máy chủ MCP, ID đại lý, phiên làm việc) để hỗ trợ phân tích bảo mật.                                                                      |   3    |    V    |

---

## C2.5 Sàng lọc Nội dung & Chính sách

Các nhà phát triển nên có khả năng phát hiện các câu lệnh hợp ngữ pháp hợp lệ yêu cầu nội dung bị cấm (chẳng hạn như hướng dẫn bất hợp pháp, ngôn ngữ thù địch và/hoặc văn bản có bản quyền) rồi ngăn chặn chúng lan rộng.

|   #   | Mô tả                                                                                                                                                                                                                                                                                                 | Cấp độ | Vai trò |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 2.5.1 | Xác minh rằng một bộ phân loại nội dung (zero shot hoặc tinh chỉnh) đánh giá từng đầu vào và đầu ra về bạo lực, tự làm hại, thù địch, nội dung tình dục và các yêu cầu bất hợp pháp, với các ngưỡng có thể cấu hình.                                                                                  |   1    |    D    |
| 2.5.2 | Xác nhận rằng các đầu vào vi phạm chính sách sẽ bị từ chối để chúng không được truyền tiếp sang các cuộc gọi LLM hoặc công cụ/MCP phía dưới.                                                                                                                                                          |   1    |   D/V   |
| 2.5.3 | Xác minh rằng việc kiểm duyệt tuân thủ các chính sách cụ thể của người dùng (tuổi tác, các ràng buộc pháp lý khu vực) thông qua các quy tắc dựa trên thuộc tính được giải quyết tại thời điểm yêu cầu, bao gồm các thuộc tính vai trò đại lý.                                                         |   2    |    D    |
| 2.5.4 | Xác minh rằng các bản ghi sàng lọc bao gồm điểm tin cậy của bộ phân loại và thẻ danh mục chính sách với giai đoạn áp dụng (trước lời nhắc hoặc sau phản hồi) cùng siêu dữ liệu truy vết (nguồn, công cụ hoặc máy chủ MCP, ID tác nhân, phiên) để tương quan SOC và phát lại red-team trong tương lai. |   3    |    V    |

---

## C2.6 Giới hạn Tốc độ Đầu vào & Ngăn chặn Lạm dụng

Các nhà phát triển nên ngăn chặn việc lạm dụng, cạn kiệt tài nguyên và các cuộc tấn công tự động chống lại các hệ thống AI bằng cách giới hạn tốc độ đầu vào và phát hiện các mẫu sử dụng bất thường.

|   #   | Mô tả                                                                                                                                                                                                                                                                             | Cấp độ | Vai trò |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 2.6.1 | Xác minh rằng giới hạn tốc độ theo người dùng, theo IP, theo khóa API, theo tác nhân và theo phiên/nhiệm vụ được thực thi cho tất cả các điểm cuối đầu vào và công cụ/MCP.                                                                                                        |   1    |   D/V   |
| 2.6.2 | Xác nhận rằng giới hạn tốc độ đột biến và duy trì được điều chỉnh để ngăn chặn các cuộc tấn công DoS và tấn công dò tìm mật khẩu, đồng thời các ngân sách theo từng tác vụ (ví dụ như token, cuộc gọi công cụ/MCP, và chi phí) được thực thi cho các vòng lập kế hoạch của agent. |   2    |   D/V   |
| 2.6.3 | Xác minh rằng các mẫu sử dụng bất thường (ví dụ: các yêu cầu liên tiếp nhanh, tràn ngập đầu vào, các cuộc gọi công cụ/MCP thất bại lặp lại hoặc vòng lặp tác nhân đệ quy) kích hoạt các khối tự động hoặc sự leo thang.                                                           |   2    |   D/V   |
| 2.6.4 | Xác minh rằng các bản ghi phòng chống lạm dụng được lưu giữ và xem xét để phát hiện các mẫu tấn công mới nổi, cùng với siêu dữ liệu truy vết (nguồn, công cụ hoặc máy chủ MCP, ID đại lý, phiên).                                                                                 |   3    |    V    |

---

## C2.7 Xác thực đầu vào đa phương thức

Hệ thống AI nên bao gồm việc xác thực mạnh mẽ cho các đầu vào phi văn bản (hình ảnh, âm thanh, tệp tin) để ngăn chặn việc tiêm nhiễm, né tránh hoặc lạm dụng tài nguyên.

|   #   | Mô tả                                                                                                                                                                                                                                                                                                                                                                                                                  | Cấp độ | Vai trò |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 2.7.1 | Xác minh rằng tất cả các đầu vào không phải văn bản (hình ảnh, âm thanh, tệp tin) đều được kiểm tra hợp lệ về loại, kích thước và định dạng trước khi xử lý, và bất kỳ văn bản được trích xuất nào (từ hình ảnh sang văn bản hoặc giọng nói sang văn bản) cũng như bất kỳ hướng dẫn ẩn hoặc nhúng nào (siêu dữ liệu, các lớp, văn bản thay thế, bình luận) đều được xử lý như nguồn không đáng tin cậy theo mục 2.1.1. |   1    |    D    |
| 2.7.2 | Xác minh rằng các tệp được quét để phát hiện phần mềm độc hại và payload ẩn trong ảnh trước khi nhập dữ liệu, và mọi nội dung hoạt động (như script hoặc macro) được loại bỏ hoặc tệp được cách ly quarantine.                                                                                                                                                                                                         |   2    |   D/V   |
| 2.7.3 | Xác minh rằng đầu vào hình ảnh/âm thanh được kiểm tra các nhiễu loạn đối kháng hoặc các mẫu tấn công đã biết, và các phát hiện này kích hoạt cơ chế kiểm soát (chặn hoặc giảm khả năng) trước khi sử dụng mô hình.                                                                                                                                                                                                     |   2    |   D/V   |
| 2.7.4 | Xác nhận rằng các lỗi xác thực đầu vào đa phương thức được ghi lại và kích hoạt cảnh báo để điều tra, kèm theo siêu dữ liệu truy vết (nguồn, công cụ hoặc máy chủ MCP, ID đại lý, phiên).                                                                                                                                                                                                                              |   3    |    V    |
| 2.7.5 | Xác minh rằng phát hiện tấn công đa phương thức nhận diện các cuộc tấn công phối hợp bao gồm nhiều loại dữ liệu đầu vào khác nhau (ví dụ, payload ẩn trong ảnh kết hợp với chèn lệnh trong văn bản) thông qua các quy tắc tương quan và tạo cảnh báo, và các phát hiện được xác nhận sẽ bị chặn hoặc yêu cầu sự phê duyệt của con người tham gia (HITL).                                                               |   2    |   D/V   |
| 2.7.6 | Xác minh rằng các lỗi xác thực đa phương thức kích hoạt ghi nhật ký chi tiết bao gồm tất cả các phương thức đầu vào, kết quả xác thực và điểm mối đe dọa, cũng như siêu dữ liệu truy vết (nguồn, công cụ hoặc máy chủ MCP, ID đại lý, phiên làm việc).                                                                                                                                                                 |   3    |   D/V   |
---

## C2.8 Phát hiện mối đe dọa thích ứng theo thời gian thực

Các nhà phát triển nên sử dụng các hệ thống phát hiện mối đe dọa tiên tiến cho AI, có khả năng thích nghi với các mẫu tấn công mới và cung cấp bảo vệ thời gian thực bằng cách sử dụng kỹ thuật so khớp mẫu biên dịch.

|   #   | Mô tả                                                                                                                                                                                                                                                                                         | Cấp độ | Vai trò |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 2.8.1 | Xác minh rằng việc so khớp mẫu (ví dụ: regex đã biên dịch) hoạt động trên tất cả các đầu vào và đầu ra (bao gồm cả bề mặt công cụ/MCP) với tác động độ trễ tối thiểu.                                                                                                                         |   1    |   D/V   |
| 2.8.3 | Xác minh rằng các mô hình phát hiện thích ứng điều chỉnh độ nhạy dựa trên hoạt động tấn công gần đây và được cập nhật với các mẫu mới trong thời gian thực, đồng thời kích hoạt các phản ứng điều chỉnh rủi ro (ví dụ như vô hiệu hóa công cụ, thu nhỏ ngữ cảnh hoặc yêu cầu phê duyệt HITL). |   2    |   D/V   |
| 2.8.4 | Xác minh rằng độ chính xác của việc phát hiện được cải thiện thông qua phân tích ngữ cảnh của lịch sử người dùng, nguồn và hành vi phiên, bao gồm siêu dữ liệu dấu vết (nguồn, công cụ hoặc máy chủ MCP, ID đại lý, phiên).                                                                   |   3    |   D/V   |
| 2.8.5 | Xác minh rằng các chỉ số hiệu suất phát hiện (tỷ lệ phát hiện, tỷ lệ dương tính giả, độ trễ xử lý) được giám sát và tối ưu hóa liên tục, bao gồm thời gian để chặn và giai đoạn (trước lời nhắc/sau phản hồi).                                                                                |   3    |   D/V   |

## Tài liệu tham khảo

* [OWASP LLM01:2025 Prompt Injection](https://genai.owasp.org/llmrisk/llm01-prompt-injection/)
* [LLM Prompt Injection Prevention Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/LLM_Prompt_Injection_Prevention_Cheat_Sheet.html)
* [MITRE ATLAS : Adversarial Input Detection](https://atlas.mitre.org/mitigations/AML.M00150)
* [Mitigate jailbreaks and prompt injections](https://docs.anthropic.com/en/docs/test-and-evaluate/strengthen-guardrails/mitigate-jailbreaks)

