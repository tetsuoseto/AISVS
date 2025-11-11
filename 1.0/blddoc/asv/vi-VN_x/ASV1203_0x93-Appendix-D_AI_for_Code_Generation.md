# Phụ lục D: Quản trị và Kiểm tra Mã hóa An toàn Hỗ trợ bởi AI

## Mục tiêu

Chương này định nghĩa các kiểm soát tổ chức cơ bản cho việc sử dụng an toàn và hiệu quả các công cụ mã hóa hỗ trợ AI trong quá trình phát triển phần mềm, đảm bảo an ninh và khả năng truy xuất trong toàn bộ SDLC.

---

## AD.1 Quy trình làm việc mã hóa an toàn được hỗ trợ bởi AI

Tích hợp công cụ AI vào vòng đời phát triển phần mềm an toàn (SSDLC) của tổ chức mà không làm yếu các điểm kiểm soát an ninh hiện có.

|   #    | Mô tả                                                                                                                                                                   | Cấp độ | Vai trò |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| AD.1.1 | Xác minh rằng một quy trình làm việc được tài liệu hóa mô tả khi nào và như thế nào các công cụ AI có thể tạo ra, tái cấu trúc hoặc kiểm tra mã.                        |   1    |   D/V   |
| AD.1.2 | Xác minh rằng quy trình làm việc phù hợp với từng giai đoạn của SSDLC (thiết kế, triển khai, xem xét mã, kiểm thử, triển khai).                                         |   2    |    D    |
| AD.1.3 | Xác minh rằng các chỉ số (ví dụ: mật độ lỗ hổng, thời gian trung bình để phát hiện) được thu thập trên mã do AI tạo ra và so sánh với các chuẩn cơ sở chỉ có con người. |   3    |   D/V   |

---

## AD.2 Đánh giá Công cụ AI & Mô hình hóa Mối đe dọa

Đảm bảo các công cụ lập trình AI được đánh giá về khả năng bảo mật, rủi ro và tác động chuỗi cung ứng trước khi áp dụng.

|   #    | Mô tả                                                                                                                                                                  | Cấp độ | Vai trò |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| AD.2.1 | Xác minh rằng mô hình đe dọa cho từng công cụ AI nhận diện được việc sử dụng sai mục đích, đảo ngược mô hình, rò rỉ dữ liệu và các rủi ro chuỗi phụ thuộc.             |   1    |   D/V   |
| AD.2.2 | Xác minh rằng việc đánh giá công cụ bao gồm phân tích tĩnh/động của bất kỳ thành phần cục bộ nào và đánh giá các điểm cuối SaaS (TLS, xác thực/ủy quyền, ghi nhật ký). |   2    |    D    |
| AD.2.3 | Xác minh rằng các đánh giá tuân theo một khuôn khổ được công nhận và được thực hiện lại sau các thay đổi phiên bản lớn.                                                |   3    |   D/V   |

---

## AD.3 Quản lý Bảo mật Prompt & Ngữ cảnh

Ngăn ngừa rò rỉ bí mật, mã nguồn độc quyền và dữ liệu cá nhân khi xây dựng câu lệnh hoặc ngữ cảnh cho các mô hình AI.

|   #    | Mô tả                                                                                                                                                                            | Cấp độ | Vai trò |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| AD.3.1 | Xác nhận rằng hướng dẫn bằng văn bản cấm gửi bí mật, thông tin đăng nhập hoặc dữ liệu mật trong các lời nhắc.                                                                    |   1    |   D/V   |
| AD.3.2 | Xác minh rằng các biện pháp kiểm soát kỹ thuật (lọc phía khách hàng, bộ lọc ngữ cảnh được phê duyệt) tự động loại bỏ các dữ liệu nhạy cảm.                                       |   2    |    D    |
| AD.3.3 | Xác minh rằng các câu lệnh nhắc và phản hồi được phân tích thành token, mã hóa khi truyền và khi lưu trữ, và các khoảng thời gian lưu trữ tuân thủ chính sách phân loại dữ liệu. |   3    |   D/V   |

---

## AD.4 Xác thực mã do AI tạo ra

Phát hiện và khắc phục các lỗ hổng do đầu ra của AI gây ra trước khi mã được gộp hoặc triển khai.

|   #    | Mô tả                                                                                                                                                                  | Cấp độ | Vai trò |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| AD.4.1 | Xác minh rằng mã do AI tạo ra luôn được đưa vào quy trình đánh giá mã bởi con người.                                                                                   |   1    |   D/V   |
| AD.4.2 | Xác minh rằng các trình quét tự động (SAST/IAST/DAST) được chạy trên mọi yêu cầu kéo chứa mã do AI tạo ra và chặn việc hợp nhất khi phát hiện các vấn đề nghiêm trọng. |   2    |    D    |
| AD.4.3 | Xác minh rằng kiểm thử fuzz vi phân hoặc kiểm thử dựa trên thuộc tính chứng minh các hành vi quan trọng về bảo mật (ví dụ: xác thực đầu vào, logic ủy quyền).          |   3    |   D/V   |

---

## AD.5 Khả năng Giải thích và Truy xuất nguồn gốc của Gợi ý Mã code

Cung cấp cho các kiểm toán viên và nhà phát triển cái nhìn sâu sắc về lý do tại sao một đề xuất được đưa ra và cách nó phát triển.

|   #    | Mô tả                                                                                                                                                                                         | Cấp độ | Vai trò |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| AD.5.1 | Xác nhận rằng các cặp lời nhắc/phản hồi được ghi lại kèm theo các ID cam kết.                                                                                                                 |   1    |   D/V   |
| AD.5.2 | Xác minh rằng các nhà phát triển có thể hiển thị trích dẫn mô hình (đoạn trích đào tạo, tài liệu) hỗ trợ một đề xuất.                                                                         |   2    |    D    |
| AD.5.3 | Xác minh rằng các báo cáo giải thích được lưu trữ cùng với các hiện vật thiết kế và được tham chiếu trong các đánh giá bảo mật, đáp ứng các nguyên tắc truy xuất nguồn gốc của ISO/IEC 42001. |   3    |   D/V   |

---

## AD.6 Phản hồi liên tục & Tinh chỉnh mô hình

Cải thiện hiệu suất bảo mật mô hình theo thời gian đồng thời ngăn ngừa sự suy giảm tiêu cực.

|   #    | Mô tả                                                                                                                                                                                                     | Cấp độ | Vai trò |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| AD.6.1 | Xác minh rằng các nhà phát triển có thể đánh dấu các gợi ý không an toàn hoặc không tuân thủ, và các đánh dấu này được theo dõi.                                                                          |   1    |   D/V   |
| AD.6.2 | Xác minh rằng phản hồi tổng hợp được sử dụng để điều chỉnh tinh chỉnh định kỳ hoặc tạo ra kết quả tăng cường truy xuất với các kho dữ liệu mã hóa an toàn đã được kiểm duyệt (ví dụ, OWASP Cheat Sheets). |   2    |    D    |
| AD.6.3 | Xác minh rằng một hệ thống đánh giá vòng kín thực hiện các bài kiểm tra hồi quy sau mỗi lần tinh chỉnh; các chỉ số bảo mật phải đạt hoặc vượt mức cơ sở trước đó trước khi triển khai.                    |   3    |   D/V   |

---

### Tài liệu tham khảo

* [NIST AI Risk Management Framework 1.0](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements](https://www.iso.org/standard/81230.html)
* [OWASP Secure Coding Practices — Quick Reference Guide](https://owasp.org/www-project-secure-coding-practices-quick-reference-guide/)

