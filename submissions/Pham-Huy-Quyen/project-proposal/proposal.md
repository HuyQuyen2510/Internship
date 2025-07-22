  ---------------------------------------------------------------------------
  ![Ảnh có chứa văn bản, Phông chữ, Đồ họa, AWS Fist Cloud Journey
  biểu tượng Nội dung do AI tạo ra có thể   
  không chính                               
  xác.](media/image1.jpg){width="3.275in"   
  height="0.8865244969378827in"}            
  ----------------------------------------- ---------------------------------

  ---------------------------------------------------------------------------

Tên: Phạm Huy Quyến

MSSV: 2180605951

DỰ ÁN :TRIỂN KHAI MÔ HÌNH ZERO TRUST VÀ HỆ THỐNG SIEM TRÊN NỀN TẢNG AWS

## 1. Tóm tắt nội dung chính

### 1.1. Problem Statement -- Vấn đề cần giải quyết

Hiện nay, nhiều tổ chức vẫn đang dựa vào mô hình quản lý truy cập truyền
thống, trong đó các lập trình viên và kỹ sư hệ thống sử dụng thông tin
xác thực tĩnh (hardcoded credentials) để truy cập tài nguyên AWS. Điều
này không chỉ tạo ra lỗ hổng bảo mật nghiêm trọng nếu credentials bị rò
rỉ, mà còn gây khó khăn cho việc kiểm soát, thu hồi quyền và truy vết
hoạt động.

Bên cạnh đó, việc thiếu cơ chế giám sát tập trung và phân tích log theo
thời gian thực khiến tổ chức mất nhiều giờ để phát hiện sự cố hoặc hành
vi bất thường. Trong bối cảnh yêu cầu tuân thủ các tiêu chuẩn bảo mật
quốc tế ngày càng cao, mô hình cũ không còn đáp ứng được yêu cầu chiến
lược về bảo mật và quản trị rủi ro.

## 

## **1.2. Solution Overview -- Tổng quan giải pháp**

Giải pháp đề xuất là triển khai mô hình Zero Trust Access Control kết
hợp giữa **HashiCorp Vault**, **AWS IAM/KMS** và hệ thống **SIEM tích
hợp Splunk** để tăng cường bảo mật truy cập, giám sát hệ thống và phát
hiện hành vi bất thường.

**Các tính năng chính của giải pháp:**

- **Truy cập tạm thời (ephemeral access):** Dev hoặc ứng dụng được cấp
  credential động có hiệu lực tối đa 1 giờ thông qua Vault.

- **Mã hóa theo chuẩn Zero Trust:** Sử dụng AWS KMS để quản lý khóa mã
  hóa và tích hợp với Vault làm back-end HSM.

- **Theo dõi và phân tích hành vi:** Toàn bộ log từ CloudTrail, VPC Flow
  Logs và hệ thống được thu thập và phân tích bởi Splunk SIEM.

- **Tự động hóa cảnh báo bảo mật:** Rule cảnh báo được cấu hình sẵn để
  phát hiện hành vi trái phép, bất thường hoặc sai cấu hình.

- **Chi phí tối ưu:** Giải pháp được triển khai thử nghiệm trong 3 ngày
  với chi phí PoC chỉ khoảng \~\$400 USD.

## 1.3. Business Benefits & ROI -- Lợi ích kinh doanh và hoàn vốn đầu tư

Giải pháp không chỉ giảm thiểu rủi ro bảo mật mà còn mang lại lợi ích rõ
ràng cho tổ chức:

- **Giảm thiểu thiệt hại do sự cố:** Phát hiện sự cố trong vòng vài phút
  thay vì vài giờ, giúp hạn chế downtime và rò rỉ dữ liệu.

- **Tăng khả năng tuân thủ:** Hỗ trợ tổ chức đáp ứng các tiêu chuẩn ISO
  27001, SOC 2, GDPR dễ dàng hơn.

- **Giảm chi phí vận hành:** Giảm thời gian xử lý sự cố và số lượng nhân
  sự giám sát cần thiết nhờ tự động hóa.

- **Sẵn sàng mở rộng:** Kiến trúc linh hoạt cho phép mở rộng ra hệ thống
  SIEM toàn diện trong tương lai.

- **Tỷ lệ hoàn vốn nhanh:** Với chi phí triển khai PoC thấp (\~\$400),
  tổ chức có thể đánh giá khả năng mở rộng với rủi ro tài chính gần như
  bằng 0.

## 1.4. Investment & Timeline -- Yêu cầu đầu tư và thời gian triển khai

**Tổng chi phí PoC ước tính:** \~\$400 USD bao gồm:

- **Chi phí AWS:** \~\$1--2 USD cho lưu log và xử lý

- **Chi phí nhân sự:** \~\$300--370 USD cho kỹ sư AWS, Splunk và kiểm
  thử

**Thời gian triển khai:** 3 ngày

- Ngày 1: Thiết lập Vault, log, IAM

- Ngày 2: Tích hợp Splunk, tạo rule và dashboard

- Ngày 3: Kiểm thử, hiệu chỉnh, đánh giá

## 1.5. Success Metrics & Expected Outcomes -- Chỉ số thành công và kết quả kỳ vọng

  -----------------------------------------------------------------------
  **Chỉ số**     **Mô tả**                            **Ngưỡng đánh giá**
  -------------- ------------------------------------ -------------------
  Log Ingestion  Tỷ lệ log ingest thành công vào      ≥ 90%
  Rate           Splunk từ AWS                        

  Alert Accuracy Tỷ lệ cảnh báo đúng với tình huống   ≥ 80%
                 mô phỏng                             

  Latency        Thời gian từ khi log được ghi đến    ≤ 2 phút
                 khi alert được phát hiện             

  System         Hệ thống PoC vận hành liên tục không ≥ 95% uptime trong
  Stability      lỗi nghiêm trọng                     3 ngày
  -----------------------------------------------------------------------

**Kết quả mong đợi:**

- Xây dựng nền tảng SIEM đầu tiên với chi phí thấp.

- Chứng minh khả năng bảo vệ hệ thống và quản lý truy cập theo Zero
  Trust.

- Làm tiền đề để mở rộng thành giải pháp bảo mật toàn diện trên AWS
  trong giai đoạn tiếp theo.

# 

# 2. Problem Statement -- Xác định vấn đề

## 2.1. Current Situation -- Tình hình hiện tại

> Dự án: Security Monitoring Platform tích hợp SIEM
>
> Trong bối cảnh các tổ chức ngày càng phụ thuộc vào hạ tầng điện toán
> đám mây và dịch vụ số, an ninh mạng đã trở thành yếu tố sống còn. Các
> cuộc tấn công ngày càng tinh vi, có thể vượt qua các công cụ bảo vệ
> truyền thống. Do đó, nhu cầu phát triển một nền tảng giám sát bảo mật
> thông minh, tự động và có khả năng tích hợp với các hệ thống SIEM
> (Security Information and Event Management) là cấp thiết.
>
> Dự án này đề xuất việc xây dựng một nền tảng giám sát bảo mật hiện
> đại, sử dụng các dịch vụ AWS và tích hợp hệ thống SIEM (như Splunk
> hoặc ELK Stack) nhằm đảm bảo khả năng phát hiện sớm, phản hồi nhanh,
> và tối ưu hóa chi phí bảo mật. Nền tảng sẽ hỗ trợ tự động thu thập log
> từ nhiều nguồn (VPC Flow, CloudTrail, GuardDuty, hệ thống ứng dụng),
> phát hiện mối đe dọa theo thời gian thực và thực thi kịch bản phản hồi
> sự cố (incident response playbook) một cách tự động.
>
> Mục tiêu chính:
>
> Xây dựng hệ thống thu thập và phân tích log tập trung, real-time.
>
> Tích hợp chặt chẽ với hệ thống SIEM (Splunk/ELK) để dễ dàng
> correlation log.
>
> Phát hiện mối đe dọa tự động thông qua rule và thuật toán học máy.
>
> Kích hoạt phản hồi sự cố tự động với Lambda hoặc SOAR.
>
> Hiển thị dữ liệu bảo mật dưới dạng dashboard trực quan.
>
> Đảm bảo tuân thủ các yêu cầu bảo mật (GDPR, ISO 27001).
>
> Tối ưu chi phí lưu trữ, vận hành và xử lý log.
>
> Giá trị mang lại:
>
> Tăng khả năng phát hiện tấn công: Hệ thống giám sát theo thời gian
> thực, phân tích log đa nguồn.
>
> Giảm thời gian phản hồi sự cố: Tự động hóa playbook phản hồi, giảm tải
> cho đội SOC.
>
> Tuân thủ quy định pháp lý: Hỗ trợ log retention, báo cáo và audit
> trail theo chuẩn quốc tế.
>
> Dễ dàng mở rộng (scalable): Thiết kế dựa trên kiến trúc serverless và
> dịch vụ AWS.
>
> Tối ưu chi phí vận hành: Log phân tầng theo mức độ ưu tiên, lưu trữ
> lifecycle policy.

## 

## 2.2. Key Challenges -- Thách thức chính

- Xây dựng hệ thống thu thập và phân tích log tập trung, real-time.

- Tích hợp chặt chẽ với hệ thống SIEM (Splunk/ELK) để dễ dàng
  correlation log.

- Phát hiện mối đe dọa tự động thông qua rule và thuật toán học máy.

- Kích hoạt phản hồi sự cố tự động với Lambda hoặc SOAR.

- Hiển thị dữ liệu bảo mật dưới dạng dashboard trực quan.

- Đảm bảo tuân thủ các yêu cầu bảo mật (GDPR, ISO 27001).

- Tối ưu chi phí lưu trữ, vận hành và xử lý log.

## 2.3. Stakeholder Impact -- Ảnh hưởng đến các bên liên quan

+------------------+-----------------+--------------------------------+
| > Bên liên quan  | > Vai trò hiện  | > Ảnh hưởng từ dự án           |
| > (Stakeholder)  | > tại           |                                |
+:=================+:================+:===============================+
| > DevOps         | > Triển khai và | > Tăng cường bảo mật           |
| > Engineers      | > vận hành hạ   | > credential, giảm gánh nặng   |
|                  | > tầng AWS      | > quản lý thủ công. Tuy nhiên, |
|                  |                 | > cần thích nghi với quy trình |
|                  |                 | > cấp quyền tạm thời và tích   |
|                  |                 | > hợp HashiCorp Vault.         |
+------------------+-----------------+--------------------------------+
| > Developers     | > Truy cập và   | > Có thể truy cập tài nguyên   |
| > (Lập trình     | > sử dụng dịch  | > an toàn hơn mà không cần lưu |
| > viên)          | > vụ AWS để     | > credential cứng. Cần điều    |
|                  | > phát triển    | > chỉnh công cụ hoặc pipeline  |
|                  | > sản phẩm      | > để tương thích với quy trình |
|                  |                 | > mới.                         |
+------------------+-----------------+--------------------------------+
| > Security Team  | > Giám sát và   | > Có đầy đủ dữ liệu truy vết,  |
|                  | > bảo vệ hệ     | > hỗ trợ phân tích hành vi bất |
|                  | > thống         | > thường thông qua SIEM. Giúp  |
|                  |                 | > thực hiện triết lý Zero      |
|                  |                 | > Trust một cách hiệu quả hơn. |
+------------------+-----------------+--------------------------------+
| > IT Compliance  | > Đảm bảo tuân  | > Dễ dàng thực hiện kiểm tra   |
| > / Audit        | > thủ chính     | > truy cập, truy xuất log và   |
|                  | > sách bảo mật  | > chứng minh tính tuân thủ.    |
|                  | > và kiểm tra   | > Hạn chế rủi ro từ việc sử    |
|                  | > định kỳ       | > dụng credential vĩnh viễn.   |
+------------------+-----------------+--------------------------------+
| > Project        | > Quản lý chiến | > Giảm thiểu rủi ro bảo mật    |
| > Manager / CTO  | > lược kỹ thuật | > cấp cao, đảm bảo định hướng  |
|                  | > và an ninh    | > phát triển hệ thống an toàn, |
|                  | > của hệ thống  | > linh hoạt và chuẩn hóa.      |
+------------------+-----------------+--------------------------------+

# 

# 3. Solution Architecture -- Kiến trúc giải pháp

## 3.1. Architecture Overview -- Tổng quan kiến trúc

Mục tiêu của kiến trúc giải pháp:

- Thu thập log đa nguồn từ AWS (CloudTrail, VPC Flow, EC2, Lambda...)

- Gửi log về hệ thống SIEM (Splunk)

- Áp dụng rule phát hiện mối đe dọa (Sigma/Splunk rules)

- Tự động phản hồi sự cố bằng automation (Lambda / SOAR)

- Hiển thị log & cảnh báo bằng dashboard bảo mật

- Tối ưu chi phí lưu trữ và xử lý log

## 3.2. AWS Services Used -- Dịch vụ AWS sử dụng

Dưới đây là danh sách các dịch vụ AWS được sử dụng trong dự án, kèm theo
vai trò và lý do lựa chọn:

  -----------------------------------------------------------------------
  Dịch vụ AWS         Mô tả chức năng chính   Lý do sử dụng
  ------------------- ----------------------- ---------------------------
  EC2 (Elastic        Máy chủ ảo dùng để      Cho phép kiểm soát môi
  Compute Cloud)      triển khai HashiCorp    trường Vault riêng biệt và
                      Vault và các agent liên bảo mật nội bộ
                      quan                    

  S3 (Simple Storage  Lưu trữ log, bản ghi sự Độ bền cao, tích hợp tốt
  Service)            kiện và dữ liệu audit   với các dịch vụ giám sát
                      từ các dịch vụ khác     như CloudTrail/SIEM

  IAM (Identity and   Quản lý quyền truy cập  Cung cấp kiểm soát truy cập
  Access Management)  dịch vụ AWS             chi tiết (fine-grained
                                              access control)

  KMS (Key Management Mã hóa dữ liệu, tích    Đáp ứng yêu cầu Zero Trust
  Service)            hợp với Vault để cung   về mã hóa ở mọi tầng
                      cấp HSM key back-end    

  CloudTrail          Ghi lại tất cả hành vi  Phân tích hoạt động bất
                      truy cập và thay đổi    thường, hỗ trợ SIEM
                      cấu hình dịch vụ AWS    

  CloudWatch Logs     Thu thập log từ Vault,  Dùng để chuyển tiếp log về
                      hệ thống và ứng dụng    Splunk hoặc phân tích sự
                                              kiện trực tiếp

  VPC (Virtual        Tạo mạng ảo riêng để cô Tăng cường bảo mật và kiểm
  Private Cloud)      lập hệ thống Vault và   soát lưu lượng truy cập
                      các dịch vụ             

  VPC Flow Logs       Ghi lại thông tin lưu   Hỗ trợ phân tích hành vi
                      lượng mạng giữa các     mạng đáng ngờ, tích hợp với
                      thành phần trong VPC    Splunk SIEM

  Secrets Manager     Lưu trữ thông tin nhạy  Có thể dùng để so sánh hoặc
  *(tùy chọn)*        cảm và tích hợp Vault   dự phòng trong giai đoạn
                      nếu cần                 chuyển đổi

  CloudFormation      Tự động triển khai hạ   Hỗ trợ tái sử dụng, tăng
  *(tùy chọn)*        tầng AWS theo mẫu kiến  tính ổn định và tự động hóa
                      trúc                    
  -----------------------------------------------------------------------

## 3.3. Component Design -- Thiết kế thành phần

Các thành phần chính của kiến trúc:

  -----------------------------------------------------------------------
  Thành phần                    Mô tả chức năng
  ----------------------------- -----------------------------------------
  CloudTrail                    Thu thập mọi API call trên AWS

  VPC Flow Logs                 Ghi lại luồng mạng trong VPC

  CloudWatch Logs               Log từ ứng dụng hoặc hệ thống

  S3                            Lưu trữ log trung tâm

  Kinesis Firehose / Lambda     Gửi log sang SIEM

  Splunk (SIEM)                 Phân tích, correlation, phát hiện mối đe
                                dọa

  Detection Engine              Rule (Sigma/Splunk SPL), Machine Learning

  Automation (Lambda / SOAR)    Gửi cảnh báo, phản hồi tự động

  Dashboard (Splunk/Kibana)     Giao diện giám sát và báo cáo

  Athena / S3 Lifecycle         Truy vấn log cũ và tối ưu lưu trữ
  -----------------------------------------------------------------------

## 3.4. Security Architecture -- Kiến trúc bảo mật

Kiến trúc hệ thống -- Mô tả chi tiết:

1\. Thu thập log đầu vào:

- CloudTrail: tự động ghi lại toàn bộ API call → lưu vào S3

- VPC Flow Logs: gửi tới CloudWatch Logs

- Application Logs: gửi về CloudWatch Logs hoặc S3

- GuardDuty: gửi các phát hiện đến EventBridge

2\. Đẩy log vào SIEM:

- Kinesis Firehose trích xuất log từ S3 hoặc CloudWatch

- Lambda lọc và chuẩn hóa log định dạng JSON/CEF/Syslog

- Log được đẩy sang Splunk HTTP Event Collector (HEC)

3\. Phân tích log và phát hiện mối đe dọa:

- Sử dụng các rule như:

  - Login thất bại nhiều lần (Brute force)

  - Truy cập root bất thường

  - SSH từ IP bất thường

  - DDoS hoặc scan port diện rộng

- Rule viết bằng Splunk SPL hoặc Sigma Rule

4\. Cảnh báo và phản hồi sự cố:

- Khi rule được match:

  - Splunk Alert gửi email, Slack hoặc gọi AWS Lambda

  - Lambda có thể:

    - Gỡ quyền IAM

    - Chặn IP bằng Security Group

    - Mở ticket trên Jira/ServiceNow

5\. Dashboard hiển thị và lưu trữ lâu dài:

- Splunk/Kibana hiển thị:

  - Top IP bất thường

  - User bị lỗi đăng nhập nhiều nhất

  - Biểu đồ log theo thời gian

- S3 Lifecycle chuyển log sang Glacier sau 30/90 ngày để tiết kiệm

![Ảnh có chứa văn bản, ảnh chụp màn hình, biểu đồ, Phông chữ Nội dung do
AI tạo ra có thể không chính xác.](media/image2.png){width="6.0in"
height="9.0in"}

# 4. Technical Implementation -- Triển khai kỹ thuật

## 4.1. Implementation Phases -- Các giai đoạn triển khai

Dự án được chia thành 4 giai đoạn chính:

  ------------------------------------------------------------------------
  Giai đoạn       Nội dung                            Kết quả đầu ra
  --------------- ----------------------------------- --------------------
  Giai đoạn 1:    Thiết lập thử nghiệm hệ thống SIEM  Mô hình SIEM mẫu
  POC (Proof of   tích hợp giữa AWS và Splunk với một hoạt động, xác minh
  Concept)        số log mẫu (VD: CloudTrail, VPC     khả năng tích hợp.
                  Flow Logs).                         

  Giai đoạn 2:    Thu thập toàn bộ log sản xuất, cấu  Mô hình SIEM hoạt
  Triển khai      hình pipeline phân tích log và rule động trên toàn hệ
  chính thức      phát hiện sự cố.                    thống thật.

  Giai đoạn 3:    Thiết kế dashboard trực quan, cấu   Báo cáo & cảnh báo
  Tối ưu hóa &    hình cảnh báo tự động (alert), xác  thời gian thực hoạt
  Cảnh báo        định các chỉ số quan trọng (KPIs).  động ổn định.

  Giai đoạn 4:    Tài liệu hóa hệ thống, đào tạo nhóm Tài liệu chi tiết,
  Đào tạo & Bàn   bảo mật, DevOps và bàn giao vận     quy trình xử lý sự
  giao            hành.                               cố, dashboard vận
                                                      hành.
  ------------------------------------------------------------------------

## 4.2. Technical Requirements -- Yêu cầu kỹ thuật

Hạ tầng AWS yêu cầu:

- CloudTrail để ghi lại hoạt động API

- CloudWatch Logs để thu thập log từ EC2, Lambda

- VPC Flow Logs để theo dõi lưu lượng mạng

- S3 bucket để lưu trữ log trung gian

- Lambda / Firehose / Glue (tuỳ chọn) để xử lý log

Splunk yêu cầu:

- Splunk Enterprise hoặc Splunk Cloud (\>=9.x)

- Splunk Universal Forwarder (nếu dùng hệ thống on-premises)

- Add-on AWS Splunk App để ingest log qua API/S3

Yêu cầu bảo mật:

- IAM Roles tách biệt theo nguyên tắc least privilege

- S3 encryption (AES-256, SSE-KMS)

- Log integrity & immutability (qua CloudTrail hoặc Object Lock)

## 4.3. Development Approach -- Phương pháp phát triển

Áp dụng phương pháp Agile + DevSecOps, cụ thể:

- Mỗi vòng lặp (sprint) kéo dài 2 tuần: phân tích log, tạo rule, kiểm
  thử

- Hạ tầng sử dụng Infrastructure as Code (IaC) với CloudFormation hoặc
  Terraform

- Áp dụng CI/CD để tự động hóa triển khai dashboard, rule cảnh báo, cấu
  hình ingest log

- Tích hợp kiểm tra bảo mật (security scan) ngay từ đầu chu trình

## 4.4. Testing Strategy -- Chiến lược kiểm thử

  ------------------------------------------------------------------------
  Loại kiểm thử  Mục tiêu                             Công cụ
  -------------- ------------------------------------ --------------------
  Functional     Kiểm tra các rule phát hiện sự kiện  Splunk Search, test
  Test           bảo mật có hoạt động chính xác       logs
                 không.                               

  Performance    Đánh giá tốc độ ingest log và độ trễ Splunk Monitoring
  Test           cảnh báo.                            Console

  Security Test  Kiểm tra phân quyền IAM, log không   AWS IAM Analyzer,
                 bị chỉnh sửa.                        Audit logs

  Integration    Xác minh pipeline từ AWS → S3 →      Manual testing,
  Test           Splunk chạy mượt.                    scripted simulation

  Alert Accuracy Kiểm tra độ chính xác của cảnh báo   Kịch bản giả lập sự
  Test           (false positive/false negative).     cố
  ------------------------------------------------------------------------

## 4.5. Deployment Plan -- Kế hoạch triển khai

  -----------------------------------------------------------------------
  Hoạt động          Mô tả                                 Trách nhiệm
  ------------------ ------------------------------------- --------------
  Cấu hình dịch vụ   Bật CloudTrail, VPC Flow Logs, cấu    Nhóm hạ tầng
  AWS                hình S3 Bucket & IAM Role             

  Cài đặt Splunk &   Cài Splunk, add-on AWS, cấu hình      Nhóm bảo mật
  Add-on             index, input, parsing log             

  Thiết lập          Thiết kế dashboard quản lý, viết rule Nhóm Splunk
  Dashboard & Rule   cảnh báo tùy theo loại log            

  Kiểm thử           Thực hiện kiểm thử bảo mật, kiểm tra  Nhóm kiểm thử
                     cảnh báo                              

  Vận hành & bảo trì Lên lịch backup, kiểm tra định kỳ,    Nhóm vận hành
                     tối ưu query Splunk                   (SOC)
  -----------------------------------------------------------------------

# 5. Timeline & Milestones -- Dòng thời gian và các mốc

## 5.1. Project Timeline -- Thời gian thực hiện

  -----------------------------------------------------------------------
  Ngày      Hoạt động chính
  --------- -------------------------------------------------------------
  Ngày 1    Thiết kế kiến trúc tích hợp AWS → S3 → Splunk\
            • Kích hoạt log AWS: CloudTrail, VPC Flow Logs\
            • Cấu hình S3, IAM, Splunk Add-on

  Ngày 2    Thiết lập pipeline ingest log\
            • Đẩy log từ AWS sang S3 → ingest vào Splunk\
            • Tạo rule phát hiện đơn giản (ví dụ: login thất bại nhiều
            lần)\
            • Thiết kế dashboard cảnh báo mẫu

  Ngày 3    Kiểm thử & bàn giao\
            • Test alert trigger, độ trễ cảnh báo\
            • Viết hướng dẫn vận hành\
            • Bàn giao dashboard & tài liệu PoC
  -----------------------------------------------------------------------

## 5.2. Key Milestones -- Các mốc quan trọng

  ------------------------------------------------------------------------
  Thời điểm   Mốc đạt được             Kết quả
  ----------- ------------------------ -----------------------------------
  Cuối ngày 1 Log AWS ghi về S3        CloudTrail & VPC logs đã được bật

  Cuối ngày 2 Splunk ingest log thành  Có dashboard, rule cảnh báo mẫu
              công                     

  Cuối ngày 3 Kiểm thử hoàn tất        Cảnh báo hoạt động, tài liệu bàn
                                       giao đầy đủ
  ------------------------------------------------------------------------

## 5.3. Dependencies -- Phụ thuộc

- Phải có quyền IAM để kích hoạt log và truy cập S3

- Splunk đã cài sẵn hoặc có Splunk Cloud trial

- Mạng ổn định để ingest log qua API hoặc pull từ S3

## 5.4. Resource Allocation -- Phân bổ tài nguyên

  ------------------------------------------------------------------------
  Vai trò                       Số lượng    Ghi chú
  ----------------------------- ----------- ------------------------------
  DevOps / AWS Engineer         1           Cấu hình log, S3, IAM

  Splunk Engineer               1           Tạo input, rule, dashboard

  Tester / Analyst              1           Kiểm thử log và alert
  ------------------------------------------------------------------------

# 6. Budget Estimation -- Dự toán ngân sách

## 6.1. Infrastructure Costs -- Chi phí hạ tầng (trên AWS)

  -----------------------------------------------------------------------
  Hạng mục              Mô tả                               Chi phí (ước
                                                            tính)
  --------------------- ----------------------------------- -------------
  S3 Storage            Lưu trữ log CloudTrail và VPC Flow  \$0.25 --
                        Logs (\~5--10GB)                    \$0.50 USD

  CloudTrail            Ghi nhận các hành vi API. Miễn phí  \$0
                        khi gửi về S3                       

  VPC Flow Logs         Ghi log mạng (chế độ Basic --       \~ \$0.50 USD
                        version 2)                          

  Lambda / Firehose     Xử lý, lọc log hoặc chuyển về       \$0 -- \$1
  *(nếu dùng)*          Splunk hoặc nơi khác                USD

  Tổng chi phí AWS      Tổng cộng cho toàn bộ hạ tầng PoC   \~ \$1 -- \$2
                        trong 3 ngày                        USD
  -----------------------------------------------------------------------

Miễn phí trong Free Tier nếu dùng tài khoản mới.

## 6.2. Development Costs -- Chi phí phát triển

  ------------------------------------------------------------------------
  **Hạng mục**        **Vai trò**                **Số     **Chi phí (ước
                                                 ngày**   tính)**
  ------------------- -------------------------- -------- ----------------
  AWS Engineer        Thiết lập log, S3, IAM     1 ngày   \$80 -- \$100

  Splunk Engineer     Thiết lập input, rule,     2 ngày   \$160 -- \$200
                      dashboard                           

  Tester              Kiểm thử cảnh báo & log    1 ngày   \$50 -- \$70

  **Tổng chi phí nhân Trong 3 ngày                        **\~\$300 --
  sự**                                                    \$370 USD**
  ------------------------------------------------------------------------

Có thể giảm nếu team nội bộ tự làm.

## 6.3. Operational Costs -- Chi phí vận hành (sau PoC)

  -----------------------------------------------------------------------
  **Hạng mục**      **Mô tả**                 **Chi phí**
  ----------------- ------------------------- ---------------------------
  Splunk Cloud      Dùng bản dùng thử 15--30  \$0
  Trial             ngày                      

  AWS tiếp tục lưu  Tùy lượng log thực tế     \~\$5 -- \$20/tháng
  log                                         

  Quản trị & giám   0.5--1h/ngày nhân viên    \$100 -- \$200/tháng (nếu
  sát               SOC                       tính công)
  -----------------------------------------------------------------------

## 6.4. ROI Analysis -- Phân tích hoàn vốn đầu tư

  -----------------------------------------------------------------------
  **Giá trị mang lại**    **Mô tả**
  ----------------------- -----------------------------------------------
  Giảm thời gian phát     Từ vài giờ xuống vài phút → giảm thiệt hại từ
  hiện sự cố              downtime/tấn công

  Nâng cao năng lực giám  Có cảnh báo tự động, dashboard minh bạch
  sát                     

  Cải thiện tuân thủ bảo  Đáp ứng tiêu chuẩn như ISO 27001, GDPR, SOC 2
  mật                     dễ dàng hơn

  Dễ mở rộng về sau       Có thể triển khai SIEM production từ nền PoC
                          hiện tại
  -----------------------------------------------------------------------

Với chi phí chỉ khoảng \~\$400 USD

## 7. Risk Assessment -- Đánh giá rủi ro

## 7.1. Risk Matrix -- Ma trận rủi ro

  ------------------------------------------------------------------------
  **Rủi ro**                    **Mức độ ảnh    **Xác suất    **Mức độ ưu
                                hưởng**         xảy ra**      tiên**
  ----------------------------- --------------- ------------- ------------
  IAM cấu hình sai → lộ quyền   Cao             Trung bình    Cao
  truy cập log                                                

  Ingest log từ AWS vào Splunk  Trung bình      Cao           Cao
  thất bại                                                    

  Dữ liệu log thiếu chuẩn hóa → Trung bình      Trung bình    Trung bình
  rule sai                                                    

  Cảnh báo Splunk gây           Thấp            Cao           Trung bình
  false-positive                                              

  Splunk dùng trial license hết Trung bình      Trung bình    Trung bình
  hạn                                                         

  Không ai vận hành sau PoC     Cao             Thấp          Trung bình
  ------------------------------------------------------------------------

## 7.2. Mitigation Strategies -- Chiến lược giảm thiểu

  ------------------------------------------------------------------------
  **Rủi ro**       **Chiến lược giảm thiểu**
  ---------------- -------------------------------------------------------
  IAM sai          Kiểm tra kỹ quyền IAM theo nguyên tắc least privilege.
                   Áp dụng checklist review cụ thể.

  Ingest log lỗi   Kiểm thử pipeline từng bước (S3 → Add-on → Splunk).
                   Dùng log mẫu trước.

  Log không chuẩn  Dùng JSON log từ đầu hoặc viết script xử lý.
  hóa              

  False-positive   Viết rule đơn giản, kiểm thử kỹ với dữ liệu giả lập. Có
                   vòng kiểm định.

  Splunk hết trial Theo dõi thời hạn, chủ động gia hạn hoặc chuyển sang
                   bản Free.

  Thiếu người vận  Đào tạo nhân sự SOC ngay trong quá trình PoC, phân công
  hành             người trực rõ ràng.
  ------------------------------------------------------------------------

## 7.3. Contingency Plans -- Kế hoạch dự phòng

  -----------------------------------------------------------------------
  **Tình huống xấu xảy ra** **Phản ứng dự phòng**
  ------------------------- ---------------------------------------------
  Ingest log từ AWS thất    Chuyển sang ingest qua syslog hoặc forwarder
  bại                       agent tạm thời

  Splunk không nhận log     Tạm thời lưu log ở S3, kiểm tra lại pipeline
                            rồi reprocess sau

  Splunk license hết hạn    Dùng Splunk Free bản local, ingest log cũ để
  đột ngột                  demo

  Không có alert nào chạy   Dùng log mẫu mô phỏng tấn công để test lại
  đúng                      các rule

  Không có người vận hành   Gán trách nhiệm SOC tạm thời, bàn giao tài
  sau PoC                   liệu vận hành cụ thể
  -----------------------------------------------------------------------

# 8. Expected Outcomes -- Kết quả mong đợi

## 8.1. Success Metrics -- Các chỉ số thành công

  ------------------------------------------------------------------------
  **Chỉ số**    **Mô tả**                                 **Ngưỡng đánh
                                                          giá**
  ------------- ----------------------------------------- ----------------
  Log Ingestion Tỷ lệ log từ AWS (CloudTrail, VPC Flow    ≥ 90% log ingest
  Rate          Logs\...) ingest vào Splunk thành công    được

  Alert         Tỷ lệ cảnh báo đúng với tình huống giả    ≥ 80% cảnh báo
  Accuracy      lập                                       đúng

  Latency       Thời gian từ khi log ghi đến khi alert    ≤ 2 phút
                hiển thị                                  

  PoC Stability Hệ thống hoạt động ổn định, không lỗi     ≥ 95% uptime
                nghiêm trọng                              trong 3 ngày
  ------------------------------------------------------------------------

## 8.2. Business Benefits -- Lợi ích kinh doanh

Phát hiện sớm rủi ro bảo mật trong hạ tầng AWS theo thời gian thực.

# Contents {#contents .TOC-Heading}

[1. Tóm tắt nội dung chính
[1](#tóm-tắt-nội-dung-chính)](#tóm-tắt-nội-dung-chính)

[1.1. Problem Statement -- Vấn đề cần giải quyết
[1](#problem-statement-vấn-đề-cần-giải-quyết)](#problem-statement-vấn-đề-cần-giải-quyết)

[**1.2. Solution Overview -- Tổng quan giải pháp**
[1](#solution-overview-tổng-quan-giải-pháp)](#solution-overview-tổng-quan-giải-pháp)

[1.3. Business Benefits & ROI -- Lợi ích kinh doanh và hoàn vốn đầu tư
[2](#business-benefits-roi-lợi-ích-kinh-doanh-và-hoàn-vốn-đầu-tư)](#business-benefits-roi-lợi-ích-kinh-doanh-và-hoàn-vốn-đầu-tư)

[1.4. Investment & Timeline -- Yêu cầu đầu tư và thời gian triển khai
[2](#investment-timeline-yêu-cầu-đầu-tư-và-thời-gian-triển-khai)](#investment-timeline-yêu-cầu-đầu-tư-và-thời-gian-triển-khai)

[1.5. Success Metrics & Expected Outcomes -- Chỉ số thành công và kết
quả kỳ vọng
[2](#success-metrics-expected-outcomes-chỉ-số-thành-công-và-kết-quả-kỳ-vọng)](#success-metrics-expected-outcomes-chỉ-số-thành-công-và-kết-quả-kỳ-vọng)

[2. Problem Statement -- Xác định vấn đề
[3](#problem-statement-xác-định-vấn-đề)](#problem-statement-xác-định-vấn-đề)

[2.1. Current Situation -- Tình hình hiện tại
[3](#current-situation-tình-hình-hiện-tại)](#current-situation-tình-hình-hiện-tại)

[2.2. Key Challenges -- Thách thức chính
[4](#key-challenges-thách-thức-chính)](#key-challenges-thách-thức-chính)

[2.3. Stakeholder Impact -- Ảnh hưởng đến các bên liên quan
[5](#stakeholder-impact-ảnh-hưởng-đến-các-bên-liên-quan)](#stakeholder-impact-ảnh-hưởng-đến-các-bên-liên-quan)

[3. Solution Architecture -- Kiến trúc giải pháp
[6](#solution-architecture-kiến-trúc-giải-pháp)](#solution-architecture-kiến-trúc-giải-pháp)

[3.1. Architecture Overview -- Tổng quan kiến trúc
[6](#architecture-overview-tổng-quan-kiến-trúc)](#architecture-overview-tổng-quan-kiến-trúc)

[3.2. AWS Services Used -- Dịch vụ AWS sử dụng
[6](#aws-services-used-dịch-vụ-aws-sử-dụng)](#aws-services-used-dịch-vụ-aws-sử-dụng)

[3.3. Component Design -- Thiết kế thành phần
[7](#component-design-thiết-kế-thành-phần)](#component-design-thiết-kế-thành-phần)

[3.4. Security Architecture -- Kiến trúc bảo mật
[8](#security-architecture-kiến-trúc-bảo-mật)](#security-architecture-kiến-trúc-bảo-mật)

[4. Technical Implementation -- Triển khai kỹ thuật
[11](#technical-implementation-triển-khai-kỹ-thuật)](#technical-implementation-triển-khai-kỹ-thuật)

[4.1. Implementation Phases -- Các giai đoạn triển khai
[11](#implementation-phases-các-giai-đoạn-triển-khai)](#implementation-phases-các-giai-đoạn-triển-khai)

[4.2. Technical Requirements -- Yêu cầu kỹ thuật
[11](#technical-requirements-yêu-cầu-kỹ-thuật)](#technical-requirements-yêu-cầu-kỹ-thuật)

[4.3. Development Approach -- Phương pháp phát triển
[12](#development-approach-phương-pháp-phát-triển)](#development-approach-phương-pháp-phát-triển)

[4.4. Testing Strategy -- Chiến lược kiểm thử
[12](#testing-strategy-chiến-lược-kiểm-thử)](#testing-strategy-chiến-lược-kiểm-thử)

[4.5. Deployment Plan -- Kế hoạch triển khai
[12](#deployment-plan-kế-hoạch-triển-khai)](#deployment-plan-kế-hoạch-triển-khai)

[5. Timeline & Milestones -- Dòng thời gian và các mốc
[13](#timeline-milestones-dòng-thời-gian-và-các-mốc)](#timeline-milestones-dòng-thời-gian-và-các-mốc)

[5.1. Project Timeline -- Thời gian thực hiện
[13](#project-timeline-thời-gian-thực-hiện)](#project-timeline-thời-gian-thực-hiện)

[5.2. Key Milestones -- Các mốc quan trọng
[13](#key-milestones-các-mốc-quan-trọng)](#key-milestones-các-mốc-quan-trọng)

[5.3. Dependencies -- Phụ thuộc
[13](#dependencies-phụ-thuộc)](#dependencies-phụ-thuộc)

[5.4. Resource Allocation -- Phân bổ tài nguyên
[14](#resource-allocation-phân-bổ-tài-nguyên)](#resource-allocation-phân-bổ-tài-nguyên)

[6. Budget Estimation -- Dự toán ngân sách
[14](#budget-estimation-dự-toán-ngân-sách)](#budget-estimation-dự-toán-ngân-sách)

[6.1. Infrastructure Costs -- Chi phí hạ tầng (trên AWS)
[14](#infrastructure-costs-chi-phí-hạ-tầng-trên-aws)](#infrastructure-costs-chi-phí-hạ-tầng-trên-aws)

[6.2. Development Costs -- Chi phí phát triển
[14](#development-costs-chi-phí-phát-triển)](#development-costs-chi-phí-phát-triển)

[6.3. Operational Costs -- Chi phí vận hành (sau PoC)
[15](#operational-costs-chi-phí-vận-hành-sau-poc)](#operational-costs-chi-phí-vận-hành-sau-poc)

[6.4. ROI Analysis -- Phân tích hoàn vốn đầu tư
[15](#roi-analysis-phân-tích-hoàn-vốn-đầu-tư)](#roi-analysis-phân-tích-hoàn-vốn-đầu-tư)

[7. Risk Assessment -- Đánh giá rủi ro
[16](#risk-assessment-đánh-giá-rủi-ro)](#risk-assessment-đánh-giá-rủi-ro)

[7.1. Risk Matrix -- Ma trận rủi ro
[16](#risk-matrix-ma-trận-rủi-ro)](#risk-matrix-ma-trận-rủi-ro)

[7.2. Mitigation Strategies -- Chiến lược giảm thiểu
[16](#mitigation-strategies-chiến-lược-giảm-thiểu)](#mitigation-strategies-chiến-lược-giảm-thiểu)

[7.3. Contingency Plans -- Kế hoạch dự phòng
[17](#contingency-plans-kế-hoạch-dự-phòng)](#contingency-plans-kế-hoạch-dự-phòng)

[8. Expected Outcomes -- Kết quả mong đợi
[17](#expected-outcomes-kết-quả-mong-đợi)](#expected-outcomes-kết-quả-mong-đợi)

[8.1. Success Metrics -- Các chỉ số thành công
[17](#success-metrics-các-chỉ-số-thành-công)](#success-metrics-các-chỉ-số-thành-công)

[8.2. Business Benefits -- Lợi ích kinh doanh
[17](#business-benefits-lợi-ích-kinh-doanh)](#business-benefits-lợi-ích-kinh-doanh)

[8.3. Technical Improvements -- Cải tiến kỹ thuật
[18](#technical-improvements-cải-tiến-kỹ-thuật)](#technical-improvements-cải-tiến-kỹ-thuật)

[8.4. Long-term Value -- Giá trị lâu dài
[18](#long-term-value-giá-trị-lâu-dài)](#long-term-value-giá-trị-lâu-dài)

Giảm thiểu tổn thất tài chính do vi phạm dữ liệu nhờ phát hiện tấn công
nhanh.

Tăng khả năng giám sát tuân thủ (compliance visibility) với các chuẩn
như ISO 27001, SOC 2.

Tối ưu chi phí vận hành SOC, tránh phụ thuộc hoàn toàn vào SIEM đắt tiền
on-prem.

## 8.3. Technical Improvements -- Cải tiến kỹ thuật

Thiết lập quy trình ingest log từ AWS → Splunk sử dụng S3, Kinesis,
Lambda hoặc add-on.

Tự động hóa tạo rule phân tích log (detection rules) cho các dịch vụ AWS
phổ biến.

Chuẩn hóa log định dạng JSON, dễ tích hợp SIEM khác trong tương lai.

Xây dựng dashboard Splunk mẫu theo dõi theo dịch vụ (IAM, S3, EC2\...).

## 8.4. Long-term Value -- Giá trị lâu dài

Cấu hình và kiến trúc PoC có thể mở rộng thành hệ thống thật sau PoC.

Tài liệu hoá quy trình, kịch bản tấn công và detection rule để tái sử
dụng trong các dự án SOC/SIEM sau.

Góp phần vào chiến lược Zero Trust trên Cloud, nâng cao năng lực bảo mật
nội bộ.

Làm nền tảng tích hợp thêm các công cụ khác như SOAR, Threat Intel,
HashiCorp Vault trong tương lai.
