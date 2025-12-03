---
title: "Worklog Tuần 4"
date: 2025-09-09
weight: 1
chapter: false
pre: " <b> 1.4. </b> "
---

### Mục tiêu tuần 4:

- Phát triển frontend service cho dự án nhóm.
- Củng cố kiến thức về AWS Compute, tập trung vào EC2, các lựa chọn storage, và Auto Scaling.
- Tìm hiểu thêm các dịch vụ compute liên quan: EFS, FSx, Lightsail, MGN.
- Hoàn thành các hands-on labs về AWS Backup, Storage Gateway, Amazon S3.
- Bắt đầu dịch các bài blog.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| Cả tuần   | - Phát triển frontend code cho dự án nhóm   | 29/09/2025 | 03/10/2025      |
| 1   | - Module 03-01 – Compute VM on AWS: <br>&emsp; + EC2 Instance Types <br>&emsp; + AMI / Backup / Key Pair <br>&emsp; + EBS <br>&emsp; + Instance Store <br>&emsp; + User Data <br>&emsp; + Meta Data <br>&emsp; + EC2 Auto Scaling <br>&emsp;  | 29/09/2025 | 29/09/2025      | <https://www.youtube.com/@AWSStudyGroup> |
| 2   | - Module 03-02 – EC2 Autoscaling, EFS, FSx, Lightsail, MGN <br> - Hands-on Labs: <br>&emsp; + Deploy AWS Backup to the System <br>&emsp; + Using File Storage Gateway| 30/09/2025 | 30/09/2025 | - <https://cloudjourney.awsstudygroup.com/> <br> - <https://000013.awsstudygroup.com/> <br> - <https://000024.awsstudygroup.com/>      |
| 3-4   | - Hands-on Lab: Starting with Amazon S3 | 01/10/2025 | 02/10/2025 | <https://000057.awsstudygroup.com/> |
| 5-7  | - Dịch blog | 03/10/2025 |  |  |


### Kết quả đạt được tuần 4:

#### Project Development:

- Dành cả tuần để triển khai phần frontend của dự án nhóm.
- Cải thiện UI structure, layout và các component workflows cơ bản.
- Phối hợp với backend team để đảm bảo frontend phù hợp API và yêu cầu hệ thống.

#### Kiến thức AWS đã học:

- Hiểu sâu hơn về Amazon EC2, bao gồm:
  - Instance types cho các workload khác nhau.
  - AMIs và các chiến lược backup.
  - Key Pair và xác thực cho instance.
  - So sánh EBS vs Instance Store và use cases.
  - Scripting với User Data cho automation.
  - Sử dụng Metadata để lấy thông tin instance.
- Tìm hiểu về EC2 Auto Scaling và cách hệ thống tự động thay đổi theo tải.
- Khám phá các dịch vụ compute nâng cao:
  - EFS cho scalable shared file storage.
  - FSx cho high-performance workloads.
  - Lightsail cho môi trường cloud đơn giản.
  - MGN để migrate server lên AWS.

#### Hands-on Labs đã hoàn thành:

  - Deploy AWS Backup to the System
  → Biết cách cấu hình backup cho EC2, EBS và các tài nguyên khác.

  - Using File Storage Gateway
  → Thực hành hybrid storage integration và kết nối với hệ thống on-premises.

  - Starting with Amazon S3
  → Hiểu về S3 buckets, versioning, storage classes, encryption, lifecycle policies.

#### Hoạt động khác

- Bắt đầu dịch các bài blog.
- Công việc dịch vẫn đang tiếp tục.

#### Kỹ năng đạt được:
- Technical Skills

  - Nâng cao kỹ năng phát triển frontend: responsive UI, thiết kế component, xử lý interaction.
  - Thành thạo hơn về EC2, AMIs, EBS vs Instance Store, User Data, Metadata, Auto Scaling.
  - Hiểu thêm về các dịch vụ compute/storage: EFS, FSx, Lightsail, AWS MGN.
  - Thực hành với AWS Backup, File Storage Gateway, và Amazon S3 (bucket, versioning, lifecycle, encryption).

- Cloud Architecture Skills

  - Nâng cao khả năng chọn storage phù hợp (EBS/EFS/S3/FSx).
  - Nắm được best practices cho scalable và secure compute architecture.

- Soft Skills

  - Cải thiện teamwork khi phát triển frontend dự án nhóm.
  - Tăng cường time management và problem-solving thông qua labs và project tasks.