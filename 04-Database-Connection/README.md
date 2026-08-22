*Navigation:* [🏠 Home](../README.md) | [⬅️ Previous: Phase 3](../03-Express-Setup/README.md) | [Next: Phase 5 ➡️](../05-React-UI-TodoList/README.md)
***

# Phase 4: Kết nối Database và Tạo Bảng Dữ liệu

## Overview
Backend của chúng ta đã chạy, nhưng nó chưa thể nhớ được thông tin gì cả vì chưa có bộ nhớ. Ở phase này, chúng ta sẽ kết nối Express Backend với PostgreSQL `Database` mà bạn đã tạo ở Phase 1. Đồng thời, bạn sẽ sử dụng công cụ pgAdmin để tạo bảng dữ liệu đầu tiên, sẵn sàng cho việc lưu trữ các công việc (todos).

## Prerequisites
*   Hoàn thành Phase 1 (Docker PostgreSQL & pgAdmin đang chạy).
*   Hoàn thành Phase 3 (Backend Express đang hoạt động ở port 3000).

## Concepts
*   **Environment Variables:** Các biến môi trường, thường được lưu trong file `.env` để bảo mật các thông tin nhạy cảm (như mật khẩu Database) mà không bị đẩy lên GitHub.
*   **SQL (Structured Query Language):** Ngôn ngữ dùng để giao tiếp và thao tác dữ liệu với PostgreSQL.
*   **Table:** Bảng dữ liệu trong SQL, bao gồm các hàng (row) và cột (column).

## Step-by-Step Tasks

### Bước 1: Cài đặt thư viện kết nối Database
Tại Terminal, bên trong thư mục `backend`, hãy cài đặt thư viện `pg` (để kết nối Postgres) và `dotenv` (để đọc các `Environment Variables`):
```bash
npm install pg dotenv
```

### Bước 2: Thiết lập file biến môi trường (`.env`)
Tạo một file có tên là `.env` nằm trực tiếp trong thư mục `backend`. File này sẽ chứa chuỗi kết nối tới Postgres. 
*Lưu ý: Bạn nhớ thêm `.env` vào file `.gitignore` ở thư mục gốc (hoặc backend) để không đẩy lên Git nhé!*

Nội dung file `.env` như sau:
```env
# Chuỗi kết nối Database (Connection String)
# Cấu trúc: postgres://<username>:<password>@<host>:<port>/<database_name>
DATABASE_URL=postgres://root:rootpassword@localhost:5432/todolist
```

### Bước 3: Cấu hình kết nối trong Express
Trong thư mục `backend`, tạo một file `db.js`. Đây sẽ là nơi thiết lập kết nối:

```javascript
// Load các Environment Variables từ file .env
require('dotenv').config();
const { Pool } = require('pg');

// TODO: Khởi tạo một Pool kết nối tới Database sử dụng chuỗi kết nối
const pool = new Pool({
  connectionString: process.env.DATABASE_URL,
});

module.exports = pool;
```

Sau đó, mở `server.js` lên và thử kết nối xem sao:
```javascript
// (Thêm vào dưới phần import)
const pool = require('./db');

// TODO: Tạo một Endpoint kiểm tra kết nối Database tại GET /test-db
// Gợi ý: Sử dụng pool.query('SELECT NOW()')
```

### Bước 4: Tạo bảng (Table) trong pgAdmin
Bây giờ, chúng ta sẽ thiết kế một bảng để lưu trữ các Todo. Hãy làm theo các bước sau trên pgAdmin (sẽ giúp bạn quen với công cụ UI này):
1.  Đảm bảo Docker đang chạy. Truy cập vào `http://localhost:5050` và đăng nhập pgAdmin.
2.  Click chuột phải vào **Servers** -> **Register** -> **Server...**
    *   Thẻ **General**: Đặt tên là `Local Postgres`.
    *   Thẻ **Connection**: Host name là `db` (đây là tên service trong file docker-compose), Username là `root`, Password là `rootpassword`. Save lại.
3.  Mở rộng Server vừa tạo, tìm đến Database `todolist` -> **Schemas** -> **public**.
4.  Bạn có 2 cách để tạo bảng `todos`:
    *   **Cách 1 (Dùng Tool UI):** Click chuột phải vào **Tables** -> **Create** -> **Table...** và định nghĩa các cột.
    *   **Cách 2 (Dùng Script SQL - Khuyên dùng):** Click vào biểu tượng **Query Tool** (hình ống kính ở thanh công cụ trên cùng), dán đoạn mã SQL sau và nhấn phím F5 để chạy (hoặc nút Play):

```sql
CREATE TABLE todos (
    id SERIAL PRIMARY KEY,
    title VARCHAR(255) NOT NULL,
    completed BOOLEAN DEFAULT FALSE
);
```

## Verification
*   **Kiểm tra Kết nối Express:** Chạy `npm run dev` trong backend. Gọi thử API kiểm tra kết nối `/test-db` (nếu bạn đã làm TODO ở Bước 3). Nếu trả về thời gian hiện tại, kết nối đã thành công!
*   **Kiểm tra pgAdmin:** Làm mới (Refresh) lại mục **Tables** trong pgAdmin. Nếu thấy bảng `todos` xuất hiện với các cột `id`, `title`, và `completed`, xuất sắc! Bạn đã có một Database sẵn sàng phục vụ.

***
*Navigation:* [🏠 Home](../README.md) | [⬅️ Previous: Phase 3](../03-Express-Setup/README.md) | [Next: Phase 5 ➡️](../05-React-UI-TodoList/README.md)
