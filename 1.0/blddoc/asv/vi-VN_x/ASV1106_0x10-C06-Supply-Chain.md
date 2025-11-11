# An ninh Chuỗi Cung ứng C6 cho Mô hình, Khung công tác & Dữ liệu

## Mục tiêu Kiểm soát

Các cuộc tấn công chuỗi cung ứng AI lợi dụng các mô hình, khung làm việc hoặc bộ dữ liệu bên thứ ba để chèn cửa hậu, thiên vị hoặc mã có thể bị khai thác. Các biện pháp kiểm soát này cung cấp nguồn gốc từ đầu đến cuối, quản lý lỗ hổng và giám sát để bảo vệ toàn bộ vòng đời của mô hình.

---

## C6.1 Kiểm tra mô hình học trước và nguồn gốc

Đánh giá và xác thực nguồn gốc, giấy phép và hành vi ẩn của mô hình bên thứ ba trước bất kỳ quá trình tinh chỉnh hoặc triển khai nào.

|   #   | Mô tả                                                                                                                                                                     | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 6.1.1 | Xác minh rằng mọi sản phẩm mô hình bên thứ ba đều bao gồm một bản ghi xuất xứ có chữ ký xác nhận kho lưu trữ nguồn và mã băm cam kết.                                     |   1    |   D/V   |
| 6.1.2 | Xác minh rằng các mô hình được quét để phát hiện các lớp độc hại hoặc kích hoạt Trojan bằng công cụ tự động trước khi nhập.                                               |   1    |   D/V   |
| 6.1.3 | Xác minh rằng việc tinh chỉnh học chuyển giao vượt qua đánh giá đối kháng để phát hiện các hành vi ẩn.                                                                    |   2    |    D    |
| 6.1.4 | Xác minh rằng giấy phép mô hình, thẻ kiểm soát xuất khẩu và tuyên bố nguồn gốc dữ liệu được ghi lại trong mục ML‑BOM.                                                     |   2    |    V    |
| 6.1.5 | Xác nhận rằng các mô hình có rủi ro cao (trọng số được tải lên công khai, người tạo chưa được xác minh) vẫn được cách ly cho đến khi được con người xem xét và phê duyệt. |   3    |   D/V   |

---

## C6.2 Quét Khung và Thư viện

Liên tục quét các framework và thư viện ML để phát hiện CVE và mã độc nhằm giữ cho ngăn xếp runtime an toàn.

|   #   | Mô tả                                                                                                                         | Cấp độ | Vai trò |
| :---: | ----------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 6.2.1 | Xác minh rằng các pipeline CI thực thi trình quét phụ thuộc trên các framework AI và thư viện quan trọng.                     |   1    |   D/V   |
| 6.2.2 | Xác minh rằng các lỗ hổng nghiêm trọng (CVSS ≥ 7.0) chặn việc thăng cấp lên các ảnh sản xuất.                                 |   1    |   D/V   |
| 6.2.3 | Xác nhận rằng phân tích mã tĩnh chạy trên các thư viện ML được phân nhánh hoặc cung cấp dưới dạng bản sao bên ngoài.          |   2    |    D    |
| 6.2.4 | Xác minh rằng các đề xuất nâng cấp framework bao gồm đánh giá tác động bảo mật có tham chiếu đến nguồn dữ liệu CVE công khai. |   2    |    V    |
| 6.2.5 | Xác minh rằng các cảm biến thời gian chạy cảnh báo về việc tải thư viện động bất thường khi không tuân theo SBOM đã ký.       |   3    |    V    |

---

## C6.3 Ghim và Xác minh Phụ thuộc

Ghim mọi phụ thuộc vào các bản tổng hợp không thể thay đổi và tái tạo các bản dựng để đảm bảo các tác phẩm là giống hệt và không bị giả mạo.

|   #   | Mô tả                                                                                                                              | Cấp độ | Vai trò |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 6.3.1 | Xác minh rằng tất cả các trình quản lý gói đều thi hành việc khoá phiên bản thông qua các file khóa.                               |   1    |   D/V   |
| 6.3.2 | Xác minh rằng các digest bất biến được sử dụng thay vì các tag có thể thay đổi trong các tham chiếu container.                     |   1    |   D/V   |
| 6.3.3 | Xác minh rằng các kiểm tra xây dựng có thể tái tạo so sánh các giá trị băm trong các lần chạy CI để đảm bảo đầu ra giống hệt nhau. |   2    |    D    |
| 6.3.4 | Xác minh rằng các bản khai nhận xây dựng được lưu trữ trong 18 tháng để phục vụ việc theo dõi kiểm toán.                           |   2    |    V    |
| 6.3.5 | Xác minh rằng các thư viện phụ thuộc hết hạn sẽ kích hoạt các PR tự động để cập nhật hoặc nhân bản các phiên bản đã được cố định.  |   3    |    D    |

---

## C6.4 Thực thi Nguồn Tin cậy

Chỉ cho phép tải xuống các hiện vật từ các nguồn được tổ chức phê duyệt và xác minh mật mã, và chặn tất cả các nguồn khác.

|   #   | Mô tả                                                                                                                            | Cấp độ | Vai trò |
| :---: | -------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 6.4.1 | Xác minh rằng trọng số mô hình, bộ dữ liệu và container chỉ được tải xuống từ các miền được phê duyệt hoặc các kho nội bộ.       |   1    |   D/V   |
| 6.4.2 | Xác minh rằng các chữ ký Sigstore/Cosign xác thực danh tính nhà phát hành trước khi các hiện vật được lưu vào bộ nhớ đệm cục bộ. |   1    |   D/V   |
| 6.4.3 | Xác minh rằng các proxy egress chặn việc tải xuống artifact không xác thực để thực thi chính sách nguồn tin cậy.                 |   2    |    D    |
| 6.4.4 | Xác minh rằng danh sách cho phép của kho lưu trữ được xem xét hàng quý kèm theo bằng chứng về lý do kinh doanh cho mỗi mục.      |   2    |    V    |
| 6.4.5 | Xác nhận rằng các vi phạm chính sách kích hoạt việc cách ly các artifact và hoàn nguyên các lần chạy pipeline phụ thuộc.         |   3    |    V    |

---

## C6.5 Đánh giá Rủi ro Bộ dữ liệu Bên thứ ba

Đánh giá các bộ dữ liệu bên ngoài về việc đầu độc, thiên vị và tuân thủ pháp lý, đồng thời theo dõi chúng trong suốt vòng đời của chúng.

|   #   | Mô tả                                                                                                                                    | Cấp độ | Vai trò |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 6.5.1 | Xác minh rằng các bộ dữ liệu bên ngoài phải trải qua đánh giá rủi ro nhiễm độc (ví dụ: định danh dữ liệu, phát hiện điểm ngoại lai).     |   1    |   D/V   |
| 6.5.2 | Xác minh rằng các chỉ số sai lệch (cân bằng nhân khẩu học, cơ hội bình đẳng) được tính toán trước khi phê duyệt bộ dữ liệu.              |   1    |    D    |
| 6.5.3 | Xác minh rằng nguồn gốc và các điều khoản cấp phép cho bộ dữ liệu được ghi lại trong các mục ML‑BOM.                                     |   2    |    V    |
| 6.5.4 | Xác minh rằng việc giám sát định kỳ phát hiện sự dịch chuyển hoặc hỏng hóc trong các bộ dữ liệu được lưu trữ.                            |   2    |    V    |
| 6.5.5 | Xác minh rằng nội dung bị cấm (bản quyền, thông tin cá nhân nhạy cảm) đã được loại bỏ thông qua việc làm sạch tự động trước khi đào tạo. |   3    |    D    |

---

## C6.6 Giám sát Tấn công Chuỗi Cung ứng

Phát hiện sớm các mối đe dọa chuỗi cung ứng thông qua nguồn cấp CVE, phân tích nhật ký kiểm toán và mô phỏng nhóm tấn công.

|   #   | Mô tả                                                                                                                                                                      | Cấp độ | Vai trò |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 6.6.1 | Xác minh rằng các nhật ký kiểm toán CI/CD được truyền đến SIEM để phát hiện các hành vi bất thường trong việc lấy gói hoặc các bước xây dựng bị can thiệp.                 |   1    |    V    |
| 6.6.2 | Xác minh rằng các kịch bản ứng phó sự cố bao gồm các thủ tục khôi phục cho các mô hình hoặc thư viện bị xâm phạm.                                                          |   2    |    D    |
| 6.6.3 | Xác minh rằng việc làm giàu thông tin tình báo mối đe dọa gắn thẻ các chỉ báo đặc thù cho ML (ví dụ: các IoC tấn công đầu độc mô hình) trong quá trình phân loại cảnh báo. |   3    |    V    |

---

## C6.7 ML‑BOM cho Các Tác phẩm Mô hình

Tạo và ký các SBOM chi tiết dành riêng cho ML (ML-BOM) để người tiêu dùng ở hạ nguồn có thể xác minh tính toàn vẹn của các thành phần khi triển khai.

|   #   | Mô tả                                                                                                                                                    | Cấp độ | Vai trò |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 6.7.1 | Xác minh rằng mỗi hiện vật mô hình đều xuất bản một ML-BOM liệt kê các bộ dữ liệu, trọng số, siêu tham số và giấy phép.                                  |   1    |   D/V   |
| 6.7.2 | Xác minh rằng việc tạo ML‑BOM và ký Cosign được tự động hóa trong CI và là yêu cầu bắt buộc để hợp nhất.                                                 |   1    |   D/V   |
| 6.7.3 | Xác minh rằng các kiểm tra độ hoàn chỉnh của ML‑BOM sẽ làm cho việc xây dựng thất bại nếu bất kỳ siêu dữ liệu thành phần nào (hash, giấy phép) bị thiếu. |   2    |    D    |
| 6.7.4 | Xác minh rằng người tiêu dùng hạ nguồn có thể truy vấn ML-BOMs thông qua API để xác thực các mô hình đã nhập khi triển khai.                             |   2    |    V    |
| 6.7.5 | Xác minh rằng các ML‑BOM được kiểm soát phiên bản và so sánh để phát hiện các sửa đổi trái phép.                                                         |   3    |    V    |

---

## Tài liệu tham khảo

* [OWASP LLM03:2025 Supply Chain](https://genai.owasp.org/llmrisk/llm032025-supply-chain/)
* [MITRE ATLAS : Supply Chain Compromise](https://atlas.mitre.org/techniques/AML.T0010)
* [SBOM Overview – CISA](https://www.cisa.gov/sbom)
* [CycloneDX – Machine Learning Bill of Materials](https://cyclonedx.org/capabilities/mlbom/)

