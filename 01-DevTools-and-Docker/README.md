*Navigation:* [🏠 Home](../README.md) | [Next: Phase 2 ➡️](../02-React-Init-and-Git/README.md)
***

# Phase 1: Setup Môi trường Phát triển và Database (Docker)

## Overview
Chào mừng bạn đến với chặng đường đầu tiên của đồ án tốt nghiệp! Ở phase này, chúng ta sẽ chuẩn bị các công cụ cần thiết nhất (DevTools) và thiết lập một `Database` PostgreSQL cùng với công cụ quản lý pgAdmin thông qua Docker. Việc setup môi trường tốt từ đầu sẽ giúp bạn tập trung hoàn toàn vào việc code sau này.

## Prerequisites
Không có yêu cầu đặc biệt. Bạn chỉ cần một chiếc máy tính có kết nối Internet!

## Concepts
*   **DevTools:** Các công cụ hỗ trợ lập trình viên (trình duyệt, IDE, hệ quản trị cơ sở dữ liệu...).
*   **Docker:** Một nền tảng giúp bạn đóng gói phần mềm cùng với toàn bộ môi trường chạy của nó vào các `Container`.
*   **Container:** Một môi trường cô lập, nhẹ và độc lập, giúp ứng dụng chạy giống hệt nhau trên mọi máy tính.
*   **Volume:** Cơ chế lưu trữ dữ liệu bền vững của Docker, đảm bảo dữ liệu trong `Database` không bị mất đi khi `Container` bị xóa.
*   **Database:** Nơi lưu trữ và tổ chức dữ liệu của ứng dụng.

## Step-by-Step Tasks

### Bước 1: Cài đặt DevTools
Hãy tải và cài đặt các phần mềm dưới đây theo hệ điều hành của bạn:
1.  **VS Code:** Editor chính để viết code. [Tải tại đây](https://code.visualstudio.com/)
2.  **Node.js:** Môi trường chạy JavaScript (Nên tải bản LTS). [Tải tại đây](https://nodejs.org/)
3.  **Git:** Hệ thống quản lý mã nguồn. [Tải tại đây](https://git-scm.com/)
4.  **Docker Desktop:** Chạy và quản lý các `Container`. [Tải tại đây](https://www.docker.com/products/docker-desktop/)

### Bước 2: Tạo cấu trúc thư mục
Tạo thư mục gốc cho dự án của bạn (ví dụ: `graduation-project`), sau đó mở thư mục này trong VS Code.

### Bước 3: Tạo file `docker-compose.yml`
Tại thư mục gốc, tạo một file tên là `docker-compose.yml`. File này định nghĩa các `Container` cho `Database` Postgres và pgAdmin. Hãy copy đoạn boilerplate code sau vào file:

```yaml
version: '3.8'

services:
  db:
    image: postgres:15
    container_name: postgres_db
    restart: always
    environment:
      POSTGRES_USER: root
      POSTGRES_PASSWORD: rootpassword
      POSTGRES_DB: todolist
    ports:
      - "5432:5432"
    volumes:
      - postgres_data:/var/lib/postgresql/data

  pgadmin:
    image: dpage/pgadmin4
    container_name: pgadmin
    restart: always
    environment:
      PGADMIN_DEFAULT_EMAIL: admin@admin.com
      PGADMIN_DEFAULT_PASSWORD: adminpassword
    ports:
      - "5050:80"
    depends_on:
      - db

volumes:
  postgres_data:
```

### Bước 4: Chạy các câu lệnh Docker
Mở Terminal trong VS Code và thực hành các lệnh sau:

*   **Khởi chạy hệ thống (chạy ngầm trong background):**
    ```bash
    docker-compose up -d
    ```
*   **Dừng hệ thống:**
    ```bash
    docker-compose down
    ```
*   **Dừng và xóa toàn bộ dữ liệu (Reset Database):** ĐẶC BIỆT chú ý lệnh này, nó sẽ xóa cả `Volume` lưu trữ dữ liệu của bạn, rất hữu ích khi muốn reset mọi thứ về trạng thái ban đầu:
    ```bash
    docker-compose down -v
    ```

## Verification
*   **Kiểm tra DevTools:** Mở Terminal và gõ `node -v`, `git --version`, `docker --version`. Nếu có số version hiện ra nghĩa là bạn đã cài đặt thành công.
*   **Kiểm tra Database:** 
    1.  Chạy `docker-compose up -d`.
    2.  Mở trình duyệt, truy cập `http://localhost:5050`.
    3.  Đăng nhập với email `admin@admin.com` và password `adminpassword`.
    4.  Nếu bạn vào được giao diện pgAdmin, tuyệt vời! Bạn đã hoàn thành xuất sắc Phase 1!

***
*Navigation:* [🏠 Home](../README.md) | [Next: Phase 2 ➡️](../02-React-Init-and-Git/README.md)
