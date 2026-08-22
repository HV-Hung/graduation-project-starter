*Navigation:* [🏠 Home](../README.md) | [⬅️ Previous: Phase 6](../06-Backend-API/README.md)
***

# Phase 7: Ghép nối toàn hệ thống (Integration)

## Overview
Chúc mừng bạn đã đi đến chặng cuối cùng của đồ án! Frontend đã có UI đẹp mắt, Backend đã có các `Endpoint` xử lý dữ liệu chuẩn xác. Ở phase này, chúng ta sẽ "bắt cầu" để hai phần này nói chuyện được với nhau, tạo thành một hệ thống web hoàn chỉnh. Bạn sẽ xóa bỏ `Mock Data` và gọi API thực tế.

## Prerequisites
*   Hoàn thành Phase 5 (React UI với Mock Data).
*   Hoàn thành Phase 6 (Backend API đã test thành công trên Postman).

## Concepts
*   **CORS (Cross-Origin Resource Sharing):** Cơ chế bảo mật của trình duyệt ngăn chặn một trang web ở tên miền/port này (ví dụ 5173) gọi API ngầm tới một tên miền/port khác (ví dụ 3000). Chúng ta cần cấu hình Backend để cho phép điều này.
*   **Middleware:** Trong Express, `Middleware` là các hàm chạy ở giữa (can thiệp vào) quá trình nhận Request và trả về Response. `cors` chính là một `Middleware`.
*   **Fetch / Axios:** Các công cụ/thư viện giúp Frontend gửi HTTP Request tới Backend để lấy hoặc cập nhật dữ liệu.
*   **Lifecycle (React):** Vòng đời của một `Component`. Chúng ta thường gọi API để lấy dữ liệu lần đầu ngay sau khi giao diện vừa render xong (sử dụng `useEffect`).

## Step-by-Step Tasks

### Bước 1: Cài đặt và cấu hình CORS ở Backend
1.  Mở Terminal trong thư mục `backend`, cài đặt thư viện `cors`:
    ```bash
    npm install cors
    ```
2.  Mở file `server.js` và thêm `Middleware` CORS vào (nhớ để TRƯỚC các dòng khai báo API):
    ```javascript
    const cors = require('cors');
    
    // Cấu hình cho phép Frontend ở port 5173 được phép gọi API
    app.use(cors({
      origin: 'http://localhost:5173'
    }));
    ```

### Bước 2: Tạm biệt Mock Data ở Frontend
1.  Quay trở lại thư mục `frontend/src`. Mở file `App.jsx` (hoặc file chứa Todo List của bạn).
2.  **Xóa (hoặc comment lại)** mảng `mockTodos` mà chúng ta đã làm ở Phase 5.
3.  Thay đổi `State` khởi tạo thành một mảng rỗng: `const [todos, setTodos] = useState([]);`

### Bước 3: Gọi API GET để lấy danh sách thực tế
*TODO: Import `useEffect` từ React. Bên trong `useEffect`, sử dụng `fetch` hoặc `axios` gọi đến `http://localhost:3000/api/todos`. Khi có kết quả trả về, dùng `setTodos(data)` để cập nhật UI.*

### Bước 4: Cập nhật các thao tác Thêm, Sửa, Xóa gọi API
Thay vì chỉ thay đổi `State` ở mảng cục bộ, bây giờ ở mỗi thao tác, bạn phải gọi API trước. Khi Backend báo thành công, mới cập nhật lại UI:
*   **Khi Thêm mới:** Gọi API `POST`. Thành công -> Thêm vào `State`.
*   **Khi Đổi trạng thái/Sửa:** Gọi API `PUT`. Thành công -> Sửa trong `State`.
*   **Khi Xóa:** Gọi API `DELETE`. Thành công -> Xóa khỏi `State`.

*TODO: Cập nhật lại logic cho các hàm `handleAdd`, `handleToggle`, `handleDelete` của bạn.*

## Verification (Checklist Cuối Cùng)
Hãy test lại toàn bộ luồng dữ liệu (UI -> API -> Database) bằng checklist sau:

- [ ] **Khởi động:** Chạy `npm run dev` ở cả 2 thư mục `frontend` và `backend`. Đảm bảo Docker (Postgres) vẫn đang chạy.
- [ ] **Load dữ liệu:** Mở `http://localhost:5173`. Giao diện có hiển thị đúng các Todo đã tạo thử bằng Postman ở Phase 6 không?
- [ ] **Thêm Todo:** Thêm một công việc mới trên giao diện. Nó có hiện ra liền không? Mở pgAdmin kiểm tra xem DB đã có dòng mới đó chưa.
- [ ] **Sửa Todo:** Đánh dấu hoàn thành một công việc. Load lại (F5) trang web xem trạng thái đó có được giữ nguyên không? (Nếu giữ nguyên tức là đã lưu thành công xuống DB).
- [ ] **Xóa Todo:** Xóa một công việc trên UI. Vào pgAdmin xem dòng đó đã biến mất chưa.

Nếu bạn đánh dấu tích được tất cả các mục trên, **XIN CHÚC MỪNG!** Bạn đã hoàn thành xuất sắc PoC đầu tiên của đồ án tốt nghiệp - Một Fullstack Web Application thực thụ!

***
*Navigation:* [🏠 Home](../README.md) | [⬅️ Previous: Phase 6](../06-Backend-API/README.md)
