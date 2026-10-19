# 🎨 03 — UI BIBLE & DESIGN SYSTEM
**Dự án:** PetMemory  
**Phong cách chủ đạo:** Cozy Scrapbook + Digital Memory Journal (Ấm áp, cảm xúc, lấy hình ảnh và ký ức làm trung tâm, không làm dashboard nhiều số liệu).  

---

## 1. Triết lý thẩm mỹ (Aesthetic Philosophy)
- **Cảm xúc & Hoài niệm:** Tái hiện xúc cảm của một cuốn sổ lưu niệm giấy thủ công (scrapbook) — nơi từng khoảnh khắc của bé cưng được trân trọng nâng niu.
- **Không áp lực số liệu:** Loại bỏ hoàn toàn cảm giác dashboard quản trị, bảng biểu lạnh lùng hay các gam màu văn phòng công nghiệp.
- **Tôn trọng tính chân thực:** Mỗi bé thú cưng có hình ảnh thật từ chính chủ nuôi (Sen), không dùng hình vẽ minh họa trừu tượng thay thế cho hình đại diện thực tế.

---

## 2. Color Tokens (CSS Variables chuẩn)

```css
:root {
  /* --- Backgrounds --- */
  --bg-primary: #FAF7F2;      /* Kem giấy thư: Nền canvas chính toàn bộ trang web */
  --bg-surface: #F2ECE4;      /* Ivory: Khung trang giấy lót, vùng chứa phụ */
  --bg-elevated: #FFFFFF;     /* Khung giấy trắng / Nền ảnh Polaroid */

  /* --- Text --- */
  --text-primary: #3D322C;    /* Nâu Espresso: Màu chữ chính, mềm mại hơn đen thuần */
  --text-secondary: #7A6B63;  /* Nâu Mocha: Phụ đề, ngày tháng, thông tin bổ trợ */
  --text-muted: #A89B93;      /* Nâu nhạt: Chú thích mờ, placeholder, trạng thái disabled */

  /* --- Accents --- */
  --accent-primary: #D7A49A;  /* Dusty Rose: Cảm xúc dịu ngọt, nút bấm nhấn, trái tim */
  --accent-secondary: #A3B19B;/* Sage Green: Xanh xô thơm, tươi mát, thiên nhiên */
  --accent-warm: #E4C9B6;     /* Nude: Băng dán washi tape, khung viền mềm */
  --accent-blue: #A4B1BA;     /* Baby Blue: Huy hiệu mây trời, kỷ niệm bình yên */

  /* --- Borders & Shadows --- */
  --border-subtle: #E6DEC8;   /* Đường viền mộc mạc như mép giấy gấp */
  --shadow-card: 0 8px 24px -4px rgba(61, 50, 44, 0.07);   /* Đổ bóng thẻ mềm mại */
  --shadow-hover: 0 14px 30px -4px rgba(61, 50, 44, 0.12); /* Đổ bóng nâng khi hover */

  /* --- Border Radius --- */
  --radius-sm: 8px;           /* Bo góc nhỏ: Nút bấm phụ, nhãn tag */
  --radius-md: 12px;          /* Bo góc vừa: Khung ảnh, ô nhập liệu */
  --radius-lg: 16px;          /* Bo góc lớn: Khung thẻ chính, Modal */
  --radius-pill: 9999px;      /* Bo tròn hoàn toàn: Huy hiệu, Pill button */
}
```

---

## 3. Typography Tokens

Hệ thống phông chữ kết hợp giữa nét hoài cổ của font có chân, sự tinh gọn dễ đọc của font không chân hiện đại, và nét chấm phá của font viết tay:

| Vai trò | Phông chữ | Fallback | Mục đích sử dụng |
| :--- | :--- | :--- | :--- |
| **Heading** | `'Cormorant Garamond'` | `serif` | Tiêu đề lớn, tên bé cưng, tiêu đề cuốn sổ, câu trích dẫn cảm xúc |
| **Body** | `'Instrument Sans'` | `sans-serif` | Toàn bộ văn bản nội dung, nhãn mô tả, form nhập liệu, thông số |
| **Accent / Handwriting** | `'Caveat'` | `cursive` | Chữ ký thư, ghi chú viết tay ngắn dán trên mép ảnh Polaroid |

### Quy chuẩn kích cỡ font (Type Scale):
```css
--text-xs: 0.75rem;     /* 12px - Chú thích thời gian, thẻ tag nhỏ */
--text-sm: 0.875rem;    /* 14px - Thông tin bổ trợ, đếm ngày bên nhau */
--text-base: 1rem;      /* 16px - Văn bản chuẩn, nội dung nhật ký */
--text-lg: 1.125rem;    /* 18px - Chữ viết tay nhấn mạnh, subheader */
--text-xl: 1.25rem;     /* 20px - Tiêu đề component, tên bé trong thẻ */
--text-2xl: 1.75rem;    /* 28px - Tiêu đề section */
--text-3xl: 2.25rem;    /* 36px - Tiêu đề trang, tên cuốn sổ chính */
```

---

## 4. Spacing & Grid System

- **Hệ số Spacing cơ bản:** 4px grid (`4px`, `8px`, `12px`, `16px`, `24px`, `32px`, `48px`, `64px`).
- **Khoảng cách đệm thẻ (Card Padding):**
  - Desktop: `20px` - `24px`
  - Mobile: `16px`

---

## 5. Quy tắc cứng (Strict Design & Accessibility Rules)

1. **Mobile-First & Responsive ngay từ đầu:** Tất cả bố cục phải hiển thị hoàn hảo từ màn hình di động nhỏ (360px) đến màn hình desktop lớn (1440px+).
2. **Tôn trọng `prefers-reduced-motion`:** Mọi chuyển động (hover, lật thẻ, fade-in) phải tự động tắt hoặc chuyển sang hiệu ứng chuyển độ mờ (`opacity transition`) tức thì khi người dùng bật chế độ giảm chuyển động trong hệ điều hành.
3. **Ảnh thật của thú cưng:** Trong hồ sơ thực tế, bắt buộc dùng ảnh thật do người dùng cung cấp. Tuyệt đối không dùng ảnh minh họa hoạt hình hay placeholder trừu tượng để thay thế ảnh bé. Nếu chưa kịp tải ảnh, chỉ dùng icon dấu chân tối giản màu nude/espresso mờ (`--accent-warm`).
4. **Không dùng màu đen tuyệt đối (`#000000`):** Mọi văn bản tối nhất đều sử dụng Espresso (`--text-primary: #3D322C`) để giữ được nét mềm mại của mực bút viết trên giấy thủ công.
