*Navigation:* [🏠 Home](../README.md) | [⬅️ Previous: Phase 5](../05-React-UI-TodoList/README.md) | [Next: Phase 7 ➡️](../07-Integration/README.md)
***

# Phase 6: Xây dựng CRUD API cho Backend

## Overview
Giao diện đã đẹp, Database đã sẵn sàng. Phase này là lúc chúng ta viết các `Endpoint` (API) thực thụ ở Backend để Frontend có thể lấy và thao tác với dữ liệu thật. Đây được gọi là hệ thống CRUD (Create - Read - Update - Delete).

## Prerequisites
*   Hoàn thành Phase 4 (đã kết nối Postgres và có bảng `todos`).
*   Tải và cài đặt phần mềm [Postman](https://www.postman.com/downloads/) (công cụ để test API).

## Concepts
*   **CRUD:** Viết tắt của Create, Read, Update, Delete - 4 thao tác cơ bản nhất khi làm việc với `Database`.
*   **HTTP Methods:** Các phương thức gọi API, tương ứng với CRUD: `POST` (Tạo mới), `GET` (Đọc), `PUT/PATCH` (Cập nhật), `DELETE` (Xóa).
*   **Request Body:** Nơi chứa dữ liệu gửi lên từ Client (ví dụ: nội dung Todo muốn tạo mới).
*   **JSON:** Định dạng dữ liệu phổ biến nhất để trao đổi giữa Frontend và Backend.

## Step-by-Step Tasks

### Bước 1: Cấu hình Express để đọc JSON
Trong file `server.js` ở `backend`, bạn phải thêm đoạn `Middleware` sau để Express có thể hiểu được định dạng JSON từ Client gửi lên:
```javascript
// Thêm dòng này TRƯỚC các đường dẫn API
app.use(express.json());
```

### Bước 2: Viết API GET (Read) - Lấy danh sách Todo
*TODO: Tạo `Endpoint` `GET /api/todos`.*
Sử dụng hàm `pool.query('SELECT * FROM todos ORDER BY id ASC')` để lấy toàn bộ dữ liệu từ bảng `todos` và trả về cho Client (`res.json(data)`).

### Bước 3: Viết API POST (Create) - Thêm Todo mới
*TODO: Tạo `Endpoint` `POST /api/todos`.*
Đọc dữ liệu `title` từ `req.body`. Sử dụng câu lệnh SQL `INSERT INTO todos (title) VALUES ($1) RETURNING *` để lưu vào DB.

### Bước 4: Viết API PUT (Update) - Cập nhật trạng thái
*TODO: Tạo `Endpoint` `PUT /api/todos/:id`.*
Đọc `id` từ `req.params.id` và trạng thái `completed` (hoặc `title` mới) từ `req.body`. Sử dụng SQL `UPDATE` để sửa dòng dữ liệu tương ứng.

### Bước 5: Viết API DELETE (Delete) - Xóa Todo
*TODO: Tạo `Endpoint` `DELETE /api/todos/:id`.*
Đọc `id` từ `req.params.id`. Sử dụng SQL `DELETE FROM todos WHERE id = $1` để xóa item.

## Verification (BẮT BUỘC)
Sau khi viết xong các API, bạn KHÔNG ĐƯỢC dùng Frontend vội. Hãy kiểm tra bằng cách:
1.  **Test API bằng Postman:** Mở Postman, tạo các Request gọi đến từng `Endpoint` tại `http://localhost:3000/api/todos`:
    *   **GET:** Chọn method `GET`, nhấn Send. Đảm bảo trả về danh sách todos (Status 200).
    *   **POST:** Chọn method `POST`, vào tab **Body** → chọn **raw** → chọn **JSON**, nhập nội dung sau rồi nhấn Send:
        ```json
        {
          "title": "Học Express"
        }
        ```
        Đảm bảo trả về todo vừa tạo (Status 201).
    *   **PUT / DELETE:** Tương tự, thay đổi method và URL (ví dụ: `http://localhost:3000/api/todos/1`).
2.  **Kiểm chứng bằng pgAdmin:** Sau khi gửi lệnh `POST` thêm mới từ Postman, hãy mở pgAdmin, chuột phải vào bảng `todos` -> **View/Edit Data**. Hãy tự mình xác nhận xem dữ liệu mới có thực sự xuất hiện dưới `Database` hay không. Tương tự cho các thao tác Update và Delete.

***
*Navigation:* [🏠 Home](../README.md) | [⬅️ Previous: Phase 5](../05-React-UI-TodoList/README.md) | [Next: Phase 7 ➡️](../07-Integration/README.md)
