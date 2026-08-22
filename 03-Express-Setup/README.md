*Navigation:* [🏠 Home](../README.md) | [⬅️ Previous: Phase 2](../02-React-Init-and-Git/README.md) | [Next: Phase 4 ➡️](../04-Database-Connection/README.md)
***

# Phase 3: Khởi tạo Backend với Node.js và Express.js

## Overview
Chào mừng bạn đã trở lại! Trong phase này, chúng ta sẽ bắt đầu xây dựng bộ não của ứng dụng - phần Backend. Bạn sẽ học cách khởi tạo một dự án Node.js, cài đặt framework Express.js cực kỳ phổ biến, và tạo ra một `Endpoint` đơn giản để backend có thể "chào hỏi" thế giới!

## Prerequisites
*   Hoàn thành Phase 1 (cài đặt Node.js) và Phase 2 (quen thuộc với Terminal).

## Concepts
*   **Backend:** Phần logic chạy trên máy chủ (server), xử lý dữ liệu và giao tiếp với `Database`.
*   **Express.js:** Một framework nhẹ và mạnh mẽ của Node.js giúp xây dựng các ứng dụng web và API dễ dàng.
*   **Routing:** Cơ chế định tuyến, quyết định xem khi người dùng gọi đến một đường dẫn (URL) nào thì code nào sẽ được chạy.
*   **Endpoint:** Một địa chỉ URL cụ thể trên server (ví dụ: `/hello`) mà Frontend có thể gọi tới để lấy dữ liệu.

## Step-by-Step Tasks

### Bước 1: Khởi tạo thư mục Backend
Mở Terminal ở thư mục gốc của dự án, sau đó tạo một thư mục mới tên là `backend` và di chuyển vào đó:
```bash
mkdir backend
cd backend
```

### Bước 2: Khởi tạo dự án Node.js
Chạy lệnh sau để tạo file `package.json` (nơi quản lý các thông tin và thư viện của backend):
```bash
npm init -y
```

### Bước 3: Cài đặt Express.js
Cài đặt thư viện Express.js vào dự án:
```bash
npm install express
```
Để quá trình phát triển thuận lợi hơn, bạn cũng nên cài thêm `nodemon`. Công cụ này sẽ tự động khởi động lại server mỗi khi bạn lưu file code mới:
```bash
npm install --save-dev nodemon
```
*(Lưu ý: Mở file `package.json` lên và thêm `"dev": "nodemon server.js"` vào phần `"scripts"` nhé!)*

### Bước 4: Viết đoạn code đầu tiên
Tạo một file có tên `server.js` bên trong thư mục `backend`. Bạn hãy sử dụng đoạn boilerplate sau làm nền tảng:

```javascript
const express = require('express');
const app = express();

// Khai báo cổng chạy server (Port 3000)
const PORT = 3000;

// TODO: Tạo một GET Endpoint tại đường dẫn '/hello'
// Gợi ý: app.get('/hello', (req, res) => { ... })
app.get('/hello', (req, res) => {
  res.send('Hello World từ Express Backend!');
});

// Khởi chạy server
app.listen(PORT, () => {
  console.log(`Server đang chạy tại http://localhost:${PORT}`);
});
```

### Bước 5: Chạy server
Mở Terminal (đảm bảo đang ở trong thư mục `backend`) và chạy lệnh sau:
```bash
npm run dev
```
*(Nếu bạn không thiết lập nodemon ở Bước 3, bạn có thể chạy bằng `node server.js`)*

## Verification
*   **Kiểm tra Endpoint:** Mở trình duyệt web của bạn và truy cập vào đường dẫn `http://localhost:3000/hello`. 
*   Nếu bạn nhìn thấy dòng chữ "Hello World từ Express Backend!" hiển thị trên màn hình, chúc mừng bạn! Backend của bạn đã chính thức hoạt động!

***
*Navigation:* [🏠 Home](../README.md) | [⬅️ Previous: Phase 2](../02-React-Init-and-Git/README.md) | [Next: Phase 4 ➡️](../04-Database-Connection/README.md)
