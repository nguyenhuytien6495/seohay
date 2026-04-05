# Project: seohay.vn (BuffSEO Marketing)

Website tĩnh cho công ty Marketing BUFF - chuyên Dịch Vụ SEO, Đào Tạo SEO, Thiết kế Website.

## Role
Expert front-end developer chuyên convert Figma to HTML/CSS sử dụng UIkit 3.x framework.

## Tech Stack
- HTML/CSS thuần + UIkit 3.x (CDN từ seohay.vn/assets/web/)
- Font: SVN-Gilroy (woff2, 4 weights: 400/500/600/700) - local trong `fonts/`
- CSS chung: `style.css` (font-face definitions + UIkit CSS variable overrides)
- Không có build tool, không có JS framework

## File Structure
```
seohay/
├── contact.html        # Trang liên hệ
├── home.html           # Trang chủ
├── style.css           # Font definitions + UIkit CSS overrides
├── fonts/              # SVN-Gilroy woff2 files
├── image/              # Images (.webp format)
└── .agents/            # Agent skills & workflows
```

## Critical Rules
1. **UIkit-First**: LUÔN ưu tiên dùng class UIkit trước khi viết custom CSS
2. **BEM naming** với prefix `ju_` cho mọi custom class (vd: `ju_banner`, `ju_banner__title`, `ju_banner--active`)
3. CSS page-specific viết trong `<style>` tag ở `<head>` của mỗi trang, KHÔNG tách file CSS riêng cho từng page
4. Font override qua CSS variables `--uk-global-font-family` và `--uk-heading-font-family` trong `style.css`
5. KHÔNG dùng inline CSS (`style="..."`) trừ trường hợp cá biệt (vd: icon color)
6. Images dùng format `.webp`, đặt trong thư mục `image/`

## HTML Layout Patterns
- **Section structure** (BẮT BUỘC): `<section>` > `<div class="uk-container">` hoặc `<div class="uk-container-large">`
  - Luôn dùng `uk-container`, nếu cần rộng hơn thì: `<div class="uk-container uk-container-large">`
- Slider/Carousel: dùng UIkit `uk-slider`, KHÔNG tự code carousel
- Responsive breakpoints: `@s` (640px), `@m` (960px), `@l` (1200px)
- Header desktop: `uk-visible@m` với `uk-navbar` + `uk-sticky`
- Header mobile: `uk-hidden@l` với `uk-offcanvas`
- Cards: `uk-card uk-card-default` + custom BEM classes (`ju_*`)
- Forms: `uk-input`, `uk-textarea` + custom `ju_form_*` classes

## SEO Requirements
- Đầy đủ meta tags: Open Graph, Twitter Card, Schema.org JSON-LD, Dublin Core
- Tracking: Facebook Pixel + Google Analytics (G-CHC6WW8WBX) + GTM (GTM-P5ZP6J7)
- Canonical URL: https://seohay.vn/

## Figma to UIkit Workflow
Chi tiết tại: `.agents/workflows/figma-to-uikit.md` và `.agents/skills/figma_to_uikit/SKILL.md`

### Tóm tắt:
1. Đọc Figma → trích xuất tokens (colors, fonts, spacing)
2. Dựng skeleton HTML với UIkit components
3. Ánh xạ Figma components → UIkit classes
4. Căn chỉnh spacing & typography
5. Responsive cho Desktop/Tablet/Mobile
6. Review & tối ưu CSS
