# C6 Bảo mật chuỗi cung ứng cho Mô hình, Khung và Dữ liệu

## Mục tiêu kiểm soát

AI tấn công chuổi cung ứng AI? Wait no, I must output final translation. The user message asks for translation to Vietnamese. I must produce the translation string only.

Final translation:

Tấn công chuỗi cung ứng AI khai thác các mô hình, khung công cụ, hoặc tập dữ liệu từ bên thứ ba để chèn cửa hậu, thiên vị, hoặc mã có thể khai thác. Những biện pháp kiểm soát này cung cấp nguồn gốc từ đầu đến cuối, quản lý lỗ hổng và giám sát để bảo vệ toàn bộ vòng đời của mô hình.

---

## C6.1 Đánh giá và nguồn gốc của mô hình tiền huấn luyện

Đánh giá và xác thực nguồn gốc mô hình bên thứ ba, giấy phép và hành vi ẩn trước bất kỳ quá trình tinh chỉnh hoặc triển khai nào.

|   #   | Mô tả                                                                                                                                                                              | Cấp độ | Vai trò |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 6.1.1 | Xác nhận rằng mọi artifact mô hình từ bên thứ ba đều đi kèm với hồ sơ nguồn gốc đã ký, xác định kho lưu trữ nguồn và mã băm commit.                                                |   1    |   D/V   |
| 6.1.2 | Xác minh rằng các mô hình được quét để dò tìm các lớp độc hại hoặc các kích hoạt Trojan bằng các công cụ tự động trước khi nhập.                                                   |   1    |   D/V   |
| 6.1.3 | Xác nhận rằng các phiên tinh chỉnh bằng transfer‑learning vượt qua đánh giá adversarial để phát hiện các hành vi ẩn.                                                               |   2    |    D    |
| 6.1.4 | Xác minh rằng các giấy phép mô hình, nhãn export‑control, và các tuyên bố data-origin được ghi vào một mục ML‑BOM.                                                                 |   2    |    V    |
| 6.1.5 | Xác nhận rằng các mô hình rủi ro cao (các trọng số được tải lên công khai, người sáng tạo chưa được xác minh) vẫn được cách ly cho đến khi được xem xét và ký duyệt bởi con người. |   3    |   D/V   |

---

## C6.2 Quét Framework và Thư viện

Quét liên tục các framework học máy và thư viện để phát hiện các lỗ hổng CVE và mã độc hại nhằm đảm bảo ngăn xếp thời gian chạy an toàn.

|   #   | Mô tả                                                                                                                      | Cấp độ | Vai trò |
| :---: | -------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 6.2.1 | Xác minh rằng các pipeline CI đang chạy các trình quét phụ thuộc trên các framework AI và các thư viện quan trọng.         |   1    |   D/V   |
| 6.2.2 | Xác minh rằng các lỗ hổng nghiêm trọng (CVSS ≥ 7.0) chặn việc đưa các ảnh container lên môi trường sản xuất.               |   1    |   D/V   |
| 6.2.3 | Xác minh rằng phân tích mã nguồn tĩnh có thể chạy trên các thư viện học máy được fork hoặc nhúng vào dự án.                |   2    |    D    |
| 6.2.4 | Xác minh rằng các đề xuất nâng cấp framework bao gồm một đánh giá tác động bảo mật tham chiếu đến các nguồn CVE công khai. |   2    |    V    |
| 6.2.5 | Xác minh rằng các cảm biến thời gian chạy cảnh báo khi có việc nạp thư viện động bất thường khác với SBOM đã ký.           |   3    |    V    |

---

## C6.3 Ghim phụ thuộc và xác minh

Ghim mọi phụ thuộc vào các chữ băm bất biến và tái tạo lại các bản dựng để đảm bảo các tác phẩm xây dựng giống hệt nhau và không thể bị giả mạo.

|   #   | Mô tả                                                                                                                            | Cấp độ | Vai trò |
| :---: | -------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 6.3.1 | Xác minh xem tất cả các trình quản lý gói có bắt buộc ghim phiên bản thông qua các tệp khóa hay không.                           |   1    |   D/V   |
| 6.3.2 | Xác minh rằng các digest bất biến được sử dụng thay vì các nhãn có thể thay đổi trong tham chiếu container.                      |   1    |   D/V   |
| 6.3.3 | Xác nhận rằng các kiểm tra khả năng tái tạo build so sánh các giá trị băm giữa các lần chạy CI để đảm bảo đầu ra giống hệt nhau. |   2    |    D    |
| 6.3.4 | Xác minh rằng các chứng thực xây dựng được lưu trữ trong 18 tháng để đảm bảo khả năng truy vết cho kiểm toán.                    |   2    |    V    |
| 6.3.5 | Xác nhận rằng các phụ thuộc đã hết hạn sẽ kích hoạt các PR tự động để cập nhật hoặc fork các phiên bản được ghim.                |   3    |    D    |

---

## C6.4 Thực thi nguồn tin đáng tin cậy

Chỉ cho phép tải xuống artefact từ các nguồn được xác thực bằng chữ ký số và được tổ chức phê duyệt, và chặn mọi nguồn khác.

|   #   | Mô tả                                                                                                                                               | Cấp độ | Vai trò |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 6.4.1 | Xác minh rằng trọng số của mô hình, các tập dữ liệu và các container chỉ được tải xuống từ các tên miền được phê duyệt hoặc từ các registry nội bộ. |   1    |   D/V   |
| 6.4.2 | Xác minh rằng chữ ký Sigstore/Cosign xác thực danh tính của nhà phát hành trước khi các artifact được lưu vào bộ nhớ đệm cục bộ.                    |   1    |   D/V   |
| 6.4.3 | Xác nhận rằng các proxy ra ngoài chặn tải xuống artifact chưa được xác thực để thực thi trusted‑source policy.                                      |   2    |    D    |
| 6.4.4 | Xác nhận rằng danh sách cho phép của kho lưu trữ được rà soát hàng quý, kèm theo bằng chứng về lý do kinh doanh cho từng mục nhập.                  |   2    |    V    |
| 6.4.5 | Xác minh rằng vi phạm chính sách sẽ kích hoạt việc cách ly các artefacts và quay lui các lần chạy pipeline phụ thuộc.                               |   3    |    V    |

---

## C6.5 Đánh giá rủi ro tập dữ liệu của bên thứ ba

Đánh giá các tập dữ liệu bên ngoài về đầu độc dữ liệu, thiên vị và tuân thủ pháp lý, và giám sát chúng trong suốt vòng đời của chúng.

|   #   | Mô tả                                                                                                                                         | Cấp độ | Vai trò |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 6.5.1 | Xác nhận rằng các bộ dữ liệu bên ngoài đã trải qua quá trình đánh giá rủi ro đầu độc (ví dụ: dấu vân dữ liệu, phát hiện giá trị ngoại lai).   |   1    |   D/V   |
| 6.5.2 | Xác nhận rằng các thước đo thiên vị (đồng nhất theo đặc điểm nhân khẩu học, cơ hội bằng nhau) được tính toán trước khi phê duyệt tập dữ liệu. |   1    |    D    |
| 6.5.3 | Xác nhận rằng nguồn gốc và các điều khoản cấp phép đối với tập dữ liệu được ghi nhận trong các mục ML‑BOM.                                    |   2    |    V    |
| 6.5.4 | Xác minh rằng việc giám sát định kỳ có thể phát hiện sự lệch hoặc hư hỏng trong các tập dữ liệu được lưu trữ.                                 |   2    |    V    |
| 6.5.5 | Xác minh rằng nội dung bị cấm (bản quyền, thông tin nhận dạng cá nhân) đã được loại bỏ thông qua làm sạch tự động trước khi huấn luyện.       |   3    |    D    |

---

## C6.6 Giám sát tấn công chuỗi cung ứng

Phát hiện sớm các mối đe dọa chuỗi cung ứng thông qua nguồn CVE, phân tích nhật ký audit-log và mô phỏng đội đỏ.

|   #   | Mô tả                                                                                                                                                     | Cấp độ | Vai trò |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 6.6.1 | Xác minh rằng nhật ký kiểm toán CI/CD được gửi tới SIEM để phát hiện các lần kéo gói bất thường hoặc các bước xây dựng bị can thiệp.                      |   1    |    V    |
| 6.6.2 | Xác minh rằng các playbook ứng phó sự cố bao gồm các thủ tục quay lại phiên bản trước cho các mô hình hoặc thư viện bị xâm phạm.                          |   2    |    D    |
| 6.6.3 | Xác nhận rằng các nhãn bổ sung threat‑intel dành cho các chỉ dấu đặc thù dành cho ML (ví dụ, IoCs về đầu độc mô hình) trong quá trình phân loại cảnh báo. |   3    |    V    |

---

## C6.7 ML‑BOM cho Tác phẩm của Mô hình

Tạo và ký các SBOM chi tiết dành cho ML (ML‑BOMs) để người tiêu dùng ở phía hạ nguồn có thể xác minh tính toàn vẹn của các thành phần tại thời điểm triển khai.

|   #   | Mô tả                                                                                                                                                      | Cấp độ | Vai trò |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 6.7.1 | Xác nhận rằng mọi tài sản mô hình đều công bố ML‑BOM liệt kê các tập dữ liệu, trọng số, siêu tham số và giấy phép.                                         |   1    |   D/V   |
| 6.7.2 | Xác nhận rằng việc tạo ML‑BOM và ký Cosign được tự động hóa trong CI và được yêu cầu khi gộp nhánh.                                                        |   1    |   D/V   |
| 6.7.3 | Xác nhận rằng các kiểm tra tính đầy đủ ML‑BOM sẽ làm cho quá trình build thất bại nếu bất kỳ siêu dữ liệu của thành phần nào (mã băm, giấy phép) bị thiếu. |   2    |    D    |
| 6.7.4 | Xác minh rằng các bên tiêu thụ ở phía sau có thể truy vấn ML-BOMs thông qua API để xác nhận các mô hình được nhập khẩu tại thời điểm triển khai.           |   2    |    V    |
| 6.7.5 | Xác minh rằng ML‑BOMs được kiểm soát phiên bản và được so sánh sự khác biệt để phát hiện các biến đổi trái phép.                                           |   3    |    V    |

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

