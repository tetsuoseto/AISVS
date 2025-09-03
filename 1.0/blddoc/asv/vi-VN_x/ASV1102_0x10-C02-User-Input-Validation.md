# C2 Kiểm tra đầu vào người dùng

## Mục tiêu kiểm soát

Việc xác thực đầu vào của người dùng một cách mạnh mẽ là lớp phòng thủ tuyến đầu chống lại một số cuộc tấn công gây hại nhất đối với hệ thống AI. Các cuộc tấn công tiêm prompt có thể ghi đè lên các chỉ dẫn của hệ thống, rò rỉ dữ liệu nhạy cảm, hoặc dẫn mô hình đến hành vi không được phép. Nếu không có các bộ lọc chuyên dụng và hệ phân cấp chỉ dẫn, nghiên cứu cho thấy các jailbreak "nhiều-shot" sẽ có hiệu quả khi khai thác cửa sổ ngữ cảnh rất dài. Ngoài ra, các cuộc tấn công nhiễu adversarial tinh vi—chẳng hạn như hoán đổi ký tự đồng dạng hoặc leetspeak—có thể âm thầm thay đổi các quyết định của mô hình.

---

## C2.1 Phòng ngừa tiêm Prompt

Tiêm nhiễm prompt là một trong những rủi ro hàng đầu đối với các hệ thống AI. Các biện pháp phòng thủ chống lại chiến thuật này kết hợp giữa các bộ lọc mẫu tĩnh, các bộ phân loại động và việc thực thi hệ phân cấp chỉ dẫn.

|   #   | Mô tả                                                                                                                                                                                                                              | Cấp độ | Vai trò |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 2.1.1 | Xác minh rằng các đầu vào của người dùng được quét thông qua một thư viện các mẫu tiêm prompt được cập nhật liên tục (từ khóa jailbreak, "bỏ qua trước đó", chuỗi đóng vai, các cuộc tấn công HTML/URL gián tiếp).                 |   1    |   D/V   |
| 2.1.2 | Xác minh rằng hệ thống thực thi một cấp độ ưu tiên chỉ dẫn mà các thông điệp từ hệ thống hoặc nhà phát triển ghi đè lên chỉ dẫn của người dùng, ngay cả khi cửa sổ ngữ cảnh được mở rộng.                                          |   1    |   D/V   |
| 2.1.3 | Xác nhận rằng các kiểm thử đánh giá đối kháng (ví dụ, các prompt 'many-shot' của Đội Đỏ) được thực hiện trước mỗi lần phát hành mô hình hoặc mẫu prompt, với ngưỡng tỷ lệ thành công và các rào chắn tự động để ngăn ngừa hồi quy. |   2    |   D/V   |
| 2.1.4 | Xác minh rằng các prompt phát sinh từ nội dung của bên thứ ba (trang web, tệp PDF, email) được làm sạch trong một ngữ cảnh phân tích cô lập trước khi được ghép nối vào prompt chính.                                              |   2    |    D    |
| 2.1.5 | Xác minh rằng tất cả cập nhật quy tắc lọc lời nhắc, các phiên bản mô hình phân loại và các thay đổi danh sách chặn được kiểm soát phiên bản và có thể kiểm tra được.                                                               |   3    |   D/V   |

---

## C2.2 Kháng đối với ví dụ đối kháng

Các mô hình Xử lý ngôn ngữ tự nhiên (NLP) vẫn còn dễ bị ảnh hưởng bởi các biến đổi tinh vi ở cấp ký tự hoặc từ, mà con người thường bỏ qua, nhưng các mô hình lại có xu hướng phân loại sai.

|   #   | Mô tả                                                                                                                                                                                                                | Cấp độ | Vai trò |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 2.2.1 | Hãy xác nhận rằng các bước chuẩn hóa đầu vào cơ bản (chuẩn hóa Unicode theo NFC, ánh xạ ký tự đồng dạng, loại bỏ khoảng trắng ở hai đầu) được thực thi trước khi phân tách từ.                                       |   1    |    D    |
| 2.2.2 | Xác nhận rằng hệ thống phát hiện bất thường thống kê sẽ đánh dấu các đầu vào có khoảng cách chỉnh sửa so với chuẩn ngôn ngữ cao bất thường, lặp lại các token quá mức, hoặc khoảng cách nhúng bất thường.            |   2    |   D/V   |
| 2.2.3 | Xác nhận rằng quy trình suy diễn hỗ trợ các biến thể mô hình được củng cố bằng huấn luyện đối kháng–hardened hoặc các lớp phòng thủ (ví dụ: ngẫu nhiên hóa, distillation phòng thủ) cho các điểm cuối có rủi ro cao. |   2    |    D    |
| 2.2.4 | Xác minh rằng các đầu vào đối kháng bị nghi ngờ được cách ly, ghi lại với đầy đủ payload (sau khi đã loại bỏ PII).                                                                                                   |   2    |    V    |
| 2.2.5 | Xác nhận rằng các thước đo độ bền (tỷ lệ thành công của các bộ thử nghiệm tấn công đã biết) được theo dõi theo thời gian và các hồi quy sẽ kích hoạt một rào chắn phát hành.                                         |   3    |   D/V   |

---

## C2.3 Xác thực lược đồ, kiểu và độ dài

Các cuộc tấn công AI có đầu vào bị định dạng sai hoặc quá lớn có thể gây lỗi phân tích cú pháp, rò rỉ prompt giữa các trường, và kiệt quệ tài nguyên.  Việc tuân thủ nghiêm ngặt schema cũng là điều kiện tiên quyết khi thực hiện các cuộc gọi công cụ có tính xác định.

|   #   | Mô tả                                                                                                                                                                                       | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 2.3.1 | Xác minh rằng mọi endpoint API hoặc hàm gọi đều định nghĩa một sơ đồ đầu vào rõ ràng (JSON Schema, Protobuf hoặc tương đương đa chế độ) và các đầu vào được xác thực trước khi ghép prompt. |   1    |    D    |
| 2.3.2 | Xác minh rằng các đầu vào vượt quá giới hạn tối đa về số token hoặc byte sẽ bị từ chối bằng một lỗi an toàn và không bao giờ bị cắt bớt một cách im lặng.                                   |   1    |   D/V   |
| 2.3.3 | Xác minh rằng các kiểm tra kiểu (ví dụ: phạm vi số, giá trị enum, kiểu MIME cho hình ảnh và âm thanh) được thực thi ở phía máy chủ, chứ không chỉ ở mã phía máy khách.                      |   2    |   D/V   |
| 2.3.4 | Xác minh rằng các trình xác thực ngữ nghĩa (ví dụ: JSON Schema) chạy với thời gian cố định để ngăn chặn tấn công từ chối dịch vụ có tính thuật toán.                                        |   2    |    D    |
| 2.3.5 | Xác minh rằng các lỗi kiểm tra tính hợp lệ được ghi lại với các đoạn payload đã bị che và các mã lỗi rõ ràng nhằm hỗ trợ phân loại sự cố an ninh.                                           |   3    |    V    |

---

## C2.4 Kiểm tra Nội dung và Chính sách

Các nhà phát triển nên có thể phát hiện các lời nhắc hợp lệ về cú pháp đang yêu cầu nội dung bị cấm (ví dụ như hướng dẫn phi pháp, ngôn ngữ kích động thù ghét và văn bản có bản quyền) rồi ngăn chúng lan truyền.

|   #   | Mô tả                                                                                                                                                                                                                                    | Cấp độ | Vai trò |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 2.4.1 | Xác minh rằng một trình phân loại nội dung (zero-shot hoặc được tinh chỉnh) đánh giá mọi đầu vào về bạo lực, tự làm hại bản thân, nội dung thù địch, nội dung tình dục và các yêu cầu bất hợp pháp, với các ngưỡng có thể cấu hình được. |   1    |    D    |
| 2.4.2 | Xác minh rằng những đầu vào vi phạm chính sách sẽ nhận được các từ chối được chuẩn hóa hoặc các đáp ứng an toàn để chúng không lan ra tới các lời gọi LLM ở phía sau.                                                                    |   1    |   D/V   |
| 2.4.3 | Xác nhận rằng mô hình sàng lọc hoặc bộ quy tắc được huấn luyện lại và cập nhật ít nhất mỗi quý một lần, đồng thời tích hợp các mẫu jailbreak hoặc né tránh chính sách mới được quan sát.                                                 |   2    |    D    |
| 2.4.4 | Xác nhận rằng quá trình sàng lọc tuân thủ các chính sách dành cho người dùng (tuổi tác, các hạn chế pháp lý theo khu vực) được giải quyết bằng các quy tắc dựa trên thuộc tính tại thời điểm yêu cầu.                                    |   2    |    D    |
| 2.4.5 | Xác nhận rằng các nhật ký sàng lọc bao gồm điểm tin cậy của bộ phân loại và nhãn danh mục chính sách để tương quan với SOC và phục vụ cho việc phát lại của đội đỏ trong tương lai.                                                      |   3    |    V    |

---

## C2.5 Giới hạn tốc độ đầu vào và phòng ngừa lạm dụng

Các nhà phát triển nên ngăn chặn lạm dụng, tiêu hao tài nguyên và các cuộc tấn công tự động nhắm vào các hệ thống AI bằng cách giới hạn lưu lượng đầu vào và phát hiện các mẫu sử dụng bất thường.

|   #   | Mô tả                                                                                                                                                                             | Cấp độ | Vai trò |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 2.5.1 | Xác nhận rằng các giới hạn tần suất theo người dùng, theo IP và theo khóa API được áp dụng cho mọi điểm đầu vào.                                                                  |   1    |   D/V   |
| 2.5.2 | Xác minh rằng các giới hạn lưu lượng đột biến (burst) và lưu lượng duy trì (sustained) được điều chỉnh để ngăn chặn DoS và các cuộc tấn công brute-force (thử mật khẩu liên tục). |   2    |   D/V   |
| 2.5.3 | Xác nhận rằng các mẫu sử dụng bất thường (ví dụ: yêu cầu liên tục với tần suất cao, gửi dữ liệu đầu vào quá mức) kích hoạt các biện pháp chặn tự động hoặc cơ chế leo thang.      |   2    |   D/V   |
| 2.5.4 | Xác nhận rằng các nhật ký phòng ngừa lạm dụng được lưu giữ và xem xét nhằm phát hiện các mẫu tấn công đang nổi lên.                                                               |   3    |    V    |

---

## C2.6 Xác thực đầu vào đa phương tiện

Hệ thống AI nên thực hiện xác thực nghiêm ngặt đối với các đầu vào không phải văn bản (hình ảnh, âm thanh, tệp) để ngăn chặn tiêm mã, né tránh hoặc lạm dụng tài nguyên.

|   #   | Mô tả                                                                                                                                         | Cấp độ | Vai trò |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 2.6.1 | Xác minh rằng tất cả các đầu vào không phải văn bản (hình ảnh, âm thanh, tệp) được xác thực về loại, kích thước và định dạng trước khi xử lý. |   1    |    D    |
| 2.6.2 | Xác minh rằng các tệp được quét để phát hiện phần mềm độc hại và payload ẩn giấu trước khi tiếp nhận.                                         |   2    |   D/V   |
| 2.6.3 | Xác minh rằng đầu vào hình ảnh và âm thanh được kiểm tra để phát hiện nhiễu adversarial hoặc các mẫu tấn công đã biết.                        |   2    |   D/V   |
| 2.6.4 | Xác minh rằng các lỗi xác thực đầu vào đa chế độ được ghi lại và kích hoạt cảnh báo để điều tra.                                              |   3    |    V    |

---

## C2.7 Nguồn gốc đầu vào và Ghi nhận

Các hệ thống AI nên hỗ trợ kiểm toán, theo dõi hành vi lạm dụng và tuân thủ bằng cách giám sát và gắn nhãn nguồn gốc của mọi đầu vào từ người dùng.

|   #   | Mô tả                                                                                                                                                              | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 2.7.1 | Xác nhận rằng mọi đầu vào của người dùng được gắn nhãn bằng siêu dữ liệu (ID người dùng, phiên, nguồn, dấu thời gian, địa chỉ IP) tại thời điểm tiếp nhận dữ liệu. |   1    |   D/V   |
| 2.7.2 | Xác nhận rằng siêu dữ liệu nguồn gốc được giữ lại và có thể kiểm toán cho mọi đầu vào đã được xử lý.                                                               |   2    |   D/V   |
| 2.7.3 | Xác minh rằng các nguồn đầu vào bất thường hoặc không đáng tin cậy được gắn cờ và chịu sự kiểm tra tăng cường hoặc bị chặn.                                        |   2    |   D/V   |

---

## C2.8 Phát hiện mối đe dọa thích ứng theo thời gian thực

Các nhà phát triển nên sử dụng các hệ thống phát hiện mối đe dọa tiên tiến cho AI có khả năng thích nghi với các mẫu tấn công mới và cung cấp bảo vệ thời gian thực bằng cơ chế khớp mẫu được biên dịch.

|   #   | Mô tả                                                                                                                                                                                                  | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 2.8.1 | Xác minh rằng các mẫu phát hiện mối đe dọa được biên dịch thành các động cơ regex tối ưu để lọc thời gian thực với hiệu suất cao và độ trễ tối thiểu.                                                  |   1    |   D/V   |
| 2.8.2 | Xác nhận rằng các hệ thống phát hiện mối đe dọa duy trì các thư viện mẫu riêng biệt cho các danh mục mối đe dọa khác nhau (tiêm prompt, nội dung có hại, dữ liệu nhạy cảm, lệnh hệ thống).             |   1    |   D/V   |
| 2.8.3 | Xác minh rằng phát hiện mối đe dọa thích ứng tích hợp các mô hình học máy cập nhật độ nhạy đối với mối đe dọa dựa trên tần suất tấn công và tỷ lệ thành công.                                          |   2    |   D/V   |
| 2.8.4 | Xác nhận rằng các nguồn cấp thông tin mối đe dọa thời gian thực tự động cập nhật thư viện mẫu với các chữ ký tấn công mới và IOCs (Indicators of Compromise).                                          |   2    |   D/V   |
| 2.8.5 | Xác minh rằng tỷ lệ dương tính giả trong phát hiện mối đe dọa được giám sát liên tục và độ đặc hiệu của mẫu được tự động tinh chỉnh để tối thiểu hóa sự can thiệp vào các trường hợp sử dụng hợp pháp. |   3    |   D/V   |
| 2.8.6 | Xác nhận rằng phân tích mối đe dọa dựa trên ngữ cảnh xem xét nguồn đầu vào, mẫu hành vi người dùng và lịch sử phiên để cải thiện độ chính xác của việc phát hiện.                                      |   3    |   D/V   |
| 2.8.7 | Xác minh rằng các chỉ số hiệu suất phát hiện mối đe dọa (tỷ lệ phát hiện, độ trễ xử lý, mức sử dụng tài nguyên) được giám sát và tối ưu hóa trong real-time.                                           |   3    |   D/V   |

---

## C2.9 Dòng xử lý kiểm tra bảo mật đa phương thức

Các nhà phát triển nên cung cấp kiểm tra bảo mật cho các chế độ đầu vào AI như văn bản, hình ảnh, âm thanh và các dạng đầu vào AI khác, với các loại phát hiện mối đe dọa cụ thể và cô lập tài nguyên.

|   #   | Mô tả                                                                                                                                                                                                                                                                             | Cấp độ | Vai trò |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 2.9.1 | Xác nhận rằng mỗi loại đầu vào có các trình xác thực bảo mật riêng biệt với các mẫu đe dọa được ghi nhận và tài liệu hoá (văn bản: tiêm prompt, hình ảnh: steganography, âm thanh: tấn công spectrogram) và ngưỡng phát hiện.                                                     |   1    |   D/V   |
| 2.9.2 | Xác minh rằng đầu vào đa chế độ được xử lý trong các sandbox cô lập với các giới hạn tài nguyên được định nghĩa (bộ nhớ, CPU, thời gian xử lý) riêng cho từng loại chế độ và được ghi nhận trong các chính sách bảo mật.                                                          |   2    |   D/V   |
| 2.9.3 | Xác nhận rằng phát hiện tấn công chéo (cross-modal) có thể nhận diện các cuộc tấn công phối hợp trải dài trên nhiều loại đầu vào, ví dụ như payload steganographic trong hình ảnh kết hợp với tiêm prompt trong văn bản, thông qua các quy tắc tương quan và cơ chế tạo cảnh báo. |   2    |   D/V   |
| 2.9.4 | Xác nhận rằng các thất bại xác thực đa chế độ kích hoạt ghi log chi tiết, bao gồm tất cả các chế độ đầu vào, kết quả xác thực, điểm đe dọa và phân tích tương quan với các định dạng log có cấu trúc cho việc tích hợp SIEM.                                                      |   3    |   D/V   |
| 2.9.5 | Xác minh rằng các bộ phân loại nội dung dành cho từng modality được cập nhật theo lịch trình được ghi nhận (tối thiểu mỗi quý) với các mẫu mối đe dọa mới, các ví dụ đối kháng, và các chuẩn hiệu suất được duy trì ở ngưỡng cơ sở ở mức cao hơn.                                 |   3    |   D/V   |

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

