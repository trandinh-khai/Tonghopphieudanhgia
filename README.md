[README.md](https://github.com/user-attachments/files/22508225/README.md)
# Dashboard Khảo Sát — Gọn & Hiện đại

> Trực quan hóa dữ liệu khảo sát CSVC, học liệu và dịch vụ hỗ trợ người học theo **Khoa** và **Tiêu chí**.  
> Công nghệ: **HTML**, **TailwindCSS**, **Chart.js (kèm datalabels)**. Không cần backend — chỉ mở file là chạy.

<p align="center">
  <img alt="status" src="https://img.shields.io/badge/status-active-brightgreen">
  <img alt="license" src="https://img.shields.io/badge/license-MIT-blue">
  <img alt="stack" src="https://img.shields.io/badge/stack-HTML%20%7C%20Tailwind%20%7C%20Chart.js-8A2BE2">
</p>

## ✨ Tính năng chính
- **KPI nhanh**: tổng số bản ghi, % Đồng ý (CA + A), % Phân vân (N), % Không đồng ý (D + CD).
- **Bộ lọc thông minh**: theo **Khoa**, **Tiêu chí**, và **Tìm kiếm nhanh**.
- **Biểu đồ gọn**:  
  - Bar Chart “**Tổng quan theo tiêu chí**” (Top 8 tỉ lệ đồng ý cao nhất).  
  - Doughnut Chart “**Cơ cấu đánh giá**” theo CA / A / N / D / CD.
- **Bảng dữ liệu**: Top 50 dòng phù hợp bộ lọc kèm **% Đồng ý** từng dòng.
- **Dark mode**: nút 🌓 ở góc dưới phải, tự nhớ lựa chọn của người dùng.
- **Parser CSV "chịu va đập"**: chấp nhận tiêu chí có dấu phẩy, tự ghép cột để đảm bảo đúng 7 cột.

## 🗂 Cấu trúc thư mục
```
.
├─ index_compact.html     # Giao diện dashboard gọn & hiện đại
├─ Data.txt               # Dữ liệu khảo sát dạng CSV (có thể đổi tên/đường dẫn)
└─ README.md              # Tài liệu dự án (file này)
```

## 🚀 Cách chạy (Local)
1. Đặt `index_compact.html` **cùng thư mục** với `Data.txt`.
2. Mở `index_compact.html` bằng trình duyệt (Chrome/Edge/Firefox).  
   > Không cần cài đặt gì thêm.

> ⚠️ Nếu bạn mở file bằng một số trình duyệt có bảo mật `file://` nghiêm ngặt, việc `fetch("Data.txt")` có thể bị chặn.  
> Cách đơn giản: chạy một HTTP server cục bộ.
> - Python 3: `python -m http.server 8000` → truy cập `http://localhost:8000`
> - Node: `npx serve`

## 🌐 Triển khai GitHub Pages
1. Tạo repo GitHub, đẩy 3 file: `index_compact.html`, `Data.txt`, `README.md`.
2. Vào **Settings → Pages**:  
   - **Source**: chọn `Deploy from a branch`  
   - **Branch**: `main` → `/ (root)` → **Save**  
3. Truy cập URL do GitHub Pages cấp.

> Lưu ý: Vì `fetch("Data.txt")`, hãy để **Data.txt ở cùng thư mục gốc** với HTML.  

## 📄 Định dạng dữ liệu (CSV)
Bắt buộc thứ tự cột:
```
Criterion, Faculty, Completely Agree, Agree, Neutral, Disagree, Completely Disagree
```

Ví dụ:
```
"Phòng đọc của thư viện đáp ứng yêu cầu về diện tích, chỗ ngồi.",Khoa Công nghệ thông tin,0.4064,0.4576,0.0899,0.0327,0.0145
```

- Cột **Criterion** có thể chứa dấu phẩy. Parser sẽ tự ghép để đảm bảo **đủ 7 cột**.
- Dữ liệu có thể ở dạng **tỉ lệ (0.40)** hoặc **% (40%)** — hệ thống tự chuyển đổi.

## 🔧 Tuỳ chỉnh nhanh
- **Giới hạn danh sách Tiêu chí** trong dropdown (mặc định lấy tối đa 300):  
  Tìm `criteria].slice(0,300)` trong JS và tăng/giảm theo nhu cầu.
- **Số dòng bảng**: tìm `data.slice(0,50)` để thay đổi giới hạn hiển thị.
- **Top N biểu đồ Bar**: tìm `.slice(0,8)` để đổi số tiêu chí hiển thị.

## 📈 Ảnh chụp màn hình (gợi ý)
> Thêm ảnh minh họa vào repo của bạn rồi cập nhật đường dẫn bên dưới.
<p align="center">
  <img src="screenshots/kpi.png" width="720" alt="KPI tổng quan">
</p>
<p align="center">
  <img src="screenshots/charts.png" width="720" alt="Biểu đồ tổng quan & cơ cấu">
</p>

## 🗺 Lộ trình (Roadmap)
- [ ] Xuất Excel/PDF báo cáo.
- [ ] Thêm biểu đồ theo **Khoa** (so sánh nhanh nhiều khoa).
- [ ] Bộ lọc theo **nhóm tiêu chí** (Thư viện, Ký túc xá, Học liệu…).

## 🤝 Đóng góp
Đóng góp, báo lỗi hoặc đề xuất tính năng bằng **Issues** / **Pull Requests**.  
Quy ước code: giữ phong cách **gọn – rõ – nhất quán**.  

## 📜 License
Phát hành theo giấy phép **MIT**. Xem nội dung trong file `LICENSE` (hoặc sửa phần này theo chính sách của bạn).
