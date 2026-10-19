# 🐾 PetMemory — Cozy Scrapbook & Digital Memory Journal

> *Nơi lưu giữ từng khoảnh khắc, ánh mắt và bước chân nhỏ của người bạn bốn chân.*

---

## 📖 1. Giới thiệu dự án (About PetMemory)
**PetMemory** là một nền tảng web lưu giữ ký ức về thú cưng (chó, mèo,...) được thiết kế theo phong cách **cozy scrapbook & digital memory journal**. 

Khác biệt hoàn toàn với các ứng dụng quản lý thú y hay dashboard số liệu khô khan, PetMemory chú trọng vào:
- **Cảm xúc & Sự ấm áp:** Từng trang ký ức mô phỏng cuốn sổ tay dán ảnh (scrapbook) thủ công với khung ảnh Polaroid, băng dính washi tape, tem dán sticker và nét chữ viết tay hoài niệm.
- **Tình yêu & Sự đồng hành:** Ghi lại từ những trò nghịch ngợm ngô nghê đầu đời, những cột mốc trưởng thành, đến góc tưởng niệm trang trọng, dịu êm (Rainbow Bridge) khi các bé tạm biệt thế giới.
- **Trải nghiệm thư giãn, chữa lành:** Tông màu pastel/kraft paper, chuyển động êm dịu, không áp lực số liệu, đem lại cảm giác yên bình mỗi lần mở trang web.

---

## 🛠️ 2. Định hướng Tech Stack
- **Frontend (`client/`):** React 18+ với TypeScript, Vite, CSS Modules / Vanilla CSS hiện đại, Framer Motion (chuyển động scrapbook & lật trang), Lucide Icons.
- **Backend (`server/`):** Node.js, Express, TypeScript / ES Modules, Mongoose (MongoDB ODM), JWT Authentication.
- **Cơ sở dữ liệu:** MongoDB Atlas (Lưu trữ linh hoạt các scrapbook entry, sticker vị trí, kỷ niệm đa phương tiện).
- **Lưu trữ hình ảnh/âm thanh:** Cloudinary / AWS S3.

---

## 📂 3. Cấu trúc dự án
```text
PetMemory/
├── README.md                      # Tài liệu tổng quan dự án
├── .gitignore                     # Cấu hình bỏ qua git cho Node & React
├── client/                        # Mã nguồn ứng dụng Frontend (React + TypeScript)
├── server/                        # Mã nguồn ứng dụng Backend (Node.js + Express)
├── design/                        # Tokens màu sắc, typography, stickers, mockup assets
├── prompts/                       # Lưu trữ master prompt & prompt chi tiết theo từng phase
└── docs/                          # Hệ thống tài liệu kiến trúc & đặc tả chi tiết
    ├── 00_PROJECT_VISION.md       # Tầm nhìn, triết lý cảm xúc và mục tiêu sản phẩm
    ├── 01_PRODUCT_REQUIREMENTS.md # Yêu cầu chức năng và phi chức năng (PRD)
    ├── 02_USER_FLOW.md            # Luồng người dùng & hành trình trải nghiệm
    ├── 03_UI_BIBLE.md             # Cẩm nang thiết kế UI (màu sắc, font, hiệu ứng giấy)
    ├── 04_COMPONENT_BIBLE.md      # Quy chuẩn component giao diện (Polaroid, Washi,...)
    ├── 05_DATABASE_BIBLE.md       # Thiết kế Schema MongoDB & quan hệ dữ liệu
    ├── 06_BACKEND_API_BIBLE.md    # Danh mục RESTful API endpoints & JWT specs
    ├── 07_FRONTEND_ARCHITECTURE.md# Kiến trúc Frontend, state management, routes
    ├── 08_ANIMATION_BIBLE.md      # Hướng dẫn micro-interactions & lật sổ mềm mại
    ├── 09_DEPLOYMENT_GUIDE.md     # Hướng dẫn deploy client & server lên cloud
    ├── 10_TESTING_GUIDE.md        # Kế hoạch kiểm thử chất lượng và UX
    ├── 11_MASTER_PROMPT_FOR_CODEX.md # Bản chỉ thị chuẩn cho AI code generation
    └── components/                # Đặc tả chi tiết từng component cụ thể
```

---

## 🚀 4. Lộ trình triển khai (Roadmap)
- **Phase 0:** Khởi tạo kiến trúc, tài liệu khung định hướng (Hiện tại).
- **Phase 1:** Thiết lập Design System, tokens, tài nguyên đồ họa scrapbook (Polaroid, paper textures, washi tape).
- **Phase 2:** Xây dựng Server Backend (Auth, Pet Profiles, Memory CRUD, Cloud Storage).
- **Phase 3:** Xây dựng Client Frontend (Giao diện sổ tay, feed kỷ niệm, trình soạn bài scrapbook).
- **Phase 4:** Góc tưởng niệm Cầu Cầu Vồng (Rainbow Bridge Memorial Space) & Tương tác ánh nến.
- **Phase 5:** Tối ưu hóa animation, xuất kỷ niệm (PDF/Image export) & triển khai production.
