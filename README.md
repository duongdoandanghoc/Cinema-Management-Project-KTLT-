# 🎬 DQA Cinema Booking System

![C](https://img.shields.io/badge/c-%2300599C.svg?style=for-the-badge&logo=c&logoColor=white)
![C++](https://img.shields.io/badge/c++-%2300599C.svg?style=for-the-badge&logo=c%2B%2B&logoColor=white)
![Windows](https://img.shields.io/badge/Windows-0078D6?style=for-the-badge&logo=windows&logoColor=white)

> Hệ thống quản lý và đặt vé xem phim Console-based, minh họa quá trình tiến hóa kiến trúc phần mềm từ **C thuần (Procedural)** sang **C++ (Object-Oriented Programming - OOP)**.

---

## 📑 Mục lục
- [Giới thiệu](#-giới-thiệu)
- [Tính năng nổi bật](#-tính-năng-nổi-bật)
- [Tiến trình phát triển (Các phiên bản)](#-tiến-trình-phát-triển-các-phiên-bản)
- [Cấu trúc hệ thống](#-cấu-trúc-hệ-thống)
- [Hướng dẫn cài đặt & Khởi chạy](#-hướng-dẫn-cài-đặt--khởi-chạy)
- [Phân loại giá vé](#-phân-loại-giá-vé)
- [Summary (English)](#-summary-english)

---

## 🚀 Giới thiệu
**DQA Cinema** là một dự án học thuật nhằm mô phỏng toàn bộ luồng nghiệp vụ của một rạp chiếu phim: từ hiển thị sơ đồ ghế, đặt vé, tính toán giá trị (bao gồm thuế), đến thanh toán và quản lý dữ liệu phim. 

Dự án sử dụng file text phẳng (`.txt`) để lưu trữ dữ liệu, phù hợp cho việc rèn luyện tư duy quản lý luồng dữ liệu (File I/O), xử lý chuỗi và thiết kế giao diện Console.

---

## ✨ Tính năng nổi bật

### 👤 Dành cho Khách hàng (User)
* **Tra cứu lịch chiếu:** Đọc và hiển thị danh sách phim thời gian thực từ `Movie_details.txt`.
* **Sơ đồ ghế trực quan:** Hiển thị ma trận ghế ngồi với trạng thái Trống (`S`) / Đã đặt (`H`).
* **Định giá động:** Tự động tính toán tổng chi phí dựa trên phân khúc ghế (Tiết kiệm, Cao cấp, Đặc biệt) và áp dụng 10% VAT.
* **Thanh toán & Xuất vé:** Giả lập thanh toán qua Mã QR hoặc Chuyển khoản và in biên lai chi tiết.

### 🔐 Dành cho Quản trị viên (Admin)
* **Xác thực:** Đăng nhập an toàn với thông tin mặc định (`admin` / `admin`).
* **Quản lý Rạp:** Thêm, sửa, xóa lịch chiếu phim.
* **Kiểm soát vé:** Truy xuất lịch sử đặt vé chi tiết của từng bộ phim.

---

## 🔄 Tiến trình phát triển (Các phiên bản)

Dự án được chia thành 3 phiên bản, thể hiện sự tối ưu hóa dần về mặt tư duy lập trình:

| File | Ngôn ngữ | Đặc điểm Kiến trúc & Kỹ thuật |
| :--- | :--- | :--- |
| `cinema.cpp` | **C thuần** | Sử dụng `FILE*`, `goto`, và Windows API (`Beep`, `Sleep`, `system("cls")`). Thể hiện tư duy lập trình tuyến tính và quản lý bộ nhớ thủ công. |
| `CinemaC++.cpp` | **C++ (Lai C)** | Quá độ lên C++. Thay thế `FILE*` bằng `fstream`. Giới thiệu class `Ticket` cơ bản nhưng vẫn sử dụng các hàm C standard (`strcmp`, `char[]`). |
| `rapchieuphimcb.cpp` | **C++ (OOP)** | Thuần hướng đối tượng. Encapsulation với class `Position` và `RoomTheatre`. Quản lý ghế theo tọa độ (A1, B2) và cung cấp các module riêng biệt để đặt/hủy/kiểm tra trạng thái. |

---

## 📂 Cấu trúc hệ thống

```text
DQA-Cinema/
├── cinema.cpp                 # Source code: Phiên bản C
├── CinemaC++.cpp              # Source code: Phiên bản C++ lai
├── rapchieuphimcb.cpp         # Source code: Phiên bản OOP C++
├── Movie_details.txt          # Database: Danh sách phim & Suất chiếu
├── tt1.txt -> tt5.txt         # Database: Lịch sử đặt vé (Tự động sinh)
├── ghe1.txt -> ghe5.txt       # Database: Trạng thái ghế (Tự động sinh)
└── README.md
```
## ⚙️ Hướng dẫn cài đặt và chạy

1. **Clone Repository**

```bash
git clone https://github.com/yourusername/DQA-Cinema.git
cd DQA-Cinema
```
2. **Biên dịch**
```bash
# Với file C (sử dụng GCC):
gcc cinema.cpp -o cinema
# Với file C++:
g++ CinemaC++.cpp -o CinemaCpp
g++ rapchieuphimcb.cpp -o rapchieuphimcb
#Trên Windows, có thể dùng các IDE như Dev-C++, Code::Blocks hoặc Visual Studio.
```
3. **Chạy chương trình**

* Trên Windows: `cinema.exe`, `CinemaCpp.exe`, `rapchieuphimcb.exe`

* Trên Linux/macOS: `./cinema`, `./CinemaCpp`, `./rapchieuphimcb`

## ⚠️ Lưu ý: Các phiên bản dùng `windows.h` (cinema.cpp) chỉ chạy được trên Windows. Nếu muốn chạy trên Linux/macOS, cần thay thế các hàm `Beep`, `Sleep`, `system("cls")` bằng các hàm tương thích (hoặc xóa bỏ).

## 📖 Sổ tay vận hành (User Manual)

🎫 1. **Luồng khách hàng (Đặt vé & Thanh toán)**
1. Tại Menu chính, nhập `1` để khởi tạo luồng đặt vé.
2. Hệ thống parse file `Movie_details.txt` và in danh sách suất chiếu.
3. Nhập ID phim. Khối xử lý sẽ load ma trận ghế (`H`: Đã khóa, `S`: Khả dụng).
4. Khai báo số lượng và map với ID ghế (01-80).Nhập Metadata người dùng (Tên, SĐT, Email).
5. Hệ thống tính toán tổng vòng tín dụng (đã gồm 10% VAT) -> In QR Code / Info chuyển khoản.
6. Ghi nhận giao dịch vào `tt*.txt` và chốt state ghế vào `ghe*.txt`.
## 🛡️ 2. Luồng quản trị (Admin Dashboard)

1. Tại Menu, chọn `2` và authenticate với credentials: `admin` / `admin`.2. Truy cập các hàm CRUD:
* Thay đổi Metadata (Tên, Thời gian chiếu).
* Truy xuất lịch sử giao dịch (Parse các file tt*.txt).
* Thêm node phim mới hoặc Delete phim theo tên.
## 🗺️ 3. Cơ chế phân vùng giá vé
| **Vùng tọa độ** | **Hạng ghế** | **Đơn giá (VND)** |
| **01 – 20** | **Tiết kiệm (Economy)** |60,000 |
| **21 – 60** | **Cao cấp (Premium)** | 80,000 |
| **61 – 80** | **Đặc biệt (VIP)** | 100,000 |
Ghi chú: Format `file Movie_details.txt` yêu cầu tuân thủ cấu trúc: `[ID] [Tên_Phim] [Giờ_chiếu]` 
## Summary (English)
# DQA Cinema Booking System
This project is a simple movie ticket booking system implemented in C and C++. It includes multiple versions: a pure C version (`cinema.cpp`), a mixed C++ version (`CinemaC++.cpp`), and an object-oriented C++ version (`rapchieuphimcb.cpp`). Key features include viewing movie listings, seat selection with dynamic pricing (`economy, premium, VIP zones`), payment simulation (`QR code/bank transfer`), receipt printing, and admin functions for movie management. Data is stored in plain text files (`Movie_details.txt, tt*.txt, ghe*.txt`). The latest version (`rapchieuphimcb.cpp`) demonstrates modern C++ with classes Position and RoomTheatre, managing seats using coordinate-based identifiers (e.g., A1, B2). Suitable for learning basic file I/O, console UI, and transitioning from C to C++.

Happy coding! 🎬🍿