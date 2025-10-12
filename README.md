# Vue 3 + Vite Project

This is a modern Vue 3 project built with Vite as the build tool. The project demonstrates best practices and key Vue 3 features.

## Getting Started

1. Install dependencies:
```bash
npm install
```

2. Run development server:
```bash
npm run dev
```

## Project Structure

```
├── public/          # Static assets
├── src/
│   ├── assets/     # Project assets (images, styles)
│   ├── components/ # Reusable Vue components
│   ├── views/      # Page components
│   ├── App.vue     # Root component
│   └── main.js     # Application entry point
├── vite.config.js  # Vite configuration
└── .gitignore      # Git ignore patterns
```

## Version Control

The project includes a `.gitignore` file that excludes:
- Node dependencies (`node_modules/`)
- Build outputs (`dist/`, `dist-ssr/`)
- Local development files (`*.local`)
- Log files (`logs/`, `*.log`)
- Editor-specific files (`.vscode/`, `.idea/`, `.DS_Store`, etc.)

## Features

- Vue 3 Composition API with `<script setup>`
- Fast development with Vite
- Component-based architecture
- Custom button component (MsButton)
- Counter view implementation
- Base CSS styling

## Development Tools

- [Vue 3 Documentation](https://v3.vuejs.org/)
- [Vite Documentation](https://vitejs.dev/)
- [Vue SFC `<script setup>`](https://v3.vuejs.org/api/sfc-script-setup.html)
- [Vue IDE Support](https://vuejs.org/guide/scaling-up/tooling.html#ide-support)

## Available Scripts

- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm run preview` - Preview production build locally
