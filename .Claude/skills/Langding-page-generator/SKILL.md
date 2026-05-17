# Landing Page Generator — Skill

Tạo landing page hoàn chỉnh dạng single-page HTML + Tailwind CSS cho các khóa học tại Softech Aptech Đà Nẵng. Trang có thể deploy trực tiếp lên Vercel.

---

## 1. THÔNG TIN CẦN HỎI TRƯỚC KHI BẮT ĐẦU

### 1.1. Chủ đề / Nội dung khóa học

Trước khi code, hỏi người dùng những thông tin sau:

| # | Câu hỏi | Ví dụ |
|---|---------|-------|
| 1 | **Khóa học gì?** Tên khóa học, ngôn ngữ/công nghệ chính | Claude Code, Python, React, Firebase |
| 2 | **Khóa học dành cho ai?** | Sinh viên, người đi làm, beginner |
| 3 | **Thời lượng?** | 8 buổi, 16 tiết, 4 tuần |
| 4 | **Học phí gốc & giảm giá?** | 5.000.000đ → 3.500.000đ (giảm 30%) |
| 5 | **Lịch khai giảng?** | Tháng 6/2026 |
| 6 | **Điểm nổi bật / ưu điểm?** | 3-6 điểm để tạo feature cards |
| 7 | **Sản phẩm học viên?** | Tên project, link demo, tech stack |
| 8 | **Đội ngũ hỗ trợ sau khóa học?** | Group Zalo, 3 tháng, video vĩnh viễn... |
| 9 | **Nội dung 8 buổi học?** | Mỗi buổi gồm: tên, số tiết, mô tả ngắn |
| 10 | **FAQ?** | 4-6 câu hỏi phổ biến + câu trả lời |

### 1.2. Màu sắc chủ đạo

Hỏi người dùng **trước khi bắt đầu code**:

- **Primary color** (màu chính — nút CTA, accent): ví dụ `#DF6B33` (cam)
- **Secondary/Accent** (màu phụ): ví dụ `#F4A261` (cam nhạt)
- **Background**: ví dụ `#090A14` (dark navy)
- **Card background**: ví dụ `#13141F`
- **Border color**: ví dụ `#1F2030`
- **Text muted**: ví dụ `#A0A0B0`

> Nếu không cung cấp → sử dụng bộ màu mặc định (cam đậm + dark theme như project Claude Code).

### 1.3. Hình ảnh & Icons

Hỏi người dùng **trước khi bắt đầu code**:

- **Ảnh minh họa / hero visual**: lấy từ nguồn nào? (Unsplash, Figma export, URL cụ thể, hoặc dùng icon placeholder)
- **Logo**: file có sẵn hay dùng text-based logo?
- **Icons**: dùng [Lucide Icons](https://lucide.dev) (miễn phí, nhẹ) hay bộ icon khác?

> Nếu không cung cấp → dùng **Lucide Icons** via CDN, hero visual = CSS-only decorative box với icon.

### 1.4. Thông tin liên hệ

- Địa chỉ: 24 Lê Thánh Tôn, Đà Nẵng
- Hotline: 0236.3.779.779
- Email: info@softech.vn
- Website: softech.vn

---

## 2. CẤU TRÚC LANDING PAGE

### 2.1. Các section theo thứ tự

```
1. Navigation          — Logo + menu + CTA button
2. Hero                — Badge + heading + subtitle + CTA + price + hero visual + stats
3. Problem Statement   — 4 pain point cards
4. Solution (Features) — 6 feature cards
5. Target Audience     — 4 audience cards (icon + title + subtitle + description)
6. Roadmap / Timeline  — 8 session cards (vertical timeline)
7. Social Proof       — Highlight project card + quote + stats
8. CTA / Registration — Heading + form (5 fields) + success message + contact info
9. FAQ                — 4-6 accordion items
10. Footer             — Brand + contact + social + newsletter
```

### 2.2. Form đăng ký — 5 trường chuẩn

| # | Trường | Type | Bắt buộc | Ghi chú |
|---|--------|------|---------|---------|
| 1 | Họ và tên | text | ✓ | |
| 2 | Email | email | ✓ | validate format |
| 3 | Số điện thoại | tel | — | |
| 4 | Nội dung cần tư vấn | select | ✓ | 7 options: Firebase Backend, Frontend, Deploy, Prompt Engineering, Debug & Refactor, Fullstack, Khác |
| 5 | Tiêu chí ngành nghề | text | — | placeholder: "VD: Thương mại điện tử, Giáo dục..." |

- Validation JS: highlight border đỏ + hiển thị thông báo lỗi
- Success state: ẩn form, hiện thông báo thành công

---

## 3. DESIGN SYSTEM (Tailwind CSS)

### 3.1. Font

- **Heading**: Plus Jakarta Sans (Google Fonts)
- **Body**: Inter (Google Fonts)

### 3.2. Tailwind config pattern

```js
tailwind.config = {
  theme: {
    extend: {
      colors: {
        bg: '#090A14',
        card: '#13141F',
        border: '#1F2030',
        primary: '#DF6B33',
        'primary-hover': '#C55A28',
        'text-main': '#FFFFFF',
        'text-muted': '#A0A0B0',
        accent: '#F4A261',
      },
      fontFamily: {
        heading: ['Plus Jakarta Sans', 'sans-serif'],
        body: ['Inter', 'sans-serif'],
      },
    }
  }
}
```

### 3.3. CSS utilities tùy chỉnh

```css
.gradient-text   { /* text gradient từ primary → accent */ }
.glow-box        { /* box-shadow glow primary */ }
.card-hover      { /* hover: border primary + translateY(-4px) */ }
.btn-primary     { /* hover: primary-hover + scale(0.98) */ }
.btn-secondary   { /* hover: border primary + text primary */ }
.reveal          { /* scroll-reveal animation: opacity + translateY */ }
.nav-scrolled    { /* navbar blur khi scroll */ }
.faq-content     { /* accordion max-height transition */ }
.mobile-menu     { /* mobile nav toggle */ }
```

### 3.4. Lucide Icons

```html
<script src="https://unpkg.com/lucide@latest"></script>
<script> lucide.createIcons(); </script>
```

Icon phổ biến: `arrow-right`, `terminal`, `target`, `wrench`, `lightbulb`, `video`, `users`, `credit-card`, `clock`, `brain`, `alert-triangle`, `bot`, `graduation-cap`, `briefcase`, `palette`, `code-2`, `layout-dashboard`, `external-link`, `phone`, `mail`, `map-pin`, `facebook`, `message-circle`, `linkedin`, `youtube`, `check-circle`, `chevron-down`, `play-circle`, `menu`

### 3.5. Scroll reveal

Dùng `IntersectionObserver` — thêm class `reveal` vào mọi element cần animate, observer trigger khi `threshold: 0.1`.

### 3.6. Counter animation

Animation đếm số từ 0 → target khi scroll vào viewport. Dùng `requestAnimationFrame`.

---

## 4. RESPONSIVE

- Breakpoint mobile-first
- Navbar: hamburger menu trên mobile, menu đầy đủ trên lg
- Grid: 1 cột mobile → 2 cột sm → 3 cột lg
- Form: full-width trên mobile

---

## 5. ACCESSIBILITY

- Semantic HTML (`<header>`, `<main>`, `<section>`, `<footer>`, `<nav>`, `<form>`)
- `aria-label` trên tất cả icon buttons và navigation links
- `aria-required`, `aria-describedby` trên form fields
- `role="alert"` trên error messages
- `aria-live="polite"` trên success message
- `aria-expanded` trên mobile menu toggle
- `:focus-visible` custom style (outline primary color)

---

## 6. DEPLOY

- Single HTML file — deploy trực tiếp lên **Vercel** (kéo thả hoặc git)
- Không cần build step, không cần server
- Vercel tự nhận diện và host static file

---

## 7. CHECKLIST TRƯỚC KHI BÀN GIAO

- [ ] Tất cả 10 sections có mặt
- [ ] Form validation hoạt động (required fields + email format)
- [ ] Success message hiện sau submit
- [ ] Mobile menu toggle hoạt động
- [ ] FAQ accordion hoạt động
- [ ] Scroll reveal animate khi cuộn
- [ ] Hero visual hiển thị đúng
- [ ] Màu sắc khớp với bộ màu đã chọn
- [ ] Hotline/email/địa chỉ chính xác
- [ ] OG meta tags đầy đủ cho social sharing
- [ ] Favicon / theme-color meta tag
- [ ] Không có dead links
