# C4 Cơ sở hạ tầng, Cấu hình & Bảo mật Triển khai

## Mục tiêu Kiểm soát

Cơ sở hạ tầng AI phải được củng cố để chống lại việc leo thang đặc quyền, can thiệp chuỗi cung ứng và di chuyển ngang thông qua cấu hình bảo mật, cô lập thời gian chạy, quy trình triển khai đáng tin cậy và giám sát toàn diện. Chỉ các thành phần và cấu hình cơ sở hạ tầng được ủy quyền và xác thực mới được đưa vào sản xuất thông qua các quy trình kiểm soát nhằm duy trì tính bảo mật, toàn vẹn và khả năng kiểm tra.

Mục tiêu Bảo mật Cốt lõi: Chỉ các thành phần hạ tầng được ký mật mã và quét lỗ hổng mới được đưa vào sản xuất thông qua các đường ống xác thực tự động, có chức năng thực thi các chính sách bảo mật và duy trì hồ sơ kiểm toán không thể thay đổi.

---

## C4.1 Cô lập Môi trường Thời gian Chạy

Ngăn ngừa việc thoát khỏi container và leo thang đặc quyền thông qua các nguyên thủy cô lập cấp kernel và các kiểm soát truy cập bắt buộc.

|   #   | Mô tả                                                                                                                                                                                                                          | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 4.1.1 | Xác minh rằng tất cả các container AI loại bỏ TẤT CẢ các quyền năng Linux ngoại trừ CAP_SETUID, CAP_SETGID và các quyền năng được yêu cầu rõ ràng được ghi trong các chuẩn bảo mật.                                            |   1    |   D/V   |
| 4.1.2 | Xác minh rằng các hồ sơ seccomp chặn tất cả các syscall ngoại trừ những syscall đã được phê duyệt trước trong danh sách cho phép, với các vi phạm sẽ khiến container bị kết thúc và tạo ra các cảnh báo bảo mật.               |   1    |   D/V   |
| 4.1.3 | Xác nhận rằng các khối lượng công việc AI chạy với hệ thống tệp gốc chỉ đọc, tmpfs cho dữ liệu tạm thời, và các volume được đặt tên cho dữ liệu lưu trữ với các tùy chọn gắn kết noexec được thực thi.                         |   2    |   D/V   |
| 4.1.4 | Xác minh rằng việc giám sát thời gian chạy dựa trên eBPF (Falco, Tetragon hoặc tương đương) phát hiện các cố gắng leo thang đặc quyền và tự động chấm dứt các tiến trình vi phạm trong phạm vi thời gian phản hồi của tổ chức. |   2    |   D/V   |
| 4.1.5 | Xác nhận rằng các khối lượng công việc AI có rủi ro cao được thực thi trong các môi trường cách ly phần cứng (Intel TXT, AMD SVM hoặc các nút bare-metal chuyên dụng) với việc xác minh chứng thực.                            |   3    |   D/V   |

---

## C4.2 Đường ống Xây dựng & Triển khai An toàn

Đảm bảo tính toàn vẹn mật mã và an ninh chuỗi cung ứng thông qua các bản build có thể tái tạo và các tác phẩm được ký.

|   #   | Mô tả                                                                                                                                                                                                  | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 4.2.1 | Xác minh rằng hạ tầng như mã được quét bằng các công cụ (tfsec, Checkov hoặc Terrascan) trên mỗi lần commit, chặn việc hợp nhất nếu phát hiện các lỗi mức độ NGHIÊM TRỌNG hoặc CAO.                    |   1    |   D/V   |
| 4.2.2 | Xác minh rằng các bản dựng container có thể tái tạo với các hàm băm SHA256 giống hệt nhau trên các lần xây dựng và tạo các chứng nhận nguồn gốc SLSA Cấp độ 3 được ký bằng Sigstore.                   |   1    |   D/V   |
| 4.2.3 | Xác minh rằng các ảnh container chứa SBOM CycloneDX hoặc SPDX và được ký bằng Cosign trước khi đẩy lên registry, với các ảnh không ký bị từ chối khi triển khai.                                       |   2    |   D/V   |
| 4.2.4 | Xác minh rằng các pipeline CI/CD sử dụng token OIDC từ HashiCorp Vault, vai trò IAM của AWS, hoặc Azure Managed Identity với thời gian tồn tại không vượt quá giới hạn chính sách bảo mật của tổ chức. |   2    |   D/V   |
| 4.2.5 | Xác minh rằng các chữ ký Cosign và nguồn gốc SLSA được kiểm tra trong quá trình triển khai trước khi container được thực thi và rằng các lỗi xác minh sẽ khiến việc triển khai bị thất bại.            |   2    |   D/V   |
| 4.2.6 | Xác minh rằng các môi trường xây dựng chạy trong các container tạm thời hoặc máy ảo không có lưu trữ lâu dài và được cách ly mạng khỏi các VPC sản xuất.                                               |   2    |   D/V   |

---

## C4.3 An ninh mạng & Kiểm soát truy cập

Triển khai mạng lưới không tin cậy với các chính sách mặc định từ chối và truyền thông được mã hóa.

|   #   | Mô tả                                                                                                                                                                                                               | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 4.3.1 | Xác minh rằng Kubernetes NetworkPolicies hoặc bất kỳ giải pháp tương đương nào thực hiện chính sách từ chối mặc định cho truy cập vào/ra với các quy tắc cho phép rõ ràng cho các cổng cần thiết (443, 8080, v.v.). |   1    |   D/V   |
| 4.3.2 | Xác minh rằng SSH (cổng 22), RDP (cổng 3389) và các điểm cuối metadata đám mây (169.254.169.254) đã bị chặn hoặc yêu cầu xác thực dựa trên chứng chỉ.                                                               |   1    |   D/V   |
| 4.3.3 | Xác minh rằng lưu lượng ra bên ngoài được lọc qua các proxy HTTP/HTTPS (Squid, Istio hoặc các cổng NAT đám mây) với danh sách cho phép miền và các yêu cầu bị chặn được ghi lại.                                    |   2    |   D/V   |
| 4.3.4 | Xác minh rằng giao tiếp giữa các dịch vụ sử dụng mutual TLS với chứng chỉ được xoay vòng theo chính sách tổ chức và thực thi việc xác thực chứng chỉ (không bỏ qua cờ skip-verify).                                 |   2    |   D/V   |
| 4.3.5 | Xác minh rằng hạ tầng AI chạy trong các VPC/VNet riêng biệt không có truy cập internet trực tiếp và chỉ giao tiếp thông qua các cổng NAT hoặc máy chủ bastion.                                                      |   2    |   D/V   |

---

## C4.4 Quản lý Bí mật & Khóa Mã hóa

Bảo vệ thông tin đăng nhập thông qua lưu trữ dựa trên phần cứng và tự động xoay vòng với truy cập không tin cậy.

|   #   | Mô tả                                                                                                                                                                                                                                                   | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 4.4.1 | Xác minh rằng các bí mật được lưu trữ trong HashiCorp Vault, AWS Secrets Manager, Azure Key Vault hoặc Google Secret Manager với mã hóa khi lưu trữ sử dụng AES-256.                                                                                    |   1    |   D/V   |
| 4.4.2 | Xác minh rằng các khóa mật mã được tạo ra trong HSM cấp độ 2 tuân thủ FIPS 140-2 (AWS CloudHSM, Azure Dedicated HSM) với việc xoay khóa theo chính sách mật mã tổ chức.                                                                                 |   1    |   D/V   |
| 4.4.3 | Xác minh rằng việc xoay vòng bí mật được tự động hóa với triển khai không thời gian chết và xoay vòng ngay lập tức được kích hoạt bởi thay đổi nhân sự hoặc sự cố bảo mật.                                                                              |   2    |   D/V   |
| 4.4.4 | Xác minh rằng các hình ảnh container được quét bằng các công cụ (GitLeaks, TruffleHog hoặc detect-secrets) để chặn các bản build có chứa khóa API, mật khẩu hoặc chứng chỉ.                                                                             |   2    |   D/V   |
| 4.4.5 | Xác minh rằng quyền truy cập bí mật trong môi trường sản xuất yêu cầu xác thực đa yếu tố (MFA) bằng các token phần cứng (YubiKey, FIDO2) và được ghi lại trong các nhật ký kiểm tra không thể thay đổi, kèm theo danh tính người dùng và dấu thời gian. |   2    |   D/V   |
| 4.4.6 | Xác minh rằng các khóa bí mật được tiêm thông qua Kubernetes secrets, volumes được gắn, hoặc init containers và đảm bảo rằng các khóa bí mật không bao giờ được nhúng trong biến môi trường hoặc hình ảnh.                                              |   2    |   D/V   |

---

## C4.5 Đóng hộp và Xác thực Khối lượng Công việc AI

Cô lập các mô hình AI không đáng tin cậy trong các sandbox an toàn với phân tích hành vi toàn diện.

|   #   | Mô tả                                                                                                                                                                                                                                 | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 4.5.1 | Xác minh rằng các mô hình AI bên ngoài được thực thi trong gVisor, microVMs (chẳng hạn như Firecracker, CrossVM), hoặc các container Docker với các tùy chọn --security-opt=no-new-privileges và --read-only.                         |   1    |   D/V   |
| 4.5.2 | Xác minh rằng các môi trường sandbox không có kết nối mạng (--network=none) hoặc chỉ truy cập localhost với tất cả các yêu cầu bên ngoài bị chặn bởi các quy tắc iptables.                                                            |   1    |   D/V   |
| 4.5.3 | Xác minh rằng việc xác thực mô hình AI bao gồm kiểm thử red-team tự động với phạm vi kiểm thử được xác định bởi tổ chức và phân tích hành vi để phát hiện cửa hậu.                                                                    |   2    |   D/V   |
| 4.5.4 | Xác minh rằng trước khi một mô hình AI được triển khai vào sản xuất, kết quả trong môi trường thử nghiệm của nó được ký bằng mật mã bởi nhân sự an ninh có thẩm quyền và được lưu trữ trong các nhật ký kiểm toán không thể thay đổi. |   2    |   D/V   |
| 4.5.5 | Xác minh rằng các môi trường sandbox được hủy và tái tạo từ các ảnh golden giữa các lần đánh giá với việc dọn dẹp hoàn toàn hệ thống tập tin và bộ nhớ.                                                                               |   2    |   D/V   |

---

## C4.6 Giám sát An ninh Hạ tầng

Liên tục quét và giám sát hạ tầng với việc khắc phục tự động và cảnh báo theo thời gian thực.

|   #   | Mô tả                                                                                                                                                                                           | Cấp độ | Vai trò |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 4.6.1 | Xác minh rằng các hình ảnh container được quét theo lịch trình của tổ chức với các lỗ hổng CRITICAL ngăn chặn việc triển khai dựa trên ngưỡng rủi ro của tổ chức.                               |   1    |   D/V   |
| 4.6.2 | Xác minh rằng hạ tầng đáp ứng các tiêu chuẩn CIS Benchmarks hoặc các kiểm soát NIST 800-53 theo các ngưỡng tuân thủ được tổ chức xác định và tự động khắc phục cho các kiểm tra không đạt.      |   1    |   D/V   |
| 4.6.3 | Xác minh rằng các lỗ hổng với mức độ nghiêm trọng CAO được vá theo tiến độ quản lý rủi ro của tổ chức với các thủ tục khẩn cấp cho các CVE đang bị khai thác tích cực.                          |   2    |   D/V   |
| 4.6.4 | Xác nhận rằng các cảnh báo bảo mật tích hợp với các nền tảng SIEM (Splunk, Elastic, hoặc Sentinel) sử dụng định dạng CEF hoặc STIX/TAXII với khả năng làm giàu tự động.                         |   2    |    V    |
| 4.6.5 | Xác minh rằng các chỉ số hạ tầng được xuất ra hệ thống giám sát (Prometheus, DataDog) với các bảng điều khiển SLA và báo cáo điều hành.                                                         |   3    |    V    |
| 4.6.6 | Xác minh rằng sự lệch cấu hình được phát hiện bằng các công cụ (Chef InSpec, AWS Config) theo yêu cầu giám sát của tổ chức với khả năng tự động khôi phục đối với các thay đổi không được phép. |   2    |   D/V   |

---

## Quản lý Tài nguyên Hạ tầng AI C4.7

Ngăn chặn các cuộc tấn công làm cạn kiệt tài nguyên và đảm bảo phân bổ tài nguyên công bằng thông qua hạn ngạch và giám sát.

|   #   | Mô tả                                                                                                                                                                                                                     | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 4.7.1 | Xác minh rằng việc sử dụng GPU/TPU được giám sát với cảnh báo được kích hoạt khi vượt ngưỡng do tổ chức xác định và tự động điều chỉnh quy mô hoặc cân bằng tải được kích hoạt dựa trên các chính sách quản lý công suất. |   1    |   D/V   |
| 4.7.2 | Xác minh rằng các chỉ số khối lượng công việc AI (độ trễ suy luận, thông lượng, tỷ lệ lỗi) được thu thập theo các yêu cầu giám sát của tổ chức và được đối chiếu với mức sử dụng hạ tầng.                                 |   1    |   D/V   |
| 4.7.3 | Xác minh rằng Kubernetes ResourceQuotas hoặc các cơ chế tương đương giới hạn từng workload theo chính sách phân bổ tài nguyên của tổ chức với các giới hạn cứng được thực thi.                                            |   2    |   D/V   |
| 4.7.4 | Xác minh rằng việc giám sát chi phí theo dõi chi tiêu theo từng khối lượng công việc/người thuê với cảnh báo dựa trên ngưỡng ngân sách tổ chức và các kiểm soát tự động cho việc vượt ngân sách.                          |   2    |    V    |
| 4.7.5 | Xác nhận rằng lập kế hoạch năng lực sử dụng dữ liệu lịch sử với các khoảng thời gian dự báo được xác định theo tổ chức và cung cấp tài nguyên tự động dựa trên các mẫu nhu cầu.                                           |   3    |    V    |
| 4.7.6 | Xác minh rằng cạn kiệt tài nguyên kích hoạt bộ ngắt mạch theo yêu cầu phản hồi của tổ chức, bao gồm giới hạn tốc độ dựa trên chính sách công suất và cách ly khối lượng công việc.                                        |   2    |   D/V   |

---

## C4.8 Kiểm soát Tách biệt Môi trường & Thăng tiến

Thực thi ranh giới môi trường nghiêm ngặt với các cổng thăng tiến tự động và xác nhận bảo mật.

|   #   | Mô tả                                                                                                                                                                                                                       | Cấp độ | Vai trò |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 4.8.1 | Xác minh rằng các môi trường dev/test/prod chạy trong các VPCs/VNets riêng biệt mà không chia sẻ vai trò IAM, nhóm bảo mật hoặc kết nối mạng nào.                                                                           |   1    |   D/V   |
| 4.8.2 | Xác minh rằng việc thăng cấp môi trường yêu cầu phải có sự phê duyệt từ nhân sự được tổ chức xác định có thẩm quyền bằng chữ ký mật mã và các bản ghi kiểm toán không thể thay đổi.                                         |   1    |   D/V   |
| 4.8.3 | Xác minh rằng các môi trường sản xuất chặn truy cập SSH, vô hiệu hóa các điểm cuối debug và yêu cầu các yêu cầu thay đổi với điều kiện thông báo trước theo tổ chức, trừ trường hợp khẩn cấp.                               |   2    |   D/V   |
| 4.8.4 | Xác minh rằng các thay đổi hạ tầng dưới dạng mã yêu cầu được xem xét bởi đồng nghiệp cùng với kiểm thử tự động và quét bảo mật trước khi hợp nhất vào nhánh chính.                                                          |   2    |   D/V   |
| 4.8.5 | Xác minh rằng dữ liệu không phải sản xuất được ẩn danh theo các yêu cầu về quyền riêng tư của tổ chức, tạo dữ liệu tổng hợp hoặc che dữ liệu hoàn toàn với việc loại bỏ thông tin nhận dạng cá nhân (PII) đã được xác minh. |   2    |   D/V   |
| 4.8.6 | Xác minh rằng các cổng thăng tiến bao gồm các bài kiểm tra bảo mật tự động (SAST, DAST, quét container) với yêu cầu không có phát hiện nghiêm trọng (CRITICAL) nào để được phê duyệt.                                       |   2    |   D/V   |

---

## C4.9 Sao lưu và Phục hồi Hạ tầng

Đảm bảo khả năng phục hồi hạ tầng thông qua sao lưu tự động, quy trình khôi phục đã được kiểm tra và khả năng phục hồi sau thảm họa.

|   #   | Mô tả                                                                                                                                                                       | Cấp độ | Vai trò |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 4.9.1 | Xác minh rằng các cấu hình hạ tầng được sao lưu theo lịch sao lưu của tổ chức đến các khu vực địa lý tách biệt với việc triển khai chiến lược sao lưu 3-2-1.                |   1    |   D/V   |
| 4.9.2 | Xác minh rằng các hệ thống sao lưu hoạt động trong các mạng tách biệt với thông tin đăng nhập riêng biệt và lưu trữ cách ly để bảo vệ chống lại ransomware.                 |   2    |   D/V   |
| 4.9.3 | Xác minh rằng các quy trình khôi phục được kiểm tra và xác nhận thông qua kiểm thử tự động theo lịch trình tổ chức với các mục tiêu RTO và RPO đáp ứng yêu cầu của tổ chức. |   2    |    V    |
| 4.9.4 | Xác nhận rằng phục hồi thảm họa bao gồm các runbook cụ thể cho AI với việc khôi phục trọng số mô hình, xây dựng lại cụm GPU và ánh xạ phụ thuộc dịch vụ.                    |   3    |    V    |

---

## C4.10 Tuân thủ & Quản trị Hạ tầng

Duy trì tuân thủ quy định thông qua đánh giá liên tục, ghi chép tài liệu và kiểm soát tự động.

|   #    | Mô tả                                                                                                                                                               | Cấp độ | Vai trò |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 4.10.1 | Xác minh rằng tuân thủ hạ tầng được đánh giá theo lịch trình của tổ chức dựa trên các kiểm soát SOC 2, ISO 27001 hoặc FedRAMP với việc thu thập bằng chứng tự động. |   2    |   D/V   |
| 4.10.2 | Xác minh rằng tài liệu hạ tầng bao gồm sơ đồ mạng, bản đồ luồng dữ liệu và mô hình mối đe dọa được cập nhật theo các yêu cầu quản lý thay đổi tổ chức.              |   2    |    V    |
| 4.10.3 | Xác minh rằng các thay đổi hạ tầng trải qua đánh giá tác động tuân thủ tự động với các quy trình phê duyệt theo quy định cho các sửa đổi có rủi ro cao.             |   3    |   D/V   |

---

## C4.11 An ninh phần cứng AI

Bảo mật các thành phần phần cứng chuyên biệt cho AI bao gồm GPU, TPU và các bộ tăng tốc AI chuyên dụng.

|   #    | Mô tả                                                                                                                                                                                           | Cấp độ | Vai trò |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 4.11.1 | Xác minh rằng firmware bộ tăng tốc AI (BIOS GPU, firmware TPU) được xác thực bằng chữ ký mật mã và được cập nhật theo thời gian biểu quản lý bản vá của tổ chức.                                |   2    |   D/V   |
| 4.11.2 | Xác minh rằng trước khi thực thi khối lượng công việc, tính toàn vẹn của bộ tăng tốc AI được xác nhận bằng chứng thực phần cứng sử dụng TPM 2.0, Intel TXT hoặc AMD SVM.                        |   2    |   D/V   |
| 4.11.3 | Xác minh rằng bộ nhớ GPU được cách ly giữa các khối lượng công việc sử dụng SR-IOV, MIG (Multi-Instance GPU), hoặc phân vùng phần cứng tương đương với việc làm sạch bộ nhớ giữa các công việc. |   2    |   D/V   |
| 4.11.4 | Xác minh rằng chuỗi cung ứng phần cứng AI bao gồm việc xác thực nguồn gốc với các chứng nhận từ nhà sản xuất và kiểm tra tính toàn vẹn của bao bì chống giả mạo.                                |   3    |    V    |
| 4.11.5 | Xác minh rằng các mô-đun bảo mật phần cứng (HSM) bảo vệ trọng số mô hình AI và khóa mật mã với chứng nhận FIPS 140-2 Cấp 3 hoặc Common Criteria EAL4+.                                          |   3    |   D/V   |

---

## C4.12 Hạ tầng Trí tuệ Nhân tạo Phân tán & Biên

Triển khai AI phân tán an toàn bao gồm điện toán biên, học liên kết và kiến trúc đa địa điểm.

|   #    | Mô tả                                                                                                                                                                        | Cấp độ | Vai trò |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 4.12.1 | Xác minh rằng các thiết bị AI biên xác thực với hạ tầng trung tâm bằng TLS hai chiều sử dụng chứng chỉ thiết bị được thay đổi theo chính sách quản lý chứng chỉ của tổ chức. |   2    |   D/V   |
| 4.12.2 | Xác minh rằng các thiết bị biên thực hiện khởi động an toàn với chữ ký đã được xác minh và bảo vệ quay lui để ngăn các cuộc tấn công hạ cấp phần mềm cơ sở.                  |   2    |   D/V   |
| 4.12.3 | Xác minh rằng phối hợp AI phân tán sử dụng các thuật toán đồng thuận chịu lỗi Byzantine với việc xác thực người tham gia và phát hiện nút độc hại.                           |   3    |   D/V   |
| 4.12.4 | Xác nhận rằng giao tiếp từ edge đến cloud bao gồm điều tiết băng thông, nén dữ liệu và khả năng hoạt động ngoại tuyến với lưu trữ cục bộ an toàn.                            |   3    |   D/V   |

---

## C4.13 Bảo mật Hạ tầng Đa đám mây & Lai

Bảo mật các khối lượng công việc AI trên nhiều nhà cung cấp đám mây và các triển khai đám mây lai kết hợp tại chỗ.

|   #    | Mô tả                                                                                                                                                                                        | Cấp độ | Vai trò |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 4.13.1 | Xác minh rằng việc triển khai AI đa đám mây sử dụng liên kết danh tính không phụ thuộc vào đám mây (OIDC, SAML) với quản lý chính sách tập trung trên các nhà cung cấp.                      |   2    |   D/V   |
| 4.13.2 | Xác minh rằng việc chuyển dữ liệu chéo đám mây sử dụng mã hóa đầu cuối với khóa do khách hàng quản lý và kiểm soát cư trú dữ liệu được thực thi theo từng khu vực pháp lý.                   |   2    |   D/V   |
| 4.13.3 | Xác minh rằng các khối lượng công việc AI đám mây lai thực hiện chính sách bảo mật nhất quán trên cả môi trường tại chỗ và đám mây với giám sát và cảnh báo thống nhất.                      |   2    |   D/V   |
| 4.13.4 | Xác nhận rằng việc ngăn ngừa khóa nhà cung cấp đám mây bao gồm hạ tầng dưới dạng mã có thể di động, các API chuẩn hóa và khả năng xuất dữ liệu với công cụ chuyển đổi định dạng.             |   3    |    V    |
| 4.13.5 | Xác minh rằng tối ưu hóa chi phí đa đám mây bao gồm các biện pháp kiểm soát bảo mật ngăn ngừa sự lan rộng tài nguyên cũng như các khoản phí chuyển dữ liệu không được phép giữa các đám mây. |   3    |    V    |

---

## C4.14 Tự động hóa Hạ tầng & Bảo mật GitOps

Tự động hóa các pipeline hạ tầng bảo mật và quy trình làm việc GitOps cho quản lý hạ tầng AI.

|   #    | Mô tả                                                                                                                                                                                          | Cấp độ | Vai trò |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 4.14.1 | Xác minh rằng các kho GitOps yêu cầu các cam kết được ký bằng khóa GPG và có các quy tắc bảo vệ nhánh ngăn chặn việc đẩy trực tiếp lên các nhánh chính.                                        |   2    |   D/V   |
| 4.14.2 | Xác minh rằng tự động hóa hạ tầng bao gồm phát hiện sai lệch với khả năng khắc phục và phục hồi tự động được kích hoạt theo yêu cầu phản hồi của tổ chức đối với các thay đổi không được phép. |   2    |   D/V   |
| 4.14.3 | Xác minh rằng việc cung cấp hạ tầng tự động bao gồm xác nhận chính sách bảo mật với việc chặn triển khai đối với các cấu hình không tuân thủ.                                                  |   2    |   D/V   |
| 4.14.4 | Xác minh rằng các bí mật tự động hóa hạ tầng được quản lý thông qua các bộ điều hành bí mật bên ngoài (External Secrets Operator, Bank-Vaults) với chức năng tự động xoay vòng.                |   2    |   D/V   |
| 4.14.5 | Xác minh rằng hạ tầng tự phục hồi bao gồm việc kết hợp sự kiện bảo mật với phản ứng sự cố tự động và các quy trình thông báo cho các bên liên quan.                                            |   3    |    V    |

---

## C4.15 An ninh Hạ tầng Kháng Lượng tử

Chuẩn bị hạ tầng AI để đối phó với các mối đe dọa từ điện toán lượng tử thông qua mật mã hậu lượng tử và các giao thức an toàn lượng tử.

|   #    | Mô tả                                                                                                                                                                                      | Cấp độ | Vai trò |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 4.15.1 | Xác minh rằng hạ tầng AI triển khai các thuật toán mật mã hậu lượng tử được NIST phê duyệt (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) cho trao đổi khóa và chữ ký số.                  |   3    |   D/V   |
| 4.15.2 | Xác minh rằng các hệ thống phân phối khóa lượng tử (QKD) được triển khai cho truyền thông AI có bảo mật cao với các giao thức quản lý khóa an toàn với lượng tử.                           |   3    |   D/V   |
| 4.15.3 | Xác minh rằng các khung linh hoạt mật mã cho phép di chuyển nhanh chóng sang các thuật toán hậu lượng tử mới với việc tự động xoay vòng chứng chỉ và khóa.                                 |   3    |   D/V   |
| 4.15.4 | Xác minh rằng mô hình hóa mối đe dọa lượng tử đánh giá mức độ dễ bị tấn công của hạ tầng AI trước các cuộc tấn công lượng tử với các mốc thời gian di cư được ghi chép và đánh giá rủi ro. |   3    |    V    |
| 4.15.5 | Xác minh rằng các hệ thống mật mã lai cổ điển-khối lượng tử cung cấp phòng thủ đa lớp trong giai đoạn chuyển tiếp lượng tử cùng với việc giám sát hiệu suất.                               |   3    |   D/V   |

---

## C4.16 Tính Toán Bảo Mật & Khu Vực Bảo Mật An Toàn

Bảo vệ các khối lượng công việc AI và trọng số mô hình bằng cách sử dụng môi trường thực thi đáng tin cậy dựa trên phần cứng và công nghệ điện toán bảo mật.

|   #    | Mô tả                                                                                                                                                                       | Cấp độ | Vai trò |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 4.16.1 | Xác minh rằng các mô hình AI nhạy cảm chạy bên trong các vùng enclave Intel SGX, AMD SEV-SNP hoặc ARM TrustZone với bộ nhớ được mã hóa và xác thực attest.                  |   3    |   D/V   |
| 4.16.2 | Xác minh rằng các container bảo mật (Kata Containers, gVisor với tính toán bảo mật) cách ly các khối công việc AI bằng mã hóa bộ nhớ được thực thi bởi phần cứng.           |   3    |   D/V   |
| 4.16.3 | Xác minh rằng việc chứng thực từ xa xác nhận tính toàn vẹn của enclave trước khi tải các mô hình AI bằng chứng mật mã về tính xác thực của môi trường thực thi.             |   3    |   D/V   |
| 4.16.4 | Xác nhận rằng các dịch vụ suy luận AI bảo mật ngăn chặn việc trích xuất mô hình thông qua tính toán được mã hóa với trọng số mô hình được đóng gói và thực thi được bảo vệ. |   3    |   D/V   |
| 4.16.5 | Xác minh rằng điều phối môi trường thực thi tin cậy quản lý vòng đời vùng bảo mật với xác thực từ xa và các kênh truyền thông được mã hóa.                                  |   3    |   D/V   |
| 4.16.6 | Xác minh rằng tính toán đa bên bảo mật (SMPC) cho phép đào tạo AI hợp tác mà không tiết lộ bộ dữ liệu cá nhân hoặc các tham số mô hình.                                     |   3    |   D/V   |

---

## C4.17 Hạ tầng Không Kiến thức

Triển khai các hệ thống bằng chứng không tiết lộ để xác minh và xác thực AI bảo vệ quyền riêng tư mà không tiết lộ thông tin nhạy cảm.

|   #    | Mô tả                                                                                                                                                                                      | Cấp độ | Vai trò |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 4.17.1 | Xác minh rằng bằng chứng không tiết lộ thông tin (ZK-SNARKs, ZK-STARKs) xác thực tính toàn vẹn của mô hình AI và nguồn gốc đào tạo mà không tiết lộ trọng số mô hình hoặc dữ liệu đào tạo. |   3    |   D/V   |
| 4.17.2 | Xác minh rằng các hệ thống xác thực dựa trên ZK cho phép xác minh người dùng bảo vệ quyền riêng tư cho các dịch vụ AI mà không tiết lộ thông tin liên quan đến danh tính.                  |   3    |   D/V   |
| 4.17.3 | Xác minh rằng các giao thức giao điểm tập hợp riêng tư (PSI) cho phép đối chiếu dữ liệu an toàn cho AI liên kết mà không làm lộ các tập dữ liệu cá nhân.                                   |   3    |   D/V   |
| 4.17.4 | Xác minh rằng các hệ thống học máy không tiết lộ thông tin (ZKML) cho phép suy luận AI có thể xác minh với bằng chứng mật mã về tính đúng đắn của phép tính.                               |   3    |   D/V   |
| 4.17.5 | Xác minh rằng ZK-rollups cung cấp xử lý giao dịch AI có khả năng mở rộng, bảo vệ quyền riêng tư với xác minh theo lô và giảm tải tính toán.                                                |   3    |   D/V   |

---

## C4.18 Ngăn ngừa Tấn công Kênh bên

Bảo vệ hạ tầng AI khỏi các cuộc tấn công kênh bên dựa trên thời gian, năng lượng, điện từ và bộ nhớ đệm có thể làm rò rỉ thông tin nhạy cảm.

|   #    | Mô tả                                                                                                                                                                                     | Cấp độ | Vai trò |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 4.18.1 | Xác minh rằng thời gian suy luận AI được chuẩn hóa bằng cách sử dụng các thuật toán thời gian không đổi và thêm đệm để ngăn chặn các cuộc tấn công trích xuất mô hình dựa trên thời gian. |   3    |   D/V   |
| 4.18.2 | Xác minh rằng bảo vệ phân tích công suất bao gồm việc tiêm nhiễu, lọc dòng điện và các mô hình thực thi ngẫu nhiên cho phần cứng AI.                                                      |   3    |   D/V   |
| 4.18.3 | Xác minh rằng biện pháp giảm thiểu kênh bên bên dựa trên bộ nhớ đệm sử dụng phân vùng bộ nhớ đệm, ngẫu nhiên hóa và các lệnh xả để ngăn chặn rò rỉ thông tin.                             |   3    |   D/V   |
| 4.18.4 | Xác minh rằng bảo vệ phát xạ điện từ bao gồm che chắn, lọc tín hiệu và xử lý ngẫu nhiên để ngăn chặn các cuộc tấn công kiểu TEMPEST.                                                      |   3    |   D/V   |
| 4.18.5 | Xác minh rằng các biện pháp phòng thủ kênh bên vi kiến trúc bao gồm kiểm soát thực thi dự đoán và che giấu mẫu truy cập bộ nhớ.                                                           |   3    |   D/V   |

---

## C4.19 An ninh Phần cứng AI Chuyên biệt & Như thần kinh

Bảo mật các kiến trúc phần cứng AI mới nổi bao gồm chip thần kinh, FPGA, ASIC tùy chỉnh và hệ thống tính toán quang học.

|   #    | Mô tả                                                                                                                                                               | Cấp độ | Vai trò |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 4.19.1 | Xác nhận rằng bảo mật chip thần kinh bao gồm mã hóa mẫu xung, bảo vệ trọng số kết nối thần kinh, và xác thực quy tắc học dựa trên phần cứng.                        |   3    |   D/V   |
| 4.19.2 | Xác minh rằng các bộ tăng tốc AI dựa trên FPGA thực hiện mã hóa bitstream, cơ chế chống giả mạo và quá trình tải cấu hình an toàn với các bản cập nhật có xác thực. |   3    |   D/V   |
| 4.19.3 | Xác minh rằng bảo mật ASIC tùy chỉnh bao gồm các bộ xử lý bảo mật trên chip, gốc tin cậy phần cứng, và lưu trữ khóa an toàn với khả năng phát hiện can thiệp.       |   3    |   D/V   |
| 4.19.4 | Xác minh rằng các hệ thống điện toán quang học triển khai mã hóa quang an toàn lượng tử, chuyển mạch quang học bảo mật và xử lý tín hiệu quang được bảo vệ.         |   3    |   D/V   |
| 4.19.5 | Xác minh rằng chip AI lai tương tự-số bao gồm tính toán tương tự an toàn, lưu trữ trọng số được bảo vệ và chuyển đổi tương tự-số được xác thực.                     |   3    |   D/V   |

---

## C4.20 Hạ tầng Tính toán Bảo vệ Quyền riêng tư

Triển khai các biện pháp kiểm soát hạ tầng cho tính toán bảo vệ quyền riêng tư nhằm bảo vệ dữ liệu nhạy cảm trong quá trình xử lý và phân tích AI.

|   #    | Mô tả                                                                                                                                                                                   | Cấp độ | Vai trò |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 4.20.1 | Xác minh rằng cơ sở hạ tầng mã hóa đồng hình cho phép tính toán được mã hóa trên các khối lượng công việc AI nhạy cảm với việc xác thực tính toàn vẹn mật mã và giám sát hiệu suất.     |   3    |   D/V   |
| 4.20.2 | Xác nhận rằng các hệ thống truy xuất thông tin riêng tư cho phép truy vấn cơ sở dữ liệu mà không tiết lộ mẫu truy vấn, đồng thời bảo vệ mật mã các mẫu truy cập.                        |   3    |   D/V   |
| 4.20.3 | Xác minh rằng các giao thức tính toán đa bên an toàn cho phép suy luận AI bảo vệ quyền riêng tư mà không tiết lộ các đầu vào cá nhân hoặc các phép tính trung gian.                     |   3    |   D/V   |
| 4.20.4 | Xác minh rằng quản lý khóa bảo vệ quyền riêng tư bao gồm tạo khóa phân tán, mật mã ngưỡng, và xoay khóa an toàn với bảo vệ phần cứng.                                                   |   3    |   D/V   |
| 4.20.5 | Xác minh rằng hiệu suất tính toán bảo vệ quyền riêng tư được tối ưu hóa thông qua việc gom nhóm, lưu bộ nhớ đệm và tăng tốc phần cứng đồng thời duy trì các đảm bảo bảo mật mật mã học. |   3    |   D/V   |

---

## C4.15 Bảo mật Tích hợp Đám mây và Triển khai Lai trong Khung Agent

Các biện pháp kiểm soát bảo mật cho các khung tác tử tích hợp đám mây với kiến trúc lai tại chỗ/đám mây.

|   #    | Mô tả                                                                                                                                        | Cấp độ | Vai trò |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 4.15.1 | Xác minh rằng tích hợp lưu trữ đám mây sử dụng mã hóa đầu cuối với quản lý khóa do tác nhân kiểm soát.                                       |   1    |   D/V   |
| 4.15.2 | Xác minh rằng ranh giới bảo mật của triển khai lai được xác định rõ ràng với các kênh giao tiếp được mã hóa.                                 |   2    |   D/V   |
| 4.15.3 | Xác minh rằng truy cập tài nguyên đám mây bao gồm xác thực không tin cậy với việc xác thực liên tục.                                         |   2    |   D/V   |
| 4.15.4 | Xác minh rằng các yêu cầu về cư trú dữ liệu được thực thi thông qua chứng nhận mật mã về vị trí lưu trữ.                                     |   3    |   D/V   |
| 4.15.5 | Xác minh rằng các đánh giá bảo mật của nhà cung cấp đám mây bao gồm việc mô hình hóa mối đe dọa và đánh giá rủi ro cụ thể cho từng tác nhân. |   3    |   D/V   |

---

## Tài liệu tham khảo

* [NIST Cybersecurity Framework 2.0](https://www.nist.gov/cyberframework)
* [CIS Controls v8](https://www.cisecurity.org/controls/v8)
* [OWASP Container Security Verification Standard](https://github.com/OWASP/Container-Security-Verification-Standard)
* [Kubernetes Security Best Practices](https://kubernetes.io/docs/concepts/security/)
* [SLSA Supply Chain Security Framework](https://slsa.dev/)
* [NIST SP 800-190: Application Container Security Guide](https://csrc.nist.gov/publications/detail/sp/800-190/final)
* [Cloud Security Alliance: Cloud Controls Matrix](https://cloudsecurityalliance.org/research/cloud-controls-matrix/)
* [ENISA: Secure Infrastructure Design](https://www.enisa.europa.eu/topics/critical-information-infrastructures-and-services)
* [NIST SP 800-53: Security Controls for Federal Information Systems](https://csrc.nist.gov/publications/detail/sp/800-53/rev-5/final)
* [ISO 27001:2022 Information Security Management](https://www.iso.org/standard/27001)
* [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
* [CIS Kubernetes Benchmark](https://www.cisecurity.org/benchmark/kubernetes)
* [FIPS 140-2 Security Requirements](https://csrc.nist.gov/publications/detail/fips/140/2/final)
* [NIST SP 800-207: Zero Trust Architecture](https://csrc.nist.gov/publications/detail/sp/800-207/final)
* [IEEE 2857: Privacy Engineering for AI Systems](https://standards.ieee.org/ieee/2857/7273/)
* [NIST SP 800-161: Cybersecurity Supply Chain Risk Management](https://csrc.nist.gov/publications/detail/sp/800-161/rev-1/final)
* [NIST Post-Quantum Cryptography Standards](https://csrc.nist.gov/Projects/post-quantum-cryptography)
* [Intel SGX Developer Guide](https://www.intel.com/content/www/us/en/developer/tools/software-guard-extensions/overview.html)
* [AMD SEV-SNP White Paper](https://www.amd.com/system/files/TechDocs/SEV-SNP-strengthening-vm-isolation-with-integrity-protection-and-more.pdf)
* [ARM TrustZone Technology](https://developer.arm.com/ip-products/security-ip/trustzone)
* [ZK-SNARKs: A Gentle Introduction](https://blog.ethereum.org/2016/12/05/zksnarks-in-a-nutshell/)
* [NIST SP 800-57: Cryptographic Key Management](https://csrc.nist.gov/publications/detail/sp/800-57-part-1/rev-5/final)
* [Side-Channel Attack Countermeasures](https://link.springer.com/book/10.1007/978-3-319-75268-6)
* [Neuromorphic Computing Security Challenges](https://ieeexplore.ieee.org/document/9458103)
* [FPGA Security: Fundamentals, Evaluation, and Countermeasures](https://link.springer.com/book/10.1007/978-3-319-90385-9)
* [Microsoft SEAL: Homomorphic Encryption Library](https://github.com/Microsoft/SEAL)
* [HElib: Homomorphic Encryption Library](https://github.com/homenc/HElib)
* [PALISADE Lattice Cryptography Library](https://palisade-crypto.org/)
* [Differential Privacy: A Survey of Results](https://link.springer.com/chapter/10.1007/978-3-540-79228-4_1)
* [Secure Aggregation for Federated Learning](https://eprint.iacr.org/2017/281.pdf)
* [Private Information Retrieval: Concepts and Constructions](https://link.springer.com/book/10.1007/978-3-030-16234-8)

