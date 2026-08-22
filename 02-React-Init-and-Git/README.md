*Navigation:* [🏠 Home](../README.md) | [⬅️ Previous: Phase 1](../01-DevTools-and-Docker/README.md) | [Next: Phase 3 ➡️](../03-Express-Setup/README.md)
***

# Phase 2: Khởi tạo React App và Quản lý Mã nguồn với Git

## Overview
Tiếp tục hành trình nào! Trong phase này, chúng ta sẽ tạo phần giao diện người dùng (Frontend) bằng React (sử dụng công cụ Vite cực kỳ nhanh chóng). Sau đó, bạn sẽ thiết lập Git để lưu lại các thay đổi của mình và đưa code lên GitHub. Việc quản lý các `Commit` cẩn thận sẽ giúp bạn dễ dàng theo dõi tiến độ và rollback khi có lỗi.

## Prerequisites
*   Hoàn thành Phase 1 (đã cài đặt Node.js và Git).

## Concepts
*   **Vite:** Một build tool hiện đại giúp khởi tạo và chạy dự án React cực nhanh.
*   **Frontend:** Phần giao diện người dùng mà người dùng tương tác trực tiếp.
*   **Git / GitHub:** Công cụ và nền tảng quản lý mã nguồn và phiên bản.
*   **Commit:** Một "ảnh chụp" lưu lại trạng thái code của bạn tại một thời điểm.
*   **Environment Variables:** Các biến môi trường dùng để lưu trữ các thông tin cấu hình thay đổi theo môi trường (như URL API), thường để trong file `.env`.

## Step-by-Step Tasks

### Bước 1: Khởi tạo dự án React bằng Vite
Mở Terminal tại thư mục gốc của dự án, và chạy lệnh sau để tạo thư mục `frontend` chứa React app:
```bash
npm create vite@latest frontend -- --template react
```
*(Nếu được hỏi, bạn cứ nhấn phím Enter để tiếp tục nhé)*

Sau khi tạo xong, hãy di chuyển vào thư mục và cài đặt các thư viện (packages) cần thiết:
```bash
cd frontend
npm install
```

### Bước 2: Thiết lập file `.gitignore`
Khi đẩy code lên GitHub, chúng ta KHÔNG muốn đẩy các thư mục quá nặng như `node_modules` hoặc các file chứa thông tin nhạy cảm.
Hãy kiểm tra xem trong thư mục `frontend` đã có file `.gitignore` chưa (Vite thường tạo sẵn). Hãy đảm bảo trong file đó có ít nhất 2 dòng sau (nếu chưa có, hãy thêm vào nhé):
```gitignore
node_modules
.env
```

### Bước 3: Khởi chạy dự án Frontend
Hãy thử chạy React app của bạn lên để xem kết quả:
```bash
npm run dev
```
Vite sẽ khởi chạy dự án tại một port mặc định (thường là 5173).

### Bước 4: Quản lý mã nguồn với Git
Mở một Terminal mới (vẫn ở thư mục gốc của toàn dự án nhé, không phải trong thư mục `frontend`), và thực hiện các lệnh sau:

1.  **Tạo file `.gitignore` ở thư mục gốc:**
    Trước khi khởi tạo Git, hãy tạo một file `.gitignore` tại thư mục gốc của dự án để đảm bảo các file nhạy cảm không bị đẩy lên GitHub:
    ```gitignore
    # Không đẩy file chứa thông tin nhạy cảm (Environment Variables)
    .env
    ```
    *(Lưu ý: Thư mục `frontend` đã có `.gitignore` riêng do Vite tạo sẵn. File này ở root sẽ bảo vệ thêm cho các thư mục khác như `backend` sau này.)*

2.  **Khởi tạo Git:**
    ```bash
    git init
    ```
3.  **Đánh dấu toàn bộ thay đổi để chuẩn bị commit:**
    ```bash
    git add .
    ```
4.  **Tạo một `Commit` đầu tiên:**
    ```bash
    git commit -m "Init frontend with Vite and setup docker-compose"
    ```
5.  **Đẩy code lên GitHub:**
    Đầu tiên, bạn cần lên [GitHub](https://github.com/) tạo một Repository trống (không chọn thêm README, .gitignore, hay license). Sau đó copy các lệnh được hướng dẫn trên GitHub dán vào Terminal. Thường nó sẽ trông như thế này:
    ```bash
    git branch -M main
    git remote add origin <URL_REPOSITORY_CUA_BAN>
    git push -u origin main
    ```

## Verification
*   **Kiểm tra UI:** Truy cập `http://localhost:5173` (hoặc port được báo trong Terminal). Nếu thấy giao diện chào mừng của Vite + React, bạn đã khởi tạo thành công!
*   **Kiểm tra Git:** Truy cập vào Repository trên GitHub của bạn. Nếu bạn thấy thư mục `frontend` và file `docker-compose.yml` hiện lên ở đó, chúc mừng bạn, mã nguồn đã được sao lưu an toàn!

***
*Navigation:* [🏠 Home](../README.md) | [⬅️ Previous: Phase 1](../01-DevTools-and-Docker/README.md) | [Next: Phase 3 ➡️](../03-Express-Setup/README.md)
