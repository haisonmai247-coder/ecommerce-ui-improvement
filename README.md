# E-commerce UI Improvement

## 1. Giới thiệu
Bài tập cá nhân Chương 1 – môn Phát triển ứng dụng thương mại điện tử.
Sau khi khảo sát website Tiki, tôi chọn cải tiến **thẻ sản phẩm trong danh sách**, tập trung vào **cách hiển thị giá gốc, giá khuyến mãi, tỷ lệ giảm giá** và **bố cục trên điện thoại**.

## 2. Website tham khảo
- Tên website: Tiki
- URL: https://tiki.vn
- Khu vực đã khảo sát: Trang chủ, Danh mục sản phẩm, Chi tiết sản phẩm, Tìm kiếm, Giỏ hàng (xem [KHAO_SAT.md](KHAO_SAT.md))

## 3. Chức năng
- Hiển thị danh sách 6 sản phẩm mẫu.
- Mỗi sản phẩm có hình ảnh, tên, đánh giá, lượt bán, giá và nút "Thêm vào giỏ".
- Hiển thị rõ giá khuyến mãi, giá gốc, nhãn % giảm và số tiền tiết kiệm.
- Bố cục hỗ trợ nhiều kích thước màn hình: 2 cột (điện thoại), 3 cột (máy tính bảng), 4 cột (máy tính).

## 4. Công nghệ
- HTML5
- CSS3 (CSS Grid, Flexbox, Media Query, CSS Variables) – không dùng thư viện ngoài, không backend.

## 5. Cách chạy
Mở file `index.html` bằng trình duyệt.
Để kiểm tra giao diện điện thoại: Chrome → `F12` → bật **Toggle device toolbar** (`Ctrl + Shift + M`) → chọn iPhone SE / Galaxy S.

Cấu trúc thư mục:
```
ecommerce-ui-improvement/
├── index.html
├── css/style.css
├── images/        (ảnh minh họa SVG tự vẽ, không dùng ảnh có bản quyền)
├── KHAO_SAT.md
├── README.md
└── AI_USAGE.md
```

## 6. Cải tiến đã thực hiện
**Vấn đề ban đầu:** Trên thẻ sản phẩm, giá gốc, giá khuyến mãi và % giảm có cỡ chữ và vị trí gần nhau nên khó so sánh nhanh; khách không thấy ngay số tiền tiết kiệm; trên điện thoại tên dài làm các thẻ lệch hàng.

**Thay đổi:**
| Thành phần | Cách làm |
|---|---|
| Giá khuyến mãi | Chữ lớn, đậm, màu đỏ (`.price-sale`) – là thông tin quan trọng nhất |
| Giá gốc | Chữ nhỏ, xám, gạch ngang bằng thẻ `<s>`, có chữ ẩn "Giá gốc" cho trình đọc màn hình |
| % giảm | Nhãn tròn đỏ ở góc ảnh (`.badge-discount`, `position: absolute`) |
| Tiết kiệm | Dòng mới "Tiết kiệm X₫" nền hồng nhạt (`.price-save`) |
| Tên sản phẩm | Giới hạn 2 dòng (`line-clamp`) để các thẻ thẳng hàng |
| Nút mua | Rộng toàn thẻ, cao ≥ 44px, dễ bấm bằng ngón tay |
| Bố cục | Mobile-first với CSS Grid: 2 → 3 → 4 cột; `margin-top: auto` giữ khối giá và nút ở đáy thẻ |

## 7. Hỗ trợ từ AI
AI (Claude) hỗ trợ: gợi ý bảng khảo sát ban đầu, đề xuất bố cục, tạo mã HTML/CSS khởi đầu.
Tôi đã kiểm tra, điều chỉnh hoặc bổ sung: đối chiếu bảng khảo sát với website thật, chạy thử trên nhiều kích thước màn hình, tự sửa … *(ghi điểm bạn tự sửa)*. Chi tiết xem [AI_USAGE.md](AI_USAGE.md).
