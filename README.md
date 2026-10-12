# Bài 5: Khởi chạy Web Server bằng Docker Compose

## 1. Mục tiêu

* Sử dụng Docker Compose CLI v2 để quản lý dịch vụ web.
* Khởi chạy Nginx bằng Docker Compose.
* Kiểm tra trạng thái dịch vụ và phản hồi HTTP.
* Dừng và xóa các tài nguyên được tạo bởi Docker Compose.

## 2. Cấu hình Docker Compose

Tạo tệp `docker-compose.yml` với nội dung:

```yaml
services:
  web:
    image: nginx:alpine
    ports:
      - "8082:80"
```

## 3. Khởi chạy dịch vụ

Chạy lệnh:

```bash
docker compose up -d
```

Lệnh này tạo và khởi chạy dịch vụ Nginx ở chế độ nền.

## 4. Kiểm tra trạng thái dịch vụ

Chạy lệnh:

```bash
docker compose ps
```

Kết quả mong đợi: Dịch vụ `web` có trạng thái đang chạy và cổng `8082` trên máy tính được ánh xạ tới cổng `80` trong container.

## 5. Kiểm tra Web Server

Chạy lệnh:

```bash
curl http://localhost:8082
```

Kết quả mong đợi: Lệnh trả về mã HTML của trang mặc định Nginx, có nội dung `Welcome to nginx!`.

## 6. Dừng dịch vụ

Sau khi kiểm tra xong, chạy lệnh:

```bash
docker compose down
```

Lệnh này dừng và xóa các container cùng mạng do Docker Compose tạo cho dự án. Image Nginx vẫn được giữ lại.

## 7. Kết luận

Đã sử dụng Docker Compose CLI v2 để cấu hình, khởi chạy, kiểm tra và dừng dịch vụ Nginx. Dịch vụ được truy cập thông qua cổng 8082 của máy tính.
