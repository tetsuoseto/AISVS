# Xác thực đầu vào người dùng C2

## Mục tiêu Kiểm soát

Xác thực đầu vào của người dùng một cách chắc chắn là biện pháp phòng thủ hàng đầu chống lại một số cuộc tấn công gây tổn hại nghiêm trọng nhất đối với các hệ thống AI. Các cuộc tấn công tiêm nhiễm prompt có thể ghi đè các hướng dẫn của hệ thống, làm lộ dữ liệu nhạy cảm hoặc điều khiển mô hình theo hành vi không được phép. Trừ khi có bộ lọc chuyên dụng và các cấp bậc hướng dẫn được thiết lập, các nghiên cứu cho thấy các jailbreak "đa lần" khai thác cửa sổ ngữ cảnh rất dài sẽ có hiệu quả. Ngoài ra, các cuộc tấn công làm nhiễu nhương tinh vi—như thay đổi homoglyph hoặc leetspeak—có thể lặng lẽ thay đổi các quyết định của mô hình.

---

## Phòng thủ tiêm nhắc lệnh C2.1

Tấn công tiêm nhiễm lệnh (prompt injection) là một trong những rủi ro hàng đầu đối với các hệ thống AI. Các biện pháp phòng chống chiến thuật này sử dụng sự kết hợp của bộ lọc mẫu tĩnh, bộ phân loại động và việc thi hành cấu trúc hướng dẫn.

|   #   | Mô tả                                                                                                                                                                                                                                                  | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 2.1.1 | Xác minh rằng các dữ liệu nhập của người dùng được kiểm tra dựa trên một thư viện các mẫu tấn công prompt injection đã được cập nhật liên tục (từ khóa jailbreak, "bỏ qua nội dung trước", chuỗi nhập vai, các cuộc tấn công gián tiếp qua HTML/URL).  |   1    |   D/V   |
| 2.1.2 | Xác minh rằng hệ thống thực thi một cấp bậc hướng dẫn trong đó các tin nhắn của hệ thống hoặc nhà phát triển ghi đè lên các hướng dẫn của người dùng, ngay cả sau khi mở rộng cửa sổ ngữ cảnh.                                                         |   1    |   D/V   |
| 2.1.3 | Xác nhận rằng các bài kiểm tra đánh giá đối kháng (ví dụ, các câu lệnh "many-shot" của Đội Đỏ) được thực hiện trước mỗi lần phát hành mô hình hoặc mẫu câu lệnh, với các ngưỡng tỷ lệ thành công và các bộ chặn tự động cho các sự suy giảm hiệu suất. |   2    |   D/V   |
| 2.1.4 | Xác minh rằng các lệnh nhắc xuất phát từ nội dung bên thứ ba (trang web, PDF, email) được làm sạch trong một ngữ cảnh phân tích tách biệt trước khi được nối vào lệnh nhắc chính.                                                                      |   2    |    D    |
| 2.1.5 | Xác minh rằng tất cả các cập nhật quy tắc lọc câu lệnh, phiên bản mô hình phân loại và các thay đổi trong danh sách chặn đều được kiểm soát phiên bản và có thể kiểm tra được.                                                                         |   3    |   D/V   |

---

## C2.2 Kháng lại Ví dụ Đối kháng

Các mô hình Xử lý Ngôn ngữ Tự nhiên (NLP) vẫn dễ bị tổn thương bởi những biến động tinh vi ở cấp độ ký tự hoặc từ mà con người thường bỏ qua nhưng các mô hình lại có xu hướng phân loại sai.

|   #   | Mô tả                                                                                                                                                                                                               | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 2.2.1 | Xác minh rằng các bước chuẩn hoá đầu vào cơ bản (Unicode NFC, ánh xạ homoglyph, cắt bớt khoảng trắng) được thực hiện trước khi phân tách từ khóa.                                                                   |   1    |    D    |
| 2.2.2 | Xác minh rằng phát hiện bất thường thống kê đánh dấu các đầu vào có khoảng cách chỉnh sửa bất thường cao so với chuẩn ngôn ngữ, các token lặp lại quá mức hoặc khoảng cách embedding bất thường.                    |   2    |   D/V   |
| 2.2.3 | Xác nhận rằng chuỗi xử lý suy luận hỗ trợ các biến thể mô hình được củng cố bằng huấn luyện đối kháng tùy chọn hoặc các lớp phòng thủ (ví dụ: ngẫu nhiên hóa, chưng cất phòng thủ) cho các điểm cuối có rủi ro cao. |   2    |    D    |
| 2.2.4 | Xác minh rằng các đầu vào nghi ngờ là tấn công đối kháng được cách ly, ghi lại với toàn bộ nội dung (sau khi đã loại bỏ thông tin cá nhân nhận dạng).                                                               |   2    |    V    |
| 2.2.5 | Xác minh rằng các chỉ số độ bền (tỷ lệ thành công của các bộ tấn công đã biết) được theo dõi theo thời gian và các suy giảm kích hoạt một chặn phát hành.                                                           |   3    |   D/V   |

---

## C2.3 Xác thực Sơ đồ, Loại & Độ dài

Các cuộc tấn công AI với đầu vào bị sai định dạng hoặc quá kích thước có thể gây ra lỗi phân tích cú pháp, tràn lệnh qua các trường và cạn kiệt tài nguyên. Việc thi hành nghiêm ngặt sơ đồ cũng là một yêu cầu bắt buộc khi thực hiện các cuộc gọi công cụ xác định.

|   #   | Mô tả                                                                                                                                                                                                     | Cấp độ | Vai trò |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 2.3.1 | Xác minh rằng mọi điểm cuối gọi API hoặc hàm đều định nghĩa một sơ đồ đầu vào rõ ràng (JSON Schema, Protobuf hoặc tương đương đa phương thức) và rằng các đầu vào được xác thực trước khi lắp ráp prompt. |   1    |    D    |
| 2.3.2 | Xác minh rằng các đầu vào vượt quá giới hạn tối đa về token hoặc byte sẽ bị từ chối với lỗi an toàn và không bao giờ bị cắt ngắn một cách im lặng.                                                        |   1    |   D/V   |
| 2.3.3 | Xác minh rằng việc kiểm tra kiểu (ví dụ: phạm vi số, giá trị enum, loại MIME cho hình ảnh/âm thanh) được thực thi phía máy chủ, không chỉ trong mã phía khách.                                            |   2    |   D/V   |
| 2.3.4 | Xác minh rằng các bộ kiểm tra ngữ nghĩa (ví dụ: JSON Schema) hoạt động trong thời gian không đổi để ngăn ngừa tấn công từ chối dịch vụ theo thuật toán (DoS).                                             |   2    |    D    |
| 2.3.5 | Xác minh rằng các lỗi xác thực được ghi lại với các đoạn payload đã được che mờ và mã lỗi rõ ràng để hỗ trợ phân loại sự cố bảo mật.                                                                      |   3    |    V    |

---

## C2.4 Kiểm tra Nội dung & Chính sách

Các nhà phát triển nên có khả năng phát hiện các lời nhắc hợp lệ về mặt cú pháp nhưng yêu cầu nội dung bị cấm (chẳng hạn như hướng dẫn bất hợp pháp, ngôn ngữ thù địch và văn bản có bản quyền), sau đó ngăn chặn chúng lan truyền.

|   #   | Mô tả                                                                                                                                                                                                           | Cấp độ | Vai trò |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 2.4.1 | Xác minh rằng bộ phân loại nội dung (không huấn luyện hoặc đã tinh chỉnh) đánh giá mọi đầu vào về bạo lực, tự làm hại, thù địch, nội dung tình dục và các yêu cầu bất hợp pháp, với các ngưỡng có thể cấu hình. |   1    |    D    |
| 2.4.2 | Xác minh rằng các đầu vào vi phạm chính sách sẽ nhận được từ chối chuẩn hóa hoặc hoàn thành an toàn để chúng không lan truyền đến các cuộc gọi LLM tiếp theo.                                                   |   1    |   D/V   |
| 2.4.3 | Xác minh rằng mô hình sàng lọc hoặc bộ quy tắc được đào tạo lại/cập nhật ít nhất mỗi quý, kết hợp các mẫu vượt rào hoặc bỏ qua chính sách mới được quan sát.                                                    |   2    |    D    |
| 2.4.4 | Xác minh rằng việc sàng lọc tuân thủ các chính sách riêng của người dùng (độ tuổi, các hạn chế pháp lý vùng) thông qua các quy tắc dựa trên thuộc tính được giải quyết tại thời điểm yêu cầu.                   |   2    |    D    |
| 2.4.5 | Xác minh rằng các nhật ký sàng lọc bao gồm điểm độ tin cậy của bộ phân loại và các thẻ danh mục chính sách cho việc tương quan SOC và phát lại đội đỏ trong tương lai.                                          |   3    |    V    |

---

## C2.5 Giới Hạn Tốc Độ Nhập Liệu & Ngăn Ngừa Lạm Dụng

Các nhà phát triển nên ngăn chặn lạm dụng, cạn kiệt tài nguyên và các cuộc tấn công tự động đối với các hệ thống AI bằng cách giới hạn tốc độ đầu vào và phát hiện các mô hình sử dụng bất thường.

|   #   | Mô tả                                                                                                                                                   | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 2.5.1 | Xác minh rằng giới hạn tốc độ theo người dùng, theo IP và theo khóa API được thực thi cho tất cả các điểm đầu vào.                                      |   1    |   D/V   |
| 2.5.2 | Xác minh rằng các giới hạn tốc độ theo đợt và liên tục được điều chỉnh để ngăn chặn các cuộc tấn công DoS và tấn công dò mật khẩu.                      |   2    |   D/V   |
| 2.5.3 | Xác minh rằng các kiểu sử dụng bất thường (ví dụ, các yêu cầu dồn dập nhanh, nhập liệu quá tải) kích hoạt các chặn tự động hoặc các biện pháp nâng cao. |   2    |   D/V   |
| 2.5.4 | Xác minh rằng các bản ghi phòng ngừa lạm dụng được lưu giữ và xem xét để phát hiện các mô hình tấn công mới nổi.                                        |   3    |    V    |

---

## C2.6 Xác thực Đầu vào Đa phương thức

Hệ thống AI nên bao gồm việc kiểm tra xác thực mạnh mẽ cho các đầu vào phi văn bản (hình ảnh, âm thanh, tệp tin) để ngăn chặn việc chèn, né tránh, hoặc lạm dụng tài nguyên.

|   #   | Mô tả                                                                                                                                         | Cấp độ | Vai trò |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 2.6.1 | Xác minh rằng tất cả các đầu vào không phải văn bản (hình ảnh, âm thanh, tệp) được kiểm tra về loại, kích thước và định dạng trước khi xử lý. |   1    |    D    |
| 2.6.2 | Xác minh rằng các tệp được quét để phát hiện phần mềm độc hại và payload ẩn trước khi nhập liệu.                                              |   2    |   D/V   |
| 2.6.3 | Xác minh rằng các đầu vào hình ảnh/âm thanh được kiểm tra các nhiễu loạn đối kháng hoặc các mẫu tấn công đã biết.                             |   2    |   D/V   |
| 2.6.4 | Xác minh rằng các lỗi xác thực đầu vào đa phương thức được ghi lại và kích hoạt cảnh báo để điều tra.                                         |   3    |    V    |

---

## C2.7 Nguồn gốc và Ghi công Đầu vào

Hệ thống AI nên hỗ trợ kiểm toán, theo dõi lạm dụng và tuân thủ bằng cách giám sát và gắn nhãn nguồn gốc của tất cả các đầu vào từ người dùng.

|   #   | Mô tả                                                                                                                                                                  | Cấp độ | Vai trò |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 2.7.1 | Xác minh rằng tất cả các đầu vào của người dùng đều được gắn thẻ với siêu dữ liệu (ID người dùng, phiên, nguồn, dấu thời gian, địa chỉ IP) tại thời điểm nhập dữ liệu. |   1    |   D/V   |
| 2.7.2 | Xác minh rằng siêu dữ liệu nguồn gốc được giữ lại và có thể kiểm tra được cho tất cả các đầu vào đã xử lý.                                                             |   2    |   D/V   |
| 2.7.3 | Xác minh rằng các nguồn đầu vào bất thường hoặc không đáng tin cậy được đánh dấu và chịu sự kiểm tra chặt chẽ hơn hoặc bị chặn.                                        |   2    |   D/V   |

---

## C2.8 Phát hiện Mối đe dọa Thích ứng Thời gian Thực

Các nhà phát triển nên sử dụng các hệ thống phát hiện mối đe dọa tiên tiến cho AI, có khả năng thích ứng với các mẫu tấn công mới và cung cấp bảo vệ thời gian thực bằng cách so khớp mẫu được biên dịch.

|   #   | Mô tả                                                                                                                                                                                                | Cấp độ | Vai trò |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 2.8.1 | Xác minh rằng các mẫu phát hiện mối đe dọa được biên dịch thành các công cụ regex được tối ưu hóa để lọc thời gian thực hiệu suất cao với tác động độ trễ tối thiểu.                                 |   1    |   D/V   |
| 2.8.2 | Xác minh rằng các hệ thống phát hiện mối đe dọa duy trì các thư viện mẫu riêng biệt cho các loại mối đe dọa khác nhau (chèn lệnh gợi ý, nội dung có hại, dữ liệu nhạy cảm, lệnh hệ thống).           |   1    |   D/V   |
| 2.8.3 | Xác nhận rằng phát hiện mối đe dọa thích ứng bao gồm các mô hình học máy cập nhật độ nhạy cảm của mối đe dọa dựa trên tần suất và tỷ lệ thành công của các cuộc tấn công.                            |   2    |   D/V   |
| 2.8.4 | Xác minh rằng các nguồn cấp dữ liệu tình báo mối đe dọa thời gian thực tự động cập nhật các thư viện mẫu với các chữ ký tấn công mới và các chỉ số xâm nhập (IOCs).                                  |   2    |   D/V   |
| 2.8.5 | Xác minh rằng tỷ lệ báo động giả của việc phát hiện mối đe dọa được giám sát liên tục và độ đặc hiệu của mẫu được điều chỉnh tự động nhằm giảm thiểu sự can thiệp vào các trường hợp sử dụng hợp lệ. |   3    |   D/V   |
| 2.8.6 | Xác minh rằng phân tích mối đe dọa theo ngữ cảnh xem xét nguồn đầu vào, các mẫu hành vi người dùng và lịch sử phiên làm việc để cải thiện độ chính xác trong phát hiện.                              |   3    |   D/V   |
| 2.8.7 | Xác minh rằng các chỉ số hiệu suất phát hiện mối đe dọa (tỷ lệ phát hiện, độ trễ xử lý, sử dụng tài nguyên) được giám sát và tối ưu hóa theo thời gian thực.                                         |   3    |   D/V   |

---

## C2.9 Quy trình xác thực bảo mật đa phương thức

Các nhà phát triển nên cung cấp xác thực bảo mật cho văn bản, hình ảnh, âm thanh và các phương thức đầu vào AI khác với các loại phát hiện mối đe dọa cụ thể và cách ly tài nguyên.

|   #   | Mô tả                                                                                                                                                                                                                                                  | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 2.9.1 | Xác minh rằng mỗi loại hình đầu vào đều có các bộ kiểm tra bảo mật riêng biệt với các mẫu mối đe dọa được tài liệu hóa (văn bản: tiêm lệnh nhắc, hình ảnh: ẩn tin, âm thanh: các cuộc tấn công phổ quang) và ngưỡng phát hiện.                         |   1    |   D/V   |
| 2.9.2 | Xác minh rằng các đầu vào đa phương thức được xử lý trong các sandbox riêng biệt với giới hạn tài nguyên đã định rõ (bộ nhớ, CPU, thời gian xử lý) cụ thể cho từng loại phương thức và được ghi trong các chính sách bảo mật.                          |   2    |   D/V   |
| 2.9.3 | Xác nhận rằng việc phát hiện tấn công đa phương thức nhận diện các cuộc tấn công phối hợp trên nhiều loại đầu vào khác nhau (ví dụ: payload giấu dữ liệu trong ảnh kết hợp với chèn prompt trong văn bản) bằng các quy tắc tương quan và tạo cảnh báo. |   2    |   D/V   |
| 2.9.4 | Xác minh rằng các lỗi xác thực đa phương thức kích hoạt ghi nhật ký chi tiết bao gồm tất cả các phương thức đầu vào, kết quả xác thực, điểm số mối đe dọa và phân tích tương quan với các định dạng nhật ký có cấu trúc để tích hợp SIEM.              |   3    |   D/V   |
| 2.9.5 | Xác minh rằng các bộ phân loại nội dung đặc thù theo phương thức được cập nhật theo lịch trình đã được ghi chép (ít nhất hàng quý) với các mẫu mối đe dọa mới, các ví dụ đối kháng và các tiêu chuẩn hiệu suất được duy trì trên ngưỡng cơ sở.         |   3    |   D/V   |

---

## Tài liệu tham khảo

* [LLM01:2025 Prompt Injection – OWASP Top 10 for LLM & Generative AI Security](https://genai.owasp.org/llmrisk/llm01-prompt-injection/)
* [Generative AI's Biggest Security Flaw Is Not Easy to Fix](https://www.wired.com/story/generative-ai-prompt-injection-hacking)
* [Many-shot jailbreaking \ Anthropic](https://www.anthropic.com/research/many-shot-jailbreaking)
* [$PDF$ OpenAI GPT-4.5 System Card](https://cdn.openai.com/gpt-4-5-system-card-2272025.pdf)
* [Notebook for the CheckThat Lab at CLEF 2024](https://ceur-ws.org/Vol-3740/paper-53.pdf)
* [Mitigate jailbreaks and prompt injections – Anthropic](https://docs.anthropic.com/en/docs/test-and-evaluate/strengthen-guardrails/mitigate-jailbreaks)
* [Chapter 3 MITRE ATT\&CK – Adversarial Model Analysis](https://ama.drwhy.ai/mitre-attck.html)
* [OWASP Top 10 for LLM Applications 2025 – WorldTech IT](https://wtit.com/blog/2025/04/17/owasp-top-10-for-llm-applications-2025/)
* [OWASP Machine Learning Security Top Ten](https://owasp.org/www-project-machine-learning-security-top-10/)
* [Few words about AI Security – Jussi Metso](https://www.jussimetso.com/index.php/2024/09/28/few-words-about-ai-security/)
* [How To Ensure LLM Output Adheres to a JSON Schema | Modelmetry](https://modelmetry.com/blog/how-to-ensure-llm-output-adheres-to-a-json-schema)
* [Easily enforcing valid JSON schema following – API](https://community.openai.com/t/feature-request-function-calling-easily-enforcing-valid-json-schema-following/263515?utm_source)
* [AI Safety + Cybersecurity R\&D Tracker – Fairly AI](https://www.fairly.ai/blog/ai-cybersecurity-tracker)
* [Anthropic makes 'jailbreak' advance to stop AI models producing harmful results](https://www.ft.com/content/cf11ebd8-aa0b-4ed4-945b-a5d4401d186e)
* [Pattern matching filter rules - IBM](https://www.ibm.com/docs/ssw_aix_71/security/intrusion_pattern_matching_filter_rules.html)
* [Real-time Threat Detection](https://www.darktrace.com/cyber-ai-glossary/real-time-threat-detection)

