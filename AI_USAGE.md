# AI Usage Log

## 1. Công cụ AI
Tên công cụ: Claude (Anthropic) – dùng qua Claude Code trong VS Code.

## 2. Mục đích sử dụng
- Phân tích giao diện và lập bảng khảo sát nháp cho 5 khu vực của website Tiki.
- Đề xuất bố cục thẻ sản phẩm và cách hiển thị giá.
- Tạo mã HTML/CSS khởi đầu và giải thích vai trò từng phần.

## 3. Prompt đã sử dụng

**Prompt 1 – Phân tích website**
```
Bạn là chuyên gia phân tích nghiệp vụ và thiết kế trải nghiệm người dùng
cho website thương mại điện tử.
Tôi đang khảo sát website: Tiki – https://tiki.vn.
Hãy giúp tôi lập bảng phân tích các khu vực:
1. Trang chủ. 2. Danh mục sản phẩm. 3. Chi tiết sản phẩm. 4. Tìm kiếm. 5. Giỏ hàng.
Với mỗi khu vực, hãy nêu:
- Mục đích của chức năng.
- Thành phần giao diện cần có.
- Điểm thuận tiện đối với khách hàng.
- Một vấn đề có thể phát sinh.
- Một đề xuất cải tiến.
Không khẳng định những tính năng chưa được kiểm chứng.
Phân biệt rõ nhận xét dựa trên quan sát và đề xuất của AI.
```

**Prompt 2 – Đề xuất giao diện**
```
Tôi đang thực hiện bài tập phát triển giao diện website thương mại điện tử
bằng HTML5 và CSS3.
Tôi muốn cải tiến khu vực: thẻ sản phẩm trong danh sách – cách hiển thị giá gốc,
giá khuyến mãi, tỷ lệ giảm giá và bố cục trên điện thoại.
Đối tượng sử dụng: khách hàng mua sắm trực tuyến tại Việt Nam.
Hãy đề xuất: 1. Bố cục giao diện. 2. Các thành phần HTML cần sử dụng.
3. Cách tổ chức CSS. 4. Cách hiển thị trên máy tính và điện thoại.
5. Những điểm cần kiểm tra về khả năng sử dụng.
Trước tiên, hãy giải thích phương án thiết kế.
Chưa tạo toàn bộ mã nguồn cho đến khi tôi yêu cầu.
```

**Prompt 3 – Tạo mã nguồn**
```
Dựa trên phương án đã thống nhất, hãy tạo một trang giao diện
thương mại điện tử bằng HTML5 và CSS3.
Yêu cầu: có tiêu đề và khu vực sản phẩm; tối thiểu 4 sản phẩm mẫu; mỗi sản phẩm
có hình ảnh, tên, giá và nút thao tác; bố cục phù hợp máy tính và điện thoại;
HTML cấu trúc rõ ràng; CSS tách file riêng; không backend/cơ sở dữ liệu;
không thư viện không cần thiết.
Giải thích cách chạy trang web và những phần tôi cần kiểm tra.
```

## 4. Kết quả AI đề xuất
- **Bố cục:** thẻ dạng cột – ảnh vuông ở trên (nhãn % ở góc), tên 2 dòng, đánh giá + lượt bán, khối giá, dòng "Tiết kiệm", nút "Thêm vào giỏ" ở đáy.
- **Thứ bậc giá:** giá bán lớn – đỏ – đậm; giá gốc nhỏ – xám – gạch ngang; thêm số tiền tiết kiệm vì người mua dễ cảm nhận "số tiền" hơn "%".
- **HTML:** `<header>`, `<main>`, `<section>`, danh sách `<ul>/<li>`, mỗi sản phẩm là `<article>`; giá gốc dùng `<s>`; `alt` cho ảnh; nhãn ẩn cho trình đọc màn hình.
- **CSS:** biến màu trong `:root`; mobile-first; CSS Grid 2/3/4 cột tại mốc 640px và 1024px; Flexbox trong thẻ với `margin-top: auto` để nút luôn nằm đáy.
- **Cần kiểm tra:** thẻ thẳng hàng khi tên dài/ngắn; giá dài không tràn trên màn hình 320–360px; nút ≥ 44px; độ tương phản màu; sản phẩm không giảm giá vẫn hiển thị hợp lý.

## 5. Kiểm tra và điều chỉnh
> Phần này **người làm bài phải tự điền** sau khi chạy thử. Gợi ý những điểm có thể tự phát hiện & sửa:

| Điểm kiểm tra | Kết quả | Điều chỉnh của tôi |
|---|---|---|
| Bảng khảo sát AI so với tiki.vn thật | … | Loại bỏ / sửa nhận xét … |
| Màn hình 320px (iPhone SE đời cũ): giá có tràn? | … | Ví dụ: đã thêm media query `max-width: 359px` giảm cỡ chữ giá |
| Sản phẩm không giảm giá (bình giữ nhiệt) | … | Ví dụ: đổi màu giá sang màu chữ thường để không gây hiểu nhầm là đang giảm |
| Nút "Thêm vào giỏ" chưa có hiệu ứng khi bấm | … | Ví dụ: thêm `.btn-buy:active { transform: scale(.97); }` |
| Phần AI đề xuất nhưng tôi **không dùng** | … | Ví dụ: không thêm JavaScript đếm giỏ hàng vì ngoài phạm vi bài |

## 6. Phần tôi hiểu và có thể giải thích
- `<meta name="viewport">`: bắt buộc để trang co giãn đúng trên điện thoại.
- `<article class="product-card">` trong `<li>`: mỗi sản phẩm là một nội dung độc lập nằm trong danh sách.
- `display: grid; grid-template-columns: repeat(2, 1fr)` + `@media (min-width: …)`: đổi số cột theo màn hình (mobile-first).
- `display: flex; flex-direction: column` + `.price { margin-top: auto }`: đẩy khối giá và nút xuống đáy để các thẻ thẳng hàng.
- `.product-media { position: relative }` + `.badge-discount { position: absolute }`: đặt nhãn % đè lên góc ảnh.
- `aspect-ratio: 1/1` + `object-fit: cover`: ảnh luôn vuông, không méo.
- `-webkit-line-clamp: 2`: cắt tên sản phẩm còn 2 dòng.
- `<s>` + `.visually-hidden`: gạch ngang giá gốc và vẫn cho trình đọc màn hình đọc "Giá gốc".
- Biến CSS (`--color-sale`…): đổi màu toàn trang tại một chỗ.
