---
title: "Event 3"
date: 2025-09-09
weight: 1
chapter: false
pre: " <b> 4.3. </b> "
---

# Bài thu hoạch: “AWS Cloud Mastery Series #2 – DevOps on AWS”

### Mục Đích Của Sự Kiện

- Cung cấp hiểu biết toàn diện về văn hóa, nguyên tắc và best practices của DevOps
- Trình bày cách triển khai CI/CD pipeline sử dụng AWS Developer Tools
- Giới thiệu các giải pháp Infrastructure as Code (IaC) với CloudFormation và AWS CDK
- Khám phá containerization, orchestration và triển khai microservices trên AWS
- Nâng cao kỹ năng giám sát và observability với CloudWatch và X-Ray
- Hướng dẫn phát triển sự nghiệp DevOps và các chứng chỉ AWS

### Nội Dung Nổi Bật

#### DevOps Mindset: 
- Hợp tác, cải tiến liên tục, DORA metrics (MTTR, deployment frequency), xây dựng văn hóa

#### CI/CD Pipeline trên AWS:

- Quản lý phiên bản với CodeCommit & chiến lược Git
- CodeBuild để biên dịch và kiểm thử
- CodeDeploy với các phương pháp triển khai blue/green, canary và rolling
- CodePipeline để tự động hóa toàn bộ quy trình
- Live demo workflow CI/CD end-to-end

#### Infrastructure as Code (IaC):

- CloudFormation stacks, templates, phát hiện drift
- AWS CDK: constructs, reusable patterns, hỗ trợ nhiều ngôn ngữ
- Demo so sánh các công cụ IaC và lựa chọn phương pháp phù hợp

#### Containers & Microservices:

- Kiến thức cơ bản về Docker và vòng đời container
- Amazon ECR để lưu trữ và scan image
- Amazon ECS & EKS cho orchestration và scale
- AWS App Runner cho triển khai đơn giản
- Case study về các mẫu triển khai microservices

#### Monitoring & Observability:

- CloudWatch logs, metrics, alarms, dashboards
- AWS X-Ray cho distributed tracing và root cause analysis
- Best practices cho alerting và quy trình on-call

#### DevOps Best Practices:

- Feature flags, automated testing, A/B testing
- Incident response, postmortems, operational excellence
- Câu chuyện thực tế về chuyển đổi DevOps

### Những Gì Học Được

- DevOps không chỉ về công cụ mà còn về văn hóa và giao tiếp
- Tự động hóa CI/CD cải thiện tốc độ, độ tin cậy và giảm rủi ro triển khai
- IaC đảm bảo quản lý hạ tầng nhất quán, có thể lặp lại và mở rộng
- Containers và orchestrators (ECS/EKS) cho kiến trúc microservices linh hoạt
- Observability rất quan trọng để chẩn đoán vấn đề hiệu suất và đảm bảo sức khỏe hệ thống
- Các chiến lược triển khai hiện đại (blue/green, canary, feature flags) giảm downtime và tăng an toàn

### Ứng Dụng Vào Công Việc

- Triển khai CI/CD pipeline để tự động hóa build, test và deploy
- Sử dụng CloudFormation hoặc CDK để đảm bảo hạ tầng nhất quán giữa các môi trường
- Áp dụng containerization cho thiết kế dịch vụ module và có khả năng mở rộng
- Sử dụng dashboards và distributed tracing để nâng cao quan sát vận hành
- Áp dụng best practices DevOps như automated testing, postmortems và cải tiến liên tục

### Trải nghiệm trong event

Buổi hội thảo cung cấp cái nhìn toàn diện về thực hành DevOps trên AWS — từ văn hóa, metrics, pipeline, IaC, triển khai container, đến observability. Các demo thực hành và case study thực tế giúp tôi hiểu rõ cách các nhóm kỹ sư hiện đại đạt tốc độ cao, độ tin cậy và operational excellence. Sự kiện nâng cao đáng kể sự tự tin của tôi trong việc áp dụng nguyên tắc DevOps và công cụ AWS vào các dự án thực tế.

### Bài Học Rút Ra

- IaC là cần thiết: CloudFormation và CDK đảm bảo triển khai hạ tầng có thể lặp lại, kiểm soát phiên bản
- Tự động hóa CI/CD cải thiện độ tin cậy
- Monitoring & Observability là yếu tố then chốt: CloudWatch, CloudTrail, X-Ray giúp theo dõi hiệu suất và phát hiện lỗi nhanh
- Tích hợp kiểm tra bảo mật, IAM policies, guardrails vào CI/CD pipelines tăng cường an ninh
- Hợp tác chặt chẽ giữa dev và ops giúp tăng tốc độ triển khai và ổn định hệ thống
- Scripting deployment, rollback, và automated testing cải thiện hiệu quả và giảm downtime
- Sử dụng ECS, EKS, Docker đảm bảo môi trường nhất quán, khả năng scale và linh hoạt triển khai

### Một số hình ảnh khi tham gia sự kiện
![Event photos](/images/IMG_0690.jpg)

> Nhìn chung, sự kiện cung cấp trải nghiệm học tập thực hành toàn diện, bao gồm CI/CD, IaC, container technologies, và best practices về observability, giúp tôi củng cố mindset DevOps, kỹ năng kỹ thuật và hiểu biết về công cụ DevOps trên AWS.