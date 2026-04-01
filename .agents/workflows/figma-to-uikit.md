---
description: Quy trình (workflow) chuyển một thiết kế Figma sang mã HTML/CSS hoàn thiện với Framework UIkit.
---

# Figma to UIkit Conversion Workflow

Dưới đây là quy trình chi tiết (step-by-step) dành cho Agent hoặc lập trình viên khi CẮT (convert) giao diện từ Figma sang web tĩnh bằng UIkit.

## Bước 1: Khởi tạo Dư án (Setup Project)
 - Đọc URL gốc Figma thông qua tiện ích mở rộng/Figma MCP Server để tải cấu trúc file.
 - Khởi tạo dự án mới:
   - Tạo file `index.html`.
   - Tạo thư mục `assets/css` chứa file `style.css`.
   - Tạo thư mục `assets/js` chứa file `main.js`.
 - Thiết lập mã nguồn chuẩn HTML5 có nhúng CDN UIkit.
```html
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Thiết kế từ Figma sang UIkit</title>
    <!-- UIkit CSS -->
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/uikit@3.21.13/dist/css/uikit.min.css" />
    <link rel="stylesheet" href="assets/css/style.css" />
</head>
<body>
    <!-- Layout chính sẽ được viết tại đây -->

    <!-- UIkit JS -->
    <script src="https://cdn.jsdelivr.net/npm/uikit@3.21.13/dist/js/uikit.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/uikit@3.21.13/dist/js/uikit-icons.min.js"></script>
</body>
</html>
```

## Bước 2: Phân tích & Trích xuất Biến thiết kế (Tokens Extraction)
 - Tìm trên Figma các màu chủ đạo (Primary, Secondary, Background, Text) và ghi nhận vào `style.css` tạo thành CSS Variables (`:root { ... }`).
 - Khai báo cấu trúc phông chữ (Google Fonts) trong `style.css` để giữ nét nhận diện thương hiệu của UIkit.
```css
:root {
  --color-primary: #mã_màu;
  --color-secondary: #mã_màu;
  --color-bg: #mã_màu_nền;
}
```

## Bước 3: Phác thảo "Khung xương" HTML (Skeleton Outline)
 - Đọc cấu trúc Auto-layout / Grid của Figma Node, tiến hành chuyển đổi ra cấu trúc HTML thuần túy.
 - Bao quát mã trong thẻ `<div class="uk-section">` cho các đoạn (section).
 - Sử dụng Component Grid của UIkit (`uk-grid`) hoặc Flexbox Component (`uk-flex`) để chia cột/kéo thả các layout lớn.
 - Giữ nội dung bên trong khu vực khung an toàn bằng `uk-container`.

## Bước 4: Ánh xạ Component trực tiếp (Component Implementation)
 - Biến mọi chi tiết Figma thành mã nguồn UIkit Component tương thích thay vì tạo CSS mới:
   - Nút nhấn (Buttons) ➔ Sử dụng class `uk-button uk-button-default` hoặc `uk-button-primary`.
   - Card/Khối thẻ (Cards) ➔ Tái cấu trúc thành: `uk-card uk-card-default uk-card-body`.
   - Ô nhập (Form input) ➔ Dùng chuẩn của UIkit `<input class="uk-input" />`.
   - Biểu tượng mờ/mũi tên/cạnh ➔ Dùng component UIKit Icon `<span uk-icon="icon: list"></span>`.

## Bước 5: Căn chỉnh Khoảng cách & Typography
 - Mọi Spacing (Padding/Margin) từ Figma cần được làm tròn và chuyển nhượng sang utility classes.
   - Khoảng cách lề ngoài (Margin) ➔ Dùng `uk-margin`, `uk-margin-small`, `uk-margin-large`.
   - Kích cỡ chữ, căn chữ ➔ `uk-text-large`, `uk-text-center`, `uk-text-bold`, `uk-heading-small`.
 - Nếu UIkit không đáp ứng được khoảng cách chuẩn tuyệt đối (Pixel-Perfect) từ Figma, viết bộ Override CSS lên file `style.css`.

## Bước 6: Kiểm tra Tính tương thích với Mobile (Responsivness)
 - Figma thường bao gồm 2 hoặc 3 trang màn hình (Desktop, Tablet, Mobile).
 - Dùng class CSS đuôi `@s`, `@m`, `@l` để ẩn hiện hoặc điều chỉnh grid cột theo tỷ lệ kích cỡ (vd: `uk-child-width-1-2@s`).
 - Bật Grid Responsive và kiểm tra lỗi overflow (xem có cột nào vỡ ra ngoài trên thiết bị nhỏ không).
 - Cấu hình Offcanvas (menu ngang trượt ra từ bên hông) cho bộ điều hướng Navigation Header trên mobile.

## Bước 7: Bàn giao & Đánh giá (Review & Finalizing)
 - Trộn/Dịch lại toàn bộ các icon nếu thiếu bằng thư viện ngoài (VD: FontAwesome nếu UIKit thiếu biểu tượng cần thiết).
 - Lược bỏ bớt CSS tùy chỉnh (Custom CSS) nếu mã nguồn đang quá rườm rà.
 - Đảm bảo Agent xuất hiện đầy đủ thông báo hoàn tất và đề xuất người dùng mở file `index.html` lên trình duyệt để nghiệm thu.

## Bước 8: Tối ưu hoá CSS & Tiêu chuẩn Đặt tên Class
 - Tối ưu CSS: Trong trường hợp cần tạo CSS riêng, hãy đặt class chung và khai báo CSS trực tiếp ở thẻ `<style>` trên `<head>`. Tuỳ vào hoàn cảnh cụ thể, có thể sử dụng inline CSS cho các trường hợp cá biệt.
 - Đặt tên Class: Bắt buộc tuân thủ chuẩn BEM (Block Element Modifier) khi đặt tên class và luôn có tiền tố `ju_` trước mỗi class (Ví dụ: `ju_banner`, `ju_banner__title`, `ju_banner--active`).
