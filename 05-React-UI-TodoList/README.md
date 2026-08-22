*Navigation:* [🏠 Home](../README.md) | [⬅️ Previous: Phase 4](../04-Database-Connection/README.md) | [Next: Phase 6 ➡️](../06-Backend-API/README.md)
***

# Phase 5: Xây dựng Giao diện React với Mock Data

## Overview
Quay trở lại với Frontend nhé! Ở phase này, bạn sẽ thiết kế và xây dựng giao diện hoàn chỉnh cho ứng dụng Todo List. Để tập trung hoàn toàn vào làm UI mà không bị vướng mắc bởi Backend, bạn bắt buộc phải sử dụng `Mock Data` (dữ liệu giả) thay vì gọi API thật.

## Prerequisites
*   Hoàn thành Phase 2 (khởi tạo React app).

## Concepts
*   **Component:** Các khối giao diện độc lập, có thể tái sử dụng trong React (ví dụ: `TodoItem`, `TodoList`).
*   **State:** Trạng thái lưu trữ dữ liệu nội bộ của một `Component`. Khi `State` thay đổi, giao diện sẽ tự động cập nhật lại (Re-render).
*   **Mock Data:** Dữ liệu mẫu (thường là JSON cứng) dùng để lập trình và test giao diện trước khi có kết nối API thật.

## Step-by-Step Tasks

### Bước 1: Khởi tạo Mock Data
Trong thư mục `frontend/src`, hãy tạo một file `App.jsx` (hoặc sửa file có sẵn). Bắt đầu bằng việc định nghĩa một mảng dữ liệu giả:

```jsx
// Sử dụng Mock Data này để render UI
const mockTodos = [
  { id: 1, title: "Học React JS", completed: true },
  { id: 2, title: "Làm Backend Node.js", completed: false },
  { id: 3, title: "Kết nối Database", completed: false }
];
```

### Bước 2: Thiết kế UI Danh sách
Hãy sử dụng hàm `map()` của mảng để render danh sách `mockTodos` ra màn hình.
*TODO: Viết code HTML/JSX để hiển thị từng item trong mảng ra danh sách.*

### Bước 3: Thêm tính năng Thêm mới (Add)
Tạo một ô input và một nút "Add".
*TODO: Khai báo một `State` (ví dụ `const [todos, setTodos] = useState(mockTodos)`). Khi người dùng nhập text và nhấn Add, hãy thêm một object mới vào mảng `State`.*

### Bước 4: Thêm tính năng Xóa (Delete) và Hoàn thành (Toggle)
*   **Xóa:** Mỗi Todo item nên có một nút Xóa.
*   **Hoàn thành:** Thêm một Checkbox. Khi click vào, đổi trạng thái `completed` của item đó.
*TODO: Viết các hàm xử lý sự kiện `onClick` và `onChange` để cập nhật lại `State` tương ứng.*

### Bước 5: (Tùy chọn) Chức năng Sửa (Edit)
*TODO: Hiển thị một nút "Edit" bên cạnh mỗi item. Khi bấm vào, biến text đó thành một ô input để sửa, sau đó lưu lại cập nhật vào `State`.*

## Verification
*   Chạy lệnh `npm run dev` trong thư mục `frontend`.
*   Truy cập vào trình duyệt. Hãy thử thêm, sửa, xóa, và đánh dấu hoàn thành các Todo.
*   Nếu giao diện phản hồi mượt mà và đúng logic (dù chỉ là thao tác trên `Mock Data`), bạn đã hoàn thành xuất sắc! Ở phase sau, chúng ta mới thay thế `Mock Data` này bằng API thực tế.

***
*Navigation:* [🏠 Home](../README.md) | [⬅️ Previous: Phase 4](../04-Database-Connection/README.md) | [Next: Phase 6 ➡️](../06-Backend-API/README.md)
