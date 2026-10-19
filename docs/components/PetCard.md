# 🐾 Component Specification: `PetCard`

---

## 1. Mục đích & Vị trí sử dụng
- **Vị trí hiển thị:** Màn hình 2 (Màn hình chọn thú cưng / Profile Selection Screen).
- **Mục đích:** Đóng vai trò là cánh cửa bước vào thế giới kỷ niệm của từng bé cưng theo phong cách thân mật, ấm áp (tương tự việc chọn profile người dùng nhưng mang cảm xúc như lật xem các bìa sổ kỷ niệm trên giá sách).
- **Các biến thể (Variants):**
  - `profile`: Hiển thị hồ sơ của bé cưng đã có trong hệ thống.
  - `add-new`: Thẻ đặc biệt dùng để thêm một bé cưng mới vào gia đình.

---

## 2. Bố cục, tỷ lệ ảnh & kích thước
- **Phong cách thiết kế:** Mô phỏng khung ảnh Polaroid thủ công đặt trên nền giấy sáng màu (`--bg-elevated: #FFFFFF`).
- **Kích thước chuẩn:**
  - Chiều rộng trên Desktop: `240px` – `260px`.
  - Chiều cao tự động ôm sát nội dung (khoảng `340px` – `360px`).
- **Khung ảnh đại diện:**
  - Tỷ lệ khung hình: Đúng chuẩn vuông `1:1`.
  - Viền xung quanh ảnh: Khoảng trắng đồng đều `12px` ở 3 cạnh trên - trái - phải; phần lề dưới mở rộng (`16px` - `20px`) tạo không gian đặc trưng của ảnh chụp lấy liền Polaroid.
  - Bo góc nhẹ: `--radius-md: 12px` cho cả thẻ và ảnh bên trong.
  - Đổ bóng: `--shadow-card` êm dịu, viền mảnh `--border-subtle`.

---

## 3. Nội dung hiển thị & Thứ tự ưu tiên
Dữ liệu trên thẻ được sắp xếp theo thứ tự thị giác từ trên xuống dưới:

1. **Ảnh đại diện thật của bé (Avatar):** 
   - Ảnh thật do người dùng tải lên, hiển thị chế độ `object-fit: cover`.
   - Nếu chưa có ảnh: Hiển thị placeholder dấu chân mộc mạc tối giản trên nền màu `--bg-surface`.
2. **Huy hiệu loài (Species Badge):**
   - Đặt nổi nhẹ ở góc hoặc ngay dưới ảnh.
   - Nhãn hiển thị: `Chó` hoặc `Mèo` (kèm icon nhỏ tinh tế).
   - Màu sắc: Nền `--accent-warm` kết hợp chữ `--text-secondary`.
3. **Tên thú cưng (Pet Name):**
   - Phông chữ: `'Cormorant Garamond', serif`, in đậm vừa (`font-weight: 600`), kích thước `--text-xl` (20px), màu `--text-primary`.
4. **Bộ đếm thời gian bên nhau (Journey Counter):**
   - Phông chữ: `'Instrument Sans', sans-serif`, kích thước `--text-sm` (14px), màu `--text-secondary`.
   - Quy tắc tính:
     - Nếu đang đồng hành (chưa có `endDate`): Tính từ `startDate` đến ngày hiện tại (ví dụ: *"3 năm 2 tháng bên nhau"* hoặc *"850 ngày yêu thương"*).
     - Nếu đã qua Cầu Cầu Vồng (có `endDate`): Tính trọn vẹn quãng thời gian bên nhau kèm biểu tượng ánh sao hoặc thiên thần nhỏ dịu dàng.

---

## 4. Các trạng thái của Component (Component States)

| Trạng thái | Biểu hiện trực quan |
| :--- | :--- |
| **Default** | Thẻ nằm phẳng trên nền, bóng đổ nhẹ `--shadow-card`, viền `--border-subtle`. |
| **Hover** | Thẻ nâng nhẹ lên `translateY(-4px)`, bóng đổ mở rộng `--shadow-hover`, viền ánh nhẹ tone `--accent-primary`. |
| **Selected** | Đường viền đổi sang màu điểm nhấn `--accent-primary` (2px), có tick dấu chân hoặc nơ nhỏ ở góc thẻ. |
| **Loading (Skeleton)** | Khung hình vuông 1:1 nhấp nháy chuyển sắc ấm mềm (shimmer effect từ `--bg-surface` sang `--bg-primary`), các dòng text giả lập dạng thanh bo tròn. |
| **Error (Ảnh hỏng)** | Tự động fallback về khung nền `--bg-surface` với biểu tượng dấu chân mộc mạc, không để vỡ giao diện. |

---

## 5. Hành vi khi nhấn (Click / Tap Interaction)
- **Khi nhấn thẻ `variant: "profile"`:**
  - Kích hoạt callback `onSelect(id)`.
  - Điều hướng người dùng bước vào **Không gian riêng của bé (Màn hình 6 - Cuốn sổ Scrapbook chính)**.
- **Khi nhấn thẻ `variant: "add-new"`:**
  - Thẻ hiển thị dấu cộng `+` vẽ nét thanh mảnh cùng dòng chữ *"Đón thêm một bé cưng"*.
  - Điều hướng người dùng mở **Màn hình 3 (Chọn Chó/Mèo để bắt đầu tạo hồ sơ mới)**.

---

## 6. Bố cục Responsive trên Mobile & Desktop

- **Desktop (>= 1024px):**
  - Hiển thị dạng lưới CSS Grid hoặc Flexbox căn giữa màn hình (`justify-content: center`).
  - Tối đa 4 thẻ trên một hàng (`grid-template-columns: repeat(auto-fit, minmax(240px, 260px))`).
  - Khoảng cách giữa các thẻ (`gap`): `24px`.
- **Tablet (768px - 1023px):**
  - Hiển thị 2 hoặc 3 thẻ trên một hàng (`gap: 20px`).
- **Mobile (< 768px):**
  - Màn hình nhỏ (dưới 420px): Grid 1 cột với thẻ co giãn vừa vặn (`max-width: 280px`, căn giữa màn hình).
  - Màn hình thông thường: Grid 2 cột nhỏ gọn hoặc dải cuộn ngang mượt mà (Snap Carousel), đảm bảo vùng chạm cảm ứng tối thiểu `44x44px`.

---

## 7. Animation & Khả năng tiếp cận (Accessibility)

- **Chuyển động (Framer Motion / CSS Transition):**
  - Khi xuất hiện lần đầu: Hiệu ứng fade-in kết hợp trượt nhẹ từ dưới lên (`opacity: 0 -> 1`, `translateY: 12px -> 0px`, thời gian 0.35s).
  - Transition khi hover: `transition: transform 0.25s ease, box-shadow 0.25s ease`.
  - **Tôn trọng `prefers-reduced-motion`:** Nếu người dùng bật cấu hình giảm chuyển động, vô hiệu hóa `translateY` và giữ nguyên trạng thái tĩnh.
- **Khả năng tiếp cận (Accessibility - a11y):**
  - Thẻ có thể focus bằng phím: `tabIndex={0}`.
  - Phím `Enter` hoặc `Space` kích hoạt hành động chọn thẻ.
  - Thuộc tính ARIA: `role="button"`, `aria-label={`Hồ sơ bé ${name}, loài ${species}, đã đồng hành ${timeTogether}`}`.

---

## 8. TypeScript Props Interface & Ví dụ sử dụng

### Interface định nghĩa:
```typescript
export interface PetCardProps {
  /** Định danh duy nhất của bé cưng (không bắt buộc đối với biến thể add-new) */
  id?: string;
  /** Tên của bé cưng */
  name?: string;
  /** Loài thú cưng */
  species?: 'dog' | 'cat';
  /** Đường dẫn ảnh đại diện thật của bé */
  avatarUrl?: string;
  /** Ngày đón bé về nhà hoặc ngày bắt đầu hành trình */
  startDate?: string | Date;
  /** Ngày bé qua Cầu Cầu Vồng (nếu có) */
  endDate?: string | Date;
  /** Trạng thái đang được chọn trong danh sách */
  isSelected?: boolean;
  /** Biến thể hiển thị: hồ sơ bình thường hoặc nút thêm mới */
  variant: 'profile' | 'add-new';
  /** Hàm callback khi người dùng click vào thẻ */
  onSelect: (petId?: string) => void;
  /** ClassName tùy biến bổ sung (nếu cần) */
  className?: string;
}
```

### Ví dụ sử dụng trong React:
```tsx
import React from 'react';
import { PetCard } from '@/components/cards/PetCard';

export const PetSelectionScreen: React.FC = () => {
  const handleSelectPet = (petId?: string) => {
    console.log('Mở sổ kỷ niệm của bé:', petId);
  };

  const handleAddNewPet = () => {
    console.log('Chuyển hướng đến màn hình tạo hồ sơ mới');
  };

  return (
    <div className="pet-grid-container">
      {/* Thẻ bé cưng có sẵn */}
      <PetCard
        id="pet_01"
        name="Mochi"
        species="cat"
        avatarUrl="/images/mochi-real-avatar.jpg"
        startDate="2021-04-15"
        variant="profile"
        onSelect={handleSelectPet}
      />

      {/* Thẻ thêm bé cưng mới */}
      <PetCard
        variant="add-new"
        onSelect={handleAddNewPet}
      />
    </div>
  );
};
```
