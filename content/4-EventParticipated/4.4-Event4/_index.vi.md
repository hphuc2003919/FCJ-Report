---
title: "Event 4"
date: 2025-09-09
weight: 1
chapter: false
pre: " <b> 4.4. </b> "
---

# Bài thu hoạch: “AWS Cloud Mastery Series #3 – AWS Well-Architected Security Pillar”

### Mục Đích Của Sự Kiện

- Giới thiệu 5 trụ cột của AWS Well-Architected Security Framework
- Hướng dẫn thực hành triển khai kiến trúc IAM hiện đại
- Trình bày giám sát liên tục và detection với các công cụ AWS-native
- Nâng cao hiểu biết về bảo mật hạ tầng và mạng trên AWS
- Đi sâu vào mã hóa, quản lý khóa và quản lý secrets
- Thực hành các tình huống incident response với tự động hóa

### Nội Dung Nổi Bật

#### Trụ Cột 1: Identity & Access Management (IAM) 
- Kiến trúc IAM hiện đại: Users, Roles, Policies
- IAM Identity Center, permission sets, SCPs, permission boundaries
- Demo thực hành: validate IAM policies và mô phỏng quyền truy cập

#### Trụ Cột 2: Detection

- Giám sát liên tục bằng CloudTrail, GuardDuty, Security Hub
- Logging nhiều tầng: VPC Flow Logs, ALB/S3 logs
- Alerting & automation với EventBridge
- Khái niệm Detection-as-Code

#### Trụ Cột 3: Infrastructure Protection

- Bảo mật mạng và workload: VPC segmentation, Security Groups vs NACLs
- Bảo vệ bằng WAF, Shield, Network Firewall
- Bảo mật cơ bản cho EC2, ECS/EKS

#### Trụ Cột 4: Data Protection

- Quản lý khóa và KMS best practices: key rotation, grants
- Mã hóa dữ liệu tại rest & in-transit cho S3, EBS, RDS, DynamoDB
- Quản lý secrets: Secrets Manager & Parameter Store
- Phân loại dữ liệu & các guardrails truy cập

#### Trụ Cột 5: Incident Response

- Vòng đời IR trên AWS: chuẩn bị → phát hiện → containment → recovery → lessons learned
- Playbooks: IAM key bị compromise, S3 public exposure, malware trên EC2
- Tự động hóa IR bằng Lambda & Step Functions


### Những Gì Học Được

#### Chiến Lược

- Security Pillar là nền tảng của mọi kiến trúc AWS, bất kể loại workload
- Quản lý multi-account và Identity Center giúp kiểm soát quyền truy cập ở quy mô lớn
- Cần chuyển từ giám sát thủ công sang tự động hóa và Detection-as-Code

#### Kỹ Thuật

- IAM phải thực thi least privilege, strong isolation và tránh static credentials dài hạn
- Giám sát liên tục bằng CloudTrail, GuardDuty, Security Hub nâng cao khả năng quan sát
- Phân đoạn mạng và bảo vệ theo tầng giúp giảm blast radius
- Bảo mật dữ liệu tốt bao gồm: mã hóa, chính sách khóa, rotation secrets và phân loại dữ liệu
- Tự động hóa IR giảm thời gian phản hồi và giảm tải vận hành

### Ứng Dụng Vào Công Việc

- Sử dụng IAM Identity Center và SCP để nâng cao governance trong môi trường multi-account
- Triển khai GuardDuty, Security Hub, EventBridge để cải thiện detection và alert automation
- Xem xét lại thiết kế VPC để đảm bảo segmentation và least-privilege network access
- Áp dụng best practices mã hóa và rotation secrets cho các workload hiện tại
- Xây dựng playbooks IR và tự động hóa các bước quan trọng với Lambda để containment nhanh hơn

### Trải nghiệm trong event

Sự kiện mang đến trải nghiệm thực hành cao về bảo mật trên AWS. Kết hợp giữa giải thích khái niệm, hướng dẫn kiến trúc và demo trực tiếp giúp tôi hiểu rõ cách AWS triển khai bảo mật ở quy mô lớn. Các thảo luận về thách thức bảo mật cloud tại Việt Nam làm nội dung trở nên rất thực tế. Cấu trúc trình bày từng trụ cột giúp củng cố cái nhìn tổng thể cần thiết cho kiến trúc bảo mật thực tế.

### Bài Học Rút Ra

- Mức độ trưởng thành IAM là bước quan trọng đầu tiên để xây dựng môi trường cloud an toàn
- Detection phải chủ động, tự động và tích hợp trên mọi tầng hạ tầng
- Phân đoạn mạng và phòng thủ theo tầng giảm đáng kể rủi ro
- Quản lý khóa và secrets đúng cách ngăn chặn nhiều lỗi bảo mật phổ biến
- Incident response cần được lập kế hoạch, tự động hóa và cải tiến liên tục
- Bảo mật là vòng đời liên tục, không chỉ là nhiệm vụ một lần

> Nhìn chung, sự kiện cung cấp kiến thức thực hành hữu ích và trải nghiệm ngành thực tế, giúp tôi nâng cao hiểu biết về công nghệ cloud và phát triển kỹ năng thực hành thông qua demo và thảo luận. Đồng thời, tôi củng cố khả năng tự học, hợp tác hiệu quả và cập nhật các xu hướng hiện tại—đóng góp tích cực cho sự phát triển nghề nghiệp trong lĩnh vực IT và cloud.
