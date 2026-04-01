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
- Pattern: `uk-section` > `uk-container` > `uk-grid`
- Responsive: dùng UIkit breakpoints (`@s`, `@m`, `@l`)
- Header chỉ hiện desktop: `uk-visible@m`
- Images dùng `.webp`

### SEO
- Đầy đủ meta tags: OG, Twitter Card, Schema.org JSON-LD, Dublin Core
- Facebook Pixel + Google Analytics + GTM

## Workflow: Figma to UIkit
Xem chi tiết: `.agents/workflows/figma-to-uikit.md`
