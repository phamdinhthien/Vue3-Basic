# Dự Án Vue 3 + Vite

Đây là một dự án hiện đại sử dụng Vue 3 và công cụ build Vite. Dự án thể hiện các phương pháp thực hành tốt nhất và các tính năng chính của Vue 3.

## Bắt Đầu

1. Cài đặt các gói phụ thuộc:
```bash
npm install
```

2. Chạy máy chủ phát triển:
```bash
npm run dev
```

## Cấu Trúc Dự Án

```
├── public/            # Tài nguyên tĩnh
├── src/
│   ├── assets/       # Tài nguyên dự án (hình ảnh, styles)
│   │   └── styles/   # File CSS
│   ├── components/   # Components Vue có thể tái sử dụng
│   │   ├── ms-button/# Component button
│   │   └── ms-table/ # Component table
│   ├── utils/        # Các hàm tiện ích
│   ├── views/        # Components trang
│   ├── App.vue       # Component gốc
│   └── main.js       # Điểm khởi đầu ứng dụng
├── vite.config.js    # Cấu hình Vite
└── .gitignore        # Cấu hình bỏ qua Git
```

## Quy Tắc Đặt Tên

### Tên Thư Mục
- Sử dụng chữ thường và dấu gạch ngang (-) để ngăn cách các từ
- Tên phải mô tả rõ mục đích của thư mục
- Ví dụ: `ms-button`, `ms-table`

### Tên File
1. File Components:
   - Sử dụng PascalCase (viết hoa chữ cái đầu của mỗi từ)
   - Phải kết thúc bằng .vue
   - Ví dụ: `MsButton.vue`, `Counter.vue`

2. File JavaScript:
   - Sử dụng camelCase (chữ cái đầu tiên viết thường, các từ tiếp theo viết hoa)
   - Phải kết thúc bằng .js
   - Ví dụ: `formatter.js`, `main.js`

3. File CSS:
   - Sử dụng chữ thường và dấu gạch ngang
   - Phải kết thúc bằng .css
   - Ví dụ: `base.css`

## Kiểm Soát Phiên Bản

File `.gitignore` loại trừ các mục sau:
- Thư mục node modules (`node_modules/`)
- Thư mục build (`dist/`, `dist-ssr/`)
- File phát triển cục bộ (`*.local`)
- File logs (`logs/`, `*.log`)
- File của trình soạn thảo (`.vscode/`, `.idea/`, `.DS_Store`, v.v.)

## Tính Năng

- Vue 3 Composition API với `<script setup>`
- Phát triển nhanh với Vite
- Kiến trúc dựa trên components
- Component button tùy chỉnh (MsButton)
- Component table tùy chỉnh (MsTable)
- Trang Counter mẫu
- CSS cơ bản

## Công Cụ Phát Triển

- [Tài liệu Vue 3](https://v3.vuejs.org/)
- [Tài liệu Vite](https://vitejs.dev/)
- [Vue SFC `<script setup>`](https://v3.vuejs.org/api/sfc-script-setup.html)
- [Hỗ trợ IDE cho Vue](https://vuejs.org/guide/scaling-up/tooling.html#ide-support)

## Các Lệnh Có Sẵn

- `npm run dev` - Khởi động máy chủ phát triển
- `npm run build` - Build cho production
- `npm run preview` - Xem trước bản build production
