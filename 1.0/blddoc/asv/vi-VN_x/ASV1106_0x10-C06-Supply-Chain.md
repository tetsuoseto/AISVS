# Bảo mật Chuỗi Cung ứng C6 cho Mô hình, Khung và Dữ liệu

## Mục tiêu Kiểm soát

Các cuộc tấn công chuỗi cung ứng AI lợi dụng các mô hình, khung, hoặc bộ dữ liệu bên thứ ba để cài đặt cửa hậu, định kiến, hoặc mã dễ bị khai thác. Các biện pháp kiểm soát này cung cấp nguồn gốc từ đầu đến cuối, quản lý lỗ hổng và giám sát nhằm bảo vệ toàn bộ vòng đời mô hình.

---

## C6.1 Kiểm tra mô hình tiền huấn luyện & Nguồn gốc

Đánh giá và xác thực nguồn gốc, giấy phép, và các hành vi ẩn của mô hình bên thứ ba trước khi thực hiện tinh chỉnh hoặc triển khai.

|   #   | Mô tả                                                                                                                                                                     | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 6.1.1 | Xác minh rằng mọi sản phẩm mô hình bên thứ ba đều bao gồm một bản ghi xuất xứ được ký xác nhận, xác định kho lưu trữ nguồn và mã băm cam kết.                             |   1    |   D/V   |
| 6.1.2 | Xác minh rằng các mô hình được quét để phát hiện các lớp độc hại hoặc kích hoạt Trojan bằng công cụ tự động trước khi nhập khẩu.                                          |   1    |   D/V   |
| 6.1.3 | Xác minh rằng việc tinh chỉnh học chuyển giao vượt qua đánh giá đối kháng để phát hiện các hành vi ẩn.                                                                    |   2    |    D    |
| 6.1.4 | Xác nhận rằng giấy phép mô hình, nhãn kiểm soát xuất khẩu và các tuyên bố nguồn gốc dữ liệu được ghi lại trong một mục ML-BOM.                                            |   2    |    V    |
| 6.1.5 | Xác minh rằng các mô hình rủi ro cao (trọng số được tải lên công khai, nhà tạo chưa được xác minh) vẫn được cách ly cho đến khi được đánh giá và phê duyệt bởi con người. |   3    |   D/V   |

---

## C6.2 Quét Khung và Thư viện

Liên tục quét các framework và thư viện ML để phát hiện CVE và mã độc nhằm giữ an toàn cho ngăn xếp thời gian chạy.

|   #   | Mô tả                                                                                                                                    | Cấp độ | Vai trò |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 6.2.1 | Xác minh rằng các pipeline CI chạy trình quét phụ thuộc trên các framework AI và các thư viện quan trọng.                                |   1    |   D/V   |
| 6.2.2 | Xác minh rằng các lỗ hổng nghiêm trọng (CVSS ≥ 7.0) ngăn chặn việc thăng cấp lên các ảnh sản xuất.                                       |   1    |   D/V   |
| 6.2.3 | Xác minh rằng phân tích mã tĩnh chạy trên các thư viện ML được fork hoặc vendored.                                                       |   2    |    D    |
| 6.2.4 | Xác nhận rằng các đề xuất nâng cấp khung làm việc bao gồm một đánh giá ảnh hưởng bảo mật tham chiếu đến các nguồn dữ liệu CVE công khai. |   2    |    V    |
| 6.2.5 | Xác minh rằng các cảm biến thời gian chạy cảnh báo về việc tải thư viện động không mong đợi, có sự sai lệch so với SBOM đã được ký.      |   3    |    V    |

---

## C6.3 Ghim phụ thuộc & Xác minh

Ghim mọi phụ thuộc vào các bản tóm tắt không thể thay đổi và tái tạo các bản dựng để đảm bảo các tác phẩm giống hệt nhau, không bị giả mạo.

|   #   | Mô tả                                                                                                                                 | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 6.3.1 | Xác minh rằng tất cả các trình quản lý gói đều thực thi việc cố định phiên bản thông qua các tệp khóa.                                |   1    |   D/V   |
| 6.3.2 | Xác minh rằng các chữ ký băm không thay đổi được sử dụng thay vì các nhãn có thể thay đổi trong các tham chiếu container.             |   1    |   D/V   |
| 6.3.3 | Xác minh rằng các kiểm tra xây dựng có thể tái tạo so sánh các hàm băm giữa các lần chạy CI để đảm bảo kết quả đầu ra giống hệt nhau. |   2    |    D    |
| 6.3.4 | Xác nhận rằng các chứng thực xây dựng được lưu trữ trong 18 tháng để có thể truy xuất kiểm toán.                                      |   2    |    V    |
| 6.3.5 | Xác nhận rằng các phụ thuộc hết hạn kích hoạt các PR tự động để cập nhật hoặc fork các phiên bản đã cố định.                          |   3    |    D    |

---

## C6.4 Thực thi Nguồn Tin Cậy

Chỉ cho phép tải các tệp artifact từ các nguồn được tổ chức phê duyệt và xác minh bằng mật mã, và chặn tất cả các nguồn khác.

|   #   | Mô tả                                                                                                                           | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 6.4.1 | Xác minh rằng trọng số mô hình, bộ dữ liệu và container chỉ được tải xuống từ các miền được phê duyệt hoặc các registry nội bộ. |   1    |   D/V   |
| 6.4.2 | Xác minh rằng các chữ ký Sigstore/Cosign xác thực danh tính nhà xuất bản trước khi các bản ghi được lưu vào bộ nhớ đệm cục bộ.  |   1    |   D/V   |
| 6.4.3 | Xác minh rằng các proxy xuất cảnh chặn việc tải xuống artifact không được xác thực để thực thi chính sách nguồn tin cậy.        |   2    |    D    |
| 6.4.4 | Xác minh rằng danh sách cho phép của kho lưu trữ được xem xét hàng quý với bằng chứng về lý do kinh doanh cho từng mục nhập.    |   2    |    V    |
| 6.4.5 | Xác minh rằng các vi phạm chính sách kích hoạt việc cách ly các hiện vật và hoàn nguyên các lần chạy ống dẫn phụ thuộc.         |   3    |    V    |

---

## C6.5 Đánh giá rủi ro bộ dữ liệu bên thứ ba

Đánh giá các bộ dữ liệu bên ngoài về việc đầu độc, thiên vị và tuân thủ pháp lý, đồng thời theo dõi chúng trong suốt vòng đời của chúng.

|   #   | Mô tả                                                                                                                                     | Cấp độ | Vai trò |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 6.5.1 | Xác minh rằng các bộ dữ liệu bên ngoài được đánh giá rủi ro nhiễm độc (ví dụ: xác định dấu vân tay dữ liệu, phát hiện điểm bất thường).   |   1    |   D/V   |
| 6.5.2 | Xác minh rằng các chỉ số thiên lệch (cân bằng nhân khẩu học, cơ hội bình đẳng) được tính toán trước khi phê duyệt bộ dữ liệu.             |   1    |    D    |
| 6.5.3 | Xác minh rằng nguồn gốc và các điều khoản giấy phép của bộ dữ liệu được ghi lại trong các mục ML‑BOM.                                     |   2    |    V    |
| 6.5.4 | Xác minh rằng việc giám sát định kỳ phát hiện được sự dịch chuyển hoặc hư hỏng trong các tập dữ liệu được lưu trữ.                        |   2    |    V    |
| 6.5.5 | Xác nhận rằng nội dung bị cấm (bản quyền, thông tin nhận dạng cá nhân) đã được loại bỏ thông qua việc làm sạch tự động trước khi đào tạo. |   3    |    D    |

---

## C6.6 Giám sát Tấn công Chuỗi Cung ứng

Phát hiện sớm các mối đe dọa chuỗi cung ứng thông qua nguồn cấp dữ liệu CVE, phân tích nhật ký kiểm toán và mô phỏng đội đỏ.

|   #   | Mô tả                                                                                                                                                                                | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 6.6.1 | Xác minh rằng nhật ký kiểm tra CI/CD được truyền đến các hệ thống phát hiện SIEM để phát hiện các trường hợp kéo gói bất thường hoặc các bước xây dựng bị can thiệp.                 |   1    |    V    |
| 6.6.2 | Xác minh rằng các sổ tay phản ứng sự cố bao gồm các quy trình hoàn tác cho các mô hình hoặc thư viện bị xâm phạm.                                                                    |   2    |    D    |
| 6.6.3 | Xác minh rằng việc làm giàu thông tin tình báo đe dọa gắn nhãn các chỉ số đặc thù của ML (ví dụ: các IoC liên quan đến tấn công đầu độc mô hình) trong quá trình phân loại cảnh báo. |   3    |    V    |

---

## C6.7 ML‑BOM cho Tác phẩm Mô hình

Tạo và ký các SBOM chi tiết dành riêng cho ML (ML-BOM) để người tiêu dùng dòng dưới có thể xác minh tính toàn vẹn của thành phần tại thời điểm triển khai.

|   #   | Mô tả                                                                                                                                            | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 6.7.1 | Xác minh rằng mọi sản phẩm mô hình đều công bố một ML‑BOM liệt kê các tập dữ liệu, trọng số, siêu tham số và giấy phép.                          |   1    |   D/V   |
| 6.7.2 | Xác minh rằng việc tạo ML‑BOM và ký Cosign được tự động hóa trong CI và là điều kiện bắt buộc để hợp nhất.                                       |   1    |   D/V   |
| 6.7.3 | Xác minh rằng các kiểm tra hoàn chỉnh ML-BOM sẽ làm cho việc xây dựng thất bại nếu bất kỳ siêu dữ liệu thành phần nào (băm, giấy phép) bị thiếu. |   2    |    D    |
| 6.7.4 | Xác minh rằng các bên tiêu thụ hạ nguồn có thể truy vấn ML-BOMs thông qua API để xác thực các mô hình đã nhập khi triển khai.                    |   2    |    V    |
| 6.7.5 | Xác minh rằng các ML‑BOM được kiểm soát phiên bản và so sánh sự khác biệt để phát hiện các sửa đổi không được phép.                              |   3    |    V    |

---

## Tài liệu tham khảo

* [ML Supply Chain Compromise – MITRE ATLAS](https://misp-galaxy.org/mitre-atlas-attack-pattern/)
* [Supply‑chain Levels for Software Artifacts (SLSA)](https://slsa.dev/)
* [CycloneDX – Machine Learning Bill of Materials](https://cyclonedx.org/capabilities/mlbom/)
* [What is Data Poisoning? – SentinelOne](https://www.sentinelone.com/cybersecurity-101/cybersecurity/data-poisoning/)
* [Transfer Learning Attack – OWASP ML Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/docs/ML07_2023-Transfer_Learning_Attack)
* [AI Data Security Best Practices – CISA](https://www.cisa.gov/news-events/cybersecurity-advisories/aa25-142a)
* [Secure CI/CD Supply Chain – Sumo Logic](https://www.sumologic.com/blog/secure-azure-devops-github-supply-chain-attacks)
* [AI & Transparency: Protect ML Models – ReversingLabs](https://www.reversinglabs.com/blog/ai-and-transparency-how-ml-model-creators-can-protect-against-supply-chain-attacks)
* [SBOM Overview – CISA](https://www.cisa.gov/sbom)
* [Training Data Poisoning Guide – Lakera.ai](https://www.lakera.ai/blog/training-data-poisoning)
* [Dependency Pinning for Reproducible Python – Medium](https://medium.com/data-science-collective/guarantee-a-locked-reproducible-environment-with-every-python-run-c0e2bf19fb53)

