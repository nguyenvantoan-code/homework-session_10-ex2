# Bài 2: Đóng gói ứng dụng Backend bằng Single-stage Dockerfile

## 1. Mục tiêu

- Xây dựng ứng dụng REST API đơn giản bằng Node.js và Express.
- Viết Dockerfile theo mô hình Single-stage.
- Build Docker Image và chạy ứng dụng trong Container.
- Kiểm tra API thông qua HTTP request.

## 2. Công nghệ sử dụng

- Node.js 18 Alpine
- Express.js
- Docker

## 3. Cấu trúc dự án

```text
ex2/
├── Dockerfile
├── package.json
├── server.js
└── README.md
```

## 4. Xây dựng Docker Image

```bash
docker build -t hw-backend:v1 .
```

## 5. Khởi chạy Container

```bash
docker run -d --name app-single-stage -p 8080:3000 hw-backend:v1
```

Cổng 8080 trên máy chủ được ánh xạ đến cổng 3000 trong Container.

## 6. Kiểm tra hoạt động

Kiểm tra Container:

```bash
docker ps
```

Xem log:

```bash
docker logs app-single-stage
```

Gửi HTTP request:

```bash
curl -i http://localhost:8080/
```

## 7. Kết quả mong đợi

API trả về mã HTTP `200 OK` cùng dữ liệu JSON:

```json
{
  "status": "success",
  "message": "Hello from Docker Single-stage!"
}
```

## 8. Kết luận

Ứng dụng đã được đóng gói thành Docker Image `hw-backend:v1` bằng Single-stage Dockerfile. Container có thể chạy độc lập với môi trường Node.js được đóng gói bên trong Image, giúp quá trình triển khai và kiểm thử ứng dụng thuận tiện hơn.
