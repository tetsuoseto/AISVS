# Bảo mật Hạ tầng, Cấu hình & Triển khai C4

## Mục tiêu Kiểm soát

Cơ sở hạ tầng AI phải được củng cố chống lại việc leo thang đặc quyền, can thiệp chuỗi cung ứng và di chuyển ngang thông qua cấu hình bảo mật, cô lập khi chạy, các quy trình triển khai đáng tin cậy và giám sát toàn diện. Chỉ các thành phần cơ sở hạ tầng đã được xác thực và ủy quyền mới được đưa vào sản xuất thông qua các quy trình kiểm soát nhằm đảm bảo bảo mật, tính toàn vẹn và khả năng kiểm toán.

Mục tiêu Bảo mật Cốt lõi: Chỉ những thành phần hạ tầng được ký kết mật mã và quét lỗ hổng mới được đưa vào sản xuất thông qua các pipeline xác thực tự động, đảm bảo thực thi các chính sách bảo mật và duy trì các hồ sơ kiểm toán bất biến.

---

## C4.1 Cô lập môi trường chạy thời gian

Ngăn chặn thoát container và leo thang đặc quyền thông qua các nguyên thủy cô lập ở cấp độ hệ điều hành.

|   #   | Mô tả                                                                                                                                                                                                                         | Cấp độ | Vai trò |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 4.1.1 | Xác minh rằng tất cả các khối lượng công việc AI chạy với quyền tối thiểu cần thiết trên hệ điều hành, ví dụ như loại bỏ các khả năng Linux không cần thiết trong trường hợp sử dụng container.                               |   1    |   D/V   |
| 4.1.2 | Xác minh rằng các khối lượng công việc được bảo vệ bằng các công nghệ giới hạn khai thác như sandboxing, hồ sơ seccomp, AppArmor, SELinux hoặc tương tự, và cấu hình phù hợp.                                                 |   1    |   D/V   |
| 4.1.3 | Xác minh rằng các khối lượng công việc chạy với hệ thống tệp gốc chỉ đọc, và bất kỳ điểm gắn kết có thể ghi đều được định nghĩa rõ ràng và được tăng cường bảo mật với các tùy chọn hạn chế (ví dụ: noexec, nosuid, nodev).   |   2    |   D/V   |
| 4.1.4 | Xác minh rằng giám sát thời gian chạy phát hiện các hành vi leo thang đặc quyền và thoát container và tự động chấm dứt các tiến trình vi phạm.                                                                                |   2    |   D/V   |
| 4.1.5 | Xác minh rằng các khối lượng công việc AI có rủi ro cao chỉ chạy trong các môi trường cách ly phần cứng (ví dụ: TEEs, trình giám sát đáng tin cậy, hoặc các nút bare-metal) sau khi thực hiện thành công việc xác thực từ xa. |   3    |   D/V   |

---

## C4.2 Dây chuyền Xây dựng & Triển khai An toàn

Đảm bảo tính toàn vẹn mật mã và an ninh chuỗi cung ứng thông qua việc xây dựng có thể tái tạo và các hiện vật đã được ký.

|   #   | Mô tả                                                                                                                                                                                | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 4.2.1 | Xác minh rằng các bản build có thể tái tạo và tạo ra siêu dữ liệu nguồn gốc đã được ký phù hợp với các sản phẩm build, để có thể kiểm chứng độc lập.                                 |   1    |   D/V   |
| 4.2.2 | Xác minh rằng các bản dựng tạo ra bảng kê nguyên liệu phần mềm (SBOM) và được ký trước khi được chấp nhận để triển khai.                                                             |   2    |   D/V   |
| 4.2.3 | Xác minh rằng chữ ký của thành phẩm xây dựng (ví dụ: hình ảnh container) và siêu dữ liệu nguồn gốc được xác thực khi triển khai, và các thành phẩm chưa được xác minh sẽ bị từ chối. |   2    |   D/V   |

---

## C4.3 Bảo mật mạng & Kiểm soát truy cập

Triển khai mạng lưới không tin cậy với các chính sách mặc định từ chối và giao tiếp được mã hóa.

|   #   | Mô tả                                                                                                                                                                                                                                                           | Cấp độ | Vai trò |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 4.3.1 | Xác minh rằng các chính sách mạng thực thi việc từ chối mặc định đối với lưu lượng vào và ra, chỉ cho phép rõ ràng các dịch vụ cần thiết.                                                                                                                       |   1    |   D/V   |
| 4.3.2 | Xác minh rằng các giao thức truy cập quản trị (ví dụ: SSH, RDP) và quyền truy cập vào dịch vụ siêu dữ liệu đám mây đều bị giới hạn và yêu cầu xác thực mạnh.                                                                                                    |   1    |   D/V   |
| 4.3.3 | Xác minh rằng lưu lượng đi ra được giới hạn đến các điểm đến được phê duyệt và tất cả các yêu cầu đều được ghi lại.                                                                                                                                             |   2    |   D/V   |
| 4.3.4 | Xác minh rằng giao tiếp giữa các dịch vụ sử dụng mutual TLS với việc xác thực chứng chỉ và xoay vòng tự động thường xuyên.                                                                                                                                      |   2    |   D/V   |
| 4.3.5 | Xác minh rằng các khối lượng công việc AI và môi trường (phát triển, kiểm thử, sản xuất) chạy trong các phân đoạn mạng tách biệt (VPCs/VNets) không có truy cập trực tiếp internet và không chia sẻ vai trò IAM, nhóm bảo mật hoặc kết nối giữa các môi trường. |   2    |   D/V   |

## C4.4 Quản lý Bí mật & Khóa Mã hóa

Bảo vệ bí mật và khóa mã hóa bằng lưu trữ an toàn, tự động xoay vòng, và kiểm soát truy cập mạnh mẽ.

|   #   | Mô tả                                                                                                                                                                                                                                                          | Cấp độ | Vai trò |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 4.4.1 | Xác minh rằng các bí mật được lưu trữ trong một hệ thống quản lý bí mật chuyên dụng với mã hóa khi lưu trữ và được tách biệt khỏi các khối lượng công việc ứng dụng.                                                                                           |   1    |   D/V   |
| 4.4.2 | Xác minh rằng các khóa mật mã được tạo và lưu trữ trong các mô-đun có hỗ trợ phần cứng (ví dụ, HSM, KMS đám mây).                                                                                                                                              |   1    |   D/V   |
| 4.4.3 | Xác minh rằng việc truy cập vào các bí mật sản xuất yêu cầu xác thực mạnh.                                                                                                                                                                                     |   1    |   D/V   |
| 4.4.4 | Xác minh rằng các bí mật được triển khai đến các ứng dụng tại thời điểm runtime thông qua một hệ thống quản lý bí mật chuyên dụng. Bí mật không được phép nhúng trong mã nguồn, tập tin cấu hình, sản phẩm xây dựng, hình ảnh container, hoặc biến môi trường. |   1    |   D/V   |
| 4.4.5 | Xác minh rằng việc xoay vòng bí mật được tự động hóa.                                                                                                                                                                                                          |   2    |   D/V   |

---

## C4.5 Phân vùng và Xác thực Khối lượng công việc AI

Cô lập các mô hình AI không đáng tin cậy trong các sandbox an toàn và bảo vệ các khối công việc AI nhạy cảm bằng cách sử dụng các môi trường thực thi đáng tin cậy (TEE) và công nghệ điện toán bảo mật.

|   #   | Mô tả                                                                                                                                                                                  | Cấp độ | Vai trò |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 4.5.1 | Xác minh rằng các mô hình AI bên ngoài hoặc không đáng tin cậy được thực thi trong các sandbox tách biệt.                                                                              |   1    |   D/V   |
| 4.5.2 | Xác minh rằng các workload trong sandbox mặc định không có kết nối mạng ra ngoài, với bất kỳ quyền truy cập cần thiết nào được định nghĩa rõ ràng.                                     |   1    |   D/V   |
| 4.5.3 | Xác minh rằng việc xác nhận khối lượng công việc được thực hiện trước khi tải mô hình hoặc khối lượng công việc, đảm bảo bằng chứng mật mã của môi trường thực thi tin cậy.            |   2    |   D/V   |
| 4.5.4 | Xác minh rằng các khối công việc bảo mật được thực thi trong môi trường thực thi tin cậy (TEE) cung cấp sự cô lập được thực thi bằng phần cứng, mã hóa bộ nhớ và bảo vệ tính toàn vẹn. |   3    |   D/V   |
| 4.5.5 | Xác nhận rằng các dịch vụ suy luận bảo mật ngăn chặn việc trích xuất mô hình thông qua tính toán được mã hóa với trọng số mô hình đóng kín và thực thi được bảo vệ.                    |   3    |   D/V   |
| 4.5.6 | Xác minh rằng việc điều phối môi trường thực thi tin cậy bao gồm quản lý vòng đời, xác thực từ xa và các kênh truyền thông được mã hóa.                                                |   3    |   D/V   |
| 4.5.7 | Xác minh rằng tính toán đa bên bảo mật (SMPC) cho phép đào tạo AI hợp tác mà không làm lộ bộ dữ liệu cá nhân hoặc các tham số mô hình.                                                 |   3    |   D/V   |

---

## C4.6 Quản lý Tài nguyên Hạ tầng AI, Sao lưu và Khôi phục

Ngăn chặn các cuộc tấn công làm cạn kiệt tài nguyên và đảm bảo phân bổ tài nguyên công bằng thông qua hạn mức và giám sát. Duy trì khả năng chống chịu của hạ tầng bằng các bản sao lưu an toàn, quy trình khôi phục đã được kiểm tra và khả năng phục hồi sau thảm họa.

|   #   | Mô tả                                                                                                                                                                                                                                                                                  | Cấp độ | Vai trò |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 4.6.1 | Xác minh rằng mức tiêu thụ tài nguyên của workload được giới hạn một cách phù hợp bằng cách sử dụng ví dụ như Kubernetes ResourceQuotas hoặc các phương pháp tương tự để giảm thiểu các cuộc tấn công Từ chối Dịch vụ (Denial of Service).                                             |   2    |   D/V   |
| 4.6.2 | Xác minh rằng việc cạn kiệt tài nguyên kích hoạt các biện pháp bảo vệ tự động (ví dụ: giới hạn tốc độ hoặc cô lập khối lượng công việc) khi vượt quá các ngưỡng đã định về CPU, bộ nhớ hoặc yêu cầu.                                                                                   |   2    |   D/V   |
| 4.6.3 | Xác minh rằng các hệ thống sao lưu hoạt động trong các mạng riêng biệt với thông tin đăng nhập riêng biệt, và hệ thống lưu trữ được vận hành trong mạng tách biệt hoàn toàn (air-gapped) hoặc triển khai bảo vệ WORM (ghi một lần, đọc nhiều lần) để ngăn chặn việc sửa đổi trái phép. |   2    |   D/V   |

---

## C4.7 An ninh Phần cứng AI

Bảo mật các thành phần phần cứng chuyên dụng cho AI bao gồm GPU, TPU và các bộ tăng tốc AI chuyên biệt.

|   #   | Mô tả                                                                                                                                                                                                                                | Cấp độ | Vai trò |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-----: |
| 4.7.1 | Xác minh rằng trước khi thực hiện khối lượng công việc, tính toàn vẹn của bộ tăng tốc AI được kiểm tra bằng các cơ chế xác thực dựa trên phần cứng (ví dụ: TPM, DRTM hoặc tương đương).                                              |   2    |   D/V   |
| 4.7.2 | Xác minh rằng bộ nhớ của bộ tăng tốc (GPU) được cách ly giữa các khối lượng công việc thông qua các cơ chế phân vùng với việc làm sạch bộ nhớ giữa các công việc.                                                                    |   2    |   D/V   |
| 4.7.3 | Xác minh rằng các mô-đun bảo mật phần cứng (HSM) bảo vệ trọng số mô hình AI và khóa mật mã với chứng nhận FIPS 140-3 Cấp 3 hoặc Common Criteria EAL4+.                                                                               |   3    |   D/V   |
| 4.7.4 | Xác minh rằng firmware bộ tăng tốc (GPU/TPU/NPUs) được gắn cố định phiên bản, ký và xác thực khi khởi động; firmware chưa ký hoặc debug bị chặn.                                                                                     |   2    |   D/V   |
| 4.7.5 | Xác minh rằng VRAM và bộ nhớ trên gói được xóa sạch giữa các công việc/người thuê và chính sách đặt lại thiết bị ngăn chặn hiện tượng dữ liệu còn sót lại giữa các người thuê.                                                       |   2    |   D/V   |
| 4.7.6 | Xác minh rằng các tính năng phân vùng/cô lập (ví dụ, phân vùng MIG/VM) được thực thi đối với từng người thuê riêng và ngăn chặn truy cập bộ nhớ từ đối tác này sang đối tác khác qua các phân vùng.                                  |   2    |   D/V   |
| 4.7.7 | Xác minh rằng các kết nối liên kết bộ tăng tốc (NVLink/PCIe/InfiniBand/RDMA/NCCL) bị giới hạn trong các kiến trúc được phê duyệt và các đầu cuối được xác thực; các liên kết văn bản thuần giữa các người thuê chéo không được phép. |   3    |   D/V   |
| 4.7.8 | Xác minh rằng dữ liệu telemetri bộ tăng tốc (công suất, nhiệt độ, ECC, bộ đếm hiệu suất) được xuất ra SIEM/OTel và có cảnh báo khi phát hiện các bất thường cho thấy kênh bên hoặc kênh che dấu.                                     |   3    |    D    |

---

## C4.8 An ninh AI Biên và Phân tán

Triển khai AI phân tán an toàn bao gồm điện toán biên, học liên kết, và kiến trúc đa địa điểm.

|   #   | Mô tả                                                                                                                                                             | Cấp độ | Vai trò |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-----: |
| 4.8.1 | Xác minh rằng các thiết bị AI biên xác thực với hạ tầng trung tâm bằng cách sử dụng TLS tương hỗ.                                                                 |   2    |   D/V   |
| 4.8.2 | Xác minh rằng các thiết bị đầu cuối thực hiện khởi động an toàn với chữ ký được xác minh và bảo vệ chống hạ cấp để ngăn chặn các cuộc tấn công giảm cấp phần mềm. |   2    |   D/V   |
| 4.8.3 | Xác minh rằng việc phối hợp AI phân tán sử dụng các cơ chế đồng thuận chịu lỗi Byzantine với việc xác thực người tham gia và phát hiện nút độc hại.               |   3    |   D/V   |
| 4.8.4 | Xác minh rằng giao tiếp từ edge đến cloud hỗ trợ điều tiết băng thông, nén dữ liệu và hoạt động ngoại tuyến an toàn với lưu trữ cục bộ được mã hóa.               |   3    |   D/V   |

---

## Tài liệu tham khảo

* [NIST Cybersecurity Framework 2.0](https://www.nist.gov/cyberframework)
* [CIS Controls v8](https://www.cisecurity.org/controls/v8)
* [Kubernetes Security Best Practices](https://kubernetes.io/docs/concepts/security/)
* [Cloud Security Alliance: Cloud Controls Matrix](https://cloudsecurityalliance.org/research/cloud-controls-matrix/)
* [ENISA: Secure Infrastructure Design](https://www.enisa.europa.eu/topics/critical-information-infrastructures-and-services)
* [ISO 27001:2022 Information Security Management](https://www.iso.org/standard/27001)
* [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)

