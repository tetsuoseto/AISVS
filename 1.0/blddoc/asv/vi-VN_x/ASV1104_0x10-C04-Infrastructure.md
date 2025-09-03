# C4 Cơ sở hạ tầng, Cấu hình và Bảo mật triển khai

## Mục tiêu kiểm soát

Hạ tầng AI phải được củng cố để chống leo thang đặc quyền, giả mạo chuỗi cung ứng và di chuyển ngang trong hệ thống thông qua cấu hình an toàn, cô lập thời gian chạy, các pipeline triển khai đáng tin cậy và giám sát toàn diện. Chỉ các thành phần và cấu hình hạ tầng được cấp phép và xác thực mới đến môi trường sản xuất thông qua các quy trình có kiểm soát nhằm duy trì an ninh, tính toàn vẹn và khả năng kiểm toán.

Mục tiêu Bảo mật Cốt lõi: Chỉ các thành phần hạ tầng được ký số và quét lỗ hổng bảo mật mới đến môi trường sản xuất thông qua các pipeline xác thực tự động, nhằm thực thi các chính sách bảo mật và duy trì dấu vết kiểm toán bất biến.

---

## C4.1 Cách ly môi trường thời gian chạy

Ngăn chặn việc thoát khỏi container và leo thang đặc quyền thông qua các cơ chế cô lập ở mức kernel và kiểm soát truy cập bắt buộc (MAC).

|   #   | Mô tả                                                                                                                                                                                                                                   | Cấp độ | Vai trò |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 4.1.1 | Xác minh rằng tất cả các container AI đều loại bỏ mọi khả năng Linux, trừ CAP_SETUID, CAP_SETGID, và các khả năng được yêu cầu rõ ràng được ghi nhận trong các tiêu chuẩn bảo mật.                                                      |   1    |   D/V   |
| 4.1.2 | Xác minh rằng các cấu hình seccomp chặn tất cả lệnh gọi hệ thống, trừ những lệnh gọi hệ thống nằm trong danh sách cho phép đã được phê duyệt trước, với các vi phạm sẽ làm container dừng và tạo cảnh báo bảo mật.                      |   1    |   D/V   |
| 4.1.3 | Xác minh rằng các tải công việc AI chạy với hệ thống tệp gốc ở chế độ chỉ đọc, tmpfs cho dữ liệu tạm thời, và các volume được đặt tên cho dữ liệu dài hạn với các tùy chọn gắn noexec được bắt buộc.                                    |   2    |   D/V   |
| 4.1.4 | Xác minh rằng giám sát thời gian chạy dựa trên eBPF (Falco, Tetragon, hoặc tương đương) có thể phát hiện các nỗ lực leo thang đặc quyền và tự động kết thúc các tiến trình vi phạm trong phạm vi thời gian đáp ứng do tổ chức quy định. |   2    |   D/V   |
| 4.1.5 | Xác nhận rằng các công việc AI có rủi ro cao được thực thi trong các môi trường cách ly phần cứng (Intel TXT, AMD SVM hoặc các nút bare-metal dành riêng) kèm theo xác thực.                                                            |   3    |   D/V   |

---

## C4.2 Quy trình Xây dựng và Triển khai được bảo mật

Đảm bảo tính toàn vẹn mật mã và bảo mật chuỗi cung ứng thông qua các bản dựng có thể tái tạo và các artefact được ký.

|   #   | Mô tả                                                                                                                                                                                                              | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 4.2.1 | Xác minh rằng hạ tầng dưới dạng mã (IaC) được quét bằng các công cụ (tfsec, Checkov hoặc Terrascan) ở mỗi commit, chặn merge khi phát hiện ở mức CRITICAL hoặc HIGH.                                               |   1    |   D/V   |
| 4.2.2 | Đảm bảo các lần dựng container có thể tái tạo với các giá trị băm SHA-256 giống hệt nhau giữa các lần dựng và tạo các chứng thực nguồn gốc SLSA Level 3 được ký bằng Sigstore.                                     |   1    |   D/V   |
| 4.2.3 | Xác minh rằng các hình ảnh container nhúng SBOM theo CycloneDX hoặc SPDX và được ký bằng Cosign trước khi đẩy lên registry; các hình ảnh chưa ký sẽ bị từ chối khi triển khai.                                     |   2    |   D/V   |
| 4.2.4 | Xác minh rằng các pipeline CI/CD sử dụng mã thông báo OIDC từ HashiCorp Vault, các vai trò IAM của AWS, hoặc danh tính được quản lý của Azure với tuổi thọ không vượt quá giới hạn của chính sách bảo mật tổ chức. |   2    |   D/V   |
| 4.2.5 | Xác minh rằng chữ ký Cosign và nguồn gốc SLSA được xác thực trong quá trình triển khai trước khi thực thi container, và các lỗi xác thực khiến quá trình triển khai thất bại.                                      |   2    |   D/V   |
| 4.2.6 | Xác minh rằng các môi trường xây dựng chạy trong các container tạm thời hoặc VM, không có lưu trữ lâu dài và được cô lập về mặt mạng khỏi VPC sản xuất.                                                            |   2    |   D/V   |

---

## C4.3 Bảo mật mạng và Kiểm soát truy cập

Triển khai mạng Zero Trust với các chính sách từ chối mặc định và truyền thông được mã hóa.

|   #   | Mô tả                                                                                                                                                                                                                     | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 4.3.1 | Xác minh rằng Kubernetes NetworkPolicies hoặc bất kỳ giải pháp tương đương nào thực hiện từ chối mặc định cho lưu lượng đến và đi (ingress/egress) với các quy tắc cho phép rõ ràng các cổng cần thiết (443, 8080, v.v.). |   1    |   D/V   |
| 4.3.2 | Xác minh rằng SSH (cổng 22), RDP (cổng 3389), và các điểm cuối metadata đám mây (169.254.169.254) bị chặn hoặc yêu cầu xác thực dựa trên chứng chỉ.                                                                       |   1    |   D/V   |
| 4.3.3 | Xác minh rằng lưu lượng ra được lọc qua các proxy HTTP/HTTPS (Squid, Istio, hoặc cổng NAT đám mây) với danh sách cho phép tên miền và các yêu cầu bị chặn được ghi lại.                                                   |   2    |   D/V   |
| 4.3.4 | Xác minh rằng giao tiếp giữa các dịch vụ sử dụng TLS xác thực hai chiều (mTLS) với chứng chỉ được đổi mới theo chính sách của tổ chức và xác thực chứng chỉ được bắt buộc (không có cờ skip-verify).                      |   2    |   D/V   |
| 4.3.5 | Xác nhận rằng hạ tầng AI chạy trong các VPCs/VNets riêng biệt, không có truy cập Internet trực tiếp và chỉ giao tiếp qua các cổng NAT hoặc máy chủ bastion.                                                               |   2    |   D/V   |

---

## C4.4 Bí mật và Quản lý khóa mật mã

Bảo vệ thông tin xác thực thông qua lưu trữ dựa trên phần cứng và quay vòng tự động với truy cập theo mô hình không tin tưởng.

|   #   | Mô tả                                                                                                                                                                                                                  | Cấp độ | Vai trò |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 4.4.1 | Xác nhận rằng các bí mật được lưu trữ trong HashiCorp Vault, AWS Secrets Manager, Azure Key Vault hoặc Google Secret Manager với mã hóa khi lưu trữ bằng AES-256.                                                      |   1    |   D/V   |
| 4.4.2 | Xác minh rằng các khóa mã hóa được tạo ra trong các HSM cấp độ 2 của FIPS 140-2 (AWS CloudHSM, Azure Dedicated HSM) với chu kỳ quay khóa theo chính sách mật mã của tổ chức.                                           |   1    |   D/V   |
| 4.4.3 | Xác nhận rằng việc xoay vòng bí mật được tự động hóa với triển khai không gián đoạn và việc xoay vòng ngay lập tức được kích hoạt bởi sự thay đổi nhân sự hoặc sự cố bảo mật.                                          |   2    |   D/V   |
| 4.4.4 | Đảm bảo các hình ảnh container được quét bằng các công cụ (GitLeaks, TruffleHog, hoặc detect-secrets) để chặn các quá trình dựng chứa khóa API, mật khẩu hoặc chứng chỉ.                                               |   2    |   D/V   |
| 4.4.5 | Xác minh rằng truy cập bí mật đến môi trường sản xuất yêu cầu Xác thực đa yếu tố (MFA) với token phần cứng (YubiKey, FIDO2) và được ghi lại bằng nhật ký kiểm toán bất biến kèm danh tính người dùng và dấu thời gian. |   2    |   D/V   |
| 4.4.6 | Xác nhận rằng bí mật được tiêm thông qua Kubernetes Secrets, các volume được gắn, hoặc các container khởi tạo và đảm bảo bí mật không bao giờ được nhúng vào biến môi trường hoặc hình ảnh.                            |   2    |   D/V   |

---

## C4.5 Cô lập và xác thực tải trọng AI

Cô lập các mô hình trí tuệ nhân tạo không đáng tin cậy trong các sandbox an toàn với phân tích hành vi toàn diện.

|   #   | Mô tả                                                                                                                                                                                          | Cấp độ | Vai trò |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 4.5.1 | Xác nhận rằng các mô hình AI bên ngoài được thực thi trong gVisor, microVMs (như Firecracker, CrossVM), hoặc container Docker với các tham số --security-opt=no-new-privileges và --read-only. |   1    |   D/V   |
| 4.5.2 | Xác minh rằng các môi trường sandbox không có kết nối mạng (--network=none) hoặc chỉ cho phép truy cập localhost và tất cả các yêu cầu từ bên ngoài bị chặn bởi các quy tắc iptables.          |   1    |   D/V   |
| 4.5.3 | Xác minh rằng xác thực mô hình AI bao gồm kiểm tra đội đỏ tự động với phạm vi kiểm thử do tổ chức xác định và phân tích hành vi để phát hiện cửa hậu.                                          |   2    |   D/V   |
| 4.5.4 | Xác minh rằng trước khi một mô hình AI được đưa lên sản xuất, kết quả sandbox của nó được ký bằng chữ ký số bởi nhân sự bảo mật có thẩm quyền và được lưu trong nhật ký kiểm toán bất biến.    |   2    |   D/V   |
| 4.5.5 | Xác minh rằng các môi trường sandbox được hủy và được tạo lại từ hình ảnh vàng giữa các lần đánh giá, với việc dọn dẹp đầy đủ hệ thống tập tin và bộ nhớ.                                      |   2    |   D/V   |

---

## C4.6 Giám sát Bảo mật Cơ sở hạ tầng

Liên tục quét và giám sát hạ tầng CNTT với khắc phục tự động và cảnh báo theo thời gian thực.

|   #   | Mô tả                                                                                                                                                                                 | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 4.6.1 | Xác minh rằng các hình ảnh container được quét theo lịch của tổ chức với các lỗ hổng CRITICAL ngăn triển khai dựa trên ngưỡng rủi ro của tổ chức.                                     |   1    |   D/V   |
| 4.6.2 | Xác minh rằng cơ sở hạ tầng đáp ứng CIS Benchmarks hoặc các kiểm soát NIST 800-53 với ngưỡng tuân thủ do tổ chức định nghĩa và tự động khắc phục đối với các kiểm tra không đạt.      |   1    |   D/V   |
| 4.6.3 | Xác nhận rằng các lỗ hổng có mức độ nghiêm trọng cao được vá đúng theo lộ trình quản lý rủi ro của tổ chức, với các thủ tục khẩn cấp dành cho các CVE đang bị khai thác tích cực.     |   2    |   D/V   |
| 4.6.4 | Xác minh rằng các cảnh báo bảo mật tích hợp với các nền tảng SIEM (Splunk, Elastic hoặc Sentinel) bằng các định dạng CEF hoặc STIX/TAXII và được làm giàu tự động.                    |   2    |    V    |
| 4.6.5 | Xác minh rằng các chỉ số hạ tầng được xuất sang các hệ thống giám sát (Prometheus, DataDog) với các bảng điều khiển SLA và báo cáo điều hành.                                         |   3    |    V    |
| 4.6.6 | Xác minh rằng sự lệch cấu hình được phát hiện bằng các công cụ (Chef InSpec, AWS Config) theo các yêu cầu giám sát của tổ chức với khả năng tự động khôi phục các thay đổi trái phép. |   2    |   D/V   |

---

## C4.7 Quản lý tài nguyên hạ tầng AI

Ngăn chặn các cuộc tấn công làm cạn kiệt tài nguyên và đảm bảo phân bổ tài nguyên công bằng thông qua hạn ngạch và giám sát.

|   #   | Mô tả                                                                                                                                                                                                                  | Cấp độ | Vai trò |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 4.7.1 | Xác nhận rằng việc sử dụng GPU/TPU được giám sát với các cảnh báo được kích hoạt tại ngưỡng do tổ chức quy định và tự động mở rộng quy mô hoặc cân bằng tải được kích hoạt dựa trên các chính sách quản lý dung lượng. |   1    |   D/V   |
| 4.7.2 | Xác nhận rằng các chỉ số khối lượng công việc AI (độ trễ suy diễn, thông lượng, tỷ lệ lỗi) được thu thập theo các yêu cầu giám sát của tổ chức và được tương quan với mức sử dụng cơ sở hạ tầng.                       |   1    |   D/V   |
| 4.7.3 | Xác minh rằng ResourceQuotas của Kubernetes hoặc các biện pháp tương đương giới hạn mỗi workload theo các chính sách phân bổ nguồn lực của tổ chức với các giới hạn nghiêm ngặt được thực thi.                         |   2    |   D/V   |
| 4.7.4 | Xác minh rằng việc theo dõi chi phí ghi nhận chi tiêu theo từng tải công việc và từng khách thuê, với các cảnh báo dựa trên ngưỡng ngân sách của tổ chức và các cơ chế tự động kiểm soát khi chi vượt ngân sách.       |   2    |    V    |
| 4.7.5 | Xác minh rằng lập kế hoạch dung lượng sử dụng dữ liệu lịch sử với các chu kỳ dự báo do tổ chức định nghĩa và cấp phát tài nguyên tự động dựa trên các mẫu nhu cầu.                                                     |   3    |    V    |
| 4.7.6 | Xác minh rằng tình trạng quá tải tài nguyên kích hoạt các cơ chế ngắt mạch theo yêu cầu phản ứng của tổ chức, bao gồm giới hạn lưu lượng dựa trên chính sách dung lượng và cô lập tải công việc.                       |   2    |   D/V   |

---

## C4.8 Phân tách môi trường và Kiểm soát thăng cấp

Đảm bảo ranh giới môi trường nghiêm ngặt với các cổng phê duyệt tự động và xác thực bảo mật.

|   #   | Mô tả                                                                                                                                                                                                         | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 4.8.1 | Xác nhận rằng các môi trường dev/test/prod chạy trên các VPCs/VNets riêng biệt và không có vai trò IAM, nhóm bảo mật hoặc kết nối mạng được chia sẻ.                                                          |   1    |   D/V   |
| 4.8.2 | Xác minh rằng việc thăng cấp môi trường đòi hỏi phê duyệt từ những nhân sự được ủy quyền do tổ chức định nghĩa, kèm chữ ký số và nhật ký kiểm toán bất biến.                                                  |   1    |   D/V   |
| 4.8.3 | Xác nhận rằng các môi trường sản xuất chặn truy cập SSH, vô hiệu hóa các điểm cuối gỡ lỗi, và yêu cầu các yêu cầu thay đổi kèm theo thông báo trước của tổ chức, trừ trường hợp khẩn cấp.                     |   2    |   D/V   |
| 4.8.4 | Xác nhận rằng các thay đổi hạ tầng dưới dạng mã (IaC) đòi hỏi đánh giá từ đồng nghiệp kèm kiểm thử tự động và quét bảo mật trước khi ghép vào nhánh chính.                                                    |   2    |   D/V   |
| 4.8.5 | Xác minh rằng dữ liệu phi sản xuất được ẩn danh theo các yêu cầu quyền riêng tư của tổ chức, hoặc được tạo thành từ dữ liệu tổng hợp, hoặc được che phủ dữ liệu hoàn toàn với việc loại bỏ PII được xác nhận. |   2    |   D/V   |
| 4.8.6 | Xác nhận rằng các cổng thăng tiến (promotion gates) bao gồm các bài kiểm tra bảo mật tự động (SAST, DAST, quét container) với yêu cầu không có phát hiện CRITICAL để phê duyệt.                               |   2    |   D/V   |

---

## C4.9 Sao lưu và khôi phục cơ sở hạ tầng

Đảm bảo tính kiên cường của cơ sở hạ tầng thông qua sao lưu tự động, các quy trình khôi phục đã được kiểm tra và khả năng khôi phục sau thảm họa.

|   #   | Mô tả                                                                                                                                                                            | Cấp độ | Vai trò |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 4.9.1 | Xác minh rằng các cấu hình cơ sở hạ tầng được sao lưu theo lịch sao lưu của tổ chức đến các khu vực địa lý khác nhau, với việc triển khai chiến lược sao lưu 3-2-1.              |   1    |   D/V   |
| 4.9.2 | Xác minh rằng các hệ thống sao lưu chạy trên các mạng được cách ly với thông tin xác thực riêng và lưu trữ được cách ly khỏi mạng để bảo vệ khỏi ransomware.                     |   2    |   D/V   |
| 4.9.3 | Xác minh rằng các thủ tục khôi phục được kiểm tra và xác thực thông qua thử nghiệm tự động theo lịch trình của tổ chức, với các mục tiêu RTO và RPO đáp ứng yêu cầu của tổ chức. |   2    |    V    |
| 4.9.4 | Xác minh rằng khôi phục sau thảm họa bao gồm các sổ tay vận hành dành cho AI với phục hồi trọng số mô hình, tái xây dựng cụm GPU và ánh xạ phụ thuộc dịch vụ.                    |   3    |    V    |

---

## C4.10 Tuân thủ và Quản trị Hạ tầng

Duy trì tuân thủ quy định pháp lý thông qua đánh giá liên tục, tài liệu hóa và kiểm soát tự động.

|   #    | Mô tả                                                                                                                                                                          | Cấp độ | Vai trò |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 4.10.1 | Xác nhận rằng tuân thủ cơ sở hạ tầng được đánh giá theo lịch trình của tổ chức đối với các kiểm soát SOC 2, ISO 27001 hoặc FedRAMP, với việc thu thập bằng chứng tự động.      |   2    |   D/V   |
| 4.10.2 | Xác minh rằng tài liệu cơ sở hạ tầng bao gồm sơ đồ mạng, bản đồ luồng dữ liệu và mô hình đe dọa được cập nhật theo các yêu cầu quản lý thay đổi tổ chức.                       |   2    |    V    |
| 4.10.3 | Đảm bảo rằng các thay đổi về cơ sở hạ tầng được thực hiện thông qua đánh giá tác động tuân thủ tự động và quy trình phê duyệt theo quy định đối với các sửa đổi có rủi ro cao. |   3    |   D/V   |

---

## C4.11 Bảo mật phần cứng AI

Bảo mật các thành phần phần cứng dành cho AI, bao gồm GPU, TPU và các bộ tăng tốc AI chuyên dụng.

|   #    | Mô tả                                                                                                                                                                                              | Cấp độ | Vai trò |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 4.11.1 | Xác minh rằng firmware cho bộ tăng tốc AI (GPU BIOS, firmware TPU) được ký số và được cập nhật theo lịch quản lý vá lỗi của tổ chức.                                                               |   2    |   D/V   |
| 4.11.2 | Xác nhận rằng trước khi thực thi khối lượng công việc, tính toàn vẹn của bộ tăng tốc AI được chứng thực bằng chứng thực phần cứng thông qua TPM 2.0, Intel TXT hoặc AMD SVM.                       |   2    |   D/V   |
| 4.11.3 | Xác nhận rằng bộ nhớ GPU được cô lập giữa các tải công việc bằng cách sử dụng SR-IOV, MIG (Multi-Instance GPU), hoặc phân vùng phần cứng tương đương và có cơ chế làm sạch bộ nhớ giữa các tác vụ. |   2    |   D/V   |
| 4.11.4 | Xác nhận rằng chuỗi cung ứng phần cứng AI bao gồm xác minh nguồn gốc với chứng chỉ của nhà sản xuất và xác thực đóng gói có niêm phong chống tráo đổi.                                             |   3    |    V    |
| 4.11.5 | Xác minh rằng các mô-đun an toàn phần cứng (HSM) bảo vệ trọng số của mô hình AI và khóa mật mã với chứng chỉ FIPS 140-2 cấp 3 hoặc Common Criteria EAL4+.                                          |   3    |   D/V   |

---

## C4.12 Cơ sở hạ tầng AI biên và phân tán

Triển khai AI phân tán an toàn, bao gồm điện toán biên, học liên kết phân tán, và kiến trúc đa địa điểm.

|   #    | Mô tả                                                                                                                                                                              | Cấp độ | Vai trò |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 4.12.1 | Xác minh rằng các thiết bị AI biên xác thực với hạ tầng trung tâm bằng TLS hai chiều, với chứng chỉ thiết bị được cấp lại theo chính sách quản lý chứng chỉ của tổ chức.           |   2    |   D/V   |
| 4.12.2 | Xác minh rằng các thiết bị biên triển khai khởi động an toàn với chữ ký được xác thực và có cơ chế bảo vệ chống quay ngược phiên bản, ngăn chặn các cuộc tấn công hạ cấp firmware. |   2    |   D/V   |
| 4.12.3 | Xác minh rằng điều phối AI phân tán sử dụng các thuật toán đồng thuận chịu lỗi Byzantine với xác thực người tham gia và phát hiện nút độc hại.                                     |   3    |   D/V   |
| 4.12.4 | Xác minh rằng edge-to-cloud giao tiếp bao gồm giới hạn băng thông, nén dữ liệu và khả năng hoạt động ngoại tuyến với lưu trữ cục bộ an toàn.                                       |   3    |   D/V   |

---

## C4.13 Bảo mật hạ tầng đa đám mây & hạ tầng lai

Bảo mật các công việc AI trên nhiều nhà cung cấp đám mây và triển khai lai đám mây-tại chỗ.

|   #    | Mô tả                                                                                                                                                                                                   | Cấp độ | Vai trò |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 4.13.1 | Xác nhận rằng các triển khai AI đa đám mây sử dụng liên kết danh tính phi đám mây (OIDC, SAML) với quản lý chính sách tập trung giữa các nhà cung cấp.                                                  |   2    |   D/V   |
| 4.13.2 | Xác nhận rằng việc chuyển dữ liệu giữa các đám mây khác nhau sử dụng mã hóa đầu-cuối với khóa do khách hàng quản lý và các kiểm soát về nơi lưu trữ dữ liệu được thực thi theo từng thẩm quyền pháp lý. |   2    |   D/V   |
| 4.13.3 | Xác minh rằng các khối lượng công việc AI trên đám mây lai triển khai các chính sách bảo mật nhất quán trên các môi trường tại chỗ và đám mây, với giám sát và cảnh báo thống nhất.                     |   2    |   D/V   |
| 4.13.4 | Xác nhận rằng biện pháp ngăn ngừa khóa nhà cung cấp đám mây bao gồm hạ tầng dưới dạng mã có thể di động, API chuẩn hóa, và khả năng xuất dữ liệu với công cụ chuyển đổi định dạng.                      |   3    |    V    |
| 4.13.5 | Xác nhận rằng tối ưu hóa chi phí đa đám mây bao gồm các biện pháp kiểm soát bảo mật ngăn chặn sự lan rộng của tài nguyên cũng như chi phí chuyển dữ liệu giữa các đám mây trái phép.                    |   3    |    V    |

---

## C4.14 Tự động hóa hạ tầng và Bảo mật GitOps

Đảm bảo an toàn cho các pipeline tự động hóa hạ tầng và quy trình GitOps cho quản lý hạ tầng trí tuệ nhân tạo.

|   #    | Mô tả                                                                                                                                                                                                                       | Cấp độ | Vai trò |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 4.14.1 | Xác minh rằng các kho GitOps yêu cầu các commit được ký bằng khóa GPG và các quy tắc bảo vệ nhánh ngăn chặn việc đẩy trực tiếp lên các nhánh chính.                                                                         |   2    |   D/V   |
| 4.14.2 | Xác minh rằng tự động hóa cơ sở hạ tầng bao gồm phát hiện lệch cấu hình với các khả năng khắc phục tự động và quay lại trạng thái trước được kích hoạt theo các yêu cầu ứng phó của tổ chức đối với các thay đổi trái phép. |   2    |   D/V   |
| 4.14.3 | Xác minh rằng việc tự động cấp phát hạ tầng bao gồm xác thực chính sách bảo mật và chặn triển khai đối với các cấu hình không tuân thủ.                                                                                     |   2    |   D/V   |
| 4.14.4 | Xác nhận rằng các bí mật cho tự động hóa hạ tầng được quản lý thông qua các operator bí mật bên ngoài (External Secrets Operator, Bank-Vaults) với quay vòng tự động.                                                       |   2    |   D/V   |
| 4.14.5 | Xác minh rằng hạ tầng tự phục hồi bao gồm sự tương quan của các sự kiện bảo mật với phản ứng sự cố tự động và các quy trình thông báo cho các bên liên quan.                                                                |   3    |    V    |

---

## C4.15 Bảo mật hạ tầng kháng lượng tử

Chuẩn bị hạ tầng AI để đối phó với các mối đe dọa từ máy tính lượng tử thông qua mật mã hậu lượng tử và các giao thức an toàn lượng tử.

|   #    | Mô tả                                                                                                                                                                                        | Cấp độ | Vai trò |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 4.15.1 | Xác minh xem hạ tầng AI có triển khai các thuật toán mật mã sau lượng tử được NIST phê duyệt (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) cho trao đổi khóa và chữ ký số hay không.        |   3    |   D/V   |
| 4.15.2 | Xác minh rằng các hệ thống phân phối khóa lượng tử (QKD) được triển khai cho các liên lạc AI có độ bảo mật cao với các giao thức quản lý khóa an toàn lượng tử.                              |   3    |   D/V   |
| 4.15.3 | Xác nhận rằng các khung linh hoạt về mật mã cho phép chuyển sang nhanh các thuật toán hậu lượng tử mới với tự động quay vòng chứng chỉ và khóa.                                              |   3    |   D/V   |
| 4.15.4 | Xác nhận rằng mô hình hóa đe dọa lượng tử đánh giá tính dễ bị tổn thương của hạ tầng AI trước các cuộc tấn công lượng tử, kèm theo lộ trình chuyển đổi được ghi nhận và các đánh giá rủi ro. |   3    |    V    |
| 4.15.5 | Xác minh rằng các hệ mật mã lai cổ điển-lượng tử cung cấp phòng thủ đa lớp trong giai đoạn chuyển đổi lượng tử và được giám sát hiệu suất.                                                   |   3    |   D/V   |

---

## C4.16 Tính toán Bảo mật và Khu vực An toàn

Bảo vệ các công việc AI và trọng số của mô hình bằng các môi trường thực thi tin cậy dựa trên phần cứng và công nghệ tính toán bí mật.

|   #    | Mô tả                                                                                                                                                                       | Cấp độ | Vai trò |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 4.16.1 | Xác minh rằng các mô hình AI nhạy cảm được thực thi trong các enclave Intel SGX, AMD SEV-SNP hoặc ARM TrustZone với bộ nhớ được mã hóa và xác thực chứng thực.              |   3    |   D/V   |
| 4.16.2 | Xác minh rằng các container bí mật (Kata Containers, gVisor với tính toán bí mật) cô lập khối lượng công việc AI bằng mã hóa bộ nhớ do phần cứng thực thi.                  |   3    |   D/V   |
| 4.16.3 | Xác minh rằng chứng thực từ xa xác nhận tính toàn vẹn của enclave trước khi nạp các mô hình AI, với bằng chứng mật mã cho tính xác thực của môi trường thực thi.            |   3    |   D/V   |
| 4.16.4 | Xác minh rằng các dịch vụ suy luận AI bí mật ngăn chặn việc rút trích mô hình thông qua tính toán được mã hóa với trọng số mô hình được niêm phong và thực thi được bảo vệ. |   3    |   D/V   |
| 4.16.5 | Xác minh rằng việc điều phối môi trường thực thi được tin cậy quản lý vòng đời của khu vực enclave an toàn với chứng thực từ xa và các kênh liên lạc được mã hóa.           |   3    |   D/V   |
| 4.16.6 | Xác minh rằng tính toán đa bên an toàn (SMPC) cho phép đào tạo AI hợp tác mà không lộ các tập dữ liệu riêng lẻ hoặc tham số của mô hình.                                    |   3    |   D/V   |

---

## C4.17 Cơ sở hạ tầng không tiết lộ thông tin

Triển khai hệ thống chứng minh vô kiến thức (ZKP) cho xác minh và xác thực AI nhằm bảo vệ quyền riêng tư mà không tiết lộ thông tin nhạy cảm.

|   #    | Mô tả                                                                                                                                                                                      | Cấp độ | Vai trò |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 4.17.1 | Xác minh rằng các chứng minh vô kiến thức (ZK-SNARKs, ZK-STARKs) có thể xác nhận tính toàn vẹn của mô hình AI và nguồn gốc đào tạo mà không tiết lộ trọng số mô hình hoặc dữ liệu đào tạo. |   3    |   D/V   |
| 4.17.2 | Xác minh rằng các hệ thống xác thực dựa trên ZK cho phép xác thực người dùng nhằm bảo vệ quyền riêng tư cho các dịch vụ AI mà không tiết lộ thông tin liên quan đến danh tính.             |   3    |   D/V   |
| 4.17.3 | Xác minh rằng các giao thức PSI (Private Set Intersection) cho phép ghép nối dữ liệu an toàn cho trí tuệ nhân tạo phân tán mà không tiết lộ các bộ dữ liệu riêng lẻ.                       |   3    |   D/V   |
| 4.17.4 | Xác minh rằng các hệ thống học máy bằng chứng không tiết lộ (ZKML) cho phép các suy luận AI được xác thực với bằng chứng mật mã cho tính toán đúng.                                        |   3    |   D/V   |
| 4.17.5 | Xác minh rằng ZK-rollups cung cấp xử lý giao dịch AI có thể mở rộng và bảo vệ quyền riêng tư, với xác thực theo lô và giảm tải chi phí tính toán.                                          |   3    |   D/V   |

---

## C4.18 Phòng ngừa tấn công Side-Channel

Bảo vệ cơ sở hạ tầng AI khỏi các tấn công kênh phụ dựa trên thời gian, công suất, điện từ và bộ nhớ đệm có thể làm lộ thông tin nhạy cảm.

|   #    | Mô tả                                                                                                                                                                 | Cấp độ | Vai trò |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 4.18.1 | Xác nhận rằng thời gian suy diễn AI được chuẩn hóa bằng các thuật toán thời gian hằng số và đệm để ngăn chặn các cuộc tấn công trích xuất mô hình dựa trên thời gian. |   3    |   D/V   |
| 4.18.2 | Xác nhận rằng các biện pháp bảo vệ chống phân tích công suất bao gồm tiêm nhiễu, lọc đường nguồn và các mẫu thực thi ngẫu nhiên cho phần cứng AI.                     |   3    |   D/V   |
| 4.18.3 | Xác minh rằng biện pháp giảm thiểu kênh cạnh dựa trên cache sử dụng phân vùng cache, ngẫu nhiên hóa, và các lệnh xả để ngăn chặn rò rỉ thông tin.                     |   3    |   D/V   |
| 4.18.4 | Xác nhận rằng bảo vệ khỏi phát xạ điện từ bao gồm che chắn, lọc tín hiệu và xử lý ngẫu nhiên để ngăn chặn các cuộc tấn công theo kiểu TEMPEST.                        |   3    |   D/V   |
| 4.18.5 | Xác nhận rằng các biện pháp phòng thủ vi kiến trúc chống lại tấn công kênh phụ bao gồm kiểm soát thực thi suy diễn và che khuất mẫu truy cập bộ nhớ.                  |   3    |   D/V   |

---

## C4.19 An ninh phần cứng AI Neuromorphic và chuyên dụng

Đảm bảo an toàn cho các kiến trúc phần cứng AI đang nổi lên, bao gồm chip neuromorphic, FPGA, ASIC tùy chỉnh và hệ thống tính toán quang học.

|   #    | Mô tả                                                                                                                                                                          | Cấp độ | Vai trò |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 4.19.1 | Xác minh rằng bảo mật của chip neuromorphic bao gồm mã hóa mẫu xung, bảo vệ trọng số synapse, và xác thực quy tắc học dựa trên phần cứng.                                      |   3    |   D/V   |
| 4.19.2 | Xác minh rằng các bộ tăng tốc AI dựa trên FPGA triển khai mã hóa bitstream, cơ chế chống can thiệp và tải cấu hình an toàn với các bản cập nhật được xác thực.                 |   3    |   D/V   |
| 4.19.3 | Xác minh rằng bảo mật ASIC tùy chỉnh bao gồm các bộ xử lý bảo mật tích hợp trên chip, gốc tin cậy phần cứng và lưu trữ khóa an toàn có khả năng phát hiện can thiệp.           |   3    |   D/V   |
| 4.19.4 | Xác minh rằng các hệ thống tính toán quang học thực hiện mã hóa quang học an toàn trước lượng tử, chuyển mạch quang học được bảo mật, và xử lý tín hiệu quang học được bảo vệ. |   3    |   D/V   |
| 4.19.5 | Xác minh rằng vi mạch AI lai analog-digital bao gồm tính toán tương tự được bảo mật, lưu trữ trọng số được bảo vệ và chuyển đổi analog-to-digital được xác thực.               |   3    |   D/V   |

---

## C4.20 Cơ sở hạ tầng tính toán bảo vệ quyền riêng tư

Triển khai các biện pháp kiểm soát cơ sở hạ tầng cho tính toán bảo toàn quyền riêng tư nhằm bảo vệ dữ liệu nhạy cảm trong quá trình xử lý và phân tích của Trí tuệ nhân tạo (AI).

|   #    | Mô tả                                                                                                                                                                                         | Cấp độ | Vai trò |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 4.20.1 | Xác nhận rằng hạ tầng mã hóa đồng hình cho phép tính toán được mã hóa trên các tải trọng AI nhạy cảm với xác minh tính toàn vẹn mật mã và giám sát hiệu suất.                                 |   3    |   D/V   |
| 4.20.2 | Xác nhận rằng các hệ thống Truy vấn thông tin riêng tư (PIR) cho phép thực hiện truy vấn cơ sở dữ liệu mà không tiết lộ các mẫu truy vấn, thông qua việc bảo vệ các mẫu truy cập bằng mật mã. |   3    |   D/V   |
| 4.20.3 | Xác nhận rằng các giao thức tính toán đa bên an toàn cho phép suy diễn AI được bảo vệ quyền riêng tư mà không tiết lộ đầu vào cá nhân hoặc các tính toán trung gian.                          |   3    |   D/V   |
| 4.20.4 | Xác nhận rằng quản lý khóa bảo mật nhằm bảo vệ quyền riêng tư bao gồm phát sinh khóa phân tán, mật mã ngưỡng và quay vòng khóa an toàn với bảo vệ dựa trên phần cứng.                         |   3    |   D/V   |
| 4.20.5 | Xác minh rằng hiệu suất tính toán bảo vệ quyền riêng tư được tối ưu hóa thông qua xử lý theo lô, bộ nhớ đệm và tăng tốc bằng phần cứng, đồng thời duy trì các đảm bảo an toàn mật mã.         |   3    |   D/V   |

---

## C4.15 Khung tác nhân tích hợp đám mây bảo mật & triển khai lai

Các biện pháp kiểm soát bảo mật cho các khung tác nhân tích hợp đám mây với kiến trúc lai giữa tại chỗ và đám mây.

|   #    | Mô tả                                                                                                                       | Cấp độ | Vai trò |
| :----: | --------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 4.15.1 | Kiểm tra xem tích hợp lưu trữ đám mây có sử dụng mã hóa đầu cuối với quản lý khóa do tác nhân kiểm soát hay không.          |   1    |   D/V   |
| 4.15.2 | Xác minh rằng ranh giới bảo mật của triển khai lai được định nghĩa rõ ràng bằng các kênh truyền thông được mã hóa.          |   2    |   D/V   |
| 4.15.3 | Xác minh rằng quyền truy cập vào tài nguyên đám mây bao gồm xác thực theo mô hình zero-trust và xác thực liên tục.          |   2    |   D/V   |
| 4.15.4 | Xác minh rằng các yêu cầu cư trú dữ liệu được thực thi thông qua chứng thực bằng mật mã của các vị trí lưu trữ.             |   3    |   D/V   |
| 4.15.5 | Xác minh rằng các đánh giá bảo mật của nhà cung cấp đám mây bao gồm mô hình hóa mối đe dọa cho tác nhân và đánh giá rủi ro. |   3    |   D/V   |

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

