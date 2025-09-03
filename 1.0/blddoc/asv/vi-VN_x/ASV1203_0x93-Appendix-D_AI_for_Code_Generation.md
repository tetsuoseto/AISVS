# Phụ lục D: Quản trị và xác thực lập trình an toàn được AI hỗ trợ

## Mục tiêu

Chương này định nghĩa các kiểm soát tổ chức cơ bản cho việc sử dụng an toàn và hiệu quả các công cụ viết mã được hỗ trợ bởi AI trong quá trình phát triển phần mềm, nhằm đảm bảo an ninh và tính truy vết xuyên suốt SDLC.

---

## AD.1 Quy trình Lập trình an toàn được AI hỗ trợ

Tích hợp các công cụ AI vào vòng đời phát triển phần mềm an toàn của tổ chức (SSDLC) mà không làm suy yếu các điểm kiểm tra bảo mật hiện có.

|   #    | Mô tả                                                                                                                                                  | Cấp độ | Vai trò |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| AD.1.1 | Đảm bảo rằng quy trình làm việc được tài liệu hóa mô tả khi nào và làm thế nào các công cụ AI có thể tạo mã nguồn, tái cấu trúc hoặc xem xét mã nguồn. |   1    |   D/V   |
| AD.1.2 | Xác minh rằng quy trình làm việc được ánh xạ tới từng giai đoạn của SSDLC (thiết kế, thực hiện, xem xét mã, kiểm thử, triển khai).                     |   2    |    D    |
| AD.1.3 | Xác nhận rằng các chỉ số được thu thập trên mã do AI tạo ra và so sánh với các chuẩn tham chiếu chỉ dựa trên con người.                                |   3    |   D/V   |

---

## AD.2 Đánh giá Công cụ AI và Mô hình hóa mối đe dọa

Đảm bảo các công cụ lập trình AI được đánh giá về khả năng bảo mật, rủi ro và tác động của chuỗi cung ứng trước khi được áp dụng.

|   #    | Mô tả                                                                                                                                                                 | Cấp độ | Vai trò |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| AD.2.1 | Đảm bảo rằng mô hình mối đe dọa cho từng công cụ AI xác định sự lạm dụng, tấn công đảo ngược mô hình, rò rỉ dữ liệu và rủi ro chuỗi phụ thuộc.                        |   1    |   D/V   |
| AD.2.2 | Xác nhận rằng các đánh giá công cụ bao gồm phân tích tĩnh/động của bất kỳ thành phần cục bộ nào và đánh giá các điểm cuối SaaS (TLS, xác thực/ủy quyền, ghi nhật ký). |   2    |    D    |
| AD.2.3 | Xác minh rằng các đánh giá tuân theo một khung công tác được công nhận và được thực hiện lại sau khi có các thay đổi ở phiên bản chính.                               |   3    |   D/V   |

---

## AD.3 Quản lý lời nhắc và ngữ cảnh an toàn

Ngăn ngừa rò rỉ bí mật, mã nguồn độc quyền và dữ liệu cá nhân khi xây dựng các lời nhắc hoặc ngữ cảnh cho các mô hình trí tuệ nhân tạo.

|   #    | Mô tả                                                                                                                                                             | Cấp độ | Vai trò |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| AD.3.1 | Xác nhận rằng hướng dẫn bằng văn bản cấm gửi bí mật, thông tin xác thực hoặc dữ liệu được phân loại trong các prompt.                                             |   1    |   D/V   |
| AD.3.2 | Xác minh rằng các biện pháp kiểm soát kỹ thuật (client‑side redaction, bộ lọc ngữ cảnh được phê duyệt) tự động loại bỏ các dấu vết nhạy cảm.                      |   2    |    D    |
| AD.3.3 | Xác minh rằng các lời nhắc và phản hồi được token hóa, được mã hóa khi truyền và khi lưu trữ, và các thời hạn lưu giữ tuân thủ theo chính sách phân loại dữ liệu. |   3    |   D/V   |

---

## AD.4 Đánh giá mã do AI tạo ra

Phát hiện và khắc phục các lỗ hổng do đầu ra AI gây ra trước khi mã được hợp nhất hoặc triển khai.

|   #    | Mô tả                                                                                                                                                                       | Cấp độ | Vai trò |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| AD.4.1 | Xác nhận rằng mã do AI tạo ra luôn được rà soát bởi con người.                                                                                                              |   1    |   D/V   |
| AD.4.2 | Xác minh rằng các trình quét tự động (SAST/IAST/DAST) chạy trên mọi pull request chứa mã do AI tạo ra và chặn việc hợp nhất khi có các phát hiện nghiêm trọng.              |   2    |    D    |
| AD.4.3 | Xác minh rằng kiểm thử fuzz khác biệt hoặc kiểm thử dựa trên đặc tính chứng minh các hành vi có tính bảo mật cao (ví dụ: kiểm tra tính hợp lệ của đầu vào, logic ủy quyền). |   3    |   D/V   |

---

## AD.5 Khả năng giải thích và truy vết các đề xuất mã nguồn

Cung cấp cho kiểm toán viên và các nhà phát triển cái nhìn sâu sắc về lý do tại sao một đề xuất được đưa ra và nó đã phát triển như thế nào.

|   #    | Mô tả                                                                                                                                                                              | Cấp độ | Vai trò |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| AD.5.1 | Xác nhận rằng các cặp prompt và phản hồi được ghi lại với các ID commit.                                                                                                           |   1    |   D/V   |
| AD.5.2 | Xác nhận rằng các nhà phát triển có thể hiển thị các tham khảo từ mô hình (những đoạn trích huấn luyện, tài liệu) để hỗ trợ một gợi ý.                                             |   2    |    D    |
| AD.5.3 | Xác nhận rằng các báo cáo giải thích được lưu trữ cùng với các tài liệu thiết kế và được tham chiếu trong các đánh giá bảo mật, đáp ứng các nguyên tắc truy vết của ISO/IEC 42001. |   3    |   D/V   |

---

## AD.6 Phản hồi liên tục và tinh chỉnh mô hình

Cải thiện hiệu suất bảo mật của mô hình theo thời gian đồng thời ngăn ngừa sự lệch hướng tiêu cực.

|   #    | Mô tả                                                                                                                                                                                                           | Cấp độ | Vai trò |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| AD.6.1 | Xác minh rằng các nhà phát triển có thể gắn cờ các gợi ý không an toàn hoặc không tuân thủ, và các cờ được theo dõi.                                                                                            |   1    |   D/V   |
| AD.6.2 | Đảm bảo rằng phản hồi được tổng hợp cung cấp thông tin cho việc tinh chỉnh định kỳ hoặc retrieval‑augmented generation với các tập dữ liệu về lập trình an toàn đã được kiểm chứng (ví dụ: OWASP Cheat Sheets). |   2    |    D    |
| AD.6.3 | Xác minh rằng một khung đánh giá vòng kín thực hiện các kiểm thử hồi quy sau mỗi lần tinh chỉnh; các chỉ số bảo mật phải đạt hoặc vượt qua điểm chuẩn trước đó trước khi triển khai.                            |   3    |   D/V   |

---

### Tài liệu tham khảo

* [NIST AI Risk Management Framework 1.0](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements](https://www.iso.org/standard/81230.html)
* [OWASP Secure Coding Practices — Quick Reference Guide](https://owasp.org/www-project-secure-coding-practices-quick-reference-guide/)

