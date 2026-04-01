---
name: Figma to UIKit Converter
description: Kỹ năng giúp chuyển đổi thiết kế chuẩn từ Figma thành mã HTML/CSS/JS sử dụng framework UIkit.
---

# Figma to UIKit Conversion Skill

## Nguyên tắc cốt lõi (Core Directives)

1. **Ưu tiên dùng class UIkit (UIKit-First Policy):** 
   Luôn cố gắng sử dụng các class và component có sẵn của UIkit (vd như `uk-card`, `uk-grid`, `uk-button`, `uk-container`, v.v.) TRƯỚC KHI sử dụng custom CSS. Điều này giúp code gọn gàng, tăng tốc độ website và dễ bảo trì.
   
2. **Khoảng cách (Spacing Utilities):** 
   Tận dụng hệ thống Utility của UIkit (`uk-margin-*`, `uk-padding-*`) để mô phỏng chính xác nhất các thông số padding/margin (Gap) trong Figma.
   
3. **Thiết kế chạy tốt trên nhiều màn hình (Responsive Design):** 
   Sử dụng UIkit Responsive Grid (vd: `uk-child-width-1-2@s uk-child-width-1-3@m`) hoặc Responsive Utilities (`uk-visible@m`) để khớp với các bản thiết kế Desktop/Tablet/Mobile trên Figma.
   
4. **Chỉ dùng Custom CSS khi thực sự cần thiết:** 
   Khi Figma yêu cầu một mã màu Hex riêng, bo góc (border-radius) đặc biệt, hoặc font chữ khác chuẩn UIkit, lúc đó mới trích xuất các thông số này riêng vào một file `styles.css`. KHÔNG dùng inline CSS (`style="..."`).

## Nguyên tắc "Map" (ánh xạ) Figma vào UIkit

- **Figma Auto Layout (Horizontal/Row)** ➔ `<div uk-grid>` hoặc `<div class="uk-flex">`
- **Figma Auto Layout (Vertical/Column)** ➔ `uk-flex-column`
- **Figma Gap / Spacing (Khoảng cách)** ➔ `uk-grid-column-*`, `uk-grid-row-*`, `uk-margin-*`
- **Figma Typography (Text, H1, H2,...)** ➔ `uk-h1`, `uk-h2`, `uk-text-lead`, `uk-text-meta`, `uk-text-muted`
- **Figma Drop Shadow (Đổ bóng)** ➔ `uk-box-shadow-small/medium/large/xlarge`
- **Figma Box (Card Layout)** ➔ `<div class="uk-card uk-card-default uk-card-body">`
- **Figma Corner Radius (Bo tròn)** ➔ Mặc định UIkit có sẵn ở các card, nhưng nếu tuỳ chỉnh có thể thêm custom `.uk-border-rounded`
- **Figma Overlay / Modal** ➔ `uk-modal`

## Hướng dẫn thực thi (Execution Instructions)

Khi người dùng yêu cầu chuyển đổi một link Figma (hoặc node Figma) sang HTML bằng UIkit:
1. **Liên kết với Figma**: Sử dụng Figma MCP Server để đọc cấu trúc Layout và các thông số styles (màu sắc, kích thước, font) từ bản thiết kế Figma của USER.
2. **Khai báo bộ khung HTML**: Xây dựng cấu trúc bằng UIkit CDN (`uikit.min.css` và `uikit.min.js`, `uikit-icons.min.js`).
3. **Phân tích theo Layout từ lớn đến bé**:
   - Xác định vùng bao quanh (`uk-section`, `uk-container`).
   - Xây dựng hệ thống lưới (Grid).
   - Đặt các khối Component nội dung (Text, Button, Card, Image) vào đúng lưới.
4. **Tuyệt đối sử dụng Component gốc**: Mọi nút bấm (button), menu chuyển hướng (navbar), tab... phải đối chiếu với [Tài liệu UIKit](https://getuikit.com/docs).
5. **Tinh chỉnh**: Bổ sung file `custom.css` cuối cùng với các biến `--primary-color`, custom font size từ Figma để sản phẩm hoàn thiện và có "cái hồn" đồ hoạ của người thiết kế.
