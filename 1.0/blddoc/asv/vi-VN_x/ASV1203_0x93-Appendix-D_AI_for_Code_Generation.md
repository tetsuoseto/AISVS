# Phụ lục D: Quản trị & Xác minh Mã hóa An toàn Hỗ trợ bởi AI

## Mục tiêu

Chương này định nghĩa các kiểm soát tổ chức cơ bản cho việc sử dụng an toàn và hiệu quả các công cụ mã hóa hỗ trợ AI trong quá trình phát triển phần mềm, đảm bảo bảo mật và khả năng truy xuất trong toàn bộ vòng đời phát triển phần mềm (SDLC).

---

## AD.1 Quy trình làm việc mã hóa an toàn được hỗ trợ bởi AI

Tích hợp công cụ AI vào vòng đời phát triển phần mềm bảo mật (SSDLC) của tổ chức mà không làm suy yếu các điểm kiểm soát an ninh hiện có.

|   #    | Mô tả                                                                                                                                                                           | Cấp độ | Vai trò |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| AD.1.1 | Xác minh rằng một quy trình làm việc đã được tài liệu hóa mô tả khi nào và cách các công cụ AI có thể tạo ra, tổ chức lại hoặc đánh giá mã.                                     |   1    |   D/V   |
| AD.1.2 | Xác nhận rằng quy trình làm việc phù hợp với từng giai đoạn của SSDLC (thiết kế, triển khai, rà soát mã, kiểm thử, triển khai).                                                 |   2    |    D    |
| AD.1.3 | Xác minh rằng các chỉ số (ví dụ, mật độ lỗ hổng, thời gian trung bình để phát hiện) được thu thập trên mã do AI tạo ra và so sánh với các chuẩn mực chỉ do con người thực hiện. |   3    |   D/V   |

---

## AD.2 Đánh giá Công cụ AI & Mô hình hóa Mối đe dọa

Đảm bảo các công cụ lập trình AI được đánh giá về khả năng bảo mật, rủi ro và tác động chuỗi cung ứng trước khi áp dụng.

|   #    | Mô tả                                                                                                                                                         | Cấp độ | Vai trò |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| AD.2.1 | Xác minh rằng mô hình mối đe dọa cho mỗi công cụ AI xác định được việc sử dụng sai, đảo ngược mô hình, rò rỉ dữ liệu và các rủi ro chuỗi phụ thuộc.           |   1    |   D/V   |
| AD.2.2 | Xác minh rằng đánh giá công cụ bao gồm phân tích tĩnh/động của bất kỳ thành phần cục bộ nào và đánh giá các điểm cuối SaaS (TLS, xác thực/ủy quyền, ghi log). |   2    |    D    |
| AD.2.3 | Xác minh rằng các đánh giá tuân theo một khung đã được công nhận và được thực hiện lại sau các thay đổi phiên bản lớn.                                        |   3    |   D/V   |

---

## AD.3 Quản lý Bảo mật Lời nhắc và Ngữ cảnh

Ngăn chặn rò rỉ bí mật, mã độc quyền và dữ liệu cá nhân khi xây dựng các lời nhắc hoặc ngữ cảnh cho các mô hình AI.

|   #    | Mô tả                                                                                                                                                      | Cấp độ | Vai trò |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| AD.3.1 | Xác nhận rằng hướng dẫn bằng văn bản cấm gửi bí mật, thông tin đăng nhập hoặc dữ liệu phân loại trong các lời nhắc.                                        |   1    |   D/V   |
| AD.3.2 | Xác minh rằng các biện pháp kiểm soát kỹ thuật (ẩn thông tin phía khách hàng, bộ lọc ngữ cảnh được duyệt) tự động loại bỏ các thông tin nhạy cảm.          |   2    |    D    |
| AD.3.3 | Xác minh rằng các câu lệnh và phản hồi được phân tách token, mã hóa khi truyền và lúc lưu trữ, và thời gian lưu giữ tuân thủ chính sách phân loại dữ liệu. |   3    |   D/V   |

---

## AD.4 Xác thực mã do AI tạo ra

Phát hiện và khắc phục các lỗ hổng bảo mật do đầu ra của AI tạo ra trước khi mã được hợp nhất hoặc triển khai.

|   #    | Mô tả                                                                                                                                                           | Cấp độ | Vai trò |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| AD.4.1 | Xác minh rằng mã do AI tạo ra luôn được kiểm tra bởi con người.                                                                                                 |   1    |   D/V   |
| AD.4.2 | Xác minh rằng các trình quét tự động (SAST/IAST/DAST) được chạy trên mọi pull request chứa mã do AI tạo ra và chặn việc gộp khi phát hiện các lỗi nghiêm trọng. |   2    |    D    |
| AD.4.3 | Xác minh rằng kiểm thử fuzz vi sai hoặc kiểm thử dựa trên thuộc tính chứng minh các hành vi quan trọng về bảo mật (ví dụ: xác thực đầu vào, logic ủy quyền).    |   3    |   D/V   |

---

## AD.5 Khả năng Giải thích và Truy xuất của Đề xuất Mã nguồn

Cung cấp cho các kiểm toán viên và nhà phát triển cái nhìn sâu sắc về lý do tại sao một đề xuất được đưa ra và cách nó phát triển.

|   #    | Mô tả                                                                                                                                                                                         | Cấp độ | Vai trò |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| AD.5.1 | Xác nhận rằng các cặp lời nhắc/phản hồi được ghi lại với các ID cam kết.                                                                                                                      |   1    |   D/V   |
| AD.5.2 | Xác minh rằng các nhà phát triển có thể hiển thị trích dẫn mô hình (đoạn trích huấn luyện, tài liệu) hỗ trợ một đề xuất.                                                                      |   2    |    D    |
| AD.5.3 | Xác minh rằng các báo cáo giải thích được lưu trữ cùng với các tài liệu thiết kế và được tham chiếu trong các đánh giá an ninh, đáp ứng các nguyên tắc truy xuất nguồn gốc của ISO/IEC 42001. |   3    |   D/V   |

---

## AD.6 Phản hồi liên tục & Tinh chỉnh mô hình

Cải thiện hiệu suất bảo mật mô hình theo thời gian trong khi ngăn chặn sự suy giảm tiêu cực.

|   #    | Mô tả                                                                                                                                                                                    | Cấp độ | Vai trò |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| AD.6.1 | Xác nhận rằng các nhà phát triển có thể đánh dấu các đề xuất không an toàn hoặc không tuân thủ, và rằng các đánh dấu này được theo dõi.                                                  |   1    |   D/V   |
| AD.6.2 | Xác minh rằng phản hồi tổng hợp được sử dụng để hỗ trợ điều chỉnh mịn định kỳ hoặc tạo ra dựa trên truy xuất với các kho mã hóa bảo mật đã được kiểm duyệt (ví dụ: Bảng gian lận OWASP). |   2    |    D    |
| AD.6.3 | Xác minh rằng bộ công cụ đánh giá vòng kín chạy các bài kiểm tra hồi quy sau mỗi lần tinh chỉnh; các chỉ số an ninh phải đạt hoặc vượt mức chuẩn trước đó trước khi triển khai.          |   3    |   D/V   |

---

### Tài liệu tham khảo

* [NIST AI Risk Management Framework 1.0](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements](https://www.iso.org/standard/81230.html)
* [OWASP Secure Coding Practices — Quick Reference Guide](https://owasp.org/www-project-secure-coding-practices-quick-reference-guide/)

