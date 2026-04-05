# Project: seohay.vn (BuffSEO Marketing)

Website tĩnh cho công ty Marketing BUFF - chuyên Dịch Vụ SEO, Đào Tạo SEO, Thiết kế Website.

## Tech Stack
- HTML/CSS thuần + UIkit 3.x (CDN)
- Font: SVN-Gilroy (woff2, weights: 400/500/600/700) trong `fonts/`
- CSS chung: `style.css` (font-face + UIkit variable overrides)
- Không có build tool, không có JS framework

## File Structure
```
seohay/
├── contact.html        # Trang liên hệ
├── home.html           # Trang chủ
├── style.css           # Font definitions + UIkit CSS overrides
├── fonts/              # SVN-Gilroy woff2
├── image/              # Images (.webp)
└── .agents/            # Agent skills & workflows
```

## Quy tắc Code

### CSS
- **UIkit-First**: Ưu tiên class UIkit, chỉ custom CSS khi UIkit không đáp ứng
- **BEM naming** với prefix `ju_` (vd: `ju_banner`, `ju_banner__title`, `ju_banner--active`)
- CSS page-specific viết trong `<style>` tag ở `<head>`, KHÔNG tách file riêng
- Font override qua CSS variables trong `style.css`

### HTML Layout
- **Section structure** (BẮT BUỘC): Mọi section đều phải bọc trong `<section>` > `<div class="uk-container">` hoặc `<div class="uk-container-large">`:
  ```html
  <section class="ju_section_name">
    <div class="uk-container">
      <!-- nội dung section -->
    </div>
  </section>
  ```
  - Luôn dùng `uk-container`, nếu cần rộng hơn thì thêm `uk-container-large`: `<div class="uk-container uk-container-large">`
- **Grid**: `uk-grid` với `uk-width-*` cho layout cột
- **Slider/Carousel**: dùng UIkit `uk-slider` (https://getuikit.com/docs/slider), KHÔNG tự code carousel
- **Header desktop**: `uk-visible@m` với `uk-navbar`, sticky dùng `uk-sticky`
- **Header mobile**: `uk-hidden@l` với `uk-offcanvas` cho menu
- **Responsive**: dùng UIkit breakpoints (`@s`, `@m`, `@l`)
- Images dùng `.webp` hoặc `.png`

### SEO
- Đầy đủ meta tags: OG, Twitter Card, Schema.org JSON-LD, Dublin Core
- Facebook Pixel + Google Analytics + GTM

## Workflow: Figma to UIkit
Xem chi tiết: `.agents/workflows/figma-to-uikit.md`
