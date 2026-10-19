# 🧩 04 — COMPONENT BIBLE & CORE CARD ROADMAP
**Dự án:** PetMemory  
**Giai đoạn:** Bước 1 — Chuẩn hóa Design Tokens & Danh mục Component cốt lõi  

---

## 1. Quy tắc thiết kế Component chung (Core Component Architecture)

Mọi component trong hệ thống giao diện PetMemory bắt buộc phải tuân thủ nghiêm ngặt 4 nguyên tắc sau:

1. **Thuần túy UI (UI-Only & Separation of Concerns):**
   - Component chỉ đảm nhận nhiệm vụ hiển thị giao diện và xử lý tương tác người dùng qua các hàm callback props (`onClick`, `onSelect`, `onChange`).
   - Tuyệt đối không gọi trực tiếp API Backend bên trong các Card Component (việc gọi API do Pages, Context hoặc Custom Hooks đảm nhận).
2. **Kế thừa 100% từ Design Tokens:**
   - Không hardcode các mã màu ngẫu nhiên (`#...`), font chữ hay khoảng cách.
   - Bắt buộc sử dụng hệ thống CSS Variables chuẩn hóa tại [03_UI_BIBLE.md](file:///d:/PetMemory/docs/03_UI_BIBLE.md) (`var(--bg-primary)`, `var(--text-primary)`, `var(--radius-md)`, `var(--shadow-card)`,...).
3. **Khả năng tiếp cận & Điều hướng bàn phím (Accessibility):**
   - Mọi thẻ bấm được đều phải hỗ trợ `tabIndex={0}`, kích hoạt bằng phím `Enter` / `Space`, và có `aria-label` mô tả rõ ràng.
   - Tự động thích ứng với cấu hình hệ điều hành `prefers-reduced-motion` để giảm bớt chuyển động cho người dùng nhạy cảm.
4. **An toàn kiểu dữ liệu (Strict Type-Safety):**
   - Toàn bộ component được định nghĩa bằng React + TypeScript, có interface Props rõ ràng, có chú thích JSDoc cho từng thuộc tính.

---

## 2. Lộ trình 7 nhóm Card cốt lõi (Core Card Taxonomy & Roadmap)

Thay vì thiết kế dàn trải hàng trăm component cùng lúc, PetMemory tập trung hoàn thiện 7 nhóm Card chủ chốt làm linh hồn cho trải nghiệm Scrapbook:

| STT | Tên Component | Mục đích & Mô tả giao diện | Trạng thái đặc tả |
| :-: | :--- | :--- | :--- |
| **01** | **`PetCard`** | Thẻ hồ sơ bé cưng trên nền ảnh Polaroid tại Màn hình 2 (chọn profile hoặc thêm bé mới). | ✅ **[Hoàn thành đặc tả chi tiết](file:///d:/PetMemory/docs/components/PetCard.md)** |
| **02** | **`MemoryPolaroidCard`** | Thẻ ảnh kỷ niệm trung tâm cuốn sổ, có viền giấy trắng, góc nghiêng tự nhiên và chữ viết tay. | ⏳ Lộ trình Phase 3 (Scrapbook Core) |
| **03** | **`MilestoneCard`** | Thẻ tôn vinh các mốc thời gian đặc biệt (Gotcha Day, sinh nhật tròn năm, chuyến đi đầu tiên). | ⏳ Lộ trình Phase 3 (Scrapbook Core) |
| **04** | **`StickyNoteCard`** | Thẻ mẩu giấy note có dòng kẻ nhạt hoặc giấy kraft xé mép, đính ghim gỗ mộc mạc. | ⏳ Lộ trình Phase 3 (Scrapbook Core) |
| **05** | **`AudioMemoryCard`** | Thẻ phát âm thanh kỷ niệm hình cuộn băng cassette vintage (tiếng gừ gừ, tiếng sủa mừng). | ⏳ Lộ trình Phase 3 (Scrapbook Core) |
| **06** | **`MemorialCandleCard`** | Thẻ nến tưởng niệm với hiệu ứng ánh lửa lung linh tại góc Cầu Cầu Vồng (Rainbow Bridge). | ⏳ Lộ trình Phase 4 (Memorial Space) |
| **07** | **`HeavenLetterCard`** | Thẻ lá thư gửi người bạn bốn chân với hiệu ứng phong bì niêm phong sáp cổ điển. | ⏳ Lộ trình Phase 4 (Memorial Space) |

---

> Các component tiếp theo sẽ lần lượt được bổ sung tài liệu chi tiết vào thư mục [`docs/components/`](file:///d:/PetMemory/docs/components/) khi bước vào từng giai đoạn tương ứng.
