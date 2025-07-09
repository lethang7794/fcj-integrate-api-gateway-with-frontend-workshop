---
title: Tích hợp API Gateway với frontend được lưu trữ trên S3
weight: 1
chapter: false
---

# Tích hợp API Gateway với frontend được lưu trữ trên S3

Trong workshop trước, bạn đã sử dụng API Gateway để tạo một REST API được hỗ trợ bởi các hàm Lambda.

Trong workshop này, bạn sẽ:

- Tích hợp ứng dụng frontend với REST API của bạn, bao gồm:

  - Cấu hình ứng dụng frontend để kết nối với REST API của bạn.
  - Cấu hình CORS cho API Gateway để cho phép giao tiếp từ ứng dụng frontend.

- Triển khai ứng dụng frontend của bạn bằng tính năng _lưu trữ trang web tĩnh_ của S3.

Kiến trúc hệ thống của chúng ta sẽ trông như sau:

![alt text](/images/diagrams/workshop-3--api-gateway--rest-api--event.drawio.svg)
